<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "4bf553c18e7e226c3d76ab0cde627d26",
  "translation_date": "2025-05-20T21:17:27+00:00",
  "source_file": "01-CoreConcepts/README.md",
  "language_code": "br"
}
-->
# 📖 MCP Core Concepts: Dominando o Model Context Protocol para Integração de IA

O Model Context Protocol (MCP) é uma estrutura poderosa e padronizada que otimiza a comunicação entre Large Language Models (LLMs) e ferramentas, aplicações e fontes de dados externas. Este guia otimizado para SEO vai te conduzir pelos conceitos fundamentais do MCP, garantindo que você compreenda sua arquitetura cliente-servidor, componentes essenciais, mecanismos de comunicação e melhores práticas de implementação.

## Visão Geral

Esta lição explora a arquitetura fundamental e os componentes que formam o ecossistema do Model Context Protocol (MCP). Você vai aprender sobre a arquitetura cliente-servidor, os principais componentes e os mecanismos de comunicação que sustentam as interações do MCP.

## 👩‍🎓 Objetivos de Aprendizagem

Ao final desta lição, você será capaz de:

- Entender a arquitetura cliente-servidor do MCP.
- Identificar os papéis e responsabilidades de Hosts, Clients e Servers.
- Analisar as principais características que fazem do MCP uma camada de integração flexível.
- Compreender como a informação flui dentro do ecossistema MCP.
- Obter insights práticos através de exemplos de código em .NET, Java, Python e JavaScript.

## 🔎 Arquitetura MCP: Um Olhar Mais Profundo

O ecossistema MCP é construído sobre um modelo cliente-servidor. Essa estrutura modular permite que aplicações de IA interajam eficientemente com ferramentas, bancos de dados, APIs e recursos contextuais. Vamos detalhar essa arquitetura em seus componentes principais.

### 1. Hosts

No Model Context Protocol (MCP), os Hosts desempenham um papel crucial como a interface principal pela qual os usuários interagem com o protocolo. Hosts são aplicações ou ambientes que iniciam conexões com servidores MCP para acessar dados, ferramentas e prompts. Exemplos de Hosts incluem ambientes de desenvolvimento integrados (IDEs) como Visual Studio Code, ferramentas de IA como Claude Desktop, ou agentes personalizados criados para tarefas específicas.

**Hosts** são aplicações LLM que iniciam conexões. Eles:

- Executam ou interagem com modelos de IA para gerar respostas.
- Iniciam conexões com servidores MCP.
- Gerenciam o fluxo da conversa e a interface do usuário.
- Controlam permissões e restrições de segurança.
- Lidam com o consentimento do usuário para compartilhamento de dados e execução de ferramentas.

### 2. Clients

Clients são componentes essenciais que facilitam a interação entre Hosts e servidores MCP. Eles atuam como intermediários, permitindo que Hosts acessem e utilizem as funcionalidades oferecidas pelos servidores MCP. Desempenham um papel fundamental para garantir uma comunicação fluida e uma troca eficiente de dados dentro da arquitetura MCP.

**Clients** são conectores dentro da aplicação host. Eles:

- Enviam solicitações para os servidores com prompts/instruções.
- Negociam capacidades com os servidores.
- Gerenciam pedidos de execução de ferramentas a partir dos modelos.
- Processam e exibem respostas para os usuários.

### 3. Servers

Servers são responsáveis por lidar com as solicitações dos clients MCP e fornecer respostas apropriadas. Eles gerenciam diversas operações, como recuperação de dados, execução de ferramentas e geração de prompts. Os servers garantem que a comunicação entre clients e Hosts seja eficiente e confiável, mantendo a integridade do processo de interação.

**Servers** são serviços que fornecem contexto e funcionalidades. Eles:

- Registram recursos disponíveis (resources, prompts, tools)
- Recebem e executam chamadas de ferramentas feitas pelo client
- Fornecem informações contextuais para melhorar as respostas do modelo
- Retornam os resultados para o client
- Mantêm estado entre interações quando necessário

