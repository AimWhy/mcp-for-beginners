<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "056918462dca9b8f75901709fb8f470c",
  "translation_date": "2025-05-17T06:16:06+00:00",
  "source_file": "01-CoreConcepts/README.md",
  "language_code": "fa"
}
-->
# 📖 مفاهیم اصلی MCP: تسلط بر پروتکل مدل کانتکست برای یکپارچه‌سازی هوش مصنوعی

پروتکل مدل کانتکست (MCP) یک چارچوب قدرتمند و استاندارد شده است که ارتباط بین مدل‌های زبان بزرگ (LLMs) و ابزارهای خارجی، برنامه‌ها و منابع داده را بهینه‌سازی می‌کند. این راهنمای بهینه‌سازی شده برای SEO شما را از طریق مفاهیم اصلی MCP هدایت می‌کند، تا مطمئن شوید که معماری کلاینت-سرور، اجزای ضروری، مکانیک‌های ارتباطی و بهترین روش‌های پیاده‌سازی آن را درک کرده‌اید.

## مرور کلی

این درس معماری بنیادی و اجزایی که اکوسیستم پروتکل مدل کانتکست (MCP) را تشکیل می‌دهند را بررسی می‌کند. شما درباره معماری کلاینت-سرور، اجزای کلیدی و مکانیسم‌های ارتباطی که تعاملات MCP را قدرت می‌بخشند، خواهید آموخت.

## 👩‍🎓 اهداف کلیدی یادگیری

تا پایان این درس، شما:

- معماری کلاینت-سرور MCP را درک خواهید کرد.
- نقش‌ها و مسئولیت‌های میزبان‌ها، کلاینت‌ها و سرورها را شناسایی خواهید کرد.
- ویژگی‌های اصلی که MCP را به یک لایه یکپارچه‌سازی انعطاف‌پذیر تبدیل می‌کند، تحلیل خواهید کرد.
- یاد خواهید گرفت که اطلاعات چگونه در اکوسیستم MCP جریان پیدا می‌کند.
- از طریق مثال‌های کد در .NET، جاوا، پایتون و جاوا اسکریپت، بینش‌های عملی کسب خواهید کرد.

## 🔎 معماری MCP: نگاهی عمیق‌تر

اکوسیستم MCP بر اساس مدل کلاینت-سرور ساخته شده است. این ساختار ماژولار به برنامه‌های هوش مصنوعی اجازه می‌دهد تا به طور کارآمد با ابزارها، پایگاه‌های داده، APIها و منابع کانتکست تعامل داشته باشند. بیایید این معماری را به اجزای اصلی آن تقسیم کنیم.

### 1. میزبان‌ها

در پروتکل مدل کانتکست (MCP)، میزبان‌ها نقش حیاتی به عنوان رابط اصلی که کاربران از طریق آن با پروتکل تعامل دارند، بازی می‌کنند. میزبان‌ها برنامه‌ها یا محیط‌هایی هستند که اتصالات با سرورهای MCP را برای دسترسی به داده‌ها، ابزارها و پیام‌ها آغاز می‌کنند. نمونه‌هایی از میزبان‌ها شامل محیط‌های توسعه یکپارچه (IDEها) مانند ویژوال استودیو کد، ابزارهای هوش مصنوعی مانند Claude Desktop، یا عوامل سفارشی‌سازی شده برای وظایف خاص هستند.

**میزبان‌ها** برنامه‌های LLM هستند که اتصالات را آغاز می‌کنند. آنها:

- مدل‌های هوش مصنوعی را اجرا یا با آنها تعامل می‌کنند تا پاسخ‌ها را تولید کنند.
- اتصالات با سرورهای MCP را آغاز می‌کنند.
- جریان مکالمه و رابط کاربری را مدیریت می‌کنند.
- محدودیت‌های اجازه و امنیت را کنترل می‌کنند.
- رضایت کاربر برای اشتراک داده و اجرای ابزار را مدیریت می‌کنند.

### 2. کلاینت‌ها

کلاینت‌ها اجزای ضروری هستند که تعامل بین میزبان‌ها و سرورهای MCP را تسهیل می‌کنند. کلاینت‌ها به عنوان واسطه‌ها عمل می‌کنند، به میزبان‌ها امکان دسترسی و استفاده از قابلیت‌های ارائه شده توسط سرورهای MCP را می‌دهند. آنها نقش حیاتی در تضمین ارتباط روان و تبادل داده کارآمد درون معماری MCP دارند.

**کلاینت‌ها** کانکتورهایی درون برنامه میزبان هستند. آنها:

