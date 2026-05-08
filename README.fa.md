# AzuDl - GC2GD

**دانلودر یونیورسال عزیزی - از Google Colab به Google Drive**

AzuDl - GC2GD یک دانلودر حرفه‌ای بر پایه Google Colab است که فایل‌ها را مستقیماً روی Google Drive ذخیره می‌کند. این پروژه از لینک مستقیم، ویدیو و پلی‌لیست YouTube، مگنت تورنت، فایل `.torrent`، تورنت خصوصی، دانلود چندتایی، تاریخچه دانلود، ابزارهای مدیریت فایل، ساخت ZIP، هش SHA256، مانیتورینگ aria2، تشخیص تورنت تکراری، وضعیت زنده سید و ادامه دانلود با Session پشتیبانی می‌کند.

> English: [README.md](README.md)

---

## نسخه

```text
Version: 1.2.8
```

---

## قابلیت‌ها

- دانلود لینک مستقیم روی Google Drive
- دانلود ویدیو از YouTube
- دانلود پلی‌لیست YouTube
- انتخاب کیفیت ویدیو
- استخراج فایل صوتی MP3
- پشتیبانی از Custom Format ID در YouTube
- رفع خودکار مشکل فرمت‌های بی‌صدای YouTube
- دانلود Magnet Torrent
- دانلود فایل `.torrent` از لینک یا مسیر محلی
- حالت تورنت خصوصی
- قابلیت سید دادن بعد از دانلود
- نمایش زنده پیشرفت دانلود تورنت
- نمایش زنده وضعیت سید
- نمایش سرعت آپلود هنگام سید
- نمایش حجم آپلودشده هنگام سید
- نمایش Ratio تورنت
- نمایش تعداد Seeder و Connection
- تشخیص InfoHash تکراری
- ادامه دادن تورنت موجود به‌جای اضافه کردن Duplicate
- حذف خودکار تورنت خطادار و اضافه کردن دوباره آن
- ذخیره Session برای aria2
- پشتیبانی بهتر از ادامه دانلود
- تشخیص خودکار نوع لینک
- دانلود چندتایی یا Batch Download
- ذخیره تاریخچه دانلودها
- نمایش فایل‌های دانلودشده
- نمایش آخرین فایل دانلودشده
- گزارش فضای Google Drive
- گرفتن SHA256 از فایل آخر یا فایل انتخابی
- ساخت ZIP از پوشه
- ساخت ZIP از آخرین پوشه دانلودشده
- منوی جدا برای ابزارهای تورنت
- بخش اطلاعات برنامه‌نویس
- بخش Help داخلی

---

## تغییرات مهم نسخه 1.2.8

نسخه `1.2.8` بیشتر روی بهتر شدن بخش تورنت و مدیریت خطاهای تکراری تمرکز دارد.

در این نسخه، AzuDl قبل از اضافه کردن فایل `.torrent` به aria2، مقدار `InfoHash` تورنت را می‌خواند. اگر همان تورنت قبلاً داخل aria2 ثبت شده باشد، تورنت دوباره اضافه نمی‌شود، GID قبلی شناسایی می‌شود، همان دانلود قبلی ادامه داده یا مانیتور می‌شود، و اگر تورنت قبلی خطا داشته باشد، حذف می‌شود و دوباره اضافه می‌شود.

این قابلیت جلوی خطای رایج زیر را می‌گیرد:

```text
InfoHash is already registered
```

---

## منوی اصلی

```text
1. Auto detect link
2. Torrent tools
3. YouTube video or playlist
4. Direct link
5. Batch download
6. Download history
7. List downloaded files
8. Storage report
9. SHA256 latest file
10. SHA256 selected file
11. ZIP folder
12. ZIP latest folder
13. Latest file
14. Developer
15. Help
16. Exit
```

---

## منوی Torrent Tools

```text
1. Torrent magnet
2. Torrent file
3. Private torrent
4. aria2 status
5. Remove aria2 GID
6. Clear stopped aria2 results
7. Save aria2 session
8. Back
```

