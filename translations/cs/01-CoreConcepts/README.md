<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "4bf553c18e7e226c3d76ab0cde627d26",
  "translation_date": "2025-05-27T16:26:22+00:00",
  "source_file": "01-CoreConcepts/README.md",
  "language_code": "cs"
}
-->
# 📖 MCP Core Concepts: Dominar el Protocolo de Contexto de Modelo para la Integración de IA

El Model Context Protocol (MCP) es un marco poderoso y estandarizado que optimiza la comunicación entre Modelos de Lenguaje Grande (LLMs) y herramientas, aplicaciones y fuentes de datos externas. Esta guía optimizada para SEO te llevará a través de los conceptos fundamentales de MCP, asegurando que comprendas su arquitectura cliente-servidor, componentes esenciales, mecánicas de comunicación y mejores prácticas de implementación.

## Visión General

Esta lección explora la arquitectura fundamental y los componentes que conforman el ecosistema del Model Context Protocol (MCP). Aprenderás sobre la arquitectura cliente-servidor, los componentes clave y los mecanismos de comunicación que impulsan las interacciones MCP.

## 👩‍🎓 Objetivos Clave de Aprendizaje

Al finalizar esta lección, podrás:

- Comprender la arquitectura cliente-servidor de MCP.
- Identificar roles y responsabilidades de Hosts, Clientes y Servidores.
- Analizar las características principales que hacen de MCP una capa de integración flexible.
- Aprender cómo fluye la información dentro del ecosistema MCP.
- Obtener conocimientos prácticos mediante ejemplos de código en .NET, Java, Python y JavaScript.

## 🔎 Arquitectura MCP: Un Análisis Profundo

El ecosistema MCP se construye sobre un modelo cliente-servidor. Esta estructura modular permite que las aplicaciones de IA interactúen eficientemente con herramientas, bases de datos, APIs y recursos contextuales. Desglosemos esta arquitectura en sus componentes principales.

### 1. Hosts

En el Model Context Protocol (MCP), los Hosts juegan un papel crucial como la interfaz principal a través de la cual los usuarios interactúan con el protocolo. Los Hosts son aplicaciones o entornos que inician conexiones con servidores MCP para acceder a datos, herramientas y prompts. Ejemplos de Hosts incluyen entornos de desarrollo integrados (IDEs) como Visual Studio Code, herramientas de IA como Claude Desktop, o agentes personalizados diseñados para tareas específicas.

**Hosts** son aplicaciones LLM que inician conexiones. Ellos:

- Ejecutan o interactúan con modelos de IA para generar respuestas.
- Inician conexiones con servidores MCP.
- Gestionan el flujo de conversación y la interfaz de usuario.
- Controlan permisos y restricciones de seguridad.
- Manejan el consentimiento del usuario para compartir datos y ejecutar herramientas.

### 2. Clientes

Los Clientes son componentes esenciales que facilitan la interacción entre Hosts y servidores MCP. Los Clientes actúan como intermediarios, permitiendo que los Hosts accedan y utilicen las funcionalidades proporcionadas por los servidores MCP. Desempeñan un papel clave en garantizar una comunicación fluida e intercambio eficiente de datos dentro de la arquitectura MCP.

**Clientes** son conectores dentro de la aplicación host. Ellos:

- Envian solicitudes a los servidores con prompts/instrucciones.
- Negocian capacidades con los servidores.
- Gestionan solicitudes de ejecución de herramientas desde los modelos.
- Procesan y muestran respuestas a los usuarios.

### 3. Servidores

Los Servidores son responsables de manejar solicitudes de los clientes MCP y proporcionar respuestas adecuadas. Gestionan diversas operaciones como recuperación de datos, ejecución de herramientas y generación de prompts. Los servidores aseguran que la comunicación entre clientes y Hosts sea eficiente y confiable, manteniendo la integridad del proceso de interacción.

**Servidores** son servicios que proporcionan contexto y capacidades. Ellos:

- Registran características disponibles (recursos, prompts, herramientas).
- Reciben y ejecutan llamadas a herramientas desde el cliente.
- Proveen información contextual para mejorar las respuestas del modelo.
- Devuelven resultados al cliente.
- Mantienen el estado a lo largo de las interacciones cuando es necesario.

Los servidores pueden ser desarrollados por cualquiera para extender las capacidades del modelo con funcionalidades especializadas.

### 4. Características del Servidor

Los servidores en el Model Context Protocol (MCP) ofrecen bloques fundamentales que permiten interacciones ricas entre clientes, hosts y modelos de lenguaje. Estas características están diseñadas para mejorar las capacidades de MCP ofreciendo contexto estructurado, herramientas y prompts.

Los servidores MCP pueden ofrecer cualquiera de las siguientes características:

#### 📑 Recursos

Los recursos en el Model Context Protocol (MCP) abarcan varios tipos de contexto y datos que pueden ser utilizados por usuarios o modelos de IA. Estos incluyen:

- **Datos Contextuales**: Información y contexto que los usuarios o modelos de IA pueden aprovechar para la toma de decisiones y ejecución de tareas.
- **Bases de Conocimiento y Repositorios Documentales**: Colecciones de datos estructurados y no estructurados, como artículos, manuales y trabajos de investigación, que brindan información valiosa.
- **Archivos Locales y Bases de Datos**: Datos almacenados localmente en dispositivos o dentro de bases de datos, accesibles para procesamiento y análisis.
- **APIs y Servicios Web**: Interfaces y servicios externos que ofrecen datos y funcionalidades adicionales, permitiendo la integración con diversos recursos y herramientas en línea.

Un ejemplo de recurso puede ser un esquema de base de datos o un archivo que puede ser accedido así:

```text
file://log.txt
database://schema
```

### 🤖 Prompts

Los prompts en el Model Context Protocol (MCP) incluyen diversas plantillas predefinidas y patrones de interacción diseñados para agilizar flujos de trabajo y mejorar la comunicación. Estos incluyen:

- **Mensajes y Flujos de Trabajo Plantilla**: Mensajes y procesos preestructurados que guían a los usuarios a través de tareas e interacciones específicas.
- **Patrones de Interacción Predefinidos**: Secuencias estandarizadas de acciones y respuestas que facilitan una comunicación consistente y eficiente.
- **Plantillas de Conversación Especializadas**: Plantillas personalizables diseñadas para tipos específicos de conversaciones, asegurando interacciones relevantes y contextualmente apropiadas.

Una plantilla de prompt puede verse así:

```markdown
Generate a product slogan based on the following {{product}} with the following {{keywords}}
```

#### ⛏️ Herramientas

Las herramientas en el Model Context Protocol (MCP) son funciones que el modelo de IA puede ejecutar para realizar tareas específicas. Estas herramientas están diseñadas para potenciar las capacidades del modelo de IA proporcionando operaciones estructuradas y confiables. Aspectos clave incluyen:

- **Funciones para que el modelo IA las ejecute**: Las herramientas son funciones ejecutables que el modelo IA puede invocar para llevar a cabo diversas tareas.
- **Nombre Único y Descripción**: Cada herramienta tiene un nombre distinto y una descripción detallada que explica su propósito y funcionalidad.
- **Parámetros y Resultados**: Las herramientas aceptan parámetros específicos y devuelven resultados estructurados, garantizando resultados consistentes y predecibles.
- **Funciones Discretas**: Las herramientas realizan funciones específicas como búsquedas web, cálculos y consultas a bases de datos.

Un ejemplo de herramienta podría verse así:

```typescript
server.tool(
  "GetProducts",
  {
    pageSize: z.string().optional(),
    pageCount: z.string().optional()
  }, () => {
    // return results from API
  }
)
```

## Características del Cliente

En el Model Context Protocol (MCP), los clientes ofrecen varias características clave a los servidores, mejorando la funcionalidad general y la interacción dentro del protocolo. Una de las características destacadas es Sampling.

