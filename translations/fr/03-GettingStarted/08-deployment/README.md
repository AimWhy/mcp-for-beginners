<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "7816cc28f7ab9a54e31f9246429ffcd9",
  "translation_date": "2025-05-16T14:59:59+00:00",
  "source_file": "03-GettingStarted/08-deployment/README.md",
  "language_code": "fr"
}
-->
# Déploiement des serveurs MCP

Déployer votre serveur MCP permet à d’autres d’accéder à ses outils et ressources au-delà de votre environnement local. Plusieurs stratégies de déploiement sont à considérer, selon vos besoins en termes de scalabilité, fiabilité et facilité de gestion. Vous trouverez ci-dessous des conseils pour déployer des serveurs MCP localement, dans des conteneurs et sur le cloud.

## Vue d’ensemble

Cette leçon explique comment déployer votre application MCP Server.

## Objectifs d’apprentissage

À la fin de cette leçon, vous serez capable de :

- Évaluer différentes approches de déploiement.
- Déployer votre application.

## Développement et déploiement local

Si votre serveur est destiné à être utilisé directement sur la machine des utilisateurs, vous pouvez suivre les étapes suivantes :

1. **Téléchargez le serveur**. Si vous n’avez pas écrit le serveur, téléchargez-le d’abord sur votre machine.  
1. **Démarrez le processus serveur** : Lancez votre application MCP server.

Pour SSE (non nécessaire pour un serveur de type stdio) :

1. **Configurez le réseau** : Assurez-vous que le serveur est accessible sur le port attendu.  
1. **Connectez les clients** : Utilisez des URLs de connexion locales comme `http://localhost:3000`.

## Déploiement sur le cloud

Les serveurs MCP peuvent être déployés sur différentes plateformes cloud :

- **Fonctions serverless** : Déployez des serveurs MCP légers en tant que fonctions serverless.  
- **Services de conteneurs** : Utilisez des services comme Azure Container Apps, AWS ECS ou Google Cloud Run.  
- **Kubernetes** : Déployez et gérez des serveurs MCP dans des clusters Kubernetes pour une haute disponibilité.

### Exemple : Azure Container Apps

Azure Container Apps prend en charge le déploiement des serveurs MCP. C’est encore en cours de développement et il supporte actuellement les serveurs SSE.

Voici comment procéder :

1. Clonez un dépôt :

  ```sh
  git clone https://github.com/anthonychu/azure-container-apps-mcp-sample.git
  ```

1. Lancez-le localement pour tester :

  ```sh
  uv venv
  uv sync

  # linux/macOS
  export API_KEYS=<AN_API_KEY>
  # windows
  set API_KEYS=<AN_API_KEY>

  uv run fastapi dev main.py
  ```

1. Pour tester localement, créez un fichier *mcp.json* dans un dossier *.vscode* et ajoutez le contenu suivant :

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

  Une fois le serveur SSE démarré, vous pouvez cliquer sur l’icône de lecture dans le fichier JSON, vous devriez voir les outils du serveur détectés par GitHub Copilot, repérez l’icône Tool.

1. Pour déployer, exécutez la commande suivante :

  ```sh
  az containerapp up -g <RESOURCE_GROUP_NAME> -n weather-mcp --environment mcp -l westus --env-vars API_KEYS=<AN_API_KEY> --source .
  ```

Voilà, déployez-le localement ou sur Azure en suivant ces étapes.

## Ressources supplémentaires

- [Azure Functions + MCP](https://learn.microsoft.com/en-us/samples/azure-samples/remote-mcp-functions-dotnet/remote-mcp-functions-dotnet/)  
- [Article sur Azure Container Apps](https://techcommunity.microsoft.com/blog/appsonazureblog/host-remote-mcp-servers-in-azure-container-apps/4403550)  
- [Dépôt MCP Azure Container Apps](https://github.com/anthonychu/azure-container-apps-mcp-sample)  

## Et après ?

- Suivant : [Mise en œuvre pratique](/04-PracticalImplementation/README.md)

**Avertissement** :  
Ce document a été traduit à l'aide du service de traduction automatique [Co-op Translator](https://github.com/Azure/co-op-translator). Bien que nous nous efforçons d'assurer l'exactitude, veuillez noter que les traductions automatiques peuvent contenir des erreurs ou des inexactitudes. Le document original dans sa langue native doit être considéré comme la source faisant foi. Pour les informations critiques, une traduction professionnelle humaine est recommandée. Nous déclinons toute responsabilité en cas de malentendus ou d'interprétations erronées résultant de l'utilisation de cette traduction.