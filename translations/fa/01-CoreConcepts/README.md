<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "4bf553c18e7e226c3d76ab0cde627d26",
  "translation_date": "2025-05-20T20:26:05+00:00",
  "source_file": "01-CoreConcepts/README.md",
  "language_code": "fa"
}
-->
# 📖 مفاهیم اصلی MCP: تسلط بر پروتکل زمینه مدل برای یکپارچه‌سازی هوش مصنوعی

پروتکل زمینه مدل (MCP) چارچوبی قدرتمند و استاندارد شده است که ارتباط بین مدل‌های زبانی بزرگ (LLM) و ابزارها، برنامه‌ها و منابع داده خارجی را بهینه می‌کند. این راهنمای بهینه‌شده برای سئو، شما را با مفاهیم اصلی MCP آشنا می‌کند و اطمینان می‌دهد که معماری کلاینت-سرور، اجزای حیاتی، مکانیزم‌های ارتباطی و بهترین روش‌های پیاده‌سازی آن را درک کنید.

## مرور کلی

این درس به معماری بنیادی و اجزایی می‌پردازد که اکوسیستم پروتکل زمینه مدل (MCP) را تشکیل می‌دهند. شما با معماری کلاینت-سرور، اجزای کلیدی و مکانیزم‌های ارتباطی که تعاملات MCP را ممکن می‌سازند، آشنا خواهید شد.

## 👩‍🎓 اهداف کلیدی یادگیری

در پایان این درس، شما قادر خواهید بود:

- معماری کلاینت-سرور MCP را درک کنید.
- نقش‌ها و مسئولیت‌های Hosts، Clients و Servers را شناسایی کنید.
- ویژگی‌های اصلی که MCP را به یک لایه یکپارچه‌سازی انعطاف‌پذیر تبدیل می‌کند، تحلیل کنید.
- نحوه جریان اطلاعات در اکوسیستم MCP را بیاموزید.
- از طریق مثال‌های کد در .NET، Java، Python و JavaScript، دید عملی کسب کنید.

## 🔎 معماری MCP: نگاهی عمیق‌تر

اکوسیستم MCP بر اساس مدل کلاینت-سرور ساخته شده است. این ساختار مدولار به برنامه‌های هوش مصنوعی اجازه می‌دهد تا به‌طور مؤثر با ابزارها، پایگاه‌های داده، APIها و منابع زمینه‌ای تعامل داشته باشند. بیایید این معماری را به اجزای اصلی آن تقسیم کنیم.

### ۱. Hosts

در پروتکل زمینه مدل (MCP)، Hosts نقش کلیدی به عنوان رابط اصلی دارند که کاربران از طریق آن با پروتکل تعامل می‌کنند. Hosts برنامه‌ها یا محیط‌هایی هستند که اتصال به سرورهای MCP را برای دسترسی به داده‌ها، ابزارها و درخواست‌ها آغاز می‌کنند. مثال‌هایی از Hosts شامل محیط‌های توسعه یکپارچه (IDE) مانند Visual Studio Code، ابزارهای هوش مصنوعی مانند Claude Desktop، یا عامل‌های سفارشی ساخته شده برای وظایف خاص هستند.

**Hosts** برنامه‌های LLM هستند که اتصال را شروع می‌کنند. آنها:

- مدل‌های هوش مصنوعی را اجرا یا با آنها تعامل می‌کنند تا پاسخ تولید کنند.
- اتصال به سرورهای MCP را آغاز می‌کنند.
- جریان گفتگو و رابط کاربری را مدیریت می‌کنند.
- کنترل مجوزها و محدودیت‌های امنیتی را بر عهده دارند.
- رضایت کاربر برای اشتراک داده‌ها و اجرای ابزارها را مدیریت می‌کنند.

### ۲. Clients

Clients اجزای حیاتی هستند که تعامل بین Hosts و سرورهای MCP را تسهیل می‌کنند. Clients به عنوان واسطه عمل می‌کنند و به Hosts امکان می‌دهند تا از قابلیت‌های ارائه شده توسط سرورهای MCP استفاده کنند. آنها نقش مهمی در اطمینان از ارتباط روان و تبادل داده مؤثر در معماری MCP دارند.

**Clients** کانکتورهایی درون برنامه میزبان هستند. آنها:

- درخواست‌ها را با درخواست‌ها/دستورالعمل‌ها به سرورها ارسال می‌کنند.
- قابلیت‌ها را با سرورها مذاکره می‌کنند.
- درخواست‌های اجرای ابزار از مدل‌ها را مدیریت می‌کنند.
- پاسخ‌ها را پردازش و به کاربران نمایش می‌دهند.

