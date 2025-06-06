<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "f00defb149ee1ac4a799e44a9783c7fc",
  "translation_date": "2025-06-06T17:59:46+00:00",
  "source_file": "01-CoreConcepts/README.md",
  "language_code": "fa"
}
-->
# 📖 مفاهیم اصلی MCP: تسلط بر پروتکل زمینه مدل برای یکپارچه‌سازی هوش مصنوعی

پروتکل زمینه مدل (MCP) یک چارچوب قدرتمند و استاندارد شده است که ارتباط بین مدل‌های زبانی بزرگ (LLM) و ابزارها، برنامه‌ها و منابع داده خارجی را بهینه می‌کند. این راهنمای بهینه‌شده برای سئو، شما را با مفاهیم اصلی MCP آشنا می‌کند و اطمینان می‌دهد معماری کلاینت-سرور، اجزای کلیدی، مکانیزم‌های ارتباطی و بهترین روش‌های پیاده‌سازی آن را به خوبی درک کنید.

## مرور کلی

این درس معماری پایه و اجزایی که اکوسیستم پروتکل زمینه مدل (MCP) را تشکیل می‌دهند، بررسی می‌کند. شما با معماری کلاینت-سرور، اجزای اصلی و مکانیزم‌های ارتباطی که تعاملات MCP را ممکن می‌سازند، آشنا خواهید شد.

## 👩‍🎓 اهداف کلیدی یادگیری

در پایان این درس، شما قادر خواهید بود:

- معماری کلاینت-سرور MCP را درک کنید.
- نقش‌ها و مسئولیت‌های Hosts، Clients و Servers را شناسایی کنید.
- ویژگی‌های اصلی که MCP را به یک لایه یکپارچه‌سازی انعطاف‌پذیر تبدیل می‌کنند، تحلیل کنید.
- جریان اطلاعات در اکوسیستم MCP را بیاموزید.
- از طریق مثال‌های کد در .NET، Java، Python و JavaScript دیدگاه‌های عملی کسب کنید.

## 🔎 معماری MCP: نگاهی عمیق‌تر

اکوسیستم MCP بر پایه مدل کلاینت-سرور ساخته شده است. این ساختار مدولار به برنامه‌های هوش مصنوعی اجازه می‌دهد به طور مؤثر با ابزارها، پایگاه‌های داده، APIها و منابع متنی تعامل داشته باشند. بیایید این معماری را به اجزای اصلی آن تقسیم کنیم.

### 1. Hosts

در پروتکل زمینه مدل (MCP)، Hosts نقش مهمی به عنوان رابط اصلی دارند که کاربران از طریق آن با پروتکل تعامل می‌کنند. Hosts برنامه‌ها یا محیط‌هایی هستند که ارتباط با سرورهای MCP را برای دسترسی به داده‌ها، ابزارها و درخواست‌ها برقرار می‌کنند. نمونه‌هایی از Hosts شامل محیط‌های توسعه یکپارچه (IDE) مانند Visual Studio Code، ابزارهای هوش مصنوعی مانند Claude Desktop یا عوامل سفارشی ساخته شده برای وظایف خاص هستند.

**Hosts** برنامه‌های LLM هستند که ارتباطات را آغاز می‌کنند. آنها:

- مدل‌های هوش مصنوعی را اجرا یا با آن‌ها تعامل می‌کنند تا پاسخ تولید کنند.
- ارتباط با سرورهای MCP را شروع می‌کنند.
- جریان مکالمه و رابط کاربری را مدیریت می‌کنند.
- مجوزها و محدودیت‌های امنیتی را کنترل می‌کنند.
- رضایت کاربر برای به اشتراک‌گذاری داده‌ها و اجرای ابزارها را مدیریت می‌کنند.

### 2. Clients

