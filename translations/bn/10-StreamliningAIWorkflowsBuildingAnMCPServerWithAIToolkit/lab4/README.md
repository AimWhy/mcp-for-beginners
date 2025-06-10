<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "f83bc722dc758efffd68667d6a1db470",
  "translation_date": "2025-06-10T06:45:16+00:00",
  "source_file": "10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab4/README.md",
  "language_code": "bn"
}
-->
# 🐙 মডিউল ৪: ব্যবহারিক MCP ডেভেলপমেন্ট - কাস্টম GitHub ক্লোন সার্ভার

![Duration](https://img.shields.io/badge/Duration-30_minutes-blue?style=flat-square)
![Difficulty](https://img.shields.io/badge/Difficulty-Intermediate-orange?style=flat-square)
![MCP](https://img.shields.io/badge/MCP-Custom%20Server-purple?style=flat-square&logo=github)
![VS Code](https://img.shields.io/badge/VS%20Code-Integration-blue?style=flat-square&logo=visualstudiocode)
![GitHub Copilot](https://img.shields.io/badge/GitHub%20Copilot-Agent%20Mode-green?style=flat-square&logo=github)

> **⚡ দ্রুত শুরু:** মাত্র ৩০ মিনিটে একটি প্রোডাকশন-রেডি MCP সার্ভার তৈরি করুন যা GitHub রিপোজিটরি ক্লোনিং এবং VS Code ইন্টিগ্রেশন স্বয়ংক্রিয় করে!

## 🎯 শেখার উদ্দেশ্যসমূহ

এই ল্যাবের শেষে আপনি সক্ষম হবেন:

- ✅ বাস্তব উন্নয়ন কার্যপ্রবাহের জন্য একটি কাস্টম MCP সার্ভার তৈরি করতে
- ✅ MCP এর মাধ্যমে GitHub রিপোজিটরি ক্লোনিং ফাংশনালিটি বাস্তবায়ন করতে
- ✅ কাস্টম MCP সার্ভারগুলোকে VS Code এবং Agent Builder এর সাথে ইন্টিগ্রেট করতে
- ✅ GitHub Copilot Agent Mode ব্যবহার করে কাস্টম MCP টুলস পরিচালনা করতে
- ✅ প্রোডাকশন পরিবেশে কাস্টম MCP সার্ভার পরীক্ষা ও ডিপ্লয় করতে

## 📋 প্রয়োজনীয়তা

- Labs 1-3 সম্পন্ন করা (MCP মৌলিক ও উন্নত ডেভেলপমেন্ট)
- GitHub Copilot সাবস্ক্রিপশন ([ফ্রি সাইনআপ উপলব্ধ](https://github.com/github-copilot/signup))
- VS Code এ AI Toolkit এবং GitHub Copilot এক্সটেনশন ইন্সটল করা
- Git CLI ইন্সটল ও কনফিগার করা

## 🏗️ প্রকল্পের সারাংশ

### **বাস্তব উন্নয়ন চ্যালেঞ্জ**
ডেভেলপার হিসেবে আমরা প্রায়ই GitHub থেকে রিপোজিটরি ক্লোন করে VS Code বা VS Code Insiders এ ওপেন করি। এই ম্যানুয়াল প্রক্রিয়াটি হলো:
1. টার্মিনাল/কমান্ড প্রম্পট খোলা
2. কাঙ্ক্ষিত ডিরেক্টরিতে যাওয়া
3. `git clone` কমান্ড চালানো
4. ক্লোন করা ডিরেক্টরিতে VS Code ওপেন করা

**আমাদের MCP সমাধান এটিকে একটি বুদ্ধিমান একক কমান্ডে পরিণত করেছে!**

### **আপনি যা তৈরি করবেন**
একটি **GitHub Clone MCP Server** (`git_mcp_server`) যা প্রদান করে:

| বৈশিষ্ট্য | বর্ণনা | সুবিধা |
|---------|-------------|---------|
| 🔄 **স্মার্ট রিপোজিটরি ক্লোনিং** | যাচাইকৃত GitHub রিপোজ ক্লোন করা | স্বয়ংক্রিয় ত্রুটি পরীক্ষা |
| 📁 **বুদ্ধিমান ডিরেক্টরি ব্যবস্থাপনা** | ডিরেক্টরি নিরাপদে চেক ও তৈরি করা | ওভাররাইট প্রতিরোধ |
| 🚀 **ক্রস-প্ল্যাটফর্ম VS Code ইন্টিগ্রেশন** | VS Code/Insiders এ প্রকল্প খোলা | নির্বিঘ্ন ওয়ার্কফ্লো ট্রানজিশন |
| 🛡️ **দৃঢ় ত্রুটি হ্যান্ডলিং** | নেটওয়ার্ক, পারমিশন, ও পাথ সমস্যা মোকাবিলা | প্রোডাকশন-রেডি নির্ভরযোগ্যতা |

---

## 📖 ধাপে ধাপে বাস্তবায়ন

### ধাপ ১: Agent Builder-এ GitHub Agent তৈরি করা

1. AI Toolkit এক্সটেনশনের মাধ্যমে **Agent Builder চালু করুন**
2. নিম্নলিখিত কনফিগারেশন সহ **নতুন একটি এজেন্ট তৈরি করুন**:
   ```
   Agent Name: GitHubAgent
   ```

3. **কাস্টম MCP সার্ভার ইনিশিয়ালাইজ করুন:**
   - **Tools** → **Add Tool** → **MCP Server** এ যান
   - **"Create A new MCP Server"** নির্বাচন করুন
   - সর্বোচ্চ নমনীয়তার জন্য **Python টেমপ্লেট** নির্বাচন করুন
   - **Server Name:** `git_mcp_server` দিন

### ধাপ ২: GitHub Copilot Agent Mode কনফিগার করা

1. VS Code এ **GitHub Copilot খুলুন** (Ctrl/Cmd + Shift + P → "GitHub Copilot: Open")
2. Copilot ইন্টারফেসে **Agent Model নির্বাচন করুন**
3. উন্নত রিজনিং ক্ষমতার জন্য **Claude 3.7 মডেল নির্বাচন করুন**
4. টুল অ্যাক্সেসের জন্য **MCP ইন্টিগ্রেশন চালু করুন**

> **💡 প্রো টিপ:** Claude 3.7 উন্নত উন্নয়ন কার্যপ্রবাহ এবং ত্রুটি হ্যান্ডলিং প্যাটার্ন বুঝতে সাহায্য করে।

### ধাপ ৩: MCP সার্ভারের মূল ফাংশনালিটি বাস্তবায়ন

**GitHub Copilot Agent Mode এর সাথে নিম্নলিখিত বিস্তারিত প্রম্পট ব্যবহার করুন:**

```
Create two MCP tools with the following comprehensive requirements:

🔧 TOOL A: clone_repository
Requirements:
- Clone any GitHub repository to a specified local folder
- Return the absolute path of the successfully cloned project
- Implement comprehensive validation:
  ✓ Check if target directory already exists (return error if exists)
  ✓ Validate GitHub URL format (https://github.com/user/repo)
  ✓ Verify git command availability (prompt installation if missing)
  ✓ Handle network connectivity issues
  ✓ Provide clear error messages for all failure scenarios

🚀 TOOL B: open_in_vscode
Requirements:
- Open specified folder in VS Code or VS Code Insiders
- Cross-platform compatibility (Windows/Linux/macOS)
- Use direct application launch (not terminal commands)
- Auto-detect available VS Code installations
- Handle cases where VS Code is not installed
- Provide user-friendly error messages

Additional Requirements:
- Follow MCP 1.9.3 best practices
- Include proper type hints and documentation
- Implement logging for debugging purposes
- Add input validation for all parameters
- Include comprehensive error handling
```

### ধাপ ৪: আপনার MCP সার্ভার পরীক্ষা করা

#### ৪a. Agent Builder-এ পরীক্ষা

1. Agent Builder এর ডিবাগ কনফিগারেশন চালু করুন
2. এই সিস্টেম প্রম্পট দিয়ে আপনার এজেন্ট কনফিগার করুন:

```
SYSTEM_PROMPT:
You are my intelligent coding repository assistant. You help developers efficiently clone GitHub repositories and set up their development environment. Always provide clear feedback about operations and handle errors gracefully.
```

3. বাস্তবসম্মত ব্যবহারকারীর পরিস্থিতিতে পরীক্ষা করুন:

```
USER_PROMPT EXAMPLES:

Scenario : Basic Clone and Open
"Clone {Your GitHub Repo link such as https://github.com/kinfey/GHCAgentWorkshop
 } and save to {The global path you specify}, then open it with VS Code Insiders"
```

![Agent Builder Testing](../../../../translated_images/DebugAgent.81d152370c503241b3b39a251b8966f7f739286df19dd57f9147f6402214a012.bn.png)

**প্রত্যাশিত ফলাফল:**
- ✅ সফল ক্লোনিং এবং পাথ নিশ্চিতকরণ
- ✅ স্বয়ংক্রিয় VS Code লঞ্চ
- ✅ অবৈধ পরিস্থিতির জন্য স্পষ্ট ত্রুটি বার্তা
- ✅ এজ কেসগুলো সঠিকভাবে হ্যান্ডেল করা

#### ৪b. MCP Inspector-এ পরীক্ষা


![MCP Inspector Testing](../../../../translated_images/DebugInspector.eb5c95f94c69a8ba36944941b9a3588309a3a2fae101ace470ee09bde41d1667.bn.png)

---



**🎉 অভিনন্দন!** আপনি সফলভাবে একটি ব্যবহারিক, প্রোডাকশন-রেডি MCP সার্ভার তৈরি করেছেন যা বাস্তব উন্নয়ন কার্যপ্রবাহের সমস্যা সমাধান করে। আপনার কাস্টম GitHub ক্লোন সার্ভার MCP এর মাধ্যমে ডেভেলপার প্রোডাক্টিভিটি স্বয়ংক্রিয়করণ ও উন্নত করার শক্তি প্রদর্শন করে।

### 🏆 অর্জনগুলি:
- ✅ **MCP ডেভেলপার** - কাস্টম MCP সার্ভার তৈরি করেছেন
- ✅ **ওয়ার্কফ্লো অটোমেটর** - উন্নয়ন প্রক্রিয়া সরল করেছেন  
- ✅ **ইন্টিগ্রেশন বিশেষজ্ঞ** - একাধিক ডেভেলপমেন্ট টুল সংযুক্ত করেছেন
- ✅ **প্রোডাকশন রেডি** - ডিপ্লয়যোগ্য সমাধান তৈরি করেছেন

---

## 🎓 ওয়ার্কশপ সমাপ্তি: Model Context Protocol এর সাথে আপনার যাত্রা

**প্রিয় ওয়ার্কশপ অংশগ্রহণকারী,**

Model Context Protocol ওয়ার্কশপের সব চারটি মডিউল সফলভাবে শেষ করার জন্য অভিনন্দন! আপনি AI Toolkit এর মৌলিক ধারণা থেকে শুরু করে বাস্তব প্রোডাকশন-রেডি MCP সার্ভার তৈরি পর্যন্ত অনেক দূর এগিয়েছেন যা বাস্তব উন্নয়ন চ্যালেঞ্জ সমাধান করে।

### 🚀 আপনার শেখার পথের সংক্ষিপ্তসার:

**[Module 1](../lab1/README.md)**: AI Toolkit এর মৌলিক বিষয়াবলী, মডেল পরীক্ষা এবং প্রথম AI এজেন্ট তৈরি শেখা।

**[Module 2](../lab2/README.md)**: MCP আর্কিটেকচার শিখেছেন, Playwright MCP ইন্টিগ্রেট করেছেন, এবং প্রথম ব্রাউজার অটোমেশন এজেন্ট তৈরি করেছেন।

**[Module 3](../lab3/README.md)**: কাস্টম MCP সার্ভার ডেভেলপমেন্টে উন্নতি করেছেন Weather MCP সার্ভার দিয়ে এবং ডিবাগিং টুলস দক্ষতা অর্জন করেছেন।

**[Module 4](../lab4/README.md)**: এখন বাস্তব GitHub রিপোজিটরি ওয়ার্কফ্লো অটোমেশন টুল তৈরি করেছেন।

### 🌟 আপনি যা দক্ষ হয়েছেন:

- ✅ **AI Toolkit ইকোসিস্টেম**: মডেল, এজেন্ট, এবং ইন্টিগ্রেশন প্যাটার্ন
- ✅ **MCP আর্কিটেকচার**: ক্লায়েন্ট-সার্ভার ডিজাইন, ট্রান্সপোর্ট প্রোটোকল, এবং সিকিউরিটি
- ✅ **ডেভেলপার টুলস**: প্লেগ্রাউন্ড থেকে ইন্সপেক্টর ও প্রোডাকশন ডিপ্লয়মেন্ট পর্যন্ত
- ✅ **কাস্টম ডেভেলপমেন্ট**: নিজের MCP সার্ভার তৈরি, পরীক্ষা ও ডিপ্লয় করা
- ✅ **বাস্তব অ্যাপ্লিকেশন**: AI দিয়ে বাস্তব ওয়ার্কফ্লো চ্যালেঞ্জ সমাধান করা

### 🔮 আপনার পরবর্তী পদক্ষেপ:

1. **নিজের MCP সার্ভার তৈরি করুন**: আপনার নিজস্ব ওয়ার্কফ্লো স্বয়ংক্রিয় করতে এই দক্ষতাগুলো প্রয়োগ করুন
2. **MCP কমিউনিটিতে যোগ দিন**: আপনার সৃষ্টি শেয়ার করুন এবং অন্যদের কাছ থেকে শিখুন
3. **উন্নত ইন্টিগ্রেশন অন্বেষণ করুন**: MCP সার্ভারগুলোকে এন্টারপ্রাইজ সিস্টেমের সাথে সংযুক্ত করুন
4. **ওপেন সোর্সে অবদান রাখুন**: MCP টুলিং এবং ডকুমেন্টেশন উন্নত করতে সাহায্য করুন

মনে রাখবেন, এই ওয়ার্কশপ শুধুমাত্র শুরু। Model Context Protocol ইকোসিস্টেম দ্রুত বিকাশমান, এবং এখন আপনি AI-চালিত ডেভেলপমেন্ট টুলসের অগ্রভাগে থাকার জন্য প্রস্তুত।

**শেখার জন্য আপনার অংশগ্রহণ এবং উৎসাহের জন্য ধন্যবাদ!**

আমরা আশা করি এই ওয়ার্কশপ আপনাকে এমন ধারণা দিয়েছে যা আপনার ডেভেলপমেন্ট যাত্রায় AI টুলস নির্মাণ ও ব্যবহারের পদ্ধতি বদলে দেবে।

**শুভ কোডিং!**

---

**দ্রষ্টব্য**:  
এই নথিটি AI অনুবাদ সেবা [Co-op Translator](https://github.com/Azure/co-op-translator) ব্যবহার করে অনূদিত হয়েছে। আমরা যথাসাধ্য সঠিকতার চেষ্টা করি, তবে অনুগ্রহ করে মনে রাখবেন যে স্বয়ংক্রিয় অনুবাদে ভুল বা অসঙ্গতি থাকতে পারে। মূল নথিটি তার নিজস্ব ভাষায়ই কর্তৃত্বপূর্ণ উৎস হিসেবে বিবেচিত হওয়া উচিত। গুরুত্বপূর্ণ তথ্যের জন্য পেশাদার মানব অনুবাদের পরামর্শ দেওয়া হয়। এই অনুবাদের ব্যবহার থেকে উদ্ভূত কোনও ভুল বোঝাবুঝি বা ব্যাখ্যার জন্য আমরা দায়ী নই।