<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "154c00dc3b2c792102e4845c19fbd166",
  "translation_date": "2025-05-20T15:53:03+00:00",
  "source_file": "01-CoreConcepts/README.md",
  "language_code": "fa"
}
-->
# 📖 مفاهیم اصلی MCP: تسلط بر پروتکل مدل کانتکست برای ادغام هوش مصنوعی

پروتکل مدل کانتکست (MCP) چارچوبی قدرتمند و استاندارد است که ارتباط بین مدل‌های زبان بزرگ (LLM) و ابزارها، برنامه‌ها و منابع داده خارجی را بهینه می‌کند. این راهنمای بهینه‌شده برای سئو شما را با مفاهیم اصلی MCP آشنا می‌کند و اطمینان می‌دهد که معماری کلاینت-سرور، اجزای حیاتی، مکانیزم‌های ارتباطی و بهترین روش‌های پیاده‌سازی آن را درک کنید.

## مرور کلی

این درس به بررسی معماری پایه و اجزایی می‌پردازد که اکوسیستم پروتکل مدل کانتکست (MCP) را تشکیل می‌دهند. شما با معماری کلاینت-سرور، اجزای کلیدی و مکانیزم‌های ارتباطی که تعاملات MCP را ممکن می‌سازند، آشنا خواهید شد.

## 👩‍🎓 اهداف کلیدی یادگیری

در پایان این درس، شما قادر خواهید بود:

- معماری کلاینت-سرور MCP را درک کنید.
- نقش‌ها و مسئولیت‌های Hosts، Clients و Servers را شناسایی کنید.
- ویژگی‌های اصلی که MCP را به یک لایه ادغام انعطاف‌پذیر تبدیل می‌کنند تحلیل کنید.
- نحوه جریان اطلاعات در اکوسیستم MCP را بیاموزید.
- از طریق مثال‌های کد در .NET، Java، Python و JavaScript دیدگاه‌های عملی کسب کنید.

## 🔎 معماری MCP: نگاهی عمیق‌تر

اکوسیستم MCP بر پایه مدل کلاینت-سرور ساخته شده است. این ساختار مدولار به برنامه‌های هوش مصنوعی اجازه می‌دهد به طور مؤثر با ابزارها، پایگاه‌های داده، APIها و منابع متنی تعامل داشته باشند. بیایید این معماری را به اجزای اصلی آن تقسیم کنیم.

### 1. Hosts

در پروتکل مدل کانتکست (MCP)، Hosts نقش مهمی به عنوان رابط اصلی دارند که کاربران از طریق آن با پروتکل تعامل می‌کنند. Hosts برنامه‌ها یا محیط‌هایی هستند که ارتباط با سرورهای MCP را برای دسترسی به داده‌ها، ابزارها و پرامپت‌ها آغاز می‌کنند. نمونه‌هایی از Hosts شامل محیط‌های توسعه یکپارچه (IDE) مانند Visual Studio Code، ابزارهای هوش مصنوعی مانند Claude Desktop یا عوامل سفارشی طراحی شده برای وظایف خاص هستند.

**Hosts** برنامه‌های LLM هستند که ارتباط را شروع می‌کنند. آن‌ها:

- مدل‌های هوش مصنوعی را اجرا یا با آن‌ها تعامل دارند تا پاسخ تولید کنند.
- ارتباط با سرورهای MCP را آغاز می‌کنند.
- جریان گفتگو و رابط کاربری را مدیریت می‌کنند.
- کنترل مجوزها و محدودیت‌های امنیتی را بر عهده دارند.
- رضایت کاربر برای اشتراک‌گذاری داده‌ها و اجرای ابزارها را مدیریت می‌کنند.

### 2. Clients

Clients اجزای حیاتی هستند که تعامل بین Hosts و سرورهای MCP را تسهیل می‌کنند. آن‌ها به عنوان واسطه عمل می‌کنند و به Hosts امکان دسترسی و استفاده از قابلیت‌های ارائه شده توسط سرورهای MCP را می‌دهند. Clients نقش مهمی در تضمین ارتباط روان و تبادل داده کارآمد در معماری MCP دارند.

**Clients** اتصال‌دهنده‌هایی درون برنامه Host هستند. آن‌ها:

- درخواست‌ها را به سرورها با پرامپت‌ها/دستورات ارسال می‌کنند.
- قابلیت‌ها را با سرورها مذاکره می‌کنند.
- درخواست‌های اجرای ابزار از مدل‌ها را مدیریت می‌کنند.
- پاسخ‌ها را پردازش و به کاربران نمایش می‌دهند.

