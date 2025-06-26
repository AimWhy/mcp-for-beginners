<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "9abe1d303ab126f9a8b87f03cebe5213",
  "translation_date": "2025-06-26T14:42:29+00:00",
  "source_file": "05-AdvancedTopics/mcp-security-entra/README.md",
  "language_code": "ne"
}
-->
# AI वर्कफ्लोज़ सुरक्षित पार्नुहोस्: Model Context Protocol सर्भरहरूको लागि Entra ID प्रमाणीकरण

## परिचय  
तपाईंको Model Context Protocol (MCP) सर्भर सुरक्षित गर्नु तपाईंको घरको मुख्य ढोका लक गर्नु जत्तिकै महत्त्वपूर्ण छ। तपाईंको MCP सर्भर खुला छ भने, तपाईंका उपकरण र डाटा अनधिकृत पहुँचमा पर्न सक्छन्, जसले सुरक्षा उल्लङ्घन निम्त्याउन सक्छ। Microsoft Entra ID एक बलियो क्लाउड-आधारित पहिचान र पहुँच व्यवस्थापन समाधान हो, जसले सुनिश्चित गर्छ कि केवल अधिकृत प्रयोगकर्ता र अनुप्रयोगहरू मात्र तपाईंको MCP सर्भरसँग अन्तरक्रिया गर्न सक्छन्। यस भागमा, तपाईं Entra ID प्रमाणीकरण प्रयोग गरेर तपाईंका AI वर्कफ्लोज़ कसरी सुरक्षित गर्ने सिक्नुहुनेछ।

## सिकाइका उद्देश्यहरू  
यस भागको अन्त्यसम्म तपाईं सक्षम हुनुहुनेछ:

- MCP सर्भरहरू सुरक्षित गर्ने महत्त्व बुझ्न।
- Microsoft Entra ID र OAuth 2.0 प्रमाणीकरणका आधारभूत कुरा व्याख्या गर्न।
- सार्वजनिक र गोप्य क्लाइन्टबीचको फरक चिन्न।
- स्थानीय (सार्वजनिक क्लाइन्ट) र रिमोट (गोप्य क्लाइन्ट) MCP सर्भर परिदृश्यहरूमा Entra ID प्रमाणीकरण लागू गर्न।
- AI वर्कफ्लोज़ विकास गर्दा सुरक्षा सर्वोत्तम अभ्यासहरू प्रयोग गर्न।

# AI वर्कफ्लोज़ सुरक्षित पार्नुहोस्: Model Context Protocol सर्भरहरूको लागि Entra ID प्रमाणीकरण

जसरी तपाईं आफ्नो घरको मुख्य ढोका अनलक्ड छोड्नुहुन्न, त्यसैगरी तपाईंले आफ्नो MCP सर्भर सबैका लागि खुला राख्नु हुँदैन। तपाईंका AI वर्कफ्लोज़हरूलाई सुरक्षित पार्नु बलियो, विश्वसनीय, र सुरक्षित अनुप्रयोगहरू निर्माण गर्न अत्यावश्यक छ। यस अध्यायले तपाईंलाई Microsoft Entra ID प्रयोग गरेर MCP सर्भरहरू कसरी सुरक्षित गर्ने भन्ने परिचय दिनेछ, जसले सुनिश्चित गर्छ कि केवल अधिकृत प्रयोगकर्ता र अनुप्रयोगहरू मात्र तपाईंका उपकरण र डाटासँग अन्तरक्रिया गर्न सक्छन्।

## MCP सर्भरहरूको लागि सुरक्षा किन आवश्यक छ

कल्पना गर्नुहोस् कि तपाईंको MCP सर्भरमा एउटा उपकरण छ जुन इमेल पठाउन वा ग्राहक डाटाबेस पहुँच गर्न सक्छ। यदि सर्भर असुरक्षित छ भने, जो कोहीले त्यो उपकरण प्रयोग गर्न सक्छ, जसले अनधिकृत डाटा पहुँच, स्प्याम, वा अन्य दुष्ट गतिविधिहरू निम्त्याउन सक्छ।

