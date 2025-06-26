<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "9abe1d303ab126f9a8b87f03cebe5213",
  "translation_date": "2025-06-26T14:40:00+00:00",
  "source_file": "05-AdvancedTopics/mcp-security-entra/README.md",
  "language_code": "ko"
}
-->
# AI 워크플로우 보안: Model Context Protocol 서버용 Entra ID 인증

## 소개  
Model Context Protocol(MCP) 서버를 보호하는 것은 집의 현관문을 잠그는 것만큼 중요합니다. MCP 서버를 열어두면 도구와 데이터가 무단 접근에 노출되어 보안 침해로 이어질 수 있습니다. Microsoft Entra ID는 강력한 클라우드 기반 ID 및 접근 관리 솔루션을 제공하여, 권한이 있는 사용자와 애플리케이션만 MCP 서버와 상호작용할 수 있도록 돕습니다. 이 섹션에서는 Entra ID 인증을 사용해 AI 워크플로우를 안전하게 보호하는 방법을 배웁니다.

## 학습 목표  
이 섹션을 마치면 다음을 할 수 있습니다:

- MCP 서버 보안의 중요성을 이해합니다.  
- Microsoft Entra ID와 OAuth 2.0 인증의 기본 개념을 설명할 수 있습니다.  
- 공개 클라이언트와 기밀 클라이언트의 차이를 인지합니다.  
- 로컬(공개 클라이언트) 및 원격(기밀 클라이언트) MCP 서버 시나리오에서 Entra ID 인증을 구현합니다.  
- AI 워크플로우 개발 시 보안 모범 사례를 적용합니다.  

# AI 워크플로우 보안: Model Context Protocol 서버용 Entra ID 인증

집의 현관문을 잠그지 않고 내버려 두지 않듯이, MCP 서버도 누구나 접근할 수 있도록 열어두면 안 됩니다. AI 워크플로우를 안전하게 보호하는 것은 견고하고 신뢰할 수 있으며 안전한 애플리케이션을 만드는 데 필수적입니다. 이 장에서는 Microsoft Entra ID를 사용해 MCP 서버를 보호하고, 권한이 있는 사용자와 애플리케이션만 도구와 데이터에 접근할 수 있도록 하는 방법을 소개합니다.

## MCP 서버 보안이 중요한 이유

MCP 서버에 이메일 전송이나 고객 데이터베이스 접근 도구가 있다고 가정해 보세요. 보안이 취약한 서버라면 누구나 그 도구를 사용할 수 있어 무단 데이터 접근, 스팸 발송 또는 기타 악의적 행위가 발생할 수 있습니다.

인증을 구현하면 서버에 대한 모든 요청이 검증되어 요청을 하는 사용자나 애플리케이션의 신원을 확인할 수 있습니다. 이는 AI 워크플로우 보안에서 가장 중요하고 첫 번째 단계입니다.

## Microsoft Entra ID 소개

**Microsoft Entra ID**는 클라우드 기반 ID 및 접근 관리 서비스입니다. 애플리케이션을 위한 만능 보안 경비원이라고 생각하면 됩니다. 사용자 신원 확인(인증)과 권한 부여(사용자가 무엇을 할 수 있는지 결정하는 과정)를 처리합니다.

Entra ID를 사용하면:

- 사용자에게 안전한 로그인 환경을 제공합니다.  
- API와 서비스를 보호합니다.  
- 중앙에서 접근 정책을 관리할 수 있습니다.  

MCP 서버에서는 Entra ID가 누가 서버 기능에 접근할 수 있는지 관리하는 강력하고 신뢰받는 솔루션을 제공합니다.

---

## Entra ID 인증 작동 원리 이해하기

Entra ID는 **OAuth 2.0** 같은 공개 표준을 사용해 인증을 처리합니다. 세부 내용은 복잡할 수 있지만, 핵심 개념은 비유를 통해 쉽게 이해할 수 있습니다.

### OAuth 2.0 간단 소개: 발레 키

