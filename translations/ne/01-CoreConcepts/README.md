<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "788eb17750e970a0bc3b5e7f2e99975b",
  "translation_date": "2025-05-18T15:08:35+00:00",
  "source_file": "01-CoreConcepts/README.md",
  "language_code": "ne"
}
-->
# 📖 MCP Core Concepts: AI एकीकरणको लागि Model Context Protocol मा दक्षता हासिल गर्ने

Model Context Protocol (MCP) एक शक्तिशाली, मानकीकृत फ्रेमवर्क हो जसले ठूलो भाषा मोडेलहरू (LLMs) र बाह्य उपकरणहरू, अनुप्रयोगहरू, र डेटा स्रोतहरू बीचको सञ्चारलाई अनुकूल बनाउँछ। यो SEO-अनुकूल मार्गदर्शनले तपाईंलाई MCP का मुख्य अवधारणाहरूमा परिचित गराउनेछ, जसले तपाईंलाई यसको क्लाइन्ट-सर्भर संरचना, आवश्यक कम्पोनेन्टहरू, सञ्चार प्रक्रिया, र कार्यान्वयनका उत्तम अभ्यासहरू बुझ्न मद्दत पुर्‍याउँछ।

## अवलोकन

यो पाठले Model Context Protocol (MCP) पारिस्थितिकी तन्त्रको आधारभूत संरचना र कम्पोनेन्टहरू अन्वेषण गर्दछ। तपाईंले क्लाइन्ट-सर्भर संरचना, मुख्य कम्पोनेन्टहरू, र सञ्चार प्रक्रियाहरूको बारेमा सिक्नु हुनेछ जसले MCP अन्तरक्रियाहरूलाई चलाउँछ।

## 👩‍🎓 मुख्य सिकाइ लक्ष्यहरू

यस पाठको अन्त्यसम्म, तपाईंले:

- MCP क्लाइन्ट-सर्भर संरचना बुझ्नुहुनेछ।
- Hosts, Clients, र Servers का भूमिका र जिम्मेवारीहरू पहिचान गर्नुहुनेछ।
- MCP लाई लचिलो एकीकरण तह बनाउने मुख्य विशेषताहरू विश्लेषण गर्नुहुनेछ।
- MCP पारिस्थितिकी तन्त्र भित्र सूचना प्रवाह कसरी हुन्छ भन्ने जान्नुहुनेछ।
- .NET, Java, Python, र JavaScript मा कोड उदाहरणहरू मार्फत व्यवहारिक ज्ञान प्राप्त गर्नुहुनेछ।

## 🔎 MCP संरचना: गहिरो दृष्टि

MCP पारिस्थितिकी तन्त्र क्लाइन्ट-सर्भर मोडलमा आधारित छ। यो मोड्युलर संरचनाले AI अनुप्रयोगहरूलाई उपकरणहरू, डाटाबेस, API हरू, र सन्दर्भ स्रोतहरूसँग प्रभावकारी रूपमा अन्तरक्रिया गर्न सक्षम बनाउँछ। अब यस संरचनालाई यसको मुख्य कम्पोनेन्टहरूमा विभाजन गरौं।

### 1. Hosts

Model Context Protocol (MCP) मा Hosts प्रयोगकर्ताहरूले प्रोटोकलसँग अन्तरक्रिया गर्ने प्राथमिक इन्टरफेसको रूपमा महत्त्वपूर्ण भूमिका खेल्दछन्। Hosts ती अनुप्रयोगहरू वा वातावरणहरू हुन् जसले MCP सर्भरहरूसँग जडान सुरु गर्छन् र डेटा, उपकरणहरू, र प्रॉम्प्टहरू पहुँच गर्छन्। Hosts का उदाहरणहरूमा Visual Studio Code जस्ता एकीकृत विकास वातावरणहरू (IDEs), Claude Desktop जस्ता AI उपकरणहरू, वा विशिष्ट कार्यहरूका लागि बनाइएका कस्टम एजेन्टहरू पर्दछन्।

