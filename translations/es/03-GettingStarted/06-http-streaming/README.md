<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "3eaf38ffe0638867045ec6664908333c",
  "translation_date": "2025-06-18T08:30:40+00:00",
  "source_file": "03-GettingStarted/06-http-streaming/README.md",
  "language_code": "es"
}
-->
# Transmisión HTTPS con el Protocolo de Contexto de Modelo (MCP)

Este capítulo ofrece una guía completa para implementar transmisión segura, escalable y en tiempo real con el Protocolo de Contexto de Modelo (MCP) usando HTTPS. Cubre la motivación para la transmisión, los mecanismos de transporte disponibles, cómo implementar HTTP transmisible en MCP, las mejores prácticas de seguridad, la migración desde SSE y orientación práctica para construir tus propias aplicaciones MCP con transmisión.

## Mecanismos de Transporte y Transmisión en MCP

Esta sección explora los diferentes mecanismos de transporte disponibles en MCP y su papel en habilitar capacidades de transmisión para la comunicación en tiempo real entre clientes y servidores.

### ¿Qué es un Mecanismo de Transporte?

Un mecanismo de transporte define cómo se intercambian datos entre el cliente y el servidor. MCP soporta múltiples tipos de transporte para adaptarse a diferentes entornos y requisitos:

- **stdio**: Entrada/salida estándar, adecuado para herramientas locales y basadas en CLI. Simple pero no apto para web o nube.
- **SSE (Server-Sent Events)**: Permite a los servidores enviar actualizaciones en tiempo real a los clientes a través de HTTP. Bueno para interfaces web, pero limitado en escalabilidad y flexibilidad.
- **Streamable HTTP**: Transporte moderno basado en HTTP para transmisión, que soporta notificaciones y mejor escalabilidad. Recomendado para la mayoría de escenarios de producción y nube.

### Tabla Comparativa

Consulta la siguiente tabla comparativa para entender las diferencias entre estos mecanismos de transporte:

| Transporte       | Actualizaciones en Tiempo Real | Transmisión | Escalabilidad | Caso de Uso             |
|------------------|-------------------------------|-------------|---------------|------------------------|
| stdio            | No                            | No          | Baja          | Herramientas CLI locales|
| SSE              | Sí                            | Sí          | Media         | Web, actualizaciones en tiempo real |
| Streamable HTTP  | Sí                            | Sí          | Alta          | Nube, multi-cliente    |

> **Tip:** Elegir el transporte adecuado impacta en el rendimiento, escalabilidad y experiencia de usuario. **Streamable HTTP** es recomendado para aplicaciones modernas, escalables y preparadas para la nube.

Ten en cuenta los transportes stdio y SSE que se mostraron en capítulos anteriores y cómo el transporte Streamable HTTP es el que se aborda en este capítulo.

## Transmisión: Conceptos y Motivación

Entender los conceptos fundamentales y la motivación detrás de la transmisión es esencial para implementar sistemas efectivos de comunicación en tiempo real.

**La transmisión** es una técnica en programación de redes que permite enviar y recibir datos en pequeños fragmentos manejables o como una secuencia de eventos, en lugar de esperar a que toda la respuesta esté lista. Esto es especialmente útil para:

- Archivos o conjuntos de datos grandes.
- Actualizaciones en tiempo real (por ejemplo, chat, barras de progreso).
- Cálculos de larga duración donde se desea mantener informado al usuario.

Esto es lo que debes saber sobre la transmisión a alto nivel:

- Los datos se entregan progresivamente, no todos de una vez.
- El cliente puede procesar los datos conforme llegan.
- Reduce la latencia percibida y mejora la experiencia del usuario.

### ¿Por qué usar transmisión?

Las razones para usar transmisión son las siguientes:

- Los usuarios reciben retroalimentación inmediata, no solo al final.
- Permite aplicaciones en tiempo real y interfaces responsivas.
- Uso más eficiente de recursos de red y cómputo.

### Ejemplo Simple: Servidor y Cliente HTTP con Transmisión

Aquí tienes un ejemplo sencillo de cómo se puede implementar la transmisión:

<details>
<summary>Python</summary>

**Servidor (Python, usando FastAPI y StreamingResponse):**
<details>
<summary>Python</summary>