Clients اجزای حیاتی هستند که تعامل بین Hosts و سرورهای MCP را تسهیل می‌کنند. Clients به عنوان واسطه عمل می‌کنند و به Hosts امکان دسترسی و استفاده از قابلیت‌های ارائه شده توسط سرورهای MCP را می‌دهند. آن‌ها نقش مهمی در اطمینان از ارتباط روان و تبادل داده کارآمد در معماری MCP دارند.

**Clients** کانکتورهایی در داخل برنامه Host هستند. آنها:

- درخواست‌ها را با درخواست‌ها/دستورالعمل‌ها به سرورها ارسال می‌کنند.
- قابلیت‌ها را با سرورها مذاکره می‌کنند.
- درخواست‌های اجرای ابزار از مدل‌ها را مدیریت می‌کنند.
- پاسخ‌ها را پردازش و به کاربران نمایش می‌دهند.

### 3. Servers

سرورها مسئول رسیدگی به درخواست‌های دریافت شده از کلاینت‌های MCP و ارائه پاسخ‌های مناسب هستند. آن‌ها عملیات مختلفی مانند بازیابی داده، اجرای ابزار و تولید درخواست‌ها را مدیریت می‌کنند. سرورها اطمینان می‌دهند که ارتباط بین کلاینت‌ها و Hosts به صورت مؤثر و قابل اعتماد حفظ شده و تمام فرایند تعامل به درستی انجام شود.

**Servers** سرویس‌هایی هستند که زمینه و قابلیت‌ها را فراهم می‌کنند. آن‌ها:

- ویژگی‌های موجود (منابع، درخواست‌ها، ابزارها) را ثبت می‌کنند.
- درخواست‌های اجرای ابزار از کلاینت را دریافت و اجرا می‌کنند.
- اطلاعات زمینه‌ای برای بهبود پاسخ‌های مدل فراهم می‌کنند.
- خروجی‌ها را به کلاینت بازمی‌گردانند.
- در صورت نیاز، وضعیت تعاملات را حفظ می‌کنند.

سرورها می‌توانند توسط هر کسی توسعه داده شوند تا قابلیت‌های مدل را با عملکردهای تخصصی گسترش دهند.

### 4. ویژگی‌های سرور

سرورها در پروتکل زمینه مدل (MCP) بلوک‌های بنیادی را فراهم می‌کنند که تعاملات غنی بین کلاینت‌ها، Hosts و مدل‌های زبانی را ممکن می‌سازند. این ویژگی‌ها برای افزایش قابلیت‌های MCP با ارائه زمینه ساختاریافته، ابزارها و درخواست‌ها طراحی شده‌اند.

سرورهای MCP می‌توانند هر یک از ویژگی‌های زیر را ارائه دهند:

#### 📑 منابع

منابع در پروتکل زمینه مدل (MCP) شامل انواع مختلفی از زمینه و داده‌ها هستند که کاربران یا مدل‌های هوش مصنوعی می‌توانند از آن‌ها بهره‌مند شوند. این موارد شامل:

- **داده‌های زمینه‌ای**: اطلاعات و زمینه‌ای که کاربران یا مدل‌های هوش مصنوعی می‌توانند برای تصمیم‌گیری و اجرای وظایف از آن استفاده کنند.
- **پایگاه‌های دانش و مخازن مستندات**: مجموعه‌هایی از داده‌های ساختاریافته و غیرساختاری مانند مقالات، راهنماها و مقالات پژوهشی که بینش‌ها و اطلاعات ارزشمندی ارائه می‌دهند.
- **فایل‌ها و پایگاه‌های داده محلی**: داده‌هایی که به صورت محلی روی دستگاه‌ها یا در پایگاه‌های داده ذخیره شده‌اند و برای پردازش و تحلیل قابل دسترسی هستند.
- **APIها و سرویس‌های وب**: رابط‌ها و سرویس‌های خارجی که داده‌ها و قابلیت‌های اضافی ارائه می‌دهند و امکان یکپارچه‌سازی با منابع و ابزارهای آنلاین مختلف را فراهم می‌کنند.

