<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "a22b7dd11cd7690f99f9195877cafdc3",
  "translation_date": "2025-06-10T05:36:40+00:00",
  "source_file": "10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab2/README.md",
  "language_code": "ar"
}
-->
# 🌐 الوحدة 2: أساسيات MCP مع مجموعة أدوات الذكاء الاصطناعي

[![Duration](https://img.shields.io/badge/Duration-20%20minutes-blue.svg)]()
[![Difficulty](https://img.shields.io/badge/Difficulty-Intermediate-yellow.svg)]()
[![Prerequisites](https://img.shields.io/badge/Prerequisites-Module%201%20Complete-orange.svg)]()

## 📋 أهداف التعلم

بنهاية هذه الوحدة، ستتمكن من:
- ✅ فهم بنية وفوائد بروتوكول سياق النموذج (MCP)
- ✅ استكشاف نظام خوادم MCP الخاص بشركة Microsoft
- ✅ دمج خوادم MCP مع منشئ وكلاء مجموعة أدوات الذكاء الاصطناعي
- ✅ بناء وكيل أتمتة متصفح وظيفي باستخدام Playwright MCP
- ✅ تكوين واختبار أدوات MCP داخل وكلائك
- ✅ تصدير ونشر وكلاء مدعومين من MCP للاستخدام الإنتاجي

## 🎯 البناء على الوحدة 1

في الوحدة 1، أتقنا أساسيات مجموعة أدوات الذكاء الاصطناعي وأنشأنا وكيل Python الأول لدينا. الآن سنقوم **بتعزيز** وكلائك من خلال ربطهم بأدوات وخدمات خارجية عبر بروتوكول ثوري يُدعى **بروتوكول سياق النموذج (MCP)**.

فكر في هذا كتحديث من آلة حاسبة بسيطة إلى حاسوب كامل - حيث ستكتسب وكلاء الذكاء الاصطناعي لديك القدرة على:
- 🌐 تصفح المواقع والتفاعل معها
- 📁 الوصول إلى الملفات والتعامل معها
- 🔧 التكامل مع أنظمة المؤسسات
- 📊 معالجة البيانات الحية من واجهات برمجة التطبيقات (APIs)

## 🧠 فهم بروتوكول سياق النموذج (MCP)

### 🔍 ما هو MCP؟

بروتوكول سياق النموذج (MCP) هو **"USB-C لتطبيقات الذكاء الاصطناعي"** - معيار مفتوح ثوري يربط نماذج اللغة الكبيرة (LLMs) بالأدوات الخارجية ومصادر البيانات والخدمات. تمامًا كما قضى USB-C على فوضى الكابلات من خلال توفير موصل عالمي واحد، يقضي MCP على تعقيدات دمج الذكاء الاصطناعي من خلال بروتوكول موحد.

### 🎯 المشكلة التي يحلها MCP

**قبل MCP:**
- 🔧 تكاملات مخصصة لكل أداة
- 🔄 الاعتماد على بائع واحد مع حلول ملكية  
- 🔒 ثغرات أمنية بسبب الاتصالات العشوائية
- ⏱️ شهور من التطوير لتكاملات بسيطة

**مع MCP:**
- ⚡ تكامل أدوات سهل وبدون تعقيد
- 🔄 بنية خالية من التبعية على البائعين
- 🛡️ ممارسات أمان مدمجة
- 🚀 دقائق لإضافة قدرات جديدة

### 🏗️ نظرة معمقة على بنية MCP

يتبع MCP بنية **عميل-خادم** تخلق نظامًا بيئيًا آمنًا وقابلًا للتوسع:

```mermaid
graph TB
    A[AI Application/Agent] --> B[MCP Client]
    B --> C[MCP Server 1: Files]
    B --> D[MCP Server 2: Web APIs]
    B --> E[MCP Server 3: Database]
    B --> F[MCP Server N: Custom Tools]
    
    C --> G[Local File System]
    D --> H[External APIs]
    E --> I[Database Systems]
    F --> J[Enterprise Systems]
```

**🔧 المكونات الأساسية:**

| المكون | الدور | أمثلة |
|-----------|------|----------|
| **MCP Hosts** | التطبيقات التي تستخدم خدمات MCP | Claude Desktop، VS Code، AI Toolkit |
| **MCP Clients** | معالجات البروتوكول (1:1 مع الخوادم) | مدمجة في تطبيقات المضيف |
| **MCP Servers** | تعرض القدرات عبر البروتوكول القياسي | Playwright، Files، Azure، GitHub |
| **Transport Layer** | طرق الاتصال | stdio، HTTP، WebSockets |

## 🏢 نظام خوادم MCP الخاص بشركة Microsoft

تتقدم Microsoft في نظام MCP البيئي بمجموعة شاملة من خوادم المؤسسات التي تلبي احتياجات الأعمال الواقعية.

### 🌟 خوادم MCP المميزة من Microsoft

#### 1. ☁️ خادم Azure MCP  
**🔗 المستودع**: [azure/azure-mcp](https://github.com/azure/azure-mcp)  
**🎯 الغرض**: إدارة شاملة لموارد Azure مع دمج الذكاء الاصطناعي

**✨ الميزات الرئيسية:**  
- توفير البنية التحتية بطريقة إعلانية  
- مراقبة الموارد في الوقت الحقيقي  
- توصيات لتحسين التكاليف  
- التحقق من الامتثال الأمني  

**🚀 حالات الاستخدام:**  
- البنية التحتية ككود بمساعدة الذكاء الاصطناعي  
- توسيع الموارد تلقائيًا  
- تحسين تكاليف السحابة  
- أتمتة سير عمل DevOps  

#### 2. 📊 Microsoft Dataverse MCP  
**📚 الوثائق**: [Microsoft Dataverse Integration](https://go.microsoft.com/fwlink/?linkid=2320176)  
**🎯 الغرض**: واجهة لغة طبيعية لبيانات الأعمال  

**✨ الميزات الرئيسية:**  
- استعلامات قاعدة البيانات بلغة طبيعية  
- فهم سياق الأعمال  
- قوالب استدعاء مخصصة  
- حوكمة بيانات المؤسسات  

**🚀 حالات الاستخدام:**  
- تقارير ذكاء الأعمال  
- تحليل بيانات العملاء  
- رؤى خط المبيعات  
- استعلامات الامتثال  

#### 3. 🌐 Playwright MCP Server  
**🔗 المستودع**: [microsoft/playwright-mcp](https://github.com/microsoft/playwright-mcp)  
**🎯 الغرض**: أتمتة المتصفح وقدرات التفاعل مع الويب  

**✨ الميزات الرئيسية:**  
- أتمتة عبر متصفحات متعددة (Chrome، Firefox، Safari)  
- كشف ذكي للعناصر  
- إنشاء لقطات شاشة وملفات PDF  
- مراقبة حركة الشبكة  

**🚀 حالات الاستخدام:**  
- سير عمل اختبار مؤتمت  
- استخراج البيانات من الويب  
- مراقبة واجهة المستخدم وتجربة المستخدم  
- أتمتة التحليل التنافسي  

#### 4. 📁 Files MCP Server  
**🔗 المستودع**: [microsoft/files-mcp-server](https://github.com/microsoft/files-mcp-server)  
**🎯 الغرض**: عمليات نظام الملفات الذكية  

**✨ الميزات الرئيسية:**  
- إدارة الملفات بطريقة إعلانية  
- مزامنة المحتوى  
- تكامل التحكم في الإصدارات  
- استخراج البيانات الوصفية  

**🚀 حالات الاستخدام:**  
- إدارة الوثائق  
- تنظيم مستودعات الأكواد  
- سير عمل نشر المحتوى  
- معالجة ملفات خطوط البيانات  

#### 5. 📝 MarkItDown MCP Server  
**🔗 المستودع**: [microsoft/markitdown](https://github.com/microsoft/markitdown)  
**🎯 الغرض**: معالجة وتعديل Markdown متقدم  

**✨ الميزات الرئيسية:**  
- تحليل Markdown غني  
- تحويل الصيغ (MD ↔ HTML ↔ PDF)  
- تحليل هيكل المحتوى  
- معالجة القوالب  

**🚀 حالات الاستخدام:**  
- سير عمل التوثيق الفني  
- أنظمة إدارة المحتوى  
- إنشاء التقارير  
- أتمتة قواعد المعرفة  

#### 6. 📈 Clarity MCP Server  
**📦 الحزمة**: [@microsoft/clarity-mcp-server](https://www.npmjs.com/package/@microsoft/clarity-mcp-server)  
**🎯 الغرض**: تحليلات الويب ورؤى سلوك المستخدم  

**✨ الميزات الرئيسية:**  
- تحليل بيانات خرائط الحرارة  
- تسجيل جلسات المستخدم  
- مقاييس الأداء  
- تحليل قمع التحويل  

**🚀 حالات الاستخدام:**  
- تحسين مواقع الويب  
- بحوث تجربة المستخدم  
- تحليل اختبارات A/B  
- لوحات معلومات ذكاء الأعمال  

### 🌍 نظام المجتمع البيئي

بعيدًا عن خوادم Microsoft، يشمل نظام MCP البيئي:  
- **🐙 GitHub MCP**: إدارة المستودعات وتحليل الأكواد  
- **🗄️ قواعد بيانات MCP**: تكاملات PostgreSQL، MySQL، MongoDB  
- **☁️ مزودو السحابة MCP**: أدوات AWS، GCP، Digital Ocean  
- **📧 تواصل MCP**: تكاملات Slack، Teams، البريد الإلكتروني  

## 🛠️ المختبر العملي: بناء وكيل أتمتة متصفح

**🎯 هدف المشروع**: إنشاء وكيل أتمتة متصفح ذكي باستخدام خادم Playwright MCP يمكنه تصفح المواقع، استخراج المعلومات، وأداء تفاعلات ويب معقدة.

### 🚀 المرحلة 1: إعداد أساس الوكيل

#### الخطوة 1: تهيئة وكيلك  
1. **افتح منشئ وكلاء AI Toolkit**  
2. **أنشئ وكيل جديد** بالإعدادات التالية:  
   - **الاسم**: `BrowserAgent`
   - **Model**: Choose GPT-4o 

![BrowserAgent](../../../../translated_images/BrowserAgent.09c1adde5e136573b64ab1baecd830049830e295eac66cb18bebb85fb386e00a.ar.png)


### 🔧 Phase 2: MCP Integration Workflow

#### Step 3: Add MCP Server Integration
1. **Navigate to Tools Section** in Agent Builder
2. **Click "Add Tool"** to open the integration menu
3. **Select "MCP Server"** from available options

![AddMCP](../../../../translated_images/AddMCP.afe3308ac20aa94469a5717b632d77b2197b9838a438b05d39aeb2db3ec47ef1.ar.png)

**🔍 Understanding Tool Types:**
- **Built-in Tools**: Pre-configured AI Toolkit functions
- **MCP Servers**: External service integrations
- **Custom APIs**: Your own service endpoints
- **Function Calling**: Direct model function access

#### Step 4: MCP Server Selection
1. **Choose "MCP Server"** option to proceed
![AddMCPServer](../../../../translated_images/AddMCPServer.69b911ccef872cbd0d0c0c2e6a00806916e1673e543b902a23dee23e6ff54b4c.ar.png)

2. **Browse MCP Catalog** to explore available integrations
![MCPCatalog](../../../../translated_images/MCPCatalog.a817d053145699006264f5a475f2b48fbd744e43633f656b6453c15a09ba5130.ar.png)


### 🎮 Phase 3: Playwright MCP Configuration

#### Step 5: Select and Configure Playwright
1. **Click "Use Featured MCP Servers"** to access Microsoft's verified servers
2. **Select "Playwright"** from the featured list
3. **Accept Default MCP ID** or customize for your environment

![MCPID](../../../../translated_images/MCPID.67d446052979e819c945ff7b6430196ef587f5217daadd3ca52fa9659c1245c9.ar.png)

#### Step 6: Enable Playwright Capabilities
**🔑 Critical Step**: Select **ALL** available Playwright methods for maximum functionality

![Tools](../../../../translated_images/Tools.3ea23c447b4d9feccbd7101e6dcf9e27cb0e5273f351995fde62c5abf9a78b4c.ar.png)

**🛠️ Essential Playwright Tools:**
- **Navigation**: `goto`, `goBack`, `goForward`, `reload`
- **Interaction**: `click`, `fill`, `press`, `hover`, `drag`
- **Extraction**: `textContent`, `innerHTML`, `getAttribute`
- **Validation**: `isVisible`, `isEnabled`, `waitForSelector`
- **Capture**: `screenshot`, `pdf`, `video`
- **Network**: `setExtraHTTPHeaders`, `route`, `waitForResponse`

#### الخطوة 7: التحقق من نجاح التكامل  
**✅ مؤشرات النجاح:**  
- ظهور جميع الأدوات في واجهة منشئ الوكلاء  
- عدم وجود رسائل خطأ في لوحة التكامل  
- حالة خادم Playwright تظهر "Connected"

![AgentTools](../../../../translated_images/AgentTools.053cfb96a17e02199dcc6563010d2b324d4fc3ebdd24889657a6950647a52f63.ar.png)

**🔧 استكشاف المشكلات الشائعة:**  
- **فشل الاتصال**: تحقق من اتصال الإنترنت وإعدادات الجدار الناري  
- **الأدوات المفقودة**: تأكد من اختيار جميع القدرات أثناء الإعداد  
- **أخطاء الأذونات**: تحقق من أن VS Code لديه الأذونات اللازمة للنظام  

### 🎯 المرحلة 4: هندسة الطلبات المتقدمة

#### الخطوة 8: تصميم مطالبات نظام ذكية  
أنشئ مطالبات متقدمة تستفيد من كامل قدرات Playwright:

```markdown
# Web Automation Expert System Prompt

## Core Identity
You are an advanced web automation specialist with deep expertise in browser automation, web scraping, and user experience analysis. You have access to Playwright tools for comprehensive browser control.

## Capabilities & Approach
### Navigation Strategy
- Always start with screenshots to understand page layout
- Use semantic selectors (text content, labels) when possible
- Implement wait strategies for dynamic content
- Handle single-page applications (SPAs) effectively

### Error Handling
- Retry failed operations with exponential backoff
- Provide clear error descriptions and solutions
- Suggest alternative approaches when primary methods fail
- Always capture diagnostic screenshots on errors

### Data Extraction
- Extract structured data in JSON format when possible
- Provide confidence scores for extracted information
- Validate data completeness and accuracy
- Handle pagination and infinite scroll scenarios

### Reporting
- Include step-by-step execution logs
- Provide before/after screenshots for verification
- Suggest optimizations and alternative approaches
- Document any limitations or edge cases encountered

## Ethical Guidelines
- Respect robots.txt and rate limiting
- Avoid overloading target servers
- Only extract publicly available information
- Follow website terms of service
```

#### الخطوة 9: إنشاء مطالبات مستخدم ديناميكية  
صمم مطالبات تعرض قدرات متنوعة:

**🌐 مثال تحليل ويب:**  
```markdown
Navigate to github.com/kinfey and provide a comprehensive analysis including:
1. Repository structure and organization
2. Recent activity and contribution patterns  
3. Documentation quality assessment
4. Technology stack identification
5. Community engagement metrics
6. Notable projects and their purposes

Include screenshots at key steps and provide actionable insights.
```

![Prompt](../../../../translated_images/Prompt.bfc846605db4999f4d9c1b09c710ef63cae7b3057444e68bf07240fb142d9f8f.ar.png)

### 🚀 المرحلة 5: التنفيذ والاختبار

#### الخطوة 10: تنفيذ أول أتمتة لك  
1. **انقر على "تشغيل"** لبدء تسلسل الأتمتة  
2. **راقب التنفيذ في الوقت الحقيقي**:  
   - فتح متصفح Chrome تلقائيًا  
   - يتنقل الوكيل إلى الموقع المستهدف  
   - التقاط لقطات شاشة لكل خطوة رئيسية  
   - تدفق نتائج التحليل في الوقت الحقيقي  

![Browser](../../../../translated_images/Browser.ec011d0bd64d0d112c8a29bd8cc44c76d0bbfd0b019cb2983ef679328435ce5d.ar.png)

#### الخطوة 11: تحليل النتائج والرؤى  
راجع التحليل الشامل في واجهة منشئ الوكلاء:

![Result](../../../../translated_images/Result.8638f2b6703e9ea6d58d4e4475e39456b6a51d4c787f9bf481bae694d370a69a.ar.png)

### 🌟 المرحلة 6: القدرات المتقدمة والنشر

#### الخطوة 12: التصدير والنشر الإنتاجي  
يدعم منشئ الوكلاء خيارات نشر متعددة:

![Code](../../../../translated_images/Code.d9eeeead0b96db0ca19c5b10ad64cfea8c1d0d1736584262970a4d43e1403d13.ar.png)

## 🎓 ملخص الوحدة 2 والخطوات التالية

### 🏆 الإنجاز المحقق: إتقان دمج MCP

**✅ المهارات المكتسبة:**  
- [ ] فهم بنية MCP وفوائده  
- [ ] استكشاف نظام خوادم MCP الخاص بـ Microsoft  
- [ ] دمج Playwright MCP مع AI Toolkit  
- [ ] بناء وكلاء أتمتة متصفح متقدمين  
- [ ] هندسة مطالبات متقدمة لأتمتة الويب  

### 📚 موارد إضافية

- **🔗 مواصفات MCP**: [الوثائق الرسمية للبروتوكول](https://modelcontextprotocol.io/)  
- **🛠️ Playwright API**: [مرجع الطرق الكامل](https://playwright.dev/docs/api/class-playwright)  
- **🏢 خوادم MCP من Microsoft**: [دليل التكامل المؤسسي](https://github.com/microsoft/mcp-servers)  
- **🌍 أمثلة المجتمع**: [معرض خوادم MCP](https://github.com/modelcontextprotocol/servers)

**🎉 تهانينا!** لقد أتقنت دمج MCP بنجاح ويمكنك الآن بناء وكلاء ذكاء اصطناعي جاهزين للإنتاج مع قدرات أدوات خارجية!

### 🔜 الانتقال إلى الوحدة التالية

هل أنت مستعد للارتقاء بمهارات MCP الخاصة بك؟ تابع إلى **[الوحدة 3: تطوير MCP متقدم مع AI Toolkit](../lab3/README.md)** حيث ستتعلم كيفية:  
- إنشاء خوادم MCP مخصصة خاصة بك  
- تكوين واستخدام أحدث SDK لـ MCP بلغة Python  
- إعداد MCP Inspector لأغراض التصحيح  
- إتقان سير عمل تطوير خوادم MCP المتقدم  
- بناء خادم MCP للطقس من الصفر

**إخلاء المسؤولية**:  
تمت ترجمة هذا المستند باستخدام خدمة الترجمة الآلية [Co-op Translator](https://github.com/Azure/co-op-translator). بينما نسعى لتحقيق الدقة، يرجى العلم أن الترجمات الآلية قد تحتوي على أخطاء أو عدم دقة. يجب اعتبار المستند الأصلي بلغته الأصلية المصدر الموثوق به. للمعلومات الهامة، يُنصح بالاعتماد على الترجمة البشرية المهنية. نحن غير مسؤولين عن أي سوء فهم أو تفسير خاطئ ناتج عن استخدام هذه الترجمة.