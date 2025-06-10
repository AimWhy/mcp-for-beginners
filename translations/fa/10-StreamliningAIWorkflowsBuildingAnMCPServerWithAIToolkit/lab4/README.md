<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "f83bc722dc758efffd68667d6a1db470",
  "translation_date": "2025-06-10T06:41:05+00:00",
  "source_file": "10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab4/README.md",
  "language_code": "fa"
}
-->
# 🐙 ماژول ۴: توسعه عملی MCP - سرور کلون گیت‌هاب سفارشی

![Duration](https://img.shields.io/badge/Duration-30_minutes-blue?style=flat-square)
![Difficulty](https://img.shields.io/badge/Difficulty-Intermediate-orange?style=flat-square)
![MCP](https://img.shields.io/badge/MCP-Custom%20Server-purple?style=flat-square&logo=github)
![VS Code](https://img.shields.io/badge/VS%20Code-Integration-blue?style=flat-square&logo=visualstudiocode)
![GitHub Copilot](https://img.shields.io/badge/GitHub%20Copilot-Agent%20Mode-green?style=flat-square&logo=github)

> **⚡ شروع سریع:** در عرض تنها ۳۰ دقیقه یک سرور MCP آماده برای تولید بسازید که کلون کردن مخازن گیت‌هاب و ادغام با VS Code را خودکار می‌کند!

## 🎯 اهداف یادگیری

تا پایان این آزمایشگاه، قادر خواهید بود:

- ✅ ساخت سرور MCP سفارشی برای جریان‌های کاری توسعه واقعی
- ✅ پیاده‌سازی قابلیت کلون کردن مخازن گیت‌هاب از طریق MCP
- ✅ ادغام سرورهای MCP سفارشی با VS Code و Agent Builder
- ✅ استفاده از حالت Agent در GitHub Copilot همراه با ابزارهای سفارشی MCP
- ✅ تست و استقرار سرورهای MCP سفارشی در محیط‌های تولید

## 📋 پیش‌نیازها

- تکمیل آزمایشگاه‌های ۱ تا ۳ (مبانی MCP و توسعه پیشرفته)
- اشتراک GitHub Copilot ([ثبت‌نام رایگان موجود است](https://github.com/github-copilot/signup))
- VS Code همراه با افزونه‌های AI Toolkit و GitHub Copilot
- نصب و پیکربندی Git CLI

## 🏗️ نمای کلی پروژه

### **چالش توسعه دنیای واقعی**
ما به عنوان توسعه‌دهنده‌ها اغلب از گیت‌هاب برای کلون کردن مخازن و باز کردن آن‌ها در VS Code یا VS Code Insiders استفاده می‌کنیم. این فرایند دستی شامل:
1. باز کردن ترمینال/کامند پرامپت
2. رفتن به دایرکتوری مورد نظر
3. اجرای دستور `git clone`
4. باز کردن VS Code در دایرکتوری کلون شده

**راهکار MCP ما این فرایند را به یک دستور هوشمند و واحد تبدیل می‌کند!**

### **آنچه خواهید ساخت**
یک **سرور MCP کلون گیت‌هاب** (`git_mcp_server`) که امکانات زیر را فراهم می‌کند:

| ویژگی | توضیح | مزیت |
|---------|-------------|---------|
| 🔄 **کلون هوشمند مخازن** | کلون مخازن گیت‌هاب با اعتبارسنجی | بررسی خودکار خطاها |
| 📁 **مدیریت هوشمند دایرکتوری** | بررسی و ایجاد ایمن دایرکتوری‌ها | جلوگیری از بازنویسی ناخواسته |
| 🚀 **ادغام چندسکویی با VS Code** | باز کردن پروژه‌ها در VS Code/Insiders | انتقال بدون مشکل در جریان کار |
| 🛡️ **مدیریت قوی خطاها** | رسیدگی به مشکلات شبکه، دسترسی و مسیرها | قابلیت اطمینان برای محیط تولید |

---

## 📖 پیاده‌سازی گام به گام

### گام ۱: ایجاد Agent گیت‌هاب در Agent Builder

1. **Agent Builder را از طریق افزونه AI Toolkit باز کنید**
2. **یک Agent جدید بسازید** با پیکربندی زیر:
   ```
   Agent Name: GitHubAgent
   ```

3. **سرور MCP سفارشی را راه‌اندازی کنید:**
   - به **Tools** → **Add Tool** → **MCP Server** بروید
   - گزینه **"Create A new MCP Server"** را انتخاب کنید
   - قالب **Python** را برای بیشترین انعطاف‌پذیری برگزینید
   - **نام سرور:** `git_mcp_server`

### گام ۲: پیکربندی حالت Agent در GitHub Copilot

1. **GitHub Copilot را در VS Code باز کنید** (Ctrl/Cmd + Shift + P → "GitHub Copilot: Open")
2. **مدل Agent را در رابط Copilot انتخاب کنید**
3. **مدل Claude 3.7 را برای قابلیت‌های پیشرفته استدلال انتخاب کنید**
4. **ادغام MCP را برای دسترسی به ابزار فعال کنید**

> **💡 نکته حرفه‌ای:** مدل Claude 3.7 درک بهتری از جریان‌های کاری توسعه و الگوهای مدیریت خطا ارائه می‌دهد.

### گام ۳: پیاده‌سازی عملکرد اصلی سرور MCP

**از پرامپت دقیق زیر در حالت Agent GitHub Copilot استفاده کنید:**

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

### گام ۴: تست سرور MCP خود

#### ۴a. تست در Agent Builder

1. **پیکربندی دیباگ را برای Agent Builder اجرا کنید**
2. **Agent خود را با این پرامپت سیستمی تنظیم کنید:**

```
SYSTEM_PROMPT:
You are my intelligent coding repository assistant. You help developers efficiently clone GitHub repositories and set up their development environment. Always provide clear feedback about operations and handle errors gracefully.
```

3. **با سناریوهای واقعی کاربر تست کنید:**

```
USER_PROMPT EXAMPLES:

Scenario : Basic Clone and Open
"Clone {Your GitHub Repo link such as https://github.com/kinfey/GHCAgentWorkshop
 } and save to {The global path you specify}, then open it with VS Code Insiders"
```

![Agent Builder Testing](../../../../translated_images/DebugAgent.81d152370c503241b3b39a251b8966f7f739286df19dd57f9147f6402214a012.fa.png)

**نتایج مورد انتظار:**
- ✅ کلون موفق با تایید مسیر
- ✅ اجرای خودکار VS Code
- ✅ پیام‌های خطای واضح برای سناریوهای نامعتبر
- ✅ مدیریت صحیح موارد خاص

#### ۴b. تست در MCP Inspector


![MCP Inspector Testing](../../../../translated_images/DebugInspector.eb5c95f94c69a8ba36944941b9a3588309a3a2fae101ace470ee09bde41d1667.fa.png)

---



**🎉 تبریک!** شما با موفقیت یک سرور MCP عملی و آماده تولید ساختید که چالش‌های واقعی جریان کاری توسعه را حل می‌کند. سرور کلون گیت‌هاب سفارشی شما قدرت MCP را در خودکارسازی و بهبود بهره‌وری توسعه‌دهندگان نشان می‌دهد.

### 🏆 دستاورد کسب شده:
- ✅ **توسعه‌دهنده MCP** - ساخت سرور MCP سفارشی
- ✅ **خودکارساز جریان کاری** - ساده‌سازی فرایندهای توسعه  
- ✅ **کارشناس ادغام** - اتصال چند ابزار توسعه
- ✅ **آماده تولید** - ساخت راه‌حل‌های قابل استقرار

---

## 🎓 پایان کارگاه: مسیر شما با Model Context Protocol

**شرکت‌کننده گرامی کارگاه،**

تبریک می‌گوییم که هر چهار ماژول کارگاه Model Context Protocol را با موفقیت به پایان رساندید! شما از درک مفاهیم پایه AI Toolkit تا ساخت سرورهای MCP آماده تولید که چالش‌های واقعی توسعه را حل می‌کنند، مسیر طولانی‌ای را طی کرده‌اید.

### 🚀 خلاصه مسیر یادگیری شما:

**[ماژول ۱](../lab1/README.md)**: با مبانی AI Toolkit، تست مدل‌ها و ساخت اولین Agent هوش مصنوعی خود شروع کردید.

**[ماژول ۲](../lab2/README.md)**: معماری MCP را یاد گرفتید، Playwright MCP را ادغام کردید و اولین Agent اتوماسیون مرورگر خود را ساختید.

**[ماژول ۳](../lab3/README.md)**: به توسعه سرور MCP سفارشی با سرور Weather MCP پرداختید و ابزارهای اشکال‌زدایی را به خوبی فرا گرفتید.

**[ماژول ۴](../lab4/README.md)**: اکنون همه چیز را به کار گرفتید تا ابزار اتوماسیون جریان کاری مخزن گیت‌هاب عملی بسازید.

### 🌟 مهارت‌هایی که کسب کردید:

- ✅ **اکوسیستم AI Toolkit**: مدل‌ها، Agentها و الگوهای ادغام
- ✅ **معماری MCP**: طراحی کلاینت-سرور، پروتکل‌های انتقال و امنیت
- ✅ **ابزارهای توسعه**: از Playground تا Inspector و استقرار در تولید
- ✅ **توسعه سفارشی**: ساخت، تست و استقرار سرورهای MCP شخصی
- ✅ **کاربردهای عملی**: حل چالش‌های واقعی جریان کاری با هوش مصنوعی

### 🔮 گام‌های بعدی شما:

1. **ساخت سرور MCP خودتان**: این مهارت‌ها را برای خودکارسازی جریان‌های کاری منحصربه‌فردتان به کار بگیرید
2. **پیوستن به جامعه MCP**: آثار خود را به اشتراک بگذارید و از دیگران یاد بگیرید
3. **کاوش در ادغام پیشرفته**: اتصال سرورهای MCP به سیستم‌های سازمانی
4. **مشارکت در متن‌باز**: به بهبود ابزارها و مستندات MCP کمک کنید

به یاد داشته باشید، این کارگاه تنها آغاز راه است. اکوسیستم Model Context Protocol به سرعت در حال پیشرفت است و شما اکنون مجهز به ابزارهای پیشرفته توسعه مبتنی بر هوش مصنوعی هستید.

**از همراهی و تلاش شما برای یادگیری سپاسگزاریم!**

امیدواریم این کارگاه الهام‌بخش ایده‌هایی باشد که روش ساخت و تعامل شما با ابزارهای هوش مصنوعی در مسیر توسعه را دگرگون کند.

**کدنویسی خوش!**

---

**سلب مسئولیت**:  
این سند با استفاده از سرویس ترجمه هوش مصنوعی [Co-op Translator](https://github.com/Azure/co-op-translator) ترجمه شده است. در حالی که ما در تلاش برای دقت هستیم، لطفاً توجه داشته باشید که ترجمه‌های خودکار ممکن است شامل خطاها یا نادرستی‌هایی باشند. سند اصلی به زبان بومی آن باید به عنوان منبع معتبر در نظر گرفته شود. برای اطلاعات حیاتی، ترجمه حرفه‌ای انسانی توصیه می‌شود. ما مسئول هیچ گونه سوءتفاهم یا برداشت نادرستی که از استفاده از این ترجمه ناشی شود، نیستیم.