**Hosts** LLM अनुप्रयोगहरू हुन् जसले जडान सुरु गर्छन्। तिनीहरूले:

- AI मोडेलहरूसँग अन्तरक्रिया गरेर प्रतिक्रिया उत्पादन गर्छन्।
- MCP सर्भरहरूसँग जडान सुरु गर्छन्।
- संवाद प्रवाह र प्रयोगकर्ता इन्टरफेस व्यवस्थापन गर्छन्।
- अनुमति र सुरक्षा प्रतिबन्धहरू नियन्त्रण गर्छन्।
- डेटा साझेदारी र उपकरण सञ्चालनका लागि प्रयोगकर्ता सहमति व्यवस्थापन गर्छन्।

### 2. Clients

Clients Hosts र MCP सर्भरहरू बीचको अन्तरक्रिया सहज बनाउन महत्त्वपूर्ण कम्पोनेन्टहरू हुन्। Clients मध्यस्थको रूपमा कार्य गर्छन्, जसले Hosts लाई MCP सर्भरहरूले प्रदान गर्ने कार्यक्षमताहरू पहुँच गर्न र प्रयोग गर्न सक्षम बनाउँछ। तिनीहरूले MCP संरचनाभित्र सहज सञ्चार र प्रभावकारी डेटा विनिमय सुनिश्चित गर्न महत्त्वपूर्ण भूमिका खेल्दछन्।

**Clients** Host अनुप्रयोग भित्रका कनेक्टर्स हुन्। तिनीहरूले:

- प्रॉम्प्ट/निर्देशनहरूसँग सर्भरहरूलाई अनुरोध पठाउँछन्।
- सर्भरहरूसँग क्षमता वार्ता गर्छन्।
- मोडेलहरूबाट उपकरण सञ्चालन अनुरोधहरू व्यवस्थापन गर्छन्।
- प्रयोगकर्तालाई प्रतिक्रिया प्रक्रिया गरी प्रदर्शन गर्छन्।

### 3. Servers

Servers MCP क्लाइन्टहरूबाट अनुरोधहरू ह्यान्डल गर्ने र उपयुक्त प्रतिक्रिया प्रदान गर्ने जिम्मेवार हुन्छन्। तिनीहरूले डेटा पुनःप्राप्ति, उपकरण सञ्चालन, र प्रॉम्प्ट उत्पादन जस्ता विभिन्न कार्यहरू व्यवस्थापन गर्छन्। Servers ले Clients र Hosts बीचको सञ्चार प्रभावकारी र भरपर्दो बनाउन सुनिश्चित गर्छन्, अन्तरक्रिया प्रक्रियाको अखण्डता कायम राख्छन्।

**Servers** सन्दर्भ र क्षमताहरू प्रदान गर्ने सेवाहरू हुन्। तिनीहरूले:

- उपलब्ध सुविधाहरू (स्रोतहरू, प्रॉम्प्टहरू, उपकरणहरू) दर्ता गर्छन्।
- Client बाट उपकरण कलहरू प्राप्त गरी सञ्चालन गर्छन्।
- मोडेल प्रतिक्रियाहरू सुधार गर्न सन्दर्भ जानकारी प्रदान गर्छन्।
- नतिजा Clients लाई फर्काउँछन्।
- आवश्यक परे अन्तरक्रियाहरूमा अवस्था कायम राख्छन्।

Servers को विकास कुनै पनि व्यक्तिले विशेष कार्यक्षमतासहित मोडेल क्षमताहरू विस्तार गर्न सक्छ।

### 4. Server Features

Model Context Protocol (MCP) मा Servers ले Clients, Hosts, र भाषा मोडेलहरू बीच समृद्ध अन्तरक्रिया सक्षम गर्ने आधारभूत ब्लकहरू प्रदान गर्छन्। यी सुविधाहरूले संरचित सन्दर्भ, उपकरणहरू, र प्रॉम्प्टहरू प्रदान गरेर MCP को क्षमताहरू बढाउन डिजाइन गरिएका छन्।

