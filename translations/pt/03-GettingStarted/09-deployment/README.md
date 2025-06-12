<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "7816cc28f7ab9a54e31f9246429ffcd9",
  "translation_date": "2025-06-12T22:11:34+00:00",
  "source_file": "03-GettingStarted/09-deployment/README.md",
  "language_code": "pt"
}
-->
# Implantando Servidores MCP

Implantar seu servidor MCP permite que outras pessoas acessem suas ferramentas e recursos além do seu ambiente local. Existem várias estratégias de implantação a considerar, dependendo das suas necessidades de escalabilidade, confiabilidade e facilidade de gerenciamento. Abaixo, você encontrará orientações para implantar servidores MCP localmente, em contêineres e na nuvem.

## Visão Geral

Esta lição aborda como implantar seu aplicativo MCP Server.

## Objetivos de Aprendizagem

Ao final desta lição, você será capaz de:

- Avaliar diferentes abordagens de implantação.
- Implantar seu aplicativo.

## Desenvolvimento e implantação local

Se o seu servidor for destinado a ser utilizado rodando na máquina dos usuários, você pode seguir os seguintes passos:

1. **Baixe o servidor**. Se você não escreveu o servidor, baixe-o primeiro para sua máquina.  
1. **Inicie o processo do servidor**: Execute seu aplicativo MCP server.

Para SSE (não necessário para servidor do tipo stdio)

1. **Configure a rede**: Garanta que o servidor esteja acessível na porta esperada.  
1. **Conecte os clientes**: Use URLs de conexão locais como `http://localhost:3000`

## Implantação na Nuvem

Servidores MCP podem ser implantados em várias plataformas de nuvem:

- **Funções Serverless**: Implemente servidores MCP leves como funções serverless  
- **Serviços de Contêiner**: Use serviços como Azure Container Apps, AWS ECS ou Google Cloud Run  
- **Kubernetes**: Implemente e gerencie servidores MCP em clusters Kubernetes para alta disponibilidade

### Exemplo: Azure Container Apps

Azure Container Apps suporta a implantação de servidores MCP. Ainda está em desenvolvimento e atualmente suporta servidores SSE.

Veja como você pode fazer isso:

1. Clone um repositório:

  ```sh
  git clone https://github.com/anthonychu/azure-container-apps-mcp-sample.git
  ```

1. Execute localmente para testar:

  ```sh
  uv venv
  uv sync

  # linux/macOS
  export API_KEYS=<AN_API_KEY>
  # windows
  set API_KEYS=<AN_API_KEY>

  uv run fastapi dev main.py
  ```

1. Para testar localmente, crie um arquivo *mcp.json* em um diretório *.vscode* e adicione o seguinte conteúdo:

  ```json
  {
      "inputs": [
          {
              "type": "promptString",
              "id": "weather-api-key",
              "description": "Weather API Key",
              "password": true
          }
      ],
      "servers": {
          "weather-sse": {
              "type": "sse",
              "url": "http://localhost:8000/sse",
              "headers": {
                  "x-api-key": "${input:weather-api-key}"
              }
          }
      }
  }
  ```

  Uma vez que o servidor SSE esteja iniciado, você pode clicar no ícone de play no arquivo JSON, e deverá ver as ferramentas no servidor sendo reconhecidas pelo GitHub Copilot, observe o ícone da Ferramenta.

1. Para implantar, execute o seguinte comando:

  ```sh
  az containerapp up -g <RESOURCE_GROUP_NAME> -n weather-mcp --environment mcp -l westus --env-vars API_KEYS=<AN_API_KEY> --source .
  ```

Pronto, implante localmente ou na Azure seguindo esses passos.

## Recursos Adicionais

- [Azure Functions + MCP](https://learn.microsoft.com/en-us/samples/azure-samples/remote-mcp-functions-dotnet/remote-mcp-functions-dotnet/)
- [Artigo sobre Azure Container Apps](https://techcommunity.microsoft.com/blog/appsonazureblog/host-remote-mcp-servers-in-azure-container-apps/4403550)
- [Repositório MCP para Azure Container Apps](https://github.com/anthonychu/azure-container-apps-mcp-sample)

## Próximos Passos

- Próximo: [Implementação Prática](/04-PracticalImplementation/README.md)

**Aviso Legal**:  
Este documento foi traduzido utilizando o serviço de tradução automática [Co-op Translator](https://github.com/Azure/co-op-translator). Embora nos esforcemos para garantir a precisão, esteja ciente de que traduções automatizadas podem conter erros ou imprecisões. O documento original em seu idioma nativo deve ser considerado a fonte autorizada. Para informações críticas, recomenda-se tradução profissional humana. Não nos responsabilizamos por quaisquer mal-entendidos ou interpretações incorretas decorrentes do uso desta tradução.