### ۳. Servers

سرورها مسئول رسیدگی به درخواست‌های کلاینت‌های MCP و ارائه پاسخ‌های مناسب هستند. آنها عملیات مختلفی مانند بازیابی داده‌ها، اجرای ابزار و تولید درخواست‌ها را مدیریت می‌کنند. سرورها اطمینان می‌دهند که ارتباط بین کلاینت‌ها و Hosts به صورت کارآمد و قابل اعتماد انجام شود و تمامیت فرآیند تعامل حفظ گردد.

**Servers** خدماتی هستند که زمینه و قابلیت‌ها را فراهم می‌کنند. آنها:

- ویژگی‌های در دسترس (منابع، درخواست‌ها، ابزارها) را ثبت می‌کنند.
- تماس‌های ابزار از کلاینت را دریافت و اجرا می‌کنند.
- اطلاعات زمینه‌ای برای بهبود پاسخ‌های مدل فراهم می‌کنند.
- خروجی‌ها را به کلاینت بازمی‌گردانند.
- در صورت نیاز، وضعیت تعاملات را حفظ می‌کنند.

سرورها می‌توانند توسط هر کسی توسعه یابند تا قابلیت‌های مدل را با عملکردهای تخصصی گسترش دهند.

### ۴. ویژگی‌های سرور

سرورها در پروتکل زمینه مدل (MCP) بلوک‌های ساختمانی بنیادی را ارائه می‌دهند که تعاملات غنی بین کلاینت‌ها، میزبان‌ها و مدل‌های زبانی را ممکن می‌سازند. این ویژگی‌ها برای ارتقاء قابلیت‌های MCP با ارائه زمینه ساختاریافته، ابزارها و درخواست‌ها طراحی شده‌اند.

سرورهای MCP می‌توانند هر یک از ویژگی‌های زیر را ارائه دهند:

#### 📑 منابع

منابع در پروتکل زمینه مدل (MCP) شامل انواع مختلفی از زمینه و داده‌ها هستند که کاربران یا مدل‌های هوش مصنوعی می‌توانند از آنها استفاده کنند. این موارد عبارتند از:

- **داده‌های زمینه‌ای**: اطلاعات و زمینه‌ای که کاربران یا مدل‌های هوش مصنوعی می‌توانند برای تصمیم‌گیری و اجرای وظایف از آن بهره ببرند.
- **پایگاه‌های دانش و مخازن اسناد**: مجموعه‌ای از داده‌های ساختاریافته و غیرساختاریافته مانند مقالات، راهنماها و مقالات پژوهشی که بینش و اطلاعات ارزشمندی ارائه می‌دهند.
- **فایل‌ها و پایگاه‌های داده محلی**: داده‌هایی که به صورت محلی روی دستگاه‌ها یا در پایگاه‌های داده ذخیره شده‌اند و برای پردازش و تحلیل در دسترس هستند.
- **APIها و خدمات وب**: رابط‌ها و خدمات خارجی که داده‌ها و قابلیت‌های اضافی ارائه می‌دهند و امکان یکپارچه‌سازی با منابع و ابزارهای آنلاین مختلف را فراهم می‌کنند.

مثالی از یک منبع می‌تواند طرح یک پایگاه داده یا فایلی باشد که به این شکل قابل دسترسی است:

```text
file://log.txt
database://schema
```

### 🤖 درخواست‌ها (Prompts)

درخواست‌ها در پروتکل زمینه مدل (MCP) شامل قالب‌ها و الگوهای تعامل از پیش تعریف شده‌ای هستند که به منظور ساده‌سازی گردش کار کاربران و بهبود ارتباط طراحی شده‌اند. این موارد شامل:

- **پیام‌ها و گردش‌های کاری قالب‌بندی شده**: پیام‌ها و فرآیندهای از پیش ساختار یافته که کاربران را در انجام وظایف و تعاملات خاص راهنمایی می‌کنند.
- **الگوهای تعامل از پیش تعریف شده**: توالی‌های استاندارد از اقدامات و پاسخ‌ها که ارتباطی سازگار و مؤثر را تسهیل می‌کنند.
- **قالب‌های مکالمه تخصصی**: قالب‌های قابل تنظیم که برای انواع خاصی از مکالمات طراحی شده‌اند تا تعاملات مرتبط و متناسب با زمینه را تضمین کنند.

یک قالب درخواست می‌تواند به این شکل باشد:

```markdown
Generate a product slogan based on the following {{product}} with the following {{keywords}}
```

#### ⛏️ ابزارها