```python
from fastapi import FastAPI
from fastapi.responses import StreamingResponse
import time

app = FastAPI()

async def event_stream():
    for i in range(1, 6):
        yield f"data: Message {i}\n\n"
        time.sleep(1)

@app.get("/stream")
def stream():
    return StreamingResponse(event_stream(), media_type="text/event-stream")
```

</details>

**Cliente (Python, usando requests):**
<details>
<summary>Python</summary>

```python
import requests

with requests.get("http://localhost:8000/stream", stream=True) as r:
    for line in r.iter_lines():
        if line:
            print(line.decode())
```

</details>

Este ejemplo demuestra un servidor enviando una serie de mensajes al cliente a medida que están disponibles, en lugar de esperar a que todos los mensajes estén listos.

**Cómo funciona:**
- El servidor entrega cada mensaje tan pronto está listo.
- El cliente recibe e imprime cada fragmento conforme llega.

**Requisitos:**
- El servidor debe usar una respuesta de transmisión (por ejemplo, `StreamingResponse` in FastAPI).
- The client must process the response as a stream (`stream=True` in requests).
- Content-Type is usually `text/event-stream` or `application/octet-stream`.

</details>

<details>
<summary>Java</summary>

**Servidor (Java, usando Spring Boot y Server-Sent Events):**

```java
@RestController
public class CalculatorController {

    @GetMapping(value = "/calculate", produces = MediaType.TEXT_EVENT_STREAM_VALUE)
    public Flux<ServerSentEvent<String>> calculate(@RequestParam double a,
                                                   @RequestParam double b,
                                                   @RequestParam String op) {
        
        double result;
        switch (op) {
            case "add": result = a + b; break;
            case "sub": result = a - b; break;
            case "mul": result = a * b; break;
            case "div": result = b != 0 ? a / b : Double.NaN; break;
            default: result = Double.NaN;
        }

        return Flux.<ServerSentEvent<String>>just(
                    ServerSentEvent.<String>builder()
                        .event("info")
                        .data("Calculating: " + a + " " + op + " " + b)
                        .build(),
                    ServerSentEvent.<String>builder()
                        .event("result")
                        .data(String.valueOf(result))
                        .build()
                )
                .delayElements(Duration.ofSeconds(1));
    }
}
```

**Cliente (Java, usando Spring WebFlux WebClient):**

```java
@SpringBootApplication
public class CalculatorClientApplication implements CommandLineRunner {

    private final WebClient client = WebClient.builder()
            .baseUrl("http://localhost:8080")
            .build();

    @Override
    public void run(String... args) {
        client.get()
                .uri(uriBuilder -> uriBuilder
                        .path("/calculate")
                        .queryParam("a", 7)
                        .queryParam("b", 5)
                        .queryParam("op", "mul")
                        .build())
                .accept(MediaType.TEXT_EVENT_STREAM)
                .retrieve()
                .bodyToFlux(String.class)
                .doOnNext(System.out::println)
                .blockLast();
    }
}
```

**Notas de Implementación en Java:**
- Usa la pila reactiva de Spring Boot con `Flux` for streaming
- `ServerSentEvent` provides structured event streaming with event types
- `WebClient` with `bodyToFlux()` enables reactive streaming consumption
- `delayElements()` simulates processing time between events
- Events can have types (`info`, `result`) for better client handling

</details>

### Comparison: Classic Streaming vs MCP Streaming

The differences between how streaming works in a "classical" manner versus how it works in MCP can be depicted like so:

| Feature                | Classic HTTP Streaming         | MCP Streaming (Notifications)      |
|------------------------|-------------------------------|-------------------------------------|
| Main response          | Chunked                       | Single, at end                      |
| Progress updates       | Sent as data chunks           | Sent as notifications               |
| Client requirements    | Must process stream           | Must implement message handler      |
| Use case               | Large files, AI token streams | Progress, logs, real-time feedback  |

### Key Differences Observed

Additionally, here are some key differences:

- **Communication Pattern:**
   - Classic HTTP streaming: Uses simple chunked transfer encoding to send data in chunks
   - MCP streaming: Uses a structured notification system with JSON-RPC protocol

- **Message Format:**
   - Classic HTTP: Plain text chunks with newlines
   - MCP: Structured LoggingMessageNotification objects with metadata

- **Client Implementation:**
   - Classic HTTP: Simple client that processes streaming responses
   - MCP: More sophisticated client with a message handler to process different types of messages

