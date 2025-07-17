<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "73240f845b99df9401fffd21c09a5f7b",
  "translation_date": "2025-07-17T08:18:58+00:00",
  "source_file": "05-AdvancedTopics/mcp-integration/README.md",
  "language_code": "tl"
}
-->
# Enterprise Integration

Kapag nagtatayo ng MCP Servers sa konteksto ng enterprise, madalas mong kailangang isama ito sa mga umiiral na AI platform at serbisyo. Tinutukoy ng seksyong ito kung paano i-integrate ang MCP sa mga enterprise system tulad ng Azure OpenAI at Microsoft AI Foundry, na nagbibigay-daan sa advanced na AI capabilities at tool orchestration.

## Panimula

Sa araling ito, matututuhan mo kung paano i-integrate ang Model Context Protocol (MCP) sa mga enterprise AI system, na nakatuon sa Azure OpenAI at Microsoft AI Foundry. Pinapayagan ka ng mga integrasyong ito na gamitin ang makapangyarihang AI models at tools habang pinananatili ang flexibility at extensibility ng MCP.

## Mga Layunin sa Pagkatuto

Sa pagtatapos ng araling ito, magagawa mong:

- I-integrate ang MCP sa Azure OpenAI upang magamit ang mga AI capabilities nito.
- Ipatupad ang MCP tool orchestration gamit ang Azure OpenAI.
- Pagsamahin ang MCP sa Microsoft AI Foundry para sa advanced na kakayahan ng AI agent.
- Gamitin ang Azure Machine Learning (ML) para sa pagpapatupad ng ML pipelines at pagrerehistro ng mga modelo bilang MCP tools.

## Azure OpenAI Integration

Nagbibigay ang Azure OpenAI ng access sa makapangyarihang AI models tulad ng GPT-4 at iba pa. Ang pag-integrate ng MCP sa Azure OpenAI ay nagpapahintulot sa iyo na gamitin ang mga modelong ito habang pinananatili ang flexibility ng tool orchestration ng MCP.

### C# Implementation

Sa code snippet na ito, ipinapakita namin kung paano i-integrate ang MCP sa Azure OpenAI gamit ang Azure OpenAI SDK.

```csharp
// .NET Azure OpenAI Integration
using Microsoft.Mcp.Client;
using Azure.AI.OpenAI;
using Microsoft.Extensions.Configuration;
using System.Threading.Tasks;

namespace EnterpriseIntegration
{
    public class AzureOpenAiMcpClient
    {
        private readonly string _endpoint;
        private readonly string _apiKey;
        private readonly string _deploymentName;
        
        public AzureOpenAiMcpClient(IConfiguration config)
        {
            _endpoint = config["AzureOpenAI:Endpoint"];
            _apiKey = config["AzureOpenAI:ApiKey"];
            _deploymentName = config["AzureOpenAI:DeploymentName"];
        }
        
        public async Task<string> GetCompletionWithToolsAsync(string prompt, params string[] allowedTools)
        {
            // Create OpenAI client
            var client = new OpenAIClient(new Uri(_endpoint), new AzureKeyCredential(_apiKey));
            
            // Create completion options with tools
            var completionOptions = new ChatCompletionsOptions
            {
                DeploymentName = _deploymentName,
                Messages = { new ChatMessage(ChatRole.User, prompt) },
                Temperature = 0.7f,
                MaxTokens = 800
            };
            
            // Add tool definitions
            foreach (var tool in allowedTools)
            {
                completionOptions.Tools.Add(new ChatCompletionsFunctionToolDefinition
                {
                    Name = tool,
                    // In a real implementation, you'd add the tool schema here
                });
            }
            
            // Get completion response
            var response = await client.GetChatCompletionsAsync(completionOptions);
            
            // Handle tool calls in the response
            foreach (var toolCall in response.Value.Choices[0].Message.ToolCalls)
            {
                // Implementation to handle Azure OpenAI tool calls with MCP
                // ...
            }
            
            return response.Value.Choices[0].Message.Content;
        }
    }
}
```

Sa naunang code ay:

- Na-configure ang Azure OpenAI client gamit ang endpoint, deployment name, at API key.
- Nilikha ang method na `GetCompletionWithToolsAsync` para makakuha ng completions na may suporta sa tools.
- Hinawakan ang mga tool calls sa response.

