<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "d88dbf928fa0f159b82312e9a6757ba0",
  "translation_date": "2025-06-18T08:52:19+00:00",
  "source_file": "04-PracticalImplementation/README.md",
  "language_code": "bn"
}
-->
# Practical Implementation

প্রায়োগিক বাস্তবায়ন হল যেখানে Model Context Protocol (MCP)-এর শক্তি স্পষ্ট হয়ে ওঠে। MCP-এর তত্ত্ব এবং স্থাপত্য বোঝা গুরুত্বপূর্ণ হলেও, প্রকৃত মূল্য তখনই আসে যখন আপনি এই ধারণাগুলো ব্যবহার করে বাস্তব সমস্যার সমাধান করতে সক্ষম হন। এই অধ্যায়টি ধারণাগত জ্ঞান এবং হাতে কলমে উন্নয়নের মধ্যে সেতুবন্ধন সৃষ্টি করে, MCP-ভিত্তিক অ্যাপ্লিকেশন তৈরি করার প্রক্রিয়ায় আপনাকে পথ দেখাবে।

আপনি যদি বুদ্ধিমান সহকারী তৈরি করেন, ব্যবসায়িক কর্মপ্রবাহে AI সংযুক্ত করেন, অথবা ডেটা প্রক্রিয়াকরণের জন্য কাস্টম টুল তৈরি করেন, MCP একটি নমনীয় ভিত্তি প্রদান করে। এর ভাষা-নিরপেক্ষ ডিজাইন এবং জনপ্রিয় প্রোগ্রামিং ভাষার জন্য অফিসিয়াল SDK গুলো বিভিন্ন ধরণের ডেভেলপারদের জন্য সহজলভ্য। এই SDK গুলো ব্যবহার করে আপনি দ্রুত প্রোটোটাইপ তৈরি, পুনরাবৃত্তি এবং বিভিন্ন প্ল্যাটফর্ম ও পরিবেশে আপনার সমাধান স্কেল করতে পারবেন।

পরবর্তী অংশগুলোতে, আপনি C#, Java, TypeScript, JavaScript, এবং Python-এ MCP বাস্তবায়নের জন্য ব্যবহারিক উদাহরণ, নমুনা কোড এবং ডিপ্লয়মেন্ট কৌশল পাবেন। এছাড়াও শিখবেন কীভাবে MCP সার্ভার ডিবাগ এবং টেস্ট করবেন, API পরিচালনা করবেন, এবং Azure ব্যবহার করে ক্লাউডে সমাধান মোতায়েন করবেন। এই হাতে কলমের রিসোর্সগুলো আপনার শেখার গতি বাড়াবে এবং আত্মবিশ্বাসের সাথে শক্তিশালী, প্রোডাকশন-রেডি MCP অ্যাপ্লিকেশন তৈরি করতে সাহায্য করবে।

## Overview

এই পাঠে MCP বাস্তবায়নের ব্যবহারিক দিকগুলো বিভিন্ন প্রোগ্রামিং ভাষায় আলোচনা করা হবে। আমরা দেখব কীভাবে C#, Java, TypeScript, JavaScript, এবং Python-এ MCP SDK ব্যবহার করে শক্তিশালী অ্যাপ্লিকেশন তৈরি করা যায়, MCP সার্ভার ডিবাগ ও টেস্ট করা যায়, এবং পুনরায় ব্যবহারযোগ্য রিসোর্স, প্রম্পট এবং টুল তৈরি করা যায়।

## Learning Objectives

এই পাঠ শেষে আপনি সক্ষম হবেন:
- বিভিন্ন প্রোগ্রামিং ভাষায় অফিসিয়াল SDK ব্যবহার করে MCP সমাধান বাস্তবায়ন করতে
- MCP সার্ভারগুলো সুনির্দিষ্টভাবে ডিবাগ ও টেস্ট করতে
- সার্ভার ফিচার (Resources, Prompts, এবং Tools) তৈরি ও ব্যবহার করতে
- জটিল কাজের জন্য কার্যকর MCP কর্মপ্রবাহ ডিজাইন করতে
- কর্মক্ষমতা এবং নির্ভরযোগ্যতার জন্য MCP বাস্তবায়ন অপ্টিমাইজ করতে

## Official SDK Resources

Model Context Protocol বিভিন্ন ভাষার জন্য অফিসিয়াল SDK প্রদান করে:

- [C# SDK](https://github.com/modelcontextprotocol/csharp-sdk)
- [Java SDK](https://github.com/modelcontextprotocol/java-sdk)
- [TypeScript SDK](https://github.com/modelcontextprotocol/typescript-sdk)
- [Python SDK](https://github.com/modelcontextprotocol/python-sdk)
- [Kotlin SDK](https://github.com/modelcontextprotocol/kotlin-sdk)

## Working with MCP SDKs

এই অংশে MCP বাস্তবায়নের ব্যবহারিক উদাহরণ দেওয়া হয়েছে বিভিন্ন প্রোগ্রামিং ভাষায়। আপনি `samples` ডিরেক্টরিতে ভাষা অনুযায়ী সংগঠিত নমুনা কোড দেখতে পাবেন।

### Available Samples

রিপোজিটরিতে নিম্নলিখিত ভাষাগুলোর [নমুনা বাস্তবায়ন](../../../04-PracticalImplementation/samples) অন্তর্ভুক্ত:

- [C#](./samples/csharp/README.md)
- [Java](./samples/java/containerapp/README.md)
- [TypeScript](./samples/typescript/README.md)
- [JavaScript](./samples/javascript/README.md)
- [Python](./samples/python/README.md)

প্রতিটি নমুনা ঐ নির্দিষ্ট ভাষা ও পরিবেশের জন্য MCP-এর মূল ধারণা এবং বাস্তবায়ন প্যাটার্ন প্রদর্শন করে।

## Core Server Features

MCP সার্ভার নিম্নলিখিত ফিচারগুলোর যেকোনো সমন্বয় বাস্তবায়ন করতে পারে:

### Resources
Resources ব্যবহারকারী বা AI মডেলের জন্য প্রসঙ্গ এবং ডেটা সরবরাহ করে:
- ডকুমেন্ট সংগ্রহস্থল
- জ্ঞানভান্ডার
- গঠনমূলক ডেটা উৎস
- ফাইল সিস্টেম

### Prompts
Prompts হলো ব্যবহারকারীদের জন্য টেমপ্লেট করা বার্তা এবং কর্মপ্রবাহ:
- পূর্বনির্ধারিত কথোপকথনের টেমপ্লেট
- নির্দেশিত ইন্টারঅ্যাকশন প্যাটার্ন
- বিশেষায়িত সংলাপ কাঠামো

### Tools
Tools হলো AI মডেলের জন্য কার্যকরী ফাংশনসমূহ:
- ডেটা প্রক্রিয়াকরণ ইউটিলিটি
- বাহ্যিক API ইন্টিগ্রেশন
- গণনামূলক ক্ষমতা
- অনুসন্ধান কার্যকারিতা

## Sample Implementations: C#

অফিসিয়াল C# SDK রিপোজিটরিতে MCP-এর বিভিন্ন দিক প্রদর্শনকারী বেশ কয়েকটি নমুনা বাস্তবায়ন রয়েছে:

- **Basic MCP Client**: MCP ক্লায়েন্ট তৈরি এবং টুল কল করার সহজ উদাহরণ
- **Basic MCP Server**: বেসিক টুল রেজিস্ট্রেশন সহ একটি মিনিমাল সার্ভার বাস্তবায়ন
- **Advanced MCP Server**: টুল রেজিস্ট্রেশন, অথেনটিকেশন এবং এরর হ্যান্ডলিংসহ পূর্ণাঙ্গ সার্ভার
- **ASP.NET Integration**: ASP.NET Core-র সাথে ইন্টিগ্রেশনের উদাহরণ
- **Tool Implementation Patterns**: বিভিন্ন জটিলতার টুল বাস্তবায়নের প্যাটার্ন

MCP C# SDK এখনও প্রিভিউ অবস্থায় এবং API পরিবর্তিত হতে পারে। SDK আপডেটের সাথে সাথে এই ব্লগ নিয়মিত আপডেট করা হবে।

### Key Features 
- [C# MCP Nuget ModelContextProtocol](https://www.nuget.org/packages/ModelContextProtocol)

- আপনার [প্রথম MCP সার্ভার তৈরি](https://devblogs.microsoft.com/dotnet/build-a-model-context-protocol-mcp-server-in-csharp/) করার গাইড।

সম্পূর্ণ C# বাস্তবায়ন নমুনার জন্য দেখুন [অফিসিয়াল C# SDK নমুনা রিপোজিটরি](https://github.com/modelcontextprotocol/csharp-sdk)

## Sample implementation: Java Implementation

Java SDK MCP বাস্তবায়নের জন্য শক্তিশালী এবং এন্টারপ্রাইজ-গ্রেড ফিচার সরবরাহ করে।

### Key Features

- Spring Framework ইন্টিগ্রেশন
- শক্তিশালী টাইপ সেফটি
- রিয়েক্টিভ প্রোগ্রামিং সাপোর্ট
- ব্যাপক এরর হ্যান্ডলিং

সম্পূর্ণ Java বাস্তবায়ন নমুনার জন্য দেখুন [MCPSample.java](../../../04-PracticalImplementation/samples/java/MCPSample.java) ফাইলটি।

## Sample implementation: JavaScript Implementation

JavaScript SDK MCP বাস্তবায়নের জন্য হালকা ও নমনীয় পদ্ধতি প্রদান করে।

### Key Features

- Node.js এবং ব্রাউজার সাপোর্ট
- Promise-ভিত্তিক API
- Express ও অন্যান্য ফ্রেমওয়ার্কের সাথে সহজ ইন্টিগ্রেশন
- স্ট্রিমিংয়ের জন্য WebSocket সাপোর্ট

সম্পূর্ণ JavaScript বাস্তবায়ন নমুনার জন্য দেখুন [mcp_sample.js](../../../04-PracticalImplementation/samples/javascript/mcp_sample.js) ফাইলটি।

## Sample implementation: Python Implementation

Python SDK MCP বাস্তবায়নের জন্য Pythonic পদ্ধতি এবং চমৎকার ML ফ্রেমওয়ার্ক ইন্টিগ্রেশন সরবরাহ করে।

### Key Features

- Async/await সাপোর্ট asyncio সহ
- Flask এবং FastAPI ইন্টিগ্রেশন
- সহজ টুল রেজিস্ট্রেশন
- জনপ্রিয় ML লাইব্রেরির সাথে নেটিভ ইন্টিগ্রেশন

সম্পূর্ণ Python বাস্তবায়ন নমুনার জন্য দেখুন [mcp_sample.py](../../../04-PracticalImplementation/samples/python/mcp_sample.py) ফাইলটি।

## API management 

Azure API Management MCP সার্ভারগুলোকে সুরক্ষিত করার একটি চমৎকার উপায়। ধারণাটি হলো আপনার MCP সার্ভারের সামনে একটি Azure API Management ইনস্ট্যান্স রাখা, যা নিম্নলিখিত সুবিধাগুলো পরিচালনা করবে:

- রেট লিমিটিং
- টোকেন ম্যানেজমেন্ট
- মনিটরিং
- লোড ব্যালেন্সিং
- সিকিউরিটি

### Azure Sample

এখানে একটি Azure Sample রয়েছে যা ঠিক এই কাজটি করে, অর্থাৎ MCP সার্ভার তৈরি করে এবং Azure API Management দিয়ে সুরক্ষিত করে। ([remote-mcp-apim-functions-python](https://github.com/Azure-Samples/remote-mcp-apim-functions-python))

নিচের ছবিতে দেখুন অথরাইজেশন ফ্লো কীভাবে ঘটে:

![APIM-MCP](https://github.com/Azure-Samples/remote-mcp-apim-functions-python/blob/main/mcp-client-authorization.gif?raw=true) 

উপরের ছবিতে নিম্নলিখিত কাজগুলো ঘটে:

- Microsoft Entra ব্যবহার করে Authentication/Authorization সম্পন্ন হয়।
- Azure API Management একটি গেটওয়ে হিসেবে কাজ করে এবং পলিসি ব্যবহার করে ট্রাফিক পরিচালনা করে।
- Azure Monitor পরবর্তী বিশ্লেষণের জন্য সব রিকোয়েস্ট লগ করে।

#### Authorization flow

অথরাইজেশন ফ্লো আরও বিস্তারিতভাবে দেখা যাক:

![Sequence Diagram](https://github.com/Azure-Samples/remote-mcp-apim-functions-python/blob/main/infra/app/apim-oauth/diagrams/images/mcp-client-auth.png?raw=true)

#### MCP authorization specification

আরো জানুন [MCP Authorization specification](https://modelcontextprotocol.io/specification/2025-03-26/basic/authorization#2-10-third-party-authorization-flow) সম্পর্কে।

## Deploy Remote MCP Server to Azure

আগের আলোচিত নমুনাটি Azure-এ মোতায়েন করার প্রক্রিয়া দেখি:

1. রিপোজিটরি ক্লোন করুন

    ```bash
    git clone https://github.com/Azure-Samples/remote-mcp-apim-functions-python.git
    cd remote-mcp-apim-functions-python
    ```

2. `Microsoft.App` রিসোর্স প্রদানকারী নিবন্ধন করুন:

    `` resource provider.
    * If you are using Azure CLI, run `az provider register --namespace Microsoft.App --wait`.
    * If you are using Azure PowerShell, run `Register-AzResourceProvider -ProviderNamespace Microsoft.App`. Then run `(Get-AzResourceProvider -ProviderNamespace Microsoft.App).RegistrationState` কমান্ডের মাধ্যমে নিবন্ধন সম্পন্ন হয়েছে কিনা কিছুক্ষণ পর চেক করুন।

3. এই [azd](https://aka.ms/azd) কমান্ডটি চালান যাতে API Management সার্ভিস, ফাংশন অ্যাপ (কোডসহ) এবং অন্যান্য প্রয়োজনীয় Azure রিসোর্স provision হয়:

    ```shell
    azd up
    ```

    এই কমান্ডটি Azure-এ সব ক্লাউড রিসোর্স মোতায়েন করবে।

### Testing your server with MCP Inspector

1. **নতুন টার্মিনাল উইন্ডোতে** MCP Inspector ইনস্টল এবং চালান:

    ```shell
    npx @modelcontextprotocol/inspector
    ```

    এরকম একটি ইন্টারফেস দেখতে পাবেন:

    ![Connect to Node inspector](../../../translated_images/connect.141db0b2bd05f096fb1dd91273771fd8b2469d6507656c3b0c9df4b3c5473929.bn.png) 

2. CTRL ক্লিক করে MCP Inspector ওয়েব অ্যাপটি URL থেকে লোড করুন (যেমন http://127.0.0.1:6274/#resources)
3. ট্রান্সপোর্ট টাইপ `SSE`
1. Set the URL to your running API Management SSE endpoint displayed after `azd up` সেট করুন এবং **Connect** করুন:

    ```shell
    https://<apim-servicename-from-azd-output>.azure-api.net/mcp/sse
    ```

5. **List Tools** দেখুন। একটি টুলে ক্লিক করে **Run Tool** করুন।

সব ধাপ সঠিকভাবে সম্পন্ন হলে আপনি MCP সার্ভারের সাথে সংযুক্ত এবং একটি টুল কল করতে সক্ষম হবেন।

## MCP servers for Azure 

[Remote-mcp-functions](https://github.com/Azure-Samples/remote-mcp-functions-dotnet): এই রিপোজিটরি সেট MCP সার্ভার তৈরি ও ডিপ্লয় করার জন্য দ্রুত শুরু করার টেমপ্লেট, যা Azure Functions ব্যবহার করে Python, C# .NET অথবা Node/TypeScript-এ নির্মিত।

নমুনাগুলো একটি পূর্ণাঙ্গ সমাধান প্রদান করে যা ডেভেলপারদের সক্ষম করে:

- স্থানীয়ভাবে তৈরি ও চালানো: লোকাল মেশিনে MCP সার্ভার ডেভেলপ এবং ডিবাগ করা
- Azure-এ ডিপ্লয় করা: সহজে ক্লাউডে azd up কমান্ড দিয়ে ডিপ্লয় করা
- ক্লায়েন্ট থেকে সংযোগ: বিভিন্ন ক্লায়েন্ট থেকে MCP সার্ভারে সংযোগ, যেমন VS Code এর Copilot agent মোড এবং MCP Inspector টুল

### Key Features:

- ডিজাইন থেকে নিরাপত্তা: MCP সার্ভার কী এবং HTTPS ব্যবহার করে সুরক্ষিত
- অথেনটিকেশন অপশন: বিল্ট-ইন অথ এবং/অথবা API Management ব্যবহার করে OAuth সাপোর্ট
- নেটওয়ার্ক আইসোলেশন: Azure Virtual Networks (VNET) ব্যবহার করে নেটওয়ার্ক আলাদা করা
- সার্ভারলেস আর্কিটেকচার: স্কেলেবল, ইভেন্ট-চালিত এক্সিকিউশনের জন্য Azure Functions ব্যবহার
- স্থানীয় উন্নয়ন: ব্যাপক স্থানীয় ডেভেলপমেন্ট এবং ডিবাগিং সাপোর্ট
- সহজ ডিপ্লয়মেন্ট: Azure-এ সরল ও দ্রুত ডিপ্লয়মেন্ট প্রক্রিয়া

রিপোজিটরিতে প্রয়োজনীয় সব কনফিগারেশন ফাইল, সোর্স কোড এবং অবকাঠামো সংজ্ঞা অন্তর্ভুক্ত, যা দ্রুত প্রোডাকশন-রেডি MCP সার্ভার বাস্তবায়নে সাহায্য করে।

- [Azure Remote MCP Functions Python](https://github.com/Azure-Samples/remote-mcp-functions-python) - Azure Functions ব্যবহার করে Python-এ MCP বাস্তবায়নের নমুনা
- [Azure Remote MCP Functions .NET](https://github.com/Azure-Samples/remote-mcp-functions-dotnet) - Azure Functions ব্যবহার করে C# .NET-এ MCP বাস্তবায়নের নমুনা
- [Azure Remote MCP Functions Node/Typescript](https://github.com/Azure-Samples/remote-mcp-functions-typescript) - Azure Functions ব্যবহার করে Node/TypeScript-এ MCP বাস্তবায়নের নমুনা

## Key Takeaways

- MCP SDK গুলো ভাষা-নির্দিষ্ট টুল সরবরাহ করে শক্তিশালী MCP সমাধান তৈরির জন্য
- ডিবাগিং ও টেস্টিং প্রক্রিয়া নির্ভরযোগ্য MCP অ্যাপ্লিকেশনের জন্য অত্যন্ত গুরুত্বপূর্ণ
- পুনরায় ব্যবহারযোগ্য প্রম্পট টেমপ্লেট AI ইন্টারঅ্যাকশনের ধারাবাহিকতা নিশ্চিত করে
- ভালো ডিজাইনকৃত কর্মপ্রবাহ জটিল কাজগুলো বিভিন্ন টুল ব্যবহার করে সংগঠিত করতে সাহায্য করে
- MCP বাস্তবায়নে নিরাপত্তা, কর্মক্ষমতা এবং এরর হ্যান্ডলিং বিবেচনা করা আবশ্যক

## Exercise

আপনার ডোমেইনের একটি বাস্তব সমস্যার জন্য একটি ব্যবহারিক MCP কর্মপ্রবাহ ডিজাইন করুন:

1. এই সমস্যার সমাধানে সহায়ক ৩-৪টি টুল চিহ্নিত করুন
2. একটি কর্মপ্রবাহ চিত্র তৈরি করুন যা দেখায় এই টুলগুলো কীভাবে একসাথে কাজ করবে
3. আপনার পছন্দের ভাষায় একটি টুলের বেসিক সংস্করণ বাস্তবায়ন করুন
4. এমন একটি প্রম্পট টেমপ্লেট তৈরি করুন যা মডেলকে আপনার টুল কার্যকরভাবে ব্যবহার করতে সাহায্য করবে

## Additional Resources


---

Next: [Advanced Topics](../05-AdvancedTopics/README.md)

**অস্বীকৃতি**:  
এই নথিটি AI অনুবাদ সেবা [Co-op Translator](https://github.com/Azure/co-op-translator) ব্যবহার করে অনূদিত হয়েছে। আমরা যথাসাধ্য সঠিকতার চেষ্টা করি, তবে স্বয়ংক্রিয় অনুবাদে ত্রুটি বা অসঙ্গতি থাকতে পারে। মূল নথিটি তার নিজস্ব ভাষায়ই কর্তৃত্বপূর্ণ উৎস হিসেবে বিবেচিত হওয়া উচিত। গুরুত্বপূর্ণ তথ্যের জন্য পেশাদার মানব অনুবাদ গ্রহণ করার পরামর্শ দেওয়া হয়। এই অনুবাদের ব্যবহারের ফলে কোনো ভুল বোঝাবুঝি বা ভুল ব্যাখ্যার জন্য আমরা দায়বদ্ধ নয়।