Qualquer pessoa pode desenvolver servers para ampliar as capacidades do modelo com funcionalidades especializadas.

### 4. Recursos do Server

Servers no Model Context Protocol (MCP) oferecem blocos fundamentais que possibilitam interações ricas entre clients, hosts e modelos de linguagem. Esses recursos são projetados para ampliar as capacidades do MCP, oferecendo contexto estruturado, ferramentas e prompts.

Servers MCP podem oferecer qualquer um dos seguintes recursos:

#### 📑 Resources

Resources no Model Context Protocol (MCP) abrangem vários tipos de contexto e dados que podem ser utilizados por usuários ou modelos de IA. Isso inclui:

- **Dados Contextuais**: Informações e contexto que usuários ou modelos de IA podem usar para tomada de decisão e execução de tarefas.
- **Bases de Conhecimento e Repositórios de Documentos**: Coleções de dados estruturados e não estruturados, como artigos, manuais e trabalhos de pesquisa, que fornecem insights e informações valiosas.
- **Arquivos Locais e Bancos de Dados**: Dados armazenados localmente em dispositivos ou dentro de bancos de dados, acessíveis para processamento e análise.
- **APIs e Serviços Web**: Interfaces e serviços externos que oferecem dados e funcionalidades adicionais, permitindo integração com diversos recursos e ferramentas online.

Um exemplo de recurso pode ser um esquema de banco de dados ou um arquivo acessado assim:

```text
file://log.txt
database://schema
```

### 🤖 Prompts

Prompts no Model Context Protocol (MCP) incluem vários templates predefinidos e padrões de interação projetados para agilizar fluxos de trabalho do usuário e melhorar a comunicação. Isso inclui:

- **Mensagens e Fluxos de Trabalho Templateados**: Mensagens e processos pré-estruturados que guiam os usuários em tarefas e interações específicas.
- **Padrões de Interação Predefinidos**: Sequências padronizadas de ações e respostas que facilitam uma comunicação consistente e eficiente.
- **Templates de Conversação Especializados**: Modelos personalizáveis feitos para tipos específicos de conversas, garantindo interações relevantes e contextualmente apropriadas.

Um template de prompt pode ser assim:

```markdown
Generate a product slogan based on the following {{product}} with the following {{keywords}}
```

#### ⛏️ Tools

Tools no Model Context Protocol (MCP) são funções que o modelo de IA pode executar para realizar tarefas específicas. Essas ferramentas são projetadas para ampliar as capacidades do modelo, fornecendo operações estruturadas e confiáveis. Aspectos chave incluem:

- **Funções para o modelo de IA executar**: Tools são funções executáveis que o modelo pode invocar para realizar diversas tarefas.
- **Nome Único e Descrição**: Cada tool tem um nome distinto e uma descrição detalhada que explica seu propósito e funcionalidade.
- **Parâmetros e Resultados**: Tools aceitam parâmetros específicos e retornam resultados estruturados, garantindo resultados consistentes e previsíveis.
- **Funções Discretas**: Tools realizam funções específicas como buscas na web, cálculos e consultas a bancos de dados.

Um exemplo de tool pode ser assim:

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

## Recursos do Client

No Model Context Protocol (MCP), os clients oferecem vários recursos importantes para os servers, ampliando a funcionalidade geral e a interação dentro do protocolo. Um dos recursos notáveis é o Sampling.

### 👉 Sampling

- **Comportamentos Agentes Iniciados pelo Server**: Clients permitem que servers iniciem ações ou comportamentos específicos de forma autônoma, aumentando as capacidades dinâmicas do sistema.
- **Interações Recursivas com LLMs**: Esse recurso permite interações recursivas com grandes modelos de linguagem (LLMs), possibilitando um processamento mais complexo e iterativo de tarefas.
- **Solicitação de Completions Adicionais do Modelo**: Servers podem solicitar completions adicionais do modelo, garantindo respostas completas e contextualmente relevantes.

## Fluxo de Informação no MCP