- درخواست‌ها را با پیام‌ها/دستورالعمل‌ها به سرورها ارسال می‌کنند.
- قابلیت‌ها را با سرورها مذاکره می‌کنند.
- درخواست‌های اجرای ابزار از مدل‌ها را مدیریت می‌کنند.
- پاسخ‌ها را پردازش و به کاربران نمایش می‌دهند.

### 3. سرورها

سرورها مسئول مدیریت درخواست‌ها از کلاینت‌های MCP و ارائه پاسخ‌های مناسب هستند. آنها عملیات مختلفی مانند بازیابی داده، اجرای ابزار و تولید پیام را مدیریت می‌کنند. سرورها تضمین می‌کنند که ارتباط بین کلاینت‌ها و میزبان‌ها کارآمد و قابل اعتماد باشد، و یکپارچگی فرآیند تعامل را حفظ می‌کنند.

**سرورها** خدماتی هستند که کانتکست و قابلیت‌ها را ارائه می‌دهند. آنها:

- ویژگی‌های موجود (منابع، پیام‌ها، ابزارها) را ثبت می‌کنند.
- تماس‌های ابزار از کلاینت را دریافت و اجرا می‌کنند.
- اطلاعات کانتکست را برای بهبود پاسخ‌های مدل ارائه می‌دهند.
- خروجی‌ها را به کلاینت بازمی‌گردانند.
- حالت را در تعاملات زمانی که لازم است حفظ می‌کنند.

سرورها می‌توانند توسط هر کسی توسعه داده شوند تا قابلیت‌های مدل را با عملکرد تخصصی گسترش دهند.

### 4. ویژگی‌های سرور

سرورها در پروتکل مدل کانتکست (MCP) بلوک‌های ساختاری بنیادی را ارائه می‌دهند که تعاملات غنی بین کلاینت‌ها، میزبان‌ها و مدل‌های زبان را امکان‌پذیر می‌کنند. این ویژگی‌ها برای بهبود قابلیت‌های MCP با ارائه کانتکست ساختاری، ابزارها و پیام‌ها طراحی شده‌اند.

سرورهای MCP می‌توانند هر یک از ویژگی‌های زیر را ارائه دهند:

#### 📑 منابع 

منابع در پروتکل مدل کانتکست (MCP) انواع مختلفی از کانتکست و داده را شامل می‌شوند که می‌توانند توسط کاربران یا مدل‌های هوش مصنوعی استفاده شوند. این شامل:

- **داده کانتکست**: اطلاعات و کانتکستی که کاربران یا مدل‌های هوش مصنوعی می‌توانند برای تصمیم‌گیری و اجرای وظایف استفاده کنند.
- **پایگاه‌های دانش و مخازن اسناد**: مجموعه‌هایی از داده‌های ساختاری و غیرساختاری، مانند مقالات، راهنماها و مقالات پژوهشی که بینش‌ها و اطلاعات ارزشمندی ارائه می‌دهند.
- **فایل‌ها و پایگاه‌های داده محلی**: داده‌هایی که به صورت محلی بر روی دستگاه‌ها یا درون پایگاه‌های داده ذخیره شده‌اند، قابل دسترسی برای پردازش و تحلیل.
- **APIها و خدمات وب**: رابط‌ها و خدمات خارجی که داده‌ها و قابلیت‌های اضافی ارائه می‌دهند، امکان یکپارچه‌سازی با منابع و ابزارهای آنلاین مختلف را فراهم می‌کنند.

مثالی از یک منبع می‌تواند یک طرح پایگاه داده یا فایلی باشد که می‌توان به این صورت به آن دسترسی داشت:

```text
file://log.txt
database://schema
```

### 🤖 پیام‌ها
پیام‌ها در پروتکل مدل کانتکست (MCP) شامل الگوهای پیش‌تعریف شده و الگوهای تعامل طراحی شده برای ساده‌سازی جریان‌های کاری کاربران و بهبود ارتباط هستند. این شامل:

- **پیام‌ها و جریان‌های کاری قالب‌بندی شده**: پیام‌ها و فرآیندهای پیش‌ساختاری که کاربران را از طریق وظایف و تعاملات خاص هدایت می‌کنند.
- **الگوهای تعامل پیش‌تعریف شده**: توالی‌های استاندارد شده از اقدامات و پاسخ‌ها که ارتباطی سازگار و کارآمد را تسهیل می‌کنند.
- **الگوهای مکالمه تخصصی**: الگوهای قابل تنظیم طراحی شده برای انواع خاصی از مکالمات، تضمین تعاملات مرتبط و مناسب کانتکست.

