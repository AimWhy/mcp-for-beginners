<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "f7a8ffd07682d554929968dfc6ae2ecb",
  "translation_date": "2025-05-17T15:07:24+00:00",
  "source_file": "04-PracticalImplementation/samples/typescript/README.md",
  "language_code": "sk"
}
-->
# Ukážka

Toto je ukážka Typescriptu pre MCP Server

Tu je príklad vytvorenia nástroja:

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

## Inštalácia

Spustite nasledujúci príkaz:

```bash
npm install
```

## Spustenie

```bash
npm start
```

**Upozornenie**:  
Tento dokument bol preložený pomocou AI prekladovej služby [Co-op Translator](https://github.com/Azure/co-op-translator). Hoci sa snažíme o presnosť, uvedomte si, že automatizované preklady môžu obsahovať chyby alebo nepresnosti. Pôvodný dokument v jeho rodnom jazyku by mal byť považovaný za autoritatívny zdroj. Pre kritické informácie sa odporúča profesionálny ľudský preklad. Nie sme zodpovední za žiadne nedorozumenia alebo nesprávne interpretácie vyplývajúce z použitia tohto prekladu.