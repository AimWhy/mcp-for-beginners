<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "9abe1d303ab126f9a8b87f03cebe5213",
  "translation_date": "2025-06-26T14:48:17+00:00",
  "source_file": "05-AdvancedTopics/mcp-security-entra/README.md",
  "language_code": "el"
}
-->
# Ασφάλεια Ροών Εργασίας Τεχνητής Νοημοσύνης: Έλεγχος Ταυτότητας Entra ID για Διακομιστές Model Context Protocol

## Εισαγωγή  
Η ασφάλεια του διακομιστή Model Context Protocol (MCP) είναι εξίσου σημαντική με το να κλειδώνετε την εξώπορτα του σπιτιού σας. Αφήνοντας τον MCP διακομιστή ανοιχτό, εκθέτετε τα εργαλεία και τα δεδομένα σας σε μη εξουσιοδοτημένη πρόσβαση, κάτι που μπορεί να οδηγήσει σε παραβιάσεις ασφάλειας. Το Microsoft Entra ID παρέχει μια αξιόπιστη λύση διαχείρισης ταυτότητας και πρόσβασης στο cloud, βοηθώντας να διασφαλιστεί ότι μόνο εξουσιοδοτημένοι χρήστες και εφαρμογές μπορούν να αλληλεπιδρούν με τον MCP διακομιστή σας. Σε αυτή την ενότητα, θα μάθετε πώς να προστατεύετε τις ροές εργασίας τεχνητής νοημοσύνης σας χρησιμοποιώντας τον έλεγχο ταυτότητας Entra ID.

## Στόχοι Μάθησης  
Στο τέλος αυτής της ενότητας, θα μπορείτε να:

- Κατανοήσετε τη σημασία της ασφάλειας των MCP διακομιστών.  
- Εξηγήσετε τα βασικά του Microsoft Entra ID και του ελέγχου ταυτότητας OAuth 2.0.  
- Αναγνωρίσετε τη διαφορά μεταξύ δημόσιων και εμπιστευτικών πελατών.  
- Εφαρμόσετε τον έλεγχο ταυτότητας Entra ID τόσο σε τοπικά (δημόσιοι πελάτες) όσο και σε απομακρυσμένα (εμπιστευτικοί πελάτες) σενάρια MCP διακομιστών.  
- Εφαρμόσετε βέλτιστες πρακτικές ασφάλειας κατά την ανάπτυξη ροών εργασίας τεχνητής νοημοσύνης.

# Ασφάλεια Ροών Εργασίας Τεχνητής Νοημοσύνης: Έλεγχος Ταυτότητας Entra ID για Διακομιστές Model Context Protocol

Όπως δεν αφήνετε ξεκλείδωτη την εξώπορτα του σπιτιού σας, έτσι δεν πρέπει να αφήνετε τον MCP διακομιστή σας ανοιχτό για οποιονδήποτε. Η ασφάλεια των ροών εργασίας τεχνητής νοημοσύνης είναι απαραίτητη για τη δημιουργία αξιόπιστων, ασφαλών και σταθερών εφαρμογών. Αυτό το κεφάλαιο θα σας εισαγάγει στη χρήση του Microsoft Entra ID για την ασφάλεια των MCP διακομιστών σας, διασφαλίζοντας ότι μόνο εξουσιοδοτημένοι χρήστες και εφαρμογές μπορούν να αλληλεπιδρούν με τα εργαλεία και τα δεδομένα σας.

## Γιατί η Ασφάλεια Έχει Σημασία για τους MCP Διακομιστές

Φανταστείτε ότι ο MCP διακομιστής σας διαθέτει ένα εργαλείο που μπορεί να στείλει email ή να έχει πρόσβαση σε μια βάση δεδομένων πελατών. Ένας μη ασφαλής διακομιστής σημαίνει ότι οποιοσδήποτε θα μπορούσε να χρησιμοποιήσει αυτό το εργαλείο, οδηγώντας σε μη εξουσιοδοτημένη πρόσβαση σε δεδομένα, ανεπιθύμητα μηνύματα ή άλλες κακόβουλες ενέργειες.

