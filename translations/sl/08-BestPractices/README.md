<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "80e5c8949af5af0f401fce6f905990aa",
  "translation_date": "2025-07-17T12:17:37+00:00",
  "source_file": "08-BestPractices/README.md",
  "language_code": "sl"
}
-->
# Najboljše prakse razvoja MCP

## Pregled

Ta lekcija se osredotoča na napredne najboljše prakse za razvoj, testiranje in uvajanje MCP strežnikov in funkcij v produkcijskih okoljih. Ker MCP ekosistemi postajajo vse bolj kompleksni in pomembni, zagotavljanje zanesljivosti, vzdržljivosti in medsebojne združljivosti zahteva upoštevanje uveljavljenih vzorcev. Ta lekcija združuje praktične izkušnje iz resničnih implementacij MCP, da vas vodi pri ustvarjanju robustnih, učinkovitih strežnikov z učinkoviti viri, pozivi in orodji.

## Cilji učenja

Ob koncu te lekcije boste znali:
- Uporabiti industrijske najboljše prakse pri oblikovanju MCP strežnikov in funkcij
- Ustvariti celovite strategije testiranja MCP strežnikov
- Oblikovati učinkovite, ponovno uporabne vzorce delovnih tokov za kompleksne MCP aplikacije
- Izvesti pravilno ravnanje z napakami, beleženje in opazovanje v MCP strežnikih
- Optimizirati MCP implementacije za zmogljivost, varnost in vzdržljivost

## Temeljna načela MCP

Preden se poglobimo v specifične prakse implementacije, je pomembno razumeti temeljna načela, ki usmerjajo učinkoviti razvoj MCP:

1. **Standardizirana komunikacija**: MCP temelji na JSON-RPC 2.0, ki zagotavlja dosleden format za zahteve, odgovore in ravnanje z napakami v vseh implementacijah.

2. **Oblikovanje osredotočeno na uporabnika**: Vedno dajajte prednost soglasju, nadzoru in preglednosti za uporabnika v vaših MCP implementacijah.

3. **Varnost na prvem mestu**: Uvedite robustne varnostne ukrepe, vključno z avtentikacijo, avtorizacijo, validacijo in omejevanjem hitrosti.

4. **Modularna arhitektura**: Oblikujte MCP strežnike modularno, kjer ima vsako orodje in vir jasno, osredotočeno nalogo.

5. **Stanje povezav**: Izkoristite sposobnost MCP za ohranjanje stanja med več zahtevki za bolj koherentne in kontekstno zavedne interakcije.

## Uradne najboljše prakse MCP

Naslednje najboljše prakse izhajajo iz uradne dokumentacije Model Context Protocol:

### Najboljše prakse varnosti

1. **Soglasje in nadzor uporabnika**: Vedno zahtevajte izrecno soglasje uporabnika pred dostopom do podatkov ali izvajanjem operacij. Zagotovite jasen nadzor nad tem, kateri podatki se delijo in katere akcije so dovoljene.

2. **Zasebnost podatkov**: Razkrijte uporabniške podatke le z izrecnim soglasjem in jih zaščitite z ustreznimi dostopnimi kontrolami. Varujte pred nepooblaščenim prenosom podatkov.

3. **Varnost orodij**: Pred uporabo kateregakoli orodja zahtevajte izrecno soglasje uporabnika. Poskrbite, da uporabniki razumejo funkcionalnost vsakega orodja in vzpostavite močne varnostne meje.

4. **Nadzor dovoljenj orodij**: Konfigurirajte, katera orodja lahko model uporablja med sejo, da zagotovite dostop le do izrecno pooblaščenih orodij.

5. **Avtentikacija**: Zahtevajte ustrezno avtentikacijo pred dostopom do orodij, virov ali občutljivih operacij z uporabo API ključev, OAuth žetonov ali drugih varnih metod.

6. **Validacija parametrov**: Uveljavljajte validacijo za vse klice orodij, da preprečite, da bi nepravilni ali zlonamerni vnosi dosegli implementacije orodij.

7. **Omejevanje hitrosti**: Uvedite omejevanje hitrosti za preprečevanje zlorab in zagotavljanje poštene uporabe strežniških virov.

### Najboljše prakse implementacije

1. **Pogajanje o zmogljivostih**: Med vzpostavitvijo povezave izmenjajte informacije o podprtih funkcijah, različicah protokola, razpoložljivih orodjih in virih.

2. **Oblikovanje orodij**: Ustvarjajte osredotočena orodja, ki dobro opravljajo eno nalogo, namesto monolitnih orodij, ki obravnavajo več skrbi.

3. **Ravnanje z napakami**: Uvedite standardizirana sporočila o napakah in kode, ki pomagajo pri diagnosticiranju težav, elegantnemu ravnanju z napakami in zagotavljanju uporabnih povratnih informacij.

4. **Beleženje**: Konfigurirajte strukturirane dnevnike za revizijo, odpravljanje napak in spremljanje interakcij protokola.

5. **Sledenje napredku**: Pri dolgotrajnih operacijah poročajte o napredku, da omogočite odzivne uporabniške vmesnike.

6. **Preklic zahtevkov**: Dovolite odjemalcem preklic zahtevkov, ki so v teku, a niso več potrebni ali trajajo predolgo.

## Dodatne reference