---

## ساختار پوشه‌ها

AzuDl داخل Google Drive این مسیر را می‌سازد:

```text
/content/drive/MyDrive/AzuDl-GC2GD
```

ساختار داخلی:

```text
AzuDl-GC2GD/
├── TorrentDownloads/
├── YouTubeDownloads/
├── DirectDownloads/
├── BatchDownloads/
├── Archives/
└── Logs/
```

| پوشه | کاربرد |
|---|---|
| `TorrentDownloads` | دانلودهای تورنت، مگنت و فایل `.torrent` |
| `YouTubeDownloads` | دانلودهای YouTube، پلی‌لیست و فایل صوتی |
| `DirectDownloads` | دانلود لینک‌های مستقیم |
| `BatchDownloads` | خروجی دانلودهای چندتایی |
| `Archives` | فایل‌های ZIP ساخته‌شده |
| `Logs` | تاریخچه، فایل Session و فایل‌های Debug |

---

## فایل Session برای aria2

AzuDl فایل Session مربوط به aria2 را اینجا ذخیره می‌کند:

```text
/content/drive/MyDrive/AzuDl-GC2GD/Logs/aria2.session
```

این فایل کمک می‌کند aria2 بعد از اجرای دوباره نوت‌بوک، دانلودهای نیمه‌کاره را دوباره بشناسد.

AzuDl از تنظیمات زیر استفاده می‌کند:

```text
--continue=true
--always-resume=true
--save-session
--input-file
--force-save=true
```

این باعث می‌شود دانلودها تا حد ممکن قابل ادامه دادن باشند.

---

## نکته مهم درباره تایم‌اوت Google Colab

AzuDl تایم‌اوت Google Colab را دور نمی‌زند. Google Colab ممکن است بسته به شرایط، Runtime را قطع کند؛ مخصوصاً وقتی Runtime طولانی‌مدت یا Idle باشد.

AzuDl فقط تلاش می‌کند دانلودها مقاوم‌تر باشند، با استفاده از ذخیره Session برای aria2، ذخیره فایل‌ها مستقیم روی Google Drive، فعال کردن Resume در aria2، تشخیص تورنت‌های تکراری و ادامه دادن تسک‌های قبلی aria2.

برای دانلودهای طولانی‌مدت یا سید دائمی تورنت، بهتر است از VPS یا Seedbox استفاده شود.

---

## لینک‌های پشتیبانی‌شده

AzuDl می‌تواند این نوع لینک‌ها را تشخیص دهد:

```text
magnet:?...
https://example.com/file.zip
https://example.com/file.torrent
https://youtube.com/...
https://youtu.be/...
```

| نوع لینک | پشتیبانی |
|---|---|
| لینک مستقیم HTTP/HTTPS | دارد |
| لینک FTP | دارد |
| ویدیو YouTube | دارد |
| پلی‌لیست YouTube | دارد |
| Magnet | دارد |
| فایل `.torrent` از URL | دارد |
| فایل `.torrent` محلی | دارد |
| دانلود چندتایی | دارد |

---

## دانلود لینک مستقیم

AzuDl لینک‌های مستقیم را با aria2 دانلود می‌کند.

مثال:

```text
https://example.com/file.zip
https://example.com/video.mp4
https://example.com/archive.rar
https://example.com/document.pdf
```

گزینه‌های اختیاری:

- نام پوشه
- نام فایل خروجی
- محدودیت سرعت
- Header اختصاصی به صورت JSON

نمونه Header:

```json
{"User-Agent":"Mozilla/5.0","Referer":"https://example.com"}
```

---

## دانلود از YouTube

AzuDl برای دانلود از YouTube از `yt-dlp` استفاده می‌کند.

قابلیت‌ها:

- دانلود با بهترین کیفیت
- محدود کردن کیفیت
- دانلود فقط صدا
- تبدیل صدا به MP3
- دانلود پلی‌لیست
- انتخاب Custom Format ID
- ذخیره Metadata
- ذخیره Thumbnail

کیفیت‌های قابل انتخاب:

```text
best
4320
2160
1440
1080
720
480
360
```

---

## رفع مشکل بی‌صدا بودن ویدیوهای YouTube

بعضی از فرمت‌های YouTube، مخصوصاً کیفیت‌های بالا، فقط تصویر هستند و صدا ندارند.

مثلاً:

```text
137
```

معمولاً فقط ویدیو است.

AzuDl به‌صورت خودکار تلاش می‌کند بهترین صدای موجود را به آن اضافه کند:

```text
137 -> 137+ba/best
```

نمونه‌های بهتر برای Custom Format:

```text
137+140
248+251
22
18
best
```

---

## استخراج MP3

برای دانلود فقط صدا، در زمان سؤال زیر:

```text
Audio only? y/n
```

گزینه زیر را وارد کنید:

```text
y
```

خروجی به شکل زیر ساخته می‌شود:

```text
MP3 320kbps
```

---

## دانلود تورنت

AzuDl از این حالت‌ها پشتیبانی می‌کند:

- Magnet link
- فایل `.torrent` از URL
- فایل `.torrent` محلی
- حالت تورنت خصوصی
- سید دادن اختیاری
- نمایش پیشرفت دانلود
- نمایش وضعیت سید
- تشخیص InfoHash تکراری
- ادامه دانلود با aria2 Session

### نمونه Magnet

```text
magnet:?xt=urn:btih:EXAMPLE_HASH
```

مسیر استفاده:

```text
Torrent Tools > Torrent magnet
```

### نمونه فایل Torrent

```text
https://example.com/file.torrent
```

مسیر استفاده:

```text
Torrent Tools > Torrent file
```

برای تورنت‌های عمومی، گزینه `Torrent file` مناسب‌تر است، نه `Private torrent`.

---

## حالت Private Torrent

حالت Private Torrent برای ترکرهای خصوصی ساخته شده است.

مسیر استفاده:

```text
Torrent Tools > Private torrent
```

ورودی پیشنهادی:

```text
فایل .torrent اختصاصی از ترکر خصوصی
```

در حالت خصوصی، این موارد خاموش می‌شوند:

```text
DHT
DHT6
PEX
LPD
```

این کار برای ترکرهای خصوصی مهم است، چون خیلی از ترکرهای خصوصی اجازه Peer Discovery عمومی را نمی‌دهند.

---

## سید دادن

وقتی AzuDl می‌پرسد:

```text
Keep seeding after download? y/n
```

اگر می‌خواهید بعد از دانلود سید بدهد، وارد کنید:

```text
y
```

AzuDl وضعیت سید را زنده نمایش می‌دهد:

```text
سرعت آپلود
حجم آپلودشده
Ratio
تعداد Connection
تعداد Seeder
زمان سپری‌شده سید
```

نمونه خروجی:

```text
Seeding Upload: up=1.20 MB/s, uploaded=350.40 MB, ratio=0.42, connections=8, seeders=12, time=08:31
```

سید فقط تا زمانی ادامه دارد که Runtime گوگل کلب روشن باشد. برای سید طولانی‌مدت، بهتر است از VPS، Seedbox یا Dedicated Server استفاده شود.

---

## چرا برای Seed Time عدد 525600 استفاده شده؟

بعضی نسخه‌های aria2 مقدار زیر را قبول نمی‌کنند:

```text
seed-time=-1
```

برای همین AzuDl از این مقدار استفاده می‌کند:

```text
525600
```

یعنی 525600 دقیقه، تقریباً یک سال. از آنجا که Colab خیلی زودتر از یک سال قطع می‌شود، این مقدار در عمل یعنی تا وقتی Runtime روشن است سید بده.

---

## تشخیص تورنت تکراری