Με την εφαρμογή ελέγχου ταυτότητας, διασφαλίζετε ότι κάθε αίτημα προς τον διακομιστή σας επαληθεύεται, επιβεβαιώνοντας την ταυτότητα του χρήστη ή της εφαρμογής που κάνει το αίτημα. Αυτό είναι το πρώτο και πιο κρίσιμο βήμα για την ασφάλεια των ροών εργασίας τεχνητής νοημοσύνης σας.

## Εισαγωγή στο Microsoft Entra ID

**Το Microsoft Entra ID** είναι μια υπηρεσία διαχείρισης ταυτότητας και πρόσβασης βασισμένη στο cloud. Σκεφτείτε το σαν έναν παγκόσμιο φύλακα ασφαλείας για τις εφαρμογές σας. Αναλαμβάνει τη σύνθετη διαδικασία επαλήθευσης ταυτότητας των χρηστών (authentication) και καθορίζει τι δικαιώματα έχουν (authorization).

Με τη χρήση του Entra ID, μπορείτε να:

- Ενεργοποιήσετε ασφαλή σύνδεση για τους χρήστες.  
- Προστατεύσετε APIs και υπηρεσίες.  
- Διαχειριστείτε πολιτικές πρόσβασης από ένα κεντρικό σημείο.

Για τους MCP διακομιστές, το Entra ID παρέχει μια ισχυρή και ευρέως αξιόπιστη λύση για τη διαχείριση του ποιος μπορεί να έχει πρόσβαση στις δυνατότητες του διακομιστή σας.

---

## Κατανόηση της Μαγικής Λειτουργίας: Πώς Λειτουργεί ο Έλεγχος Ταυτότητας Entra ID

Το Entra ID χρησιμοποιεί ανοιχτά πρότυπα όπως το **OAuth 2.0** για τη διαχείριση του ελέγχου ταυτότητας. Αν και οι λεπτομέρειες μπορεί να είναι περίπλοκες, η βασική ιδέα είναι απλή και μπορεί να γίνει κατανοητή μέσω μιας αναλογίας.

### Μια Απλή Εισαγωγή στο OAuth 2.0: Το Κλειδί του Υπαλλήλου Υπηρεσίας Παρκαρίσματος

Σκεφτείτε το OAuth 2.0 σαν μια υπηρεσία υπαλλήλου παρκαρίσματος για το αυτοκίνητό σας. Όταν φτάνετε σε ένα εστιατόριο, δεν δίνετε στον υπάλληλο το γενικό κλειδί του αυτοκινήτου. Αντίθετα, του δίνετε ένα **κλειδί υπαλλήλου** που έχει περιορισμένες άδειες — μπορεί να ξεκινήσει το αυτοκίνητο και να κλειδώσει τις πόρτες, αλλά δεν μπορεί να ανοίξει το πορτμπαγκάζ ή το ντουλαπάκι.

Σε αυτή την αναλογία:

- **Εσείς** είστε ο **Χρήστης**.  
- **Το αυτοκίνητό σας** είναι ο **MCP Διακομιστής** με τα πολύτιμα εργαλεία και δεδομένα του.  
- Ο **Υπάλληλος Υπηρεσίας Παρκαρίσματος** είναι το **Microsoft Entra ID**.  
- Ο **Υπάλληλος Πάρκινγκ** είναι ο **MCP Client** (η εφαρμογή που προσπαθεί να έχει πρόσβαση στον διακομιστή).  
- Το **Κλειδί Υπαλλήλου** είναι το **Access Token**.