Za najnovejše informacije o najboljših praksah MCP si oglejte:
- [MCP Documentation](https://modelcontextprotocol.io/)
- [MCP Specification](https://spec.modelcontextprotocol.io/)
- [GitHub Repository](https://github.com/modelcontextprotocol)
- [Security Best Practices](https://modelcontextprotocol.io/specification/draft/basic/security_best_practices)

## Primeri praktične implementacije

### Najboljše prakse oblikovanja orodij

#### 1. Načelo enotne odgovornosti

Vsako MCP orodje naj ima jasno, osredotočeno nalogo. Namesto da ustvarjate monolitna orodja, ki poskušajo obravnavati več skrbi, razvijajte specializirana orodja, ki so odlična pri določenih nalogah.

```csharp
// A focused tool that does one thing well
public class WeatherForecastTool : ITool
{
    private readonly IWeatherService _weatherService;
    
    public WeatherForecastTool(IWeatherService weatherService)
    {
        _weatherService = weatherService;
    }
    
    public string Name => "weatherForecast";
    public string Description => "Gets weather forecast for a specific location";
    
    public ToolDefinition GetDefinition()
    {
        return new ToolDefinition
        {
            Name = Name,
            Description = Description,
            Parameters = new Dictionary<string, ParameterDefinition>
            {
                ["location"] = new ParameterDefinition
                {
                    Type = ParameterType.String,
                    Description = "City or location name"
                },
                ["days"] = new ParameterDefinition
                {
                    Type = ParameterType.Integer,
                    Description = "Number of forecast days",
                    Default = 3
                }
            },
            Required = new[] { "location" }
        };
    }
    
    public async Task<ToolResponse> ExecuteAsync(IDictionary<string, object> parameters)
    {
        var location = parameters["location"].ToString();
        var days = parameters.ContainsKey("days") 
            ? Convert.ToInt32(parameters["days"]) 
            : 3;
            
        var forecast = await _weatherService.GetForecastAsync(location, days);
        
        return new ToolResponse
        {
            Content = new List<ContentItem>
            {
                new TextContent(JsonSerializer.Serialize(forecast))
            }
        };
    }
}
```

#### 2. Dosledno ravnanje z napakami

Uvedite robustno ravnanje z napakami z informativnimi sporočili o napakah in ustreznimi mehanizmi za obnovitev.

```python
# Python example with comprehensive error handling
class DataQueryTool:
    def get_name(self):
        return "dataQuery"
        
    def get_description(self):
        return "Queries data from specified database tables"
    
    async def execute(self, parameters):
        try:
            # Parameter validation
            if "query" not in parameters:
                raise ToolParameterError("Missing required parameter: query")
                
            query = parameters["query"]
            
            # Security validation
            if self._contains_unsafe_sql(query):
                raise ToolSecurityError("Query contains potentially unsafe SQL")
            
            try:
                # Database operation with timeout
                async with timeout(10):  # 10 second timeout
                    result = await self._database.execute_query(query)
                    
                return ToolResponse(
                    content=[TextContent(json.dumps(result))]
                )
            except asyncio.TimeoutError:
                raise ToolExecutionError("Database query timed out after 10 seconds")
            except DatabaseConnectionError as e:
                # Connection errors might be transient
                self._log_error("Database connection error", e)
                raise ToolExecutionError(f"Database connection error: {str(e)}")
            except DatabaseQueryError as e:
                # Query errors are likely client errors
                self._log_error("Database query error", e)
                raise ToolExecutionError(f"Invalid query: {str(e)}")
                
        except ToolError:
            # Let tool-specific errors pass through
            raise
        except Exception as e:
            # Catch-all for unexpected errors
            self._log_error("Unexpected error in DataQueryTool", e)
            raise ToolExecutionError(f"An unexpected error occurred: {str(e)}")
    
    def _contains_unsafe_sql(self, query):
        # Implementation of SQL injection detection
        pass
        
    def _log_error(self, message, error):
        # Implementation of error logging
        pass
```

#### 3. Validacija parametrov

Vedno temeljito validirajte parametre, da preprečite nepravilne ali zlonamerne vnose.

```javascript
// JavaScript/TypeScript example with detailed parameter validation
class FileOperationTool {
  getName() {
    return "fileOperation";
  }
  
  getDescription() {
    return "Performs file operations like read, write, and delete";
  }
  
  getDefinition() {
    return {
      name: this.getName(),
      description: this.getDescription(),
      parameters: {
        operation: {
          type: "string",
          description: "Operation to perform",
          enum: ["read", "write", "delete"]
        },
        path: {
          type: "string",
          description: "File path (must be within allowed directories)"
        },
        content: {
          type: "string",
          description: "Content to write (only for write operation)",
          optional: true
        }
      },
      required: ["operation", "path"]
    };
  }
  
  async execute(parameters) {
    // 1. Validate parameter presence
    if (!parameters.operation) {
      throw new ToolError("Missing required parameter: operation");
    }
    
    if (!parameters.path) {
      throw new ToolError("Missing required parameter: path");
    }
    
    // 2. Validate parameter types
    if (typeof parameters.operation !== "string") {
      throw new ToolError("Parameter 'operation' must be a string");
    }
    
    if (typeof parameters.path !== "string") {
      throw new ToolError("Parameter 'path' must be a string");
    }
    
    // 3. Validate parameter values
    const validOperations = ["read", "write", "delete"];
    if (!validOperations.includes(parameters.operation)) {
      throw new ToolError(`Invalid operation. Must be one of: ${validOperations.join(", ")}`);
    }
    
    // 4. Validate content presence for write operation
    if (parameters.operation === "write" && !parameters.content) {
      throw new ToolError("Content parameter is required for write operation");
    }
    
    // 5. Path safety validation
    if (!this.isPathWithinAllowedDirectories(parameters.path)) {
      throw new ToolError("Access denied: path is outside of allowed directories");
    }
    
    // Implementation based on validated parameters
    // ...
  }
  
  isPathWithinAllowedDirectories(path) {
    // Implementation of path safety check
    // ...
  }
}
```

### Primeri implementacije varnosti

#### 1. Avtentikacija in avtorizacija

```java
// Java example with authentication and authorization
public class SecureDataAccessTool implements Tool {
    private final AuthenticationService authService;
    private final AuthorizationService authzService;
    private final DataService dataService;
    
    // Dependency injection
    public SecureDataAccessTool(
            AuthenticationService authService,
            AuthorizationService authzService,
            DataService dataService) {
        this.authService = authService;
        this.authzService = authzService;
        this.dataService = dataService;
    }
    
    @Override
    public String getName() {
        return "secureDataAccess";
    }
    
    @Override
    public ToolResponse execute(ToolRequest request) {
        // 1. Extract authentication context
        String authToken = request.getContext().getAuthToken();
        
        // 2. Authenticate user
        UserIdentity user;
        try {
            user = authService.validateToken(authToken);
        } catch (AuthenticationException e) {
            return ToolResponse.error("Authentication failed: " + e.getMessage());
        }
        
        // 3. Check authorization for the specific operation
        String dataId = request.getParameters().get("dataId").getAsString();
        String operation = request.getParameters().get("operation").getAsString();
        
        boolean isAuthorized = authzService.isAuthorized(user, "data:" + dataId, operation);
        if (!isAuthorized) {
            return ToolResponse.error("Access denied: Insufficient permissions for this operation");
        }
        
        // 4. Proceed with authorized operation
        try {
            switch (operation) {
                case "read":
                    Object data = dataService.getData(dataId, user.getId());
                    return ToolResponse.success(data);
                case "update":
                    JsonNode newData = request.getParameters().get("newData");
                    dataService.updateData(dataId, newData, user.getId());
                    return ToolResponse.success("Data updated successfully");
                default:
                    return ToolResponse.error("Unsupported operation: " + operation);
            }
        } catch (Exception e) {
            return ToolResponse.error("Operation failed: " + e.getMessage());
        }
    }
}
```

#### 2. Omejevanje hitrosti

```csharp
// C# rate limiting implementation
public class RateLimitingMiddleware
{
    private readonly RequestDelegate _next;
    private readonly IMemoryCache _cache;
    private readonly ILogger<RateLimitingMiddleware> _logger;
    
    // Configuration options
    private readonly int _maxRequestsPerMinute;
    
    public RateLimitingMiddleware(
        RequestDelegate next,
        IMemoryCache cache,
        ILogger<RateLimitingMiddleware> logger,
        IConfiguration config)
    {
        _next = next;
        _cache = cache;
        _logger = logger;
        _maxRequestsPerMinute = config.GetValue<int>("RateLimit:MaxRequestsPerMinute", 60);
    }
    
    public async Task InvokeAsync(HttpContext context)
    {
        // 1. Get client identifier (API key or user ID)
        string clientId = GetClientIdentifier(context);
        
        // 2. Get rate limiting key for this minute
        string cacheKey = $"rate_limit:{clientId}:{DateTime.UtcNow:yyyyMMddHHmm}";
        
        // 3. Check current request count
        if (!_cache.TryGetValue(cacheKey, out int requestCount))
        {
            requestCount = 0;
        }
        
        // 4. Enforce rate limit
        if (requestCount >= _maxRequestsPerMinute)
        {
            _logger.LogWarning("Rate limit exceeded for client {ClientId}", clientId);
            
            context.Response.StatusCode = StatusCodes.Status429TooManyRequests;
            context.Response.Headers.Add("Retry-After", "60");
            
            await context.Response.WriteAsJsonAsync(new
            {
                error = "Rate limit exceeded",
                message = "Too many requests. Please try again later.",
                retryAfterSeconds = 60
            });
            
            return;
        }
        
        // 5. Increment request count
        _cache.Set(cacheKey, requestCount + 1, TimeSpan.FromMinutes(2));
        
        // 6. Add rate limit headers
        context.Response.Headers.Add("X-RateLimit-Limit", _maxRequestsPerMinute.ToString());
        context.Response.Headers.Add("X-RateLimit-Remaining", (_maxRequestsPerMinute - requestCount - 1).ToString());
        
        // 7. Continue with the request
        await _next(context);
    }
    
    private string GetClientIdentifier(HttpContext context)
    {
        // Implementation to extract API key or user ID
        // ...
    }
}
```

## Najboljše prakse testiranja

### 1. Enotno testiranje MCP orodij

Vedno testirajte orodja izolirano, z uporabo lažnih zunanjih odvisnosti:

```typescript
// TypeScript example of a tool unit test
describe('WeatherForecastTool', () => {
  let tool: WeatherForecastTool;
  let mockWeatherService: jest.Mocked<IWeatherService>;
  
  beforeEach(() => {
    // Create a mock weather service
    mockWeatherService = {
      getForecasts: jest.fn()
    } as any;
    
    // Create the tool with the mock dependency
    tool = new WeatherForecastTool(mockWeatherService);
  });
  
  it('should return weather forecast for a location', async () => {
    // Arrange
    const mockForecast = {
      location: 'Seattle',
      forecasts: [
        { date: '2025-07-16', temperature: 72, conditions: 'Sunny' },
        { date: '2025-07-17', temperature: 68, conditions: 'Partly Cloudy' },
        { date: '2025-07-18', temperature: 65, conditions: 'Rain' }
      ]
    };
    
    mockWeatherService.getForecasts.mockResolvedValue(mockForecast);
    
    // Act
    const response = await tool.execute({
      location: 'Seattle',
      days: 3
    });
    
    // Assert
    expect(mockWeatherService.getForecasts).toHaveBeenCalledWith('Seattle', 3);
    expect(response.content[0].text).toContain('Seattle');
    expect(response.content[0].text).toContain('Sunny');
  });
  
  it('should handle errors from the weather service', async () => {
    // Arrange
    mockWeatherService.getForecasts.mockRejectedValue(new Error('Service unavailable'));
    
    // Act & Assert
    await expect(tool.execute({
      location: 'Seattle',
      days: 3
    })).rejects.toThrow('Weather service error: Service unavailable');
  });
});
```

### 2. Integracijsko testiranje

Testirajte celoten potek od zahtevkov odjemalca do odgovorov strežnika:

```python
# Python integration test example
@pytest.mark.asyncio
async def test_mcp_server_integration():
    # Start a test server
    server = McpServer()
    server.register_tool(WeatherForecastTool(MockWeatherService()))
    await server.start(port=5000)
    
    try:
        # Create a client
        client = McpClient("http://localhost:5000")
        
        # Test tool discovery
        tools = await client.discover_tools()
        assert "weatherForecast" in [t.name for t in tools]
        
        # Test tool execution
        response = await client.execute_tool("weatherForecast", {
            "location": "Seattle",
            "days": 3
        })
        
        # Verify response
        assert response.status_code == 200
        assert "Seattle" in response.content[0].text
        assert len(json.loads(response.content[0].text)["forecasts"]) == 3
        
    finally:
        # Clean up
        await server.stop()
```

## Optimizacija zmogljivosti

### 1. Strategije predpomnjenja

Uvedite ustrezno predpomnjenje za zmanjšanje zakasnitve in porabe virov:

```csharp
// C# example with caching
public class CachedWeatherTool : ITool
{
    private readonly IWeatherService _weatherService;
    private readonly IDistributedCache _cache;
    private readonly ILogger<CachedWeatherTool> _logger;
    
    public CachedWeatherTool(
        IWeatherService weatherService,
        IDistributedCache cache,
        ILogger<CachedWeatherTool> logger)
    {
        _weatherService = weatherService;
        _cache = cache;
        _logger = logger;
    }
    
    public string Name => "weatherForecast";
    
    public async Task<ToolResponse> ExecuteAsync(IDictionary<string, object> parameters)
    {
        var location = parameters["location"].ToString();
        var days = Convert.ToInt32(parameters.GetValueOrDefault("days", 3));
        
        // Create cache key
        string cacheKey = $"weather:{location}:{days}";
        
        // Try to get from cache
        string cachedForecast = await _cache.GetStringAsync(cacheKey);
        if (!string.IsNullOrEmpty(cachedForecast))
        {
            _logger.LogInformation("Cache hit for weather forecast: {Location}", location);
            return new ToolResponse
            {
                Content = new List<ContentItem>
                {
                    new TextContent(cachedForecast)
                }
            };
        }
        
        // Cache miss - get from service
        _logger.LogInformation("Cache miss for weather forecast: {Location}", location);
        var forecast = await _weatherService.GetForecastAsync(location, days);
        string forecastJson = JsonSerializer.Serialize(forecast);
        
        // Store in cache (weather forecasts valid for 1 hour)
        await _cache.SetStringAsync(
            cacheKey,
            forecastJson,
            new DistributedCacheEntryOptions
            {
                AbsoluteExpirationRelativeToNow = TimeSpan.FromHours(1)
            });
        
        return new ToolResponse
        {
            Content = new List<ContentItem>
            {
                new TextContent(forecastJson)
            }
        };
    }
}

#### 2. Dependency Injection and Testability

Design tools to receive their dependencies through constructor injection, making them testable and configurable:

```java
// Primer v Javi z injiciranjem odvisnosti
public class CurrencyConversionTool implements Tool {
    private final ExchangeRateService exchangeService;
    private final CacheService cacheService;
    private final Logger logger;
    
    // Odvisnosti se injicirajo preko konstruktorja
    public CurrencyConversionTool(
            ExchangeRateService exchangeService,
            CacheService cacheService,
            Logger logger) {
        this.exchangeService = exchangeService;
        this.cacheService = cacheService;
        this.logger = logger;
    }
    
    // Implementacija orodja
    // ...
}
```

#### 3. Composable Tools

Design tools that can be composed together to create more complex workflows:

```python
# Primer v Pythonu, ki prikazuje sestavljiva orodja
class DataFetchTool(Tool):
    def get_name(self):
        return "dataFetch"
    
    # Implementacija...

class DataAnalysisTool(Tool):
    def get_name(self):
        return "dataAnalysis"
    
    # To orodje lahko uporablja rezultate orodja dataFetch
    async def execute_async(self, request):
        # Implementacija...
        pass

class DataVisualizationTool(Tool):
    def get_name(self):
        return "dataVisualize"
    
    # To orodje lahko uporablja rezultate orodja dataAnalysis
    async def execute_async(self, request):
        # Implementacija...
        pass

# Ta orodja se lahko uporabljajo samostojno ali kot del delovnega toka
```

### Schema Design Best Practices

The schema is the contract between the model and your tool. Well-designed schemas lead to better tool usability.

#### 1. Clear Parameter Descriptions

Always include descriptive information for each parameter:

```csharp
public object GetSchema()
{
    return new {
        type = "object",
        properties = new {
            query = new { 
                type = "string", 
                description = "Besedilo iskalnega poizvedbe. Uporabite natančne ključne besede za boljše rezultate." 
            },
            filters = new {
                type = "object",
                description = "Neobvezni filtri za zožitev rezultatov iskanja",
                properties = new {
                    dateRange = new { 
                        type = "string", 
                        description = "Obdobje v formatu YYYY-MM-DD:YYYY-MM-DD" 
                    },
                    category = new { 
                        type = "string", 
                        description = "Ime kategorije za filtriranje" 
                    }
                }
            },
            limit = new { 
                type = "integer", 
                description = "Največje število vrnjenih rezultatov (1-50)",
                default = 10
            }
        },
        required = new[] { "query" }
    };
}
```

#### 2. Validation Constraints

Include validation constraints to prevent invalid inputs:

```java
Map<String, Object> getSchema() {
    Map<String, Object> schema = new HashMap<>();
    schema.put("type", "object");
    
    Map<String, Object> properties = new HashMap<>();
    
    // Lastnost e-pošte z validacijo formata
    Map<String, Object> email = new HashMap<>();
    email.put("type", "string");
    email.put("format", "email");
    email.put("description", "E-poštni naslov uporabnika");
    
    // Lastnost starosti z numeričnimi omejitvami
    Map<String, Object> age = new HashMap<>();
    age.put("type", "integer");
    age.put("minimum", 13);
    age.put("maximum", 120);
    age.put("description", "Starost uporabnika v letih");
    
    // Enumerirana lastnost
    Map<String, Object> subscription = new HashMap<>();
    subscription.put("type", "string");
    subscription.put("enum", Arrays.asList("free", "basic", "premium"));
    subscription.put("default", "free");
    subscription.put("description", "Nivo naročnine");
    
    properties.put("email", email);
    properties.put("age", age);
    properties.put("subscription", subscription);
    
    schema.put("properties", properties);
    schema.put("required", Arrays.asList("email"));
    
    return schema;
}
```

#### 3. Consistent Return Structures

Maintain consistency in your response structures to make it easier for models to interpret results:

```python
async def execute_async(self, request):
    try:
        # Obdelava zahtevka
        results = await self._search_database(request.parameters["query"])
        
        # Vedno vrni dosledno strukturo
        return ToolResponse(
            result={
                "matches": [self._format_item(item) for item in results],
                "totalCount": len(results),
                "queryTime": calculation_time_ms,
                "status": "success"
            }
        )
    except Exception as e:
        return ToolResponse(
            result={
                "matches": [],
                "totalCount": 0,
                "queryTime": 0,
                "status": "error",
                "error": str(e)
            }
        )
    
def _format_item(self, item):
    """Zagotavlja, da ima vsak element dosledno strukturo"""
    return {
        "id": item.id,
        "title": item.title,
        "summary": item.summary[:100] + "..." if len(item.summary) > 100 else item.summary,
        "url": item.url,
        "relevance": item.score
    }
```

### Error Handling

Robust error handling is crucial for MCP tools to maintain reliability.

#### 1. Graceful Error Handling

Handle errors at appropriate levels and provide informative messages:

```csharp
public async Task<ToolResponse> ExecuteAsync(ToolRequest request)
{
    try
    {
        string fileId = request.Parameters.GetProperty("fileId").GetString();
        
        try
        {
            var fileData = await _fileService.GetFileAsync(fileId);
            return new ToolResponse { 
                Result = JsonSerializer.SerializeToElement(fileData) 
            };
        }
        catch (FileNotFoundException)
        {
            throw new ToolExecutionException($"Datoteka ni najdena: {fileId}");
        }
        catch (UnauthorizedAccessException)
        {
            throw new ToolExecutionException("Nimate dovoljenja za dostop do te datoteke");
        }
        catch (Exception ex) when (ex is IOException || ex is TimeoutException)
        {
            _logger.LogError(ex, "Napaka pri dostopu do datoteke {FileId}", fileId);
            throw new ToolExecutionException("Napaka pri dostopu do datoteke: storitev je začasno nedosegljiva");
        }
    }
    catch (JsonException)
    {
        throw new ToolExecutionException("Neveljavna oblika ID datoteke");
    }
    catch (Exception ex)
    {
        _logger.LogError(ex, "Nepričakovana napaka v FileAccessTool");
        throw new ToolExecutionException("Prišlo je do nepričakovane napake");
    }
}
```

#### 2. Structured Error Responses

Return structured error information when possible:

```java
@Override
public ToolResponse execute(ToolRequest request) {
    try {
        // Implementacija
    } catch (Exception ex) {
        Map<String, Object> errorResult = new HashMap<>();
        
        errorResult.put("success", false);
        
        if (ex instanceof ValidationException) {
            ValidationException validationEx = (ValidationException) ex;
            
            errorResult.put("errorType", "validation");
            errorResult.put("errorMessage", validationEx.getMessage());
            errorResult.put("validationErrors", validationEx.getErrors());
            
            return new ToolResponse.Builder()
                .setResult(errorResult)
                .build();
        }
        
        // Ponovno vrzi druge izjeme kot ToolExecutionException
        throw new ToolExecutionException("Izvajanje orodja ni uspelo: " + ex.getMessage(), ex);
    }
}
```

#### 3. Retry Logic

Implement appropriate retry logic for transient failures:

```python
async def execute_async(self, request):
    max_retries = 3
    retry_count = 0
    base_delay = 1  # sekunde
    
    while retry_count < max_retries:
        try:
            # Klic zunanjega API-ja
            return await self._call_api(request.parameters)
        except TransientError as e:
            retry_count += 1
            if retry_count >= max_retries:
                raise ToolExecutionException(f"Operacija ni uspela po {max_retries} poskusih: {str(e)}")
                
            # Eksponentna zakasnitev
            delay = base_delay * (2 ** (retry_count - 1))
            logging.warning(f"Prehodna napaka, ponovni poskus čez {delay}s: {str(e)}")
            await asyncio.sleep(delay)
        except Exception as e:
            # Neprehodna napaka, brez ponovnega poskusa
            raise ToolExecutionException(f"Operacija ni uspela: {str(e)}")
```

### Performance Optimization

#### 1. Caching

Implement caching for expensive operations:

```csharp
public class CachedDataTool : IMcpTool
{
    private readonly IDatabase _database;
    private readonly IMemoryCache _cache;
    
    public CachedDataTool(IDatabase database, IMemoryCache cache)
    {
        _database = database;
        _cache = cache;
    }
    
    public async Task

ExecuteAsync(ToolRequest request)
    {
        var query = request.Parameters.GetProperty("query").GetString();
        
        // Ustvari ključ predpomnilnika na podlagi parametrov
        var cacheKey = $"data_query_{ComputeHash(query)}";
        
        // Najprej poskusi pridobiti iz predpomnilnika
        if (_cache.TryGetValue(cacheKey, out var cachedResult))
        {
            return new ToolResponse { Result = cachedResult };
        }
        
        // Ni v predpomnilniku - izvede dejanski poizvedbo
        var result = await _database.QueryAsync(query);
        
        // Shrani v predpomnilnik z rokom veljavnosti
        var cacheOptions = new MemoryCacheEntryOptions()
            .SetAbsoluteExpiration(TimeSpan.FromMinutes(15));
            
        _cache.Set(cacheKey, JsonSerializer.SerializeToElement(result), cacheOptions);
        
        return new ToolResponse { Result = JsonSerializer.SerializeToElement(result) };
    }
    
    private string ComputeHash(string input)
    {
        // Implementacija za generiranje stabilnega hasha za ključ predpomnilnika
    }
}
```

#### 2. Asynchronous Processing

Use asynchronous programming patterns for I/O-bound operations:

```java
public class AsyncDocumentProcessingTool implements Tool {
    private final DocumentService documentService;
    private final ExecutorService executorService;
    
    @Override
    public ToolResponse execute(ToolRequest request) {
        String documentId = request.getParameters().get("documentId").asText();
        
        // Za dolgotrajne operacije takoj vrni ID procesa
        String processId = UUID.randomUUID().toString();
        
        // Začni asinhrono obdelavo
        CompletableFuture.runAsync(() -> {
            try {
                // Izvedi dolgotrajno operacijo
                documentService.processDocument(documentId);
                
                // Posodobi status (običajno shranjeno v bazi podatkov)
                processStatusRepository.updateStatus(processId, "completed");
            } catch (Exception ex) {
                processStatusRepository.updateStatus(processId, "failed", ex.getMessage());
            }
        }, executorService);
        
        // Vrni takojšen odgovor z ID procesa
        Map<String, Object> result = new HashMap<>();
        result.put("processId", processId);
        result.put("status", "processing");
        result.put("estimatedCompletionTime", ZonedDateTime.now().plusMinutes(5));
        
        return new ToolResponse.Builder().setResult(result).build();
    }
    
    // Pomožno orodje za preverjanje statusa
    public class ProcessStatusTool implements Tool {
        @Override
        public ToolResponse execute(ToolRequest request) {
            String processId = request.getParameters().get("processId").asText();
            ProcessStatus status = processStatusRepository.getStatus(processId);
            
            return new ToolResponse.Builder().setResult(status).build();
        }
    }
}
```

#### 3. Resource Throttling

Implement resource throttling to prevent overload:

```python
class ThrottledApiTool(Tool):
    def __init__(self):
        self.rate_limiter = TokenBucketRateLimiter(
            tokens_per_second=5,  # Dovoli 5 zahtevkov na sekundo
            bucket_size=10        # Dovoli sunke do 10 zahtevkov
        )
    
    async def execute_async(self, request):
        # Preveri, ali lahko nadaljujemo ali moramo počakati
        delay = self.rate_limiter.get_delay_time()
        
        if delay > 0:
            if delay > 2.0:  # Če je čakanje predolgo
                raise ToolExecutionException(
                    f"Presežena omejitev hitrosti. Poskusite znova čez {delay:.1f} sekund."
                )
            else:
                # Počakaj ustrezno časovno zamudo
                await asyncio.sleep(delay)
        
        # Porabi en žeton in nadaljuj z zahtevkom
        self.rate_limiter.consume()
        
        # Pokliči API
        result = await self._call_api(request.parameters)
        return ToolResponse(result=result)

class TokenBucketRateLimiter:
    def __init__(self, tokens_per_second, bucket_size):
        self.tokens_per_second = tokens_per_second
        self.bucket_size = bucket_size
        self.tokens = bucket_size
        self.last_refill = time.time()
        self.lock = asyncio.Lock()
    
    async def get_delay_time(self):
        async with self.lock:
            self._refill()
            if self.tokens >= 1:
                return 0
            
            # Izračunaj čas do naslednjega razpoložljivega žetona
            return (1 - self.tokens) / self.tokens_per_second
    
    async def consume(self):
        async with self.lock:
            self._refill()
            self.tokens -= 1
    
    def _refill(self):
        now = time.time()
        elapsed = now - self.last_refill
        
        # Dodaj nove žetone glede na pretečen čas
        new_tokens = elapsed * self.tokens_per_second
        self.tokens = min(self.bucket_size, self.tokens + new_tokens)
        self.last_refill = now
```

### Security Best Practices

#### 1. Input Validation

Always validate input parameters thoroughly:

```csharp
public async Task<ToolResponse> ExecuteAsync(ToolRequest request)
{
    // Preveri, ali parametri obstajajo
    if (!request.Parameters.TryGetProperty("query", out var queryProp))
    {
        throw new ToolExecutionException("Manjka zahtevan parameter: query");
    }
    
    // Preveri pravilen tip
    if (queryProp.ValueKind != JsonValueKind.String)
    {
        throw new ToolExecutionException("Parameter query mora biti niz");
    }
    
    var query = queryProp.GetString();
    
    // Preveri vsebino niza
    if (string.IsNullOrWhiteSpace(query))
    {
        throw new ToolExecutionException("Parameter query ne sme biti prazen");
    }
    
    if (query.Length > 500)
    {
        throw new ToolExecutionException("Parameter query presega največjo dolžino 500 znakov");
    }
    
    // Preveri morebitne SQL injekcije, če je primerno
    if (ContainsSqlInjection(query))
    {
        throw new ToolExecutionException("Neveljavna poizvedba: vsebuje potencialno nevaren SQL");
    }
    
    // Nadaljuj z izvajanjem
    // ...
}
```

#### 2. Authorization Checks

Implement proper authorization checks:

```java
@Override
public ToolResponse execute(ToolRequest request) {
    // Pridobi uporabniški kontekst iz zahteve
    UserContext user = request.getContext().getUserContext();
    
    // Preveri, ali ima uporabnik potrebna dovoljenja
    if (!authorizationService.hasPermission(user, "documents:read")) {
        throw new ToolExecutionException("Uporabnik nima dovoljenja za dostop do dokumentov");
    }
    
    // Za določene vire preveri dostop do tega vira
    String documentId = request.getParameters().get("documentId").asText();
    if (!documentService.canUserAccess(user.getId(), documentId)) {
        throw new ToolExecutionException("Dostop do zahtevanega dokumenta zavrnjen");
    }
    
    // Nadaljuj z izvajanjem orodja
    // ...
}
```

#### 3. Sensitive Data Handling

Handle sensitive data carefully:

```python
class SecureDataTool(Tool):
    def get_schema(self):
        return {
            "type": "object",
            "properties": {
                "userId": {"type": "string"},
                "includeSensitiveData": {"type": "boolean", "default": False}
            },
            "required": ["userId"]
        }
    
    async def execute_async(self, request):
        user_id = request.parameters["userId"]
        include_sensitive = request.parameters.get("includeSensitiveData", False)
        
        # Pridobi uporabniške podatke
        user_data = await self.user_service.get_user_data(user_id)
        
        # Filtriraj občutljiva polja, razen če so izrecno zahtevana IN je uporabnik pooblaščen
        if not include_sensitive or not self._is_authorized_for_sensitive_data(request):
            user_data = self._redact_sensitive_fields(user_data)
        
        return ToolResponse(result=user_data)
    
    def _is_authorized_for_sensitive_data(self, request):
        # Preveri raven pooblastila v kontekstu zahteve
        auth_level = request.context.get("authorizationLevel")
        return auth_level == "admin"
    
    def _redact_sensitive_fields(self, user_data):
        # Ustvari kopijo, da ne spremeniš izvirnika
        redacted = user_data.copy()
        
        # Prekrij določena občutljiva polja
        sensitive_fields = ["ssn", "creditCardNumber", "password"]
        for field in sensitive_fields:
            if field in redacted:
                redacted[field] = "REDACTED"
        
        # Prekrij gnezdene občutljive podatke
        if "financialInfo" in redacted:
            redacted["financialInfo"] = {"available": True, "accessRestricted": True}
        
        return redacted
```

## Testing Best Practices for MCP Tools

Comprehensive testing ensures that MCP tools function correctly, handle edge cases, and integrate properly with the rest of the system.

### Unit Testing

#### 1. Test Each Tool in Isolation

Create focused tests for each tool's functionality:

```csharp
[Fact]
public async Task WeatherTool_ValidLocation_ReturnsCorrectForecast()
{
    // Priprava
    var mockWeatherService = new Mock<IWeatherService>();
    mockWeatherService
        .Setup(s => s.GetForecastAsync("Seattle", 3))
        .ReturnsAsync(new WeatherForecast(/* testni podatki */));
    
    var tool = new WeatherForecastTool(mockWeatherService.Object);
    
    var request = new ToolRequest(
        toolName: "weatherForecast",
        parameters: JsonSerializer.SerializeToElement(new { 
            location = "Seattle", 
            days = 3 
        })
    );
    
    // Izvedba
    var response = await tool.ExecuteAsync(request);
    
    // Preverjanje
    Assert.NotNull(response);
    var result = JsonSerializer.Deserialize<WeatherForecast>(response.Result);
    Assert.Equal("Seattle", result.Location);
    Assert.Equal(3, result.DailyForecasts.Count);
}

[Fact]
public async Task WeatherTool_InvalidLocation_ThrowsToolExecutionException()
{
    // Priprava
    var mockWeatherService = new Mock<IWeatherService>();
    mockWeatherService
        .Setup(s => s.GetForecastAsync("InvalidLocation", It.IsAny<int>()))
        .ThrowsAsync(new LocationNotFoundException("Lokacija ni bila najdena"));
    
    var tool = new WeatherForecastTool(mockWeatherService.Object);
    
    var request = new ToolRequest(
        toolName: "weatherForecast",
        parameters: JsonSerializer.SerializeToElement(new { 
            location = "InvalidLocation", 
            days = 3 
        })
    );
    
    // Izvedba in preverjanje
    var exception = await Assert.ThrowsAsync<ToolExecutionException>(
        () => tool.ExecuteAsync(request)
    );
    
    Assert.Contains("Lokacija ni bila najdena", exception.Message);
}
```

#### 2. Schema Validation Testing

Test that schemas are valid and properly enforce constraints:

```java
@Test
public void testSchemaValidation() {
    // Ustvari instanco orodja
    SearchTool searchTool = new SearchTool();
    
    // Pridobi shemo
    Object schema = searchTool.getSchema();
    
    // Pretvori shemo v JSON za validacijo
    String schemaJson = objectMapper.writeValueAsString(schema);
    
    // Preveri, da je shema veljavna JSONShema
    JsonSchemaFactory factory = JsonSchemaFactory.byDefault();
    JsonSchema jsonSchema = factory.getJsonSchema(schemaJson);
    
    // Testiraj veljavne parametre
    JsonNode validParams = objectMapper.createObjectNode()
        .put("query", "test query")
        .put("limit", 5);
        
    ProcessingReport validReport = jsonSchema.validate(validParams);
    assertTrue(validReport.isSuccess());
    
    // Testiraj manjkajoči zahtevan parameter
    JsonNode missingRequired = objectMapper.createObjectNode()
        .put("limit", 5);
        
    ProcessingReport missingReport = jsonSchema.validate(missingRequired);
    assertFalse(missingReport.isSuccess());
    
    // Testiraj neveljaven tip parametra
    JsonNode invalidType = objectMapper.createObjectNode()
        .put("query", "test")
        .put("limit", "not-a-number");
        
    ProcessingReport invalidReport = jsonSchema.validate(invalidType);
    assertFalse(invalidReport.isSuccess());
}
```

#### 3. Error Handling Tests

Create specific tests for error conditions:

```python
@pytest.mark.asyncio
async def test_api_tool_handles_timeout():
    # Priprava
    tool = ApiTool(timeout=0.1)  # Zelo kratek timeout
    
    # Mock zahtevek, ki bo potekel
    with aioresponses() as mocked:
        mocked.get(
            "https://api.example.com/data",
            callback=lambda *args, **kwargs: asyncio.sleep(0.5)  # Daljše od timeouta
        )
        
        request = ToolRequest(
            tool_name="apiTool",
            parameters={"url": "https://api.example.com/data"}
        )
        
        # Izvedba in preverjanje
        with pytest.raises(ToolExecutionException) as exc_info:
            await tool.execute_async(request)
        
        # Preveri sporočilo o izjema
        assert "timed out" in str(exc_info.value).lower()

@pytest.mark.asyncio
async def test_api_tool_handles_rate_limiting():
    # Priprava
    tool = ApiTool()
    
    # Mock odgovor z omejitvijo hitrosti
    with aioresponses() as mocked:
        mocked.get(
            "https://api.example.com/data",
            status=429,
            headers={"Retry-After": "2"},
            body=json.dumps({"error": "Rate limit exceeded"})
        )
        
        request = ToolRequest(
            tool_name="apiTool",
            parameters={"url": "https://api.example.com/data"}
        )
        
        # Izvedba in preverjanje
        with pytest.raises(ToolExecutionException) as exc_info:
            await tool.execute_async(request)
        
        # Preveri, da izjema vsebuje informacije o omejitvi hitrosti
        error_msg = str(exc_info.value).lower()
        assert "rate limit" in error_msg
        assert "try again" in error_msg
```

### Integration Testing

#### 1. Tool Chain Testing

Test tools working together in expected combinations:

```csharp
[Fact]
public async Task DataProcessingWorkflow_CompletesSuccessfully()
{
    // Priprava
    var dataFetchTool = new DataFetchTool(mockDataService.Object);
    var analysisTools = new DataAnalysisTool(mockAnalysisService.Object);
    var visualizationTool = new DataVisualizationTool(mockVisualizationService.Object);
    
    var toolRegistry = new ToolRegistry();
    toolRegistry.RegisterTool(dataFetchTool);
    toolRegistry.RegisterTool(analysisTools);
    toolRegistry.RegisterTool(visualizationTool);
    
    var workflowExecutor = new WorkflowExecutor(toolRegistry);
    
    // Izvedba
var result = await workflowExecutor.ExecuteWorkflowAsync(new[] {
    new ToolCall("dataFetch", new { source = "sales2023" }),
    new ToolCall("dataAnalysis", ctx =>
        new { 
            data = ctx.GetResult("dataFetch"),
            analysis = "trend" 
        }),
    new ToolCall("dataVisualize", ctx => new {
        analysisResult = ctx.GetResult("dataAnalysis"),
        type = "line-chart"
    })
});

// Preveri
Assert.NotNull(result);
Assert.True(result.Success);
Assert.NotNull(result.GetResult("dataVisualize"));
Assert.Contains("chartUrl", result.GetResult("dataVisualize").ToString());
}
```

#### 2. MCP Server Testing

Test the MCP server with full tool registration and execution:

```java
@SpringBootTest
@AutoConfigureMockMvc
public class McpServerIntegrationTest {
    
    @Autowired
    private MockMvc mockMvc;
    
    @Autowired
    private ObjectMapper objectMapper;
    
    @Test
    public void testToolDiscovery() throws Exception {
        // Preizkusi endpoint za odkrivanje orodij
        mockMvc.perform(get("/mcp/tools"))
            .andExpect(status().isOk())
            .andExpect(jsonPath("$.tools").isArray())
            .andExpect(jsonPath("$.tools[*].name").value(hasItems(
                "weatherForecast", "calculator", "documentSearch"
            )));
    }
    
    @Test
    public void testToolExecution() throws Exception {
        // Ustvari zahtevo za orodje
        Map<String, Object> request = new HashMap<>();
        request.put("toolName", "calculator");
        
        Map<String, Object> parameters = new HashMap<>();
        parameters.put("operation", "add");
        parameters.put("a", 5);
        parameters.put("b", 7);
        request.put("parameters", parameters);
        
        // Pošlji zahtevo in preveri odgovor
        mockMvc.perform(post("/mcp/execute")
            .contentType(MediaType.APPLICATION_JSON)
            .content(objectMapper.writeValueAsString(request)))
            .andExpect(status().isOk())
            .andExpect(jsonPath("$.result.value").value(12));
    }
    
    @Test
    public void testToolValidation() throws Exception {
        // Ustvari neveljavno zahtevo za orodje
        Map<String, Object> request = new HashMap<>();
        request.put("toolName", "calculator");
        
        Map<String, Object> parameters = new HashMap<>();
        parameters.put("operation", "divide");
        parameters.put("a", 10);
        // Manjka parameter "b"
        request.put("parameters", parameters);
        
        // Pošlji zahtevo in preveri napako v odgovoru
        mockMvc.perform(post("/mcp/execute")
            .contentType(MediaType.APPLICATION_JSON)
            .content(objectMapper.writeValueAsString(request)))
            .andExpect(status().isBadRequest())
            .andExpect(jsonPath("$.error").exists());
    }
}
```

#### 3. End-to-End Testing

Test complete workflows from model prompt to tool execution:

```python
@pytest.mark.asyncio
async def test_model_interaction_with_tool():
    # Priprava - nastavi MCP klienta in lažni model
    mcp_client = McpClient(server_url="http://localhost:5000")
    
    # Lažni odgovori modela
    mock_model = MockLanguageModel([
        MockResponse(
            "Kakšno je vreme v Seattlu?",
            tool_calls=[{
                "tool_name": "weatherForecast",
                "parameters": {"location": "Seattle", "days": 3}
            }]
        ),
        MockResponse(
            "Tukaj je vremenska napoved za Seattle:\n- Danes: 65°F, delno oblačno\n- Jutri: 68°F, sončno\n- Naslednji dan: 62°F, dež",
            tool_calls=[]
        )
    ])
    
    # Lažen odgovor vremenskega orodja
    with aioresponses() as mocked:
        mocked.post(
            "http://localhost:5000/mcp/execute",
            payload={
                "result": {
                    "location": "Seattle",
                    "forecast": [
                        {"date": "2023-06-01", "temperature": 65, "conditions": "Partly Cloudy"},
                        {"date": "2023-06-02", "temperature": 68, "conditions": "Sunny"},
                        {"date": "2023-06-03", "temperature": 62, "conditions": "Rain"}
                    ]
                }
            }
        )
        
        # Izvedi
        response = await mcp_client.send_prompt(
            "Kakšno je vreme v Seattlu?",
            model=mock_model,
            allowed_tools=["weatherForecast"]
        )
        
        # Preveri
        assert "Seattle" in response.generated_text
        assert "65" in response.generated_text
        assert "Sunny" in response.generated_text
        assert "Rain" in response.generated_text
        assert len(response.tool_calls) == 1
        assert response.tool_calls[0].tool_name == "weatherForecast"
```

### Performance Testing

#### 1. Load Testing

Test how many concurrent requests your MCP server can handle:

```csharp
[Fact]
public async Task McpServer_HandlesHighConcurrency()
{
    // Priprava
    var server = new McpServer(
        name: "TestServer",
        version: "1.0",
        maxConcurrentRequests: 100
    );
    
    server.RegisterTool(new FastExecutingTool());
    await server.StartAsync();
    
    var client = new McpClient("http://localhost:5000");
    
    // Izvedba
    var tasks = new List<Task<McpResponse>>();
    for (int i = 0; i < 1000; i++)
    {
        tasks.Add(client.ExecuteToolAsync("fastTool", new { iteration = i }));
    }
    
    var results = await Task.WhenAll(tasks);
    
    // Preveri
    Assert.Equal(1000, results.Length);
    Assert.All(results, r => Assert.NotNull(r));
}
```

#### 2. Stress Testing

Test the system under extreme load:

```java
@Test
public void testServerUnderStress() {
    int maxUsers = 1000;
    int rampUpTimeSeconds = 60;
    int testDurationSeconds = 300;
    
    // Nastavi JMeter za stresno testiranje
    StandardJMeterEngine jmeter = new StandardJMeterEngine();
    
    // Konfiguriraj testni načrt JMeterja
    HashTree testPlanTree = new HashTree();
    
    // Ustvari testni načrt, skupino niti, samplerje itd.
    TestPlan testPlan = new TestPlan("MCP Server Stress Test");
    testPlanTree.add(testPlan);
    
    ThreadGroup threadGroup = new ThreadGroup();
    threadGroup.setNumThreads(maxUsers);
    threadGroup.setRampUp(rampUpTimeSeconds);
    threadGroup.setScheduler(true);
    threadGroup.setDuration(testDurationSeconds);
    
    testPlanTree.add(threadGroup);
    
    // Dodaj HTTP sampler za izvajanje orodja
    HTTPSampler toolExecutionSampler = new HTTPSampler();
    toolExecutionSampler.setDomain("localhost");
    toolExecutionSampler.setPort(5000);
    toolExecutionSampler.setPath("/mcp/execute");
    toolExecutionSampler.setMethod("POST");
    toolExecutionSampler.addArgument("toolName", "calculator");
    toolExecutionSampler.addArgument("parameters", "{\"operation\":\"add\",\"a\":5,\"b\":7}");
    
    threadGroup.add(toolExecutionSampler);
    
    // Dodaj poslušalce
    SummaryReport summaryReport = new SummaryReport();
    threadGroup.add(summaryReport);
    
    // Zaženi test
    jmeter.configure(testPlanTree);
    jmeter.run();
    
    // Preveri rezultate
    assertEquals(0, summaryReport.getErrorCount());
    assertTrue(summaryReport.getAverage() < 200); // Povprečni odzivni čas < 200ms
    assertTrue(summaryReport.getPercentile(90.0) < 500); // 90. percentil < 500ms
}
```

#### 3. Monitoring and Profiling

Set up monitoring for long-term performance analysis:

```python
# Konfiguracija nadzora za MCP strežnik
def configure_monitoring(server):
    # Nastavi Prometheus metrike
    prometheus_metrics = {
        "request_count": Counter("mcp_requests_total", "Skupno število MCP zahtev"),
        "request_latency": Histogram(
            "mcp_request_duration_seconds", 
            "Trajanje zahtev v sekundah",
            buckets=[0.01, 0.05, 0.1, 0.5, 1.0, 2.5, 5.0, 10.0]
        ),
        "tool_execution_count": Counter(
            "mcp_tool_executions_total", 
            "Število izvedb orodij",
            labelnames=["tool_name"]
        ),
        "tool_execution_latency": Histogram(
            "mcp_tool_duration_seconds", 
            "Trajanje izvajanja orodij v sekundah",
            labelnames=["tool_name"],
            buckets=[0.01, 0.05, 0.1, 0.5, 1.0, 2.5, 5.0, 10.0]
        ),
        "tool_errors": Counter(
            "mcp_tool_errors_total",
            "Napake pri izvajanju orodij",
            labelnames=["tool_name", "error_type"]
        )
    }
    
    # Dodaj middleware za merjenje časa in beleženje metrik
    server.add_middleware(PrometheusMiddleware(prometheus_metrics))
    
    # Izpostavi endpoint za metrike
    @server.router.get("/metrics")
    async def metrics():
        return generate_latest()
    
    return server
```

## MCP Workflow Design Patterns

Well-designed MCP workflows improve efficiency, reliability, and maintainability. Here are key patterns to follow:

### 1. Chain of Tools Pattern

Connect multiple tools in a sequence where each tool's output becomes the input for the next:

```python
# Implementacija verige orodij v Pythonu
class ChainWorkflow:
    def __init__(self, tools_chain):
        self.tools_chain = tools_chain  # Seznam imen orodij za zaporedno izvajanje
    
    async def execute(self, mcp_client, initial_input):
        current_result = initial_input
        all_results = {"input": initial_input}
        
        for tool_name in self.tools_chain:
            # Izvedi vsako orodje v verigi, pri čemer posreduj prejšnji rezultat
            response = await mcp_client.execute_tool(tool_name, current_result)
            
            # Shrani rezultat in ga uporabi kot vhod za naslednje orodje
            all_results[tool_name] = response.result
            current_result = response.result
        
        return {
            "final_result": current_result,
            "all_results": all_results
        }

# Primer uporabe
data_processing_chain = ChainWorkflow([
    "dataFetch",
    "dataCleaner",
    "dataAnalyzer",
    "dataVisualizer"
])

result = await data_processing_chain.execute(
    mcp_client,
    {"source": "sales_database", "table": "transactions"}
)
```

### 2. Dispatcher Pattern

Use a central tool that dispatches to specialized tools based on input:

```csharp
public class ContentDispatcherTool : IMcpTool
{
    private readonly IMcpClient _mcpClient;
    
    public ContentDispatcherTool(IMcpClient mcpClient)
    {
        _mcpClient = mcpClient;
    }
    
    public string Name => "contentProcessor";
    public string Description => "Obdeluje vsebine različnih vrst";
    
    public object GetSchema()
    {
        return new {
            type = "object",
            properties = new {
                content = new { type = "string" },
                contentType = new { 
                    type = "string",
                    enum = new[] { "text", "html", "markdown", "csv", "code" }
                },
                operation = new { 
                    type = "string",
                    enum = new[] { "summarize", "analyze", "extract", "convert" }
                }
            },
            required = new[] { "content", "contentType", "operation" }
        };
    }
    
    public async Task<ToolResponse> ExecuteAsync(ToolRequest request)
    {
        var content = request.Parameters.GetProperty("content").GetString();
        var contentType = request.Parameters.GetProperty("contentType").GetString();
        var operation = request.Parameters.GetProperty("operation").GetString();
        
        // Določi, katero specializirano orodje uporabiti
        string targetTool = DetermineTargetTool(contentType, operation);
        
        // Posreduj specializiranemu orodju
        var specializedResponse = await _mcpClient.ExecuteToolAsync(
            targetTool,
            new { content, options = GetOptionsForTool(targetTool, operation) }
        );
        
        return new ToolResponse { Result = specializedResponse.Result };
    }
    
    private string DetermineTargetTool(string contentType, string operation)
    {
        return (contentType, operation) switch
        {
            ("text", "summarize") => "textSummarizer",
            ("text", "analyze") => "textAnalyzer",
            ("html", _) => "htmlProcessor",
            ("markdown", _) => "markdownProcessor",
            ("csv", _) =>
# csvProcessor

csvProcessor je orodje za enostavno obdelavo CSV datotek v vaših projektih.

## Funkcije

- Branje CSV datotek
- Filtriranje vrstic glede na pogoje
- Izvoz spremenjenih podatkov nazaj v CSV format

## Kako začeti

1. Namestite csvProcessor z ukazom:

   ```
   npm install csvProcessor
   ```

2. Uvozite modul v vašo datoteko:

   ```javascript
   const csvProcessor = require('csvProcessor');
   ```

3. Naložite CSV datoteko:

   ```javascript
   const data = csvProcessor.read('podatki.csv');
   ```

## Primer uporabe

```javascript
// Filtriraj vrstice, kjer je vrednost v stolpcu "starost" večja od 30
const filteredData = csvProcessor.filter(data, row => row.starost > 30);

// Izvozi filtrirane podatke v novo CSV datoteko
csvProcessor.write(filteredData, 'filtrirani_podatki.csv');
```

## Opombe

[!NOTE] csvProcessor trenutno podpira samo CSV datoteke z ločilom vejica (,).

[!WARNING] Prepričajte se, da so vse vrstice v vaši CSV datoteki pravilno oblikovane, da se izognete napakam pri branju.

## Nasveti

[!TIP] Za boljšo zmogljivost obdelave velikih datotek uporabite stream način, ki ga ponuja csvProcessor.
            ("code", _) => "codeAnalyzer",
            _ => throw new ToolExecutionException($"Ni orodja za {contentType}/{operation}")
        };
    }
    
    private object GetOptionsForTool(string toolName, string operation)
    {
        // Vrni ustrezne možnosti za vsako specializirano orodje
        return toolName switch
        {
            "textSummarizer" => new { length = "medium" },
            "htmlProcessor" => new { cleanUp = true, operation },
            // Možnosti za druga orodja...
            _ => new { }
        };
    }
}
```

### 3. Parallel Processing Pattern

Execute multiple tools simultaneously for efficiency:

```java
public class ParallelDataProcessingWorkflow {
    private final McpClient mcpClient;
    
    public ParallelDataProcessingWorkflow(McpClient mcpClient) {
        this.mcpClient = mcpClient;
    }
    
    public WorkflowResult execute(String datasetId) {
        // Korak 1: Pridobi metapodatke nabora podatkov (sinhrono)
        ToolResponse metadataResponse = mcpClient.executeTool("datasetMetadata", 
            Map.of("datasetId", datasetId));
        
        // Korak 2: Zaženi več analiz vzporedno
        CompletableFuture<ToolResponse> statisticalAnalysis = CompletableFuture.supplyAsync(() ->
            mcpClient.executeTool("statisticalAnalysis", Map.of(
                "datasetId", datasetId,
                "type", "comprehensive"
            ))
        );
        
        CompletableFuture<ToolResponse> correlationAnalysis = CompletableFuture.supplyAsync(() ->
            mcpClient.executeTool("correlationAnalysis", Map.of(
                "datasetId", datasetId,
                "method", "pearson"
            ))
        );
        
        CompletableFuture<ToolResponse> outlierDetection = CompletableFuture.supplyAsync(() ->
            mcpClient.executeTool("outlierDetection", Map.of(
                "datasetId", datasetId,
                "sensitivity", "medium"
            ))
        );
        
        // Počakaj, da se vse vzporedne naloge zaključijo
        CompletableFuture<Void> allAnalyses = CompletableFuture.allOf(
            statisticalAnalysis, correlationAnalysis, outlierDetection
        );
        
        allAnalyses.join();  // Počakaj na dokončanje
        
        // Korak 3: Združi rezultate
        Map<String, Object> combinedResults = new HashMap<>();
        combinedResults.put("metadata", metadataResponse.getResult());
        combinedResults.put("statistics", statisticalAnalysis.join().getResult());
        combinedResults.put("correlations", correlationAnalysis.join().getResult());
        combinedResults.put("outliers", outlierDetection.join().getResult());
        
        // Korak 4: Ustvari povzetek poročila
        ToolResponse summaryResponse = mcpClient.executeTool("reportGenerator", 
            Map.of("analysisResults", combinedResults));
        
        // Vrni celoten rezultat poteka dela
        WorkflowResult result = new WorkflowResult();
        result.setDatasetId(datasetId);
        result.setAnalysisResults(combinedResults);
        result.setSummaryReport(summaryResponse.getResult());
        
        return result;
    }
}
```

### 4. Error Recovery Pattern

Implement graceful fallbacks for tool failures:

```python
class ResilientWorkflow:
    def __init__(self, mcp_client):
        self.client = mcp_client
    
    async def execute_with_fallback(self, primary_tool, fallback_tool, parameters):
        try:
            # Najprej poskusi primarno orodje
            response = await self.client.execute_tool(primary_tool, parameters)
            return {
                "result": response.result,
                "source": "primary",
                "tool": primary_tool
            }
        except ToolExecutionException as e:
            # Zabeleži neuspeh
            logging.warning(f"Primarno orodje '{primary_tool}' ni uspelo: {str(e)}")
            
            # Preklopi na rezervno orodje
            try:
                # Morda bo treba prilagoditi parametre za rezervno orodje
                fallback_params = self._adapt_parameters(parameters, primary_tool, fallback_tool)
                
                response = await self.client.execute_tool(fallback_tool, fallback_params)
                return {
                    "result": response.result,
                    "source": "fallback",
                    "tool": fallback_tool,
                    "primaryError": str(e)
                }
            except ToolExecutionException as fallback_error:
                # Obe orodji sta spodleteli
                logging.error(f"Obe orodji, primarno in rezervno, sta spodleteli. Napaka rezervnega orodja: {str(fallback_error)}")
                raise WorkflowExecutionException(
                    f"Potek dela ni uspel: primarna napaka: {str(e)}; napaka rezervnega orodja: {str(fallback_error)}"
                )
    
    def _adapt_parameters(self, params, from_tool, to_tool):
        """Prilagodi parametre med različnimi orodji, če je potrebno"""
        # Ta implementacija je odvisna od specifičnih orodij
        # V tem primeru bomo vrnili izvirne parametre
        return params

# Primer uporabe
async def get_weather(workflow, location):
    return await workflow.execute_with_fallback(
        "premiumWeatherService",  # Primarni (plačljivi) vremenski API
        "basicWeatherService",    # Rezervni (brezplačni) vremenski API
        {"location": location}
    )
```

### 5. Workflow Composition Pattern

Build complex workflows by composing simpler ones:

```csharp
public class CompositeWorkflow : IWorkflow
{
    private readonly List<IWorkflow> _workflows;
    
    public CompositeWorkflow(IEnumerable<IWorkflow> workflows)
    {
        _workflows = new List<IWorkflow>(workflows);
    }
    
    public async Task<WorkflowResult> ExecuteAsync(WorkflowContext context)
    {
        var results = new Dictionary<string, object>();
        
        foreach (var workflow in _workflows)
        {
            var workflowResult = await workflow.ExecuteAsync(context);
            
            // Shrani rezultat vsakega poteka dela
            results[workflow.Name] = workflowResult;
            
            // Posodobi kontekst z rezultatom za naslednji potek dela
            context = context.WithResult(workflow.Name, workflowResult);
        }
        
        return new WorkflowResult(results);
    }
    
    public string Name => "CompositeWorkflow";
    public string Description => "Izvede več potekov dela zaporedno";
}

// Primer uporabe
var documentWorkflow = new CompositeWorkflow(new IWorkflow[] {
    new DocumentFetchWorkflow(),
    new DocumentProcessingWorkflow(),
    new InsightGenerationWorkflow(),
    new ReportGenerationWorkflow()
});

var result = await documentWorkflow.ExecuteAsync(new WorkflowContext {
    Parameters = new { documentId = "12345" }
});
```

# Testing MCP Servers: Best Practices and Top Tips

## Overview

Testing is a critical aspect of developing reliable, high-quality MCP servers. This guide provides comprehensive best practices and tips for testing your MCP servers throughout the development lifecycle, from unit tests to integration tests and end-to-end validation.

## Why Testing Matters for MCP Servers

MCP servers serve as crucial middleware between AI models and client applications. Thorough testing ensures:

- Reliability in production environments
- Accurate handling of requests and responses
- Proper implementation of MCP specifications
- Resilience against failures and edge cases
- Consistent performance under various loads

## Unit Testing for MCP Servers

### Unit Testing (Foundation)

Unit tests verify individual components of your MCP server in isolation.

#### What to Test

1. **Resource Handlers**: Test each resource handler's logic independently
2. **Tool Implementations**: Verify tool behavior with various inputs
3. **Prompt Templates**: Ensure prompt templates render correctly
4. **Schema Validation**: Test parameter validation logic
5. **Error Handling**: Verify error responses for invalid inputs

#### Best Practices for Unit Testing

```csharp
// Primer enotnega testa za orodje kalkulator v C#
[Fact]
public async Task CalculatorTool_Add_ReturnsCorrectSum()
{
    // Priprava
    var calculator = new CalculatorTool();
    var parameters = new Dictionary<string, object>
    {
        ["operation"] = "add",
        ["a"] = 5,
        ["b"] = 7
    };
    
    // Izvedba
    var response = await calculator.ExecuteAsync(parameters);
    var result = JsonSerializer.Deserialize<CalculationResult>(response.Content[0].ToString());
    
    // Preverjanje
    Assert.Equal(12, result.Value);
}
```

```python
# Primer enotnega testa za orodje kalkulator v Pythonu
def test_calculator_tool_add():
    # Priprava
    calculator = CalculatorTool()
    parameters = {
        "operation": "add",
        "a": 5,
        "b": 7
    }
    
    # Izvedba
    response = calculator.execute(parameters)
    result = json.loads(response.content[0].text)
    
    # Preverjanje
    assert result["value"] == 12
```

### Integration Testing (Middle Layer)

Integration tests verify interactions between components of your MCP server.

#### What to Test

1. **Server Initialization**: Test server startup with various configurations
2. **Route Registration**: Verify all endpoints are correctly registered
3. **Request Processing**: Test the full request-response cycle
4. **Error Propagation**: Ensure errors are properly handled across components
5. **Authentication & Authorization**: Test security mechanisms

#### Best Practices for Integration Testing

```csharp
// Primer integracijskega testa za MCP strežnik v C#
[Fact]
public async Task Server_ProcessToolRequest_ReturnsValidResponse()
{
    // Priprava
    var server = new McpServer();
    server.RegisterTool(new CalculatorTool());
    await server.StartAsync();
    
    var request = new McpRequest
    {
        Tool = "calculator",
        Parameters = new Dictionary<string, object>
        {
            ["operation"] = "multiply",
            ["a"] = 6,
            ["b"] = 7
        }
    };
    
    // Izvedba
    var response = await server.ProcessRequestAsync(request);
    
    // Preverjanje
    Assert.NotNull(response);
    Assert.Equal(McpStatusCodes.Success, response.StatusCode);
    // Dodatne trditve za vsebino odgovora
    
    // Čiščenje
    await server.StopAsync();
}
```

### End-to-End Testing (Top Layer)

End-to-end tests verify the complete system behavior from client to server.

#### What to Test

1. **Client-Server Communication**: Test complete request-response cycles
2. **Real Client SDKs**: Test with actual client implementations
3. **Performance Under Load**: Verify behavior with multiple concurrent requests
4. **Error Recovery**: Test system recovery from failures
5. **Long-Running Operations**: Verify handling of streaming and long operations

#### Best Practices for E2E Testing

```typescript
// Primer E2E testa s klientom v TypeScriptu
describe('MCP Server E2E Tests', () => {
  let client: McpClient;
  
  beforeAll(async () => {
    // Zaženi strežnik v testnem okolju
    await startTestServer();
    client = new McpClient('http://localhost:5000');
  });
  
  afterAll(async () => {
    await stopTestServer();
  });
  
  test('Client can invoke calculator tool and get correct result', async () => {
    // Izvedba
    const response = await client.invokeToolAsync('calculator', {
      operation: 'divide',
      a: 20,
      b: 4
    });
    
    // Preverjanje
    expect(response.statusCode).toBe(200);
    expect(response.content[0].text).toContain('5');
  });
});
```

## Mocking Strategies for MCP Testing

Mocking is essential for isolating components during testing.

### Components to Mock

1. **External AI Models**: Mock model responses for predictable testing
2. **External Services**: Mock API dependencies (databases, third-party services)
3. **Authentication Services**: Mock identity providers
4. **Resource Providers**: Mock expensive resource handlers

### Example: Mocking an AI Model Response

```csharp
// C# primer z Moq
var mockModel = new Mock<ILanguageModel>();
mockModel
    .Setup(m => m.GenerateResponseAsync(
        It.IsAny<string>(),
        It.IsAny<McpRequestContext>()))
    .ReturnsAsync(new ModelResponse { 
        Text = "Mocked model response",
        FinishReason = FinishReason.Completed
    });

var server = new McpServer(modelClient: mockModel.Object);
```

```python
# Python primer z unittest.mock
@patch('mcp_server.models.OpenAIModel')
def test_with_mock_model(mock_model):
    # Konfiguriraj mock
    mock_model.return_value.generate_response.return_value = {
        "text": "Mocked model response",
        "finish_reason": "completed"
    }
    
    # Uporabi mock v testu
    server = McpServer(model_client=mock_model)
    # Nadaljuj s testom
```

## Performance Testing

Performance testing is crucial for production MCP servers.

### What to Measure

1. **Latency**: Response time for requests
2. **Throughput**: Requests handled per second
3. **Resource Utilization**: CPU, memory, network usage
4. **Concurrency Handling**: Behavior under parallel requests
5. **Scaling Characteristics**: Performance as load increases

### Tools for Performance Testing

- **k6**: Open-source load testing tool
- **JMeter**: Comprehensive performance testing
- **Locust**: Python-based load testing
- **Azure Load Testing**: Cloud-based performance testing

### Example: Basic Load Test with k6

```javascript
// k6 skripta za obremenitveno testiranje MCP strežnika
import http from 'k6/http';
import { check, sleep } from 'k6';

export const options = {
  vus: 10,  // 10 virtualnih uporabnikov
  duration: '30s',
};

export default function () {
  const payload = JSON.stringify({
    tool: 'calculator',
    parameters: {
      operation: 'add',
      a: Math.floor(Math.random() * 100),
      b: Math.floor(Math.random() * 100)
    }
  });

  const params = {
    headers: {
      'Content-Type': 'application/json',
      'Authorization': 'Bearer test-token'
    },
  };

  const res = http.post('http://localhost:5000/api/tools/invoke', payload, params);
  
  check(res, {
    'status is 200': (r) => r.status === 200,
    'response time < 500ms': (r) => r.timings.duration < 500,
  });
  
  sleep(1);
}
```

## Test Automation for MCP Servers

Automating your tests ensures consistent quality and faster feedback loops.

### CI/CD Integration

1. **Run Unit Tests on Pull Requests**: Ensure code changes don't break existing functionality
2. **Integration Tests in Staging**: Run integration tests in pre-production environments
3. **Performance Baselines**: Maintain performance benchmarks to catch regressions
4. **Security Scans**: Automate security testing as part of the pipeline

### Example CI Pipeline (GitHub Actions)

```yaml
name: MCP Server Tests

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  test:
    runs-on: ubuntu-latest
    
    steps:
    - uses: actions/checkout@v2
    
    - name: Set up Runtime
      uses: actions/setup-dotnet@v1
      with:
        dotnet-version: '8.0.x'
    
    - name: Restore dependencies
      run: dotnet restore
    
    - name: Build
      run: dotnet build --no-restore
    
    - name: Unit Tests
      run: dotnet test --no-build --filter Category=Unit
    
    - name: Integration Tests
      run: dotnet test --no-build --filter Category=Integration
      
    - name: Performance Tests
      run: dotnet run --project tests/PerformanceTests/PerformanceTests.csproj
```

## Testing for Compliance with MCP Specification

Verify your server correctly implements the MCP specification.

### Key Compliance Areas

1. **API Endpoints**: Test required endpoints (/resources, /tools, etc.)
2. **Request/Response Format**: Validate schema compliance
3. **Error Codes**: Verify correct status codes for various scenarios
4. **Content Types**: Test handling of different content types
5. **Authentication Flow**: Verify spec-compliant auth mechanisms

### Compliance Test Suite

```csharp
[Fact]
public async Task Server_ResourceEndpoint_ReturnsCorrectSchema()
{
    // Priprava
    var client = new HttpClient();
    client.DefaultRequestHeaders.Add("Authorization", "Bearer test-token");
    
    // Izvedba
    var response = await client.GetAsync("http://localhost:5000/api/resources");
    var content = await response.Content.ReadAsStringAsync();
    var resources = JsonSerializer.Deserialize

// Assert
Assert.Equal(HttpStatusCode.OK, response.StatusCode);
Assert.NotNull(resources);
Assert.All(resources.Resources, resource => 
{
    Assert.NotNull(resource.Id);
    Assert.NotNull(resource.Type);
    // Dodatna validacija sheme
});
}
```

## Top 10 nasvetov za učinkovito testiranje MCP strežnika

1. **Testirajte definicije orodij ločeno**: Preverite definicije shem neodvisno od logike orodij  
2. **Uporabljajte parametrične teste**: Testirajte orodja z različnimi vhodnimi podatki, vključno z robnimi primeri  
3. **Preverite odzive na napake**: Zagotovite pravilno obravnavo napak za vse možne napake  
4. **Testirajte avtentikacijsko logiko**: Preverite ustrezno kontrolo dostopa za različne uporabniške vloge  
5. **Spremljajte pokritost testov**: Ciljajte na visoko pokritost kritičnih delov kode  
6. **Testirajte pretočne odzive**: Preverite pravilno obravnavo pretočne vsebine  
7. **Simulirajte omrežne težave**: Testirajte vedenje ob slabih omrežnih pogojih  
8. **Testirajte omejitve virov**: Preverite vedenje ob doseganju kvot ali omejitev hitrosti  
9. **Avtomatizirajte regresijske teste**: Ustvarite nabor testov, ki se izvajajo ob vsaki spremembi kode  
10. **Dokumentirajte testne primere**: Vzdržujte jasno dokumentacijo testnih scenarijev  

## Pogoste pasti pri testiranju

- **Prevelika zanašanje na teste "srečne poti"**: Poskrbite, da boste temeljito testirali tudi napake  
- **Ignoriranje testiranja zmogljivosti**: Prepoznajte ozka grla, preden vplivajo na produkcijo  
- **Testiranje samo v izolaciji**: Združite enotne, integracijske in E2E teste  
- **Nepopolna pokritost API-ja**: Poskrbite, da so testirani vsi končni točki in funkcionalnosti  
- **Nekonsistentna testna okolja**: Uporabljajte kontejnere za zagotovitev enotnih testnih okolij  

## Zaključek

Celovita strategija testiranja je ključna za razvoj zanesljivih in kakovostnih MCP strežnikov. Z upoštevanjem najboljših praks in nasvetov iz tega vodiča lahko zagotovite, da vaše MCP implementacije dosegajo najvišje standarde kakovosti, zanesljivosti in zmogljivosti.

## Ključne ugotovitve

1. **Oblikovanje orodij**: Upoštevajte načelo enotne odgovornosti, uporabljajte odvisnostno injekcijo in načrtujte za sestavljivost  
2. **Oblikovanje shem**: Ustvarite jasne, dobro dokumentirane sheme z ustreznimi validacijskimi omejitvami  
3. **Obravnava napak**: Implementirajte elegantno obravnavo napak, strukturirane odzive na napake in logiko ponovnih poskusov  
4. **Zmogljivost**: Uporabljajte predpomnjenje, asinhrono obdelavo in omejevanje virov  
5. **Varnost**: Uporabljajte temeljito validacijo vhodnih podatkov, preverjanje avtorizacije in ravnanje z občutljivimi podatki  
6. **Testiranje**: Ustvarite celovite enotne, integracijske in end-to-end teste  
7. **Vzorce delovnih tokov**: Uporabljajte uveljavljene vzorce, kot so verige, razpošiljevalci in vzporedna obdelava  

## Vaja

Oblikujte MCP orodje in delovni tok za sistem za obdelavo dokumentov, ki:

1. Sprejema dokumente v več formatih (PDF, DOCX, TXT)  
2. Izvleče besedilo in ključne informacije iz dokumentov  
3. Klasificira dokumente glede na tip in vsebino  
4. Ustvari povzetek vsakega dokumenta  

Implementirajte sheme orodij, obravnavo napak in vzorec delovnega toka, ki najbolj ustreza temu scenariju. Razmislite, kako bi testirali to implementacijo.

## Viri

1. Pridružite se MCP skupnosti na [Azure AI Foundry Discord Community](https://aka.ms/foundrydevs) in ostanite na tekočem z najnovejšimi razvoji  
2. Prispevajte k odprtokodnim [MCP projektom](https://github.com/modelcontextprotocol)  
3. Uporabljajte MCP principe v AI pobudah vaše organizacije  
4. Raziščite specializirane MCP implementacije za vašo industrijo  
5. Razmislite o naprednih tečajih na specifičnih MCP temah, kot so multimodalna integracija ali integracija poslovnih aplikacij  
6. Preizkusite gradnjo lastnih MCP orodij in delovnih tokov z uporabo principov, pridobljenih v [Hands on Lab](../10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/README.md)  

Naslednje: Najboljše prakse [študije primerov](../09-CaseStudy/README.md)

**Omejitev odgovornosti**:  
Ta dokument je bil preveden z uporabo storitve za avtomatski prevod AI [Co-op Translator](https://github.com/Azure/co-op-translator). Čeprav si prizadevamo za natančnost, vas opozarjamo, da lahko avtomatski prevodi vsebujejo napake ali netočnosti. Izvirni dokument v njegovem izvirnem jeziku velja za avtoritativni vir. Za pomembne informacije priporočamo strokovni človeški prevod. Za morebitne nesporazume ali napačne interpretacije, ki izhajajo iz uporabe tega prevoda, ne odgovarjamo.