AzuDl قبل از اضافه کردن فایل `.torrent`، مقدار InfoHash را می‌خواند.

اگر همان تورنت قبلاً داخل aria2 وجود داشته باشد، AzuDl این کارها را انجام می‌دهد:

- تورنت موجود را تشخیص می‌دهد
- GID موجود را نمایش می‌دهد
- همان تسک قبلی را ادامه یا مانیتور می‌کند
- اگر تسک قبلی خطادار باشد، آن را حذف می‌کند و تورنت را دوباره اضافه می‌کند

این باعث می‌شود اجرای دوباره یک تورنت باعث Duplicate و خطای aria2 نشود.

---

## وضعیت aria2

مسیر:

```text
Torrent Tools > aria2 status
```

این بخش اطلاعات زیر را نمایش می‌دهد:

```text
GID
Status
Name
InfoHash
Progress
Completed size
Download speed
Upload speed
Uploaded size
Ratio
Connections
Seeders
Errors
```

---

## حذف یک تسک تورنت

مسیر:

```text
Torrent Tools > Remove aria2 GID
```

بعد GID موردنظر را وارد کنید.

این قابلیت برای موارد زیر کاربرد دارد:

- تورنت گیر کرده
- تورنت تکراری ثبت شده
- تورنت خطا دارد
- می‌خواهید سید را متوقف کنید

---

## دانلود چندتایی

Batch Download اجازه می‌دهد چند لینک را پشت سر هم وارد کنید.

در حالت Batch این لینک‌ها پشتیبانی می‌شوند:

- لینک مستقیم
- لینک YouTube
- Magnet
- فایل `.torrent`

لینک‌های ناشناخته رد می‌شوند.

---

## تاریخچه دانلود

AzuDl تاریخچه دانلودها را اینجا ذخیره می‌کند:

```text
/content/drive/MyDrive/AzuDl-GC2GD/Logs/download_history.json
```

تاریخچه شامل نوع دانلود، لینک منبع، مسیر خروجی، وضعیت، زمان، فرمت، حالت سید و خطا است.

---

## ابزارهای مدیریت فایل

AzuDl ابزارهای ساده برای مدیریت فایل دارد:

```text
نمایش فایل‌های دانلودشده
نمایش آخرین فایل
گزارش فضای Google Drive
SHA256 فایل آخر
SHA256 فایل انتخابی
ZIP کردن پوشه
ZIP کردن آخرین پوشه دانلودشده
```

خروجی ZIP در این مسیر ذخیره می‌شود:

```text
/content/drive/MyDrive/AzuDl-GC2GD/Archives
```

---

## نمونه محدودیت سرعت

```text
500K
2M
10M
```

اگر نمی‌خواهید محدودیت سرعت بگذارید، خالی بگذارید.

---

## پیش‌نیازها

AzuDl داخل Colab پکیج‌های لازم را نصب می‌کند:

```bash
apt install -y aria2 ffmpeg p7zip-full
pip install tqdm requests yt-dlp
```

| ابزار | کاربرد |
|---|---|
| aria2 | دانلود لینک مستقیم، مگنت و تورنت |
| ffmpeg | ادغام ویدیو و صدا و استخراج MP3 |
| yt-dlp | موتور دانلود YouTube |
| tqdm | نمایش نوار پیشرفت |
| requests | درخواست‌های HTTP |
| p7zip-full | پشتیبانی از آرشیو |

---

## روش استفاده

1. وارد Google Colab شوید: `https://colab.research.google.com`
2. یک Notebook جدید بسازید.
3. کد کامل AzuDl را داخل یک Cell قرار دهید.
4. Cell را اجرا کنید.
5. اجازه اتصال Google Drive را بدهید.
6. از منوی برنامه گزینه موردنظر را انتخاب کنید.

---

## پیشنهاد استفاده

برای تورنت عمومی:

```text
Torrent Tools > Torrent file
```

برای ترکر خصوصی:

```text
Torrent Tools > Private torrent
```

