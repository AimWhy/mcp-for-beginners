<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "f7a8ffd07682d554929968dfc6ae2ecb",
  "translation_date": "2025-05-16T15:37:19+00:00",
  "source_file": "04-PracticalImplementation/samples/typescript/README.md",
  "language_code": "de"
}
-->
# Beispiel

Dies ist ein Typescript-Beispiel für einen MCP-Server

Hier ist ein Beispiel zur Erstellung eines Tools:

```typescript
this.mcpServer.tool(
'completion',
{
    model: z.string(),
    prompt: z.string(),
    options: z.object({
        temperature: z.number().optional(),
        max_tokens: z.number().optional(),
        stream: z.boolean().optional()
    }).optional()
},
async ({ model, prompt, options }) => {
    console.log(`Processing completion request for model: ${model}`);

    // Validate model
    if (!this.models.includes(model)) {
        throw new Error(`Model ${model} not supported`);
    }

    // Emit event for monitoring/metrics
    this.events.emit('request', { 
        type: 'completion', 
        model, 
        timestamp: new Date() 
    });

    // In a real implementation, this would call an AI model
    // Here we just echo back parts of the request with a mock response
    const response = {
        id: `mcp-resp-${Date.now()}`,
        model,
        text: `This is a response to: ${prompt.substring(0, 30)}...`,
        usage: {
        promptTokens: prompt.split(' ').length,
        completionTokens: 20,
        totalTokens: prompt.split(' ').length + 20
        }
    };

    // Simulate network delay
    await new Promise(resolve => setTimeout(resolve, 500));

    // Emit completion event
    this.events.emit('completion', {
        model,
        timestamp: new Date()
    });

    return {
        content: [
        {
            type: 'text',
            text: JSON.stringify(response)
        }
        ]
    };
}
);
```

## Installation

Führen Sie den folgenden Befehl aus:

```bash
npm install
```

## Ausführen

```bash
npm start
```

**Haftungsausschluss**:  
Dieses Dokument wurde mithilfe des KI-Übersetzungsdienstes [Co-op Translator](https://github.com/Azure/co-op-translator) übersetzt. Obwohl wir uns um Genauigkeit bemühen, beachten Sie bitte, dass automatisierte Übersetzungen Fehler oder Ungenauigkeiten enthalten können. Das Originaldokument in seiner Ursprungssprache gilt als maßgebliche Quelle. Für wichtige Informationen wird eine professionelle menschliche Übersetzung empfohlen. Wir übernehmen keine Haftung für Missverständnisse oder Fehlinterpretationen, die durch die Nutzung dieser Übersetzung entstehen.