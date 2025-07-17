<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "7b4b9bfacd2926725e6f1cda82bc8ff5",
  "translation_date": "2025-07-17T06:09:03+00:00",
  "source_file": "06-CommunityContributions/README.md",
  "language_code": "sv"
}
-->
# Community och Bidrag

## Översikt

Den här lektionen fokuserar på hur man engagerar sig i MCP-communityt, bidrar till MCP-ekosystemet och följer bästa praxis för samarbetsutveckling. Att förstå hur man deltar i öppna MCP-projekt är avgörande för dem som vill forma framtiden för denna teknik.

## Lärandemål

Efter den här lektionen kommer du att kunna:
- Förstå strukturen i MCP-communityt och ekosystemet
- Delta effektivt i MCP-communityts forum och diskussioner
- Bidra till MCP:s open-source-repositorier
- Skapa och dela anpassade MCP-verktyg och servrar
- Följa bästa praxis för MCP-utveckling och samarbete
- Upptäcka communityresurser och ramverk för MCP-utveckling

## MCP-communityts ekosystem

MCP-ekosystemet består av olika komponenter och deltagare som samarbetar för att driva protokollet framåt.

### Viktiga communitykomponenter

1. **Core Protocol Maintainers**: Den officiella [Model Context Protocol GitHub-organisationen](https://github.com/modelcontextprotocol) underhåller de centrala MCP-specifikationerna och referensimplementationerna
2. **Tool Developers**: Individer och team som skapar MCP-verktyg och servrar
3. **Integration Providers**: Företag som integrerar MCP i sina produkter och tjänster
4. **End Users**: Utvecklare och organisationer som använder MCP i sina applikationer
5. **Contributors**: Communitymedlemmar som bidrar med kod, dokumentation eller andra resurser

### Communityresurser

#### Officiella kanaler

- [MCP GitHub Organization](https://github.com/modelcontextprotocol)
- [MCP Documentation](https://modelcontextprotocol.io/)
- [MCP Specification](https://modelcontextprotocol.io/docs/specification)
- [GitHub Discussions](https://github.com/orgs/modelcontextprotocol/discussions)
- [MCP Examples & Servers Repository](https://github.com/modelcontextprotocol/servers)

#### Communitydrivna resurser

- [MCP Clients](https://modelcontextprotocol.io/clients) - Lista över klienter som stödjer MCP-integrationer
- [Community MCP Servers](https://github.com/modelcontextprotocol/servers?tab=readme-ov-file#-community-servers) - Växande lista över communityutvecklade MCP-servrar
- [Awesome MCP Servers](https://github.com/wong2/awesome-mcp-servers) - Kurerad lista över MCP-servrar
- [PulseMCP](https://www.pulsemcp.com/) - Communitynav och nyhetsbrev för att upptäcka MCP-resurser
- [Discord Server](https://discord.gg/jHEGxQu2a5) - Koppla upp dig med MCP-utvecklare
- Språkspecifika SDK-implementationer
- Blogginlägg och tutorials

## Bidra till MCP

### Typer av bidrag

MCP-ekosystemet välkomnar olika typer av bidrag:

1. **Kodbidrag**:
   - Förbättringar av core-protokollet
   - Buggfixar
   - Verktygs- och serverimplementationer
   - Klient-/serverbibliotek i olika språk

2. **Dokumentation**:
   - Förbättra befintlig dokumentation
   - Skapa tutorials och guider
   - Översätta dokumentation
   - Skapa exempel och provapplikationer

3. **Communitystöd**:
   - Svara på frågor i forum och diskussioner
   - Testa och rapportera problem
   - Organisera communityevent
   - Vägleda nya bidragsgivare

### Bidragsprocess: Core Protocol

För att bidra till core MCP-protokollet eller officiella implementationer, följ principerna i [de officiella bidragsriktlinjerna](https://github.com/modelcontextprotocol/modelcontextprotocol/blob/main/CONTRIBUTING.md):

1. **Enkelhet och minimalism**: MCP-specifikationen håller en hög standard för att lägga till nya koncept. Det är lättare att lägga till saker än att ta bort dem.

2. **Konkreta tillvägagångssätt**: Specifikationsändringar ska baseras på specifika implementeringsutmaningar, inte spekulativa idéer.

3. **Faser för ett förslag**:
   - Definiera: Utforska problemområdet, verifiera att andra MCP-användare har liknande problem
   - Prototyp: Bygg en exempelösning och visa dess praktiska användning
   - Skriv: Baserat på prototypen, skriv ett specifikationsförslag

### Utvecklingsmiljö Setup

```bash
# Fork the repository
git clone https://github.com/YOUR-USERNAME/modelcontextprotocol.git
cd modelcontextprotocol

# Install dependencies
npm install

# For schema changes, validate and generate schema.json:
npm run check:schema:ts
npm run generate:schema

# For documentation changes
npm run check:docs
npm run format

# Preview documentation locally (optional):
npm run serve:docs
```

### Exempel: Bidra med en buggfix

```javascript
// Original code with bug in the typescript-sdk
export function validateResource(resource: unknown): resource is MCPResource {
  if (!resource || typeof resource !== 'object') {
    return false;
  }
  
  // Bug: Missing property validation
  // Current implementation:
  const hasName = 'name' in resource;
  const hasSchema = 'schema' in resource;
  
  return hasName && hasSchema;
}

// Fixed implementation in a contribution
export function validateResource(resource: unknown): resource is MCPResource {
  if (!resource || typeof resource !== 'object') {
    return false;
  }
  
  // Improved validation
  const hasName = 'name' in resource && typeof (resource as MCPResource).name === 'string';
  const hasSchema = 'schema' in resource && typeof (resource as MCPResource).schema === 'object';
  const hasDescription = !('description' in resource) || typeof (resource as MCPResource).description === 'string';
  
  return hasName && hasSchema && hasDescription;
}
```

### Exempel: Bidra med ett nytt verktyg till standardbiblioteket

```python
# Example contribution: A CSV data processing tool for the MCP standard library

from mcp_tools import Tool, ToolRequest, ToolResponse, ToolExecutionException
import pandas as pd
import io
import json
from typing import Dict, Any, List, Optional

class CsvProcessingTool(Tool):
    """
    Tool for processing and analyzing CSV data.
    
    This tool allows models to extract information from CSV files,
    run basic analysis, and convert data between formats.
    """
    
    def get_name(self):
        return "csvProcessor"
        
    def get_description(self):
        return "Processes and analyzes CSV data"
    
    def get_schema(self):
        return {
            "type": "object",
            "properties": {
                "csvData": {
                    "type": "string", 
                    "description": "CSV data as a string"
                },
                "csvUrl": {
                    "type": "string",
                    "description": "URL to a CSV file (alternative to csvData)"
                },
                "operation": {
                    "type": "string",
                    "enum": ["summary", "filter", "transform", "convert"],
                    "description": "Operation to perform on the CSV data"
                },
                "filterColumn": {
                    "type": "string",
                    "description": "Column to filter by (for filter operation)"
                },
                "filterValue": {
                    "type": "string",
                    "description": "Value to filter for (for filter operation)"
                },
                "outputFormat": {
                    "type": "string",
                    "enum": ["json", "csv", "markdown"],
                    "default": "json",
                    "description": "Output format for the processed data"
                }
            },
            "oneOf": [
                {"required": ["csvData", "operation"]},
                {"required": ["csvUrl", "operation"]}
            ]
        }
    
    async def execute_async(self, request: ToolRequest) -> ToolResponse:
        try:
            # Extract parameters
            operation = request.parameters.get("operation")
            output_format = request.parameters.get("outputFormat", "json")
            
            # Get CSV data from either direct data or URL
            df = await self._get_dataframe(request)
            
            # Process based on requested operation
            result = {}
            
            if operation == "summary":
                result = self._generate_summary(df)
            elif operation == "filter":
                column = request.parameters.get("filterColumn")
                value = request.parameters.get("filterValue")
                if not column:
                    raise ToolExecutionException("filterColumn is required for filter operation")
                result = self._filter_data(df, column, value)
            elif operation == "transform":
                result = self._transform_data(df, request.parameters)
            elif operation == "convert":
                result = self._convert_format(df, output_format)
            else:
                raise ToolExecutionException(f"Unknown operation: {operation}")
            
            return ToolResponse(result=result)
        
        except Exception as e:
            raise ToolExecutionException(f"CSV processing failed: {str(e)}")
    
    async def _get_dataframe(self, request: ToolRequest) -> pd.DataFrame:
        """Gets a pandas DataFrame from either CSV data or URL"""
        if "csvData" in request.parameters:
            csv_data = request.parameters.get("csvData")
            return pd.read_csv(io.StringIO(csv_data))
        elif "csvUrl" in request.parameters:
            csv_url = request.parameters.get("csvUrl")
            return pd.read_csv(csv_url)
        else:
            raise ToolExecutionException("Either csvData or csvUrl must be provided")
    
    def _generate_summary(self, df: pd.DataFrame) -> Dict[str, Any]:
        """Generates a summary of the CSV data"""
        return {
            "columns": df.columns.tolist(),
            "rowCount": len(df),
            "columnCount": len(df.columns),
            "numericColumns": df.select_dtypes(include=['number']).columns.tolist(),
            "categoricalColumns": df.select_dtypes(include=['object']).columns.tolist(),
            "sampleRows": json.loads(df.head(5).to_json(orient="records")),
            "statistics": json.loads(df.describe().to_json())
        }
    
    def _filter_data(self, df: pd.DataFrame, column: str, value: str) -> Dict[str, Any]:
        """Filters the DataFrame by a column value"""
        if column not in df.columns:
            raise ToolExecutionException(f"Column '{column}' not found")
            
        filtered_df = df[df[column].astype(str).str.contains(value)]
        
        return {
            "originalRowCount": len(df),
            "filteredRowCount": len(filtered_df),
            "data": json.loads(filtered_df.to_json(orient="records"))
        }
    
    def _transform_data(self, df: pd.DataFrame, params: Dict[str, Any]) -> Dict[str, Any]:
        """Transforms the data based on parameters"""
        # Implementation would include various transformations
        return {
            "status": "success",
            "message": "Transformation applied"
        }
    
    def _convert_format(self, df: pd.DataFrame, format: str) -> Dict[str, Any]:
        """Converts the DataFrame to different formats"""
        if format == "json":
            return {
                "data": json.loads(df.to_json(orient="records")),
                "format": "json"
            }
        elif format == "csv":
            return {
                "data": df.to_csv(index=False),
                "format": "csv"
            }
        elif format == "markdown":
            return {
                "data": df.to_markdown(),
                "format": "markdown"
            }
        else:
            raise ToolExecutionException(f"Unsupported output format: {format}")
```

### Bidragsriktlinjer

För att göra ett framgångsrikt bidrag till MCP-projekt:

1. **Börja smått**: Starta med dokumentation, buggfixar eller små förbättringar
2. **Följ stilguiden**: Håll dig till projektets kodningsstil och konventioner
3. **Skriv tester**: Inkludera enhetstester för dina kodbidrag
4. **Dokumentera ditt arbete**: Lägg till tydlig dokumentation för nya funktioner eller ändringar
5. **Skicka riktade PRs**: Håll pull requests fokuserade på en enda fråga eller funktion
6. **Engagera dig i feedback**: Var lyhörd för feedback på dina bidrag

### Exempel på bidragsarbetsflöde

```bash
# Clone the repository
git clone https://github.com/modelcontextprotocol/typescript-sdk.git
cd typescript-sdk

# Create a new branch for your contribution
git checkout -b feature/my-contribution

# Make your changes
# ...

# Run tests to ensure your changes don't break existing functionality
npm test

# Commit your changes with a descriptive message
git commit -am "Fix validation in resource handler"

# Push your branch to your fork
git push origin feature/my-contribution

# Create a pull request from your branch to the main repository
# Then engage with feedback and iterate on your PR as needed
```

## Skapa och dela MCP-servrar

Ett av de mest värdefulla sätten att bidra till MCP-ekosystemet är att skapa och dela anpassade MCP-servrar. Communityt har redan utvecklat hundratals servrar för olika tjänster och användningsområden.

### Ramverk för MCP-serverutveckling

Flera ramverk finns för att förenkla utvecklingen av MCP-servrar:

1. **Officiella SDKs**:
   - [TypeScript SDK](https://github.com/modelcontextprotocol/typescript-sdk)
   - [Python SDK](https://github.com/modelcontextprotocol/python-sdk)
   - [C# SDK](https://github.com/modelcontextprotocol/csharp-sdk)
   - [Go SDK](https://github.com/modelcontextprotocol/go-sdk)
   - [Java SDK](https://github.com/modelcontextprotocol/java-sdk)
   - [Kotlin SDK](https://github.com/modelcontextprotocol/kotlin-sdk)

2. **Community-ramverk**:
   - [MCP-Framework](https://mcp-framework.com/) - Bygg MCP-servrar med elegans och snabbhet i TypeScript
   - [MCP Declarative Java SDK](https://github.com/codeboyzhou/mcp-declarative-java-sdk) - Annotation-drivna MCP-servrar med Java
   - [Quarkus MCP Server SDK](https://github.com/quarkiverse/quarkus-mcp-server) - Java-ramverk för MCP-servrar
   - [Next.js MCP Server Template](https://github.com/vercel-labs/mcp-for-next.js) - Startprojekt för MCP-servrar i Next.js

### Utveckla delbara verktyg

#### .NET-exempel: Skapa ett delbart verktygspaket

```csharp
// Create a new .NET library project
// dotnet new classlib -n McpFinanceTools

using Microsoft.Mcp.Tools;
using System.Threading.Tasks;
using System.Net.Http;
using System.Text.Json;

namespace McpFinanceTools
{
    // Stock quote tool
    public class StockQuoteTool : IMcpTool
    {
        private readonly HttpClient _httpClient;
        
        public StockQuoteTool(HttpClient httpClient = null)
        {
            _httpClient = httpClient ?? new HttpClient();
        }
        
        public string Name => "stockQuote";
        public string Description => "Gets current stock quotes for specified symbols";
        
        public object GetSchema()
        {
            return new {
                type = "object",
                properties = new {
                    symbol = new { 
                        type = "string",
                        description = "Stock symbol (e.g., MSFT, AAPL)" 
                    },
                    includeHistory = new { 
                        type = "boolean",
                        description = "Whether to include historical data",
                        default = false
                    }
                },
                required = new[] { "symbol" }
            };
        }
        
        public async Task<ToolResponse> ExecuteAsync(ToolRequest request)
        {
            // Extract parameters
            string symbol = request.Parameters.GetProperty("symbol").GetString();
            bool includeHistory = false;
            
            if (request.Parameters.TryGetProperty("includeHistory", out var historyProp))
            {
                includeHistory = historyProp.GetBoolean();
            }
            
            // Call external API (example)
            var quoteResult = await GetStockQuoteAsync(symbol);
            
            // Add historical data if requested
            if (includeHistory)
            {
                var historyData = await GetStockHistoryAsync(symbol);
                quoteResult.Add("history", historyData);
            }
            
            // Return formatted result
            return new ToolResponse {
                Result = JsonSerializer.SerializeToElement(quoteResult)
            };
        }
        
        private async Task<Dictionary<string, object>> GetStockQuoteAsync(string symbol)
        {
            // Implementation would call a real stock API
            // This is a simplified example
            return new Dictionary<string, object>
            {
                ["symbol"] = symbol,
                ["price"] = 123.45,
                ["change"] = 2.5,
                ["percentChange"] = 1.2,
                ["lastUpdated"] = DateTime.UtcNow
            };
        }
        
        private async Task<object> GetStockHistoryAsync(string symbol)
        {
            // Implementation would get historical data
            // Simplified example
            return new[]
            {
                new { date = DateTime.Now.AddDays(-7).Date, price = 120.25 },
                new { date = DateTime.Now.AddDays(-6).Date, price = 122.50 },
                new { date = DateTime.Now.AddDays(-5).Date, price = 121.75 }
                // More historical data...
            };
        }
    }
}

// Create package and publish to NuGet
// dotnet pack -c Release
// dotnet nuget push bin/Release/McpFinanceTools.1.0.0.nupkg -s https://api.nuget.org/v3/index.json -k YOUR_API_KEY
```

#### Java-exempel: Skapa ett Maven-paket för verktyg

```java
// pom.xml configuration for a shareable MCP tool package
<!-- 
<project>
    <groupId>com.example</groupId>
    <artifactId>mcp-weather-tools</artifactId>
    <version>1.0.0</version>
    
    <dependencies>
        <dependency>
            <groupId>com.mcp</groupId>
            <artifactId>mcp-server</artifactId>
            <version>1.0.0</version>
        </dependency>
    </dependencies>
    
    <distributionManagement>
        <repository>
            <id>github</id>
            <name>GitHub Packages</name>
            <url>https://maven.pkg.github.com/username/mcp-weather-tools</url>
        </repository>
    </distributionManagement>
</project>
-->

package com.example.mcp.weather;

import com.mcp.tools.Tool;
import com.mcp.tools.ToolRequest;
import com.mcp.tools.ToolResponse;
import com.mcp.tools.ToolExecutionException;

import java.net.http.HttpClient;
import java.net.http.HttpRequest;
import java.net.http.HttpResponse;
import java.net.URI;
import java.util.HashMap;
import java.util.Map;

public class WeatherForecastTool implements Tool {
    private final HttpClient httpClient;
    private final String apiKey;
    
    public WeatherForecastTool(String apiKey) {
        this.httpClient = HttpClient.newHttpClient();
        this.apiKey = apiKey;
    }
    
    @Override
    public String getName() {
        return "weatherForecast";
    }
    
    @Override
    public String getDescription() {
        return "Gets weather forecast for a specified location";
    }
    
    @Override
    public Object getSchema() {
        Map<String, Object> schema = new HashMap<>();
        // Schema definition...
        return schema;
    }
    
    @Override
    public ToolResponse execute(ToolRequest request) {
        try {
            String location = request.getParameters().get("location").asText();
            int days = request.getParameters().has("days") ? 
                request.getParameters().get("days").asInt() : 3;
            
            // Call weather API
            Map<String, Object> forecast = getForecast(location, days);
            
            // Build response
            return new ToolResponse.Builder()
                .setResult(forecast)
                .build();
        } catch (Exception ex) {
            throw new ToolExecutionException("Weather forecast failed: " + ex.getMessage(), ex);
        }
    }
    
    private Map<String, Object> getForecast(String location, int days) {
        // Implementation would call weather API
        // Simplified example
        Map<String, Object> result = new HashMap<>();
        // Add forecast data...
        return result;
    }
}

// Build and publish using Maven
// mvn clean package
// mvn deploy
```

#### Python-exempel: Publicera ett PyPI-paket

```python
# Directory structure for a PyPI package:
# mcp_nlp_tools/
# ├── LICENSE
# ├── README.md
# ├── setup.py
# ├── mcp_nlp_tools/
# │   ├── __init__.py
# │   ├── sentiment_tool.py
# │   └── translation_tool.py

# Example setup.py
"""
from setuptools import setup, find_packages

setup(
    name="mcp_nlp_tools",
    version="0.1.0",
    packages=find_packages(),
    install_requires=[
        "mcp_server>=1.0.0",
        "transformers>=4.0.0",
        "torch>=1.8.0"
    ],
    author="Your Name",
    author_email="your.email@example.com",
    description="MCP tools for natural language processing tasks",
    long_description=open("README.md").read(),
    long_description_content_type="text/markdown",
    url="https://github.com/username/mcp_nlp_tools",
    classifiers=[
        "Programming Language :: Python :: 3",
        "License :: OSI Approved :: MIT License",
        "Operating System :: OS Independent",
    ],
    python_requires=">=3.8",
)
"""

# Example NLP tool implementation (sentiment_tool.py)
from mcp_tools import Tool, ToolRequest, ToolResponse, ToolExecutionException
from transformers import pipeline
import torch

class SentimentAnalysisTool(Tool):
    """MCP tool for sentiment analysis of text"""
    
    def __init__(self, model_name="distilbert-base-uncased-finetuned-sst-2-english"):
        # Load the sentiment analysis model
        self.sentiment_analyzer = pipeline("sentiment-analysis", model=model_name)
    
    def get_name(self):
        return "sentimentAnalysis"
        
    def get_description(self):
        return "Analyzes the sentiment of text, classifying it as positive or negative"
    
    def get_schema(self):
        return {
            "type": "object",
            "properties": {
                "text": {
                    "type": "string", 
                    "description": "The text to analyze for sentiment"
                },
                "includeScore": {
                    "type": "boolean",
                    "description": "Whether to include confidence scores",
                    "default": True
                }
            },
            "required": ["text"]
        }
    
    async def execute_async(self, request: ToolRequest) -> ToolResponse:
        try:
            # Extract parameters
            text = request.parameters.get("text")
            include_score = request.parameters.get("includeScore", True)
            
            # Analyze sentiment
            sentiment_result = self.sentiment_analyzer(text)[0]
            
            # Format result
            result = {
                "sentiment": sentiment_result["label"],
                "text": text
            }
            
            if include_score:
                result["score"] = sentiment_result["score"]
            
            # Return result
            return ToolResponse(result=result)
            
        except Exception as e:
            raise ToolExecutionException(f"Sentiment analysis failed: {str(e)}")

# To publish:
# python setup.py sdist bdist_wheel
# python -m twine upload dist/*
```

### Dela bästa praxis

När du delar MCP-verktyg med communityt:

1. **Fullständig dokumentation**:
   - Dokumentera syfte, användning och exempel
   - Förklara parametrar och returvärden
   - Dokumentera eventuella externa beroenden

2. **Felhantering**:
   - Implementera robust felhantering
   - Ge användbara felmeddelanden
   - Hantera kantfall på ett smidigt sätt

3. **Prestanda**:
   - Optimera för både hastighet och resursanvändning
   - Implementera caching när det är lämpligt
   - Tänk på skalbarhet

4. **Säkerhet**:
   - Använd säkra API-nycklar och autentisering
   - Validera och sanera indata
   - Implementera rate limiting för externa API-anrop

5. **Testning**:
   - Inkludera omfattande testtäckning
   - Testa med olika indata och kantfall
   - Dokumentera testprocedurer

## Community-samarbete och bästa praxis

Effektivt samarbete är nyckeln till ett blomstrande MCP-ekosystem.

### Kommunikationskanaler

- GitHub Issues och Discussions
- Microsoft Tech Community
- Discord- och Slack-kanaler
- Stack Overflow (tagg: `model-context-protocol` eller `mcp`)

### Kodgranskningar

När du granskar MCP-bidrag:

1. **Tydlighet**: Är koden tydlig och väl dokumenterad?
2. **Korrekthet**: Fungerar den som förväntat?
3. **Konsekvens**: Följer den projektets konventioner?
4. **Fullständighet**: Ingår tester och dokumentation?
5. **Säkerhet**: Finns det några säkerhetsrisker?

### Versionskompatibilitet

När du utvecklar för MCP:

1. **Protokollversionering**: Följ den MCP-protokollversion som ditt verktyg stödjer
2. **Klientkompatibilitet**: Tänk på bakåtkompatibilitet
3. **Serverkompatibilitet**: Följ riktlinjer för serverimplementation
4. **Brytande ändringar**: Dokumentera tydligt eventuella brytande ändringar

## Exempel på communityprojekt: MCP Tool Registry

Ett viktigt communitybidrag kan vara att utveckla ett offentligt register för MCP-verktyg.

```python
# Example schema for a community tool registry API

from fastapi import FastAPI, HTTPException, Depends
from pydantic import BaseModel, Field, HttpUrl
from typing import List, Optional
import datetime
import uuid

# Models for the tool registry
class ToolSchema(BaseModel):
    """JSON Schema for a tool"""
    type: str
    properties: dict
    required: List[str] = []

class ToolRegistration(BaseModel):
    """Information for registering a tool"""
    name: str = Field(..., description="Unique name for the tool")
    description: str = Field(..., description="Description of what the tool does")
    version: str = Field(..., description="Semantic version of the tool")
    schema: ToolSchema = Field(..., description="JSON Schema for tool parameters")
    author: str = Field(..., description="Author of the tool")
    repository: Optional[HttpUrl] = Field(None, description="Repository URL")
    documentation: Optional[HttpUrl] = Field(None, description="Documentation URL")
    package: Optional[HttpUrl] = Field(None, description="Package URL")
    tags: List[str] = Field(default_factory=list, description="Tags for categorization")
    examples: List[dict] = Field(default_factory=list, description="Example usage")

class Tool(ToolRegistration):
    """Tool with registry metadata"""
    id: uuid.UUID = Field(default_factory=uuid.uuid4)
    created_at: datetime.datetime = Field(default_factory=datetime.datetime.now)
    updated_at: datetime.datetime = Field(default_factory=datetime.datetime.now)
    downloads: int = Field(default=0)
    rating: float = Field(default=0.0)
    ratings_count: int = Field(default=0)

# FastAPI application for the registry
app = FastAPI(title="MCP Tool Registry")

# In-memory database for this example
tools_db = {}

@app.post("/tools", response_model=Tool)
async def register_tool(tool: ToolRegistration):
    """Register a new tool in the registry"""
    if tool.name in tools_db:
        raise HTTPException(status_code=400, detail=f"Tool '{tool.name}' already exists")
    
    new_tool = Tool(**tool.dict())
    tools_db[tool.name] = new_tool
    return new_tool

@app.get("/tools", response_model=List[Tool])
async def list_tools(tag: Optional[str] = None):
    """List all registered tools, optionally filtered by tag"""
    if tag:
        return [tool for tool in tools_db.values() if tag in tool.tags]
    return list(tools_db.values())

@app.get("/tools/{tool_name}", response_model=Tool)
async def get_tool(tool_name: str):
    """Get information about a specific tool"""
    if tool_name not in tools_db:
        raise HTTPException(status_code=404, detail=f"Tool '{tool_name}' not found")
    return tools_db[tool_name]

@app.delete("/tools/{tool_name}")
async def delete_tool(tool_name: str):
    """Delete a tool from the registry"""
    if tool_name not in tools_db:
        raise HTTPException(status_code=404, detail=f"Tool '{tool_name}' not found")
    del tools_db[tool_name]
    return {"message": f"Tool '{tool_name}' deleted"}
```

## Viktiga punkter att ta med sig

- MCP-communityt är mångsidigt och välkomnar olika typer av bidrag
- Att bidra till MCP kan handla om allt från core-protokollförbättringar till anpassade verktyg
- Att följa bidragsriktlinjer ökar chansen att din PR accepteras
- Att skapa och dela MCP-verktyg är ett värdefullt sätt att stärka ekosystemet
- Community-samarbete är avgörande för MCP:s tillväxt och förbättring

## Övning

1. Identifiera ett område i MCP-ekosystemet där du kan bidra utifrån dina kunskaper och intressen
2. Fork:a MCP-repositoriet och sätt upp en lokal utvecklingsmiljö
3. Skapa en liten förbättring, buggfix eller verktyg som kan gynna communityt
4. Dokumentera ditt bidrag med lämpliga tester och dokumentation
5. Skicka en pull request till rätt repository

## Ytterligare resurser

- [MCP Community Projects](https://github.com/topics/model-context-protocol)


---

Nästa: [Lessons from Early Adoption](../07-LessonsfromEarlyAdoption/README.md)

**Ansvarsfriskrivning**:  
Detta dokument har översatts med hjälp av AI-översättningstjänsten [Co-op Translator](https://github.com/Azure/co-op-translator). Även om vi strävar efter noggrannhet, vänligen observera att automatiska översättningar kan innehålla fel eller brister. Det ursprungliga dokumentet på dess modersmål bör betraktas som den auktoritativa källan. För kritisk information rekommenderas professionell mänsklig översättning. Vi ansvarar inte för några missförstånd eller feltolkningar som uppstår vid användning av denna översättning.