مثالی از یک منبع می‌تواند یک طرح پایگاه داده یا فایلی باشد که به این شکل قابل دسترسی است:

```text
file://log.txt
database://schema
```

### 🤖 درخواست‌ها

درخواست‌ها در پروتکل زمینه مدل (MCP) شامل قالب‌ها و الگوهای تعاملی از پیش تعریف شده‌ای هستند که برای ساده‌سازی روند کاری کاربران و بهبود ارتباط طراحی شده‌اند. این موارد شامل:

- **پیام‌ها و روندهای کاری قالب‌بندی شده**: پیام‌ها و فرایندهای از پیش ساختاربندی شده که کاربران را در انجام وظایف و تعاملات خاص راهنمایی می‌کنند.
- **الگوهای تعامل از پیش تعریف شده**: توالی‌های استاندارد شده از اقدامات و پاسخ‌ها که ارتباط مؤثر و منسجم را تسهیل می‌کنند.
- **قالب‌های مکالمه تخصصی**: قالب‌های قابل تنظیم که برای انواع خاصی از مکالمات طراحی شده‌اند و تعاملات مرتبط و متناسب با زمینه را تضمین می‌کنند.

یک قالب درخواست می‌تواند به این صورت باشد:

```markdown
Generate a product slogan based on the following {{product}} with the following {{keywords}}
```

#### ⛏️ ابزارها

ابزارها در پروتکل زمینه مدل (MCP) توابعی هستند که مدل هوش مصنوعی می‌تواند برای انجام وظایف خاص اجرا کند. این ابزارها برای افزایش قابلیت‌های مدل هوش مصنوعی با ارائه عملیات ساختاریافته و قابل اطمینان طراحی شده‌اند. جنبه‌های کلیدی شامل:

- **توابعی که مدل هوش مصنوعی می‌تواند اجرا کند**: ابزارها توابع اجرایی هستند که مدل می‌تواند برای انجام وظایف مختلف فراخوانی کند.
- **نام و توضیح منحصر به فرد**: هر ابزار دارای نامی متمایز و توضیح دقیقی است که هدف و عملکرد آن را شرح می‌دهد.
- **پارامترها و خروجی‌ها**: ابزارها پارامترهای خاصی را می‌پذیرند و خروجی‌های ساختاریافته‌ای برمی‌گردانند تا نتایج ثابت و قابل پیش‌بینی داشته باشند.
- **توابع مجزا**: ابزارها وظایف مجزایی مانند جستجوی وب، محاسبات و پرس‌وجوهای پایگاه داده را انجام می‌دهند.

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

در پروتکل زمینه مدل (MCP)، کلاینت‌ها چندین ویژگی کلیدی به سرورها ارائه می‌دهند که عملکرد کلی و تعامل درون پروتکل را بهبود می‌بخشد. یکی از ویژگی‌های قابل توجه، نمونه‌گیری (Sampling) است.

### 👉 نمونه‌گیری

- **رفتارهای عامل‌محور آغاز شده توسط سرور**: کلاینت‌ها به سرورها اجازه می‌دهند تا به طور خودکار اقدامات یا رفتارهای خاصی را شروع کنند و قابلیت‌های پویا سیستم را افزایش دهند.
- **تعاملات بازگشتی با LLM**: این ویژگی امکان تعاملات بازگشتی با مدل‌های زبانی بزرگ را فراهم می‌کند و پردازش‌های پیچیده‌تر و تکراری را ممکن می‌سازد.
- **درخواست تکمیل‌های بیشتر مدل**: سرورها می‌توانند درخواست تکمیل‌های بیشتری از مدل داشته باشند تا اطمینان حاصل شود پاسخ‌ها جامع و مرتبط با زمینه هستند.

## جریان اطلاعات در MCP