प्रमाणीकरण लागू गरेर, तपाईं सुनिश्चित गर्नुहुन्छ कि सर्भरमा आउने प्रत्येक अनुरोध प्रमाणित छ, जसले अनुरोध गर्ने प्रयोगकर्ता वा अनुप्रयोगको पहिचान पुष्टि गर्छ। यो तपाईंका AI वर्कफ्लोज़हरूलाई सुरक्षित पार्ने पहिलो र सबैभन्दा महत्वपूर्ण कदम हो।

## Microsoft Entra ID परिचय

**Microsoft Entra ID** एक क्लाउड-आधारित पहिचान र पहुँच व्यवस्थापन सेवा हो। यसलाई तपाईंको अनुप्रयोगहरूको लागि एक सार्वभौमिक सुरक्षा गार्डको रूपमा सोच्न सक्नुहुन्छ। यसले प्रयोगकर्ता पहिचान (प्रमाणीकरण) जाँच्ने र उनीहरूले के गर्न सक्छन् भनेर निर्धारण गर्ने (अधिकृत) जटिल प्रक्रियालाई सम्हाल्छ।

Entra ID प्रयोग गरेर तपाईं:

- प्रयोगकर्ताहरूका लागि सुरक्षित साइन-इन सक्षम गर्न सक्नुहुन्छ।
- API र सेवाहरू सुरक्षित गर्न सक्नुहुन्छ।
- पहुँच नीतिहरूलाई केन्द्रिय स्थानबाट व्यवस्थापन गर्न सक्नुहुन्छ।

MCP सर्भरहरूका लागि, Entra ID एक बलियो र विश्वसनीय समाधान हो जसले तपाईंको सर्भरमा को पहुँच पाउँछ भनेर व्यवस्थापन गर्छ।

---

## जादू बुझ्नुहोस्: Entra ID प्रमाणीकरण कसरी काम गर्छ

Entra ID प्रमाणीकरणका लागि खुला मानकहरू जस्तै **OAuth 2.0** प्रयोग गर्छ। यद्यपि विवरणहरू जटिल हुन सक्छन्, यसको मूल अवधारणा सरल छ र एउटा उपमा मार्फत बुझ्न सकिन्छ।

### OAuth 2.0 को सरल परिचय: भ्यालेट कुञ्जी

OAuth 2.0 लाई तपाईंको कारको लागि भ्यालेट सेवा जस्तो सोच्नुहोस्। जब तपाईं रेस्टुरेन्ट पुग्नुहुन्छ, तपाईंले आफ्नो मास्टर कुञ्जी भ्यालेटलाई दिनुहुन्न। यसको सट्टा, तपाईं एउटा **भ्यालेट कुञ्जी** दिनुहुन्छ जसले सीमित अधिकारहरू दिन्छ—कार सुरु गर्न र ढोका लक गर्न सक्छ, तर ट्रंक वा ग्लोभ कम्पार्टमेन्ट खोल्न सक्दैन।

यस उपमामा:

- **तपाईं** हुनुहुन्छ **प्रयोगकर्ता**।
- **तपाईंको कार** हो **MCP सर्भर** जसमा मूल्यवान उपकरण र डाटा छन्।
- **भ्यालेट** हो **Microsoft Entra ID**।
- **पार्किङ अटेन्डेन्ट** हो **MCP क्लाइन्ट** (सर्भर पहुँच गर्न खोज्ने अनुप्रयोग)।
- **भ्यालेट कुञ्जी** हो **Access Token**।

Access token एउटा सुरक्षित टेक्स्ट स्ट्रिङ हो जुन MCP क्लाइन्टले तपाईं साइन इन गरेपछि Entra ID बाट प्राप्त गर्छ। क्लाइन्टले यो टोकन प्रत्येक अनुरोधमा MCP सर्भरलाई प्रस्तुत गर्छ। सर्भरले टोकन प्रमाणित गरेर अनुरोध वैध छ कि छैन र क्लाइन्टसँग आवश्यक अनुमति छ कि छैन भनेर जाँच गर्छ, र तपाईंका वास्तविक प्रमाणहरू (जस्तै पासवर्ड) कहिल्यै प्रयोग गर्दैन।