### 3. Servers

سرورها مسئول رسیدگی به درخواست‌های Clients MCP و ارائه پاسخ‌های مناسب هستند. آن‌ها عملیات مختلفی مانند بازیابی داده، اجرای ابزار و تولید پرامپت را مدیریت می‌کنند. سرورها اطمینان می‌دهند که ارتباط بین Clients و Hosts کارآمد و قابل اعتماد باشد و یکپارچگی فرایند تعامل حفظ شود.

**Servers** سرویس‌هایی هستند که کانتکست و قابلیت‌ها را فراهم می‌کنند. آن‌ها:

- ویژگی‌های در دسترس (منابع، پرامپت‌ها، ابزارها) را ثبت می‌کنند.
- درخواست‌های اجرای ابزار از کلاینت را دریافت و اجرا می‌کنند.
- اطلاعات متنی برای بهبود پاسخ‌های مدل ارائه می‌دهند.
- خروجی‌ها را به کلاینت باز می‌گردانند.
- در صورت نیاز، وضعیت تعاملات را حفظ می‌کنند.

هر کسی می‌تواند سرور توسعه دهد تا قابلیت‌های مدل را با عملکردهای تخصصی گسترش دهد.

### 4. ویژگی‌های سرور

سرورها در پروتکل مدل کانتکست (MCP) بلوک‌های اصلی‌ای فراهم می‌کنند که تعاملات غنی بین کلاینت‌ها، هاست‌ها و مدل‌های زبانی را ممکن می‌سازند. این ویژگی‌ها برای افزایش قابلیت‌های MCP با ارائه کانتکست ساختاریافته، ابزارها و پرامپت‌ها طراحی شده‌اند.

سرورهای MCP می‌توانند هر یک از ویژگی‌های زیر را ارائه دهند:

#### 📑 منابع

منابع در پروتکل مدل کانتکست (MCP) شامل انواع مختلفی از کانتکست و داده‌ها هستند که کاربران یا مدل‌های هوش مصنوعی می‌توانند از آن‌ها بهره ببرند. این موارد شامل:

- **داده‌های متنی**: اطلاعات و کانتکستی که کاربران یا مدل‌های هوش مصنوعی می‌توانند برای تصمیم‌گیری و اجرای وظایف استفاده کنند.
- **پایگاه‌های دانش و مخازن اسناد**: مجموعه‌هایی از داده‌های ساختاریافته و غیرساختاریافته مانند مقالات، راهنماها و مقالات پژوهشی که بینش‌ها و اطلاعات ارزشمندی ارائه می‌دهند.
- **فایل‌ها و پایگاه‌های داده محلی**: داده‌های ذخیره شده به صورت محلی روی دستگاه‌ها یا در پایگاه‌های داده که برای پردازش و تحلیل قابل دسترسی هستند.
- **APIها و خدمات وب**: رابط‌ها و سرویس‌های خارجی که داده‌ها و قابلیت‌های اضافی ارائه می‌دهند و امکان ادغام با منابع و ابزارهای آنلاین مختلف را فراهم می‌کنند.

مثالی از یک منبع می‌تواند یک طرح پایگاه داده یا فایلی باشد که به این شکل قابل دسترسی است:

```text
file://log.txt
database://schema
```

### 🤖 پرامپت‌ها

پرامپت‌ها در پروتکل مدل کانتکست (MCP) شامل قالب‌ها و الگوهای تعامل از پیش تعریف شده هستند که برای ساده‌سازی جریان‌های کاری کاربران و بهبود ارتباط طراحی شده‌اند. این موارد شامل:

- **پیام‌ها و جریان‌های کاری قالب‌بندی شده**: پیام‌ها و فرآیندهای ساختاربندی شده که کاربران را در انجام وظایف و تعاملات خاص هدایت می‌کنند.
- **الگوهای تعامل از پیش تعریف شده**: توالی‌های استانداردی از اقدامات و پاسخ‌ها که ارتباطی یکنواخت و کارآمد را تسهیل می‌کنند.
- **قالب‌های مکالمه تخصصی**: قالب‌های قابل تنظیم که برای انواع خاصی از مکالمات طراحی شده‌اند و تعاملات مرتبط و متناسب با کانتکست را تضمین می‌کنند.

یک قالب پرامپت می‌تواند به این شکل باشد:

```markdown
Generate a product slogan based on the following {{product}} with the following {{keywords}}
```

#### ⛏️ ابزارها

