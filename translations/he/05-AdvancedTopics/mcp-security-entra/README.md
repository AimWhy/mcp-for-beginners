<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "6e562d7e5a77c8982da4aa8f762ad1d8",
  "translation_date": "2025-07-02T09:40:33+00:00",
  "source_file": "05-AdvancedTopics/mcp-security-entra/README.md",
  "language_code": "he"
}
-->
# אבטחת זרימות עבודה של AI: אימות Entra ID לשרתי Model Context Protocol

## מבוא  
אבטחת שרת Model Context Protocol (MCP) שלך חשובה לא פחות מלהנעל את דלת הבית. השארת שרת ה-MCP פתוח חושפת את הכלים והנתונים שלך לגישה לא מורשית, שעלולה לגרום להפרות אבטחה. Microsoft Entra ID מספק פתרון חזק לניהול זהויות וגישה מבוסס ענן, המסייע לוודא שרק משתמשים ויישומים מורשים יוכלו לתקשר עם שרת ה-MCP שלך. בסעיף זה תלמד כיצד להגן על זרימות העבודה של ה-AI שלך באמצעות אימות Entra ID.

## מטרות הלמידה  
בסיום הסעיף תוכל:

- להבין את חשיבות אבטחת שרתי MCP.  
- להסביר את היסודות של Microsoft Entra ID ואימות OAuth 2.0.  
- להבחין בין לקוחות ציבוריים ללקוחות חסויים.  
- ליישם אימות Entra ID בתרחישים של שרתי MCP מקומיים (לקוחות ציבוריים) ומרוחקים (לקוחות חסויים).  
- ליישם שיטות אבטחה מיטביות בפיתוח זרימות עבודה של AI.

## אבטחה ו-MCP  

כמו שלא היית משאיר את דלת הבית שלך פתוחה, כך גם אסור להשאיר את שרת ה-MCP שלך פתוח לגישה חופשית. אבטחת זרימות העבודה של ה-AI חיונית לבניית יישומים חזקים, אמינים ובטוחים. פרק זה יציג כיצד להשתמש ב-Microsoft Entra ID כדי לאבטח את שרתי ה-MCP שלך, ולוודא שרק משתמשים ויישומים מורשים יוכלו לגשת לכלים ולנתונים שלך.

## למה אבטחה חשובה לשרתי MCP  

דמיין שלשרת ה-MCP שלך יש כלי שיכול לשלוח מיילים או לגשת למסד נתונים של לקוחות. שרת לא מאובטח יאפשר לכל אחד להשתמש בכלי הזה, מה שעלול להוביל לגישה לא מורשית לנתונים, ספאם או פעילויות זדוניות אחרות.

על ידי יישום אימות, אתה מוודא שכל בקשה לשרת שלך מאומתת, תוך אימות זהות המשתמש או היישום שמבצע את הבקשה. זו השלב הראשון והחשוב ביותר באבטחת זרימות העבודה של ה-AI שלך.

## מבוא ל-Microsoft Entra ID  

