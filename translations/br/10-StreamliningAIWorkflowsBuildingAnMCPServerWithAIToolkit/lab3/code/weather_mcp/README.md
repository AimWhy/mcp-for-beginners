<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "999c5e7623c1e2d5e5a07c2feb39eb67",
  "translation_date": "2025-06-10T06:29:01+00:00",
  "source_file": "10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab3/code/weather_mcp/README.md",
  "language_code": "br"
}
-->
# Weather MCP Server

Este é um exemplo de MCP Server em Python que implementa ferramentas de clima com respostas simuladas. Pode ser usado como base para o seu próprio MCP Server. Inclui as seguintes funcionalidades:

- **Weather Tool**: Uma ferramenta que fornece informações de clima simuladas com base na localização informada.
- **Conectar ao Agent Builder**: Um recurso que permite conectar o MCP Server ao Agent Builder para testes e depuração.
- **Depurar no [MCP Inspector](https://github.com/modelcontextprotocol/inspector)**: Um recurso que permite depurar o MCP Server usando o MCP Inspector.

## Começando com o template Weather MCP Server

> **Pré-requisitos**
>
> Para executar o MCP Server na sua máquina de desenvolvimento local, você precisará de:
>
> - [Python](https://www.python.org/)
> - (*Opcional - se preferir uv*) [uv](https://github.com/astral-sh/uv)
> - [Extensão Python Debugger](https://marketplace.visualstudio.com/items?itemName=ms-python.debugpy)

## Preparar o ambiente

Existem duas formas de configurar o ambiente para este projeto. Você pode escolher qualquer uma delas conforme sua preferência.

> Nota: Recarregue o VSCode ou o terminal para garantir que o Python do ambiente virtual seja usado após a criação do ambiente virtual.

| Abordagem | Passos |
| -------- | ----- |
| Usando `uv` | 1. Crie o ambiente virtual: `uv venv` <br>2. Execute o comando do VSCode "***Python: Select Interpreter***" e selecione o Python do ambiente virtual criado <br>3. Instale as dependências (incluindo as de desenvolvimento): `uv pip install -r pyproject.toml --extra dev` |
| Usando `pip` | 1. Crie o ambiente virtual: `python -m venv .venv` <br>2. Execute o comando do VSCode "***Python: Select Interpreter***" e selecione o Python do ambiente virtual criado<br>3. Instale as dependências (incluindo as de desenvolvimento): `pip install -e .[dev]` |

Após configurar o ambiente, você pode executar o servidor na sua máquina local via Agent Builder como MCP Client para começar:
1. Abra o painel de depuração do VS Code. Selecione `Debug in Agent Builder` ou pressione `F5` para iniciar a depuração do MCP Server.
2. Use o AI Toolkit Agent Builder para testar o servidor com [este prompt](../../../../../../../../../../../open_prompt_builder). O servidor será conectado automaticamente ao Agent Builder.
3. Clique `Run` para testar o servidor com o prompt.

**Parabéns**! Você executou com sucesso o Weather MCP Server na sua máquina local via Agent Builder como MCP Client.
![DebugMCP](https://raw.githubusercontent.com/microsoft/windows-ai-studio-templates/refs/heads/dev/mcpServers/mcp_debug.gif)

## O que está incluído no template

| Pasta / Arquivo | Conteúdo                                    |
| --------------- | ------------------------------------------- |
| `.vscode`    | Arquivos do VSCode para depuração           |
| `.aitk`      | Configurações para o AI Toolkit              |
| `src`        | Código-fonte do weather mcp server           |

## Como depurar o Weather MCP Server

> Notas:
> - [MCP Inspector](https://github.com/modelcontextprotocol/inspector) é uma ferramenta visual para desenvolvedores testarem e depurarem MCP servers.
> - Todos os modos de depuração suportam breakpoints, então você pode adicionar pontos de interrupção no código da implementação da ferramenta.

| Modo de Depuração | Descrição | Passos para depurar |
| ----------------- | --------- | ------------------- |
| Agent Builder | Depure o MCP Server no Agent Builder via AI Toolkit. | 1. Abra o painel de depuração do VS Code. Selecione `Debug in Agent Builder` e pressione `F5` para iniciar a depuração do MCP Server.<br>2. Use o AI Toolkit Agent Builder para testar o servidor com [este prompt](../../../../../../../../../../../open_prompt_builder). O servidor será conectado automaticamente ao Agent Builder.<br>3. Clique `Run` para testar o servidor com o prompt. |
| MCP Inspector | Depure o MCP Server usando o MCP Inspector. | 1. Instale o [Node.js](https://nodejs.org/)<br> 2. Configure o Inspector: `cd inspector` && `npm install` <br> 3. Abra o painel de depuração do VS Code. Selecione `Debug SSE in Inspector (Edge)` ou `Debug SSE in Inspector (Chrome)`. Pressione F5 para iniciar a depuração.<br> 4. Quando o MCP Inspector abrir no navegador, clique no botão `Connect` para conectar este MCP Server.<br> 5. Então você pode `List Tools`, selecionar uma ferramenta, inserir parâmetros e `Run Tool` para depurar seu código do servidor.<br> |

## Portas padrão e personalizações

| Modo de Depuração | Portas | Definições | Personalizações | Observação |
| ----------------- | ------ | ---------- | -------------- | ---------- |
| Agent Builder | 3001 | [tasks.json](../../../../../../10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab3/code/weather_mcp/.vscode/tasks.json) | Edite [launch.json](../../../../../../10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab3/code/weather_mcp/.vscode/launch.json), [tasks.json](../../../../../../10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab3/code/weather_mcp/.vscode/tasks.json), [\_\_init\_\_.py](../../../../../../10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab3/code/weather_mcp/src/__init__.py), [mcp.json](../../../../../../10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab3/code/weather_mcp/.aitk/mcp.json) para alterar as portas acima. | N/A |
| MCP Inspector | 3001 (Servidor); 5173 e 3000 (Inspector) | [tasks.json](../../../../../../10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab3/code/weather_mcp/.vscode/tasks.json) | Edite [launch.json](../../../../../../10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab3/code/weather_mcp/.vscode/launch.json), [tasks.json](../../../../../../10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab3/code/weather_mcp/.vscode/tasks.json), [\_\_init\_\_.py](../../../../../../10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab3/code/weather_mcp/src/__init__.py), [mcp.json](../../../../../../10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab3/code/weather_mcp/.aitk/mcp.json) para alterar as portas acima. | N/A |

## Feedback

Se você tiver algum feedback ou sugestão para este template, por favor, abra uma issue no [repositório AI Toolkit no GitHub](https://github.com/microsoft/vscode-ai-toolkit/issues)

**Aviso Legal**:  
Este documento foi traduzido utilizando o serviço de tradução automática [Co-op Translator](https://github.com/Azure/co-op-translator). Embora nos esforcemos para garantir a precisão, esteja ciente de que traduções automáticas podem conter erros ou imprecisões. O documento original em seu idioma nativo deve ser considerado a fonte oficial. Para informações críticas, recomenda-se a tradução profissional feita por humanos. Não nos responsabilizamos por quaisquer mal-entendidos ou interpretações equivocadas decorrentes do uso desta tradução.