Το access token είναι μια ασφαλής συμβολοσειρά κειμένου που λαμβάνει ο MCP client από το Entra ID μετά τη σύνδεσή σας. Ο client παρουσιάζει αυτό το token στον MCP διακομιστή με κάθε αίτημα. Ο διακομιστής μπορεί να επαληθεύσει το token για να βεβαιωθεί ότι το αίτημα είναι νόμιμο και ότι ο client έχει τα απαραίτητα δικαιώματα, χωρίς να χρειάζεται ποτέ να χειριστεί τα πραγματικά σας διαπιστευτήρια (όπως τον κωδικό πρόσβασής σας).

### Η Ροή Ελέγχου Ταυτότητας

Ακολουθεί πώς λειτουργεί η διαδικασία στην πράξη:

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

### Εισαγωγή στη Microsoft Authentication Library (MSAL)

Πριν προχωρήσουμε στον κώδικα, είναι σημαντικό να παρουσιάσουμε ένα βασικό συστατικό που θα δείτε στα παραδείγματα: τη **Microsoft Authentication Library (MSAL)**.

Η MSAL είναι μια βιβλιοθήκη που έχει αναπτύξει η Microsoft και διευκολύνει πολύ τους προγραμματιστές στην υλοποίηση ελέγχου ταυτότητας. Αντί να γράφετε όλο τον πολύπλοκο κώδικα για τη διαχείριση των security tokens, τη διαχείριση συνδέσεων και την ανανέωση συνεδριών, η MSAL αναλαμβάνει το μεγαλύτερο μέρος της δουλειάς.

Η χρήση μιας βιβλιοθήκης όπως η MSAL συνιστάται έντονα επειδή:

- **Είναι Ασφαλής:** Υλοποιεί πρωτόκολλα βιομηχανικού επιπέδου και βέλτιστες πρακτικές ασφάλειας, μειώνοντας τον κίνδυνο ευπαθειών στον κώδικά σας.  
- **Απλοποιεί την Ανάπτυξη:** Αφαιρεί την πολυπλοκότητα των πρωτοκόλλων OAuth 2.0 και OpenID Connect, επιτρέποντάς σας να προσθέσετε ισχυρό έλεγχο ταυτότητας στην εφαρμογή σας με λίγες μόνο γραμμές κώδικα.  
- **Υποστηρίζεται Ενεργά:** Η Microsoft διατηρεί και ενημερώνει ενεργά τη MSAL για να αντιμετωπίζει νέες απειλές ασφάλειας και αλλαγές πλατφορμών.

Η MSAL υποστηρίζει ποικιλία γλωσσών και πλαισίων εφαρμογών, όπως .NET, JavaScript/TypeScript, Python, Java, Go και κινητές πλατφόρμες όπως iOS και Android. Αυτό σημαίνει ότι μπορείτε να χρησιμοποιείτε τα ίδια συνεπή πρότυπα ελέγχου ταυτότητας σε όλο το τεχνολογικό σας περιβάλλον.