- **Progress Updates:**
   - Classic HTTP: The progress is part of the main response stream
   - MCP: Progress is sent via separate notification messages while the main response comes at the end

### Recommendations

There are some things we recommend when it comes to choosing between implementing classical streaming (as an endpoint we showed you above using `/stream`) frente a elegir transmisión vía MCP.

- **Para necesidades simples de transmisión:** La transmisión HTTP clásica es más fácil de implementar y suficiente para necesidades básicas.

- **Para aplicaciones complejas e interactivas:** La transmisión MCP ofrece un enfoque más estructurado con metadatos más ricos y separación entre notificaciones y resultados finales.

- **Para aplicaciones de IA:** El sistema de notificaciones de MCP es especialmente útil para tareas de IA de larga duración donde quieres mantener informados a los usuarios del progreso.

## Transmisión en MCP

Bien, hasta ahora has visto algunas recomendaciones y comparaciones sobre la diferencia entre la transmisión clásica y la transmisión en MCP. Ahora vamos a detallar exactamente cómo puedes aprovechar la transmisión en MCP.

Entender cómo funciona la transmisión dentro del marco MCP es esencial para construir aplicaciones responsivas que proporcionen retroalimentación en tiempo real a los usuarios durante operaciones de larga duración.

En MCP, la transmisión no consiste en enviar la respuesta principal en fragmentos, sino en enviar **notificaciones** al cliente mientras una herramienta procesa una solicitud. Estas notificaciones pueden incluir actualizaciones de progreso, registros u otros eventos.

### Cómo funciona

El resultado principal sigue enviándose como una única respuesta. Sin embargo, las notificaciones pueden enviarse como mensajes separados durante el procesamiento y así actualizar al cliente en tiempo real. El cliente debe ser capaz de manejar y mostrar estas notificaciones.

## ¿Qué es una Notificación?

Mencionamos "Notificación", ¿qué significa eso en el contexto de MCP?

Una notificación es un mensaje enviado desde el servidor al cliente para informar sobre progreso, estado u otros eventos durante una operación de larga duración. Las notificaciones mejoran la transparencia y la experiencia del usuario.

Por ejemplo, se espera que un cliente envíe una notificación una vez que se haya realizado el apretón de manos inicial con el servidor.

Una notificación se ve así como un mensaje JSON:

```json
{
  jsonrpc: "2.0";
  method: string;
  params?: {
    [key: string]: unknown;
  };
}
```