### 👉 Sampling

- **Comportamientos Agénticos Iniciados por el Servidor**: Los clientes permiten que los servidores inicien acciones o comportamientos específicos de forma autónoma, aumentando las capacidades dinámicas del sistema.
- **Interacciones Recursivas con LLMs**: Esta característica permite interacciones recursivas con modelos de lenguaje grande (LLMs), posibilitando un procesamiento más complejo e iterativo de tareas.
- **Solicitar Completaciones Adicionales del Modelo**: Los servidores pueden solicitar completaciones adicionales del modelo, asegurando que las respuestas sean completas y contextualmente relevantes.

## Flujo de Información en MCP

El Model Context Protocol (MCP) define un flujo estructurado de información entre hosts, clientes, servidores y modelos. Entender este flujo ayuda a clarificar cómo se procesan las solicitudes de los usuarios y cómo las herramientas externas y datos se integran en las respuestas del modelo.

- **Host Inicia Conexión**  
  La aplicación host (como un IDE o interfaz de chat) establece una conexión con un servidor MCP, típicamente vía STDIO, WebSocket u otro transporte soportado.

- **Negociación de Capacidades**  
  El cliente (integrado en el host) y el servidor intercambian información sobre sus características, herramientas, recursos y versiones del protocolo soportadas. Esto asegura que ambas partes entiendan las capacidades disponibles para la sesión.

- **Solicitud del Usuario**  
  El usuario interactúa con el host (por ejemplo, ingresando un prompt o comando). El host recoge esta entrada y la pasa al cliente para su procesamiento.

- **Uso de Recursos o Herramientas**  
  - El cliente puede solicitar contexto o recursos adicionales al servidor (como archivos, entradas de bases de datos o artículos de la base de conocimiento) para enriquecer la comprensión del modelo.
  - Si el modelo determina que se necesita una herramienta (por ejemplo, para obtener datos, realizar un cálculo o llamar a una API), el cliente envía una solicitud de invocación de herramienta al servidor, especificando el nombre y los parámetros de la herramienta.

- **Ejecución en el Servidor**  
  El servidor recibe la solicitud de recurso o herramienta, ejecuta las operaciones necesarias (como correr una función, consultar una base de datos o recuperar un archivo) y devuelve los resultados al cliente en un formato estructurado.

- **Generación de Respuesta**  
  El cliente integra las respuestas del servidor (datos de recursos, salidas de herramientas, etc.) en la interacción continua con el modelo. El modelo utiliza esta información para generar una respuesta completa y contextualmente relevante.

- **Presentación del Resultado**  
  El host recibe la salida final del cliente y la presenta al usuario, incluyendo tanto el texto generado por el modelo como cualquier resultado de la ejecución de herramientas o búsquedas de recursos.

Este flujo permite que MCP soporte aplicaciones de IA avanzadas, interactivas y conscientes del contexto, conectando sin problemas modelos con herramientas y fuentes de datos externas.

## Detalles del Protocolo

