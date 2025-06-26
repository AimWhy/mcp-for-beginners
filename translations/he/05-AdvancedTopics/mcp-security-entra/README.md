<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "0abf26a6c4dbe905d5d49ccdc0ccfe92",
  "translation_date": "2025-06-26T16:34:51+00:00",
  "source_file": "05-AdvancedTopics/mcp-security-entra/README.md",
  "language_code": "he"
}
-->
# אבטחת זרימות עבודה של בינה מלאכותית: אימות Entra ID עבור שרתי פרוטוקול הקשר של מודלים

## מבוא  
אבטחת שרת ה-Model Context Protocol (MCP) שלך חשובה לא פחות מלהנעל את דלת הבית. השארת שרת ה-MCP פתוח חושפת את הכלים והנתונים שלך לגישה לא מורשית, שעלולה להוביל להפרות אבטחה. Microsoft Entra ID מספק פתרון חזק לניהול זהויות וגישה מבוסס ענן, שעוזר להבטיח שרק משתמשים ויישומים מורשים יוכלו לתקשר עם שרת ה-MCP שלך. בחלק זה תלמד כיצד להגן על זרימות העבודה של הבינה המלאכותית שלך באמצעות אימות Entra ID.

## מטרות הלמידה  
בסיום חלק זה תוכל:

- להבין את חשיבות אבטחת שרתי MCP.  
- להסביר את היסודות של Microsoft Entra ID ואימות OAuth 2.0.  
- להבחין בין לקוחות ציבוריים ללקוחות חסויים.  
- ליישם אימות Entra ID בתרחישים של שרתי MCP מקומיים (לקוחות ציבוריים) ומרוחקים (לקוחות חסויים).  
- ליישם שיטות אבטחה מיטביות בפיתוח זרימות עבודה של בינה מלאכותית.

## אבטחה ו-MCP  

כמו שלא היית משאיר את דלת הבית שלך פתוחה, כך אסור להשאיר את שרת ה-MCP פתוח לגישה חופשית. אבטחת זרימות העבודה של הבינה המלאכותית חיונית לבניית יישומים חזקים, אמינים ובטוחים. פרק זה יציג כיצד להשתמש ב-Microsoft Entra ID כדי לאבטח את שרתי ה-MCP שלך, ולהבטיח שרק משתמשים ויישומים מורשים יוכלו לגשת לכלים ולנתונים שלך.

## מדוע אבטחה חשובה לשרתי MCP  

תאר לעצמך ששרת ה-MCP שלך כולל כלי שיכול לשלוח אימיילים או לגשת למסד נתונים של לקוחות. שרת לא מאובטח יאפשר לכל אחד להשתמש בכלי הזה, מה שעלול להוביל לגישה לא מורשית לנתונים, לספאם או לפעילויות זדוניות אחרות.

על ידי יישום אימות, אתה מוודא שכל בקשה לשרת שלך מאומתת, ומאשרת את זהות המשתמש או היישום המבצע את הבקשה. זו השלב הראשון והחשוב ביותר באבטחת זרימות העבודה של הבינה המלאכותית שלך.

## מבוא ל-Microsoft Entra ID  