O Model Context Protocol (MCP) define um fluxo estruturado de informações entre hosts, clients, servers e modelos. Entender esse fluxo ajuda a esclarecer como os pedidos dos usuários são processados e como ferramentas externas e dados são integrados nas respostas do modelo.

- **Host Inicia a Conexão**  
  A aplicação host (como um IDE ou interface de chat) estabelece uma conexão com um servidor MCP, normalmente via STDIO, WebSocket ou outro transporte suportado.

- **Negociação de Capacidades**  
  O client (embutido no host) e o servidor trocam informações sobre os recursos, ferramentas, versões do protocolo e funcionalidades suportadas. Isso garante que ambos os lados compreendam as capacidades disponíveis para a sessão.

- **Pedido do Usuário**  
  O usuário interage com o host (por exemplo, digitando um prompt ou comando). O host coleta essa entrada e a envia para o client para processamento.

- **Uso de Recurso ou Ferramenta**  
  - O client pode solicitar contexto ou recursos adicionais ao servidor (como arquivos, entradas de banco de dados ou artigos de base de conhecimento) para enriquecer o entendimento do modelo.
  - Se o modelo determinar que uma ferramenta é necessária (por exemplo, para buscar dados, realizar um cálculo ou chamar uma API), o client envia uma solicitação de invocação da ferramenta para o servidor, especificando o nome da ferramenta e os parâmetros.

- **Execução pelo Server**  
  O servidor recebe a solicitação de recurso ou ferramenta, executa as operações necessárias (como rodar uma função, consultar um banco de dados ou recuperar um arquivo) e retorna os resultados para o client em formato estruturado.

- **Geração da Resposta**  
  O client integra as respostas do servidor (dados de recurso, resultados da ferramenta, etc.) na interação contínua com o modelo. O modelo usa essas informações para gerar uma resposta abrangente e contextualmente relevante.

- **Apresentação do Resultado**  
  O host recebe o resultado final do client e o apresenta ao usuário, geralmente incluindo tanto o texto gerado pelo modelo quanto os resultados das execuções de ferramentas ou consultas a recursos.

Esse fluxo permite que o MCP suporte aplicações de IA avançadas, interativas e conscientes do contexto, conectando modelos com ferramentas e fontes de dados externas de forma fluida.

## Detalhes do Protocolo

