# SinaGoldAPI - وب‌سرویس قیمت لحظه‌ای طلا و سکه 🇮🇷💰

SinaGoldAPI یک وب‌سرویس سبک و سریع برای دریافت قیمت لحظه‌ای **طلا**، **سکه** و **آبشده** از معتبرترین منبع نرخ‌ها در ایران است.

- بدون نیاز به **توکن** ✅
- سرعت بالا و کاملاً به‌روز ✅
- مناسب برای ربات‌ها، اپلیکیشن‌ها و وبسایت‌ها ✅

---

## 🌐 Endpoint

```
https://gold.api-sina-free.workers.dev/gold
```

---

## 📦 خروجی وب‌سرویس

| کلید | نوع | توضیح |
|-----|-----|--------|
| gold_18_ayar | number | قیمت هر گرم طلای ۱۸ عیار |
| gold_24_ayar | number | قیمت هر گرم طلای ۲۴ عیار |
| gold_second_hand | number | طلای دست دوم |
| mesghal_tala | number | قیمت هر مثقال طلا |
| abshode_naghd | number | آبشده نقدی |
| abshode_moamelati | number | آبشده معاملاتی |
| sekke_emami | number | سکه امامی |
| sekke_bahar_azadi | number | سکه بهار آزادی |
| nim_sekke | number | نیم‌سکه |
| rob_sekke | number | ربع‌سکه |
| sekke_gerami | number | سکه گرمی |
| habab_emami | number | حباب سکه امامی |
| habab_bahar | number | حباب بهار آزادی |
| habab_nim | number | حباب نیم سکه |
| habab_rob | number | حباب ربع سکه |
| habab_gerami | number | حباب سکه گرمی |
| updated_at | string | زمان بروزرسانی |
| source | string | منبع نرخ‌ها |

---

## 🧪 نمونه درخواست

```
GET https://gold.api-sina-free.workers.dev/gold
```

---

## 📝 نمونه خروجی

```json
{
  "gold_18_ayar": 104989000,
  "gold_24_ayar": 139983000,
  "gold_second_hand": 103588700,
  "mesghal_tala": 454890000,
  "abshode_naghd": 454740000,
  "abshode_moamelati": 454750000,
  "sekke_emami": 1114050000,
  "sekke_bahar_azadi": 1044300000,
  "nim_sekke": 582000000,
  "rob_sekke": 336000000,
  "sekke_gerami": 164000000,
  "habab_emami": 96460000,
  "habab_bahar": 27160000,
  "habab_nim": 73470000,
  "habab_rob": 81710000,
  "habab_gerami": 38910000,
  "updated_at": "2025-11-06T12:19:14.378Z",
  "source": "tgju.org"
}
```

---

## 💻 نمونه استفاده در Python

```python
import requests

data = requests.get("https://gold.api-sina-free.workers.dev/gold").json()

print("طلای 18 عیار:", data["gold_18_ayar"])
print("سکه امامی:", data["sekke_emami"])
print("زمان بروزرسانی:", data["updated_at"])
```

---

## 🤖 نمونه استفاده در ربات Rubika (rubpy)

```python
from rubpy import Client, filters
import requests

bot = Client(name="sina_gold")

@bot.on_message_updates(filters.text)
async def handler(message):
    if message.text == "قیمت طلا":
        data = requests.get("https://gold.api-sina-free.workers.dev/gold").json()
        await message.reply(
            f"💰 قیمت لحظه‌ای طلا:

"
            f"طلای ۱۸ عیار: {data['gold_18_ayar']:,} تومان
"
            f"سکه امامی: {data['sekke_emami']:,} تومان
"
            f"نیم سکه: {data['nim_sekke']:,} تومان
"
            f"
⏱ بروزرسانی: {data['updated_at']}"
        )

bot.run()
```

---

## 🟢 چرا SinaGoldAPI؟

| ویژگی | توضیح |
|------|------|
| بی‌نیاز از توکن | بدون محدودیت اولیه |
| سرعت بسیار بالا | میزبانی روی Cloudflare Workers |
| مناسب برنامه‌نویسان | پاسخ JSON استاندارد |
| همیشه بروز | نرخ‌ها از معتبرترین منبع دریافت می‌شود |
