<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "bc76969a3bb20c032d1d5e95a304a2e3",
  "translation_date": "2025-06-24T16:38:05+00:00",
  "source_file": "README.md",
  "language_code": "fi"
}
-->
![MCP-for-beginners](../../translated_images/mcp-beginners.2ce2b317996369ff66c5b72e25eff9d4288ab2741fc70c0b4e523d1ae1e249fd.fi.png) 

[![GitHub contributors](https://img.shields.io/github/contributors/microsoft/mcp-for-beginners.svg)](https://GitHub.com/microsoft/mcp-for-beginners/graphs/contributors)
[![GitHub issues](https://img.shields.io/github/issues/microsoft/mcp-for-beginners.svg)](https://GitHub.com/microsoft/mcp-for-beginners/issues)
[![GitHub pull-requests](https://img.shields.io/github/issues-pr/microsoft/mcp-for-beginners.svg)](https://GitHub.com/microsoft/mcp-for-beginners/pulls)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com)

[![GitHub watchers](https://img.shields.io/github/watchers/microsoft/mcp-for-beginners.svg?style=social&label=Watch)](https://GitHub.com/microsoft/mcp-for-beginners/watchers)
[![GitHub forks](https://img.shields.io/github/forks/microsoft/mcp-for-beginners.svg?style=social&label=Fork)](https://GitHub.com/microsoft/mcp-for-beginners/fork)
[![GitHub stars](https://img.shields.io/github/stars/microsoft/mcp-for-beginners?style=social&label=Star)](https://GitHub.com/microsoft/mcp-for-beginners/stargazers)


[![Microsoft Azure AI Foundry Discord](https://dcbadge.vercel.app/api/server/ByRwuEEgH4)](https://discord.com/invite/ByRwuEEgH4)


Seuraa näitä ohjeita aloittaaksesi näiden resurssien käytön:
1. **Tee forkki repositoriosta**: Klikkaa [![GitHub forks](https://img.shields.io/github/forks/microsoft/mcp-for-beginners.svg?style=social&label=Fork)](https://GitHub.com/microsoft/mcp-for-beginners/fork)
2. **Kloonaa repositorio**:   `git clone https://github.com/microsoft/mcp-for-beginners.git`
3. [**Liity Azure AI Foundryn Discordiin ja tapaa asiantuntijoita sekä muita kehittäjiä**](https://discord.com/invite/ByRwuEEgH4)


### 🌐 Monikielinen tuki

#### Tuettu GitHub Actionin kautta (automaattinen ja aina ajan tasalla)

# 🚀 Model Context Protocol (MCP) -opetussuunnitelma aloittelijoille

## **Opi MCP käytännön koodiesimerkkien avulla C#:ssa, Javassa, JavaScriptissä, Pythonissa ja TypeScriptissä**

## 🧠 Yleiskatsaus Model Context Protocol -opetussuunnitelmaan

**Model Context Protocol (MCP)** on huippuluokan kehys, joka on suunniteltu vakioimaan vuorovaikutukset AI-mallien ja asiakasohjelmien välillä. Tämä avoimen lähdekoodin opetussuunnitelma tarjoaa jäsennellyn oppimispolun, sisältäen käytännön koodiesimerkkejä ja todellisia käyttötapauksia suosituilla ohjelmointikielillä kuten C#, Java, JavaScript, TypeScript ja Python.

Oletpa sitten AI-kehittäjä, järjestelmäarkkitehti tai ohjelmistoinsinööri, tämä opas on kattava resurssi MCP:n perusteiden ja toteutusstrategioiden hallintaan.

## 🔗 Viralliset MCP-resurssit

- 📘 [MCP-dokumentaatio](https://modelcontextprotocol.io/) – Yksityiskohtaiset tutoriaalit ja käyttäjäoppaat  
- 📜 [MCP-spesifikaatio](https://spec.modelcontextprotocol.io/) – Protokollan arkkitehtuuri ja tekniset viitteet  
- 🧑‍💻 [MCP GitHub-repositorio](https://github.com/modelcontextprotocol) – Avoimen lähdekoodin SDK:t, työkalut ja koodiesimerkit  

## 🧭 MCP-opetussuunnitelman yleiskatsaus

<details>
  <summary><strong>00-03: Perusteet</strong></summary>

- **00. Johdanto MCP:hen**  
  Yleiskatsaus Model Context Protocoliin ja sen merkitykseen AI-putkistoissa. [Lue lisää](./00-Introduction/README.md)
- **01. Keskeiset käsitteet selitettynä**  
  Syvällinen tarkastelu MCP:n keskeisiin käsitteisiin. [Lue lisää](./01-CoreConcepts/README.md)
- **02. Turvallisuus MCP:ssä**  
  Turvauhat ja parhaat käytännöt. [Lue lisää](./02-Security/README.md)
- **03. MCP:n käyttöönotto**  
  Ympäristön asennus, peruspalvelimet/asiakkaat, integraatio. [Lue lisää](./03-GettingStarted/README.md)
</details>

<details>
  <summary><strong>03.x: Käytännön laboratoriot</strong></summary>

- **3.1. Ensimmäinen palvelin** – [Opas](./03-GettingStarted/01-first-server/README.md)
- **3.2. Ensimmäinen asiakas** – [Opas](./03-GettingStarted/02-client/README.md)
- **3.3. Asiakas LLM:llä** – [Opas](./03-GettingStarted/03-llm-client/README.md)
- **3.4. Palvelimen käyttäminen Visual Studio Codella** – [Opas](./03-GettingStarted/04-vscode/README.md)
- **3.5. Palvelimen luominen SSE:llä** – [Opas](./03-GettingStarted/05-sse-server/README.md)
- **3.6. HTTP-suoratoisto** – [Opas](./03-GettingStarted/06-http-streaming/README.md)
- **3.7. AI Toolkitin käyttö** – [Opas](./03-GettingStarted/07-aitk/README.md)
- **3.8. Palvelimen testaaminen** – [Opas](./03-GettingStarted/08-testing/README.md)
- **3.9. Palvelimen käyttöönotto** – [Opas](./03-GettingStarted/09-deployment/README.md)
</details>

<details>
  <summary><strong>04-05: Käytännön ja edistynyt</strong></summary>

- **04. Käytännön toteutus**  
  SDK:t, virheenkorjaus, testaus, uudelleenkäytettävät prompt-mallit. [Lue lisää](./04-PracticalImplementation/README.md)
- **05. Edistyneet MCP-aiheet**  
  Monimuotoinen AI, skaalaus, yrityskäyttö. [Lue lisää](./05-AdvancedTopics/README.md)
- **5.1. MCP-integraatio Azuren kanssa** – [Opas](./05-AdvancedTopics/mcp-integration/README.md)
- **5.2. Monimuotoisuus** – [Opas](./05-AdvancedTopics/mcp-multi-modality/README.md)
- **5.3. MCP OAuth2 -demo** – [Opas](./05-AdvancedTopics/mcp-oauth2-demo/README.md)
- **5.4. Juurikontekstit** – [Opas](./05-AdvancedTopics/mcp-root-contexts/README.md)
- **5.5. Reititys** – [Opas](./05-AdvancedTopics/mcp-routing/README.md)
- **5.6. Otanta** – [Opas](./05-AdvancedTopics/mcp-sampling/README.md)
- **5.7. Skaalaus** – [Opas](./05-AdvancedTopics/mcp-scaling/README.md)
- **5.8. Turvallisuus** – [Opas](./05-AdvancedTopics/mcp-security/README.md)
- **5.9. Web-haku MCP:llä** – [Opas](./05-AdvancedTopics/web-search-mcp/README.md)
- **5.10. Reaaliaikainen suoratoisto** – [Opas](./05-AdvancedTopics/mcp-realtimestreaming/README.md)
- **5.11. Reaaliaikainen web-haku** – [Opas](./05-AdvancedTopics/mcp-realtimesearch/README.md)
</details>

<details>
  <summary><strong>06-10: Yhteisö, parhaat käytännöt ja laboratoriot</strong></summary>

- **06. Yhteisön panokset** – [Opas](./06-CommunityContributions/README.md)
- **07. Varhaisen käyttöönoton opit** – [Opas](./07-LessonsFromEarlyAdoption/README.md)
- **08. MCP:n parhaat käytännöt** – [Opas](./08-BestPractices/README.md)
- **09. MCP tapaustutkimukset** – [Opas](./09-CaseStudy/README.md)
- **10. AI-työnkulkujen tehostaminen: MCP-palvelimen rakentaminen AI Toolkitillä** – [Käytännön harjoitus](./10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/README.md)
</details>

## Esimerkkiprojektit

### 🧮 MCP-laskin esimerkkiprojektit:
<details>
  <summary><strong>Tutustu koodiesimerkkeihin kielittäin</strong></summary>

  - [C# MCP-palvelin esimerkki](./03-GettingStarted/samples/csharp/README.md)
  - [Java MCP-laskin](./03-GettingStarted/samples/java/calculator/README.md)
  - [JavaScript MCP-demo](./03-GettingStarted/samples/javascript/README.md)
  - [Python MCP-palvelin](../../03-GettingStarted/samples/python/mcp_calculator_server.py)
  - [TypeScript MCP-esimerkki](./03-GettingStarted/samples/typescript/README.md)

</details>

### 💡 MCP kehittyneet laskinprojektit:
<details>
  <summary><strong>Tutustu kehittyneisiin esimerkkeihin</strong></summary>

  - [Kehittynyt C# esimerkki](./04-PracticalImplementation/samples/csharp/README.md)
  - [Java Container App esimerkki](./04-PracticalImplementation/samples/java/containerapp/README.md)
  - [JavaScript kehittynyt esimerkki](./04-PracticalImplementation/samples/javascript/README.md)
  - [Python monimutkainen toteutus](../../04-PracticalImplementation/samples/python/mcp_sample.py)
  - [TypeScript Container esimerkki](./04-PracticalImplementation/samples/typescript/README.md)

</details>


## 🎯 MCP:n oppimisen edellytykset

Jotta saat tästä opetussuunnitelmasta parhaan hyödyn, sinulla tulisi olla:

- Perustiedot C#:stä, Javasta tai Pythonista
- Ymmärrys asiakas-palvelin-mallista ja API:sta
- (Valinnainen) Tuntemus koneoppimisen peruskäsitteistä

## 📚 Opas opiskeluun

Laaja [Opas opiskeluun](./study_guide.md) auttaa sinua liikkumaan tässä repositoriossa tehokkaasti. Oppaassa on:

- Visuaalinen opetussuunnitelmakartta kaikista käsitellyistä aiheista
- Yksityiskohtainen erittely jokaisesta repositorion osasta
- Ohjeet esimerkkiprojektien käyttöön
- Suositellut oppimispolut eri taitotasoille
- Lisäresursseja oppimisen tueksi

## 🛠️ Kuinka käyttää tätä opetussuunnitelmaa tehokkaasti

Jokainen tämän oppaan oppitunti sisältää:

1. Selkeät selitykset MCP-konsepteista  
2. Live-koodiesimerkkejä useilla kielillä  
3. Harjoituksia oikeiden MCP-sovellusten rakentamiseen  
4. Lisäresursseja edistyneille oppijoille


## 🌟 Yhteisön kiitokset

Kiitos Microsoft Valued Professional [Shivam Goyalille](https://www.linkedin.com/in/shivam2003/) tärkeiden koodiesimerkkien jakamisesta.

## 📜 Lisenssitiedot

Tämä sisältö on lisensoitu **MIT-lisenssillä**. Ehdot löydät [LICENSE](../../LICENSE) tiedostosta.

## 🤝 Osallistumisohjeet

Tämä projekti ottaa mielellään vastaan panoksia ja ehdotuksia. Useimmat panokset edellyttävät, että hyväksyt
Contributor License Agreementin (CLA), jossa vahvistat, että sinulla on oikeus ja että myönnät meille
oikeudet käyttää panostasi. Lisätietoja löytyy osoitteesta <https://cla.opensource.microsoft.com>.

Kun lähetät pull requestin, CLA-botti automaattisesti tarkistaa, tarvitseeko sinun toimittaa CLA ja merkitsee PR:n asianmukaisesti (esim. statustarkistus, kommentti). Noudata vain botin antamia ohjeita. Tämä riittää tekemään vain kerran kaikissa CLA:a käyttävissä repozitorioissa.

Tämä projekti on ottanut käyttöön [Microsoft Open Source Code of Conductin](https://opensource.microsoft.com/codeofconduct/).
Lisätietoja löydät [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) sivulta tai ota yhteyttä osoitteeseen [opencode@microsoft.com](mailto:opencode@microsoft.com) mahdollisissa lisäkysymyksissä tai palautteessa.

## 🎒 Muut kurssit
Tiimimme tuottaa myös muita kursseja! Tutustu:

- [AI Agents For Beginners](https://github.com/microsoft/ai-agents-for-beginners?WT.mc_id=academic-105485-koreyst)
- [Generative AI for Beginners using .NET](https://github.com/microsoft/Generative-AI-for-beginners-dotnet?WT.mc_id=academic-105485-koreyst)
- [Generative AI for Beginners using JavaScript](https://github.com/microsoft/generative-ai-with-javascript?WT.mc_id=academic-105485-koreyst)
- [Generative AI for Beginners](https://github.com/microsoft/generative-ai-for-beginners?WT.mc_id=academic-105485-koreyst)
- [ML for Beginners](https://aka.ms/ml-beginners?WT.mc_id=academic-105485-koreyst)
- [Data Science for Beginners](https://aka.ms/datascience-beginners?WT.mc_id=academic-105485-koreyst)
- [AI for Beginners](https://aka.ms/ai-beginners?WT.mc_id=academic-105485-koreyst)
- [Cybersecurity for Beginners](https://github.com/microsoft/Security-101??WT.mc_id=academic-96948-sayoung)
- [Web Dev for Beginners](https://aka.ms/webdev-beginners?WT.mc_id=academic-105485-koreyst)
- [IoT for Beginners](https://aka.ms/iot-beginners?WT.mc_id=academic-105485-koreyst)
- [XR-kehitys aloittelijoille](https://github.com/microsoft/xr-development-for-beginners?WT.mc_id=academic-105485-koreyst)
- [GitHub Copilotin hallinta tekoälypariohjelmointiin](https://aka.ms/GitHubCopilotAI?WT.mc_id=academic-105485-koreyst)
- [GitHub Copilotin hallinta C#/.NET-kehittäjille](https://github.com/microsoft/mastering-github-copilot-for-dotnet-csharp-developers?WT.mc_id=academic-105485-koreyst)
- [Valitse oma Copilot-seikkailusi](https://github.com/microsoft/CopilotAdventures?WT.mc_id=academic-105485-koreyst)


## ™️ Tavaranmerkki-ilmoitus

Tässä projektissa saattaa olla tavaramerkkejä tai logoja projekteista, tuotteista tai palveluista. Microsoftin tavaramerkkien tai logojen luvallinen käyttö edellyttää ja noudattaa
[Microsoftin tavaramerkki- ja brändiohjeita](https://www.microsoft.com/legal/intellectualproperty/trademarks/usage/general).
Microsoftin tavaramerkkien tai logojen käyttö muokatuissa versioissa ei saa aiheuttaa sekaannusta tai antaa vaikutelmaa Microsoftin sponsoroimasta.
Kolmansien osapuolien tavaramerkkien tai logojen käyttö on näiden osapuolten sääntöjen mukaista.

**Vastuuvapauslauseke**:  
Tämä asiakirja on käännetty käyttämällä tekoälypohjaista käännöspalvelua [Co-op Translator](https://github.com/Azure/co-op-translator). Vaikka pyrimme tarkkuuteen, huomioithan, että automaattiset käännökset saattavat sisältää virheitä tai epätarkkuuksia. Alkuperäistä asiakirjaa sen alkuperäiskielellä tulee pitää virallisena lähteenä. Tärkeissä tiedoissa suositellaan ammattimaista ihmiskäännöstä. Emme ole vastuussa tämän käännöksen käytöstä aiheutuvista väärinymmärryksistä tai tulkinnoista.