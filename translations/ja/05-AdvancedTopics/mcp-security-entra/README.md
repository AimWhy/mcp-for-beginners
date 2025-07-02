<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "6e562d7e5a77c8982da4aa8f762ad1d8",
  "translation_date": "2025-07-02T09:05:35+00:00",
  "source_file": "05-AdvancedTopics/mcp-security-entra/README.md",
  "language_code": "ja"
}
-->
# AIワークフローのセキュリティ強化：モデルコンテキストプロトコルサーバーのEntra ID認証

## はじめに  
モデルコンテキストプロトコル（MCP）サーバーのセキュリティは、自宅の玄関の鍵をかけるのと同じくらい重要です。MCPサーバーを開放したままにすると、ツールやデータが不正アクセスにさらされ、セキュリティ侵害につながる恐れがあります。Microsoft Entra IDは、クラウドベースの強力なアイデンティティとアクセス管理ソリューションを提供し、許可されたユーザーやアプリケーションだけがMCPサーバーとやり取りできるようにします。このセクションでは、Entra ID認証を使ってAIワークフローを保護する方法を学びます。

## 学習目標  
このセクションを終える頃には、以下ができるようになります。

- MCPサーバーのセキュリティの重要性を理解する。
- Microsoft Entra IDとOAuth 2.0認証の基本を説明できる。
- パブリッククライアントとコンフィデンシャルクライアントの違いを理解する。
- ローカル（パブリッククライアント）およびリモート（コンフィデンシャルクライアント）MCPサーバーシナリオでEntra ID認証を実装する。
- AIワークフロー開発時のセキュリティベストプラクティスを適用する。

## セキュリティとMCP

自宅の玄関の鍵をかけずに放置しないのと同様に、MCPサーバーを誰でもアクセスできる状態にしてはいけません。AIワークフローのセキュリティ確保は、堅牢で信頼できる安全なアプリケーションを構築するために不可欠です。本章では、Microsoft Entra IDを使ってMCPサーバーを保護し、許可されたユーザーとアプリケーションのみがツールやデータにアクセスできるようにする方法を紹介します。

## MCPサーバーにおけるセキュリティの重要性

例えば、MCPサーバーにメール送信や顧客データベースへのアクセスができるツールがあるとします。セキュリティが甘いサーバーでは、誰でもそのツールを使えてしまい、不正なデータアクセスやスパム、悪意ある行為につながる可能性があります。

認証を実装することで、サーバーへのすべてのリクエストが検証され、リクエストを行うユーザーやアプリケーションの身元が確認されます。これはAIワークフローのセキュリティ確保における最初で最も重要なステップです。

## Microsoft Entra IDの紹介