Hinihikayat kang ipatupad ang aktwal na lohika sa paghawak ng tools base sa iyong partikular na setup ng MCP server.

## Microsoft AI Foundry Integration

Nagbibigay ang Azure AI Foundry ng platform para sa pagbuo at deployment ng AI agents. Ang pag-integrate ng MCP sa AI Foundry ay nagpapahintulot sa iyo na gamitin ang mga kakayahan nito habang pinananatili ang flexibility ng MCP.

Sa code sa ibaba, bumuo kami ng isang Agent integration na nagpoproseso ng mga request at humahawak ng tool calls gamit ang MCP.

### Java Implementation

```java
// Java AI Foundry Agent Integration
package com.example.mcp.enterprise;

import com.microsoft.aifoundry.AgentClient;
import com.microsoft.aifoundry.AgentToolResponse;
import com.microsoft.aifoundry.models.AgentRequest;
import com.microsoft.aifoundry.models.AgentResponse;
import com.mcp.client.McpClient;
import com.mcp.tools.ToolRequest;
import com.mcp.tools.ToolResponse;

public class AIFoundryMcpBridge {
    private final AgentClient agentClient;
    private final McpClient mcpClient;
    
    public AIFoundryMcpBridge(String aiFoundryEndpoint, String mcpServerUrl) {
        this.agentClient = new AgentClient(aiFoundryEndpoint);
        this.mcpClient = new McpClient.Builder()
            .setServerUrl(mcpServerUrl)
            .build();
    }
    
    public AgentResponse processAgentRequest(AgentRequest request) {
        // Process the AI Foundry Agent request
        AgentResponse initialResponse = agentClient.processRequest(request);
        
        // Check if the agent requested to use tools
        if (initialResponse.getToolCalls() != null && !initialResponse.getToolCalls().isEmpty()) {
            // For each tool call, route it to the appropriate MCP tool
            for (AgentToolCall toolCall : initialResponse.getToolCalls()) {
                String toolName = toolCall.getName();
                Map<String, Object> parameters = toolCall.getArguments();
                
                // Execute the tool using MCP
                ToolResponse mcpResponse = mcpClient.executeTool(toolName, parameters);
                
                // Create tool response for AI Foundry
                AgentToolResponse toolResponse = new AgentToolResponse(
                    toolCall.getId(),
                    mcpResponse.getResult()
                );
                
                // Submit tool response back to the agent
                initialResponse = agentClient.submitToolResponse(
                    request.getConversationId(), 
                    toolResponse
                );
            }
        }
        
        return initialResponse;
    }
}
```

Sa naunang code, ginawa namin ang mga sumusunod:

- Nilikha ang `AIFoundryMcpBridge` class na nag-iintegrate sa parehong AI Foundry at MCP.
- Ipinatupad ang method na `processAgentRequest` na nagpoproseso ng AI Foundry agent request.
- Hinawakan ang tool calls sa pamamagitan ng pagpapatupad nito gamit ang MCP client at pagsusumite ng mga resulta pabalik sa AI Foundry agent.

## Pag-integrate ng MCP sa Azure ML

Ang pag-integrate ng MCP sa Azure Machine Learning (ML) ay nagpapahintulot sa iyo na gamitin ang makapangyarihang ML capabilities ng Azure habang pinananatili ang flexibility ng MCP. Magagamit ang integrasyong ito para magpatakbo ng ML pipelines, magrehistro ng mga modelo bilang tools, at pamahalaan ang compute resources.

### Python Implementation