پروتکل زمینه مدل (MCP) جریان ساختاریافته‌ای از اطلاعات بین Hosts، Clients، Servers و مدل‌ها تعریف می‌کند. درک این جریان به روشن شدن نحوه پردازش درخواست‌های کاربر و یکپارچه‌سازی ابزارها و داده‌های خارجی در پاسخ‌های مدل کمک می‌کند.

- **Host ارتباط را آغاز می‌کند**  
  برنامه Host (مانند یک IDE یا رابط چت) اتصال به سرور MCP را برقرار می‌کند، معمولاً از طریق STDIO، WebSocket یا سایر روش‌های انتقال پشتیبانی شده.

- **مذاکره قابلیت‌ها**  
  کلاینت (که در Host جاسازی شده) و سرور اطلاعات مربوط به ویژگی‌ها، ابزارها، منابع و نسخه‌های پروتکل پشتیبانی شده را مبادله می‌کنند. این اطمینان می‌دهد که هر دو طرف قابلیت‌های موجود برای جلسه را درک می‌کنند.

- **درخواست کاربر**  
  کاربر با Host تعامل می‌کند (مثلاً درخواست یا فرمانی وارد می‌کند). Host این ورودی را جمع‌آوری کرده و برای پردازش به کلاینت ارسال می‌کند.

- **استفاده از منبع یا ابزار**  
  - کلاینت ممکن است درخواست زمینه یا منابع اضافی از سرور کند (مانند فایل‌ها، ورودی‌های پایگاه داده یا مقالات پایگاه دانش) تا درک مدل را غنی‌تر کند.
  - اگر مدل تشخیص دهد که به ابزاری نیاز است (مثلاً برای بازیابی داده، انجام محاسبه یا فراخوانی API)، کلاینت درخواست اجرای ابزار را به سرور ارسال می‌کند و نام ابزار و پارامترها را مشخص می‌کند.

- **اجرای سرور**  
  سرور درخواست منبع یا ابزار را دریافت می‌کند، عملیات لازم را اجرا می‌کند (مانند اجرای تابع، پرس‌وجوی پایگاه داده یا بازیابی فایل) و نتایج را در قالب ساختاریافته به کلاینت بازمی‌گرداند.

- **تولید پاسخ**  
  کلاینت پاسخ‌های سرور (داده‌های منابع، خروجی‌های ابزار و غیره) را در تعامل جاری مدل ادغام می‌کند. مدل از این اطلاعات برای تولید پاسخ جامع و مرتبط با زمینه استفاده می‌کند.

- **ارائه نتیجه**  
  Host خروجی نهایی را از کلاینت دریافت کرده و به کاربر نمایش می‌دهد، که معمولاً شامل متن تولید شده توسط مدل و هر نتیجه‌ای از اجرای ابزارها یا جستجوی منابع است.

این جریان امکان پشتیبانی از برنامه‌های هوش مصنوعی پیشرفته، تعاملی و آگاه به زمینه را با اتصال بی‌وقفه مدل‌ها به ابزارها و منابع داده خارجی فراهم می‌کند.

## جزئیات پروتکل

