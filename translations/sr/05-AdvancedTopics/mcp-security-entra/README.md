<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "0abf26a6c4dbe905d5d49ccdc0ccfe92",
  "translation_date": "2025-06-26T16:41:37+00:00",
  "source_file": "05-AdvancedTopics/mcp-security-entra/README.md",
  "language_code": "sr"
}
-->
# Заштићивање AI токова рада: Entra ID аутентификација за Model Context Protocol сервере

## Увод  
Заштићивање вашег Model Context Protocol (MCP) сервера је једнако важно као и закључавање улазних врата куће. Остављање MCP сервера отвореним излаже ваше алате и податке неовлашћеном приступу, што може довести до безбедносних пропуста. Microsoft Entra ID пружа поуздано решење за управљање идентитетом и приступом у облаку, помажући да само овлашћени корисници и апликације могу да комуницирају са вашим MCP сервером. У овом делу научићете како да заштитите своје AI токове рада коришћењем Entra ID аутентификације.

## Циљеви учења  
До краја овог дела, моћи ћете да:  

- Разумете значај заштите MCP сервера.  
- Објасните основе Microsoft Entra ID и OAuth 2.0 аутентификације.  
- Препознате разлику између јавних и поверљивих клијената.  
- Имплементирате Entra ID аутентификацију у локалним (јавни клијент) и удаљеним (поверљиви клијент) MCP сервер сценаријима.  
- Примените најбоље безбедносне праксе приликом развоја AI токова рада.  

## Безбедност и MCP  

Као што не бисте оставили улазна врата куће откључана, тако не би требало да остављате MCP сервер отвореним за приступ свима. Заштита ваших AI токова рада је кључна за изградњу поузданих, сигурних и безбедних апликација. Ово поглавље ће вас упознати са коришћењем Microsoft Entra ID за заштиту ваших MCP сервера, осигуравајући да само овлашћени корисници и апликације могу приступити вашим алатима и подацима.

## Зашто је безбедност важна за MCP сервере  

Замислите да ваш MCP сервер има алат који може да шаље имејлове или приступа бази података клијената. Несигуран сервер би значио да било ко може потенцијално да користи тај алат, што може довести до неовлашћеног приступа подацима, слања спама или других злонамерних активности.  

Имплементирањем аутентификације осигуравате да сваки захтев према серверу буде проверен, потврђујући идентитет корисника или апликације која шаље захтев. Ово је први и најважнији корак у заштити ваших AI токова рада.

## Увод у Microsoft Entra ID  