MCP सर्भरहरूले निम्न सुविधाहरू प्रदान गर्न सक्छन्:

#### 📑 Resources 

Model Context Protocol (MCP) मा Resources विभिन्न प्रकारका सन्दर्भ र डेटा समेट्छन् जुन प्रयोगकर्ताहरू वा AI मोडेलहरूले प्रयोग गर्न सक्छन्। यीमा समावेश छन्:

- **सन्दर्भ डेटा**: निर्णय लिन र कार्यान्वयनका लागि प्रयोगकर्ताहरू वा AI मोडेलहरूले उपयोग गर्न सक्ने सूचना र सन्दर्भ।
- **ज्ञान आधारहरू र दस्तावेज भण्डारहरू**: संरचित र असंरचित डेटा संग्रहहरू, जस्तै लेखहरू, म्यानुअलहरू, र अनुसन्धान कागजातहरू, जसले मूल्यवान जानकारी र अन्तर्दृष्टि प्रदान गर्छन्।
- **स्थानीय फाइलहरू र डाटाबेसहरू**: उपकरणहरूमा वा डाटाबेसहरूमा स्थानीय रूपमा संग्रहित डेटा, जसलाई प्रशोधन र विश्लेषणका लागि पहुँच गर्न सकिन्छ।
- **API हरू र वेब सेवाहरू**: अतिरिक्त डेटा र कार्यक्षमताहरू प्रदान गर्ने बाह्य इन्टरफेस र सेवाहरू, जसले विभिन्न अनलाइन स्रोतहरू र उपकरणहरूसँग एकीकरण सक्षम पार्छ।

स्रोतको उदाहरणको रूपमा डेटाबेस स्कीमा वा फाइल लिन सकिन्छ जुन यसरी पहुँच गर्न सकिन्छ:

```text
file://log.txt
database://schema
```

### 🤖 Prompts

Model Context Protocol (MCP) मा Prompts विभिन्न पूर्वनिर्धारित ढाँचा र अन्तरक्रिया ढाँचाहरू समावेश छन् जसले प्रयोगकर्ता कार्यप्रवाहहरूलाई सहज बनाउँछन् र सञ्चार सुधार गर्छन्। यीमा समावेश छन्:

- **ढाँचाबद्ध सन्देशहरू र कार्यप्रवाहहरू**: पूर्व-संरचित सन्देशहरू र प्रक्रियाहरू जसले प्रयोगकर्ताहरूलाई विशेष कार्यहरू र अन्तरक्रियाहरूमा मार्गदर्शन गर्छन्।
- **पूर्वनिर्धारित अन्तरक्रिया ढाँचाहरू**: मानकीकृत क्रियाहरू र प्रतिक्रियाहरूको अनुक्रम जसले निरन्तर र प्रभावकारी सञ्चारलाई सहज बनाउँछ।
- **विशेषीकृत संवाद ढाँचाहरू**: विशिष्ट प्रकारका संवादहरूका लागि अनुकूलन योग्य ढाँचाहरू, जसले सान्दर्भिक र सन्दर्भानुकूल अन्तरक्रियाहरू सुनिश्चित गर्छ।

प्रॉम्प्ट टेम्प्लेट यस प्रकार देखिन सक्छ:

```markdown
Generate a product slogan based on the following {{product}} with the following {{keywords}}
```

#### ⛏️ Tools

Model Context Protocol (MCP) मा Tools ती कार्यहरू हुन् जुन AI मोडेलले विशिष्ट कार्यहरू सम्पन्न गर्न सञ्चालन गर्न सक्छ। यी उपकरणहरूले AI मोडेलको क्षमताहरू बढाउन संरचित र भरपर्दो अपरेसनहरू प्रदान गर्छन्। मुख्य पक्षहरू:

- **AI मोडेलले सञ्चालन गर्न सक्ने कार्यहरू**: Tools चलाउन मिल्ने कार्यहरू हुन् जुन AI मोडेलले विभिन्न कार्यहरू सम्पन्न गर्न बोलाउन सक्छ।
- **विशिष्ट नाम र विवरण**: प्रत्येक उपकरणको फरक नाम र यसको उद्देश्य तथा कार्यक्षमताको विस्तृत विवरण हुन्छ।
- **प्यारामिटरहरू र आउटपुटहरू**: Tools ले विशिष्ट प्यारामिटरहरू स्वीकार्छन् र संरचित नतिजाहरू फर्काउँछन्, जसले निरन्तर र पूर्वानुमेय परिणाम सुनिश्चित गर्छ।
- **अलग कार्यहरू**: Tools वेब खोज, गणना, र डाटाबेस क्वेरी जस्ता छुट्टै कार्यहरू सञ्चालन गर्छन्।

उदाहरण उपकरण यसरी देखिन सक्छ:

```typescript
server.tool(
  "GetProducts"
  {
    pageSize: z.string().optional(),
    pageCount: z.string().optional()
  }, () => {
    // return results from API
  }
)
```

## Client Features

Model Context Protocol (MCP) मा Clients ले Servers लाई विभिन्न प्रमुख सुविधाहरू प्रदान गर्छन् जसले प्रोटोकल भित्रको समग्र कार्यक्षमता र अन्तरक्रियालाई बढाउँछ। एउटा उल्लेखनीय सुविधा Sampling हो।

### 👉 Sampling

- **Server-प्रेरित एजेन्टिक व्यवहारहरू**: Clients ले Servers लाई स्वतन्त्र रूपमा विशिष्ट कार्यहरू वा व्यवहारहरू सुरु गर्न सक्षम बनाउँछन्, जसले प्रणालीको गतिशील क्षमताहरू बढाउँछ।
- **Recursive LLM अन्तरक्रियाहरू**: यस सुविधाले ठूलो भाषा मोडेलहरूसँग पुनरावृत्त अन्तरक्रियाहरू गर्न अनुमति दिन्छ, जसले जटिल र पुनरावृत्त कार्यहरूको प्रशोधन सक्षम बनाउँछ।
- **थप मोडेल पूर्ति अनुरोधहरू**: Servers मोडेलबाट थप पूर्तिहरू अनुरोध गर्न सक्छन्, जसले प्रतिक्रियाहरूलाई पूर्ण र सान्दर्भिक बनाउँछ।

## MCP मा सूचना प्रवाह

Model Context Protocol (MCP) ले Hosts, Clients, Servers, र मोडेलहरू बीच संरचित सूचना प्रवाह परिभाषित गर्छ। यस प्रवाहलाई बुझ्नाले प्रयोगकर्ता अनुरोधहरू कसरी प्रशोधन हुन्छन् र कसरी बाह्य उपकरणहरू र डेटा मोडेल प्रतिक्रियामा समाहित हुन्छन् भन्ने स्पष्ट हुन्छ।

- **Host जडान सुरु गर्छ**  
  Host अनुप्रयोग (जस्तै IDE वा च्याट इन्टरफेस) ले MCP सर्भरसँग जडान स्थापना गर्छ, सामान्यतया STDIO, WebSocket, वा अन्य समर्थित ट्रान्सपोर्ट मार्फत।

- **क्षमता वार्ता**  
  Client (Host भित्र एम्बेड गरिएको) र Server ले आफ्नो समर्थित सुविधाहरू, उपकरणहरू, स्रोतहरू, र प्रोटोकल संस्करणहरूको बारेमा जानकारी आदानप्रदान गर्छन्। यसले दुबै पक्षलाई सत्रका लागि उपलब्ध क्षमताहरू बुझ्न सुनिश्चित गर्छ।