[**Microsoft Entra ID**](https://adoption.microsoft.com/microsoft-security/entra/) היא שירות ניהול זהויות וגישה מבוסס ענן. תחשוב עליו כשומר אבטחה אוניברסלי ליישומים שלך. השירות מטפל בתהליך המורכב של אימות זהויות המשתמשים (Authentication) וקביעת ההרשאות שלהם (Authorization).

באמצעות Entra ID תוכל:

- לאפשר התחברות מאובטחת למשתמשים.  
- להגן על APIs ושירותים.  
- לנהל מדיניות גישה ממקום מרכזי.

עבור שרתי MCP, Entra ID מספק פתרון אמין ומקובל לניהול מי יכול לגשת ליכולות של השרת.

---

## הבנת הקסם: איך עובד אימות Entra ID  

Entra ID משתמש בסטנדרטים פתוחים כמו **OAuth 2.0** לטיפול באימות. למרות שהפרטים עשויים להיות מורכבים, הרעיון המרכזי פשוט וניתן להבין אותו באמצעות אנלוגיה.

### הקדמה עדינה ל-OAuth 2.0: מפתח הוולט  
תחשוב על OAuth 2.0 כשירות וולט למכונית שלך. כשאתה מגיע למסעדה, אינך נותן לוולט את המפתח הראשי שלך. במקום זאת, אתה נותן לו **מפתח וולט** שמוגבל בהרשאות — הוא יכול להניע את המכונית ולנעול את הדלתות, אך לא לפתוח את תא המטען או את תא הכפפות.

באנלוגיה זו:

- **אתה** הוא ה-**משתמש**.  
- **המכונית שלך** היא ה-**שרת MCP** עם הכלים והנתונים היקרים שלו.  
- ה-**וולט** הוא **Microsoft Entra ID**.  
- ה-**חניין החניה** הוא ה-**לקוח MCP** (היישום שמנסה לגשת לשרת).  
- ה-**מפתח הוולט** הוא ה-**Access Token**.

אסימון הגישה הוא מחרוזת טקסט מאובטחת שהלקוח מקבל מ-Entra ID לאחר ההתחברות שלך. הלקוח מציג אסימון זה לשרת MCP בכל בקשה. השרת יכול לאמת את האסימון כדי לוודא שהבקשה חוקית ושהלקוח מורשה, וכל זאת מבלי לטפל בסיסמאות או פרטי ההתחברות שלך.

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

MSAL היא ספרייה שפותחה על ידי Microsoft שמקלה משמעותית על מפתחים בטיפול באימות. במקום שתכתוב את כל הקוד המורכב לטיפול באסימוני אבטחה, ניהול התחברויות ורענון סשנים, MSAL עושה את העבודה הקשה עבורך.

שימוש בספרייה כמו MSAL מומלץ מאוד כי:

- **היא מאובטחת:** מיישמת פרוטוקולים ותהליכי אבטחה סטנדרטיים בתעשייה, ומפחיתה סיכונים לפגיעויות בקוד שלך.  
- **מפשטת את הפיתוח:** מסתירה את המורכבות של פרוטוקולי OAuth 2.0 ו-OpenID Connect, ומאפשרת לך להוסיף אימות חזק ליישום שלך בכמה שורות קוד בלבד.  
- **מתוחזקת:** מיקרוסופט מעדכנת ומשפרת את MSAL באופן שוטף כדי להתמודד עם איומי אבטחה חדשים ושינויים בפלטפורמות.

MSAL תומכת במגוון שפות ומסגרות עבודה, כולל .NET, JavaScript/TypeScript, Python, Java, Go ופלטפורמות מובייל כמו iOS ואנדרואיד. משמעות הדבר היא שתוכל להשתמש בדפוסי אימות עקביים בכל טכנולוגיות הפיתוח שלך.

למידע נוסף על MSAL, ניתן לעיין בתיעוד הרשמי [MSAL overview documentation](https://learn.microsoft.com/entra/identity-platform/msal-overview).

---

## אבטחת שרת MCP שלך עם Entra ID: מדריך שלב-אחר-שלב  

כעת נעבור כיצד לאבטח שרת MCP מקומי (אשר מתקשר דרך `stdio`) using Entra ID. This example uses a **public client**, which is suitable for applications running on a user's machine, like a desktop app or a local development server.

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
- **`AcquireTokenAsync`**: זוהי השיטה המרכזית. היא מנסה תחילה לקבל אסימון באופן שקט (ללא צורך בהתחברות מחודשת אם כבר קיימת סשן תקף). אם לא ניתן לקבל אסימון בשקט, המשתמש יתבקש להתחבר באופן אינטראקטיבי.

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
- **`GetUserDetailsFromGraph` tool**: This tool requires an instance of `AuthenticationService`. Before it does anything, it calls `authService.AcquireTokenAsync()` כדי לקבל אסימון גישה תקף. אם האימות מצליח, הוא משתמש באסימון לקרוא ל-Microsoft Graph API ולהביא את פרטי המשתמש.

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

1. כאשר לקוח MCP מנסה להשתמש ב-`GetUserDetailsFromGraph` tool, the tool first calls `AcquireTokenAsync`.
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
- **`/auth/callback`**: נקודת קצה זו מטפלת בהפניה מ-Entra ID לאחר שהמשתמש התחבר. היא מחליפה את קוד האישור באסימון גישה ואסימון רענון.

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

This file defines the tools that the MCP server provides. The `getUserDetails` הכלי דומה לזה שבדוגמה הקודמת, אך מקבל את אסימון הגישה מהסשן.

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
6. When the `getUserDetails` כאשר הכלי נקרא, הוא משתמש באסימון הסשן כדי למצוא את אסימון הגישה של Entra ID ואז משתמש בו לקריאה ל-Microsoft Graph API.

הזרימה הזו מורכבת יותר מזו של הלקוח הציבורי, אך נדרשת לנקודות קצה הפונות לאינטרנט. מכיוון ששרתי MCP מרוחקים נגישים דרך האינטרנט הציבורי, הם זקוקים לאמצעי אבטחה חזקים יותר כדי להגן מפני גישה לא מורשית ותקיפות פוטנציאליות.

## שיטות עבודה מומלצות לאבטחה  

- **השתמש תמיד ב-HTTPS**: הצפן את התקשורת בין הלקוח לשרת כדי להגן על האסימונים מפני חטיפה.  
- **יישם בקרת גישה מבוססת תפקידים (RBAC)**: אל תבדוק רק *אם* המשתמש מאומת; בדוק *מה* הוא מורשה לעשות. ניתן להגדיר תפקידים ב-Entra ID ולבדוק אותם בשרת ה-MCP.  
- **נטר ובצע ביקורת**: רשם את כל אירועי האימות כדי לזהות ולהגיב לפעילות חשודה.  
- **טפל במגבלות קצב ו-throttling**: Microsoft Graph ו-APIs אחרים מיישמים מגבלות קצב למניעת ניצול לרעה. יישם לוגיקת exponential backoff ו-retry בשרת ה-MCP כדי להתמודד בצורה חלקה עם תגובות HTTP 429 (Too Many Requests). שקול להשתמש במטמון לנתונים הנגישים לעיתים קרובות כדי להפחית קריאות API.  
- **אחסן אסימונים בצורה מאובטחת**: אחסן את אסימוני הגישה ואסימוני הרענון בצורה בטוחה. עבור יישומים מקומיים, השתמש במנגנוני אחסון מאובטחים של המערכת. עבור יישומי שרת, שקול שימוש באחסון מוצפן או בשירותי ניהול מפתחות מאובטחים כמו Azure Key Vault.  
- **טפל בתוקף האסימון**: לאסימוני גישה יש תוקף מוגבל. יישם רענון אוטומטי של אסימונים באמצעות אסימוני רענון כדי לשמור על חוויית משתמש רציפה ללא צורך באימות חוזר.  
- **שקול שימוש ב-Azure API Management**: למרות שיישום אבטחה ישירות בשרת ה-MCP נותן לך שליטה מדויקת, שערי API כמו Azure API Management יכולים לטפל ברוב נושאי האבטחה אוטומטית, כולל אימות, הרשאות, הגבלת קצב ומעקב. הם מספקים שכבת אבטחה מרכזית שממוקמת בין הלקוחות לשרתי MCP שלך. לפרטים נוספים על שימוש בשערי API עם MCP, ראה [Azure API Management Your Auth Gateway For MCP Servers](https://techcommunity.microsoft.com/blog/integrationsonazureblog/azure-api-management-your-auth-gateway-for-mcp-servers/4402690).

## נקודות מרכזיות  

- אבטחת שרת ה-MCP שלך חיונית להגנה על הנתונים והכלים שלך.  
- Microsoft Entra ID מספק פתרון חזק ומדרג לניהול אימות והרשאות.  
- השתמש ב-**לקוח ציבורי** עבור יישומים מקומיים וב-**לקוח חסוי** עבור שרתים מרוחקים.  
- **Authorization Code Flow** היא האפשרות המאובטחת ביותר ליישומי רשת.

## תרגיל  

1. חשוב על שרת MCP שאתה עשוי לבנות. האם הוא יהיה מקומי או מרוחק?  
2. בהתבסס על התשובה, האם תשתמש בלקוח ציבורי או חסוי?  
3. איזו הרשאה ידרוש שרת ה-MCP שלך כדי לבצע פעולות מול Microsoft Graph?

## תרגילים מעשיים  

### תרגיל 1: רישום יישום ב-Entra ID  
גש לפורטל Microsoft Entra.  
רשום יישום חדש עבור שרת ה-MCP שלך.  
רשום את מזהה היישום (client ID) ואת מזהה התיקייה (tenant ID).

### תרגיל 2: אבטחת שרת MCP מקומי (לקוח ציבורי)  
- עקוב אחר דוגמת הקוד לשילוב MSAL (Microsoft Authentication Library) לאימות משתמשים.  
- בדוק את זרימת האימות על ידי קריאה לכלי MCP שמביא פרטי משתמש מ-Microsoft Graph.

### תרגיל 3: אבטחת שרת MCP מרוחק (לקוח חסוי)  
- רשם לקוח חסוי ב-Entra ID ויצר סוד לקוח (client secret).  
- קבע את תצורת שרת ה-Express.js MCP לשימוש ב-Authorization Code Flow.  
- בדוק את נקודות הקצה המוגנות ואמת גישה מבוססת אסימון.

### תרגיל 4: יישום שיטות עבודה מומלצות לאבטחה  
- אפשר HTTPS בשרת המקומי או המרוחק שלך.  
- יישם בקרת גישה מבוססת תפקידים (RBAC) בלוגיקת השרת.  
- הוסף טיפול בתוקף אסימון ואחסון מאובטח של אסימונים.

## משאבים  

1. **תיעוד סקירה של MSAL**  
   למד כיצד Microsoft Authentication Library (MSAL) מאפשרת רכישת אסימונים מאובטחת בפלטפורמות שונות:  
   [סקירת MSAL ב-Microsoft Learn](https://learn.microsoft.com/en-gb/entra/msal/overview)

2. **מאגר GitHub של Azure-Samples/mcp-auth-servers**  
   יישומים לדוגמה של שרתי MCP המדגימים זרימות אימות:  
   [Azure-Samples/mcp-auth-servers ב-GitHub](https://github.com/Azure-Samples/mcp-auth-servers)

3. **סקירה של Managed Identities עבור משאבי Azure**  
   הבן כיצד לבטל סודות באמצעות זהויות מנוהלות שמוקצות למערכת או למשתמש:  
   [סקירת Managed Identities ב-Microsoft Learn](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/)

4. **Azure API Management: שער האימות שלך לשרתי MCP**  
   סקירה מעמיקה של שימוש ב-APIM כשער OAuth2 מאובטח לשרתי MCP:  
   [Azure API Management Your Auth Gateway For MCP Servers](https://techcommunity.microsoft.com/blog/integrationsonazureblog/azure-api-management-your-auth-gateway-for-mcp-servers/4402690)

5. **רפרנס הרשאות Microsoft Graph**  
   רשימה מקיפה של הרשאות מונפקות ויישומיות עבור Microsoft Graph:  
   [רפרנס הרשאות Microsoft Graph](https://learn.microsoft.com/zh-tw/graph/permissions-reference)

## תוצאות למידה  
בסיום חלק זה תוכל:

- להסביר מדוע אימות הוא קריטי עבור שרתי MCP וזרימות עבודה של בינה מלאכותית.  
- להגדיר ולהגדיר אימות Entra ID עבור תרחישי שרתי MCP מקומיים ומרוחקים.  
- לבחור את סוג הלקוח המתאים (ציבורי או חסוי) בהתאם לפריסת השרת שלך.  
- ליישם שיטות קידוד מאובטחות, כולל אחסון אסימונים והרשאות מבוססות תפקידים.  
- להגן בביטחון על שרת ה-MCP שלך וכליו מפני גישה לא מורשית.

## מה הלאה  

- [6. תרומות מהקהילה](../../06-CommunityContributions/README.md)

**כתב ויתור**:  
מסמך זה תורגם באמצעות שירות תרגום מבוסס בינה מלאכותית [Co-op Translator](https://github.com/Azure/co-op-translator). למרות שאנו שואפים לדיוק, יש לקחת בחשבון שתרגומים אוטומטיים עלולים להכיל שגיאות או אי-דיוקים. המסמך המקורי בשפתו המקורית צריך להיחשב למקור הסמכותי. למידע קריטי מומלץ להשתמש בתרגום מקצועי של אדם. אנו לא נושאים באחריות לכל אי הבנה או פרשנות שגויה הנובעת משימוש בתרגום זה.