Για να μάθετε περισσότερα για τη MSAL, μπορείτε να δείτε την επίσημη [τεκμηρίωση επισκόπησης MSAL](https://learn.microsoft.com/entra/identity-platform/msal-overview).

---

## Ασφαλίζοντας τον MCP Διακομιστή σας με Entra ID: Οδηγός Βήμα-Βήμα

Τώρα, ας δούμε πώς να ασφαλίσετε έναν τοπικό MCP διακομιστή (έναν που επικοινωνεί μέσω `stdio`) using Entra ID. This example uses a **public client**, which is suitable for applications running on a user's machine, like a desktop app or a local development server.

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
- **`AcquireTokenAsync`**: Αυτή είναι η βασική μέθοδος. Πρώτα προσπαθεί να αποκτήσει token σιωπηλά (δηλαδή ο χρήστης δεν χρειάζεται να συνδεθεί ξανά αν έχει ήδη ενεργή συνεδρία). Αν δεν μπορέσει να αποκτήσει σιωπηλά το token, θα ζητήσει από τον χρήστη να συνδεθεί αλληλεπιδραστικά.

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
- **`GetUserDetailsFromGraph` tool**: This tool requires an instance of `AuthenticationService`. Before it does anything, it calls `authService.AcquireTokenAsync()` για να πάρει ένα έγκυρο access token. Αν η αυθεντικοποίηση είναι επιτυχής, χρησιμοποιεί το token για να καλέσει το Microsoft Graph API και να πάρει τις λεπτομέρειες του χρήστη.

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

#### 3. Πώς Λειτουργούν Όλα Μαζί

1. Όταν ο MCP client προσπαθεί να χρησιμοποιήσει το `GetUserDetailsFromGraph` tool, the tool first calls `AcquireTokenAsync`.
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
- **`/auth/callback`**: Αυτό το endpoint χειρίζεται την ανακατεύθυνση από το Entra ID μετά την αυθεντικοποίηση του χρήστη. Ανταλλάσσει τον κωδικό εξουσιοδότησης με ένα access token και ένα refresh token.

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

This file defines the tools that the MCP server provides. The `getUserDetails` εργαλείο είναι παρόμοιο με αυτό του προηγούμενου παραδείγματος, αλλά παίρνει το access token από τη συνεδρία.

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
6. When the `getUserDetails` εργαλείο καλείται, χρησιμοποιεί το token της συνεδρίας για να βρει το access token του Entra ID και στη συνέχεια το χρησιμοποιεί για να καλέσει το Microsoft Graph API.

Αυτή η ροή είναι πιο σύνθετη από αυτή του δημόσιου πελάτη, αλλά είναι απαραίτητη για endpoints που είναι προσβάσιμα μέσω του δημόσιου διαδικτύου. Επειδή οι απομακρυσμένοι MCP διακομιστές είναι προσβάσιμοι μέσω του δημόσιου διαδικτύου, χρειάζονται πιο ισχυρά μέτρα ασφάλειας για προστασία από μη εξουσιοδοτημένη πρόσβαση και πιθανές επιθέσεις.

## Βέλτιστες Πρακτικές Ασφάλειας

- **Χρησιμοποιείτε πάντα HTTPS**: Κρυπτογραφείστε την επικοινωνία μεταξύ client και διακομιστή για να προστατεύσετε τα tokens από υποκλοπή.  
- **Εφαρμόστε Έλεγχο Πρόσβασης με Βάση Ρόλους (RBAC)**: Μην ελέγχετε μόνο αν ο χρήστης είναι αυθεντικοποιημένος, αλλά και τι δικαιώματα έχει. Μπορείτε να ορίσετε ρόλους στο Entra ID και να τους ελέγχετε στον MCP διακομιστή σας.  
- **Παρακολουθείτε και κάνετε έλεγχο**: Καταγράφετε όλα τα γεγονότα ελέγχου ταυτότητας ώστε να εντοπίζετε και να αντιδράτε σε ύποπτες δραστηριότητες.  
- **Διαχειριστείτε περιορισμούς ρυθμού και throttling**: Το Microsoft Graph και άλλα APIs εφαρμόζουν περιορισμούς ρυθμού για να αποτρέψουν κατάχρηση. Εφαρμόστε λογική εκθετικής καθυστέρησης και επανάληψης στο MCP διακομιστή σας για να διαχειρίζεστε ομαλά τις απαντήσεις HTTP 429 (Too Many Requests). Σκεφτείτε την προσωρινή αποθήκευση συχνά προσπελάσιμων δεδομένων για να μειώσετε τις κλήσεις API.  
- **Ασφαλής αποθήκευση tokens**: Αποθηκεύστε με ασφάλεια τα access tokens και τα refresh tokens. Για τοπικές εφαρμογές, χρησιμοποιήστε τους μηχανισμούς ασφαλούς αποθήκευσης του συστήματος. Για διακομιστές, σκεφτείτε κρυπτογραφημένη αποθήκευση ή υπηρεσίες ασφαλούς διαχείρισης κλειδιών όπως το Azure Key Vault.  
- **Διαχείριση λήξης tokens**: Τα access tokens έχουν περιορισμένη διάρκεια ζωής. Υλοποιήστε αυτόματη ανανέωση tokens χρησιμοποιώντας refresh tokens για να διατηρείτε την εμπειρία χρήστη ομαλή χωρίς να απαιτείται εκ νέου σύνδεση.  
- **Σκεφτείτε τη χρήση Azure API Management**: Ενώ η εφαρμογή ασφάλειας απευθείας στον MCP διακομιστή σας προσφέρει λεπτομερή έλεγχο, τα API Gateways όπως το Azure API Management μπορούν να διαχειριστούν πολλές από αυτές τις ανησυχίες ασφάλειας αυτόματα, συμπεριλαμβανομένων του ελέγχου ταυτότητας, της εξουσιοδότησης, του περιορισμού ρυθμού και της παρακολούθησης. Παρέχουν ένα κεντρικό επίπεδο ασφάλειας που βρίσκεται ανάμεσα στους clients και τους MCP διακομιστές σας. Για περισσότερες λεπτομέρειες σχετικά με τη χρήση API Gateways με MCP, δείτε το [Azure API Management Your Auth Gateway For MCP Servers](https://techcommunity.microsoft.com/blog/integrationsonazureblog/azure-api-management-your-auth-gateway-for-mcp-servers/4402690).

## Βασικά Συμπεράσματα

- Η ασφάλεια του MCP διακομιστή σας είναι κρίσιμη για την προστασία των δεδομένων και των εργαλείων σας.  
- Το Microsoft Entra ID παρέχει μια ισχυρή και κλιμακούμενη λύση για έλεγχο ταυτότητας και εξουσιοδότηση.  
- Χρησιμοποιήστε **δημόσιο πελάτη** για τοπικές εφαρμογές και **εμπιστευτικό πελάτη** για απομακρυσμένους διακομιστές.  
- Η **Ροή Κωδικού Εξουσιοδότησης (Authorization Code Flow)** είναι η πιο ασφαλής επιλογή για web εφαρμογές.

## Άσκηση

1. Σκεφτείτε έναν MCP διακομιστή που μπορεί να δημιουργήσετε. Θα είναι τοπικός ή απομακρυσμένος;  
2. Με βάση την απάντησή σας, θα χρησιμοποιούσατε δημόσιο ή εμπιστευτικό πελάτη;  
3. Ποια δικαιώματα θα ζητούσε ο MCP διακομιστής σας για να εκτελεί ενέργειες στο Microsoft Graph;

## Πρακτικές Ασκήσεις

### Άσκηση 1: Καταχώριση Εφαρμογής στο Entra ID  
Πλοηγηθείτε στην πύλη Microsoft Entra.  
Καταχωρίστε μια νέα εφαρμογή για τον MCP διακομιστή σας.  
Καταγράψτε το Application (client) ID και το Directory (tenant) ID.

### Άσκηση 2: Ασφάλεια Τοπικού MCP Διακομιστή (Δημόσιος Πε

**Αποποίηση Ευθυνών**:  
Αυτό το έγγραφο έχει μεταφραστεί χρησιμοποιώντας την υπηρεσία μετάφρασης με τεχνητή νοημοσύνη [Co-op Translator](https://github.com/Azure/co-op-translator). Παρόλο που προσπαθούμε για ακρίβεια, παρακαλούμε να έχετε υπόψη ότι οι αυτόματες μεταφράσεις ενδέχεται να περιέχουν λάθη ή ανακρίβειες. Το πρωτότυπο έγγραφο στη γλώσσα του θεωρείται η αυθεντική πηγή. Για κρίσιμες πληροφορίες συνιστάται επαγγελματική μετάφραση από άνθρωπο. Δεν φέρουμε ευθύνη για οποιεσδήποτε παρεξηγήσεις ή λανθασμένες ερμηνείες που προκύπτουν από τη χρήση αυτής της μετάφρασης.