[**Microsoft Entra ID**](https://adoption.microsoft.com/microsoft-security/entra/)は、クラウドベースのアイデンティティおよびアクセス管理サービスです。アプリケーションのための万能なセキュリティガードのようなものと考えてください。ユーザーの身元確認（認証）や、ユーザーが何を許可されているか（認可）を扱う複雑な処理を代行します。

Entra IDを使うことで、以下が可能になります。

- ユーザーの安全なサインインを実現。
- APIやサービスを保護。
- アクセスポリシーを一元管理。

MCPサーバーにおいては、Entra IDが誰がサーバーの機能にアクセスできるかを管理するための信頼性の高いソリューションを提供します。

---

## 魔法の仕組み：Entra ID認証のしくみ

Entra IDは**OAuth 2.0**などのオープンスタンダードを使って認証を処理します。詳細は複雑ですが、基本的な考え方はシンプルで、例え話で理解できます。

### OAuth 2.0のやさしい紹介：バレットキーの例え

OAuth 2.0は車のバレットサービスのようなものです。レストランに着いたとき、あなたはマスターキーをバレットに渡すわけではありません。代わりに、制限付きの**バレットキー**を渡します。これは車を始動させてドアをロックできますが、トランクやグローブボックスは開けられません。

この例での対応は以下の通りです。

- **あなた**は**ユーザー**。
- **あなたの車**は貴重なツールやデータを持つ**MCPサーバー**。
- **バレット**は**Microsoft Entra ID**。
- **パーキングアテンダント**は**MCPクライアント**（サーバーにアクセスしようとするアプリケーション）。
- **バレットキー**は**アクセストークン**。

アクセストークンは、ユーザーがサインインした後にMCPクライアントがEntra IDから受け取る安全な文字列です。クライアントはこのトークンをサーバーへの各リクエストに添えて送信し、サーバーはトークンを検証してリクエストの正当性や必要な権限があるかを確認します。これにより、パスワードなどの実際の資格情報を扱う必要がなくなります。

### 認証の流れ

実際のプロセスは次のように進みます。

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

### Microsoft Authentication Library (MSAL)の紹介

コード例に入る前に、重要なコンポーネントである**Microsoft Authentication Library (MSAL)**を紹介します。

MSALはMicrosoftが開発したライブラリで、認証処理を開発者にとってずっと簡単にします。セキュリティトークンの管理やサインイン、セッションの更新などの複雑なコードを書く代わりに、MSALがそれらを担います。

MSALを使うことが強く推奨される理由は以下の通りです。

- **安全性**：業界標準のプロトコルとセキュリティベストプラクティスを実装しており、コードの脆弱性リスクを減らします。
- **開発の簡素化**：OAuth 2.0やOpenID Connectの複雑さを抽象化し、数行のコードで堅牢な認証をアプリに追加できます。
- **メンテナンス**：Microsoftが積極的に保守・更新を行い、新たな脅威やプラットフォームの変化に対応しています。

MSALは.NET、JavaScript/TypeScript、Python、Java、Go、iOSやAndroidなど多様な言語やプラットフォームに対応しており、技術スタック全体で一貫した認証パターンを利用できます。

MSALの詳細は公式の[MSAL概要ドキュメント](https://learn.microsoft.com/entra/identity-platform/msal-overview)をご覧ください。

---

## Entra IDでMCPサーバーを保護する：ステップバイステップガイド

ここからは、ローカルMCPサーバー（`stdio`) using Entra ID. This example uses a **public client**, which is suitable for applications running on a user's machine, like a desktop app or a local development server.

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
- **`AcquireTokenAsync`**：これはコアメソッドです。最初にサイレントにトークンを取得しようとします（すでに有効なセッションがあればユーザーは再サインイン不要）。サイレント取得ができなければ、ユーザーにインタラクティブなサインインを促します。

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
- **`GetUserDetailsFromGraph` tool**: This tool requires an instance of `AuthenticationService`. Before it does anything, it calls `authService.AcquireTokenAsync()`で有効なアクセストークンを取得し、認証に成功するとMicrosoft Graph APIを呼び出してユーザー情報を取得します。

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

#### 3. これらが連携する仕組み

1. MCPクライアントが`GetUserDetailsFromGraph` tool, the tool first calls `AcquireTokenAsync`.
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
- **`/auth/callback`**にアクセスしようとします。このエンドポイントはユーザーが認証後にEntra IDからのリダイレクトを処理し、認可コードをアクセストークンとリフレッシュトークンに交換します。

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

This file defines the tools that the MCP server provides. The `getUserDetails`ツールは前の例と似ていますが、アクセストークンをセッションから取得します。

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
6. When the `getUserDetails`ツールが呼ばれると、セッションのトークンを使ってEntra IDのアクセストークンを取得し、それを使ってMicrosoft Graph APIを呼び出します。

このフローはパブリッククライアントの流れより複雑ですが、インターネットに公開されるエンドポイントでは必須です。リモートMCPサーバーはパブリックインターネット経由でアクセスされるため、不正アクセスや攻撃から守るためにより強力なセキュリティ対策が必要です。

## セキュリティベストプラクティス

- **常にHTTPSを使用する**：クライアントとサーバー間の通信を暗号化し、トークンの盗聴を防ぎます。
- **ロールベースアクセス制御（RBAC）を実装する**：ユーザーが認証されているかだけでなく、何が許可されているかをチェックします。Entra IDでロールを定義し、MCPサーバーでそれを確認しましょう。
- **監視と監査を行う**：すべての認証イベントをログに記録し、不審な活動を検知・対応できるようにします。
- **レート制限とスロットリングに対応する**：Microsoft GraphなどのAPIは悪用防止のためレート制限を実施しています。HTTP 429（リクエスト過多）応答を受けた際は指数的バックオフやリトライロジックを実装し、頻繁にアクセスするデータはキャッシュを検討しましょう。
- **トークンの安全な保管**：アクセストークンやリフレッシュトークンは安全に保管します。ローカルアプリケーションではシステムの安全なストレージを使い、サーバーアプリケーションでは暗号化ストレージやAzure Key Vaultなどの安全なキー管理サービスを利用しましょう。
- **トークンの有効期限管理**：アクセストークンは有効期限があります。リフレッシュトークンを使って自動的にトークンを更新し、ユーザーが再認証なしでシームレスに利用できるようにします。
- **Azure API Managementの利用を検討する**：MCPサーバーに直接セキュリティを実装することで細かい制御は可能ですが、Azure API ManagementのようなAPIゲートウェイは認証、認可、レート制限、監視など多くのセキュリティ課題を自動で処理し、クライアントとMCPサーバー間のセキュリティレイヤーを一元化します。MCPでAPIゲートウェイを使う詳細は[Azure API Management Your Auth Gateway For MCP Servers](https://techcommunity.microsoft.com/blog/integrationsonazureblog/azure-api-management-your-auth-gateway-for-mcp-servers/4402690)をご覧ください。

## まとめ

- MCPサーバーのセキュリティは、データやツールを守るために不可欠です。
- Microsoft Entra IDは認証と認可のための強力でスケーラブルなソリューションを提供します。
- ローカルアプリケーションには**パブリッククライアント**を、リモートサーバーには**コンフィデンシャルクライアント**を使い分けましょう。
- Webアプリケーションには最も安全な**認可コードフロー**を利用します。

## 演習

1. あなたが構築しようとするMCPサーバーはローカルサーバーですか、それともリモートサーバーですか？
2. その答えに基づいて、パブリッククライアントとコンフィデンシャルクライアントのどちらを使いますか？
3. Microsoft Graphに対してどのような権限をMCPサーバーに要求させますか？

## ハンズオン演習

### 演習1：Entra IDにアプリケーションを登録する  
Microsoft Entraポータルにアクセスし、MCPサーバー用の新しいアプリケーションを登録します。  
アプリケーション（クライアント）IDとディレクトリ（テナント）IDを控えましょう。

### 演習2：ローカルMCPサーバーを保護する（パブリッククライアント）  
- MSAL（Microsoft Authentication Library）を統合してユーザー認証を実装します。  
- Microsoft Graphからユーザー情報を取得するMCPツールを使って認証フローをテストします。

### 演習3：リモートMCPサーバーを保護する（コンフィデンシャルクライアント）  
- Entra IDでコンフィデンシャルクライアントを登録し、クライアントシークレットを作成します。  
- Express.jsのMCPサーバーを認可コードフローで設定します。  
- 保護されたエンドポイントをテストし、トークンベースのアクセスを確認します。

### 演習4：セキュリティベストプラクティスを適用する  
- ローカルまたはリモートサーバーでHTTPSを有効にします。  
- サーバーのロジックにロールベースアクセス制御（RBAC）を実装します。  
- トークンの有効期限管理と安全な保管を追加します。

## 参考資料

1. **MSAL概要ドキュメント**  
   Microsoft Authentication Library (MSAL)がプラットフォーム横断で安全なトークン取得を可能にする仕組み：  
   [MSAL Overview on Microsoft Learn](https://learn.microsoft.com/en-gb/entra/msal/overview)

2. **Azure-Samples/mcp-auth-servers GitHubリポジトリ**  
   認証フローを示すMCPサーバーのリファレンス実装：  
   [Azure-Samples/mcp-auth-servers on GitHub](https://github.com/Azure-Samples/mcp-auth-servers)

3. **AzureリソースのマネージドID概要**  
   シークレットを使わずにシステムまたはユーザー割り当てマネージドIDを利用する方法：  
   [Managed Identities Overview on Microsoft Learn](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/)

4. **Azure API Management: MCPサーバーの認証ゲートウェイ**  
   MCPサーバーのOAuth2ゲートウェイとしてAPIMを使う方法の詳細：  
   [Azure API Management Your Auth Gateway For MCP Servers](https://techcommunity.microsoft.com/blog/integrationsonazureblog/azure-api-management-your-auth-gateway-for-mcp-servers/4402690)

5. **Microsoft Graph権限リファレンス**  
   Microsoft Graphの委任権限とアプリケーション権限の包括的リスト：  
   [Microsoft Graph Permissions Reference](https://learn.microsoft.com/zh-tw/graph/permissions-reference)

## 学習成果  
このセクションを終えた時点で、以下ができるようになります。

- MCPサーバーとAIワークフローにおける認証の重要性を説明できる。
- ローカルおよびリモートMCPサーバーシナリオでEntra ID認証を設定・構成できる。
- サーバーの展開形態に応じて適切なクライアントタイプ（パブリックまたはコンフィデンシャル）を選択できる。
- トークン保管やロールベース認可などの安全なコーディングプラクティスを実装できる。
- MCPサーバーとそのツールを不正アクセスから確実に守

**免責事項**:  
本書類はAI翻訳サービス[Co-op Translator](https://github.com/Azure/co-op-translator)を使用して翻訳されました。正確性を期しておりますが、自動翻訳には誤りや不正確な部分が含まれる可能性があります。原文の言語によるオリジナル文書が正式な情報源とみなされます。重要な情報については、専門の人間による翻訳を推奨いたします。本翻訳の使用により生じた誤解や解釈の相違について、当方は一切の責任を負いかねます。