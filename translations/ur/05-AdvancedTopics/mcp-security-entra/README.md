<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "0abf26a6c4dbe905d5d49ccdc0ccfe92",
  "translation_date": "2025-06-26T16:18:24+00:00",
  "source_file": "05-AdvancedTopics/mcp-security-entra/README.md",
  "language_code": "ur"
}
-->
# AI ورک فلو کی حفاظت: ماڈل کانٹیکسٹ پروٹوکول سرورز کے لیے Entra ID تصدیق

## تعارف  
اپنے ماڈل کانٹیکسٹ پروٹوکول (MCP) سرور کو محفوظ بنانا اتنا ہی ضروری ہے جتنا اپنے گھر کا دروازہ بند کرنا۔ اگر آپ کا MCP سرور کھلا رہ جائے تو آپ کے ٹولز اور ڈیٹا غیر مجاز رسائی کے خطرے میں آ جاتے ہیں، جو سیکیورٹی خلاف ورزیوں کا باعث بن سکتا ہے۔ Microsoft Entra ID ایک مضبوط کلاؤڈ بیسڈ شناخت اور رسائی مینجمنٹ حل فراہم کرتا ہے، جو یقینی بناتا ہے کہ صرف مجاز صارفین اور ایپلیکیشنز ہی آپ کے MCP سرور کے ساتھ تعامل کر سکیں۔ اس سیکشن میں، آپ سیکھیں گے کہ Entra ID تصدیق کے ذریعے اپنے AI ورک فلو کو کیسے محفوظ بنایا جائے۔

## سیکھنے کے مقاصد  
اس سیکشن کے اختتام تک، آپ قادر ہوں گے کہ:

- MCP سرورز کو محفوظ بنانے کی اہمیت کو سمجھیں۔
- Microsoft Entra ID اور OAuth 2.0 تصدیق کی بنیادی باتوں کی وضاحت کریں۔
- عوامی اور خفیہ کلائنٹس میں فرق پہچانیں۔
- Entra ID تصدیق کو مقامی (عوامی کلائنٹ) اور دور دراز (خفیہ کلائنٹ) MCP سرور کے منظرناموں میں نافذ کریں۔
- AI ورک فلو کی تیاری میں سیکیورٹی کی بہترین مشقیں اپنائیں۔

## سیکیورٹی اور MCP  

جیسے آپ اپنے گھر کا دروازہ کھلا نہیں چھوڑتے، ویسے ہی آپ کو اپنے MCP سرور کو بھی ہر کسی کے لیے کھلا نہیں چھوڑنا چاہیے۔ اپنے AI ورک فلو کی حفاظت مضبوط، قابل اعتماد اور محفوظ ایپلیکیشنز بنانے کے لیے ضروری ہے۔ یہ باب آپ کو Microsoft Entra ID کے استعمال سے اپنے MCP سرورز کو محفوظ بنانے کا تعارف کرائے گا، تاکہ صرف مجاز صارفین اور ایپلیکیشنز ہی آپ کے ٹولز اور ڈیٹا تک رسائی حاصل کر سکیں۔

## MCP سرورز کے لیے سیکیورٹی کیوں ضروری ہے  

تصور کریں کہ آپ کے MCP سرور میں ایک ایسا ٹول ہے جو ای میل بھیج سکتا ہے یا کسٹمر ڈیٹا بیس تک رسائی حاصل کر سکتا ہے۔ اگر سرور غیر محفوظ ہو تو کوئی بھی اس ٹول کو استعمال کر سکتا ہے، جس سے غیر مجاز ڈیٹا تک رسائی، اسپیم یا دیگر نقصان دہ سرگرمیاں ہو سکتی ہیں۔

تصدیق کے نفاذ سے، آپ یقینی بناتے ہیں کہ ہر درخواست کی تصدیق کی جاتی ہے، یعنی درخواست کرنے والے صارف یا ایپلیکیشن کی شناخت کی تصدیق ہوتی ہے۔ یہ آپ کے AI ورک فلو کو محفوظ بنانے کا پہلا اور سب سے اہم قدم ہے۔

## Microsoft Entra ID کا تعارف  