```python
# Python Azure AI Integration
from mcp_client import McpClient
from azure.ai.ml import MLClient
from azure.identity import DefaultAzureCredential
from azure.ai.ml.entities import Environment, AmlCompute
import os
import asyncio

class EnterpriseAiIntegration:
    def __init__(self, mcp_server_url, subscription_id, resource_group, workspace_name):
        # Set up MCP client
        self.mcp_client = McpClient(server_url=mcp_server_url)
        
        # Set up Azure ML client
        self.credential = DefaultAzureCredential()
        self.ml_client = MLClient(
            self.credential,
            subscription_id,
            resource_group,
            workspace_name
        )
    
    async def execute_ml_pipeline(self, pipeline_name, input_data):
        """Executes an ML pipeline in Azure ML"""
        # First process the input data using MCP tools
        processed_data = await self.mcp_client.execute_tool(
            "dataPreprocessor",
            {
                "data": input_data,
                "operations": ["normalize", "clean", "transform"]
            }
        )
        
        # Submit the pipeline to Azure ML
        pipeline_job = self.ml_client.jobs.create_or_update(
            entity={
                "name": pipeline_name,
                "display_name": f"MCP-triggered {pipeline_name}",
                "experiment_name": "mcp-integration",
                "inputs": {
                    "processed_data": processed_data.result
                }
            }
        )
        
        # Return job information
        return {
            "job_id": pipeline_job.id,
            "status": pipeline_job.status,
            "creation_time": pipeline_job.creation_context.created_at
        }
    
    async def register_ml_model_as_tool(self, model_name, model_version="latest"):
        """Registers an Azure ML model as an MCP tool"""
        # Get model details
        if model_version == "latest":
            model = self.ml_client.models.get(name=model_name, label="latest")
        else:
            model = self.ml_client.models.get(name=model_name, version=model_version)
        
        # Create deployment environment
        env = Environment(
            name="mcp-model-env",
            conda_file="./environments/inference-env.yml"
        )
        
        # Set up compute
        compute = self.ml_client.compute.get("mcp-inference")
        
        # Deploy model as online endpoint
        deployment = self.ml_client.online_deployments.create_or_update(
            endpoint_name=f"mcp-{model_name}",
            deployment={
                "name": f"mcp-{model_name}-deployment",
                "model": model.id,
                "environment": env,
                "compute": compute,
                "scale_settings": {
                    "scale_type": "auto",
                    "min_instances": 1,
                    "max_instances": 3
                }
            }
        )
        
        # Create MCP tool schema based on model schema
        tool_schema = {
            "type": "object",
            "properties": {},
            "required": []
        }
        
        # Add input properties based on model schema
        for input_name, input_spec in model.signature.inputs.items():
            tool_schema["properties"][input_name] = {
                "type": self._map_ml_type_to_json_type(input_spec.type)
            }
            tool_schema["required"].append(input_name)
        
        # Register as MCP tool
        # In a real implementation, you would create a tool that calls the endpoint
        return {
            "model_name": model_name,
            "model_version": model.version,
            "endpoint": deployment.endpoint_uri,
            "tool_schema": tool_schema
        }
    
    def _map_ml_type_to_json_type(self, ml_type):
        """Maps ML data types to JSON schema types"""
        mapping = {
            "float": "number",
            "int": "integer",
            "bool": "boolean",
            "str": "string",
            "object": "object",
            "array": "array"
        }
        return mapping.get(ml_type, "string")
```

Sa naunang code, ginawa namin ang mga sumusunod:

- Nilikha ang `EnterpriseAiIntegration` class na nag-iintegrate ng MCP sa Azure ML.
- Ipinatupad ang method na `execute_ml_pipeline` na nagpoproseso ng input data gamit ang MCP tools at nagsusumite ng ML pipeline sa Azure ML.
- Ipinatupad ang method na `register_ml_model_as_tool` na nagrerehistro ng Azure ML model bilang MCP tool, kabilang ang paglikha ng kinakailangang deployment environment at compute resources.
- Inilapat ang pagma-map ng Azure ML data types sa JSON schema types para sa pagrerehistro ng tools.
- Gumamit ng asynchronous programming para hawakan ang mga posibleng matagal na operasyon tulad ng pagpapatupad ng ML pipeline at pagrerehistro ng modelo.

## Ano ang susunod

- [5.2 Multi modality](../mcp-multi-modality/README.md)

**Paalala**:  
Ang dokumentong ito ay isinalin gamit ang AI translation service na [Co-op Translator](https://github.com/Azure/co-op-translator). Bagamat nagsusumikap kami para sa katumpakan, pakatandaan na ang mga awtomatikong pagsasalin ay maaaring maglaman ng mga pagkakamali o di-tumpak na impormasyon. Ang orihinal na dokumento sa orihinal nitong wika ang dapat ituring na pangunahing sanggunian. Para sa mahahalagang impormasyon, inirerekomenda ang propesyonal na pagsasalin ng tao. Hindi kami mananagot sa anumang hindi pagkakaunawaan o maling interpretasyon na maaaring magmula sa paggamit ng pagsasaling ito.