برای YouTube:

```text
YouTube video or playlist
```

برای لینک مستقیم:

```text
Direct link
```

برای تشخیص خودکار:

```text
Auto detect link
```

---

## نکته قانونی

از AzuDl فقط برای دانلود، ذخیره یا توزیع محتوایی استفاده کنید که حق استفاده از آن را دارید. مسئولیت استفاده از پروژه و محتوای دانلودشده با کاربر است. AzuDl فقط یک ابزار دانلود است و مسئولیتی در قبال سوءاستفاده از آن ندارد.

---

## محدودیت‌ها

- Google Colab ممکن است هر زمان Runtime را قطع کند.
- Colab برای سید دائمی تورنت مناسب نیست.
- بعضی لینک‌های مستقیم نیاز به احراز هویت دارند.
- بعضی سایت‌ها IPهای Colab را محدود یا بلاک می‌کنند.
- بعضی ویدیوهای YouTube ممکن است در Colab قابل دریافت نباشند.
- برای Ratio واقعی در ترکرهای خصوصی، VPS یا Seedbox بهتر است.
- سرعت نوشتن روی Google Drive ممکن است متغیر باشد.

---

## برنامه‌نویس

```text
Developer: The Azizi
Project: AzuDl - GC2GD
Full Name: Azizi Universal Downloader - Google Colab to Google Drive
```

لینک‌ها:

- X: https://x.com/the_azzi
- GitHub: https://github.com/TheGreatAzizi
- Telegram: https://t.me/luluch_code
- Git: https://git.theazizi.ir/TheAzizi
- Website: https://theazizi.ir

---

## توضیح کوتاه برای Repository

```text
AzuDl - GC2GD یک دانلودر یونیورسال بر پایه Google Colab است که لینک مستقیم، YouTube، پلی‌لیست، Magnet، فایل Torrent و تورنت خصوصی را مستقیم روی Google Drive دانلود می‌کند و از ادامه دانلود، وضعیت زنده دانلود و سید، Batch Download، تاریخچه، ZIP و SHA256 پشتیبانی می‌کند.
```

---

## پیام Commit پیشنهادی

```text
fix(torrent): detect duplicate infohash and resume existing aria2 task
```

یا:

```text
release: AzuDl GC2GD v1.2.8
```

---

## تغییرات نسخه‌ها

### v1.2.8

- اضافه شدن تشخیص InfoHash قبل از اضافه کردن فایل `.torrent`
- اضافه شدن تشخیص تورنت تکراری
- ادامه دادن یا مانیتور کردن تسک موجود aria2 به‌جای ساخت Duplicate
- حذف خودکار تورنت خطادار و اضافه کردن دوباره آن
- بهتر شدن خروجی aria2 status با نمایش InfoHash
- حفظ منوی جدا برای Torrent Tools
- حفظ حالت Private Torrent
- حفظ نمایش زنده وضعیت سید
- حفظ Session Persistence برای aria2
- حفظ فیکس صدای YouTube
- حفظ ابزارهای ZIP، SHA256، تاریخچه و مدیریت فایل

### v1.2.7

- رفع خطای tqdm هنگام نمایش وضعیت سید

### v1.2.6

- انتقال گزینه‌های تورنت به منوی جداگانه Torrent Tools

### v1.2.5

- اضافه شدن نمایش زنده وضعیت سید
- اضافه شدن Session Persistence برای aria2
- بهتر شدن قابلیت ادامه دانلود

### v1.2.4

- رفع مشکل seed-time نامعتبر
- جایگزینی `-1` با مقدار معتبر طولانی برای سید

### v1.2.3

- بهبود اعتبارسنجی فایل `.torrent`
- بهبود پیام‌های خطای aria2 RPC

---

## لایسنس

لایسنسی را انتخاب کنید که با سیاست Repository شما هماهنگ است.

گزینه‌های پیشنهادی:

```text
MIT
Apache-2.0
GPL-3.0
```