[**Microsoft Entra ID**](https://adoption.microsoft.com/microsoft-security/entra/) ایک کلاؤڈ بیسڈ شناخت اور رسائی مینجمنٹ سروس ہے۔ اسے آپ اپنی ایپلیکیشنز کے لیے ایک یونیورسل سیکیورٹی گارڈ سمجھیں۔ یہ صارف کی شناخت کی تصدیق (authentication) اور ان کی اجازتوں کا تعین (authorization) کرنے کے پیچیدہ عمل کو سنبھالتا ہے۔

Entra ID کے استعمال سے آپ کر سکتے ہیں:

- صارفین کے لیے محفوظ سائن ان کو فعال کریں۔
- APIs اور سروسز کی حفاظت کریں۔
- رسائی کی پالیسیز کو مرکزی جگہ سے منظم کریں۔

MCP سرورز کے لیے، Entra ID ایک مضبوط اور قابل اعتماد حل فراہم کرتا ہے تاکہ یہ کنٹرول کیا جا سکے کہ کون آپ کے سرور کی صلاحیتوں تک رسائی حاصل کر سکتا ہے۔

---

## جادو کو سمجھنا: Entra ID تصدیق کیسے کام کرتی ہے  

Entra ID اوپن اسٹینڈرڈز جیسے **OAuth 2.0** کو تصدیق کے لیے استعمال کرتا ہے۔ اگرچہ تفصیلات پیچیدہ ہو سکتی ہیں، لیکن بنیادی تصور آسان ہے اور ایک مثال سے سمجھایا جا سکتا ہے۔

### OAuth 2.0 کا نرم تعارف: ویلیٹ کی

OAuth 2.0 کو آپ اپنی گاڑی کے لیے ویلیٹ سروس سمجھیں۔ جب آپ کسی ریستوراں پہنچتے ہیں، تو آپ ویلیٹ کو اپنی ماسٹر کی نہیں دیتے۔ اس کی بجائے، آپ اسے ایک **ویلیٹ کی** دیتے ہیں جس کی محدود اجازتیں ہوتی ہیں — یہ گاڑی کو اسٹارٹ کر سکتی ہے اور دروازے بند کر سکتی ہے، لیکن ٹرنک یا گلوز کمپارٹمنٹ نہیں کھول سکتی۔

اس مثال میں:

- **آپ** ہیں **صارف**۔
- **آپ کی گاڑی** ہے **MCP سرور** جس میں قیمتی ٹولز اور ڈیٹا ہے۔
- **ویلیٹ** ہے **Microsoft Entra ID**۔
- **پارکنگ اٹینڈنٹ** ہے **MCP کلائنٹ** (وہ ایپلیکیشن جو سرور تک رسائی کی کوشش کر رہی ہے)۔
- **ویلیٹ کی** ہے **Access Token**۔

Access token ایک محفوظ متن کی شکل ہے جو MCP کلائنٹ کو Entra ID سے سائن ان کے بعد ملتی ہے۔ کلائنٹ ہر درخواست کے ساتھ یہ ٹوکن MCP سرور کو پیش کرتا ہے۔ سرور اس ٹوکن کی تصدیق کر کے درخواست کی قانونی حیثیت اور کلائنٹ کی اجازتوں کی جانچ کرتا ہے، بغیر آپ کے اصل اسناد (جیسے پاس ورڈ) کو سنبھالے۔

### تصدیق کا عمل  

عملی طور پر یہ طریقہ کار کچھ یوں ہوتا ہے:

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

### Microsoft Authentication Library (MSAL) کا تعارف  

کوڈ میں جانے سے پہلے، ایک اہم جزو سے واقف ہونا ضروری ہے جو آپ مثالوں میں دیکھیں گے: **Microsoft Authentication Library (MSAL)**۔

MSAL ایک لائبریری ہے جو Microsoft نے تیار کی ہے تاکہ ڈویلپرز کے لیے تصدیق کا عمل آسان بنایا جا سکے۔ آپ کو سیکیورٹی ٹوکنز سنبھالنے، سائن ان مینج کرنے اور سیشن ریفریش کرنے کے پیچیدہ کوڈ لکھنے کی ضرورت نہیں پڑتی، کیونکہ MSAL یہ کام خود کرتا ہے۔

MSAL استعمال کرنے کی سفارش کی جاتی ہے کیونکہ:

- **یہ محفوظ ہے:** یہ انڈسٹری کے معیاری پروٹوکولز اور سیکیورٹی بہترین طریقوں کو نافذ کرتا ہے، جس سے آپ کے کوڈ میں کمزوریوں کا خطرہ کم ہوتا ہے۔
- **یہ ترقی کو آسان بناتا ہے:** OAuth 2.0 اور OpenID Connect کے پیچیدہ عمل کو چھپا دیتا ہے، جس سے آپ چند لائنوں کوڈ میں مضبوط تصدیق شامل کر سکتے ہیں۔
- **یہ برقرار رکھا جاتا ہے:** Microsoft MSAL کو فعال طور پر اپ ڈیٹ کرتا ہے تاکہ نئے سیکیورٹی خطرات اور پلیٹ فارم تبدیلیوں کا مقابلہ کیا جا سکے۔

MSAL مختلف زبانوں اور ایپلیکیشن فریم ورکس کی حمایت کرتا ہے، جیسے .NET، JavaScript/TypeScript، Python، Java، Go، اور موبائل پلیٹ فارمز جیسے iOS اور Android۔ اس کا مطلب ہے کہ آپ اپنے پورے ٹیکنالوجی اسٹیک میں یکساں تصدیقی نمونے استعمال کر سکتے ہیں۔

MSAL کے بارے میں مزید جاننے کے لیے، آپ سرکاری [MSAL overview documentation](https://learn.microsoft.com/entra/identity-platform/msal-overview) دیکھ سکتے ہیں۔

---

## Entra ID کے ذریعے اپنے MCP سرور کی حفاظت: مرحلہ وار رہنمائی  

اب، چلیں دیکھتے ہیں کہ مقامی MCP سرور کو کیسے محفوظ کیا جائے (جو `stdio`) using Entra ID. This example uses a **public client**, which is suitable for applications running on a user's machine, like a desktop app or a local development server.

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
- **`AcquireTokenAsync` کے ذریعے بات چیت کرتا ہے): یہ بنیادی طریقہ ہے۔ یہ پہلے خاموشی سے ٹوکن حاصل کرنے کی کوشش کرتا ہے (یعنی اگر صارف کے پاس پہلے سے فعال سیشن ہے تو دوبارہ سائن ان کی ضرورت نہیں ہوتی)۔ اگر خاموشی سے ٹوکن حاصل نہ ہو سکے، تو صارف کو انٹرایکٹو طور پر سائن ان کرنے کے لیے کہا جائے گا۔

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
- **`GetUserDetailsFromGraph` tool**: This tool requires an instance of `AuthenticationService`. Before it does anything, it calls `authService.AcquireTokenAsync()` ایک درست Access Token حاصل کرنے کے لیے استعمال ہوتا ہے۔ اگر تصدیق کامیاب ہو جائے، تو یہ ٹوکن Microsoft Graph API کو کال کرنے اور صارف کی تفصیلات حاصل کرنے کے لیے استعمال ہوتا ہے۔**

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

#### 3. یہ سب کیسے مل کر کام کرتا ہے  

1. جب MCP کلائنٹ `GetUserDetailsFromGraph` tool, the tool first calls `AcquireTokenAsync`.
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
- **`/auth/callback` اینڈپوائنٹ استعمال کرنے کی کوشش کرتا ہے: یہ اینڈپوائنٹ Entra ID سے صارف کی تصدیق کے بعد ری ڈائریکٹ کو ہینڈل کرتا ہے۔ یہ authorization code کو access token اور refresh token میں تبدیل کرتا ہے۔**

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

This file defines the tools that the MCP server provides. The `getUserDetails` ٹول پچھلے مثال کی طرح ہے، لیکن یہ سیشن سے access token حاصل کرتا ہے۔**

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
6. When the `getUserDetails` ٹول کال کیا جاتا ہے، یہ سیشن ٹوکن کو استعمال کر کے Entra ID access token تلاش کرتا ہے اور پھر Microsoft Graph API کو کال کرتا ہے۔**

یہ عمل عوامی کلائنٹ کے بہاؤ سے زیادہ پیچیدہ ہے، لیکن انٹرنیٹ پر دستیاب اینڈپوائنٹس کے لیے ضروری ہے۔ چونکہ دور دراز MCP سرورز عوامی انٹرنیٹ پر دستیاب ہوتے ہیں، انہیں غیر مجاز رسائی اور ممکنہ حملوں سے بچانے کے لیے مضبوط سیکیورٹی تدابیر کی ضرورت ہوتی ہے۔

## سیکیورٹی کی بہترین مشقیں  

- **ہمیشہ HTTPS استعمال کریں:** کلائنٹ اور سرور کے درمیان مواصلات کو انکرپٹ کریں تاکہ ٹوکنز کو روکنے سے بچایا جا سکے۔
- **رول بیسڈ ایکسس کنٹرول (RBAC) نافذ کریں:** صرف یہ نہ چیک کریں کہ صارف تصدیق شدہ ہے؛ یہ بھی دیکھیں کہ اسے کیا کرنے کی اجازت ہے۔ آپ Entra ID میں رولز تعریف کر سکتے ہیں اور انہیں MCP سرور میں چیک کر سکتے ہیں۔
- **مانیٹرنگ اور آڈٹ کریں:** تمام تصدیقی واقعات کو لاگ کریں تاکہ مشکوک سرگرمی کا پتہ چلایا جا سکے اور اس پر ردعمل دیا جا سکے۔
- **ریٹ لمٹنگ اور تھروٹلنگ کو سنبھالیں:** Microsoft Graph اور دیگر APIs ریٹ لمٹنگ نافذ کرتے ہیں تاکہ بدسلوکی کو روکا جا سکے۔ اپنے MCP سرور میں ایکسپونینشل بیک آف اور ریٹری لاجک نافذ کریں تاکہ HTTP 429 (Too Many Requests) کے جواب کو مناسب طریقے سے سنبھالا جا سکے۔ اکثر استعمال ہونے والے ڈیٹا کو کیش کرنے پر غور کریں تاکہ API کالز کم ہوں۔
- **ٹوکن اسٹوریج کو محفوظ بنائیں:** Access اور refresh tokens کو محفوظ طریقے سے ذخیرہ کریں۔ مقامی ایپلیکیشنز کے لیے، سسٹم کے محفوظ اسٹوریج میکانزم استعمال کریں۔ سرور ایپلیکیشنز کے لیے، انکرپٹڈ اسٹوریج یا محفوظ کی مینجمنٹ سروسز جیسے Azure Key Vault کا استعمال کریں۔
- **ٹوکن کی میعاد ختم ہونے کا انتظام:** Access tokens کی محدود مدت ہوتی ہے۔ بغیر دوبارہ تصدیق کے مسلسل تجربہ کے لیے refresh tokens کے ذریعے خودکار ٹوکن ریفریش نافذ کریں۔
- **Azure API Management کا استعمال غور کریں:** اگرچہ MCP سرور میں براہ راست سیکیورٹی نافذ کرنا آپ کو باریک بینی سے کنٹرول دیتا ہے، API گیٹ ویز جیسے Azure API Management خود بخود بہت سی سیکیورٹی تشویشات کو سنبھالتے ہیں، جن میں تصدیق، اجازت، ریٹ لمٹنگ اور مانیٹرنگ شامل ہیں۔ یہ آپ کے کلائنٹس اور MCP سرورز کے درمیان ایک مرکزی حفاظتی پرت فراہم کرتے ہیں۔ MCP کے لیے API گیٹ وے کے استعمال کی مزید تفصیلات کے لیے، ہمارا [Azure API Management Your Auth Gateway For MCP Servers](https://techcommunity.microsoft.com/blog/integrationsonazureblog/azure-api-management-your-auth-gateway-for-mcp-servers/4402690) دیکھیں۔

## اہم نکات  

- اپنے MCP سرور کی حفاظت آپ کے ڈیٹا اور ٹولز کی حفاظت کے لیے ناگزیر ہے۔
- Microsoft Entra ID تصدیق اور اجازت کے لیے ایک مضبوط اور قابل توسیع حل فراہم کرتا ہے۔
- مقامی ایپلیکیشنز کے لیے **عوامی کلائنٹ** اور دور دراز سرورز کے لیے **خفیہ کلائنٹ** استعمال کریں۔
- ویب ایپلیکیشنز کے لیے **Authorization Code Flow** سب سے محفوظ آپشن ہے۔

## مشق  

1. ایک MCP سرور کے بارے میں سوچیں جو آپ بنا سکتے ہیں۔ کیا یہ مقامی سرور ہوگا یا دور دراز سرور؟  
2. اپنے جواب کی بنیاد پر، کیا آپ عوامی یا خفیہ کلائنٹ استعمال کریں گے؟  
3. Microsoft Graph کے خلاف کارروائیوں کے لیے آپ کا MCP سرور کون سی اجازت طلب کرے گا؟  

## عملی مشقیں  

### مشق 1: Entra ID میں ایک ایپلیکیشن رجسٹر کریں  
Microsoft Entra پورٹل پر جائیں۔  
اپنے MCP سرور کے لیے ایک نئی ایپلیکیشن رجسٹر کریں۔  
Application (client) ID اور Directory (tenant) ID نوٹ کریں۔

### مشق 2: مقامی MCP سرور کو محفوظ بنائیں (عوامی کلائنٹ)  
- MSAL (Microsoft Authentication Library) کو صارف کی تصدیق کے لیے ضم کرنے کے لیے کوڈ کی مثال پر عمل کریں۔  
- Microsoft Graph سے صارف کی تفصیلات حاصل کرنے والے MCP ٹول کو کال کر کے تصدیق کے عمل کی جانچ کریں۔

### مشق 3: دور دراز MCP سرور کو محفوظ بنائیں (خفیہ کلائنٹ)  
- Entra ID میں ایک خفیہ کلائنٹ رجسٹر کریں اور کلائنٹ سیکریٹ بنائیں۔  
- اپنے Express.js MCP سرور کو Authorization Code Flow کے لیے ترتیب دیں۔  
- محفوظ اینڈپوائنٹس کی جانچ کریں اور ٹوکن کی بنیاد پر رسائی کی تصدیق کریں۔

### مشق 4: سیکیورٹی کی بہترین مشقیں اپنائیں  
- اپنے مقامی یا دور دراز سرور کے لیے HTTPS فعال کریں۔  
- سرور لاجک میں رول بیسڈ ایکسس کنٹرول (RBAC) نافذ کریں۔  
- ٹوکن کی میعاد ختم ہونے کا انتظام اور محفوظ ٹوکن اسٹوریج شامل کریں۔

## وسائل  

1. **MSAL Overview Documentation**  
   جانیں کہ Microsoft Authentication Library (MSAL) کس طرح مختلف پلیٹ فارمز پر محفوظ ٹوکن حاصل کرنے کی سہولت دیتی ہے:  
   [MSAL Overview on Microsoft Learn](https://learn.microsoft.com/en-gb/entra/msal/overview)

2. **Azure-Samples/mcp-auth-servers GitHub Repository**  
   MCP سرورز کی تصدیق کے بہاؤ کی مثالیں:  
   [Azure-Samples/mcp-auth-servers on GitHub](https://github.com/Azure-Samples/mcp-auth-servers)

3. **Managed Identities for Azure Resources Overview**  
   سسٹم یا صارف تفویض کردہ منیجڈ شناختوں کے ذریعے سیکریٹس کو ختم کرنے کا طریقہ:  
   [Managed Identities Overview on Microsoft Learn](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/)

4. **Azure API Management: Your Auth Gateway for MCP Servers**  
   MCP سرورز کے لیے APIM کو محفوظ OAuth2 گیٹ وے کے طور پر استعمال کرنے کی تفصیلی معلومات:  
   [Azure API Management Your Auth Gateway For MCP Servers](https://techcommunity.microsoft.com/blog/integrationsonazureblog/azure-api-management-your-auth-gateway-for-mcp-servers/4402690)

5. **Microsoft Graph Permissions Reference**  
   Microsoft Graph کے لیے تفویض شدہ اور ایپلیکیشن اجازتوں کی جامع فہرست:  
   [Microsoft Graph Permissions Reference](https://learn.microsoft.com/zh-tw/graph/permissions-reference)

## سیکھنے کے نتائج  
اس سیکشن کو مکمل کرنے کے بعد، آپ قابل ہوں گے کہ:

- MCP سرورز اور AI ورک فلو کے لیے تصدیق کی اہمیت کو واضح کریں۔  
- مقامی اور دور دراز MCP سرور کے منظرناموں کے لیے Entra ID تصدیق کو ترتیب اور نافذ کریں۔  
- اپنے سرور کی تعیناتی کی بنیاد پر مناسب کلائنٹ قسم (عوامی یا خفیہ) منتخب کریں۔  
- محفوظ کوڈنگ کی مشقیں نافذ کریں، بشمول ٹوکن اسٹوریج اور رول بیسڈ اجازت۔  
- اپنے MCP سرور اور اس کے ٹولز کو غیر مجاز رسائی سے مؤثر طریقے سے محفوظ بنائیں۔

## آگے کیا ہے  

- [6. کمیونٹی کی شراکتیں](../../06-CommunityContributions/README.md)

**دستخطی نوٹ**:  
یہ دستاویز AI ترجمہ سروس [Co-op Translator](https://github.com/Azure/co-op-translator) کے ذریعے ترجمہ کی گئی ہے۔ اگرچہ ہم درستگی کے لیے کوشاں ہیں، براہ کرم اس بات سے آگاہ رہیں کہ خودکار ترجمے میں غلطیاں یا عدم صحت ہو سکتی ہے۔ اصل دستاویز اپنی مادری زبان میں معتبر ماخذ سمجھی جانی چاہیے۔ اہم معلومات کے لیے پیشہ ور انسانی ترجمہ کی سفارش کی جاتی ہے۔ اس ترجمے کے استعمال سے پیدا ہونے والی کسی بھی غلط فہمی یا غلط تعبیر کی ذمہ داری ہم پر نہیں ہوگی۔