- **प्रयोगकर्ता अनुरोध**  
  प्रयोगकर्ताले Host सँग अन्तरक्रिया गर्छ (जस्तै प्रॉम्प्ट वा आदेश प्रविष्टि)। Host ले यो इनपुट सङ्कलन गरी Client लाई प्रशोधनका लागि पठाउँछ।

- **स्रोत वा उपकरण प्रयोग**  
  - Client ले Server बाट थप सन्दर्भ वा स्रोतहरू (जस्तै फाइलहरू, डाटाबेस प्रविष्टिहरू, वा ज्ञान आधार लेखहरू) अनुरोध गर्न सक्छ जसले मोडेलको बुझाइ समृद्ध पार्छ।
  - यदि मोडेलले उपकरण आवश्यक ठान्छ (जस्तै डेटा ल्याउन, गणना गर्न, वा API कल गर्न), Client ले उपकरण कल अनुरोध Server लाई पठाउँछ, उपकरण नाम र प्यारामिटरहरू निर्दिष्ट गर्दै।

- **Server सञ्चालन**  
  Server ले स्रोत वा उपकरण अनुरोध प्राप्त गरी आवश्यक अपरेसनहरू (जस्तै कार्य चलाउने, डाटाबेस क्वेरी गर्ने, वा फाइल पुनःप्राप्त गर्ने) सञ्चालन गरी नतिजा संरचित रूपमा Client लाई फर्काउँछ।

- **प्रतिक्रिया उत्पादन**  
  Client ले Server को प्रतिक्रियाहरू (स्रोत डेटा, उपकरण आउटपुट आदि) मोडेल अन्तरक्रियामा समाहित गर्छ। मोडेलले यस सूचनाको प्रयोग गरी व्यापक र सान्दर्भिक प्रतिक्रिया उत्पादन गर्छ।

- **नतिजा प्रस्तुति**  
  Host ले Client बाट अन्तिम आउटपुट प्राप्त गरी प्रयोगकर्तालाई प्रस्तुत गर्छ, प्रायः मोडेलले उत्पन्न गरेको पाठ र उपकरण सञ्चालन वा स्रोत खोजीका नतिजाहरू दुवै समावेश गर्दै।

यस प्रवाहले MCP लाई उन्नत, अन्तरक्रियात्मक, र सन्दर्भ-सचेत AI अनुप्रयोगहरूलाई मोडेलहरूलाई बाह्य उपकरणहरू र डेटा स्रोतहरूसँग सहज रूपमा जोड्न सक्षम बनाउँछ।

## प्रोटोकल विवरण