### प्रमाणीकरण प्रवाह

व्यावहारिक रूपमा प्रक्रिया यसरी काम गर्छ:

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

### Microsoft Authentication Library (MSAL) परिचय

कोडमा जाने अघि, एउटा महत्वपूर्ण कम्पोनेन्ट परिचय गराउन आवश्यक छ: **Microsoft Authentication Library (MSAL)**।

MSAL Microsoft द्वारा विकास गरिएको एउटा लाइब्रेरी हो जसले विकासकर्ताहरूलाई प्रमाणीकरण सजिलो बनाउँछ। तपाईंलाई सुरक्षा टोकनहरू व्यवस्थापन, साइन-इन प्रक्रिया, र सत्र ताजा पार्ने जटिल कोड लेख्नु नपरोस् भनेर MSAL ले काम गर्छ।

MSAL प्रयोग गर्न सुझाव दिइन्छ किनभने:

- **यो सुरक्षित छ:** यसले उद्योग-मानक प्रोटोकल र सुरक्षा सर्वोत्तम अभ्यासहरू लागू गर्छ, जसले तपाईंको कोडमा कमजोरीको जोखिम घटाउँछ।
- **यसले विकासलाई सजिलो बनाउँछ:** OAuth 2.0 र OpenID Connect प्रोटोकलहरूको जटिलता लुकाएर, तपाईंलाई केवल केही लाइन कोडमा बलियो प्रमाणीकरण थप्न अनुमति दिन्छ।
- **यो मर्मतसम्भार हुन्छ:** Microsoft ले नयाँ सुरक्षा खतराहरू र प्लेटफर्म परिवर्तनहरूलाई सम्बोधन गर्न MSAL लाई सक्रिय रूपमा अपडेट गर्छ।

MSAL धेरै भाषाहरू र एप्लिकेसन फ्रेमवर्कहरूमा समर्थन गर्दछ, जस्तै .NET, JavaScript/TypeScript, Python, Java, Go, र मोबाइल प्लेटफर्महरू (iOS, Android)। यसले तपाईंलाई पुरै टेक्नोलोजी स्ट्याकमा एकसमान प्रमाणीकरण ढाँचा प्रयोग गर्न अनुमति दिन्छ।

MSAL बारे थप जान्न, तपाईंले आधिकारिक [MSAL अवलोकन कागजात](https://learn.microsoft.com/entra/identity-platform/msal-overview) हेर्न सक्नुहुन्छ।

---

## Entra ID प्रयोग गरेर तपाईंको MCP सर्भर सुरक्षित पार्ने चरण-दर-चरण मार्गदर्शन

अब, स्थानीय MCP सर्भर (जसले `stdio`) using Entra ID. This example uses a **public client**, which is suitable for applications running on a user's machine, like a desktop app or a local development server.

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
- **`AcquireTokenAsync` प्रयोग गर्छ) कसरी सुरक्षित गर्ने हेरौं: यो मुख्य विधि हो। यो पहिले टोकन शान्तिपूर्वक प्राप्त गर्न प्रयास गर्छ (यदि प्रयोगकर्तासँग वैध सत्र छ भने पुनः साइन इन गर्नु पर्दैन)। यदि शान्त टोकन प्राप्त गर्न सकिँदैन भने, प्रयोगकर्तालाई अन्तरक्रियात्मक रूपमा साइन इन गर्न आग्रह गरिन्छ।

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
- **`GetUserDetailsFromGraph` tool**: This tool requires an instance of `AuthenticationService`. Before it does anything, it calls `authService.AcquireTokenAsync()` प्रयोग गरेर मान्य पहुँच टोकन प्राप्त गर्छ। यदि प्रमाणीकरण सफल भयो भने, यो टोकन प्रयोग गरेर Microsoft Graph API कल गरी प्रयोगकर्ताको विवरण ल्याउँछ।

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

#### ३. सबै कुरा कसरी सँगै काम गर्छ