[**Microsoft Entra ID**](https://adoption.microsoft.com/microsoft-security/entra/) היא שירות ניהול זהויות וגישה מבוסס ענן. אפשר לדמיין אותה כשומר ביטחון אוניברסלי ליישומים שלך. היא מטפלת בתהליך המורכב של אימות זהויות משתמשים (authentication) וקביעת ההרשאות שלהם (authorization).

באמצעות Entra ID תוכל:

- לאפשר כניסה מאובטחת למשתמשים.  
- להגן על APIs ושירותים.  
- לנהל מדיניות גישה ממקום מרכזי.

עבור שרתי MCP, Entra ID מספקת פתרון חזק ומוכר לניהול מי יכול לגשת ליכולות השרת.

---

## להבין את הקסם: איך עובד אימות Entra ID  

Entra ID משתמשת בסטנדרטים פתוחים כמו **OAuth 2.0** לטיפול באימות. למרות שהפרטים יכולים להיות מורכבים, הרעיון המרכזי פשוט וניתן להבין אותו באמצעות אנלוגיה.

### מבוא עדין ל-OAuth 2.0: מפתח הוולט  
תחשוב על OAuth 2.0 כמו שירות וולט לרכב שלך. כשאתה מגיע למסעדה, אתה לא נותן לוולט את המפתח הראשי שלך. במקום זאת, אתה נותן לו **מפתח וולט** עם הרשאות מוגבלות — הוא יכול להדליק את הרכב ולהנעל את הדלתות, אבל לא לפתוח את תא המטען או את תא הכפפות.

באנלוגיה הזו:

- **אתה** הוא ה-**משתמש**.  
- **הרכב שלך** הוא שרת ה-**MCP** עם הכלים והנתונים היקרים שלו.  
- ה-**וולט** הוא **Microsoft Entra ID**.  
- **חניית הרכב** הוא ה-**לקוח MCP** (היישום שמנסה לגשת לשרת).  
- **מפתח הוולט** הוא ה-**Access Token**.

טוקן הגישה הוא מחרוזת טקסט מאובטחת שהלקוח מקבל מ-Entra ID לאחר הכניסה שלך. הלקוח מציג את הטוקן הזה לשרת ה-MCP בכל בקשה. השרת יכול לאמת את הטוקן כדי לוודא שהבקשה חוקית ושהלקוח מחזיק בהרשאות הנדרשות, וכל זאת מבלי שיצטרך לטפל בפרטי ההתחברות שלך (כמו הסיסמה).

### זרימת האימות  

כך התהליך עובד בפועל:

```mermaid
sequenceDiagram
    actor User as 👤 User
    participant Client as 🖥️ MCP Client
    participant Entra as 🔐 Microsoft Entra ID
    participant Server as 🔧 MCP Server

    Client->>+User: Please sign in to continue.
    User->>+Entra: Enters credentials (username/password).
    Entra-->>Client: Here is your access token.
    User-->>-Client: (Returns to the application)

    Client->>+Server: I need to use a tool. Here is my access token.
    Server->>+Entra: Is this access token valid?
    Entra-->>-Server: Yes, it is.
    Server-->>-Client: Token is valid. Here is the result of the tool.
```

### היכרות עם ספריית האימות של Microsoft (MSAL)  

לפני שנצלול לקוד, חשוב להכיר רכיב מרכזי שתראה בדוגמאות: **Microsoft Authentication Library (MSAL)**.

MSAL היא ספרייה שפותחה על ידי מיקרוסופט שמקלה מאוד על מפתחים לטפל באימות. במקום שתצטרך לכתוב את כל הקוד המורכב לניהול טוקנים, כניסות ותחזוקת סשנים, MSAL עושה את העבודה הכבדה.

שימוש בספרייה כמו MSAL מומלץ מאוד כי:

- **מאובטח:** מיישם פרוטוקולים ותהליכי אבטחה תקניים בתעשייה, ומפחית סיכונים לפרצות בקוד שלך.  
- **מפשט פיתוח:** מסתיר את המורכבות של פרוטוקולי OAuth 2.0 ו-OpenID Connect, ומאפשר להוסיף אימות חזק ליישום בכמה שורות קוד בלבד.  
- **מתוחזק:** מיקרוסופט מעדכנת ושומרת על MSAL באופן פעיל כדי להתמודד עם איומי אבטחה חדשים ושינויים בפלטפורמות.

MSAL תומכת בשפות ובמסגרות עבודה רבות, כולל .NET, JavaScript/TypeScript, Python, Java, Go ופלטפורמות מובייל כמו iOS ואנדרואיד. משמעות הדבר היא שתוכל להשתמש בדפוסי אימות עקביים בכל ערכת הטכנולוגיה שלך.

למידע נוסף על MSAL, ניתן לעיין בתיעוד הרשמי [MSAL overview documentation](https://learn.microsoft.com/entra/identity-platform/msal-overview).

---

## אבטחת שרת MCP עם Entra ID: מדריך שלב אחר שלב  

כעת נעבור כיצד לאבטח שרת MCP מקומי (שמתקשר באמצעות `stdio`) using Entra ID. This example uses a **public client**, which is suitable for applications running on a user's machine, like a desktop app or a local development server.

### Scenario 1: Securing a Local MCP Server (with a Public Client)

In this scenario, we'll look at an MCP server that runs locally, communicates over `stdio`, and uses Entra ID to authenticate the user before allowing access to its tools. The server will have a single tool that fetches the user's profile information from the Microsoft Graph API.

#### 1. Setting Up the Application in Entra ID

Before writing any code, you need to register your application in Microsoft Entra ID. This tells Entra ID about your application and grants it permission to use the authentication service.

1. Navigate to the **[Microsoft Entra portal](https://entra.microsoft.com/)**.
2. Go to **App registrations** and click **New registration**.
3. Give your application a name (e.g., "My Local MCP Server").
4. For **Supported account types**, select **Accounts in this organizational directory only**.
5. You can leave the **Redirect URI** blank for this example.
6. Click **Register**.

Once registered, take note of the **Application (client) ID** and **Directory (tenant) ID**. You'll need these in your code.

#### 2. The Code: A Breakdown

Let's look at the key parts of the code that handle authentication. The full code for this example is available in the [Entra ID - Local - WAM](https://github.com/Azure-Samples/mcp-auth-servers/tree/main/src/entra-id-local-wam) folder of the [mcp-auth-servers GitHub repository](https://github.com/Azure-Samples/mcp-auth-servers).

**`AuthenticationService.cs`**

This class is responsible for handling the interaction with Entra ID.

- **`CreateAsync`**: This method initializes the `PublicClientApplication` from the MSAL (Microsoft Authentication Library). It's configured with your application's `clientId` and `tenantId`.
- **`WithBroker`**: This enables the use of a broker (like the Windows Web Account Manager), which provides a more secure and seamless single sign-on experience.
- **`AcquireTokenAsync`**: זוהי השיטה המרכזית. תחילה היא מנסה לקבל טוקן בשקט (כלומר, המשתמש לא יצטרך להיכנס שוב אם כבר יש לו סשן תקף). אם לא ניתן לקבל טוקן בשקט, תתבקש כניסה אינטראקטיבית.

```csharp
// Simplified for clarity
public static async Task<AuthenticationService> CreateAsync(ILogger<AuthenticationService> logger)
{
    var msalClient = PublicClientApplicationBuilder
        .Create(_clientId) // Your Application (client) ID
        .WithAuthority(AadAuthorityAudience.AzureAdMyOrg)
        .WithTenantId(_tenantId) // Your Directory (tenant) ID
        .WithBroker(new BrokerOptions(BrokerOptions.OperatingSystems.Windows))
        .Build();

    // ... cache registration ...

    return new AuthenticationService(logger, msalClient);
}

public async Task<string> AcquireTokenAsync()
{
    try
    {
        // Try silent authentication first
        var accounts = await _msalClient.GetAccountsAsync();
        var account = accounts.FirstOrDefault();

        AuthenticationResult? result = null;

        if (account != null)
        {
            result = await _msalClient.AcquireTokenSilent(_scopes, account).ExecuteAsync();
        }
        else
        {
            // If no account, or silent fails, go interactive
            result = await _msalClient.AcquireTokenInteractive(_scopes).ExecuteAsync();
        }

        return result.AccessToken;
    }
    catch (Exception ex)
    {
        _logger.LogError(ex, "An error occurred while acquiring the token.");
        throw; // Optionally rethrow the exception for higher-level handling
    }
}
```

**`Program.cs`**

This is where the MCP server is set up and the authentication service is integrated.

- **`AddSingleton<AuthenticationService>`**: This registers the `AuthenticationService` with the dependency injection container, so it can be used by other parts of the application (like our tool).
- **`GetUserDetailsFromGraph` tool**: This tool requires an instance of `AuthenticationService`. Before it does anything, it calls `authService.AcquireTokenAsync()` לקבלת טוקן גישה תקף. אם האימות מצליח, משתמשים בטוקן כדי לקרוא ל-Microsoft Graph API ולמשוך את פרטי המשתמש.

```csharp
// Simplified for clarity
[McpServerTool(Name = "GetUserDetailsFromGraph")]
public static async Task<string> GetUserDetailsFromGraph(
    AuthenticationService authService)
{
    try
    {
        // This will trigger the authentication flow
        var accessToken = await authService.AcquireTokenAsync();

        // Use the token to create a GraphServiceClient
        var graphClient = new GraphServiceClient(
            new BaseBearerTokenAuthenticationProvider(new TokenProvider(authService)));

        var user = await graphClient.Me.GetAsync();

        return System.Text.Json.JsonSerializer.Serialize(user);
    }
    catch (Exception ex)
    {
        return $"Error: {ex.Message}";
    }
}
```

#### 3. איך הכל עובד ביחד  

1. כאשר לקוח ה-MCP מנסה להשתמש ב-`GetUserDetailsFromGraph` tool, the tool first calls `AcquireTokenAsync`.
2. `AcquireTokenAsync` triggers the MSAL library to check for a valid token.
3. If no token is found, MSAL, through the broker, will prompt the user to sign in with their Entra ID account.
4. Once the user signs in, Entra ID issues an access token.
5. The tool receives the token and uses it to make a secure call to the Microsoft Graph API.
6. The user's details are returned to the MCP client.

This process ensures that only authenticated users can use the tool, effectively securing your local MCP server.

### Scenario 2: Securing a Remote MCP Server (with a Confidential Client)

When your MCP server is running on a remote machine (like a cloud server) and communicates over a protocol like HTTP Streaming, the security requirements are different. In this case, you should use a **confidential client** and the **Authorization Code Flow**. This is a more secure method because the application's secrets are never exposed to the browser.

This example uses a TypeScript-based MCP server that uses Express.js to handle HTTP requests.

#### 1. Setting Up the Application in Entra ID

The setup in Entra ID is similar to the public client, but with one key difference: you need to create a **client secret**.

1. Navigate to the **[Microsoft Entra portal](https://entra.microsoft.com/)**.
2. In your app registration, go to the **Certificates & secrets** tab.
3. Click **New client secret**, give it a description, and click **Add**.
4. **Important:** Copy the secret value immediately. You will not be able to see it again.
5. You also need to configure a **Redirect URI**. Go to the **Authentication** tab, click **Add a platform**, select **Web**, and enter the redirect URI for your application (e.g., `http://localhost:3001/auth/callback`).

> **⚠️ Important Security Note:** For production applications, Microsoft strongly recommends using **secretless authentication** methods such as **Managed Identity** or **Workload Identity Federation** instead of client secrets. Client secrets pose security risks as they can be exposed or compromised. Managed identities provide a more secure approach by eliminating the need to store credentials in your code or configuration.
>
> For more information about managed identities and how to implement them, see the [Managed identities for Azure resources overview](https://learn.microsoft.com/entra/identity/managed-identities-azure-resources/overview).

#### 2. The Code: A Breakdown

This example uses a session-based approach. When the user authenticates, the server stores the access token and refresh token in a session and gives the user a session token. This session token is then used for subsequent requests. The full code for this example is available in the [Entra ID - Confidential client](https://github.com/Azure-Samples/mcp-auth-servers/tree/main/src/entra-id-cca-session) folder of the [mcp-auth-servers GitHub repository](https://github.com/Azure-Samples/mcp-auth-servers).

**`Server.ts`**

This file sets up the Express server and the MCP transport layer.

- **`requireBearerAuth`**: This is middleware that protects the `/sse` and `/message` endpoints. It checks for a valid bearer token in the `Authorization` header of the request.
- **`EntraIdServerAuthProvider`**: This is a custom class that implements the `McpServerAuthorizationProvider` interface. It's responsible for handling the OAuth 2.0 flow.
- **`/auth/callback`**: נקודת הקצה הזו מטפלת בהפניה מ-Entra ID לאחר שהמשתמש אותת. היא מחליפה את קוד האישור בטוקן גישה וטוקן רענון.

```typescript
// Simplified for clarity
const app = express();
const { server } = createServer();
const provider = new EntraIdServerAuthProvider();

// Protect the SSE endpoint
app.get("/sse", requireBearerAuth({
  provider,
  requiredScopes: ["User.Read"]
}), async (req, res) => {
  // ... connect to the transport ...
});

// Protect the message endpoint
app.post("/message", requireBearerAuth({
  provider,
  requiredScopes: ["User.Read"]
}), async (req, res) => {
  // ... handle the message ...
});

// Handle the OAuth 2.0 callback
app.get("/auth/callback", (req, res) => {
  provider.handleCallback(req.query.code, req.query.state)
    .then(result => {
      // ... handle success or failure ...
    });
});
```

**`Tools.ts`**

This file defines the tools that the MCP server provides. The `getUserDetails` הכלי דומה לזה שבדוגמה הקודמת, אך מקבל את טוקן הגישה מהסשן.

```typescript
// Simplified for clarity
server.setRequestHandler(CallToolRequestSchema, async (request) => {
  const { name } = request.params;
  const context = request.params?.context as { token?: string } | undefined;
  const sessionToken = context?.token;

  if (name === ToolName.GET_USER_DETAILS) {
    if (!sessionToken) {
      throw new AuthenticationError("Authentication token is missing or invalid. Ensure the token is provided in the request context.");
    }

    // Get the Entra ID token from the session store
    const tokenData = tokenStore.getToken(sessionToken);
    const entraIdToken = tokenData.accessToken;

    const graphClient = Client.init({
      authProvider: (done) => {
        done(null, entraIdToken);
      }
    });

    const user = await graphClient.api('/me').get();

    // ... return user details ...
  }
});
```

**`auth/EntraIdServerAuthProvider.ts`**

This class handles the logic for:

- Redirecting the user to the Entra ID sign-in page.
- Exchanging the authorization code for an access token.
- Storing the tokens in the `tokenStore`.
- Refreshing the access token when it expires.

#### 3. How It All Works Together

1. When a user first tries to connect to the MCP server, the `requireBearerAuth` middleware will see that they don't have a valid session and will redirect them to the Entra ID sign-in page.
2. The user signs in with their Entra ID account.
3. Entra ID redirects the user back to the `/auth/callback` endpoint with an authorization code.
4. The server exchanges the code for an access token and a refresh token, stores them, and creates a session token which is sent to the client.
5. The client can now use this session token in the `Authorization` header for all future requests to the MCP server.
6. When the `getUserDetails` כשהכלי נקרא, הוא משתמש בטוקן הסשן כדי לאתר את טוקן הגישה של Entra ID ומשתמש בו לקריאה ל-Microsoft Graph API.

זרימה זו מורכבת יותר מזו של הלקוח הציבורי, אך נדרשת לנקודות קצה חשופות באינטרנט. מכיוון ששרתי MCP מרוחקים נגישים דרך האינטרנט הציבורי, הם צריכים אמצעי אבטחה חזקים יותר כדי להגן מפני גישה לא מורשית ותקיפות פוטנציאליות.

## שיטות אבטחה מומלצות  

- **תמיד השתמש ב-HTTPS**: הצפן את התקשורת בין הלקוח לשרת כדי להגן על הטוקנים מיירוט.  
- **יישם בקרת גישה מבוססת תפקידים (RBAC)**: אל תבדוק רק *אם* המשתמש אותת; בדוק *מה* הוא מורשה לעשות. ניתן להגדיר תפקידים ב-Entra ID ולבדוק אותם בשרת ה-MCP.  
- **נטר ובצע ביקורת**: רישום כל אירועי האימות כדי לזהות ולהגיב לפעילות חשודה.  
- **טפל בהגבלת קצב ותיעול**: Microsoft Graph ו-APIs אחרים מיישמים הגבלת קצב למניעת ניצול לרעה. יישם לוגיקה של backoff אקספוננציאלי וניסיונות חוזרים בשרת ה-MCP כדי להתמודד בצורה חלקה עם תגובות HTTP 429 (יותר מדי בקשות). שקול מטמון לנתונים שניגשים אליהם לעיתים קרובות כדי להפחית קריאות API.  
- **אחסון מאובטח של טוקנים**: אחסן טוקני גישה וטוקני רענון בצורה מאובטחת. עבור יישומים מקומיים, השתמש במנגנוני האחסון המאובטח של המערכת. עבור יישומי שרת, שקול להשתמש באחסון מוצפן או בשירותי ניהול מפתחות מאובטחים כמו Azure Key Vault.  
- **טיפול בתוקף טוקנים**: לטוקני גישה יש תוקף מוגבל. יישם רענון אוטומטי של טוקנים באמצעות טוקני רענון כדי לשמור על חווית משתמש רציפה ללא צורך באימות מחדש.  
- **שקול שימוש ב-Azure API Management**: בעוד שיישום אבטחה ישירות בשרת ה-MCP מעניק לך שליטה מדויקת, שערי API כמו Azure API Management יכולים לטפל בהרבה מהנושאים האלו אוטומטית, כולל אימות, הרשאות, הגבלת קצב וניטור. הם מספקים שכבת אבטחה מרכזית בין הלקוחות לשרתי ה-MCP שלך. לפרטים נוספים על שימוש בשערי API עם MCP, ראה את [Azure API Management Your Auth Gateway For MCP Servers](https://techcommunity.microsoft.com/blog/integrationsonazureblog/azure-api-management-your-auth-gateway-for-mcp-servers/4402690).

## נקודות מפתח  

- אבטחת שרת ה-MCP שלך חיונית להגנת הנתונים והכלים שלך.  
- Microsoft Entra ID מספק פתרון חזק וסקלאבילי לאימות והרשאות.  
- השתמש ב**לקוח ציבורי** עבור יישומים מקומיים וב**לקוח חסוי** עבור שרתים מרוחקים.  
- **Authorization Code Flow** היא האפשרות המאובטחת ביותר ליישומי ווב.

## תרגיל  

1. חשוב על שרת MCP שייתכן שתבנה. האם הוא יהיה שרת מקומי או מרוחק?  
2. בהתבסס על התשובה, האם תשתמש בלקוח ציבורי או חסוי?  
3. איזו הרשאה שרת ה-MCP שלך יבקש לביצוע פעולות מול Microsoft Graph?

## תרגילים מעשיים  

### תרגיל 1: רישום יישום ב-Entra ID  
גש לפורטל Microsoft Entra.  
רשום יישום חדש עבור שרת ה-MCP שלך.  
תעד את מזהה היישום (client ID) ומזהה הספריה (tenant ID).

### תרגיל 2: אבטחת שרת MCP מקומי (לקוח ציבורי)  
- עקוב אחר דוגמת הקוד לשילוב MSAL (Microsoft Authentication Library) לאימות משתמשים.  
- בדוק את זרימת האימות באמצעות קריאה לכלי MCP שמושך פרטי משתמש מ-Microsoft Graph.

### תרגיל 3: אבטחת שרת MCP מרוחק (לקוח חסוי)  
- רשום לקוח חסוי ב-Entra ID ויצר סוד לקוח (client secret).  
- קנפג את שרת ה-MCP שלך ב-Express.js לשימוש ב-Authorization Code Flow.  
- בדוק את נקודות הקצה המוגנות ואמת גישה מבוססת טוקן.

### תרגיל 4: יישום שיטות אבטחה מיטביות  
- אפשר HTTPS לשרת המקומי או המרוחק שלך.  
- יישם בקרת גישה מבוססת תפקידים (RBAC) בלוגיקת השרת.  
- הוסף טיפול בתוקף טוקנים ואחסון מאובטח שלהם.

## משאבים  

1. **MSAL Overview Documentation**  
   למד כיצד Microsoft Authentication Library (MSAL) מאפשרת רכישת טוקנים מאובטחת בפלטפורמות שונות:  
   [MSAL Overview on Microsoft Learn](https://learn.microsoft.com/en-gb/entra/msal/overview)

2. **Azure-Samples/mcp-auth-servers GitHub Repository**  
   מימושים לדוגמה של שרתי MCP המדגימים זרימות אימות:  
   [Azure-Samples/mcp-auth-servers on GitHub](https://github.com/Azure-Samples/mcp-auth-servers)

3. **Managed Identities for Azure Resources Overview**  
   הבן כיצד לבטל סודות באמצעות זהויות מנוהלות מוקצות למערכת או למשתמש:  
   [Managed Identities Overview on Microsoft Learn](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/)

4. **Azure API Management: Your Auth Gateway for MCP Servers**  
   מבט מעמיק על שימוש ב-APIM כשער OAuth2 מאובטח לשרתי MCP:  
   [Azure API Management Your Auth Gateway For MCP Servers](https://techcommunity.microsoft.com/blog/integrationsonazureblog/azure-api-management-your-auth-gateway-for-mcp-servers/4402690)

5. **Microsoft Graph Permissions Reference**  
   רשימה מקיפה של הרשאות מונחות ויישומיות עבור Microsoft Graph:  
   [Microsoft Graph Permissions Reference](https://learn.microsoft.com/zh-tw/graph/permissions-reference)

## תוצאות הלמידה  
בסיום הסעיף תוכל:

- להסביר מדוע אימות הוא קריטי לשרתי MCP ולזרימות עבודה של AI.  
- להגדיר ולקנפג אימות Entra ID לתרחישי שרתי MCP מקומיים ומרוחקים.  
- לבחור את סוג הלקוח המתאים (ציבורי או חסוי) בהתאם לפריסת השרת.  
- ליישם שיטות קידוד מאובטחות, כולל אחסון טוקנים והרשאות מבוססות תפקיד.  
- להגן בביטחון על שרת ה-MCP שלך וכליו מפני גישה לא מורשית.

## מה הלאה  

- [5.13 אינטגרציה של Model Context Protocol (MCP) עם Azure AI Foundry](../mcp-foundry-agent-integration/README.md)

**כתב ויתור**:  
מסמך זה תורגם באמצעות שירות תרגום מבוסס בינה מלאכותית [Co-op Translator](https://github.com/Azure/co-op-translator). למרות שאנו שואפים לדיוק, יש לקחת בחשבון כי תרגומים אוטומטיים עלולים להכיל שגיאות או אי-דיוקים. המסמך המקורי בשפת המקור שלו נחשב למקור הסמכותי. עבור מידע קריטי, מומלץ להשתמש בתרגום מקצועי אנושי. איננו אחראים לכל אי-הבנות או פרשנויות שגויות הנובעות משימוש בתרגום זה.