MCP (Model Context Protocol) se basa en [JSON-RPC 2.0](https://www.jsonrpc.org/), proporcionando un formato de mensajes estandarizado y agnóstico al lenguaje para la comunicación entre hosts, clientes y servidores. Esta base permite interacciones fiables, estructuradas y extensibles a través de diversas plataformas y lenguajes de programación.

### Características Clave del Protocolo

MCP extiende JSON-RPC 2.0 con convenciones adicionales para la invocación de herramientas, acceso a recursos y gestión de prompts. Soporta múltiples capas de transporte (STDIO, WebSocket, SSE) y permite una comunicación segura, extensible y agnóstica al lenguaje entre componentes.

#### 🧢 Protocolo Base

- **Formato de Mensajes JSON-RPC**: Todas las solicitudes y respuestas usan la especificación JSON-RPC 2.0, asegurando una estructura consistente para llamadas a métodos, parámetros, resultados y manejo de errores.
- **Conexiones con Estado**: Las sesiones MCP mantienen estado a través de múltiples solicitudes, soportando conversaciones continuas, acumulación de contexto y gestión de recursos.
- **Negociación de Capacidades**: Durante la configuración de la conexión, clientes y servidores intercambian información sobre características soportadas, versiones del protocolo, herramientas y recursos disponibles. Esto asegura que ambas partes comprendan sus capacidades y puedan adaptarse en consecuencia.

#### ➕ Utilidades Adicionales

A continuación algunas utilidades y extensiones del protocolo que MCP provee para mejorar la experiencia del desarrollador y habilitar escenarios avanzados:

- **Opciones de Configuración**: MCP permite la configuración dinámica de parámetros de sesión, como permisos de herramientas, acceso a recursos y ajustes del modelo, adaptados a cada interacción.
- **Seguimiento de Progreso**: Operaciones de larga duración pueden reportar actualizaciones de progreso, permitiendo interfaces de usuario más receptivas y mejor experiencia durante tareas complejas.
- **Cancelación de Solicitudes**: Los clientes pueden cancelar solicitudes en curso, permitiendo a los usuarios interrumpir operaciones que ya no son necesarias o que tardan demasiado.
- **Reporte de Errores**: Mensajes y códigos de error estandarizados ayudan a diagnosticar problemas, manejar fallos de forma elegante y proveer retroalimentación útil a usuarios y desarrolladores.
- **Registro de Logs**: Tanto clientes como servidores pueden emitir logs estructurados para auditoría, depuración y monitoreo de interacciones del protocolo.

Al aprovechar estas características del protocolo, MCP garantiza una comunicación robusta, segura y flexible entre modelos de lenguaje y herramientas o fuentes de datos externas.

### 🔐 Consideraciones de Seguridad

Las implementaciones MCP deben adherirse a varios principios clave de seguridad para garantizar interacciones seguras y confiables:

- **Consentimiento y Control del Usuario**: Los usuarios deben dar consentimiento explícito antes de que se acceda a cualquier dato o se realicen operaciones. Deben tener control claro sobre qué datos se comparten y qué acciones están autorizadas, apoyado por interfaces intuitivas para revisar y aprobar actividades.

- **Privacidad de Datos**: Los datos del usuario solo deben exponerse con consentimiento explícito y deben protegerse mediante controles de acceso adecuados. Las implementaciones MCP deben salvaguardar contra transmisiones no autorizadas y garantizar que la privacidad se mantenga durante todas las interacciones.

- **Seguridad de las Herramientas**: Antes de invocar cualquier herramienta, se requiere consentimiento explícito del usuario. Los usuarios deben entender claramente la funcionalidad de cada herramienta, y deben aplicarse límites de seguridad robustos para evitar ejecuciones no deseadas o inseguras.

Siguiendo estos principios, MCP asegura que la confianza, privacidad y seguridad del usuario se mantengan en todas las interacciones del protocolo.

## Ejemplos de Código: Componentes Clave

A continuación se presentan ejemplos de código en varios lenguajes populares que ilustran cómo implementar componentes clave de un servidor MCP y herramientas.

### Ejemplo en .NET: Creando un Servidor MCP Simple con Herramientas

Aquí hay un ejemplo práctico en .NET que demuestra cómo implementar un servidor MCP simple con herramientas personalizadas. Este ejemplo muestra cómo definir y registrar herramientas, manejar solicitudes y conectar el servidor usando el Model Context Protocol.

```csharp
using System;
using System.Threading.Tasks;
using ModelContextProtocol.Server;
using ModelContextProtocol.Server.Transport;
using ModelContextProtocol.Server.Tools;

public class WeatherServer
{
    public static async Task Main(string[] args)
    {
        // Create an MCP server
        var server = new McpServer(
            name: "Weather MCP Server",
            version: "1.0.0"
        );
        
        // Register our custom weather tool
        server.AddTool<string, WeatherData>("weatherTool", 
            description: "Gets current weather for a location",
            execute: async (location) => {
                // Call weather API (simplified)
                var weatherData = await GetWeatherDataAsync(location);
                return weatherData;
            });
        
        // Connect the server using stdio transport
        var transport = new StdioServerTransport();
        await server.ConnectAsync(transport);
        
        Console.WriteLine("Weather MCP Server started");
        
        // Keep the server running until process is terminated
        await Task.Delay(-1);
    }
    
    private static async Task<WeatherData> GetWeatherDataAsync(string location)
    {
        // This would normally call a weather API
        // Simplified for demonstration
        await Task.Delay(100); // Simulate API call
        return new WeatherData { 
            Temperature = 72.5,
            Conditions = "Sunny",
            Location = location
        };
    }
}

public class WeatherData
{
    public double Temperature { get; set; }
    public string Conditions { get; set; }
    public string Location { get; set; }
}
```

### Ejemplo en Java: Componentes del Servidor MCP

Este ejemplo demuestra el mismo servidor MCP y registro de herramientas que el ejemplo en .NET anterior, pero implementado en Java.

```java
import io.modelcontextprotocol.server.McpServer;
import io.modelcontextprotocol.server.McpToolDefinition;
import io.modelcontextprotocol.server.transport.StdioServerTransport;
import io.modelcontextprotocol.server.tool.ToolExecutionContext;
import io.modelcontextprotocol.server.tool.ToolResponse;

public class WeatherMcpServer {
    public static void main(String[] args) throws Exception {
        // Create an MCP server
        McpServer server = McpServer.builder()
            .name("Weather MCP Server")
            .version("1.0.0")
            .build();
            
        // Register a weather tool
        server.registerTool(McpToolDefinition.builder("weatherTool")
            .description("Gets current weather for a location")
            .parameter("location", String.class)
            .execute((ToolExecutionContext ctx) -> {
                String location = ctx.getParameter("location", String.class);
                
                // Get weather data (simplified)
                WeatherData data = getWeatherData(location);
                
                // Return formatted response
                return ToolResponse.content(
                    String.format("Temperature: %.1f°F, Conditions: %s, Location: %s", 
                    data.getTemperature(), 
                    data.getConditions(), 
                    data.getLocation())
                );
            })
            .build());
        
        // Connect the server using stdio transport
        try (StdioServerTransport transport = new StdioServerTransport()) {
            server.connect(transport);
            System.out.println("Weather MCP Server started");
            // Keep server running until process is terminated
            Thread.currentThread().join();
        }
    }
    
    private static WeatherData getWeatherData(String location) {
        // Implementation would call a weather API
        // Simplified for example purposes
        return new WeatherData(72.5, "Sunny", location);
    }
}

class WeatherData {
    private double temperature;
    private String conditions;
    private String location;
    
    public WeatherData(double temperature, String conditions, String location) {
        this.temperature = temperature;
        this.conditions = conditions;
        this.location = location;
    }
    
    public double getTemperature() {
        return temperature;
    }
    
    public String getConditions() {
        return conditions;
    }
    
    public String getLocation() {
        return location;
    }
}
```

### Ejemplo en Python: Construyendo un Servidor MCP

En este ejemplo mostramos cómo construir un servidor MCP en Python. También se presentan dos formas diferentes de crear herramientas.

```python
#!/usr/bin/env python3
import asyncio
from mcp.server.fastmcp import FastMCP
from mcp.server.transports.stdio import serve_stdio

# Create a FastMCP server
mcp = FastMCP(
    name="Weather MCP Server",
    version="1.0.0"
)

@mcp.tool()
def get_weather(location: str) -> dict:
    """Gets current weather for a location."""
    # This would normally call a weather API
    # Simplified for demonstration
    return {
        "temperature": 72.5,
        "conditions": "Sunny",
        "location": location
    }

# Alternative approach using a class
class WeatherTools:
    @mcp.tool()
    def forecast(self, location: str, days: int = 1) -> dict:
        """Gets weather forecast for a location for the specified number of days."""
        # This would normally call a weather API forecast endpoint
        # Simplified for demonstration
        return {
            "location": location,
            "forecast": [
                {"day": i+1, "temperature": 70 + i, "conditions": "Partly Cloudy"}
                for i in range(days)
            ]
        }

# Initialize class for its methods to be registered as tools
weather_tools = WeatherTools()

if __name__ == "__main__":
    # Start the server with stdio transport
    print("Weather MCP Server starting...")
    asyncio.run(serve_stdio(mcp))
```

### Ejemplo en JavaScript: Creando un Servidor MCP

Este ejemplo muestra la creación de un servidor MCP en JavaScript y cómo registrar dos herramientas relacionadas con el clima.

```javascript
// Using the official Model Context Protocol SDK
import { McpServer } from "@modelcontextprotocol/sdk/server/mcp.js";
import { StdioServerTransport } from "@modelcontextprotocol/sdk/server/stdio.js";
import { z } from "zod"; // For parameter validation

// Create an MCP server
const server = new McpServer({
  name: "Weather MCP Server",
  version: "1.0.0"
});

// Define a weather tool
server.tool(
  "weatherTool",
  {
    location: z.string().describe("The location to get weather for")
  },
  async ({ location }) => {
    // This would normally call a weather API
    // Simplified for demonstration
    const weatherData = await getWeatherData(location);
    
    return {
      content: [
        { 
          type: "text", 
          text: `Temperature: ${weatherData.temperature}°F, Conditions: ${weatherData.conditions}, Location: ${weatherData.location}` 
        }
      ]
    };
  }
);

// Define a forecast tool
server.tool(
  "forecastTool",
  {
    location: z.string(),
    days: z.number().default(3).describe("Number of days for forecast")
  },
  async ({ location, days }) => {
    // This would normally call a weather API
    // Simplified for demonstration
    const forecast = await getForecastData(location, days);
    
    return {
      content: [
        { 
          type: "text", 
          text: `${days}-day forecast for ${location}: ${JSON.stringify(forecast)}` 
        }
      ]
    };
  }
);

// Helper functions
async function getWeatherData(location) {
  // Simulate API call
  return {
    temperature: 72.5,
    conditions: "Sunny",
    location: location
  };
}

async function getForecastData(location, days) {
  // Simulate API call
  return Array.from({ length: days }, (_, i) => ({
    day: i + 1,
    temperature: 70 + Math.floor(Math.random() * 10),
    conditions: i % 2 === 0 ? "Sunny" : "Partly Cloudy"
  }));
}

// Connect the server using stdio transport
const transport = new StdioServerTransport();
server.connect(transport).catch(console.error);

console.log("Weather MCP Server started");
```

Este ejemplo en JavaScript demuestra cómo crear un cliente MCP que se conecta a un servidor, envía un prompt y procesa la respuesta incluyendo cualquier llamada a herramientas que se haya realizado.

## Seguridad y Autorización

MCP incluye varios conceptos y mecanismos integrados para gestionar la seguridad y autorización a lo largo del protocolo:

1. **Control de Permisos para Herramientas**:  
  Los clientes pueden especificar qué herramientas puede usar un modelo durante una sesión. Esto asegura que solo las herramientas explícitamente autorizadas estén accesibles, reduciendo el riesgo de operaciones no deseadas o inseguras. Los permisos pueden configurarse dinámicamente según preferencias del usuario, políticas organizacionales o el contexto de la interacción.

2. **Autenticación**:  
  Los servidores pueden requerir autenticación antes de conceder acceso a herramientas, recursos u operaciones sensibles. Esto puede involucrar claves API, tokens OAuth u otros esquemas de autenticación. La autenticación adecuada asegura que solo clientes y usuarios confiables puedan invocar capacidades del lado servidor.

3. **Validación**:  
  Se aplica validación de parámetros para todas las invocaciones de herramientas. Cada herramienta define los tipos, formatos y restricciones esperados para sus parámetros, y el servidor valida las solicitudes entrantes en consecuencia. Esto previene entradas malformadas o maliciosas que puedan afectar las implementaciones de herramientas y ayuda a mantener la integridad de las operaciones.

4. **Limitación de Tasa**:  
  Para prevenir abusos y asegurar un uso justo de los recursos del servidor, los servidores MCP pueden implementar limitación de tasa para llamadas a herramientas y acceso a recursos. Los límites pueden aplicarse por usuario, por sesión o globalmente, y ayudan a proteger contra ataques de denegación de servicio o consumo excesivo de recursos.

Al combinar estos mecanismos, MCP ofrece una base segura para integrar modelos de lenguaje con herramientas y fuentes de datos externas, mientras brinda a usuarios y desarrolladores control granular sobre el acceso y uso.

## Mensajes del Protocolo

La comunicación MCP utiliza mensajes JSON estructurados para facilitar interacciones claras y confiables entre clientes, servidores y modelos. Los principales tipos de mensajes incluyen:

- **Solicitud del Cliente**  
  Enviada del cliente al servidor, este mensaje típicamente incluye:
  - El prompt o comando del usuario
  - Historial de conversación para contexto
  - Configuración y permisos de herramientas
  - Cualquier metadato adicional o información de sesión

- **Respuesta del Modelo**  
  Devuelta por el modelo (a través del cliente), este mensaje contiene:
  - Texto generado o completación basada en el prompt y contexto
  - Instrucciones opcionales para llamada a herramienta si el modelo determina que debe invocarse una
  - Referencias a recursos o contexto adicional según sea necesario

- **Solicitud de Herramienta**  
  Enviada del cliente al servidor cuando se necesita ejecutar una herramienta. Este mensaje incluye:
  - El nombre de la herramienta a invocar
  - Parámetros requeridos por la herramienta (validados contra el esquema de la herramienta)
  - Información contextual o identificadores para seguimiento de la solicitud

- **Respuesta de Herramienta**  
  Devuelta por el servidor tras ejecutar una herramienta. Este mensaje provee:
  - Resultados de la ejecución de la herramienta (datos estructurados o contenido)
  - Cualquier error o información de estado si la llamada a la herramienta falló
  - Opcionalmente, metadatos adicionales o logs relacionados con la ejecución

Estos mensajes estructurados aseguran que cada paso en el flujo de trabajo MCP sea explícito, rastreable y extensible, apoyando escenarios avanzados como conversaciones multi-turno, encadenamiento de herramientas y manejo robusto de errores.

## Puntos Clave

- MCP utiliza una arquitectura cliente-servidor para conectar modelos con capacidades externas
- El ecosistema consiste en clientes, hosts, servidores, herramientas y fuentes de datos
- La comunicación puede ocurrir a través de STDIO, SSE o WebSockets
- Las herramientas son las unidades fundamentales de funcionalidad expuestas a los modelos
- Protocolos de comunicación estructurados aseguran interacciones consistentes

## Ejercicio

Diseña una herramienta MCP simple que sea útil en tu dominio. Define:
1. Cómo se llamaría la herramienta
2. Qué parámetros aceptaría
3. Qué salida devolvería
4. Cómo un modelo podría usar esta herramienta para resolver problemas de usuario

---

## Qué sigue

Siguiente: [Capítulo 2: Seguridad](/02-Security/README.md)

**Prohlášení o vyloučení odpovědnosti**:  
Tento dokument byl přeložen pomocí AI překladatelské služby [Co-op Translator](https://github.com/Azure/co-op-translator). I když usilujeme o přesnost, mějte prosím na paměti, že automatizované překlady mohou obsahovat chyby nebo nepřesnosti. Původní dokument v jeho mateřském jazyce by měl být považován za závazný zdroj. Pro důležité informace se doporučuje profesionální lidský překlad. Nejsme odpovědní za jakékoliv nedorozumění nebo mylné výklady vyplývající z použití tohoto překladu.