1. जब MCP क्लाइन्टले `GetUserDetailsFromGraph` tool, the tool first calls `AcquireTokenAsync`.
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
- **`/auth/callback` लाई प्रयोग गर्न खोज्छ: यो अन्त बिन्दु Entra ID बाट प्रयोगकर्ताले प्रमाणीकरण गरेपछि रिडाइरेक्टलाई ह्यान्डल गर्छ। यसले अधिकृत कोडलाई पहुँच टोकन र रिफ्रेस टोकनमा बदल्छ।

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

This file defines the tools that the MCP server provides. The `getUserDetails` उपकरण पहिलेको उदाहरण जस्तै छ, तर यसले सत्रबाट पहुँच टोकन प्राप्त गर्छ।

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
6. When the `getUserDetails` उपकरण बोलाउँदा, यो सत्र टोकन प्रयोग गरेर Entra ID पहुँच टोकन खोज्छ र त्यसपछि Microsoft Graph API कल गर्छ।

यो प्रवाह सार्वजनिक क्लाइन्ट प्रवाह भन्दा जटिल छ, तर इन्टरनेट-आधारित अन्त बिन्दुहरूको लागि आवश्यक छ। किनभने रिमोट MCP सर्भरहरू सार्वजनिक इन्टरनेटमा पहुँचयोग्य हुन्छन्, उनीहरूलाई अनधिकृत पहुँच र सम्भावित आक्रमणबाट सुरक्षा गर्न कडा सुरक्षा उपायहरू चाहिन्छ।

## सुरक्षा सर्वोत्तम अभ्यासहरू

