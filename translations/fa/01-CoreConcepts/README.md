<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "788eb17750e970a0bc3b5e7f2e99975b",
  "translation_date": "2025-05-18T14:56:25+00:00",
  "source_file": "01-CoreConcepts/README.md",
  "language_code": "fa"
}
-->
# 📖 مفاهیم اصلی MCP: تسلط بر پروتکل زمینه مدل برای یکپارچه‌سازی هوش مصنوعی

پروتکل زمینه مدل (MCP) چارچوبی قدرتمند و استاندارد شده است که ارتباط بین مدل‌های زبان بزرگ (LLM) و ابزارها، برنامه‌ها و منابع داده خارجی را بهینه می‌کند. این راهنمای بهینه‌شده برای سئو، شما را با مفاهیم اصلی MCP آشنا می‌کند و اطمینان می‌دهد که معماری کلاینت-سرور، اجزای اساسی، مکانیزم‌های ارتباطی و بهترین شیوه‌های پیاده‌سازی آن را درک کنید.

## مرور کلی

این درس معماری پایه و اجزایی را که اکوسیستم پروتکل زمینه مدل (MCP) را تشکیل می‌دهند، بررسی می‌کند. شما با معماری کلاینت-سرور، اجزای کلیدی و مکانیزم‌های ارتباطی که تعاملات MCP را ممکن می‌سازند، آشنا خواهید شد.

## 👩‍🎓 اهداف کلیدی یادگیری

در پایان این درس، شما:

- معماری کلاینت-سرور MCP را درک خواهید کرد.
- نقش‌ها و مسئولیت‌های Hosts، Clients و Servers را شناسایی می‌کنید.
- ویژگی‌های اصلی که MCP را به لایه‌ای انعطاف‌پذیر برای یکپارچه‌سازی تبدیل می‌کنند، تحلیل می‌کنید.
- نحوه جریان اطلاعات در اکوسیستم MCP را می‌آموزید.
- با مثال‌های عملی کد در .NET، Java، Python و JavaScript آشنا می‌شوید.

## 🔎 معماری MCP: نگاهی عمیق‌تر

اکوسیستم MCP بر پایه مدل کلاینت-سرور ساخته شده است. این ساختار مدولار به برنامه‌های هوش مصنوعی اجازه می‌دهد به صورت کارآمد با ابزارها، پایگاه‌های داده، APIها و منابع زمینه‌ای تعامل داشته باشند. بیایید این معماری را به اجزای اصلی آن تقسیم کنیم.

### 1. Hosts

در پروتکل زمینه مدل (MCP)، Hosts نقش حیاتی به عنوان رابط اصلی‌ای دارند که کاربران از طریق آن با پروتکل تعامل می‌کنند. Hosts برنامه‌ها یا محیط‌هایی هستند که اتصال به سرورهای MCP را برای دسترسی به داده‌ها، ابزارها و پرامپت‌ها برقرار می‌کنند. نمونه‌هایی از Hosts شامل محیط‌های توسعه یکپارچه (IDE) مانند Visual Studio Code، ابزارهای هوش مصنوعی مانند Claude Desktop، یا عامل‌های سفارشی ساخته شده برای وظایف خاص هستند.

**Hosts** برنامه‌های LLM هستند که اتصال را آغاز می‌کنند. آن‌ها:

- مدل‌های هوش مصنوعی را اجرا یا با آن‌ها تعامل دارند تا پاسخ‌ها را تولید کنند.
- اتصال به سرورهای MCP را برقرار می‌کنند.
- جریان مکالمه و رابط کاربری را مدیریت می‌کنند.
- مجوزها و محدودیت‌های امنیتی را کنترل می‌کنند.
- رضایت کاربر برای به اشتراک‌گذاری داده‌ها و اجرای ابزارها را مدیریت می‌کنند.

### 2. Clients

Clients اجزای حیاتی‌ای هستند که تعامل بین Hosts و سرورهای MCP را تسهیل می‌کنند. Clients به عنوان واسطه عمل می‌کنند و به Hosts اجازه می‌دهند از قابلیت‌های ارائه شده توسط سرورهای MCP استفاده کنند. آن‌ها نقش مهمی در تضمین ارتباط روان و تبادل داده کارآمد در معماری MCP دارند.

**Clients** کانکتورهایی درون برنامه Host هستند. آن‌ها:

- درخواست‌ها را با پرامپت‌ها/دستورالعمل‌ها به سرورها ارسال می‌کنند.
- قابلیت‌ها را با سرورها مذاکره می‌کنند.
- درخواست‌های اجرای ابزار از مدل‌ها را مدیریت می‌کنند.
- پاسخ‌ها را پردازش و به کاربران نمایش می‌دهند.