ابزارها در پروتکل زمینه مدل (MCP) توابعی هستند که مدل هوش مصنوعی می‌تواند برای انجام وظایف خاص اجرا کند. این ابزارها برای افزایش قابلیت‌های مدل هوش مصنوعی با ارائه عملیات ساختاریافته و قابل اعتماد طراحی شده‌اند. نکات کلیدی عبارتند از:

- **توابعی که مدل هوش مصنوعی می‌تواند اجرا کند**: ابزارها توابع اجرایی هستند که مدل می‌تواند برای انجام وظایف مختلف فراخوانی کند.
- **نام و توضیح منحصر به فرد**: هر ابزار نام متمایز و توضیح دقیقی دارد که هدف و عملکرد آن را شرح می‌دهد.
- **پارامترها و خروجی‌ها**: ابزارها پارامترهای مشخصی را می‌پذیرند و خروجی‌های ساختاریافته‌ای بازمی‌گردانند که نتایج سازگار و قابل پیش‌بینی را تضمین می‌کند.
- **توابع مستقل**: ابزارها وظایف مستقل مانند جستجوی وب، محاسبات و پرس‌وجوهای پایگاه داده را انجام می‌دهند.

مثالی از یک ابزار می‌تواند به این شکل باشد:

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

در پروتکل زمینه مدل (MCP)، کلاینت‌ها چندین ویژگی کلیدی به سرورها ارائه می‌دهند که عملکرد کلی و تعامل درون پروتکل را بهبود می‌بخشد. یکی از ویژگی‌های قابل توجه، Sampling است.

### 👉 Sampling

- **رفتارهای عامل‌محور آغاز شده توسط سرور**: کلاینت‌ها به سرورها اجازه می‌دهند تا اقدامات یا رفتارهای خاصی را به صورت خودکار آغاز کنند و قابلیت‌های دینامیک سیستم را افزایش دهند.
- **تعاملات بازگشتی با LLM**: این ویژگی امکان تعاملات بازگشتی با مدل‌های زبانی بزرگ را فراهم می‌کند که پردازش‌های پیچیده‌تر و تکراری را ممکن می‌سازد.
- **درخواست تکمیل‌های اضافی مدل**: سرورها می‌توانند درخواست تکمیل‌های بیشتری از مدل داشته باشند تا پاسخ‌ها جامع‌تر و متناسب با زمینه باشند.

## جریان اطلاعات در MCP

پروتکل زمینه مدل (MCP) جریان ساختاریافته‌ای از اطلاعات بین میزبان‌ها، کلاینت‌ها، سرورها و مدل‌ها تعریف می‌کند. درک این جریان به روشن شدن چگونگی پردازش درخواست‌های کاربر و یکپارچه‌سازی ابزارها و داده‌های خارجی در پاسخ‌های مدل کمک می‌کند.

- **میزبان اتصال را آغاز می‌کند**  
  برنامه میزبان (مانند IDE یا رابط چت) اتصال به سرور MCP را برقرار می‌کند، معمولاً از طریق STDIO، WebSocket یا دیگر روش‌های پشتیبانی شده.

- **مذاکره قابلیت‌ها**  
  کلاینت (که در میزبان جاسازی شده) و سرور اطلاعات مربوط به ویژگی‌ها، ابزارها، منابع و نسخه‌های پروتکل را مبادله می‌کنند. این اطمینان حاصل می‌کند که هر دو طرف قابلیت‌های موجود برای جلسه را می‌فهمند.

- **درخواست کاربر**  
  کاربر با میزبان تعامل می‌کند (مثلاً درخواست یا فرمانی وارد می‌کند). میزبان این ورودی را جمع‌آوری و به کلاینت برای پردازش ارسال می‌کند.

- **استفاده از منبع یا ابزار**  
  - کلاینت ممکن است درخواست زمینه یا منابع اضافی از سرور (مانند فایل‌ها، ورودی‌های پایگاه داده یا مقالات پایگاه دانش) برای غنی‌سازی درک مدل داشته باشد.
  - اگر مدل تشخیص دهد که به ابزاری نیاز است (مثلاً برای دریافت داده، انجام محاسبه یا فراخوانی API)، کلاینت درخواست فراخوانی ابزار را به سرور ارسال می‌کند و نام ابزار و پارامترها را مشخص می‌کند.

- **اجرای سرور**  
  سرور درخواست منبع یا ابزار را دریافت کرده، عملیات لازم را اجرا می‌کند (مانند اجرای تابع، پرس‌وجوی پایگاه داده یا بازیابی فایل) و نتایج را در قالب ساختاریافته به کلاینت بازمی‌گرداند.