MCP (پروتکل زمینه مدل) بر پایه [JSON-RPC 2.0](https://www.jsonrpc.org/) ساخته شده است و قالب پیام استاندارد، مستقل از زبان برنامه‌نویسی، برای ارتباط بین Hosts، Clients و Servers فراهم می‌کند. این پایه امکان تعاملات قابل اعتماد، ساختاریافته و قابل توسعه را در پلتفرم‌ها و زبان‌های برنامه‌نویسی مختلف فراهم می‌کند.

### ویژگی‌های کلیدی پروتکل

MCP JSON-RPC 2.0 را با قراردادهای اضافی برای فراخوانی ابزار، دسترسی به منابع و مدیریت درخواست‌ها گسترش می‌دهد. این پروتکل از چندین لایه انتقال (STDIO، WebSocket، SSE) پشتیبانی می‌کند و ارتباطی امن، قابل توسعه و مستقل از زبان بین اجزا فراهم می‌سازد.

#### 🧢 پروتکل پایه

- **قالب پیام JSON-RPC**: تمام درخواست‌ها و پاسخ‌ها از مشخصات JSON-RPC 2.0 استفاده می‌کنند که ساختار یکسانی برای فراخوانی متدها، پارامترها، نتایج و مدیریت خطا فراهم می‌کند.
- **اتصالات حالت‌دار**: جلسات MCP وضعیت را در چندین درخواست حفظ می‌کنند و از مکالمات مداوم، انباشت زمینه و مدیریت منابع پشتیبانی می‌کنند.
- **مذاکره قابلیت‌ها**: در زمان برقراری اتصال، کلاینت‌ها و سرورها اطلاعات مربوط به ویژگی‌های پشتیبانی شده، نسخه‌های پروتکل، ابزارها و منابع را مبادله می‌کنند تا هر دو طرف قابلیت‌های یکدیگر را درک و تطبیق دهند.

#### ➕ امکانات اضافی

در ادامه برخی امکانات و توسعه‌های پروتکل که MCP برای بهبود تجربه توسعه‌دهنده و پشتیبانی از سناریوهای پیشرفته ارائه می‌دهد، آمده است:

- **گزینه‌های پیکربندی**: MCP اجازه تنظیم پویا پارامترهای جلسه مانند مجوزهای ابزار، دسترسی به منابع و تنظیمات مدل را می‌دهد که متناسب با هر تعامل تنظیم می‌شوند.
- **ردیابی پیشرفت**: عملیات طولانی می‌توانند به‌روزرسانی‌های پیشرفت را گزارش دهند که باعث رابط‌های کاربری پاسخگو و تجربه بهتر در طول وظایف پیچیده می‌شود.
- **لغو درخواست**: کلاینت‌ها می‌توانند درخواست‌های در حال اجرا را لغو کنند و به کاربران اجازه می‌دهند عملیات غیرضروری یا زمان‌بر را متوقف کنند.
- **گزارش خطا**: پیام‌ها و کدهای خطای استاندارد شده به تشخیص مشکلات، مدیریت شکست‌ها به شکل مناسب و ارائه بازخورد عملی به کاربران و توسعه‌دهندگان کمک می‌کند.
- **ثبت لاگ**: هم کلاینت‌ها و هم سرورها می‌توانند لاگ‌های ساختاریافته برای حسابرسی، اشکال‌زدایی و نظارت بر تعاملات پروتکل تولید کنند.

با استفاده از این ویژگی‌ها، MCP ارتباطی مقاوم، امن و انعطاف‌پذیر بین مدل‌های زبانی و ابزارها یا منابع داده خارجی تضمین می‌کند.

### 🔐 ملاحظات امنیتی

پیاده‌سازی‌های MCP باید به چند اصل کلیدی امنیتی پایبند باشند تا تعاملات ایمن و قابل اعتماد باشند:

- **رضایت و کنترل کاربر**: کاربران باید رضایت صریح خود را قبل از دسترسی به داده‌ها یا انجام عملیات ارائه دهند. آن‌ها باید کنترل واضحی بر اینکه چه داده‌هایی به اشتراک گذاشته می‌شود و کدام اقدامات مجاز هستند داشته باشند، همراه با رابط‌های کاربری شهودی برای بازبینی و تأیید فعالیت‌ها.

- **حریم خصوصی داده‌ها**: داده‌های کاربران تنها با رضایت صریح افشا شوند و باید با کنترل‌های دسترسی مناسب محافظت شوند. پیاده‌سازی‌های MCP باید از انتقال غیرمجاز داده جلوگیری کنند و اطمینان حاصل کنند که حریم خصوصی در تمام تعاملات حفظ می‌شود.

- **ایمنی ابزارها**: قبل از فراخوانی هر ابزار، رضایت صریح کاربر لازم است. کاربران باید عملکرد هر ابزار را به خوبی درک کنند و مرزهای امنیتی محکمی اعمال شود تا از اجرای ناخواسته یا ناامن ابزارها جلوگیری شود.

با رعایت این اصول، MCP اطمینان می‌دهد که اعتماد، حریم خصوصی و ایمنی کاربران در تمام تعاملات پروتکل حفظ شود.

## مثال‌های کد: اجزای کلیدی

در ادامه مثال‌های کد در چند زبان برنامه‌نویسی محبوب آورده شده که نحوه پیاده‌سازی اجزای کلیدی سرور MCP و ابزارها را نشان می‌دهد.

### مثال .NET: ساخت یک سرور ساده MCP با ابزارها

در اینجا یک مثال عملی در .NET آمده که نشان می‌دهد چگونه یک سرور ساده MCP با ابزارهای سفارشی پیاده‌سازی کنید. این مثال نحوه تعریف و ثبت ابزارها، مدیریت درخواست‌ها و اتصال سرور با استفاده از پروتکل زمینه مدل را نشان می‌دهد.

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

این مثال همان سرور MCP و ثبت ابزار را که در مثال .NET آمده، اما به زبان Java پیاده‌سازی می‌کند.

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

در این مثال نحوه ساخت یک سرور MCP در Python نشان داده شده است. همچنین دو روش مختلف برای ایجاد ابزارها آموزش داده شده است.

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

# Instantiate the class to register its tools
weather_tools = WeatherTools()

# Start the server using stdio transport
if __name__ == "__main__":
    asyncio.run(serve_stdio(mcp))
```

### مثال JavaScript: ساخت سرور MCP

این مثال ساخت سرور MCP در JavaScript را نشان می‌دهد و نحوه ثبت دو ابزار مرتبط با آب و هوا را آموزش می‌دهد.

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

این مثال JavaScript نشان می‌دهد چگونه یک کلاینت MCP بسازید که به سرور متصل می‌شود، درخواست ارسال می‌کند و پاسخ را از جمله هر فراخوانی ابزار پردازش می‌کند.

## امنیت و مجوزدهی

MCP چندین مفهوم و مکانیزم داخلی برای مدیریت امنیت و مجوزدهی در سراسر پروتکل دارد:

1. **کنترل مجوز ابزار**  
   کلاینت‌ها می‌توانند مشخص کنند که مدل در طول جلسه اجازه استفاده از کدام ابزارها را دارد. این اطمینان می‌دهد که تنها ابزارهای صریحاً مجاز قابل دسترسی هستند و خطر عملیات ناخواسته یا ناامن کاهش می‌یابد. مجوزها می‌توانند به صورت پویا بر اساس ترجیحات کاربر، سیاست‌های سازمانی یا زمینه تعامل تنظیم شوند.

2. **احراز هویت**  
   سرورها می‌توانند قبل از اعطای دسترسی به ابزارها، منابع یا عملیات حساس، احراز هویت را الزامی کنند. این ممکن است

**سلب مسئولیت**:  
این سند با استفاده از سرویس ترجمه هوش مصنوعی [Co-op Translator](https://github.com/Azure/co-op-translator) ترجمه شده است. در حالی که ما برای دقت تلاش می‌کنیم، لطفاً توجه داشته باشید که ترجمه‌های خودکار ممکن است حاوی خطاها یا نواقصی باشند. سند اصلی به زبان بومی آن باید به عنوان منبع معتبر در نظر گرفته شود. برای اطلاعات حیاتی، ترجمه حرفه‌ای انسانی توصیه می‌شود. ما مسئول هیچ گونه سوءتفاهم یا تفسیر نادرستی که ناشی از استفاده از این ترجمه باشد، نیستیم.