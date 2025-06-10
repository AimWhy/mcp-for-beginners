<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "3ede7f051090bd4acfe5b068bab9f6b0",
  "translation_date": "2025-06-10T04:29:52+00:00",
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


Noudata näitä vaiheita aloittaaksesi näiden resurssien käytön:
1. **Forkkaa repositorio**: Klikkaa [![GitHub forks](https://img.shields.io/github/forks/microsoft/mcp-for-beginners.svg?style=social&label=Fork)](https://GitHub.com/microsoft/mcp-for-beginners/fork)
2. **Kloonaa repositorio**: `git clone https://github.com/microsoft/mcp-for-beginners.git`
3. [**Liity Azure AI Foundry Discordiin ja tapaa asiantuntijoita sekä muita kehittäjiä**](https://discord.com/invite/ByRwuEEgH4)


### 🌐 Monikielinen tuki

#### Tuettu GitHub Actionin kautta (automaattinen ja aina ajan tasalla)

# 🚀 Model Context Protocol (MCP) Aloittelijan Opetussuunnitelma

## **Opiskele MCP:tä käytännön koodiesimerkkien avulla C#:ssa, Javassa, JavaScriptissä, Pythonissa ja TypeScriptissä**

## 🧠 Yleiskatsaus Model Context Protocol -opetussuunnitelmaan

**Model Context Protocol (MCP)** on huipputason kehys, joka on suunniteltu vakioimaan vuorovaikutukset tekoälymallien ja asiakasohjelmien välillä. Tämä avoimen lähdekoodin opetussuunnitelma tarjoaa jäsennellyn oppimispolun, joka sisältää käytännön koodiesimerkkejä ja todellisia käyttötapauksia suosituissa ohjelmointikielissä kuten C#, Java, JavaScript, TypeScript ja Python.

Oletpa sitten tekoälykehittäjä, järjestelmäarkkitehti tai ohjelmistosuunnittelija, tämä opas on kattava resurssi MCP:n perusteiden ja toteutusstrategioiden hallintaan.

## 🔗 Viralliset MCP-resurssit

- 📘 [MCP-dokumentaatio](https://modelcontextprotocol.io/) – Yksityiskohtaiset opetusohjelmat ja käyttäjäoppaat  
- 📜 [MCP-spesifikaatio](https://spec.modelcontextprotocol.io/) – Protokollan arkkitehtuuri ja tekniset viitteet  
- 🧑‍💻 [MCP GitHub-repositorio](https://github.com/modelcontextprotocol) – Avoimen lähdekoodin SDK:t, työkalut ja koodiesimerkit  

## 🧭 Kokonaisvaltainen MCP-opetussuunnitelman rakenne

| Luku | Otsikko | Kuvaus | Linkki |
|--|--|--|--|
| 00 | **Johdatus MCP:hen** | Yleiskatsaus Model Context Protocoliin ja sen merkitykseen tekoälyputkistoissa, mukaan lukien mitä MCP on, miksi standardisointi on tärkeää sekä käytännön esimerkkejä ja hyötyjä | [Johdatus](./00-Introduction/README.md) |
| 01 | **Keskeiset käsitteet selitettynä** | Syvällinen katsaus MCP:n keskeisiin käsitteisiin, mukaan lukien asiakas-palvelin-arkkitehtuuri, protokollan tärkeimmät osat ja viestintämallit | [Keskeiset käsitteet](./01-CoreConcepts/README.md) |
| 02 | **Turvallisuus MCP:ssä** | Turvauhkien tunnistaminen MCP-pohjaisissa järjestelmissä, menetelmät ja parhaat käytännöt turvallisten toteutusten varmistamiseksi | [Turvallisuus](./02-Security/README.md) |
| 03 | **Aloittaminen MCP:n kanssa** | Ympäristön asennus ja konfigurointi, perus MCP-palvelinten ja -asiakkaiden luominen, MCP:n integrointi olemassa oleviin sovelluksiin | [Aloittaminen](./03-GettingStarted/README.md) |
| 3.1 | **Ensimmäinen palvelin** | Peruspalvelimen pystyttäminen MCP-protokollaa käyttäen, palvelin-asiakas-vuorovaikutuksen ymmärtäminen ja palvelimen testaaminen | [Ensimmäinen palvelin](./03-GettingStarted/01-first-server/README.md) |
| 3.2 | **Ensimmäinen asiakas** | Perusasiakkaan pystyttäminen MCP-protokollaa käyttäen, asiakas-palvelin-vuorovaikutuksen ymmärtäminen ja asiakkaan testaaminen | [Ensimmäinen asiakas](./03-GettingStarted/02-client/README.md) |
| 3.3 | **Asiakas LLM:llä** | Asiakkaan pystyttäminen MCP-protokollaa käyttäen yhdessä suuren kielimallin (LLM) kanssa | [Asiakas LLM:llä](./03-GettingStarted/03-llm-client/README.md) |
| 3.4 | **Palvelimen käyttö Visual Studio Codella** | Visual Studio Coden asetukset palvelinten käyttämiseen MCP-protokollan avulla | [Palvelimen käyttö Visual Studio Codella](./03-GettingStarted/04-vscode/README.md) |
| 3.5 | **Palvelimen luominen SSE:n avulla** | SSE:n avulla voimme altistaa palvelimen internetiin. Tässä osiossa opit luomaan palvelimen SSE:tä käyttäen | [Palvelimen luominen SSE:llä](./03-GettingStarted/05-sse-server/README.md) |
| 3.6 | **AI Toolkitin käyttö** | AI toolkit on erinomainen työkalu, joka auttaa hallitsemaan tekoäly- ja MCP-työnkulkuasi | [AI Toolkitin käyttö](./03-GettingStarted/06-aitk/README.md) |
| 3.7 | **Palvelimen testaaminen** | Testaus on tärkeä osa kehitysprosessia. Tässä osiossa opit käyttämään useita eri testausvälineitä | [Palvelimen testaaminen](./03-GettingStarted/07-testing/README.md) |
| 3.8 | **Palvelimen käyttöönotto** | Miten siirryt paikallisesta kehityksestä tuotantoon? Tämä osio auttaa sinua kehittämään ja ottamaan palvelimen käyttöön | [Palvelimen käyttöönotto](./03-GettingStarted/08-deployment/README.md) |
| 04 | **Käytännön toteutus** | SDK:iden käyttö eri kielillä, virheenkorjaus, testaus ja validointi, uudelleenkäytettävien prompt-mallien ja työnkulkujen luominen | [Käytännön toteutus](./04-PracticalImplementation/README.md) |
| 05 | **Edistyneet aiheet MCP:ssä** | Monimodaaliset tekoälytyönkulut ja laajennettavuus, turvalliset skaalausstrategiat, MCP yritysekosysteemeissä | [Edistyneet aiheet](./05-AdvancedTopics/README.md) |
| 5.1 | **MCP:n integrointi Azureen** | Näyttää integraation Azuren kanssa | [MCP Azure -integraatio](./05-AdvancedTopics/mcp-integration/README.md) |
| 5.2 | **Monimodaalisuus** | Näyttää, miten työskennellä eri modaliteettien, kuten kuvien, kanssa | [Monimodaalisuus](./05-AdvancedTopics/mcp-multi-modality/README.md) |
| 5.3 | **MCP OAuth2 Demo** | Minimipainoinen Spring Boot -sovellus, joka näyttää OAuth2:n käytön MCP:n kanssa sekä valtuutus- että resurssipalvelimena. Demonstroi turvallista tokenin myöntämistä, suojattuja päätepisteitä, Azure Container Apps -käyttöönottoa ja API Management -integraatiota | [MCP OAuth2 Demo](./05-AdvancedTopics/mcp-oauth2-demo/README.md) |
| 5.4 | **Root Contexts** | Lisätietoa root contextista ja sen toteuttamisesta | [Root Contexts](./05-AdvancedTopics/mcp-root-contexts/README.md) |
| 5.5 | **Reititys** | Opit eri reititystyypit | [Reititys](./05-AdvancedTopics/mcp-routing/README.md) |
| 5.6 | **Näytteiden ottaminen** | Opit, miten näytteitä otetaan | [Näytteiden ottaminen](./05-AdvancedTopics/mcp-sampling/README.md) |
| 5.7 | **Skaalaus** | Opit MCP-palvelinten skaalaamisesta, mukaan lukien horisontaalinen ja vertikaalinen skaalaus, resurssien optimointi ja suorituskyvyn hienosäätö | [Skaalaus](./05-AdvancedTopics/mcp-scaling/README.md) |
| 5.8 | **Turvallisuus** | Suojaa MCP-palvelimesi, mukaan lukien todennus, valtuutus ja tietosuoja | [Turvallisuus](./05-AdvancedTopics/mcp-security/README.md) |
| 5.9 | **Web Search MCP** | Python MCP -palvelin ja asiakas, jotka integroivat SerpAPI:n reaaliaikaiseen verkko-, uutis-, tuotehakuun ja Q&A-toimintoihin. Demonstroi monityökalujen orkestrointia, ulkoisten API:en integraatiota ja vankkaa virheenkäsittelyä | [Web Search MCP](./05-AdvancedTopics/web-search-mcp/README.md) |
| 06 | **Yhteisön panokset** | Kuinka osallistua koodiin ja dokumentaatioon, yhteistyö GitHubin kautta, yhteisön vetämät parannukset ja palaute | [Yhteisön panokset](./06-CommunityContributions/README.md) |
| 07 | **Oppeja varhaisesta käyttöönotosta** | Todelliset käyttöönotot ja mikä toimi, MCP-pohjaisten ratkaisujen rakentaminen ja käyttöönotto, trendit ja tulevaisuuden tiekartta | [Oppeja](./07-LessonsFromEarlyAdoption/README.md) |
| 08 | **Parhaat käytännöt MCP:lle** | Suorituskyvyn hienosäätö ja optimointi, vikasietoisien MCP-järjestelmien suunnittelu, testaus- ja resilienssistrategiat | [Parhaat käytännöt](./08-BestPractices/README.md) |
| 09 | **MCP-tapaukset** | Syvälliset tarkastelut MCP-ratkaisuarkkitehtuureista, käyttöönotto-ohjeista ja integraatiovinkeistä, selitetyt kaaviot ja projektikierrokset | [Tapaukset](./09-CaseStudy/README.md) |
| 10 | **AI-työnkulkujen tehostaminen: MCP-palvelimen rakentaminen AI Toolkitin avulla** | Kattava käytännön työpaja, joka yhdistää MCP:n ja Microsoftin AI Toolkitin VS Codeen. Opit rakentamaan älykkäitä sovelluksia, jotka yhdistävät AI-mallit todellisiin työkaluihin käytännön moduulien avulla, kattaen perusteet, räätälöidyn palvelinkehityksen ja tuotantoon vientistrategiat. | [Hands On Lab](./10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/README.md) |

## Esimerkkiprojektit

### 🧮 MCP-laskin esimerkkiprojektit:
<details>
  <summary><strong>Tutustu koodiesimerkkeihin kielittäin</strong></summary>

  - [C# MCP Server Example](./03-GettingStarted/samples/csharp/README.md)
  - [Java MCP Calculator](./03-GettingStarted/samples/java/calculator/README.md)
  - [JavaScript MCP Demo](./03-GettingStarted/samples/javascript/README.md)
  - [Python MCP Server](../../03-GettingStarted/samples/python/mcp_calculator_server.py)
  - [TypeScript MCP Example](./03-GettingStarted/samples/typescript/README.md)

</details>

### 💡 MCP-edistyneet laskinprojektit:
<details>
  <summary><strong>Tutustu edistyneisiin esimerkkeihin</strong></summary>

  - [Advanced C# Sample](./04-PracticalImplementation/samples/csharp/README.md)
  - [Java Container App Example](./04-PracticalImplementation/samples/java/containerapp/README.md)
  - [JavaScript Advanced Sample](./04-PracticalImplementation/samples/javascript/README.md)
  - [Python Complex Implementation](../../04-PracticalImplementation/samples/python/mcp_sample.py)
  - [TypeScript Container Sample](./04-PracticalImplementation/samples/typescript/README.md)

</details>


## 🎯 MCP:n oppimisen ennakkoedellytykset

Jotta saat tästä opetussuunnitelmasta parhaan hyödyn, sinulla tulisi olla:

- Perustiedot C#:stä, Javasta tai Pythonista  
- Ymmärrys asiakas-palvelin-mallista ja API:sta  
- (Valinnainen) Tuntemus koneoppimisen perusteista  

## 🛠️ Kuinka käyttää tätä opetussuunnitelmaa tehokkaasti

Jokainen tämän oppaan oppitunti sisältää:

1. Selkeät selitykset MCP:n peruskäsitteistä  
2. Live-koodiesimerkkejä useilla kielillä  
3. Harjoituksia oikeiden MCP-sovellusten rakentamiseen  
4. Lisäresursseja edistyneille oppijoille  

## 📜 Lisenssitiedot

Tämä sisältö on lisensoitu **MIT License** -lisenssillä. Käyttöehdot löytyvät tiedostosta [LICENSE](../../LICENSE).

## 🤝 Osallistumisohjeet

Tämä projekti toivottaa tervetulleiksi panokset ja ehdotukset. Useimmat panokset edellyttävät, että hyväksyt Contributor License Agreementin (CLA), jossa vakuutat, että sinulla on oikeus ja että myönnät meille oikeudet käyttää panostasi. Lisätietoja löytyy osoitteesta <https://cla.opensource.microsoft.com>.

Kun lähetät pull requestin, CLA-botti määrittää automaattisesti, tarvitsetko CLA:n ja merkitsee PR:n asianmukaisesti (esim. tilantarkistus, kommentti). Noudata vain botin antamia ohjeita. Tämä pitää tehdä vain kerran kaikissa CLA:ta käyttävissä repositorioissa.

Tämä projekti on ottanut käyttöön [Microsoft Open Source Code of Conductin](https://opensource.microsoft.com/codeofconduct/). Lisätietoja löytyy [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) -sivulta tai ota yhteyttä osoitteeseen [opencode@microsoft.com](mailto:opencode@microsoft.com) mahdollisissa lisäkysymyksissä tai palautteessa.

## 🎒 Muut kurssit
Tiimimme tarjoaa myös muita kursseja! Tutustu:

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
- [XR Development for Beginners](https://github.com/microsoft/xr-development-for-beginners?WT.mc_id=academic-105485-koreyst)
- [Mastering GitHub Copilot for AI Paired Programming](https://aka.ms/GitHubCopilotAI?WT.mc_id=academic-105485-koreyst)
- [Mastering GitHub Copilot for C#/.NET Developers](https://github.com/microsoft/mastering-github-copilot-for-dotnet-csharp-developers?WT.mc_id=academic-105485-koreyst)
- [Choose Your Own Copilot Adventure](https://github.com/microsoft/CopilotAdventures?WT.mc_id=academic-105485-koreyst)


## ™️ Tavaramerkki-ilmoitus

Tämä projekti saattaa sisältää tavaramerkkejä tai logoja projekteista, tuotteista tai palveluista. Microsoftin tavaramerkkien tai logojen luvallinen käyttö on ehdollista ja sen tulee noudattaa [Microsoftin tavaramerkki- ja brändiohjeita](https://www.microsoft.com/legal/intellectualproperty/trademarks/usage/general). Microsoftin tavaramerkkien tai logojen käyttö muokatuissa versioissa ei saa aiheuttaa sekaannusta tai antaa vaikutelmaa Microsoftin sponsoroimasta. Kolmansien osapuolien tavaramerkkien tai logojen käyttö on näiden osapuolien sääntöjen alaista.

**Vastuuvapauslauseke**:  
Tämä asiakirja on käännetty käyttämällä tekoälypohjaista käännöspalvelua [Co-op Translator](https://github.com/Azure/co-op-translator). Vaikka pyrimme tarkkuuteen, huomioithan, että automaattikäännöksissä saattaa esiintyä virheitä tai epätarkkuuksia. Alkuperäistä asiakirjaa sen alkuperäiskielellä tulisi pitää ensisijaisena ja luotettavana lähteenä. Tärkeissä tiedoissa suositellaan ammattimaisen ihmiskääntäjän käyttöä. Emme ole vastuussa mahdollisista väärinymmärryksistä tai virhetulkinnoista, jotka johtuvat tämän käännöksen käytöstä.