- **تولید پاسخ**  
  کلاینت پاسخ‌های سرور (داده‌های منبع، خروجی‌های ابزار و غیره) را در تعامل جاری مدل ادغام می‌کند. مدل از این اطلاعات برای تولید پاسخ جامع و متناسب با زمینه استفاده می‌کند.

- **ارائه نتیجه**  
  میزبان خروجی نهایی را از کلاینت دریافت و به کاربر ارائه می‌دهد، معمولاً شامل متن تولید شده توسط مدل و هر نتیجه‌ای از اجرای ابزارها یا جستجوی منابع است.

این جریان به MCP امکان می‌دهد برنامه‌های هوش مصنوعی پیشرفته، تعاملی و آگاه از زمینه را با اتصال بی‌وقفه مدل‌ها به ابزارها و منابع داده خارجی پشتیبانی کند.

## جزئیات پروتکل

MCP (پروتکل زمینه مدل) بر پایه [JSON-RPC 2.0](https://www.jsonrpc.org/) ساخته شده است و قالب پیام استاندارد و زبان‌ناپذیری برای ارتباط بین میزبان‌ها، کلاینت‌ها و سرورها فراهم می‌کند. این پایه تعاملات قابل اعتماد، ساختاریافته و قابل توسعه را در پلتفرم‌ها و زبان‌های برنامه‌نویسی مختلف ممکن می‌سازد.

### ویژگی‌های کلیدی پروتکل

MCP با افزودن قراردادهای اضافی برای فراخوانی ابزار، دسترسی به منابع و مدیریت درخواست‌ها، JSON-RPC 2.0 را گسترش می‌دهد. این پروتکل از چندین لایه انتقال (STDIO، WebSocket، SSE) پشتیبانی کرده و ارتباط امن، قابل توسعه و زبان‌ناپذیر بین اجزا را ممکن می‌سازد.

#### 🧢 پروتکل پایه

- **قالب پیام JSON-RPC**: تمام درخواست‌ها و پاسخ‌ها از مشخصات JSON-RPC 2.0 استفاده می‌کنند که ساختار یکنواختی برای فراخوانی متدها، پارامترها، نتایج و مدیریت خطاها فراهم می‌آورد.
- **اتصالات حالت‌دار**: جلسات MCP وضعیت را در چندین درخواست حفظ می‌کنند و از گفتگوهای مستمر، انباشت زمینه و مدیریت منابع پشتیبانی می‌کنند.
- **مذاکره قابلیت‌ها**: در زمان برقراری اتصال، کلاینت‌ها و سرورها اطلاعاتی درباره ویژگی‌های پشتیبانی شده، نسخه‌های پروتکل، ابزارها و منابع را مبادله می‌کنند تا هر دو طرف قابلیت‌های یکدیگر را درک کرده و بتوانند تطبیق یابند.

#### ➕ امکانات اضافی

در ادامه چند قابلیت و توسعه پروتکل که MCP برای بهبود تجربه توسعه‌دهنده و پشتیبانی از سناریوهای پیشرفته ارائه می‌دهد:

- **گزینه‌های پیکربندی**: MCP امکان پیکربندی پویا پارامترهای جلسه، مانند مجوزهای ابزار، دسترسی به منابع و تنظیمات مدل را متناسب با هر تعامل فراهم می‌کند.
- **ردیابی پیشرفت**: عملیات‌های طولانی می‌توانند به‌روزرسانی‌های پیشرفت را گزارش دهند و رابط‌های کاربری پاسخگو و تجربه بهتر کاربر را در طول وظایف پیچیده ممکن سازند.
- **لغو درخواست**: کلاینت‌ها می‌توانند درخواست‌های در حال اجرا را لغو کنند تا کاربران بتوانند عملیات غیرضروری یا طولانی را متوقف کنند.
- **گزارش خطا**: پیام‌ها و کدهای خطای استاندارد شده به تشخیص مشکلات، مدیریت شکست‌ها به صورت ملایم و ارائه بازخورد عملی به کاربران و توسعه‌دهندگان کمک می‌کنند.
- **ثبت وقایع (Logging)**: کلاینت‌ها و سرورها می‌توانند لاگ‌های ساختاریافته برای حسابرسی، اشکال‌زدایی و نظارت بر تعاملات پروتکل تولید کنند.

با بهره‌گیری از این ویژگی‌ها، MCP ارتباطی مقاوم، امن و انعطاف‌پذیر بین مدل‌های زبانی و ابزارها یا منابع داده خارجی فراهم می‌کند.

### 🔐 ملاحظات امنیتی

پیاده‌سازی‌های MCP باید به چند اصل کلیدی امنیتی پایبند باشند تا تعاملات ایمن و قابل اعتماد تضمین شود:

- **رضایت و کنترل کاربر**: کاربران باید پیش از دسترسی به هر داده یا انجام هر عملی رضایت صریح دهند. آنها باید کنترل واضحی بر داده‌های به اشتراک گذاشته شده و اقداماتی که مجاز هستند داشته باشند، که این با رابط‌های کاربری شهودی برای بازبینی و تأیید فعالیت‌ها پشتیبانی می‌شود.

- **حریم خصوصی داده‌ها**: داده‌های کاربر تنها با رضایت صریح افشا می‌شوند و باید توسط کنترل‌های دسترسی مناسب محافظت گردند. پیاده‌سازی‌های MCP باید از انتقال غیرمجاز داده جلوگیری کرده و حفظ حریم خصوصی را در تمامی تعاملات تضمین کنند.

- **ایمنی ابزارها**: پیش از فراخوانی هر ابزاری، رضایت صریح کاربر لازم است. کاربران باید درک روشنی از عملکرد هر ابزار داشته باشند و مرزهای امنیتی قوی برای جلوگیری از اجرای ناخواسته یا ناامن ابزارها اعمال شود.

با رعایت این اصول، MCP اطمینان می‌دهد که اعتماد، حریم خصوصی و ایمنی کاربران در تمامی تعاملات پروتکل حفظ شود.

## مثال‌های کد: اجزای کلیدی

در ادامه مثال‌هایی از کد در چند زبان برنامه‌نویسی محبوب ارائه شده که نحوه پیاده‌سازی اجزای کلیدی سرور MCP و ابزارها را نشان می‌دهد.

### مثال .NET: ایجاد یک سرور ساده MCP با ابزارها

در این مثال عملی .NET، نحوه پیاده‌سازی یک سرور ساده MCP با ابزارهای سفارشی نشان داده شده است. این مثال نحوه تعریف و ثبت ابزارها، مدیریت درخواست‌ها و اتصال سرور با استفاده از پروتکل زمینه مدل را نمایش می‌دهد.

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

این مثال همان سرور MCP و ثبت ابزار را مانند مثال .NET بالا نشان می‌دهد، اما به زبان Java پیاده‌سازی شده است.

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

### مثال Python: ساخت یک سرور MCP

در این مثال نشان داده شده چگونه یک سرور MCP را در Python بسازیم. همچنین دو روش مختلف برای ایجاد ابزارها ارائه شده است.

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

### مثال JavaScript: ایجاد یک سرور MCP

این مثال ایجاد سرور MCP را در JavaScript نشان می‌دهد و نحوه ثبت دو ابزار مرتبط با آب و هوا را توضیح می‌دهد.

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

این مثال JavaScript نشان می‌دهد چگونه یک کلاینت MCP ایجاد کنیم که به سرور متصل شده، درخواست ارسال می‌کند و پاسخ را از جمله هر فراخوانی ابزاری که انجام شده است، پردازش می‌کند.

## امنیت و مجوزها

MCP چندین مفهوم و مکانیزم داخلی برای مدیریت امنیت و مجوزها در سراسر پروتکل ارائه می‌دهد:

1. **کنترل مجوز ابزار**:  
  کلاینت‌ها می‌توانند مشخص کنند که مدل در طول جلسه مجاز به استفاده از کدام ابزارها است. این اطمینان حاصل می‌کند که فقط ابزارهای صریحاً مجاز در دسترس هستند و خطر عملیات ناخواسته یا ناامن کاهش می‌یابد. مجوزها می‌توانند به صورت پویا بر اساس ترجیحات کاربر، سیاست‌های سازمانی یا زمینه تعامل تنظیم شوند.

2. **احراز هویت**:  
  سرورها می‌توانند پیش از دسترسی

**سلب مسئولیت**:  
این سند با استفاده از سرویس ترجمه هوش مصنوعی [Co-op Translator](https://github.com/Azure/co-op-translator) ترجمه شده است. در حالی که ما در تلاش برای دقت هستیم، لطفاً توجه داشته باشید که ترجمه‌های خودکار ممکن است حاوی اشتباهات یا نواقصی باشند. سند اصلی به زبان بومی آن باید به عنوان منبع معتبر در نظر گرفته شود. برای اطلاعات حیاتی، ترجمه حرفه‌ای انسانی توصیه می‌شود. ما در قبال هرگونه سوءتفاهم یا برداشت نادرست ناشی از استفاده از این ترجمه مسئولیتی نداریم.