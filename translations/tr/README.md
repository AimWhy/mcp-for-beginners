<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "af49e2a6fd462dde6f9ad952d5c8cc6e",
  "translation_date": "2025-06-21T13:50:29+00:00",
  "source_file": "README.md",
  "language_code": "tr"
}
-->
![MCP-for-beginners](../../translated_images/mcp-beginners.2ce2b317996369ff66c5b72e25eff9d4288ab2741fc70c0b4e523d1ae1e249fd.tr.png) 

[![GitHub contributors](https://img.shields.io/github/contributors/microsoft/mcp-for-beginners.svg)](https://GitHub.com/microsoft/mcp-for-beginners/graphs/contributors)
[![GitHub issues](https://img.shields.io/github/issues/microsoft/mcp-for-beginners.svg)](https://GitHub.com/microsoft/mcp-for-beginners/issues)
[![GitHub pull-requests](https://img.shields.io/github/issues-pr/microsoft/mcp-for-beginners.svg)](https://GitHub.com/microsoft/mcp-for-beginners/pulls)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com)

[![GitHub watchers](https://img.shields.io/github/watchers/microsoft/mcp-for-beginners.svg?style=social&label=Watch)](https://GitHub.com/microsoft/mcp-for-beginners/watchers)
[![GitHub forks](https://img.shields.io/github/forks/microsoft/mcp-for-beginners.svg?style=social&label=Fork)](https://GitHub.com/microsoft/mcp-for-beginners/fork)
[![GitHub stars](https://img.shields.io/github/stars/microsoft/mcp-for-beginners?style=social&label=Star)](https://GitHub.com/microsoft/mcp-for-beginners/stargazers)


[![Microsoft Azure AI Foundry Discord](https://dcbadge.vercel.app/api/server/ByRwuEEgH4)](https://discord.com/invite/ByRwuEEgH4)


Bu kaynakları kullanmaya başlamak için şu adımları izleyin:
1. **Depoyu Forklayın**: Tıklayın [![GitHub forks](https://img.shields.io/github/forks/microsoft/mcp-for-beginners.svg?style=social&label=Fork)](https://GitHub.com/microsoft/mcp-for-beginners/fork)
2. **Depoyu Klonlayın**:   `git clone https://github.com/microsoft/mcp-for-beginners.git`
3. [**Azure AI Foundry Discord’a Katılın ve uzmanlar ile diğer geliştiricilerle tanışın**](https://discord.com/invite/ByRwuEEgH4)


### 🌐 Çoklu Dil Desteği

#### GitHub Action ile desteklenmektedir (Otomatik ve Her Zaman Güncel)

# 🚀 Başlangıç Seviyesi için Model Context Protocol (MCP) Müfredatı

## **C#, Java, JavaScript, Python ve TypeScript ile Pratik Kod Örnekleriyle MCP Öğrenin**

## 🧠 Model Context Protocol Müfredatı Genel Bakış

**Model Context Protocol (MCP)**, yapay zeka modelleri ile istemci uygulamaları arasındaki etkileşimleri standartlaştırmak için geliştirilmiş ileri seviye bir çerçevedir. Bu açık kaynaklı müfredat, C#, Java, JavaScript, TypeScript ve Python gibi popüler programlama dillerinde pratik kod örnekleri ve gerçek dünya kullanım senaryoları içeren yapılandırılmış bir öğrenme yolu sunar.

İster bir yapay zeka geliştiricisi, sistem mimarı ya da yazılım mühendisi olun, bu rehber MCP temellerini ve uygulama stratejilerini ustalıkla öğrenmeniz için kapsamlı bir kaynaktır.

## 🔗 Resmi MCP Kaynakları

- 📘 [MCP Dokümantasyonu](https://modelcontextprotocol.io/) – Detaylı eğitimler ve kullanıcı kılavuzları  
- 📜 [MCP Spesifikasyonu](https://spec.modelcontextprotocol.io/) – Protokol mimarisi ve teknik referanslar  
- 🧑‍💻 [MCP GitHub Deposu](https://github.com/modelcontextprotocol) – Açık kaynak SDK’lar, araçlar ve kod örnekleri  

## 🧭 MCP Müfredatı Genel Bakış

<details>
  <summary><strong>00-03: Temeller</strong></summary>

- **00. MCP’ye Giriş**  
  Model Context Protocol’un genel tanıtımı ve yapay zeka süreçlerindeki önemi. [Devamını oku](./00-Introduction/README.md)
- **01. Temel Kavramların Açıklaması**  
  MCP’nin temel kavramlarının detaylı incelenmesi. [Devamını oku](./01-CoreConcepts/README.md)
- **02. MCP’de Güvenlik**  
  Güvenlik tehditleri ve en iyi uygulamalar. [Devamını oku](./02-Security/README.md)
- **03. MCP ile Başlarken**  
  Ortam kurulumu, temel sunucu/istemci yapıları, entegrasyon. [Devamını oku](./03-GettingStarted/README.md)
</details>

<details>
  <summary><strong>03.x: Uygulamalı Laboratuvarlar</strong></summary>

- **3.1. İlk sunucu** – [Kılavuz](./03-GettingStarted/01-first-server/README.md)
- **3.2. İlk istemci** – [Kılavuz](./03-GettingStarted/02-client/README.md)
- **3.3. LLM ile istemci** – [Kılavuz](./03-GettingStarted/03-llm-client/README.md)
- **3.4. Visual Studio Code ile sunucu kullanımı** – [Kılavuz](./03-GettingStarted/04-vscode/README.md)
- **3.5. SSE kullanarak sunucu oluşturma** – [Kılavuz](./03-GettingStarted/05-sse-server/README.md)
- **3.6. HTTP Akışı** – [Kılavuz](./03-GettingStarted/06-http-streaming/README.md)
- **3.7. AI Toolkit kullanımı** – [Kılavuz](./03-GettingStarted/07-aitk/README.md)
- **3.8. Sunucunuzu test etme** – [Kılavuz](./03-GettingStarted/08-testing/README.md)
- **3.9. Sunucunuzu dağıtma** – [Kılavuz](./03-GettingStarted/09-deployment/README.md)
</details>

<details>
  <summary><strong>04-05: Pratik ve İleri Seviye</strong></summary>

- **04. Pratik Uygulama**  
  SDK’lar, hata ayıklama, test etme, tekrar kullanılabilir prompt şablonları. [Devamını oku](./04-PracticalImplementation/README.md)
- **05. MCP’de İleri Konular**  
  Çok modlu yapay zeka, ölçeklendirme, kurumsal kullanım. [Devamını oku](./05-AdvancedTopics/README.md)
- **5.1. Azure ile MCP Entegrasyonu** – [Kılavuz](./05-AdvancedTopics/mcp-integration/README.md)
- **5.2. Çok modluluk** – [Kılavuz](./05-AdvancedTopics/mcp-multi-modality/README.md)
- **5.3. MCP OAuth2 Demo** – [Kılavuz](./05-AdvancedTopics/mcp-oauth2-demo/README.md)
- **5.4. Root Contexts** – [Kılavuz](./05-AdvancedTopics/mcp-root-contexts/README.md)
- **5.5. Yönlendirme** – [Kılavuz](./05-AdvancedTopics/mcp-routing/README.md)
- **5.6. Örnekleme** – [Kılavuz](./05-AdvancedTopics/mcp-sampling/README.md)
- **5.7. Ölçeklendirme** – [Kılavuz](./05-AdvancedTopics/mcp-scaling/README.md)
- **5.8. Güvenlik** – [Kılavuz](./05-AdvancedTopics/mcp-security/README.md)
- **5.9. Web Arama MCP** – [Kılavuz](./05-AdvancedTopics/web-search-mcp/README.md)
- **5.10. Gerçek Zamanlı Akış** – [Kılavuz](./05-AdvancedTopics/mcp-realtimestreaming/README.md)
- **5.11. Gerçek Zamanlı Web Arama** – [Kılavuz](./05-AdvancedTopics/mcp-realtimesearch/README.md)
</details>

<details>
  <summary><strong>06-10: Topluluk, En İyi Uygulamalar ve Laboratuvarlar</strong></summary>

- **06. Topluluk Katkıları** – [Kılavuz](./06-CommunityContributions/README.md)
- **07. Erken Benimsemeden Alınan Dersler** – [Kılavuz](./07-LessonsFromEarlyAdoption/README.md)
- **08. MCP İçin En İyi Uygulamalar** – [Kılavuz](./08-BestPractices/README.md)
- **09. MCP Vaka Çalışmaları** – [Kılavuz](./09-CaseStudy/README.md)
- **10. Yapay Zeka İş Akışlarını Kolaylaştırma: AI Toolkit ile MCP Sunucusu Oluşturma** – [Uygulamalı Laboratuvar](./10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/README.md)
</details>

## Örnek Projeler

### 🧮 MCP Hesaplayıcı Örnek Projeleri:
<details>
  <summary><strong>Dil Bazında Kod Uygulamalarını Keşfedin</strong></summary>

  - [C# MCP Sunucu Örneği](./03-GettingStarted/samples/csharp/README.md)
  - [Java MCP Hesaplayıcı](./03-GettingStarted/samples/java/calculator/README.md)
  - [JavaScript MCP Demo](./03-GettingStarted/samples/javascript/README.md)
  - [Python MCP Sunucu](../../03-GettingStarted/samples/python/mcp_calculator_server.py)
  - [TypeScript MCP Örneği](./03-GettingStarted/samples/typescript/README.md)

</details>

### 💡 MCP Gelişmiş Hesaplayıcı Projeleri:
<details>
  <summary><strong>Gelişmiş Örnekleri Keşfedin</strong></summary>

  - [Gelişmiş C# Örneği](./04-PracticalImplementation/samples/csharp/README.md)
  - [Java Konteyner Uygulama Örneği](./04-PracticalImplementation/samples/java/containerapp/README.md)
  - [JavaScript Gelişmiş Örnek](./04-PracticalImplementation/samples/javascript/README.md)
  - [Python Karmaşık Uygulama](../../04-PracticalImplementation/samples/python/mcp_sample.py)
  - [TypeScript Konteyner Örneği](./04-PracticalImplementation/samples/typescript/README.md)

</details>

## 🎯 MCP Öğrenimi İçin Ön Koşullar

Bu müfredattan en iyi şekilde faydalanmak için:

- C#, Java veya Python hakkında temel bilgi sahibi olmalısınız  
- İstemci-sunucu modeli ve API’leri anlamalısınız  
- (İsteğe bağlı) Makine öğrenimi kavramlarına aşina olmanız faydalı olur  

## 📚 Çalışma Rehberi

Bu depoyu etkili şekilde kullanmanız için kapsamlı bir [Çalışma Rehberi](./study_guide.md) mevcut. Rehberde şunlar yer alır:

- Tüm konuları gösteren görsel müfredat haritası  
- Her depo bölümünün detaylı açıklaması  
- Örnek projelerin nasıl kullanılacağına dair yönlendirmeler  
- Farklı beceri seviyeleri için önerilen öğrenme yolları  
- Öğrenme sürecinizi destekleyecek ek kaynaklar  

## 🛠️ Bu Müfredatı Etkili Kullanma Yöntemleri

Her derste şunlar bulunur:

1. MCP kavramlarının net açıklamaları  
2. Birden fazla dilde canlı kod örnekleri  
3. Gerçek MCP uygulamaları geliştirmek için alıştırmalar  
4. İleri seviye öğrenenler için ek kaynaklar  

## 📜 Lisans Bilgisi

Bu içerik **MIT Lisansı** altında lisanslanmıştır. Şartlar için [LICENSE](../../LICENSE) dosyasına bakınız.

## 🤝 Katkı Rehberi

Bu proje katkı ve önerilere açıktır. Çoğu katkı için, katkınızın kullanım hakkını bize verdiğinizi beyan eden bir Contributor License Agreement (CLA) kabul etmeniz gerekir. Detaylar için <https://cla.opensource.microsoft.com> adresini ziyaret edin.

Bir pull request gönderdiğinizde, CLA botu otomatik olarak CLA gerekip gerekmediğini belirler ve PR’ı uygun şekilde işaretler (örneğin, durum kontrolü, yorum). Botun verdiği talimatları takip etmeniz yeterlidir. CLA işlemini, CLA kullanan tüm depolar için sadece bir kez yapmanız gerekir.

Bu proje [Microsoft Açık Kaynak Davranış Kuralları](https://opensource.microsoft.com/codeofconduct/)’nu benimsemiştir. Daha fazla bilgi için [Davranış Kuralları SSS](https://opensource.microsoft.com/codeofconduct/faq/) sayfasına bakabilir veya sorularınız için [opencode@microsoft.com](mailto:opencode@microsoft.com) adresine yazabilirsiniz.

## 🎒 Diğer Kurslar  
Ekibimiz başka kurslar da sunmaktadır! Göz atın:

- [Yeni Başlayanlar İçin AI Ajanları](https://github.com/microsoft/ai-agents-for-beginners?WT.mc_id=academic-105485-koreyst)  
- [.NET Kullanarak Yeni Başlayanlar İçin Üretken AI](https://github.com/microsoft/Generative-AI-for-beginners-dotnet?WT.mc_id=academic-105485-koreyst)  
- [JavaScript Kullanarak Yeni Başlayanlar İçin Üretken AI](https://github.com/microsoft/generative-ai-with-javascript?WT.mc_id=academic-105485-koreyst)  
- [Yeni Başlayanlar İçin Üretken AI](https://github.com/microsoft/generative-ai-for-beginners?WT.mc_id=academic-105485-koreyst)  
- [Yeni Başlayanlar İçin ML](https://aka.ms/ml-beginners?WT.mc_id=academic-105485-koreyst)  
- [Yeni Başlayanlar İçin Veri Bilimi](https://aka.ms/datascience-beginners?WT.mc_id=academic-105485-koreyst)  
- [Yeni Başlayanlar İçin AI](https://aka.ms/ai-beginners?WT.mc_id=academic-105485-koreyst)  
- [Yeni Başlayanlar İçin Siber Güvenlik](https://github.com/microsoft/Security-101??WT.mc_id=academic-96948-sayoung)  
- [Yeni Başlayanlar İçin Web Geliştirme](https://aka.ms/webdev-beginners?WT.mc_id=academic-105485-koreyst)  
- [Yeni Başlayanlar İçin IoT](https://aka.ms/iot-beginners?WT.mc_id=academic-105485-koreyst)  
- [Yeni Başlayanlar İçin XR Geliştirme](https://github.com/microsoft/xr-development-for-beginners?WT.mc_id=academic-105485-koreyst)
- [Yapay Zeka Eşli Programlama için GitHub Copilot'u Ustalaştırmak](https://aka.ms/GitHubCopilotAI?WT.mc_id=academic-105485-koreyst)
- [C#/.NET Geliştiricileri için GitHub Copilot'u Ustalaştırmak](https://github.com/microsoft/mastering-github-copilot-for-dotnet-csharp-developers?WT.mc_id=academic-105485-koreyst)
- [Kendi Copilot Maceranı Seç](https://github.com/microsoft/CopilotAdventures?WT.mc_id=academic-105485-koreyst)


## ™️ Marka Bildirimi

Bu proje, projeler, ürünler veya hizmetler için ticari markalar veya logolar içerebilir. Microsoft ticari markalarının veya logolarının yetkili kullanımı, [Microsoft'un Ticari Marka ve Marka Kılavuzları](https://www.microsoft.com/legal/intellectualproperty/trademarks/usage/general) doğrultusunda olmalı ve bu kurallara uyulmalıdır. Microsoft ticari markalarının veya logolarının bu projenin değiştirilmiş sürümlerinde kullanımı, karışıklığa yol açmamalı veya Microsoft sponsorluğunu ima etmemelidir. Üçüncü taraf ticari markalarının veya logolarının kullanımı ise ilgili üçüncü tarafların politikalarına tabidir.

**Feragatname**:  
Bu belge, AI çeviri hizmeti [Co-op Translator](https://github.com/Azure/co-op-translator) kullanılarak çevrilmiştir. Doğruluk için çaba göstersek de, otomatik çevirilerin hatalar veya yanlışlıklar içerebileceğini lütfen unutmayınız. Orijinal belge, kendi dilinde yetkili kaynak olarak kabul edilmelidir. Kritik bilgiler için profesyonel insan çevirisi önerilir. Bu çevirinin kullanımı sonucu oluşabilecek yanlış anlamalar veya yorum hatalarından sorumlu değiliz.