ابزارها در پروتکل مدل کانتکست (MCP) توابعی هستند که مدل هوش مصنوعی می‌تواند برای انجام وظایف خاص اجرا کند. این ابزارها برای افزایش قابلیت‌های مدل با ارائه عملیات ساختاریافته و قابل اعتماد طراحی شده‌اند. نکات کلیدی عبارتند از:

- **توابعی که مدل AI می‌تواند اجرا کند**: ابزارها توابع قابل اجرایی هستند که مدل می‌تواند برای انجام کارهای مختلف فراخوانی کند.
- **نام و توضیح منحصر به فرد**: هر ابزار نام متمایز و توضیح دقیقی دارد که هدف و عملکرد آن را شرح می‌دهد.
- **پارامترها و خروجی‌ها**: ابزارها پارامترهای مشخصی را می‌پذیرند و خروجی‌های ساختاریافته‌ای بازمی‌گردانند تا نتایج قابل پیش‌بینی و سازگار تضمین شود.
- **توابع مستقل**: ابزارها وظایف مشخصی مانند جستجوی وب، محاسبات و پرس‌وجوهای پایگاه داده را انجام می‌دهند.

نمونه‌ای از یک ابزار می‌تواند به این شکل باشد:

```typescript
server.tool(
  "GetProducts",
  {
    pageSize: z.string().optional(),
    pageCount: z.string().optional()
  }, () => {
    // return results from API
  }
)
```

## ویژگی‌های کلاینت

در پروتکل مدل کانتکست (MCP)، کلاینت‌ها چندین ویژگی کلیدی به سرورها ارائه می‌دهند که عملکرد کلی و تعامل درون پروتکل را بهبود می‌بخشد. یکی از ویژگی‌های قابل توجه Sampling است.

### 👉 Sampling

- **رفتارهای عامل‌محور آغاز شده توسط سرور**: کلاینت‌ها امکان می‌دهند سرورها اقدامات یا رفتارهای خاصی را به صورت خودکار آغاز کنند و قابلیت‌های پویا سیستم را افزایش دهند.
- **تعاملات بازگشتی با LLM**: این ویژگی اجازه می‌دهد تعاملات بازگشتی با مدل‌های زبان بزرگ انجام شود و پردازش‌های پیچیده‌تر و تکراری تسهیل گردد.
- **درخواست تکمیل‌های بیشتر مدل**: سرورها می‌توانند درخواست تکمیل‌های اضافی از مدل کنند تا پاسخ‌ها جامع و مرتبط با کانتکست باشند.

## جریان اطلاعات در MCP

پروتکل مدل کانتکست (MCP) جریان ساختاریافته‌ای از اطلاعات بین هاست‌ها، کلاینت‌ها، سرورها و مدل‌ها تعریف می‌کند. درک این جریان به روشن شدن نحوه پردازش درخواست‌های کاربر و ادغام ابزارها و داده‌های خارجی در پاسخ‌های مدل کمک می‌کند.

- **هاست ارتباط را آغاز می‌کند**  
  برنامه هاست (مانند IDE یا رابط چت) اتصال به سرور MCP را برقرار می‌کند، معمولاً از طریق STDIO، WebSocket یا سایر پروتکل‌های پشتیبانی شده.

- **مذاکره قابلیت‌ها**  
  کلاینت (که در هاست جاسازی شده) و سرور اطلاعات مربوط به ویژگی‌ها، ابزارها، منابع و نسخه‌های پروتکل پشتیبانی شده را تبادل می‌کنند. این اطمینان می‌دهد که هر دو طرف قابلیت‌های موجود برای جلسه را می‌فهمند.

- **درخواست کاربر**  
  کاربر با هاست تعامل می‌کند (مثلاً پرامپت یا دستور وارد می‌کند). هاست این ورودی را جمع‌آوری کرده و برای پردازش به کلاینت می‌فرستد.

- **استفاده از منبع یا ابزار**  
  - کلاینت ممکن است برای غنی‌سازی درک مدل، کانتکست یا منابع اضافی از سرور درخواست کند (مانند فایل‌ها، ورودی‌های پایگاه داده یا مقالات پایگاه دانش).
  - اگر مدل تشخیص دهد که ابزار لازم است (مثلاً برای دریافت داده، انجام محاسبه یا فراخوانی API)، کلاینت درخواست اجرای ابزار را به سرور ارسال می‌کند و نام ابزار و پارامترها را مشخص می‌کند.

- **اجرای سرور**  
  سرور درخواست منبع یا ابزار را دریافت کرده، عملیات لازم را انجام می‌دهد (مانند اجرای تابع، پرس‌وجوی پایگاه داده یا بازیابی فایل) و نتایج را به صورت ساختاریافته به کلاینت بازمی‌گرداند.