OAuth 2.0을 자동차 발레 서비스에 비유해 보겠습니다. 식당에 도착했을 때, 발레 파킹 직원에게 자동차의 마스터 키를 주지 않습니다. 대신, 제한된 권한이 부여된 **발레 키**를 줍니다. 이 키로는 차 시동을 걸고 문을 잠글 수 있지만, 트렁크나 글로브 박스는 열 수 없습니다.

이 비유에서:

- **당신**은 **사용자**입니다.  
- **당신의 차**는 도구와 데이터가 있는 **MCP 서버**입니다.  
- **발레 파킹 직원**은 **Microsoft Entra ID**입니다.  
- **주차 안내원**은 **MCP 클라이언트**(서버에 접근하려는 애플리케이션)입니다.  
- **발레 키**는 **액세스 토큰**입니다.  

액세스 토큰은 사용자가 로그인한 후 MCP 클라이언트가 Entra ID로부터 받는 보안 문자열입니다. 클라이언트는 이 토큰을 매 요청 시 MCP 서버에 제시합니다. 서버는 토큰을 검증해 요청이 합법적이며 클라이언트가 필요한 권한을 갖고 있는지 확인합니다. 이 과정에서 사용자의 실제 자격 증명(예: 비밀번호)을 다룰 필요가 없습니다.

### 인증 흐름

실제로는 다음과 같이 진행됩니다:

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

### Microsoft 인증 라이브러리(MSAL) 소개

코드 예제로 넘어가기 전에 중요한 구성 요소인 **Microsoft 인증 라이브러리(MSAL)**를 소개합니다.

MSAL은 Microsoft가 개발한 라이브러리로, 개발자가 인증을 쉽게 처리할 수 있도록 도와줍니다. 보안 토큰 처리, 로그인 관리, 세션 갱신 같은 복잡한 코드를 직접 작성할 필요 없이 MSAL이 이를 대신 처리합니다.

MSAL 사용을 권장하는 이유는:

- **안전성**: 업계 표준 프로토콜과 보안 모범 사례를 구현해 코드 취약점 위험을 줄입니다.  
- **개발 간소화**: OAuth 2.0과 OpenID Connect 프로토콜의 복잡성을 추상화하여 몇 줄의 코드로 강력한 인증을 추가할 수 있습니다.  
- **지속적 유지보수**: Microsoft가 보안 위협과 플랫폼 변화에 대응해 MSAL을 적극적으로 업데이트합니다.  

MSAL은 .NET, JavaScript/TypeScript, Python, Java, Go, iOS, Android 등 다양한 언어와 플랫폼을 지원해 기술 스택 전반에 걸쳐 일관된 인증 패턴을 사용할 수 있습니다.

MSAL에 대해 더 알고 싶다면 공식 [MSAL 개요 문서](https://learn.microsoft.com/entra/identity-platform/msal-overview)를 참고하세요.

---

## Entra ID로 MCP 서버 보호하기: 단계별 가이드

이제 로컬 MCP 서버(예: `stdio`) using Entra ID. This example uses a **public client**, which is suitable for applications running on a user's machine, like a desktop app or a local development server.

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
- **`AcquireTokenAsync` 메서드 사용) 보안 설정 방법을 살펴봅니다. 이 메서드는 먼저 조용히 토큰을 얻으려 시도합니다(이미 유효한 세션이 있으면 사용자가 다시 로그인할 필요가 없습니다). 조용한 토큰 획득에 실패하면 사용자가 직접 로그인하도록 요청합니다.

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
- **`GetUserDetailsFromGraph` tool**: This tool requires an instance of `AuthenticationService`. Before it does anything, it calls `authService.AcquireTokenAsync()`**를 호출해 유효한 액세스 토큰을 얻습니다. 인증에 성공하면 이 토큰으로 Microsoft Graph API를 호출해 사용자 정보를 가져옵니다.

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

#### 3. 전체 작동 방식

1. MCP 클라이언트가 `GetUserDetailsFromGraph` tool, the tool first calls `AcquireTokenAsync`.
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
- **`/auth/callback` 엔드포인트에 접근을 시도합니다. 이 엔드포인트는 사용자가 인증을 마친 후 Entra ID로부터 리디렉션을 처리합니다. 권한 코드를 액세스 토큰과 리프레시 토큰으로 교환합니다.

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