### 3. Servers

سرورها مسئول رسیدگی به درخواست‌های کلاینت‌های MCP و ارائه پاسخ‌های مناسب هستند. آن‌ها عملیات مختلفی مانند بازیابی داده، اجرای ابزار و تولید پرامپت را مدیریت می‌کنند. سرورها اطمینان می‌دهند که ارتباط بین کلاینت‌ها و Hosts کارآمد و قابل اعتماد است و یکپارچگی فرآیند تعامل حفظ می‌شود.

**Servers** سرویس‌هایی هستند که زمینه و قابلیت‌ها را فراهم می‌کنند. آن‌ها:

- ویژگی‌های در دسترس (منابع، پرامپت‌ها، ابزارها) را ثبت می‌کنند.
- تماس‌های ابزار را از کلاینت دریافت و اجرا می‌کنند.
- اطلاعات زمینه‌ای برای بهبود پاسخ‌های مدل فراهم می‌کنند.
- خروجی‌ها را به کلاینت بازمی‌گردانند.
- در صورت نیاز، وضعیت را در طول تعاملات حفظ می‌کنند.

سرورها می‌توانند توسط هر کسی توسعه داده شوند تا قابلیت‌های مدل را با عملکرد تخصصی گسترش دهند.

### 4. ویژگی‌های سرور

سرورها در پروتکل زمینه مدل (MCP) بلوک‌های ساختمانی اساسی‌ای فراهم می‌کنند که تعاملات غنی بین کلاینت‌ها، Hosts و مدل‌های زبانی را ممکن می‌سازند. این ویژگی‌ها به منظور افزایش قابلیت‌های MCP با ارائه زمینه ساختارمند، ابزارها و پرامپت‌ها طراحی شده‌اند.

سرورهای MCP می‌توانند هر یک از ویژگی‌های زیر را ارائه دهند:

#### 📑 منابع

منابع در پروتکل زمینه مدل (MCP) شامل انواع مختلفی از زمینه و داده هستند که کاربران یا مدل‌های هوش مصنوعی می‌توانند از آن‌ها استفاده کنند. این موارد شامل:

- **داده‌های زمینه‌ای**: اطلاعات و زمینه‌ای که کاربران یا مدل‌های هوش مصنوعی می‌توانند برای تصمیم‌گیری و انجام وظایف استفاده کنند.
- **پایگاه‌های دانش و مخازن اسناد**: مجموعه‌ای از داده‌های ساختاریافته و غیرساختاریافته، مانند مقالات، راهنماها و مقالات پژوهشی که دیدگاه‌ها و اطلاعات ارزشمندی ارائه می‌دهند.
- **فایل‌ها و پایگاه‌های داده محلی**: داده‌هایی که به صورت محلی روی دستگاه‌ها یا در پایگاه‌های داده ذخیره شده‌اند و برای پردازش و تحلیل در دسترس هستند.
- **APIها و سرویس‌های وب**: رابط‌ها و سرویس‌های خارجی که داده‌ها و قابلیت‌های اضافی ارائه می‌دهند و امکان یکپارچه‌سازی با منابع و ابزارهای آنلاین مختلف را فراهم می‌کنند.

یک نمونه از منبع می‌تواند طرح پایگاه داده یا فایلی باشد که به این شکل قابل دسترسی است:

```text
file://log.txt
database://schema
```

### 🤖 پرامپت‌ها

پرامپت‌ها در پروتکل زمینه مدل (MCP) شامل قالب‌ها و الگوهای تعامل از پیش تعریف شده‌ای هستند که برای ساده‌سازی جریان کار کاربران و بهبود ارتباط طراحی شده‌اند. این موارد شامل:

- **پیام‌ها و جریان‌های کاری قالب‌بندی شده**: پیام‌ها و فرآیندهای ساختارمند که کاربران را در انجام وظایف و تعاملات خاص راهنمایی می‌کنند.
- **الگوهای تعامل از پیش تعریف شده**: توالی‌های استاندارد شده‌ای از اقدامات و پاسخ‌ها که ارتباط سازگار و کارآمد را تسهیل می‌کنند.
- **قالب‌های مکالمه تخصصی**: قالب‌های قابل تنظیم که برای انواع خاصی از مکالمات طراحی شده‌اند و تعاملات مرتبط و متناسب با زمینه را تضمین می‌کنند.

یک قالب پرامپت می‌تواند به این شکل باشد:

```markdown
Generate a product slogan based on the following {{product}} with the following {{keywords}}
```

#### ⛏️ ابزارها

ابزارها در پروتکل زمینه مدل (MCP) توابعی هستند که مدل هوش مصنوعی می‌تواند برای انجام وظایف خاص اجرا کند. این ابزارها برای افزایش قابلیت‌های مدل هوش مصنوعی با ارائه عملیات ساختارمند و قابل اعتماد طراحی شده‌اند. نکات کلیدی شامل:

- **توابعی که مدل هوش مصنوعی می‌تواند اجرا کند**: ابزارها توابع اجرایی هستند که مدل می‌تواند برای انجام وظایف مختلف فراخوانی کند.
- **نام و توضیح منحصر به فرد**: هر ابزار نام مشخص و توضیح دقیقی دارد که هدف و عملکرد آن را شرح می‌دهد.
- **پارامترها و خروجی‌ها**: ابزارها پارامترهای مشخصی را می‌پذیرند و خروجی‌های ساختارمند بازمی‌گردانند که نتایج سازگار و قابل پیش‌بینی را تضمین می‌کند.
- **توابع جداگانه**: ابزارها وظایف جداگانه‌ای مانند جستجوی وب، محاسبات و پرس‌وجوی پایگاه داده را انجام می‌دهند.

یک نمونه ابزار می‌تواند به این شکل باشد:

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

## ویژگی‌های کلاینت

در پروتکل زمینه مدل (MCP)، کلاینت‌ها چندین ویژگی کلیدی به سرورها ارائه می‌دهند که عملکرد کلی و تعامل درون پروتکل را بهبود می‌بخشد. یکی از ویژگی‌های قابل توجه، نمونه‌برداری (Sampling) است.

### 👉 نمونه‌برداری

- **رفتارهای عاملیت‌مند آغاز شده توسط سرور**: کلاینت‌ها امکان می‌دهند سرورها اقدامات یا رفتارهای خاصی را به صورت خودکار آغاز کنند و قابلیت‌های پویا سیستم را افزایش دهند.
- **تعاملات بازگشتی با LLM**: این ویژگی امکان تعاملات بازگشتی با مدل‌های زبان بزرگ را فراهم می‌کند و پردازش پیچیده‌تر و تکراری وظایف را ممکن می‌سازد.
- **درخواست تکمیل‌های اضافی مدل**: سرورها می‌توانند تکمیل‌های بیشتری از مدل درخواست کنند تا اطمینان حاصل شود پاسخ‌ها کامل و متناسب با زمینه هستند.

## جریان اطلاعات در MCP

پروتکل زمینه مدل (MCP) جریان ساختاریافته‌ای از اطلاعات بین Hosts، Clients، Servers و مدل‌ها تعریف می‌کند. درک این جریان کمک می‌کند تا روشن شود چگونه درخواست‌های کاربر پردازش می‌شوند و چگونه ابزارها و داده‌های خارجی در پاسخ‌های مدل ادغام می‌شوند.

- **Host اتصال را آغاز می‌کند**  
  برنامه Host (مانند IDE یا رابط چت) اتصال به سرور MCP را برقرار می‌کند، معمولاً از طریق STDIO، WebSocket یا روش انتقال پشتیبانی شده دیگر.

- **مذاکره قابلیت‌ها**  
  کلاینت (درون Host) و سرور اطلاعات مربوط به ویژگی‌ها، ابزارها، منابع و نسخه‌های پروتکل پشتیبانی شده را مبادله می‌کنند. این اطمینان می‌دهد که هر دو طرف قابلیت‌های موجود برای جلسه را درک می‌کنند.

- **درخواست کاربر**  
  کاربر با Host تعامل دارد (مثلاً پرامپت یا دستور وارد می‌کند). Host این ورودی را جمع‌آوری و به کلاینت برای پردازش منتقل می‌کند.

- **استفاده از منبع یا ابزار**  
  - کلاینت ممکن است درخواست زمینه یا منابع اضافی از سرور (مانند فایل‌ها، ورودی‌های پایگاه داده یا مقالات پایگاه دانش) برای غنی‌سازی درک مدل ارسال کند.  
  - اگر مدل تشخیص دهد که به ابزار نیاز است (مثلاً برای بازیابی داده، انجام محاسبه یا فراخوانی API)، کلاینت درخواست اجرای ابزار را به سرور ارسال می‌کند و نام ابزار و پارامترها را مشخص می‌کند.

