<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "0abf26a6c4dbe905d5d49ccdc0ccfe92",
  "translation_date": "2025-06-26T16:17:49+00:00",
  "source_file": "05-AdvancedTopics/mcp-security-entra/README.md",
  "language_code": "fa"
}
-->
# ایمن‌سازی جریان‌های کاری هوش مصنوعی: احراز هویت Entra ID برای سرورهای پروتکل مدل کانتکست

## مقدمه  
ایمن نگه داشتن سرور پروتکل مدل کانتکست (MCP) به اندازه قفل کردن درب ورودی خانه‌تان اهمیت دارد. باز گذاشتن سرور MCP شما، ابزارها و داده‌هایتان را در معرض دسترسی غیرمجاز قرار می‌دهد که می‌تواند منجر به نفوذهای امنیتی شود. مایکروسافت Entra ID راهکاری قدرتمند و مبتنی بر ابر برای مدیریت هویت و دسترسی ارائه می‌دهد که تضمین می‌کند تنها کاربران و برنامه‌های مجاز می‌توانند با سرور MCP شما تعامل داشته باشند. در این بخش، خواهید آموخت چگونه با استفاده از احراز هویت Entra ID، جریان‌های کاری هوش مصنوعی خود را محافظت کنید.

## اهداف آموزشی  
تا پایان این بخش، قادر خواهید بود:

- اهمیت ایمن‌سازی سرورهای MCP را درک کنید.  
- اصول پایه‌ای Microsoft Entra ID و احراز هویت OAuth 2.0 را توضیح دهید.  
- تفاوت بین کلاینت‌های عمومی و محرمانه را تشخیص دهید.  
- احراز هویت Entra ID را در سناریوهای سرور MCP محلی (کلاینت عمومی) و از راه دور (کلاینت محرمانه) پیاده‌سازی کنید.  
- بهترین شیوه‌های امنیتی را در توسعه جریان‌های کاری هوش مصنوعی به کار ببندید.

## امنیت و MCP  

همانطور که درب ورودی خانه‌تان را باز نمی‌گذارید، نباید سرور MCP خود را به روی همه باز بگذارید. ایمن‌سازی جریان‌های کاری هوش مصنوعی برای ساخت برنامه‌هایی مقاوم، قابل اعتماد و امن ضروری است. این فصل شما را با استفاده از Microsoft Entra ID برای محافظت از سرورهای MCP آشنا می‌کند تا تنها کاربران و برنامه‌های مجاز بتوانند به ابزارها و داده‌های شما دسترسی داشته باشند.

## چرا امنیت برای سرورهای MCP مهم است  

فرض کنید سرور MCP شما ابزاری دارد که می‌تواند ایمیل ارسال کند یا به پایگاه داده مشتریان دسترسی داشته باشد. اگر سرور بدون امنیت باشد، هر کسی ممکن است از آن ابزار استفاده کند که منجر به دسترسی غیرمجاز به داده‌ها، ارسال اسپم یا فعالیت‌های مخرب دیگر می‌شود.

با پیاده‌سازی احراز هویت، اطمینان حاصل می‌کنید که هر درخواست به سرور شما تأیید می‌شود و هویت کاربر یا برنامه درخواست‌کننده مشخص می‌شود. این اولین و مهم‌ترین گام در ایمن‌سازی جریان‌های کاری هوش مصنوعی شماست.

## معرفی Microsoft Entra ID  