This file defines the tools that the MCP server provides. The `getUserDetails`** 도구는 이전 예제와 비슷하지만, 세션에서 액세스 토큰을 가져옵니다.

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
6. When the `getUserDetails`** 도구가 호출되면 세션 토큰으로 Entra ID 액세스 토큰을 조회하고, 이를 사용해 Microsoft Graph API를 호출합니다.

이 흐름은 공개 클라이언트 흐름보다 복잡하지만, 인터넷에 노출된 엔드포인트에는 필수적입니다. 원격 MCP 서버는 공용 인터넷에서 접근 가능하기 때문에 무단 접근과 잠재적 공격에 대비해 더 강력한 보안 조치가 필요합니다.

## 보안 모범 사례

- **항상 HTTPS 사용**: 클라이언트와 서버 간 통신을 암호화해 토큰 탈취를 방지합니다.  
- **역할 기반 접근 제어(RBAC) 구현**: 단순히 사용자가 인증되었는지 여부뿐 아니라 어떤 권한이 있는지 확인하세요. Entra ID에서 역할을 정의하고 MCP 서버에서 이를 검증할 수 있습니다.  
- **모니터링 및 감사**: 모든 인증 이벤트를 기록해 의심스러운 활동을 탐지하고 대응합니다.  
- **요청 제한 및 조절 처리**: Microsoft Graph 및 기타 API는 남용 방지를 위해 요청 제한을 적용합니다. MCP 서버에서 지수적 백오프와 재시도 로직을 구현해 HTTP 429(요청 과다) 응답을 우아하게 처리하세요. 자주 사용하는 데이터는 캐싱해 API 호출을 줄이는 것도 고려하세요.  
- **토큰 안전 저장**: 액세스 토큰과 리프레시 토큰은 안전하게 저장하세요. 로컬 애플리케이션은 시스템의 보안 저장소를, 서버 애플리케이션은 암호화 저장소나 Azure Key Vault 같은 보안 키 관리 서비스를 활용하세요.  
- **토큰 만료 처리**: 액세스 토큰은 유효 기간이 제한적입니다. 리프레시 토큰을 사용해 자동으로 토큰을 갱신해 재인증 없이 원활한 사용자 경험을 유지하세요.  
- **Azure API Management 사용 고려**: MCP 서버 내에서 직접 보안을 구현하면 세밀한 제어가 가능하지만, Azure API Management 같은 API 게이트웨이는 인증, 권한 부여, 요청 제한, 모니터링 등 많은 보안 문제를 자동으로 처리해줍니다. 클라이언트와 MCP 서버 사이에 중앙 집중식 보안 계층을 제공합니다. MCP와 API 게이트웨이 활용에 관한 자세한 내용은 [Azure API Management Your Auth Gateway For MCP Servers](https://techcommunity.microsoft.com/blog/integrationsonazureblog/azure-api-management-your-auth-gateway-for-mcp-servers/4402690) 문서를 참고하세요.

## 주요 내용 정리

- MCP 서버 보안은 데이터와 도구를 보호하는 데 필수적입니다.  
- Microsoft Entra ID는 인증과 권한 부여를 위한 강력하고 확장 가능한 솔루션을 제공합니다.  
- 로컬 애플리케이션에는 **공개 클라이언트**, 원격 서버에는 **기밀 클라이언트**를 사용하세요.  
- 웹 애플리케이션에는 가장 안전한 **권한 부여 코드 흐름(Authorization Code Flow)**을 사용하세요.  

## 연습 문제

1. 당신이 만들고자 하는 MCP 서버는 로컬 서버인가요, 원격 서버인가요?  
2. 답변에 따라 공개 클라이언트와 기밀 클라이언트 중 어떤 것을 사용할 건가요?  
3. Microsoft Graph에서 작업을 수행하기 위해 MCP 서버가 요청할 권한은 무엇인가요?  

## 실습 과제

### 과제 1: Entra ID에 애플리케이션 등록하기  
Microsoft Entra 포털로 이동하세요.  
MCP 서버용 새 애플리케이션을 등록하세요.  
애플리케이션(클라이언트) ID와 디렉터리(테넌트) ID를 기록하세요.

### 과제 2: 로컬 MCP 서버 보안 설정(공개 클라이언트)  
코드 예제를 따라 MSAL(Microsoft Authentication Library)을 통합해 사용자 인증을 구현하세요.  
Microsoft Graph에서 사용자 정보를 가져오는 MCP 도구를 호출해 인증 흐름을 테스트하세요.

### 과제 3: 원격 MCP 서버 보안 설정(기밀 클라이언트)  
Entra ID에 기밀 클라이언트를 등록하고 클라이언트 비밀을 생성하세요.  
Express.js MCP 서버를 권한 부여 코드 흐름으로 구성하세요.  
보호된 엔드포인트를 테스트하고 토큰 기반 접근이 제대로 동작하는지 확인하세요.

### 과제 4: 보안 모범 사례 적용하기  
로컬 또는 원격 서버에 HTTPS를 활성화하세요.  
서버 로직에 역할 기반 접근 제어(RBAC)를 구현하세요.  
토큰 만료 처리 및 안전한 토큰 저장을 추가하세요.

## 참고 자료

1. **MSAL 개요 문서**  
   Microsoft Authentication Library(MSAL)가 플랫폼 전반에서 안전한 토큰 획득을 어떻게 지원하는지 알아보기:  
   [Microsoft Learn의 MSAL 개요](https://learn.microsoft.com/en-gb/entra/msal/overview)

2. **Azure-Samples/mcp-auth-servers GitHub 저장소**  
   인증 흐름을 보여주는 MCP 서버 참조 구현:  
   [Azure-Samples/mcp-auth-servers GitHub](https://github.com/Azure-Samples/mcp-auth-servers)

3. **Azure 리소스용 관리 ID 개요**  
   시스템 또는 사용자 할당 관리 ID를 사용해 비밀 정보를 없애는 방법:  
   [Microsoft Learn의 관리 ID 개요](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/)

4. **Azure API Management: MCP 서버용 인증 게이트웨이**  
   MCP 서버용 안전한 OAuth2 게이트웨이로 APIM 활용 심층 가이드:  
   [Azure API Management Your Auth Gateway For MCP Servers](https://techcommunity.microsoft.com/blog/integrationsonazureblog/azure-api-management-your-auth-gateway-for-mcp-servers/4402690)

5. **Microsoft Graph 권한 참조**  
   Microsoft Graph의 위임 및 애플리케이션 권한 목록:  
   [Microsoft Graph 권한 참조](https://learn.microsoft.com/zh-tw/graph/permissions-reference)

## 학습 성과  
이 섹션을 완료하면 다음을 할 수 있습니다:

- MCP 서버와 AI 워크플로우에서 인증이 왜 중요한지 설명할 수 있습니다.  
- 로컬 및 원격 MCP 서버 시나리오에 맞게 Entra ID 인증을 설정하고 구성할 수 있습니다.  
- 서버 배포 환경에 따라 적절한 클라이언트 유형(공개 또는 기밀)을 선택할 수 있습니다.  
- 토큰 저장 및 역할 기반 권한 부여 등 안전한 코딩 관행을 구현할 수 있습니다.  
- MCP 서버와 도구를 무단 접근으로부터 자신 있게 보호할 수 있습니다.

## 다음 단계  

- [6. 커뮤니티 기여](../../06-CommunityContributions/README.md)

**면책 조항**:  
이 문서는 AI 번역 서비스 [Co-op Translator](https://github.com/Azure/co-op-translator)를 사용하여 번역되었습니다. 정확성을 위해 노력하고 있으나, 자동 번역에는 오류나 부정확성이 포함될 수 있음을 유의하시기 바랍니다. 원본 문서의 원어 버전을 권위 있는 출처로 간주해야 합니다. 중요한 정보의 경우 전문적인 인간 번역을 권장합니다. 본 번역 사용으로 인한 오해나 잘못된 해석에 대해 당사는 책임을 지지 않습니다.