MCP (Model Context Protocol) [JSON-RPC 2.0](https://www.jsonrpc.org/) माथि निर्माण गरिएको हो, जसले Hosts, Clients, र Servers बीच सञ्चारका लागि मानकीकृत, भाषा-स्वतन्त्र सन्देश ढाँचा प्रदान गर्छ। यस आधारले विभिन्न प्लेटफर्म र प्रोग्रामिङ भाषाहरूमा भरपर्दो, संरचित, र विस्तारयोग्य अन्तरक्रियाहरू सक्षम बनाउँछ।

### मुख्य प्रोटोकल सुविधाहरू

MCP ले JSON-RPC 2.0 लाई उपकरण कल, स्रोत पहुँच, र प्रॉम्प्ट व्यवस्थापनका लागि थप परम्पराहरूले विस्तार गर्दछ। यसले बहु ट्रान्सपोर्ट तहहरू (STDIO, WebSocket, SSE) समर्थन गर्दछ र कम्पोनेन्टहरू बीच सुरक्षित, विस्तारयोग्य, र भाषा-स्वतन्त्र सञ्चार सक्षम बनाउँछ।

#### 🧢 आधारभूत प्रोटोकल

- **JSON-RPC सन्देश ढाँचा**: सबै अनुरोध र प्रतिक्रियाहरू JSON-RPC 2.0 विशिष्टता प्रयोग गर्छन्, जसले विधि कलहरू, प्यारामिटरहरू, नतिजा, र त्रुटि ह्यान्डलिङको लागि निरन्तर संरचना सुनिश्चित गर्छ।
- **राज्यपूर्ण जडानहरू**: MCP सत्रहरूले धेरै अनुरोधहरूमा अवस्था कायम राख्छन्, निरन्तर संवाद, सन्दर्भ संचय, र स्रोत व्यवस्थापन समर्थन गर्दै।
- **क्षमता वार्ता**: जडान सेटअपको क्रममा, Clients र Servers ले समर्थित सुविधाहरू, प्रोटोकल संस्करणहरू, उपलब्ध उपकरणहरू, र स्रोतहरूको बारेमा जानकारी आदानप्रदान गर्छन्। यसले दुबै पक्षलाई एक अर्काका क्षमताहरू बुझ्न र आवश्यक अनुसार अनुकूलन गर्न सक्षम बनाउँछ।

#### ➕ अतिरिक्त उपयोगिताहरू

तल MCP ले विकासकर्ताको अनुभव सुधार्न र उन्नत परिदृश्यहरू सक्षम पार्न प्रदान गर्ने केही अतिरिक्त उपयोगिताहरू र प्रोटोकल विस्तारहरू छन्:

- **कन्फिगरेसन विकल्पहरू**: MCP ले सत्र प्यारामिटरहरूको गतिशील कन्फिगरेसन अनुमति दिन्छ, जस्तै उपकरण अनुमति, स्रोत पहुँच, र मोडेल सेटिङहरू, प्रत्येक अन्तरक्रियामा अनुकूलित।
- **प्रगति ट्र्याकिङ**: लामो समय लाग्ने अपरेसनहरूले प्रगति अद्यावधिकहरू रिपोर्ट गर्न सक्छन्, जसले प्रतिक्रिया दिने प्रयोगकर्ता इन्टरफेस र जटिल कार्यहरूको दौरान राम्रो प्रयोगकर्ता अनुभव सक्षम बनाउँछ।
- **अनुरोध रद्दीकरण**: Clients ले प्रगतिको क्रममा रहेका अनुरोधहरू रद्द गर्न सक्छन्, जसले प्रयोगकर्ताहरूलाई आवश्यक नभएको वा धेरै समय लागिरहेको अपरेसनहरू रोक्न अनुमति दिन्छ।
- **त्रुटि रिपोर्टिङ**: मानकीकृत त्रुटि सन्देशहरू र कोडहरूले समस्याहरू पत्ता लगाउन, असफलताहरू सजिलै ह्यान्डल गर्न, र प्रयोगकर्ता तथा विकासकर्तालाई क्रियाशील प्रतिक्रिया प्रदान गर्न मद्दत गर्छ।
- **लगिङ**: Clients र Servers दुवैले प्रोटोकल अन्तरक्रियाहरूको अडिट, डिबगिङ, र अनुगमनका लागि संरचित लगहरू उत्सर्जन गर्न सक्छन्।

यी प्रोटोकल सुविधाहरू प्रयोग गरेर, MCP ले भाषा मोडेलहरू र बाह्य उपकरण वा डेटा स्रोतहरू बीच robust, सुरक्षित, र लचिलो सञ्चार सुनिश्चित गर्छ।

### 🔐 सुरक्षा विचारहरू

MCP कार्यान्वयनहरूले सुरक्षित र भरपर्दो अन्तरक्रियाहरू सुनिश्चित गर्न केही मुख्य सुरक्षा सिद्धान्तहरू पालना गर्नुपर्छ:

- **प्रयोगकर्ता सहमति र नियन्त्रण**: कुनै पनि डेटा पहुँच वा अपरेसन अघि प्रयोगकर्ताबाट स्पष्ट सहमति लिनुपर्छ। प्रयोगकर्ताले कुन डेटा साझा गर्ने र कुन कार्यहरू अधिकृत गर्ने स्पष्ट नियन्त्रण पाउनु पर्छ, र समीक्षा तथा स्वीकृतिका लागि सहज इन्टरफेस उपलब्ध गराउनु पर्छ।

- **डेटा गोपनीयता**: प्रयोगकर्ता डेटा केवल स्पष्ट सहमतिपछि मात्र पहुँचयोग्य हुनुपर्छ र उपयुक्त पहुँच नियन्त्रणहरूले सुरक्षित हुनुपर्छ। MCP कार्यान्वयनहरूले अनधिकृत डेटा प्रसारणबाट सुरक्षा गर्नुपर्छ र सबै अन्तरक्रियाहरूमा गोपनीयता कायम राख्नुपर्छ।

- **उपकरण सुरक्षा**: कुनै पनि उपकरण कल गर्नु अघि स्पष्ट प्रयोगकर्ता सहमति आवश्यक छ। प्रयोगकर्ताले प्रत्येक उपकरणको कार्यक्षमता स्पष्ट रूपमा बुझ्नुपर्छ र अनपेक्षित वा असुरक्षित उपकरण सञ्चालन रोक्न कडा सुरक्षा सीमा लागू गर्नुपर्छ।

यी सिद्धान्तहरू पालना गरेर, MCP ले प्रयोगकर्ता विश्वास, गोपनीयता, र सुरक्षा सबै प्रोटोकल अन्तरक्रियाहरूमा कायम राख्छ।

## कोड उदाहरणहरू: मुख्य कम्पोनेन्टहरू

तल केही लोकप्रिय प्रोग्रामिङ भाषाहरूमा MCP सर्भर कम्पोनेन्टहरू र उपकरणहरू कसरी कार्यान्वयन गर्ने देखाउने कोड उदाहरणहरू छन्।

### .NET उदाहरण: साधारण MCP सर्भर उपकरणहरूसहित सिर्जना

यहाँ .NET मा एक साधारण MCP सर्भर कसरी उपकरणहरूसहित कार्यान्वयन गर्ने व्यावहारिक उदाहरण छ। यसले उपकरणहरू परिभाषित र दर्ता गर्ने, अनुरोधहरू ह्यान्डल गर्ने, र Model Context Protocol प्रयोग गरी सर्भर जडान गर्ने तरिका देखाउँछ।

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

### Java उदाहरण: MCP सर्भर कम्पोनेन्टहरू

यो उदाहरणले माथिको .NET उदाहरण जस्तै MCP सर्भर र उपकरण दर्ता देखाउँछ, तर Java मा कार्यान्वयन गरिएको।

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

### Python उदाहरण: MCP सर्भर निर्माण

यस उदाहरणमा हामी Python मा MCP सर्भर कसरी बनाउने देखाउँछौं। तपाईंलाई दुई फरक तरिकाले उपकरणहरू सिर्जना गर्ने तरिका पनि देखाइन्छ।

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

### JavaScript उदाहरण: MCP सर्भर सिर्जना

यो उदाहरणले JavaScript मा MCP सर्भर सिर्जना गर्ने तरिका देखाउँछ र मौसमसँग सम्बन्धित दुई उपकरणहरू दर्ता गर्ने देखाउँछ।

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

यो

**अस्वीकरण**:  
यो दस्तावेज़ AI अनुवाद सेवा [Co-op Translator](https://github.com/Azure/co-op-translator) प्रयोग गरेर अनुवाद गरिएको हो। हामी शुद्धताको लागि प्रयासरत छौं, तर कृपया ध्यान दिनुहोस् कि स्वचालित अनुवादमा त्रुटिहरू वा अशुद्धता हुन सक्छ। मूल दस्तावेज़लाई यसको मूल भाषामा नै आधिकारिक स्रोतको रूपमा मान्नुपर्छ। महत्वपूर्ण जानकारीका लागि पेशेवर मानव अनुवाद सिफारिस गरिन्छ। यस अनुवादको प्रयोगबाट उत्पन्न कुनै पनि गलतफहमी वा गलत व्याख्याका लागि हामी जिम्मेवार छैनौं।