- **تولید پاسخ**  
  کلاینت پاسخ‌های سرور (داده‌های منبع، خروجی ابزار و غیره) را در تعامل جاری مدل ادغام می‌کند. مدل از این اطلاعات برای تولید پاسخ جامع و مرتبط با کانتکست استفاده می‌کند.

- **نمایش نتیجه**  
  هاست خروجی نهایی را از کلاینت دریافت کرده و به کاربر نمایش می‌دهد، معمولاً شامل متن تولید شده توسط مدل و هر نتیجه حاصل از اجرای ابزار یا جستجوی منابع است.

این جریان امکان پشتیبانی از برنامه‌های هوش مصنوعی پیشرفته، تعاملی و آگاه به کانتکست را با اتصال بی‌وقفه مدل‌ها به ابزارها و داده‌های خارجی فراهم می‌کند.

## جزئیات پروتکل

MCP (پروتکل مدل کانتکست) بر پایه [JSON-RPC 2.0](https://www.jsonrpc.org/) ساخته شده و فرمت پیام استاندارد و مستقل از زبان را برای ارتباط بین هاست‌ها، کلاینت‌ها و سرورها فراهم می‌کند. این پایه تعاملات قابل اعتماد، ساختاریافته و قابل توسعه را در پلتفرم‌ها و زبان‌های برنامه‌نویسی مختلف ممکن می‌سازد.

### ویژگی‌های کلیدی پروتکل

MCP با افزودن قراردادهای اضافی برای فراخوانی ابزار، دسترسی به منابع و مدیریت پرامپت، JSON-RPC 2.0 را توسعه می‌دهد. این پروتکل از چندین لایه انتقال (STDIO، WebSocket، SSE) پشتیبانی می‌کند و ارتباط امن، قابل توسعه و مستقل از زبان بین اجزا را ممکن می‌سازد.

#### 🧢 پروتکل پایه

- **فرمت پیام JSON-RPC**: تمام درخواست‌ها و پاسخ‌ها مطابق مشخصات JSON-RPC 2.0 هستند که ساختار یکنواختی برای فراخوانی متدها، پارامترها، نتایج و مدیریت خطا تضمین می‌کند.
- **اتصالات حالت‌دار**: جلسات MCP حالت را در چندین درخواست حفظ می‌کنند و از گفتگوهای پیوسته، انباشت کانتکست و مدیریت منابع پشتیبانی می‌کنند.
- **مذاکره قابلیت‌ها**: در زمان برقراری اتصال، کلاینت‌ها و سرورها اطلاعات مربوط به ویژگی‌های پشتیبانی شده، نسخه‌های پروتکل، ابزارها و منابع را تبادل می‌کنند تا هر دو طرف قابلیت‌های یکدیگر را درک کنند و متناسب شوند.

#### ➕ ابزارهای اضافی

در ادامه چند ابزار و توسعه پروتکل که MCP برای بهبود تجربه توسعه‌دهنده و سناریوهای پیشرفته فراهم می‌کند آمده است:

- **گزینه‌های پیکربندی**: MCP اجازه پیکربندی پویا پارامترهای جلسه مانند مجوزهای ابزار، دسترسی به منابع و تنظیمات مدل را می‌دهد که برای هر تعامل قابل تنظیم است.
- **ردیابی پیشرفت**: عملیات طولانی می‌توانند به‌روزرسانی‌های پیشرفت را گزارش دهند و رابط‌های کاربری پاسخگو و تجربه کاربری بهتر در وظایف پیچیده فراهم کنند.
- **لغو درخواست**: کلاینت‌ها می‌توانند درخواست‌های در حال اجرا را لغو کنند تا کاربران بتوانند عملیات غیرضروری یا طولانی را متوقف کنند.
- **گزارش خطا**: پیام‌ها و کدهای خطای استاندارد به تشخیص مشکلات، مدیریت شکست‌ها و ارائه بازخورد قابل اقدام به کاربران و توسعه‌دهندگان کمک می‌کند.
- **ثبت لاگ**: کلاینت‌ها و سرورها می‌توانند لاگ‌های ساختاریافته برای حسابرسی، اشکال‌زدایی و نظارت بر تعاملات پروتکل ارسال کنند.

با استفاده از این ویژگی‌ها، MCP ارتباطی قوی، امن و انعطاف‌پذیر بین مدل‌های زبانی و ابزارها یا منابع داده خارجی تضمین می‌کند.

### 🔐 ملاحظات امنیتی

پیاده‌سازی‌های MCP باید به چند اصل کلیدی امنیتی پایبند باشند تا تعاملات ایمن و قابل اعتماد باشند:

- **رضایت و کنترل کاربر**: کاربران باید قبل از دسترسی به داده‌ها یا انجام عملیات، رضایت صریح دهند. آن‌ها باید کنترل واضحی بر داده‌های به اشتراک گذاشته شده و اقدامات مجاز داشته باشند که توسط رابط‌های کاربری شهودی برای مرور و تأیید فعالیت‌ها پشتیبانی می‌شود.

- **حریم خصوصی داده‌ها**: داده‌های کاربران فقط با رضایت صریح افشا شوند و باید توسط کنترل‌های دسترسی مناسب محافظت شوند. پیاده‌سازی‌های MCP باید از انتقال غیرمجاز داده جلوگیری کنند و حفظ حریم خصوصی را در تمام تعاملات تضمین نمایند.

- **ایمنی ابزارها**: قبل از فراخوانی هر ابزار، رضایت صریح کاربر لازم است. کاربران باید عملکرد هر ابزار را به خوبی درک کنند و مرزهای امنیتی محکمی برای جلوگیری از اجرای ناخواسته یا ناایمن ابزارها اعمال شود.

با رعایت این اصول، MCP اطمینان می‌دهد که اعتماد، حریم خصوصی و ایمنی کاربران در تمام تعاملات پروتکل حفظ شود.

## مثال‌های کد: اجزای کلیدی

در ادامه مثال‌هایی از کد در چند زبان برنامه‌نویسی محبوب ارائه شده است که نشان می‌دهد چگونه اجزای کلیدی سرور MCP و ابزارها را پیاده‌سازی کنیم.

### مثال .NET: ایجاد یک سرور ساده MCP با ابزارها

در این مثال عملی در .NET نشان داده شده که چگونه یک سرور ساده MCP با ابزارهای سفارشی پیاده‌سازی کنیم. این مثال نحوه تعریف و ثبت ابزارها، مدیریت درخواست‌ها و اتصال سرور با استفاده از پروتکل مدل کانتکست را نشان می‌دهد.

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

### مثال Java: اجزای سرور MCP

این مثال همان سرور MCP و ثبت ابزار را که در مثال .NET بالا بود، نشان می‌دهد اما با زبان Java پیاده‌سازی شده است.

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

### مثال Python: ساخت سرور MCP

در این مثال نشان داده شده که چگونه یک سرور MCP در Python ساخته شود. همچنین دو روش مختلف برای ایجاد ابزارها معرفی شده است.

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

### مثال JavaScript: ایجاد سرور MCP

این مثال ایجاد سرور MCP در JavaScript و نحوه ثبت دو ابزار مرتبط با آب و هوا را نشان می‌دهد.

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

این مثال JavaScript نشان می‌دهد چگونه یک کلاینت MCP ایجاد کنیم که به سرور متصل شده، پرامپتی ارسال می‌کند و پاسخ از جمله هر فراخوانی ابزاری را پردازش می‌کند.

## امنیت و مجوزدهی

MCP شامل چندین مفهوم و مکانیزم داخلی برای مدیریت امنیت و مجوزدهی در سراسر پروتکل است:

1. **کنترل مجوز ابزار**:  
  کلاینت‌ها می‌توانند مشخص کنند که مدل در طول جلسه مجاز به استفاده از کدام ابزارها است. این تضمین می‌کند که فقط ابزارهای صریحاً مجاز قابل دسترسی هستند و ریسک عملیات ناخواسته یا ناایمن کاهش می‌یابد. مجوزها می‌توانند به صورت پویا بر اساس ترجیحات کاربر، سیاست‌های سازمانی یا کانتکست تعامل تنظیم شوند.

2. **احراز هویت**:  
  سرورها می‌توانند پیش از اعطای دسترسی به ابزارها

**سلب مسئولیت**:  
این سند با استفاده از سرویس ترجمه هوش مصنوعی [Co-op Translator](https://github.com/Azure/co-op-translator) ترجمه شده است. در حالی که ما برای دقت تلاش می‌کنیم، لطفاً توجه داشته باشید که ترجمه‌های خودکار ممکن است حاوی خطاها یا نادرستی‌هایی باشند. سند اصلی به زبان مادری خود باید به عنوان منبع معتبر در نظر گرفته شود. برای اطلاعات حیاتی، ترجمه حرفه‌ای انسانی توصیه می‌شود. ما مسئول هیچگونه سوءتفاهم یا برداشت نادرستی که از استفاده این ترجمه ناشی شود، نیستیم.