Las notificaciones pertenecen a un tema en MCP referido como ["Logging"](https://modelcontextprotocol.io/specification/draft/server/utilities/logging).

Para que el registro funcione, el servidor necesita habilitarlo como característica/capacidad de esta forma:

```json
{
  "capabilities": {
    "logging": {}
  }
}
```

> [!NOTE]
> Dependiendo del SDK utilizado, el registro puede estar habilitado por defecto o puede que necesites activarlo explícitamente en la configuración de tu servidor.

Existen diferentes tipos de notificaciones:

| Nivel     | Descripción                   | Ejemplo de Uso               |
|-----------|------------------------------|-----------------------------|
| debug     | Información detallada de depuración | Puntos de entrada/salida de funciones |
| info      | Mensajes informativos generales | Actualizaciones de progreso de operación |
| notice    | Eventos normales pero significativos | Cambios en configuración    |
| warning   | Condiciones de advertencia    | Uso de características obsoletas |
| error     | Condiciones de error          | Fallos en la operación       |
| critical  | Condiciones críticas          | Fallos en componentes del sistema |
| alert     | Acción inmediata requerida    | Detección de corrupción de datos |
| emergency | Sistema inutilizable          | Fallo completo del sistema   |

## Implementación de Notificaciones en MCP

Para implementar notificaciones en MCP, necesitas configurar tanto el servidor como el cliente para manejar actualizaciones en tiempo real. Esto permite que tu aplicación proporcione retroalimentación inmediata a los usuarios durante operaciones de larga duración.

### Lado servidor: Enviando Notificaciones

Comencemos con el lado servidor. En MCP, defines herramientas que pueden enviar notificaciones mientras procesan solicitudes. El servidor usa el objeto de contexto (usualmente `ctx`) para enviar mensajes al cliente.

<details>
<summary>Python</summary>

<details>
<summary>Python</summary>

```python
@mcp.tool(description="A tool that sends progress notifications")
async def process_files(message: str, ctx: Context) -> TextContent:
    await ctx.info("Processing file 1/3...")
    await ctx.info("Processing file 2/3...")
    await ctx.info("Processing file 3/3...")
    return TextContent(type="text", text=f"Done: {message}")
```

En el ejemplo anterior, el transporte `process_files` tool sends three notifications to the client as it processes each file. The `ctx.info()` method is used to send informational messages.

</details>

Additionally, to enable notifications, ensure your server uses a streaming transport (like `streamable-http`) and your client implements a message handler to process notifications. Here's how you can set up the server to use the `streamable-http`:

```python
mcp.run(transport="streamable-http")
```

</details>

<details>
<summary>.NET</summary>

```csharp
[Tool("A tool that sends progress notifications")]
public async Task<TextContent> ProcessFiles(string message, ToolContext ctx)
{
    await ctx.Info("Processing file 1/3...");
    await ctx.Info("Processing file 2/3...");
    await ctx.Info("Processing file 3/3...");
    return new TextContent
    {
        Type = "text",
        Text = $"Done: {message}"
    };
}
```

En este ejemplo .NET, el método `ProcessFiles` tool is decorated with the `Tool` attribute and sends three notifications to the client as it processes each file. The `ctx.Info()` se usa para enviar mensajes informativos.

Para habilitar notificaciones en tu servidor MCP .NET, asegúrate de usar un transporte de transmisión:

```csharp
var builder = McpBuilder.Create();
await builder
    .UseStreamableHttp() // Enable streamable HTTP transport
    .Build()
    .RunAsync();
```

</details>

### Lado cliente: Recibiendo Notificaciones

El cliente debe implementar un manejador de mensajes para procesar y mostrar notificaciones conforme llegan.

<details>
<summary>Python</summary>

```python
async def message_handler(message):
    if isinstance(message, types.ServerNotification):
        print("NOTIFICATION:", message)
    else:
        print("SERVER MESSAGE:", message)

async with ClientSession(
   read_stream, 
   write_stream,
   logging_callback=logging_collector,
   message_handler=message_handler,
) as session:
```

En el código anterior, el `message_handler` function checks if the incoming message is a notification. If it is, it prints the notification; otherwise, it processes it as a regular server message. Also note how the `ClientSession` is initialized with the `message_handler` maneja las notificaciones entrantes.

</details>

<details>
<summary>.NET</summary>

```csharp
// Define a message handler
void MessageHandler(IJsonRpcMessage message)
{
    if (message is ServerNotification notification)
    {
        Console.WriteLine($"NOTIFICATION: {notification}");
    }
    else
    {
        Console.WriteLine($"SERVER MESSAGE: {message}");
    }
}

// Create and use a client session with the message handler
var clientOptions = new ClientSessionOptions
{
    MessageHandler = MessageHandler,
    LoggingCallback = (level, message) => Console.WriteLine($"[{level}] {message}")
};

using var client = new ClientSession(readStream, writeStream, clientOptions);
await client.InitializeAsync();

// Now the client will process notifications through the MessageHandler
```

En este ejemplo .NET, el `MessageHandler` function checks if the incoming message is a notification. If it is, it prints the notification; otherwise, it processes it as a regular server message. The `ClientSession` is initialized with the message handler via the `ClientSessionOptions`.

</details>

To enable notifications, ensure your server uses a streaming transport (like `streamable-http`) y tu cliente implementa un manejador de mensajes para procesar notificaciones.

## Notificaciones de Progreso y Escenarios

Esta sección explica el concepto de notificaciones de progreso en MCP, por qué son importantes y cómo implementarlas usando Streamable HTTP. También encontrarás un ejercicio práctico para reforzar tu comprensión.

Las notificaciones de progreso son mensajes en tiempo real enviados desde el servidor al cliente durante operaciones de larga duración. En lugar de esperar a que todo el proceso termine, el servidor mantiene al cliente actualizado sobre el estado actual. Esto mejora la transparencia, la experiencia de usuario y facilita la depuración.

**Ejemplo:**

```text

"Processing document 1/10"
"Processing document 2/10"
...
"Processing complete!"

```

### ¿Por qué usar notificaciones de progreso?

Las notificaciones de progreso son esenciales por varias razones:

- **Mejor experiencia de usuario:** Los usuarios ven actualizaciones conforme avanza el trabajo, no solo al final.
- **Retroalimentación en tiempo real:** Los clientes pueden mostrar barras de progreso o registros, haciendo que la aplicación se sienta más responsiva.
- **Depuración y monitoreo más fáciles:** Desarrolladores y usuarios pueden ver dónde un proceso podría estar lento o detenido.

### Cómo implementar notificaciones de progreso

Así es como puedes implementar notificaciones de progreso en MCP:

- **En el servidor:** Usa `ctx.info()` or `ctx.log()` para enviar notificaciones a medida que se procesa cada ítem. Esto envía un mensaje al cliente antes de que el resultado principal esté listo.
- **En el cliente:** Implementa un manejador de mensajes que escuche y muestre las notificaciones conforme llegan. Este manejador distingue entre notificaciones y el resultado final.

**Ejemplo servidor:**

<details>
<summary>Python</summary>

```python
@mcp.tool(description="A tool that sends progress notifications")
async def process_files(message: str, ctx: Context) -> TextContent:
    for i in range(1, 11):
        await ctx.info(f"Processing document {i}/10")
    await ctx.info("Processing complete!")
    return TextContent(type="text", text=f"Done: {message}")
```

</details>

**Ejemplo cliente:**

<details>
<summary>Python</summary>

```python
async def message_handler(message):
    if isinstance(message, types.ServerNotification):
        print("NOTIFICATION:", message)
    else:
        print("SERVER MESSAGE:", message)
```

</details>

## Consideraciones de Seguridad

Al implementar servidores MCP con transportes basados en HTTP, la seguridad se convierte en una preocupación fundamental que requiere atención cuidadosa a múltiples vectores de ataque y mecanismos de protección.

### Resumen

La seguridad es crítica cuando se exponen servidores MCP a través de HTTP. Streamable HTTP introduce nuevas superficies de ataque y requiere una configuración cuidadosa.

### Puntos Clave
- **Validación del encabezado Origin**: Siempre valida el encabezado `Origin` header to prevent DNS rebinding attacks.
- **Localhost Binding**: For local development, bind servers to `localhost` to avoid exposing them to the public internet.
- **Authentication**: Implement authentication (e.g., API keys, OAuth) for production deployments.
- **CORS**: Configure Cross-Origin Resource Sharing (CORS) policies to restrict access.
- **HTTPS**: Use HTTPS in production to encrypt traffic.

### Best Practices
- Never trust incoming requests without validation.
- Log and monitor all access and errors.
- Regularly update dependencies to patch security vulnerabilities.

### Challenges
- Balancing security with ease of development
- Ensuring compatibility with various client environments


## Upgrading from SSE to Streamable HTTP

For applications currently using Server-Sent Events (SSE), migrating to Streamable HTTP provides enhanced capabilities and better long-term sustainability for your MCP implementations.

### Why Upgrade?
- Streamable HTTP offers better scalability, compatibility, and richer notification support than SSE.
- It is the recommended transport for new MCP applications.

### Migration Steps
- **Update server code** to use `transport="streamable-http"` in `mcp.run()`.
- **Update client code** to use `streamablehttp_client` instead of SSE client.
- **Implement a message handler** in the client to process notifications.
- **Test for compatibility** with existing tools and workflows.

### Maintaining Compatibility
- You can support both SSE and Streamable HTTP by running both transports on different endpoints.
- Gradually migrate clients to the new transport.

### Challenges
- Ensuring all clients are updated
- Handling differences in notification delivery

## Security Considerations

Security should be a top priority when implementing any server, especially when using HTTP-based transports like Streamable HTTP in MCP. 

When implementing MCP servers with HTTP-based transports, security becomes a paramount concern that requires careful attention to multiple attack vectors and protection mechanisms.

### Overview

Security is critical when exposing MCP servers over HTTP. Streamable HTTP introduces new attack surfaces and requires careful configuration.

Here are some key security considerations:

- **Origin Header Validation**: Always validate the `Origin` header to prevent DNS rebinding attacks.
- **Localhost Binding**: For local development, bind servers to `localhost` to avoid exposing them to the public internet.
- **Authentication**: Implement authentication (e.g., API keys, OAuth) for production deployments.
- **CORS**: Configure Cross-Origin Resource Sharing (CORS) policies to restrict access.
- **HTTPS**: Use HTTPS in production to encrypt traffic.

### Best Practices

Additionally, here are some best practices to follow when implementing security in your MCP streaming server:

- Never trust incoming requests without validation.
- Log and monitor all access and errors.
- Regularly update dependencies to patch security vulnerabilities.

### Challenges

You will face some challenges when implementing security in MCP streaming servers:

- Balancing security with ease of development
- Ensuring compatibility with various client environments


## Upgrading from SSE to Streamable HTTP

For applications currently using Server-Sent Events (SSE), migrating to Streamable HTTP provides enhanced capabilities and better long-term sustainability for your MCP implementations.

### Why Upgrade?

There are two compelling reasons to upgrade from SSE to Streamable HTTP:

- Streamable HTTP offers better scalability, compatibility, and richer notification support than SSE.
- It is the recommended transport for new MCP applications.

### Migration Steps

Here's how you can migrate from SSE to Streamable HTTP in your MCP applications:

1. **Update server code** to use `transport="streamable-http"` in `mcp.run()`.
2. **Update client code** to use `streamablehttp_client` en lugar del cliente SSE.
3. **Implementa un manejador de mensajes** en el cliente para procesar notificaciones.
4. **Prueba la compatibilidad** con herramientas y flujos de trabajo existentes.

### Mantener la Compatibilidad

Se recomienda mantener compatibilidad con clientes SSE existentes durante el proceso de migración. Aquí algunas estrategias:

- Puedes soportar ambos, SSE y Streamable HTTP, ejecutando ambos transportes en diferentes endpoints.
- Migra gradualmente los clientes al nuevo transporte.

### Desafíos

Asegúrate de abordar los siguientes desafíos durante la migración:

- Asegurar que todos los clientes estén actualizados.
- Manejar diferencias en la entrega de notificaciones.

### Ejercicio: Construye tu propia aplicación MCP con transmisión

**Escenario:**
Construye un servidor y cliente MCP donde el servidor procese una lista de ítems (por ejemplo, archivos o documentos) y envíe una notificación por cada ítem procesado. El cliente debe mostrar cada notificación conforme llega.

**Pasos:**

1. Implementa una herramienta servidor que procese una lista y envíe notificaciones por cada ítem.
2. Implementa un cliente con un manejador de mensajes para mostrar notificaciones en tiempo real.
3. Prueba tu implementación ejecutando servidor y cliente, y observa las notificaciones.

[Solución](./solution/README.md)

## Lecturas Recomendadas y ¿Qué Sigue?

Para continuar tu camino con la transmisión en MCP y ampliar tus conocimientos, esta sección proporciona recursos adicionales y los siguientes pasos sugeridos para construir aplicaciones más avanzadas.

### Lecturas Recomendadas

- [Microsoft: Introducción a HTTP Streaming](https://learn.microsoft.com/aspnet/core/fundamentals/http-requests?view=aspnetcore-8.0&WT.mc_id=%3Fwt.mc_id%3DMVP_452430#streaming)
- [Microsoft: Server-Sent Events (SSE)](https://learn.microsoft.com/azure/application-gateway/for-containers/server-sent-events?tabs=server-sent-events-gateway-api&WT.mc_id=%3Fwt.mc_id%3DMVP_452430)
- [Microsoft: CORS en ASP.NET Core](https://learn.microsoft.com/en-us/aspnet/core/security/cors?view=aspnetcore-8.0&WT.mc_id=%3Fwt.mc_id%3DMVP_452430)
- [Python requests: Solicitudes con transmisión](https://requests.readthedocs.io/en/latest/user/advanced/#streaming-requests)

### ¿Qué sigue?

- Intenta construir herramientas MCP más avanzadas que usen transmisión para análisis en tiempo real, chat o edición colaborativa.
- Explora integrar la transmisión MCP con frameworks frontend (React, Vue, etc.) para actualizaciones en vivo de la interfaz.
- Siguiente: [Utilizando AI Toolkit para VSCode](../07-aitk/README.md)

**Aviso legal**:  
Este documento ha sido traducido utilizando el servicio de traducción automática [Co-op Translator](https://github.com/Azure/co-op-translator). Aunque nos esforzamos por la precisión, tenga en cuenta que las traducciones automáticas pueden contener errores o inexactitudes. El documento original en su idioma nativo debe considerarse la fuente autorizada. Para información crítica, se recomienda la traducción profesional realizada por humanos. No nos hacemos responsables de ningún malentendido o interpretación errónea derivada del uso de esta traducción.