- **اجرای سرور**  
  سرور درخواست منبع یا ابزار را دریافت کرده، عملیات لازم را اجرا می‌کند (مانند اجرای تابع، پرس‌وجوی پایگاه داده یا بازیابی فایل) و نتایج را به صورت ساختارمند به کلاینت بازمی‌گرداند.

- **تولید پاسخ**  
  کلاینت پاسخ‌های سرور (داده‌های منبع، خروجی‌های ابزار و غیره) را در تعامل جاری مدل ادغام می‌کند. مدل از این اطلاعات برای تولید پاسخی جامع و متناسب با زمینه استفاده می‌کند.

- **ارائه نتیجه**  
  Host خروجی نهایی را از کلاینت دریافت و به کاربر ارائه می‌دهد، که معمولاً شامل متن تولید شده توسط مدل و هر نتیجه‌ای از اجرای ابزارها یا جستجوی منابع است.

این جریان امکان پشتیبانی MCP از برنامه‌های هوش مصنوعی پیشرفته، تعاملی و آگاه به زمینه را با اتصال بی‌وقفه مدل‌ها به ابزارها و منابع داده خارجی فراهم می‌کند.

## جزئیات پروتکل

MCP (پروتکل زمینه مدل) بر پایه [JSON-RPC 2.0](https://www.jsonrpc.org/) ساخته شده است و قالب پیام استاندارد و مستقل از زبان برنامه‌نویسی را برای ارتباط بین Hosts، Clients و Servers فراهم می‌کند. این پایه امکان تعاملات قابل اعتماد، ساختارمند و قابل توسعه در پلتفرم‌ها و زبان‌های برنامه‌نویسی مختلف را می‌دهد.

### ویژگی‌های کلیدی پروتکل

MCP JSON-RPC 2.0 را با قراردادهای اضافی برای فراخوانی ابزار، دسترسی به منابع و مدیریت پرامپت گسترش می‌دهد. این پروتکل چندین لایه انتقال (STDIO، WebSocket، SSE) را پشتیبانی می‌کند و ارتباط امن، قابل توسعه و مستقل از زبان بین اجزا را ممکن می‌سازد.

#### 🧢 پروتکل پایه

- **قالب پیام JSON-RPC**: تمام درخواست‌ها و پاسخ‌ها از مشخصات JSON-RPC 2.0 پیروی می‌کنند تا ساختار یکسانی برای فراخوانی متدها، پارامترها، نتایج و مدیریت خطاها تضمین شود.
- **اتصالات حالت‌دار**: جلسات MCP وضعیت را در چندین درخواست حفظ می‌کنند و از مکالمات پیوسته، انباشت زمینه و مدیریت منابع پشتیبانی می‌کنند.
- **مذاکره قابلیت‌ها**: در هنگام برقراری اتصال، کلاینت‌ها و سرورها اطلاعات مربوط به ویژگی‌های پشتیبانی شده، نسخه‌های پروتکل، ابزارها و منابع را مبادله می‌کنند تا اطمینان حاصل شود هر دو طرف قابلیت‌های یکدیگر را درک کرده و بتوانند تطبیق یابند.

#### ➕ ابزارهای اضافی

در ادامه چند ابزار و توسعه پروتکل اضافی که MCP برای بهبود تجربه توسعه‌دهنده و امکان‌پذیر ساختن سناریوهای پیشرفته ارائه می‌دهد:

- **گزینه‌های پیکربندی**: MCP امکان پیکربندی پویا پارامترهای جلسه مانند مجوزهای ابزار، دسترسی به منابع و تنظیمات مدل را فراهم می‌کند که برای هر تعامل قابل تنظیم است.
- **ردیابی پیشرفت**: عملیات طولانی مدت می‌توانند به‌روزرسانی‌های پیشرفت را گزارش دهند تا رابط‌های کاربری پاسخگو و تجربه کاربری بهتر در طول وظایف پیچیده فراهم شود.
- **لغو درخواست**: کلاینت‌ها می‌توانند درخواست‌های در حال اجرا را لغو کنند تا کاربران بتوانند عملیات غیرضروری یا طولانی را متوقف کنند.
- **گزارش خطا**: پیام‌ها و کدهای خطای استاندارد شده به تشخیص مشکلات، مدیریت خطاها به صورت مناسب و ارائه بازخورد عملی به کاربران و توسعه‌دهندگان کمک می‌کنند.
- **ثبت لاگ**: هم کلاینت‌ها و هم سرورها می‌توانند لاگ‌های ساختارمند برای حسابرسی، اشکال‌زدایی و نظارت بر تعاملات پروتکل ارسال کنند.

با استفاده از این ویژگی‌های پروتکل، MCP ارتباطی قوی، امن و انعطاف‌پذیر بین مدل‌های زبان و ابزارها یا منابع داده خارجی فراهم می‌کند.

### 🔐 ملاحظات امنیتی

پیاده‌سازی‌های MCP باید به چند اصل کلیدی امنیتی پایبند باشند تا تعاملات ایمن و قابل اعتماد تضمین شود:

- **رضایت و کنترل کاربر**: کاربران باید قبل از دسترسی به هر داده یا انجام هر عملی رضایت صریح خود را اعلام کنند. آن‌ها باید کنترل واضحی بر داده‌های به اشتراک گذاشته شده و اقدامات مجاز داشته باشند که با رابط‌های کاربری شهودی برای مرور و تأیید فعالیت‌ها پشتیبانی می‌شود.

- **حفظ حریم خصوصی داده‌ها**: داده‌های کاربر فقط با رضایت صریح افشا می‌شوند و باید با کنترل‌های دسترسی مناسب محافظت شوند. پیاده‌سازی‌های MCP باید از انتقال غیرمجاز داده جلوگیری کرده و اطمینان دهند که حریم خصوصی در تمام تعاملات حفظ می‌شود.

- **ایمنی ابزارها**: پیش از فراخوانی هر ابزار، رضایت صریح کاربر لازم است. کاربران باید درک روشنی از عملکرد هر ابزار داشته باشند و مرزهای امنیتی محکمی برای جلوگیری از اجرای ناخواسته یا ناامن ابزارها برقرار شود.

با رعایت این اصول، MCP اطمینان می‌دهد که اعتماد، حریم خصوصی و ایمنی کاربران در تمامی تعاملات پروتکل حفظ شود.

## مثال‌های کد: اجزای کلیدی

در ادامه مثال‌هایی از کد در چند زبان برنامه‌نویسی محبوب ارائه شده که نحوه پیاده‌سازی اجزای کلیدی سرور MCP و ابزارها را نشان می‌دهد.

### مثال .NET: ایجاد یک سرور ساده MCP با ابزارها

در این مثال عملی کد .NET نشان داده شده که چگونه یک سرور ساده MCP با ابزارهای سفارشی پیاده‌سازی شود. این مثال نحوه تعریف و ثبت ابزارها، مدیریت درخواست‌ها و اتصال سرور با استفاده از پروتکل زمینه مدل را نمایش می‌دهد.

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

این مثال همان سرور MCP و ثبت ابزار در مثال .NET بالا را نشان می‌دهد اما در زبان Java پیاده‌سازی شده است.

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

### مثال JavaScript: ایجاد یک سرور MCP

این مثال ایجاد سرور MCP در JavaScript را نشان می‌دهد و نحوه ثبت دو ابزار مرتبط با آب و هوا را نمایش می‌دهد.

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

این مثال JavaScript نحوه ایجاد یک کلاینت MCP که به سرور متصل می‌شود، پرامپتی ارسال می‌کند و پاسخ از جمله هر فراخوانی ابزار را پردازش می‌کند، نشان می‌دهد.

## امنیت و مجوزها

MCP چندین مفهوم و مکانیزم داخلی برای مدیریت امنیت و مجوزها در سراسر پروتکل دارد:

1. **کنترل مجوز ابزار**:  
  کلاینت‌ها می‌توانند مشخص کنند که مدل در طول جلسه از کدام ابزارها می‌تواند استفاده کند. این اطمینان می‌دهد که فقط ابزارهای صریحاً مجاز در دسترس هستند و خطر عملیات ناخواسته یا ناامن کاهش می‌یابد. مجوزها می‌توانند به صورت پویا بر اساس ترجیحات کاربر، سیاست‌های سازمانی یا زمینه تعامل تنظیم شوند.

2. **احراز هویت**:

**سلب مسئولیت**:  
این سند با استفاده از سرویس ترجمه هوش مصنوعی [Co-op Translator](https://github.com/Azure/co-op-translator) ترجمه شده است. در حالی که ما برای دقت تلاش می‌کنیم، لطفاً توجه داشته باشید که ترجمه‌های خودکار ممکن است حاوی خطاها یا نادرستی‌هایی باشند. سند اصلی به زبان بومی خود باید به عنوان منبع معتبر در نظر گرفته شود. برای اطلاعات حیاتی، توصیه می‌شود از ترجمه حرفه‌ای انسانی استفاده شود. ما مسئول هیچ گونه سوءتفاهم یا تفسیر نادرستی که از استفاده این ترجمه ناشی شود، نیستیم.