O MCP (Model Context Protocol) é construído sobre [JSON-RPC 2.0](https://www.jsonrpc.org/), fornecendo um formato de mensagem padronizado e independente de linguagem para comunicação entre hosts, clients e servers. Essa base possibilita interações confiáveis, estruturadas e extensíveis em diversas plataformas e linguagens de programação.

### Principais Características do Protocolo

O MCP estende o JSON-RPC 2.0 com convenções adicionais para invocação de ferramentas, acesso a recursos e gerenciamento de prompts. Suporta múltiplas camadas de transporte (STDIO, WebSocket, SSE) e possibilita comunicação segura, extensível e independente de linguagem entre os componentes.

#### 🧢 Protocolo Base

- **Formato de Mensagens JSON-RPC**: Todas as requisições e respostas seguem a especificação JSON-RPC 2.0, garantindo estrutura consistente para chamadas de métodos, parâmetros, resultados e tratamento de erros.
- **Conexões com Estado**: Sessões MCP mantêm estado entre múltiplas requisições, suportando conversas contínuas, acumulação de contexto e gerenciamento de recursos.
- **Negociação de Capacidades**: Durante a configuração da conexão, clients e servers trocam informações sobre recursos suportados, versões do protocolo, ferramentas disponíveis e recursos. Isso garante que ambos os lados compreendam as capacidades um do outro e possam se adaptar.

#### ➕ Utilitários Adicionais

A seguir, alguns utilitários e extensões do protocolo que o MCP oferece para melhorar a experiência do desenvolvedor e permitir cenários avançados:

- **Opções de Configuração**: O MCP permite configuração dinâmica de parâmetros da sessão, como permissões de ferramentas, acesso a recursos e configurações do modelo, adaptadas a cada interação.
- **Monitoramento de Progresso**: Operações de longa duração podem reportar atualizações de progresso, possibilitando interfaces responsivas e melhor experiência do usuário durante tarefas complexas.
- **Cancelamento de Requisições**: Clients podem cancelar requisições em andamento, permitindo que usuários interrompam operações desnecessárias ou demoradas.
- **Relato de Erros**: Mensagens e códigos de erro padronizados ajudam a diagnosticar problemas, tratar falhas de forma elegante e fornecer feedback útil a usuários e desenvolvedores.
- **Registro de Logs**: Tanto clients quanto servers podem emitir logs estruturados para auditoria, depuração e monitoramento das interações do protocolo.

Aproveitando essas funcionalidades, o MCP garante comunicação robusta, segura e flexível entre modelos de linguagem e ferramentas ou fontes de dados externas.

### 🔐 Considerações de Segurança

Implementações do MCP devem seguir princípios-chave de segurança para garantir interações seguras e confiáveis:

- **Consentimento e Controle do Usuário**: Usuários devem fornecer consentimento explícito antes que qualquer dado seja acessado ou operação executada. Eles devem ter controle claro sobre quais dados são compartilhados e quais ações são autorizadas, apoiados por interfaces intuitivas para revisar e aprovar atividades.

- **Privacidade dos Dados**: Dados do usuário só devem ser expostos com consentimento explícito e protegidos por controles de acesso adequados. Implementações MCP devem prevenir transmissão não autorizada de dados e garantir a privacidade durante todas as interações.

- **Segurança das Ferramentas**: Antes de invocar qualquer ferramenta, é necessário o consentimento explícito do usuário. Eles devem entender claramente a funcionalidade de cada ferramenta, e barreiras de segurança robustas devem ser aplicadas para evitar execuções não intencionais ou inseguras.

Seguindo esses princípios, o MCP assegura que a confiança, privacidade e segurança do usuário sejam mantidas em todas as interações do protocolo.

## Exemplos de Código: Componentes Principais

A seguir, exemplos de código em várias linguagens populares que ilustram como implementar componentes principais do servidor MCP e ferramentas.

### Exemplo .NET: Criando um Servidor MCP Simples com Ferramentas

Aqui está um exemplo prático em .NET demonstrando como implementar um servidor MCP simples com ferramentas personalizadas. Este exemplo mostra como definir e registrar ferramentas, lidar com requisições e conectar o servidor usando o Model Context Protocol.

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

### Exemplo Java: Componentes do Servidor MCP

Este exemplo demonstra o mesmo servidor MCP e registro de ferramentas do exemplo .NET acima, mas implementado em Java.

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

### Exemplo Python: Construindo um Servidor MCP

Neste exemplo mostramos como construir um servidor MCP em Python. Você verá também duas formas diferentes de criar ferramentas.

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

### Exemplo JavaScript: Criando um Servidor MCP

Este exemplo mostra a criação de um servidor MCP em JavaScript e como registrar duas ferramentas relacionadas ao clima.

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

Este exemplo em JavaScript demonstra como criar um client MCP que se conecta a um servidor, envia um prompt e processa a resposta, incluindo quaisquer chamadas de ferramentas feitas.

## Segurança e Autorização

O MCP inclui vários conceitos e mecanismos embutidos para gerenciar segurança e autorização ao longo do protocolo:

1. **Controle de Permissões de Ferramentas**:  
  Clients podem especificar quais ferramentas um modelo pode usar durante uma sessão. Isso garante que apenas ferramentas explicitamente autorizadas estejam acessíveis, reduzindo riscos de operações não intencionais ou inseguras. Permissões podem ser configuradas dinamicamente com base nas preferências do usuário, políticas organizacionais ou contexto da interação.

2. **Autenticação**:  
  Servers podem exigir autenticação antes de conceder acesso a ferramentas, recursos ou operações sensíveis. Isso pode envolver chaves de API, tokens OAuth ou outros esquemas de autenticação. Autenticação adequada assegura que apenas clients e usuários confiáveis possam invocar capacidades do lado do servidor.

3. **Validação**:  
  Validação de parâmetros é aplicada a todas as invocações de ferramentas. Cada ferramenta define os tipos, formatos e restrições esperados para seus parâmetros, e o servidor valida as requisições recebidas de acordo. Isso previne entrada malformada ou maliciosa e ajuda a manter a integridade das operações.

4. **Limitação de Taxa (Rate Limiting)**:  
  Para evitar abusos e garantir uso justo dos recursos do servidor, MCP servers podem implementar limitação de taxa para chamadas de ferramentas e acesso a recursos. Limites podem ser aplicados por usuário, por sessão ou globalmente, ajudando a proteger contra ataques de negação de serviço ou consumo excessivo.

Combinando esses mecanismos, o MCP oferece uma base segura para integrar modelos de linguagem com ferramentas e fontes de dados externas, ao mesmo tempo em que oferece controle refinado de acesso e uso para usuários e desenvolvedores.

## Mensagens do Protocolo

A comunicação MCP usa mensagens JSON estruturadas para facilitar interações claras e confiáveis entre clients, servers e modelos. Os principais tipos de mensagem incluem:

- **Requisição do Client**  
  Enviada do client para o servidor, essa mensagem normalmente inclui:
  - O prompt ou comando do usuário
  - Histórico da conversa para contexto
  - Configuração e permissões de ferramentas
  - Metadados adicionais ou informações da sessão

- **Resposta do Modelo**  
  Retornada pelo modelo (via client), essa mensagem contém:
  - Texto gerado ou completion baseado no prompt e contexto
  - Instruções opcionais de chamada de ferramenta, caso o modelo determine que uma ferramenta deve ser invocada
  - Referências a recursos ou contexto adicional conforme necessário

- **Requisição de Ferramenta**  
  Enviada do client para o servidor quando uma ferramenta precisa ser executada. Essa mensagem inclui:
  - O nome da ferramenta a ser invocada
  - Parâmetros requeridos pela ferramenta (validados contra o esquema da ferramenta)
  - Informações contextuais ou identificadores para rastrear a requisição

- **Resposta da Ferramenta**  
  Retornada pelo servidor após a execução da ferramenta. Essa mensagem fornece:
  - Os resultados da execução da ferramenta (dados estruturados ou conteúdo)
  - Quaisquer erros ou informações de status caso a chamada da ferramenta tenha falhado
  - Opcionalmente, metadados adicionais ou logs relacionados à execução

Essas mensagens estruturadas garantem que cada etapa do fluxo MCP seja explícita, rastreável e extensível, suportando cenários avançados como conversas multi-turno, encadeamento de ferramentas e tratamento robusto de erros.

## Principais Lições

- MCP usa uma arquitetura cliente-servidor para conectar modelos com capacidades externas
- O ecossistema é composto por clients, hosts, servers, tools e fontes de dados
- A comunicação pode ocorrer via STDIO, SSE ou WebSockets
- Tools são as unidades fundamentais de funcionalidade expostas aos modelos
- Protocolos de comunicação estruturados garantem interações consistentes

## Exercício

Projete uma tool simples MCP que seria útil no seu domínio. Defina:
1. Qual seria o nome da tool
2. Quais parâmetros ela aceitaria
3. Qual saída ela retornaria
4. Como um modelo poderia usar essa tool para resolver problemas dos usuários

---

## O que vem a seguir

Próximo: [Capítulo 2: Segurança](/02-Security/README.md)

**Aviso Legal**:  
Este documento foi traduzido utilizando o serviço de tradução automática [Co-op Translator](https://github.com/Azure/co-op-translator). Embora nos esforcemos para garantir a precisão, esteja ciente de que traduções automáticas podem conter erros ou imprecisões. O documento original em seu idioma nativo deve ser considerado a fonte autorizada. Para informações críticas, recomenda-se tradução profissional humana. Não nos responsabilizamos por quaisquer mal-entendidos ou interpretações incorretas decorrentes do uso desta tradução.