[**Microsoft Entra ID**](https://adoption.microsoft.com/microsoft-security/entra/) је сервис за управљање идентитетима и приступом у облаку. Можете га замислити као универзалног чувара безбедности за ваше апликације. Он управља сложеним процесом верификације идентитета корисника (аутентификација) и одређује шта им је дозвољено да раде (ауторација).  

Коришћењем Entra ID можете:  

- Омогућити безбедно пријављивање корисника.  
- Заштитити API-је и сервисе.  
- Управљати политикама приступа са централизоване локације.  

За MCP сервере, Entra ID пружа поуздано и широко прихваћено решење за контролу ко може да приступи могућностима вашег сервера.

---

## Разумевање магије: Како функционише Entra ID аутентификација  

Entra ID користи отворене стандарде као што је **OAuth 2.0** за управљање аутентификацијом. Иако детаљи могу бити сложени, основна идеја је једноставна и може се објаснити аналогом.  

### Благи увод у OAuth 2.0: Кључ за паркирање  

Замислите OAuth 2.0 као услугу паркирања вашег аутомобила. Када стигнете у ресторан, не дајете паркирачу свој главни кључ. Уместо тога, дајете **кључ за паркирање** који има ограничене дозволе — може да упали ауто и закључа врата, али не може да отвори пртљажник или рукавски фах.  

У овој аналогији:  

- **Ви** сте **Корисник**.  
- **Ваш ауто** је **MCP сервер** са вредним алатима и подацима.  
- **Паркирач** је **Microsoft Entra ID**.  
- **Парклирање аутомобила** је **MCP клијент** (апликација која покушава да приступи серверу).  
- **Кључ за паркирање** је **Access Token**.  

Access token је безбедан текстуални низ који MCP клијент добија од Entra ID након ваше пријаве. Клијент потом представља овај токен MCP серверу при сваком захтеву. Сервер може да провери токен како би осигурао да је захтев легитиман и да клијент има потребна овлашћења, све то без потребе да рукује вашим стварним подацима за пријаву (као што је лозинка).

### Ток аутентификације  

Ево како процес функционише у пракси:  

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

### Упознавање са Microsoft Authentication Library (MSAL)  

Пре него што пређемо на код, важно је упознати кључну компоненту коју ћете видети у примерима: **Microsoft Authentication Library (MSAL)**.  

MSAL је библиотека коју је развио Microsoft и која знатно олакшава програмерима рад са аутентификацијом. Уместо да ви пишете сав сложени код за управљање безбедносним токенима, пријавама и освежавањем сесија, MSAL обавља цео тај тежак посао.  

Коришћење библиотеке као што је MSAL се топло препоручује јер:  

- **Безбедна је:** Имплементира индустријске стандарде и најбоље безбедносне праксе, смањујући ризик од рањивости у вашем коду.  
- **Поједностављује развој:** Апстрахује сложеност OAuth 2.0 и OpenID Connect протокола, омогућавајући вам да додате робусну аутентификацију у апликацију са само неколико редова кода.  
- **Одржава се:** Microsoft активно одржава и ажурира MSAL како би одговорио на нове безбедносне претње и промене платформи.  

MSAL подржава широк спектар језика и оквира апликација, укључујући .NET, JavaScript/TypeScript, Python, Java, Go и мобилне платформе као што су iOS и Android. То значи да можете користити доследне шаблоне аутентификације у целокупном технолошком скупу.  

За више информација о MSAL, можете погледати званичну [MSAL overview документацију](https://learn.microsoft.com/entra/identity-platform/msal-overview).

---

## Заштићивање вашег MCP сервера уз Entra ID: Водич корак по корак  

Сада ћемо проћи кроз поступак заштите локалног MCP сервера (који комуницира преко `stdio`) using Entra ID. This example uses a **public client**, which is suitable for applications running on a user's machine, like a desktop app or a local development server.

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
- **`AcquireTokenAsync`**: Ово је кључна метода. Прво покушава да добије токен тихо (што значи да корисник не мора поново да се пријављује ако већ има валидну сесију). Ако тихо добијање токена није могуће, затражиће од корисника интерактивну пријаву.

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
- **`GetUserDetailsFromGraph` tool**: This tool requires an instance of `AuthenticationService`. Before it does anything, it calls `authService.AcquireTokenAsync()` да добије валидан access token. Ако је аутентификација успешна, користи тај токен за позив Microsoft Graph API-ја и преузима детаље корисника.

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

#### 3. Како све то функционише заједно  

1. Када MCP клијент покуша да користи `GetUserDetailsFromGraph` tool, the tool first calls `AcquireTokenAsync`.
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
- **`/auth/callback`**: Овај крајњи тачка обрађује преусмеравање из Entra ID након што се корисник аутентификовaо. Она мења authorization код за access токен и refresh токен.

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

This file defines the tools that the MCP server provides. The `getUserDetails` алатка је слична оној из претходног примера, али добија access токен из сесије.

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
6. When the `getUserDetails` алатка се позива, користи сесијски токен да пронађе Entra ID access токен, а затим га користи за позив Microsoft Graph API-ја.

Овај ток је сложенији од тока за јавне клијенте, али је неопходан за интернет-усмерене крајње тачке. Пошто су удаљени MCP сервери доступни преко јавног интернета, потребне су јаче безбедносне мере како би се заштитили од неовлашћеног приступа и потенцијалних напада.

## Најбоље безбедносне праксе  

- **Увек користите HTTPS**: Шифрујте комуникацију између клијента и сервера како бисте заштитили токене од пресретања.  
- **Имплементирајте контролу приступа засновану на улогама (RBAC)**: Не проверавајте само *да ли* је корисник аутентификован, већ и *шта* је овлашћен да ради. Можете дефинисати улоге у Entra ID и проверавати их у вашем MCP серверу.  
- **Пратите и ревидирајте**: Логовање свих аутентификационих догађаја омогућава вам да откријете и реагујете на сумњиве активности.  
- **Обрада ограничења брзине и убрзања (rate limiting и throttling)**: Microsoft Graph и други API-ји имају ограничења брзине како би спречили злоупотребе. Имплементирајте експоненцијално одлагање и логику поновног покушаја у вашем MCP серверу да бисте лепо обрадили HTTP 429 (превише захтева) одговоре. Размотрите кеширање често коришћених података како бисте смањили број позива API-ју.  
- **Безбедно чување токена**: Чувајте access и refresh токене на безбедан начин. За локалне апликације користите системске механизме за безбедно складиштење. За серверске апликације размотрите коришћење шифрованог складишта или сервиса за управљање кључевима као што је Azure Key Vault.  
- **Обрада истека токена**: Access токени имају ограничен рок трајања. Имплементирајте аутоматско освежавање токена помоћу refresh токена како бисте обезбедили непрекидан кориснички доживљај без поновне пријаве.  
- **Размотрите коришћење Azure API Management**: Иако директна имплементација безбедности у вашем MCP серверу пружа прецизну контролу, API Gateway-ји као што је Azure API Management могу аутоматски обрадити многе безбедносне аспекте, укључујући аутентификацију, ауторацију, ограничење брзине и праћење. Они пружају централизовани безбедносни слој између ваших клијената и MCP сервера. За више детаља о коришћењу API Gateway-ја са MCP, погледајте наш чланак [Azure API Management Your Auth Gateway For MCP Servers](https://techcommunity.microsoft.com/blog/integrationsonazureblog/azure-api-management-your-auth-gateway-for-mcp-servers/4402690).

## Кључне поуке  

- Заштита вашег MCP сервера је кључна за безбедност ваших података и алата.  
- Microsoft Entra ID пружа робусно и скалабилно решење за аутентификацију и ауторацију.  
- Користите **јавног клијента** за локалне апликације и **поверљивог клијента** за удаљене сервере.  
- **Authorization Code Flow** је најсигурнија опција за веб апликације.  

## Вежба  

1. Размислите о MCP серверу који бисте могли направити. Да ли би то био локални или удаљени сервер?  
2. На основу одговора, да ли бисте користили јавног или поверљивог клијента?  
3. Које дозволе би ваш MCP сервер тражио за извршавање радњи према Microsoft Graph?  

## Практичне вежбе  

### Вежба 1: Региструјте апликацију у Entra ID  
Идите на Microsoft Entra портал.  
Региструјте нову апликацију за ваш MCP сервер.  
Запишите Application (client) ID и Directory (tenant) ID.  

### Вежба 2: Заштитите локални MCP сервер (јавни клијент)  
- Пратите пример кода за интеграцију MSAL (Microsoft Authentication Library) за аутентификацију корисника.  
- Тестирајте ток аутентификације позивом MCP алата који преузима детаље корисника из Microsoft Graph.  

### Вежба 3: Заштитите удаљени MCP сервер (поверљиви клијент)  
- Региструјте поверљивог клијента у Entra ID и креирајте client secret.  
- Конфигуришите ваш Express.js MCP сервер да користи Authorization Code Flow.  
- Тестирајте заштићене крајње тачке и потврдите приступ базиран на токену.  

### Вежба 4: Примените најбоље безбедносне праксе  
- Омогућите HTTPS за ваш локални или удаљени сервер.  
- Имплементирајте контролу приступа засновану на улогама (RBAC) у логици сервера.  
- Додајте обраду истека токена и безбедно складиштење токена.  

## Ресурси  

1. **MSAL Overview Documentation**  
   Сазнајте како Microsoft Authentication Library (MSAL) омогућава безбедно преузимање токена на различитим платформама:  
   [MSAL Overview on Microsoft Learn](https://learn.microsoft.com/en-gb/entra/msal/overview)  

2. **Azure-Samples/mcp-auth-servers GitHub репозиторијум**  
   Референтне имплементације MCP сервера који демонстрирају токове аутентификације:  
   [Azure-Samples/mcp-auth-servers on GitHub](https://github.com/Azure-Samples/mcp-auth-servers)  

3. **Managed Identities for Azure Resources Overview**  
   Схватите како да елиминишете тајне користећи системски или кориснички додељене управљане идентитете:  
   [Managed Identities Overview on Microsoft Learn](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/)  

4. **Azure API Management: Your Auth Gateway for MCP Servers**  
   Детаљан преглед коришћења APIM као безбедног OAuth2 gateway-а за MCP сервере:  
   [Azure API Management Your Auth Gateway For MCP Servers](https://techcommunity.microsoft.com/blog/integrationsonazureblog/azure-api

**Одрицање од одговорности**:  
Овај документ је преведен коришћењем АИ услуге за превођење [Co-op Translator](https://github.com/Azure/co-op-translator). Иако се трудимо да превод буде тачан, молимо вас да имате у виду да аутоматизовани преводи могу садржати грешке или нетачности. Изворни документ на његовом оригиналном језику треба сматрати ауторитетним извором. За критичне информације препоручује се професионални превод од стране људског преводиоца. Нисмо одговорни за било каква неспоразума или погрешне тумачења која могу настати употребом овог превода.