[**Microsoft Entra ID**](https://adoption.microsoft.com/microsoft-security/entra/) یک سرویس مدیریت هویت و دسترسی مبتنی بر ابر است. آن را مانند یک نگهبان امنیتی همه‌جانبه برای برنامه‌های خود تصور کنید. این سرویس فرآیند پیچیده تأیید هویت کاربران (احراز هویت) و تعیین مجوزهای آن‌ها (مجوزدهی) را مدیریت می‌کند.

با استفاده از Entra ID می‌توانید:

- ورود امن کاربران را فعال کنید.  
- از APIها و سرویس‌ها محافظت کنید.  
- سیاست‌های دسترسی را از یک محل مرکزی مدیریت کنید.

برای سرورهای MCP، Entra ID راهکاری قدرتمند و مورد اعتماد برای مدیریت دسترسی به قابلیت‌های سرور فراهم می‌کند.

---

## درک جادوی کارکرد احراز هویت Entra ID  

Entra ID از استانداردهای باز مانند **OAuth 2.0** برای مدیریت احراز هویت استفاده می‌کند. هرچند جزئیات ممکن است پیچیده باشد، مفهوم اصلی ساده است و می‌توان آن را با یک مثال تشریح کرد.

### معرفی ساده OAuth 2.0: کلید پارکینگ  

OAuth 2.0 را مانند یک سرویس پارکینگ برای خودروی خود در نظر بگیرید. وقتی به رستوران می‌رسید، کلید اصلی خودرو را به پارکبان نمی‌دهید. بلکه یک **کلید پارکینگ** می‌دهید که دسترسی محدودی دارد — می‌تواند خودرو را روشن کند و درها را قفل کند، اما نمی‌تواند صندوق عقب یا داشبورد را باز کند.

در این تشبیه:

- **شما** کاربر هستید.  
- **خودروی شما** سرور MCP با ابزارها و داده‌های ارزشمند است.  
- **پارکبان** همان Microsoft Entra ID است.  
- **کارمند پارکینگ** کلاینت MCP (برنامه‌ای که می‌خواهد به سرور دسترسی پیدا کند) است.  
- **کلید پارکینگ** همان Access Token است.

توکن دسترسی رشته‌ای امن از متن است که کلاینت MCP پس از ورود شما از Entra ID دریافت می‌کند. سپس کلاینت این توکن را با هر درخواست به سرور MCP ارائه می‌دهد. سرور می‌تواند توکن را تأیید کند تا اطمینان حاصل شود که درخواست معتبر است و کلاینت مجوزهای لازم را دارد، بدون اینکه نیاز باشد رمز عبور واقعی شما را مدیریت کند.

### روند احراز هویت  

روند کار به این شکل است:

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

### معرفی Microsoft Authentication Library (MSAL)  

قبل از ورود به کد، معرفی یک مؤلفه کلیدی ضروری است که در مثال‌ها مشاهده خواهید کرد: **Microsoft Authentication Library (MSAL)**.

MSAL کتابخانه‌ای است که توسط مایکروسافت توسعه یافته و فرآیند احراز هویت را برای توسعه‌دهندگان بسیار ساده‌تر می‌کند. به جای اینکه خودتان کد پیچیده مدیریت توکن‌های امنیتی، ورود کاربران و تازه‌سازی نشست‌ها را بنویسید، MSAL این کارها را بر عهده می‌گیرد.

استفاده از کتابخانه‌ای مانند MSAL به شدت توصیه می‌شود زیرا:

- **امن است:** پروتکل‌های استاندارد صنعتی و بهترین شیوه‌های امنیتی را پیاده‌سازی می‌کند و خطر آسیب‌پذیری در کد شما را کاهش می‌دهد.  
- **توسعه را ساده می‌کند:** پیچیدگی‌های OAuth 2.0 و OpenID Connect را پنهان می‌کند و به شما اجازه می‌دهد با چند خط کد احراز هویت قوی به برنامه خود اضافه کنید.  
- **به‌روزرسانی می‌شود:** مایکروسافت به طور فعال MSAL را نگهداری و به‌روزرسانی می‌کند تا تهدیدات امنیتی جدید و تغییرات پلتفرم را پوشش دهد.

MSAL از زبان‌ها و چارچوب‌های متنوعی مانند .NET، JavaScript/TypeScript، Python، Java، Go و پلتفرم‌های موبایل مانند iOS و Android پشتیبانی می‌کند. این یعنی می‌توانید الگوهای احراز هویت یکنواختی را در کل فناوری خود به کار ببرید.

برای اطلاعات بیشتر درباره MSAL، می‌توانید مستندات رسمی [بررسی کلی MSAL](https://learn.microsoft.com/entra/identity-platform/msal-overview) را مطالعه کنید.

---

## ایمن‌سازی سرور MCP با Entra ID: راهنمای گام‌به‌گام  

حالا بیایید قدم به قدم نحوه ایمن‌سازی یک سرور MCP محلی (که از طریق `stdio`) using Entra ID. This example uses a **public client**, which is suitable for applications running on a user's machine, like a desktop app or a local development server.

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
- **`AcquireTokenAsync` ارتباط برقرار می‌کند) را بررسی کنیم. این متد اصلی است که ابتدا تلاش می‌کند توکن را به صورت بی‌صدا دریافت کند (یعنی اگر کاربر قبلاً نشست معتبری داشته باشد، نیازی به ورود مجدد نیست). اگر نتواند توکن بی‌صدا بگیرد، از کاربر می‌خواهد به صورت تعاملی وارد شود.

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
- **`GetUserDetailsFromGraph` tool**: This tool requires an instance of `AuthenticationService`. Before it does anything, it calls `authService.AcquireTokenAsync()` برای گرفتن توکن دسترسی معتبر استفاده می‌کند. اگر احراز هویت موفق باشد، از این توکن برای فراخوانی Microsoft Graph API و دریافت جزئیات کاربر بهره می‌برد.

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

#### ۳. نحوه عملکرد کلی  

1. وقتی کلاینت MCP تلاش می‌کند تا `GetUserDetailsFromGraph` tool, the tool first calls `AcquireTokenAsync`.
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
- **`/auth/callback` را فراخوانی کند: این نقطه پایانی پس از ورود کاربر به Entra ID، ریدایرکت را مدیریت می‌کند و کد مجوز را به توکن دسترسی و توکن تازه‌سازی تبدیل می‌کند.

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

This file defines the tools that the MCP server provides. The `getUserDetails` ابزاری مشابه نمونه قبلی است اما توکن دسترسی را از نشست دریافت می‌کند.

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
6. When the `getUserDetails` زمانی که فراخوانی می‌شود، از توکن نشست برای یافتن توکن دسترسی Entra ID استفاده می‌کند و سپس با آن به Microsoft Graph API تماس می‌گیرد.

این روند پیچیده‌تر از جریان کلاینت عمومی است، اما برای نقاط پایانی قابل دسترس از طریق اینترنت ضروری است. از آنجا که سرورهای MCP از راه دور از طریق اینترنت عمومی قابل دسترسی هستند، به اقدامات امنیتی قوی‌تری برای محافظت در برابر دسترسی غیرمجاز و حملات احتمالی نیاز دارند.

## بهترین شیوه‌های امنیتی  

- **همیشه از HTTPS استفاده کنید:** ارتباط بین کلاینت و سرور را رمزنگاری کنید تا توکن‌ها در برابر رهگیری محافظت شوند.  
- **کنترل دسترسی مبتنی بر نقش (RBAC) را پیاده‌سازی کنید:** فقط بررسی نکنید که کاربر احراز هویت شده است، بلکه بررسی کنید چه کاری مجاز به انجام آن است. می‌توانید نقش‌ها را در Entra ID تعریف و در سرور MCP خود بررسی کنید.  
- **نظارت و حسابرسی کنید:** تمام رویدادهای احراز هویت را ثبت کنید تا بتوانید فعالیت‌های مشکوک را شناسایی و پاسخ دهید.  
- **محدودیت نرخ و مدیریت بار را رعایت کنید:** Microsoft Graph و سایر APIها محدودیت نرخ دارند تا از سوءاستفاده جلوگیری کنند. در سرور MCP خود، منطق تلاش مجدد با تأخیر افزایشی را پیاده کنید تا به خوبی پاسخ HTTP 429 (تعداد درخواست‌ها زیاد است) را مدیریت کند. همچنین، کش کردن داده‌های پر استفاده می‌تواند تعداد تماس‌های API را کاهش دهد.  
- **ذخیره امن توکن‌ها:** توکن‌های دسترسی و تازه‌سازی را به صورت امن ذخیره کنید. برای برنامه‌های محلی از مکانیزم‌های ذخیره امن سیستم استفاده کنید. برای برنامه‌های سروری، ذخیره رمزگذاری شده یا خدمات مدیریت کلید امن مانند Azure Key Vault را در نظر بگیرید.  
- **مدیریت انقضای توکن:** توکن‌های دسترسی مدت محدودی اعتبار دارند. با استفاده از توکن‌های تازه‌سازی، به صورت خودکار توکن‌ها را تازه کنید تا تجربه کاربری بدون نیاز به ورود مجدد حفظ شود.  
- **استفاده از Azure API Management را مد نظر داشته باشید:** در حالی که پیاده‌سازی امنیت مستقیماً در سرور MCP کنترل دقیق‌تری می‌دهد، دروازه‌های API مانند Azure API Management می‌توانند بسیاری از این نگرانی‌های امنیتی را به صورت خودکار مدیریت کنند، از جمله احراز هویت، مجوزدهی، محدودیت نرخ و نظارت. این‌ها یک لایه امنیتی متمرکز بین کلاینت‌ها و سرورهای MCP شما فراهم می‌کنند. برای جزئیات بیشتر در مورد استفاده از دروازه‌های API با MCP، بخش [Azure API Management Your Auth Gateway For MCP Servers](https://techcommunity.microsoft.com/blog/integrationsonazureblog/azure-api-management-your-auth-gateway-for-mcp-servers/4402690) را ببینید.

## نکات کلیدی  

- ایمن‌سازی سرور MCP برای حفاظت از داده‌ها و ابزارهای شما حیاتی است.  
- Microsoft Entra ID راهکاری قدرتمند و مقیاس‌پذیر برای احراز هویت و مجوزدهی ارائه می‌دهد.  
- برای برنامه‌های محلی از کلاینت **عمومی** و برای سرورهای از راه دور از کلاینت **محرمانه** استفاده کنید.  
- جریان **Authorization Code Flow** امن‌ترین گزینه برای برنامه‌های وب است.

## تمرین  

1. به سرور MCP که ممکن است بسازید فکر کنید. آیا سرور محلی است یا از راه دور؟  
2. بر اساس پاسخ، از کلاینت عمومی استفاده می‌کنید یا محرمانه؟  
3. سرور MCP شما برای انجام عملیات روی Microsoft Graph چه مجوزی درخواست خواهد کرد؟

## تمرین‌های عملی  

### تمرین ۱: ثبت یک برنامه در Entra ID  
به پرتال Microsoft Entra مراجعه کنید.  
یک برنامه جدید برای سرور MCP خود ثبت کنید.  
شناسه برنامه (client ID) و شناسه دایرکتوری (tenant ID) را یادداشت کنید.

### تمرین ۲: ایمن‌سازی یک سرور MCP محلی (کلاینت عمومی)  
- از مثال کد برای ادغام MSAL (کتابخانه احراز هویت مایکروسافت) جهت احراز هویت کاربران استفاده کنید.  
- روند احراز هویت را با فراخوانی ابزاری که جزئیات کاربر را از Microsoft Graph می‌گیرد، تست کنید.

### تمرین ۳: ایمن‌سازی یک سرور MCP از راه دور (کلاینت محرمانه)  
- یک کلاینت محرمانه در Entra ID ثبت و یک راز کلاینت ایجاد کنید.  
- سرور Express.js خود را برای استفاده از Authorization Code Flow پیکربندی کنید.  
- نقاط پایانی محافظت شده را تست و دسترسی مبتنی بر توکن را تأیید کنید.

### تمرین ۴: اعمال بهترین شیوه‌های امنیتی  
- HTTPS را برای سرور محلی یا از راه دور خود فعال کنید.  
- کنترل دسترسی مبتنی بر نقش (RBAC) را در منطق سرور پیاده‌سازی کنید.  
- مدیریت انقضای توکن و ذخیره امن توکن‌ها را اضافه کنید.

## منابع  

1. **مستندات مروری MSAL**  
   یاد بگیرید چگونه Microsoft Authentication Library (MSAL) امکان دریافت توکن امن را در پلتفرم‌های مختلف فراهم می‌کند:  
   [بررسی کلی MSAL در Microsoft Learn](https://learn.microsoft.com/en-gb/entra/msal/overview)

2. **مخزن GitHub Azure-Samples/mcp-auth-servers**  
   پیاده‌سازی‌های نمونه سرورهای MCP با جریان‌های احراز هویت:  
   [Azure-Samples/mcp-auth-servers در GitHub](https://github.com/Azure-Samples/mcp-auth-servers)

3. **مروری بر Managed Identities برای منابع Azure**  
   درک چگونگی حذف نیاز به اسرار با استفاده از شناسه‌های مدیریت‌شده سیستم یا کاربر:  
   [مروری بر Managed Identities در Microsoft Learn](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/)

4. **Azure API Management: دروازه احراز هویت شما برای سرورهای MCP**  
   بررسی عمیق استفاده از APIM به عنوان دروازه امن OAuth2 برای سرورهای MCP:  
   [Azure API Management Your Auth Gateway For MCP Servers](https://techcommunity.microsoft.com/blog/integrationsonazureblog/azure-api-management-your-auth-gateway-for-mcp-servers/4402690)

5. **فهرست مجوزهای Microsoft Graph**  
   فهرست جامع مجوزهای تفویض شده و برنامه‌ای برای Microsoft Graph:  
   [Microsoft Graph Permissions Reference](https://learn.microsoft.com/zh-tw/graph/permissions-reference)

## نتایج یادگیری  
پس از تکمیل این بخش، شما قادر خواهید بود:

- توضیح دهید چرا احراز هویت برای سرورهای MCP و جریان‌های کاری هوش مصنوعی حیاتی است.  
- احراز هویت Entra ID را برای سناریوهای سرور MCP محلی و از راه دور تنظیم و پیکربندی کنید.  
- نوع کلاینت مناسب (عمومی یا محرمانه) را بر اساس نحوه استقرار سرور خود انتخاب کنید.  
- بهترین شیوه‌های برنامه‌نویسی امن شامل ذخیره توکن و مجوزدهی مبتنی بر نقش را پیاده‌سازی کنید.  
- با اطمینان سرور MCP و ابزارهای آن را در برابر دسترسی غیرمجاز محافظت کنید.

## گام بعدی  

- [۶. مشارکت‌های جامعه](../../06-CommunityContributions/README.md)

**سلب مسئولیت**:  
این سند با استفاده از سرویس ترجمه ماشینی [Co-op Translator](https://github.com/Azure/co-op-translator) ترجمه شده است. در حالی که ما در تلاش برای دقت هستیم، لطفاً توجه داشته باشید که ترجمه‌های خودکار ممکن است حاوی اشتباهات یا نادرستی‌هایی باشند. سند اصلی به زبان بومی خود باید به عنوان منبع معتبر در نظر گرفته شود. برای اطلاعات حیاتی، ترجمه حرفه‌ای انسانی توصیه می‌شود. ما مسئول هیچ گونه سوء تفاهم یا برداشت نادرستی که از استفاده این ترجمه ناشی شود، نیستیم.