یک قالب پیام می‌تواند به این صورت باشد:

```markdown
Generate a product slogan based on the following {{product}} with the following {{keywords}}
```

#### ⛏️ ابزارها

ابزارها در پروتکل مدل کانتکست (MCP) عملکردهایی هستند که مدل هوش مصنوعی می‌تواند برای انجام وظایف خاص اجرا کند. این ابزارها برای بهبود قابلیت‌های مدل هوش مصنوعی با ارائه عملیات ساختاری و قابل اعتماد طراحی شده‌اند. جنبه‌های کلیدی شامل:

- **عملکردهایی برای مدل هوش مصنوعی برای اجرا**: ابزارها عملکردهای قابل اجرا هستند که مدل هوش مصنوعی می‌تواند برای انجام وظایف مختلف فراخوانی کند.
- **نام و توضیحات منحصر به فرد**: هر ابزار دارای نامی خاص و توضیحاتی دقیق است که هدف و عملکرد آن را توضیح می‌دهد.
- **پارامترها و خروجی‌ها**: ابزارها پارامترهای خاصی را قبول می‌کنند و خروجی‌های ساختاری ارائه می‌دهند، تضمین نتایج سازگار و قابل پیش‌بینی.
- **عملکردهای جداگانه**: ابزارها عملکردهای جداگانه‌ای مانند جستجوهای وب، محاسبات و پرسش‌های پایگاه داده را انجام می‌دهند.

یک ابزار نمونه می‌تواند به این صورت باشد:

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
در پروتکل مدل کانتکست (MCP)، کلاینت‌ها چندین ویژگی کلیدی به سرورها ارائه می‌دهند، که عملکرد کلی و تعامل درون پروتکل را بهبود می‌بخشند. یکی از ویژگی‌های قابل توجه نمونه‌گیری است.

### 👉 نمونه‌گیری

- **رفتارهای عاملانه سرور-آغاز شده**: کلاینت‌ها به سرورها اجازه می‌دهند تا به طور خودمختار اقدامات یا رفتارهای خاصی را آغاز کنند، قابلیت‌های پویا سیستم را افزایش می‌دهند.
- **تعاملات LLM بازگشتی**: این ویژگی اجازه تعاملات بازگشتی با مدل‌های زبان بزرگ (LLMs) را می‌دهد، امکان پردازش پیچیده‌تر و تکراری وظایف را فراهم می‌کند.
- **درخواست تکمیل‌های مدل اضافی**: سرورها می‌توانند تکمیل‌های اضافی از مدل درخواست کنند، تضمین می‌کنند که پاسخ‌ها کامل و مناسب کانتکست هستند.

## جریان اطلاعات در MCP

پروتکل مدل کانتکست (MCP) جریان ساختاری اطلاعات بین میزبان‌ها، کلاینت‌ها، سرورها و مدل‌ها را تعریف می‌کند. درک این جریان کمک می‌کند تا روشن شود که چگونه درخواست‌های کاربر پردازش می‌شوند و چگونه ابزارها و داده‌های خارجی در پاسخ‌های مدل یکپارچه می‌شوند.

- **میزبان اتصال را آغاز می‌کند**  
  برنامه میزبان (مانند یک IDE یا رابط چت) یک اتصال به سرور MCP برقرار می‌کند، معمولاً از طریق STDIO، WebSocket، یا یک حمل‌ونقل پشتیبانی شده دیگر.

- **مذاکره قابلیت‌ها**  
  کلاینت (مستقر در میزبان) و سرور اطلاعات درباره ویژگی‌های پشتیبانی شده، ابزارها، منابع و نسخه‌های پروتکل خود را تبادل می‌کنند. این اطمینان می‌دهد که هر دو طرف درک می‌کنند چه قابلیت‌هایی برای جلسه در دسترس است.

- **درخواست کاربر**  
  کاربر با میزبان تعامل می‌کند (مثلاً یک پیام یا فرمان وارد می‌کند). میزبان این ورودی را جمع‌آوری کرده و به کلاینت برای پردازش ارسال می‌کند.

- **استفاده از منابع یا ابزار**  
  - کلاینت ممکن است از سرور درخواست کانتکست یا منابع اضافی (مانند فایل‌ها، ورودی‌های پایگاه داده، یا مقالات پایگاه دانش) کند تا درک مدل را غنی کند.
  - اگر مدل تشخیص دهد که یک ابزار مورد نیاز است (مثلاً برای دریافت داده، انجام محاسبات، یا فراخوانی API)، کلاینت درخواست فراخوانی ابزار را به سرور ارسال می‌کند، نام و پارامترهای ابزار را مشخص می‌کند.

