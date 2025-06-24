<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "bc76969a3bb20c032d1d5e95a304a2e3",
  "translation_date": "2025-06-24T16:26:54+00:00",
  "source_file": "README.md",
  "language_code": "ko"
}
-->
![MCP-for-beginners](../../translated_images/mcp-beginners.2ce2b317996369ff66c5b72e25eff9d4288ab2741fc70c0b4e523d1ae1e249fd.ko.png) 

[![GitHub contributors](https://img.shields.io/github/contributors/microsoft/mcp-for-beginners.svg)](https://GitHub.com/microsoft/mcp-for-beginners/graphs/contributors)
[![GitHub issues](https://img.shields.io/github/issues/microsoft/mcp-for-beginners.svg)](https://GitHub.com/microsoft/mcp-for-beginners/issues)
[![GitHub pull-requests](https://img.shields.io/github/issues-pr/microsoft/mcp-for-beginners.svg)](https://GitHub.com/microsoft/mcp-for-beginners/pulls)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com)

[![GitHub watchers](https://img.shields.io/github/watchers/microsoft/mcp-for-beginners.svg?style=social&label=Watch)](https://GitHub.com/microsoft/mcp-for-beginners/watchers)
[![GitHub forks](https://img.shields.io/github/forks/microsoft/mcp-for-beginners.svg?style=social&label=Fork)](https://GitHub.com/microsoft/mcp-for-beginners/fork)
[![GitHub stars](https://img.shields.io/github/stars/microsoft/mcp-for-beginners?style=social&label=Star)](https://GitHub.com/microsoft/mcp-for-beginners/stargazers)


[![Microsoft Azure AI Foundry Discord](https://dcbadge.vercel.app/api/server/ByRwuEEgH4)](https://discord.com/invite/ByRwuEEgH4)


이 리소스를 사용하기 위해 다음 단계를 따라주세요:
1. **저장소 포크하기**: 클릭 [![GitHub forks](https://img.shields.io/github/forks/microsoft/mcp-for-beginners.svg?style=social&label=Fork)](https://GitHub.com/microsoft/mcp-for-beginners/fork)
2. **저장소 클론하기**: `git clone https://github.com/microsoft/mcp-for-beginners.git`
3. [**Azure AI Foundry Discord에 참여하여 전문가 및 다른 개발자들과 만나기**](https://discord.com/invite/ByRwuEEgH4)


### 🌐 다국어 지원

#### GitHub Action을 통해 지원 (자동화 및 항상 최신 상태 유지)

# 🚀 초보자를 위한 Model Context Protocol (MCP) 커리큘럼

## **C#, Java, JavaScript, Python, TypeScript로 배우는 MCP 실습 코드 예제**

## 🧠 Model Context Protocol 커리큘럼 개요

**Model Context Protocol (MCP)**는 AI 모델과 클라이언트 애플리케이션 간 상호작용을 표준화하기 위해 설계된 최첨단 프레임워크입니다. 이 오픈소스 커리큘럼은 C#, Java, JavaScript, TypeScript, Python 등 인기 프로그래밍 언어를 아우르며 실용적인 코드 예제와 실제 사례를 포함한 체계적인 학습 경로를 제공합니다.

AI 개발자, 시스템 아키텍트, 소프트웨어 엔지니어 누구든 MCP의 기본 원리와 구현 전략을 완벽하게 익힐 수 있는 종합 가이드입니다.

## 🔗 공식 MCP 자료

- 📘 [MCP Documentation](https://modelcontextprotocol.io/) – 자세한 튜토리얼과 사용자 가이드  
- 📜 [MCP Specification](https://spec.modelcontextprotocol.io/) – 프로토콜 구조 및 기술 참고자료  
- 🧑‍💻 [MCP GitHub Repository](https://github.com/modelcontextprotocol) – 오픈소스 SDK, 도구, 코드 샘플  

## 🧭 MCP 커리큘럼 개요

<details>
  <summary><strong>00-03: 기초</strong></summary>

- **00. MCP 소개**  
  Model Context Protocol과 AI 파이프라인에서의 중요성 개요. [자세히 보기](./00-Introduction/README.md)
- **01. 핵심 개념 설명**  
  MCP 핵심 개념 심층 탐구. [자세히 보기](./01-CoreConcepts/README.md)
- **02. MCP 보안**  
  보안 위협과 모범 사례. [자세히 보기](./02-Security/README.md)
- **03. MCP 시작하기**  
  환경 설정, 기본 서버/클라이언트, 통합 방법. [자세히 보기](./03-GettingStarted/README.md)
</details>

<details>
  <summary><strong>03.x: 실습 랩</strong></summary>

- **3.1. 첫 번째 서버** – [가이드](./03-GettingStarted/01-first-server/README.md)
- **3.2. 첫 번째 클라이언트** – [가이드](./03-GettingStarted/02-client/README.md)
- **3.3. LLM을 사용하는 클라이언트** – [가이드](./03-GettingStarted/03-llm-client/README.md)
- **3.4. Visual Studio Code로 서버 사용하기** – [가이드](./03-GettingStarted/04-vscode/README.md)
- **3.5. SSE를 이용한 서버 생성** – [가이드](./03-GettingStarted/05-sse-server/README.md)
- **3.6. HTTP 스트리밍** – [가이드](./03-GettingStarted/06-http-streaming/README.md)
- **3.7. AI 툴킷 사용하기** – [가이드](./03-GettingStarted/07-aitk/README.md)
- **3.8. 서버 테스트하기** – [가이드](./03-GettingStarted/08-testing/README.md)
- **3.9. 서버 배포하기** – [가이드](./03-GettingStarted/09-deployment/README.md)
</details>

<details>
  <summary><strong>04-05: 실전 및 고급</strong></summary>

- **04. 실전 구현**  
  SDK, 디버깅, 테스트, 재사용 가능한 프롬프트 템플릿. [자세히 보기](./04-PracticalImplementation/README.md)
- **05. MCP 고급 주제**  
  멀티모달 AI, 확장성, 엔터프라이즈 활용. [자세히 보기](./05-AdvancedTopics/README.md)
- **5.1. Azure와 MCP 통합** – [가이드](./05-AdvancedTopics/mcp-integration/README.md)
- **5.2. 멀티 모달리티** – [가이드](./05-AdvancedTopics/mcp-multi-modality/README.md)
- **5.3. MCP OAuth2 데모** – [가이드](./05-AdvancedTopics/mcp-oauth2-demo/README.md)
- **5.4. 루트 컨텍스트** – [가이드](./05-AdvancedTopics/mcp-root-contexts/README.md)
- **5.5. 라우팅** – [가이드](./05-AdvancedTopics/mcp-routing/README.md)
- **5.6. 샘플링** – [가이드](./05-AdvancedTopics/mcp-sampling/README.md)
- **5.7. 확장성** – [가이드](./05-AdvancedTopics/mcp-scaling/README.md)
- **5.8. 보안** – [가이드](./05-AdvancedTopics/mcp-security/README.md)
- **5.9. 웹 검색 MCP** – [가이드](./05-AdvancedTopics/web-search-mcp/README.md)
- **5.10. 실시간 스트리밍** – [가이드](./05-AdvancedTopics/mcp-realtimestreaming/README.md)
- **5.11. 실시간 웹 검색** – [가이드](./05-AdvancedTopics/mcp-realtimesearch/README.md)
</details>

<details>
  <summary><strong>06-10: 커뮤니티, 모범 사례 & 랩</strong></summary>

- **06. 커뮤니티 기여** – [가이드](./06-CommunityContributions/README.md)
- **07. 초기 도입에서 얻은 인사이트** – [가이드](./07-LessonsFromEarlyAdoption/README.md)
- **08. MCP 모범 사례** – [가이드](./08-BestPractices/README.md)
- **09. MCP 사례 연구** – [가이드](./09-CaseStudy/README.md)
- **10. AI 워크플로우 간소화: AI Toolkit으로 MCP 서버 구축하기** – [핸즈온 랩](./10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/README.md)
</details>

## 샘플 프로젝트

### 🧮 MCP 계산기 샘플 프로젝트:
<details>
  <summary><strong>언어별 코드 구현 살펴보기</strong></summary>

  - [C# MCP 서버 예제](./03-GettingStarted/samples/csharp/README.md)
  - [Java MCP 계산기](./03-GettingStarted/samples/java/calculator/README.md)
  - [JavaScript MCP 데모](./03-GettingStarted/samples/javascript/README.md)
  - [Python MCP 서버](../../03-GettingStarted/samples/python/mcp_calculator_server.py)
  - [TypeScript MCP 예제](./03-GettingStarted/samples/typescript/README.md)

</details>

### 💡 MCP 고급 계산기 프로젝트:
<details>
  <summary><strong>고급 샘플 살펴보기</strong></summary>

  - [고급 C# 샘플](./04-PracticalImplementation/samples/csharp/README.md)
  - [Java 컨테이너 앱 예제](./04-PracticalImplementation/samples/java/containerapp/README.md)
  - [JavaScript 고급 샘플](./04-PracticalImplementation/samples/javascript/README.md)
  - [Python 복잡한 구현](../../04-PracticalImplementation/samples/python/mcp_sample.py)
  - [TypeScript 컨테이너 샘플](./04-PracticalImplementation/samples/typescript/README.md)

</details>


## 🎯 MCP 학습을 위한 사전 조건

이 커리큘럼을 최대한 활용하려면 다음이 필요합니다:

- C#, Java 또는 Python에 대한 기본 지식
- 클라이언트-서버 모델과 API에 대한 이해
- (선택 사항) 머신러닝 개념에 대한 친숙함

## 📚 학습 가이드

효과적으로 리포지토리를 탐색할 수 있도록 종합적인 [학습 가이드](./study_guide.md)가 제공됩니다. 가이드에는 다음이 포함되어 있습니다:

- 다루는 모든 주제를 시각적으로 보여주는 커리큘럼 맵
- 각 리포지토리 섹션에 대한 상세한 분류
- 샘플 프로젝트 활용 방법 안내
- 다양한 숙련도에 맞는 추천 학습 경로
- 학습 여정을 보완할 추가 자료

## 🛠️ 이 커리큘럼을 효과적으로 활용하는 방법

각 레슨에는 다음이 포함됩니다:

1. MCP 개념에 대한 명확한 설명  
2. 여러 언어로 된 실시간 코드 예제  
3. 실제 MCP 애플리케이션 개발을 위한 연습 문제  
4. 고급 학습자를 위한 추가 자료


## 🌟 커뮤니티 감사 인사

중요한 코드 샘플을 기여해 주신 Microsoft Valued Professional [Shivam Goyal](https://www.linkedin.com/in/shivam2003/)님께 감사드립니다.

## 📜 라이선스 정보

이 콘텐츠는 **MIT 라이선스** 하에 제공됩니다. 이용 약관은 [LICENSE](../../LICENSE)에서 확인하세요.

## 🤝 기여 가이드라인

이 프로젝트는 기여와 제안을 환영합니다. 대부분의 기여는 기여자가 자신의 기여를 사용할 권리를 실제로 보유하고 있음을 선언하는 Contributor License Agreement(CLA)에 동의해야 합니다. 자세한 내용은 <https://cla.opensource.microsoft.com>를 참조하세요.

풀 리퀘스트를 제출하면 CLA 봇이 자동으로 CLA 제출 필요 여부를 판단하고 PR에 적절한 상태 표시나 댓글을 추가합니다. 봇의 안내에 따라 진행하면 됩니다. 모든 리포지토리에서 한 번만 진행하면 됩니다.

이 프로젝트는 [Microsoft 오픈 소스 행동 강령](https://opensource.microsoft.com/codeofconduct/)을 채택했습니다. 자세한 내용은 [행동 강령 FAQ](https://opensource.microsoft.com/codeofconduct/faq/)를 참고하거나 추가 질문이나 의견은 [opencode@microsoft.com](mailto:opencode@microsoft.com)으로 문의하세요.

## 🎒 기타 강좌
저희 팀은 다른 강좌도 제작합니다! 확인해 보세요:

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
- [초보자를 위한 XR 개발](https://github.com/microsoft/xr-development-for-beginners?WT.mc_id=academic-105485-koreyst)
- [AI 페어 프로그래밍을 위한 GitHub Copilot 마스터하기](https://aka.ms/GitHubCopilotAI?WT.mc_id=academic-105485-koreyst)
- [C#/.NET 개발자를 위한 GitHub Copilot 마스터하기](https://github.com/microsoft/mastering-github-copilot-for-dotnet-csharp-developers?WT.mc_id=academic-105485-koreyst)
- [나만의 Copilot 모험 선택하기](https://github.com/microsoft/CopilotAdventures?WT.mc_id=academic-105485-koreyst)


## ™️ 상표 고지

이 프로젝트에는 프로젝트, 제품 또는 서비스의 상표나 로고가 포함될 수 있습니다. Microsoft 상표 또는 로고의 승인된 사용은 [Microsoft의 상표 및 브랜드 가이드라인](https://www.microsoft.com/legal/intellectualproperty/trademarks/usage/general)을 준수해야 합니다.  
이 프로젝트의 수정된 버전에서 Microsoft 상표 또는 로고를 사용할 경우 혼동을 초래하거나 Microsoft의 후원을 암시해서는 안 됩니다.  
제3자 상표 또는 로고의 사용은 해당 제3자의 정책을 따릅니다.

**면책 조항**:  
이 문서는 AI 번역 서비스 [Co-op Translator](https://github.com/Azure/co-op-translator)를 사용하여 번역되었습니다. 정확성을 위해 최선을 다하고 있으나, 자동 번역에는 오류나 부정확성이 포함될 수 있음을 유의하시기 바랍니다. 원본 문서는 해당 언어의 원문이 권위 있는 출처로 간주되어야 합니다. 중요한 정보의 경우 전문 인력에 의한 번역을 권장합니다. 본 번역 사용으로 인해 발생하는 오해나 잘못된 해석에 대해 당사는 책임을 지지 않습니다.