- **सधैं HTTPS प्रयोग गर्नुहोस्**: क्लाइन्ट र सर्भर बीच सञ्चारलाई इन्क्रिप्ट गरेर टोकनहरू चोरी हुनबाट बचाउनुहोस्।
- **Role-Based Access Control (RBAC) लागू गर्नुहोस्**: केवल प्रयोगकर्ता प्रमाणीकरण भए कि भएन जाँच्नु पर्याप्त छैन; उनीहरूलाई के गर्न अनुमति छ पनि जाँच्नुहोस्। Entra ID मा भूमिका परिभाषित गर्न सकिन्छ र तपाईंको MCP सर्भरमा तिनीहरूलाई जाँच्न सकिन्छ।
- **निगरानी र अडिट गर्नुहोस्**: सबै प्रमाणीकरण घटनाहरू लग गर्नुहोस् ताकि संदिग्ध गतिविधि पत्ता लगाउन र प्रतिक्रिया दिन सकियोस्।
- **रेट लिमिटिंग र थ्रोटलिंग व्यवस्थापन गर्नुहोस्**: Microsoft Graph र अन्य API हरूले दुरुपयोग रोक्न रेट लिमिट लागू गर्छन्। तपाईंको MCP सर्भरमा HTTP 429 (Too Many Requests) प्रतिक्रिया सहजै व्यवस्थापन गर्न exponential backoff र retry तर्क लागू गर्नुहोस्। बारम्बार पहुँच गरिने डाटा क्यासिङ गरेर API कल घटाउन विचार गर्नुहोस्।
- **टोकन सुरक्षित भण्डारण गर्नुहोस्**: पहुँच टोकन र रिफ्रेस टोकनहरू सुरक्षित रूपमा भण्डारण गर्नुहोस्। स्थानीय अनुप्रयोगहरूको लागि प्रणालीको सुरक्षित भण्डारण प्रणाली प्रयोग गर्नुहोस्। सर्भर अनुप्रयोगहरूको लागि, एन्क्रिप्टेड भण्डारण वा Azure Key Vault जस्ता सुरक्षित कुञ्जी व्यवस्थापन सेवा प्रयोग गर्ने विचार गर्नुहोस्।
- **टोकनको म्याद समाप्ति व्यवस्थापन गर्नुहोस्**: पहुँच टोकनहरूको सीमित जीवनकाल हुन्छ। रिफ्रेस टोकन प्रयोग गरेर स्वतः टोकन ताजा पार्ने कार्यान्वयन गर्नुहोस् जसले पुनः प्रमाणीकरण बिना प्रयोगकर्ताको अनुभव निरन्तरता दिन्छ।
- **Azure API Management प्रयोग गर्ने विचार गर्नुहोस्**: MCP सर्भरमा प्रत्यक्ष सुरक्षा लागू गर्दा तपाईंलाई सूक्ष्म नियन्त्रण मिल्छ, तर Azure API Management जस्ता API गेटवेहरूले प्रमाणीकरण, अधिकृत, रेट लिमिटिंग, र निगरानी जस्ता सुरक्षा चिन्ताहरू स्वचालित रूपमा व्यवस्थापन गर्न सक्छन्। यी गेटवेहरूले तपाईंका क्लाइन्ट र MCP सर्भरहरू बीच केन्द्रिय सुरक्षा तह प्रदान गर्छन्। MCP सँग API गेटवे प्रयोग गर्ने बारे थप जानकारीका लागि हाम्रो [Azure API Management Your Auth Gateway For MCP Servers](https://techcommunity.microsoft.com/blog/integrationsonazureblog/azure-api-management-your-auth-gateway-for-mcp-servers/4402690) हेर्नुहोस्।

## मुख्य सिकाइहरू

- तपाईंको MCP सर्भर सुरक्षित गर्नु तपाईंका डाटा र उपकरणहरू संरक्षण गर्न अत्यावश्यक छ।
- Microsoft Entra ID प्रमाणीकरण र अधिकृतका लागि बलियो र स्केलेबल समाधान हो।
- स्थानीय अनुप्रयोगहरूको लागि **सार्वजनिक क्लाइन्ट** र रिमोट सर्भरहरूको लागि **गोप्य क्लाइन्ट** प्रयोग गर्नुहोस्।
- वेब अनुप्रयोगहरूको लागि **Authorization Code Flow** सबैभन्दा सुरक्षित विकल्प हो।

## अभ्यास

1. तपाईंले बनाउने सम्भावित MCP सर्भर कस्तो हुनेछ? स्थानीय सर्भर वा रिमोट सर्भर?
2. तपाईंको उत्तर अनुसार, सार्वजनिक वा गोप्य क्लाइन्ट कुन प्रयोग गर्नुहुन्छ?
3. Microsoft Graph विरुद्ध कार्य गर्न तपाईंको MCP सर्भरले कुन अनुमति माग्नेछ?

## व्यावहारिक अभ्यासहरू

### अभ्यास १: Entra ID मा अनुप्रयोग दर्ता गर्नुहोस्  
Microsoft Entra पोर्टलमा जानुहोस्।  
तपाईंको MCP सर्भरका लागि नयाँ अनुप्रयोग दर्ता गर्नुहोस्।  
Application (client) ID र Directory (tenant) ID रेकर्ड गर्नुहोस्।

### अभ्यास २: स्थानीय MCP सर्भर सुरक्षित पार्नुहोस् (सार्वजनिक क्लाइन्ट)  
प्रयोगकर्ता प्रमाणीकरणका लागि MSAL (Microsoft Authentication Library) एकीकरण गर्न कोड उदाहरण अनुसरण गर्नुहोस्।  
Microsoft Graph बाट प्रयोगकर्ता विवरण ल्याउने MCP उपकरण कल गरेर प्रमाणीकरण प्रवाह परीक्षण गर्नुहोस्।

### अभ्यास ३: रिमोट MCP सर्भर सुरक्षित पार्नुहोस् (गोप्य क्लाइन्ट)  
Entra ID मा गोप्य क्लाइन्ट दर्ता गर्नुहोस् र क्लाइन्ट गोप्य कुञ्जी बनाउनुहोस्।  
Express.js MCP सर्भरमा Authorization Code Flow कन्फिगर गर्नुहोस्।  
सुरक्षित अन्त बिन्दुहरू परीक्षण गर्नुहोस् र टोकन-आधारित पहुँच सुनिश्चित गर्नुहोस्।

### अभ्यास ४: सुरक्षा सर्वोत्तम अभ्यासहरू लागू गर्नुहोस्  
तपाईंको स्थानीय वा रिमोट सर्भरमा HTTPS सक्षम गर्नुहोस्।  
सर्भर लॉजिकमा role-based access control (RBAC) लागू गर्नुहोस्।  
टोकन म्याद समाप्ति व्यवस्थापन र सुरक्षित टोकन भण्डारण थप्नुहोस्।

## स्रोतहरू

1. **MSAL अवलोकन कागजात**  
   Microsoft Authentication Library (MSAL) ले कसरी प्लेटफर्महरूमा सुरक्षित टोकन प्राप्ति सक्षम गर्छ जान्न:  
   [MSAL Overview on Microsoft Learn](https://learn.microsoft.com/en-gb/entra/msal/overview)

2. **Azure-Samples/mcp-auth-servers GitHub भण्डार**  
   प्रमाणीकरण प्रवाह देखाउने MCP सर्भरहरूको सन्दर्भ कार्यान्वयनहरू:  
   [Azure-Samples/mcp-auth-servers on GitHub](https://github.com/Azure-Samples/mcp-auth-servers)

3. **Azure स्रोतहरूको लागि Managed Identities अवलोकन**  
   प्रणाली वा प्रयोगकर्ता-निर्दिष्ट प्रबन्धित पहिचानहरू प्रयोग गरेर गोप्य कुञ्जीहरू हटाउने तरिका:  
   [Managed Identities Overview on Microsoft Learn](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/)

4. **Azure API Management: MCP सर्भरहरूको लागि तपाईंको प्रमाणीकरण गेटवे**  
   MCP सर्भरहरूको लागि OAuth2 गेटवेको रूपमा APIM को प्रयोगमा गहिरो जानकारी:  
   [Azure API Management Your Auth Gateway For MCP Servers](https://techcommunity.microsoft.com/blog/integrationsonazureblog/azure-api-management-your-auth-gateway-for-mcp-servers/4402690)

5. **Microsoft Graph अनुमति सन्दर्भ**  
   Microsoft Graph का लागि प्रतिनिधित्व र अनुप्रयोग अनुमति सूची:  
   [Microsoft Graph Permissions Reference](https://learn.microsoft.com/zh-tw/graph/permissions-reference)

## सिकाइ परिणामहरू  
यस भाग पूरा गरेपछि, तपाईं सक्षम हुनुहुनेछ:

- MCP सर्भर र AI वर्कफ्लोज़का लागि प्रमाणीकरण किन महत्त्वपूर्ण छ स्पष्ट पार्न।
- स्थानीय र रिमोट MCP सर्भर परिदृश्यहरूमा Entra ID प्रमाणीकरण सेटअप र कन्फिगर गर्न।
- तपाईंको सर्भरको डिप्लोयमेन्ट अनुसार उपयुक्त क्लाइन्ट प्रकार (सार्वजनिक वा गोप्य) छनौट गर्न।
- टोकन भण्डारण र भूमिका-आधारित अधिकृतसहित सुरक्षित कोडिङ अभ्यासहरू लागू गर्न।
- तपाईंको MCP सर्भर र उपकरणहरूलाई अनधिकृत पहुँचबाट आत्मविश्वासका साथ सुरक्षा गर्न।

## के छ अर्को

- [6. Community Contributions](../../06-CommunityContributions/README.md)

**अस्वीकरण**:  
यो दस्तावेज़ AI अनुवाद सेवा [Co-op Translator](https://github.com/Azure/co-op-translator) प्रयोग गरी अनुवाद गरिएको हो। हामी सटीकताको प्रयास गर्छौं भने पनि, कृपया ध्यान दिनुहोस् कि स्वचालित अनुवादमा त्रुटि वा असत्यता हुन सक्छ। मूल दस्तावेज़ यसको मूल भाषामा नै आधिकारिक स्रोत मानिनुपर्छ। महत्वपूर्ण जानकारीका लागि व्यावसायिक मानव अनुवाद सिफारिस गरिन्छ। यस अनुवादको प्रयोगबाट उत्पन्न कुनै पनि गलतफहमी वा गलत व्याख्याको लागि हामी जिम्मेवार छैनौं।