- **اجرای سرور**  
  سرور درخواست منابع یا ابزار را دریافت کرده، عملیات لازم را اجرا می‌کند (مانند اجرای یک عملکرد، پرسش از پایگاه داده، یا بازیابی یک فایل)، و نتایج را به کلاینت در قالب ساختاری بازمی‌گرداند.

- **تولید پاسخ**  
  کلاینت پاسخ‌های سرور (داده‌های منابع، خروجی‌های ابزار و غیره) را در تعاملات جاری مدل یکپارچه می‌کند. مدل از این اطلاعات برای تولید یک پاسخ جامع و مناسب کانتکست استفاده می‌کند.

- **ارائه نتیجه**  
  میزبان خروجی نهایی را از کلاینت دریافت کرده و به کاربر ارائه می‌دهد، اغلب شامل متن تولید شده مدل و هر نتیجه‌ای از اجرای ابزار یا جستجوهای منابع.

این جریان MCP را قادر می‌سازد تا برنامه‌های هوش مصنوعی پیشرفته، تعاملی و آگاه به کانتکست را با اتصال بی‌نقص مدل‌ها با ابزارها و منابع داده خارجی پشتیبانی کند.

## جزئیات پروتکل

MCP (پروتکل مدل کانتکست) بر اساس [JSON-RPC 2.0](https://www.jsonrpc.org/) ساخته شده است، ارائه یک قالب پیام استاندارد شده و زبان-آگنستیک برای ارتباط بین میزبان‌ها، کلاینت‌ها و سرورها. این پایه‌گذاری تعاملات قابل اعتماد، ساختاری و قابل گسترش در سراسر پلتفرم‌ها و زبان‌های برنامه‌نویسی مختلف را امکان‌پذیر می‌کند.

### ویژگی‌های کلیدی پروتکل

MCP JSON-RPC 2.0 را با کنوانسیون‌های اضافی برای فراخوانی ابزار، دسترسی به منابع و مدیریت پیام‌ها گسترش می‌دهد. این پروتکل از لایه‌های حمل‌ونقل متعدد (STDIO، WebSocket، SSE) پشتیبانی می‌کند و ارتباط امن، قابل گسترش و زبان-آگنستیک بین اجزا را امکان‌پذیر می‌کند.

#### 🧢 پروتکل پایه

- **قالب پیام JSON-RPC**: تمام درخواست‌ها و پاسخ‌ها از مشخصات JSON-RPC 2.0 استفاده می‌کنند، تضمین ساختار سازگار برای فراخوانی روش‌ها، پارامترها، نتایج و مدیریت خطا.
- **اتصالات حالت‌دار**: جلسات MCP حالت را در سراسر درخواست‌های متعدد حفظ می‌کنند، پشتیبانی از مکالمات جاری، انباشت کانتکست و مدیریت منابع.
- **مذاکره قابلیت‌ها**: در طول تنظیم اتصال، کلاینت‌ها و سرورها اطلاعات درباره ویژگی‌های پشتیبانی شده، نسخه‌های پروتکل، ابزارهای موجود و منابع را تبادل می‌کنند. این اطمینان می‌دهد که هر دو طرف درک می‌کنند قابلیت‌های یکدیگر را و می‌توانند به تناسب تطبیق یابند.

#### ➕ ابزارهای اضافی

در زیر برخی از ابزارهای اضافی و افزونه‌های پروتکل که MCP برای بهبود تجربه توسعه‌دهنده و امکان‌پذیر کردن سناریوهای پیشرفته ارائه می‌دهد، آمده است:

- **گزینه‌های پیکربندی**: MCP اجازه پیکربندی پویا پارامترهای جلسه، مانند اجازه‌های ابزار، دسترسی به منابع و تنظیمات مدل را می‌دهد، متناسب با هر تعامل.
- **ردیابی پیشرفت**: عملیات طولانی‌مدت می‌توانند به‌روزرسانی‌های پیشرفت گزارش دهند، امکان‌پذیر کردن رابط‌های کاربری پاسخگو و تجربه کاربری بهتر در طول وظایف پیچیده.
- **لغو درخواست**: کلاینت‌ها می‌توانند درخواست‌های در حال اجرا را لغو کنند، به کاربران اجازه می‌دهند عملیات‌هایی که دیگر مورد نیاز نیستند یا خیلی طولانی می‌کشند را قطع کنند.
- **گزارش خطا**: پیام‌ها و کدهای خطای استاندارد شده به تشخیص مسائل، مدیریت شکست‌ها به طور مؤثر، و ارائه بازخورد قابل اقدام به کاربران و توسعه‌دهندگان کمک می‌کنند.
- **ثبت وقایع**: هم کلاینت‌ها و هم سرورها می‌توانند وقایع ساختاری را برای حسابرسی، اشکال‌زدایی و نظارت بر تعاملات پروتکل منتشر کنند.

با بهره‌گیری از این ویژگی‌های پروتکل، MCP ارتباطی قوی، امن و انعطاف‌پذیر بین مدل‌های زبان و ابزارها یا منابع داده خارجی را تضمین می‌کند.

### 🔐 ملاحظات امنیتی

پیاده‌سازی‌های MCP باید به چندین اصل امنیتی کلیدی پایبند باشند تا تعاملات ایمن و قابل اعتماد را تضمین کنند:

- **رضایت و کنترل کاربر**: کاربران باید قبل از دسترسی به داده یا انجام عملیات رضایت صریح ارائه دهند. آنها باید کنترل واضحی بر اینکه چه داده‌ای به اشتراک گذاشته می‌شود و کدام اقدامات مجاز هستند، داشته باشند، که توسط رابط‌های کاربری بصری برای بررسی و تأیید فعالیت‌ها پشتیبانی می‌شود.

- **حریم خصوصی داده**: داده‌های کاربر فقط باید با رضایت صریح به اشتراک گذاشته شوند و باید با کنترل‌های دسترسی مناسب محافظت شوند. پیاده‌سازی‌های MCP باید از انتقال داده غیرمجاز محافظت کنند و اطمینان حاصل کنند که حریم خصوصی در طول تمام تعاملات حفظ می‌شود.

- **ایمنی ابزار**: قبل از فراخوانی هر ابزار، رضایت صریح کاربر مورد نیاز است. کاربران باید درک واضحی از عملکرد هر ابزار داشته باشند، و مرزهای امنیتی قوی باید اعمال شوند تا از اجرای ناخواسته یا ناامن ابزار جلوگیری شود.

با پیروی از این اصول، MCP تضمین می‌کند که اعتماد، حریم خصوصی و ایمنی کاربر در تمام تعاملات پروتکل حفظ می‌شود.

## مثال‌های کد: اجزای کلیدی

در زیر مثال‌های کد در چندین زبان برنامه‌نویسی محبوب که نشان می‌دهد چگونه اجزای کلیدی سرور MCP و ابزارها را پیاده‌سازی کنید، آمده است.

### مثال .NET: ایجاد یک سرور MCP ساده با ابزارها

در اینجا یک مثال عملی کد .NET آمده است که نشان می‌دهد چگونه یک سرور MCP ساده با ابزارهای سفارشی پیاده‌سازی کنید. این مثال نشان می‌دهد که چگونه ابزارها را تعریف و ثبت کنید، درخواست‌ها را مدیریت کنید و سرور را با استفاده از پروتکل مدل کانتکست متصل کنید.

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

### مثال جاوا: اجزای سرور MCP

این مثال همان سرور MCP و ثبت ابزار مانند مثال .NET بالا را نشان می‌دهد، اما در جاوا پیاده‌سازی شده است.

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

### مثال پایتون: ساخت یک سرور MCP

در این مثال نشان می‌دهیم که چگونه یک سرور MCP در پایتون بسازید. همچنین دو روش مختلف برای ایجاد ابزارها نشان داده شده است.

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

### مثال جاوا اسکریپت: ایجاد یک سرور MCP

این مثال ایجاد سرور MCP در جاوا اسکریپت و نشان می‌دهد که چگونه دو ابزار مرتبط با آب و هوا را ثبت کنید.

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

این مثال جاوا اس

**سلب مسئولیت**:  
این سند با استفاده از خدمات ترجمه هوش مصنوعی [Co-op Translator](https://github.com/Azure/co-op-translator) ترجمه شده است. در حالی که ما برای دقت تلاش می‌کنیم، لطفاً توجه داشته باشید که ترجمه‌های خودکار ممکن است حاوی خطاها یا نادرستی‌هایی باشند. سند اصلی به زبان مادری خود باید به عنوان منبع معتبر در نظر گرفته شود. برای اطلاعات حیاتی، ترجمه انسانی حرفه‌ای توصیه می‌شود. ما در قبال هرگونه سوء تفاهم یا تفسیر نادرست ناشی از استفاده از این ترجمه مسئولیتی نداریم.