# 📊 XAUUSD Analyzer v7.3

[![Live Demo](https://img.shields.io/badge/🌐_Live_Demo-Open_Tool-success?style=for-the-badge)](https://mohsen-mollahasani.github.io/xauusd-analyzer/)
[![Version](https://img.shields.io/badge/version-7.3-blue?style=flat-square)](https://github.com/mohsen-mollahasani/xauusd-analyzer)
[![License](https://img.shields.io/badge/license-MIT-green?style=flat-square)](./LICENSE)
[![Languages](https://img.shields.io/badge/languages-EN%20%7C%20FA%20%7C%20RU%20%7C%20ZH-orange?style=flat-square)](#)

**A single-file, multilingual technical analysis tool for Gold (XAUUSD) with AI-ready output and TradingView integration.**

🌐 **[Try it live →](https://mohsen-mollahasani.github.io/xauusd-analyzer/)**

[🇬🇧 English](#-english) · [🇮🇷 فارسی](#-فارسی) · [🇷🇺 Русский](#-русский) · [🇨🇳 中文](#-中文)
---

## 🇬🇧 English

### Overview

XAUUSD Analyzer is a client-side, single-file HTML tool that fetches Gold spot prices (via Twelve Data API, OANDA feed), computes multi-timeframe technical indicators, identifies ranked support/resistance zones, and generates a compact, AI-ready output for use with LLMs like Claude, GPT, or DeepSeek.

It also generates ready-to-paste numbers for a companion **Pine Script** indicator on TradingView — and now tracks changes between sessions so you can instantly spot which levels shifted.

### Features

- **4 Timeframes:** 30M, 1H, 4H, Daily
- **Indicators:** EMA20/50, RSI, ATR, ADX, MACD, Ichimoku Cloud, Market Structure, Fibonacci
- **Weighted Confluence:** Daily (1.6×), 4H (1.3×), 1H (0.8×), 30M (0.6×)
- **Ranked Zones:** Nearest & Strongest Supports/Resistances
- **Final Score:** 60% Strength + 40% Proximity (ATR-based)
- **Divergence Detection:** RSI vs Price (4H & Daily)
- **Session High/Low:** Asia, London, NY (DST-aware)
- **Weekend Filter:** Removes fake weekend candles for accurate Ichimoku
- **Pine History Tracking:** Remembers last anchor levels — changed numbers appear highlighted (bold + green) in the TradingView modal
- **4 Languages:** English, Persian, Russian, Chinese
- **AI-Ready Output:** Copy once, paste into any LLM
- **TradingView Integration:** 4 copy-ready lines + Pine Script generator
- **Donation Support:** BSC wallet

### Quick Start

1. **Download** the HTML file.
2. **Open it** in any modern browser.
3. **Get a free API key** from [twelvedata.com](https://twelvedata.com) (30 sec, no credit card).
4. **Paste the key** into the "API Key Setup" box → click **Save & Test**.
5. Click **Load All** to fetch data.
6. Click **Copy for AI** → paste into your preferred LLM.
7. For chart levels: click **Copy for TradingView** → follow the on-screen guide.

### How the AI Output Works

The output includes:

- **Confluence:** Overall bias + confidence %
- **Per-TF snapshots:** Trend, RSI, ADX, MACD, Ichimoku, Structure, Fib
- **Nearest/Strongest S/R zones:** with Zone, Anchor, Dist, Final Score
- **Session High/Low**
- **Divergence flags**
- **AI Instructions:** A structured prompt that tells the LLM exactly how to respond

The output instructs the LLM to **respond in your current UI language** while keeping section headings in English.

### Pine History Tracking (v7.3)

When you click **Copy for TradingView**, the tool remembers the current set of anchor levels. Next time you use it:

- **Unchanged numbers** → normal text
- **Changed numbers** → **bold + green** highlight

This helps you instantly spot which support/resistance levels have shifted since your last analysis session.

- **First time:** all numbers appear highlighted (nothing to compare yet)
- **"Reset History" button:** clears the saved snapshot so all numbers appear highlighted again
- **Snapshot stored under:** `xauusd_last_pine` in localStorage
- **Clipboard stays clean:** only the modal display is highlighted — the copied text is plain (ready to paste into TradingView)

### TradingView Setup

1. Click **Copy for TradingView** — 4 lines are copied and the modal opens.
2. In the modal → click **Show / Copy Pine Script**.
3. Paste the Pine Script into TradingView's Pine Editor → Save → Add to chart.
4. In the indicator settings, paste each of the 4 lines into matching inputs.
5. Lines appear on your chart (Strongest = thick, Nearest = dashed).

**Tip:** Numbers highlighted in green in the modal are new/changed since your last copy.

### Privacy

- **Your API key** is stored only in your browser's `localStorage`.
- **Pine snapshot** is also stored only in `localStorage`.
- **No tracking**, no analytics, no telemetry.
- **No backend.** Everything runs client-side.

### Technical Stack

- Pure HTML/CSS/JavaScript (no frameworks, no build step)
- Twelve Data API (OANDA feed)
- `Intl.DateTimeFormat` for DST-aware sessions
- `localStorage` for language, API key, and Pine history persistence

### Known Limitations

- Data feed is Twelve Data's OANDA source — may differ slightly from your broker (1-5 USD on some candles).
- Twelve Data free tier has rate limits (~8 requests/min).
- Custom indicators are not supported on MT4/MT5 mobile — that's why we use TradingView Pine Script.
- Pine history comparison is **index-based** (same position = same zone) — since zones are always sorted descending, this works reliably.

### Version History

- **v7.3** — Pine history tracking (highlight changed levels)
- **v7.2** — Multilingual (EN/FA/RU/ZH), English session names in AI output
- **v7.1** — TradingView setup modal, Pine Script generator
- **v7.0** — English edition, API key input, donation support
- **v6.x** — Ranked zones, ATR-based proximity, weighted confluence

### Donate

If this tool helps you, consider a small donation on BSC:

```
0x63013226D82d1070eC98fBA2b3fdD6E626e9E8f6
```

⚠️ **Send only BEP-20 tokens** (BNB, USDT-BEP20, BUSD). Other networks may result in loss of funds.

---

## 🇮🇷 فارسی

### معرفی

XAUUSD Analyzer یه ابزار تحلیل تکنیکال تک‌فایل و سمت‌کاربره که قیمت لحظه‌ای طلا رو از Twelve Data (فید OANDA) می‌گیره، اندیکاتورهای چند تایم‌فریمی رو محاسبه می‌کنه، سطوح حمایت/مقاومت رتبه‌بندی‌شده رو استخراج می‌کنه، و یه خروجی فشرده آماده برای LLM هایی مثل Claude، GPT یا DeepSeek تولید می‌کنه.

همچنین اعداد آماده برای یه اندیکاتور **Pine Script** روی TradingView تولید می‌کنه — و الان تغییرات بین نشست‌ها رو هم رصد می‌کنه تا سریع بفهمی کدوم سطوح جابجا شدن.

### ویژگی‌ها

- **۴ تایم‌فریم:** 30M، 1H، 4H، Daily
- **اندیکاتورها:** EMA20/50، RSI، ATR، ADX، MACD، Ichimoku، ساختار بازار، فیبوناچی
- **هم‌رأیی وزن‌دار:** Daily (1.6×)، 4H (1.3×)، 1H (0.8×)، 30M (0.6×)
- **سطوح رتبه‌بندی‌شده:** نزدیک‌ترین و قوی‌ترین حمایت/مقاومت
- **Final Score:** ۶۰٪ قدرت + ۴۰٪ نزدیکی (بر اساس ATR)
- **تشخیص واگرایی:** RSI vs Price روی 4H و Daily
- **سقف/کف سشن:** آسیا، لندن، نیویورک (با DST خودکار)
- **فیلتر آخر هفته:** حذف کندل‌های تعطیل برای Ichimoku دقیق
- **رصد تغییرات Pine:** آخرین سطوح anchor رو به یاد می‌سپاره — اعدادی که تغییر کردن توی مودال TradingView بولد سبز نشون داده می‌شن
- **۴ زبانه:** انگلیسی، فارسی، روسی، چینی
- **خروجی آماده AI:** یه بار کپی، پیست توی هر LLM
- **یکپارچگی TradingView:** ۴ خط آماده + تولید Pine Script
- **حمایت:** ولت BSC

### شروع سریع

۱. فایل HTML رو **دانلود** کن.
۲. توی هر مرورگر مدرن **بازش کن**.
۳. یه **API Key رایگان** از [twelvedata.com](https://twelvedata.com) بگیر (۳۰ ثانیه، بدون کارت).
۴. کلید رو توی باکس **API Key Setup** پیست کن → **Save & Test**.
۵. روی **Load All** بزن.
۶. روی **Copy for AI** بزن → توی LLM مورد نظرت پیست کن.
۷. برای سطوح روی چارت: روی **Copy for TradingView** بزن و راهنما رو دنبال کن.

### نحوه‌ی کار خروجی AI

خروجی شامل:

- **Confluence:** بایاس کلی + درصد اطمینان
- **هر تایم‌فریم:** روند، RSI، ADX، MACD، Ichimoku، ساختار، فیب
- **سطوح Nearest/Strongest:** با Zone، Anchor، Dist، Final Score
- **سقف/کف سشن**
- **واگرایی‌ها**
- **دستور به AI:** پرامپت ساختاریافته که به LLM می‌گه چطور پاسخ بده

خروجی به LLM دستور می‌ده که **به زبون فعلی UI** پاسخ بده، ولی عنوان بخش‌ها انگلیسی بمونه.

### رصد تغییرات Pine (نسخه ۷.۳)

وقتی روی **Copy for TradingView** می‌زنی، ابزار آخرین سطوح anchor رو ذخیره می‌کنه. دفعه‌ی بعد:

- **اعداد بدون تغییر** → متن عادی
- **اعداد تغییرکرده** → **بولد سبز**

این کمک می‌کنه سریع بفهمی کدوم سطوح حمایت/مقاومت از آخرین تحلیل جابجا شدن.

- **بار اول:** همه‌ی اعداد بولد می‌شن (چیزی برای مقایسه نیست)
- **دکمه‌ی Reset History:** حافظه رو پاک می‌کنه تا همه بولد بشن
- **ذخیره‌سازی:** کلید `xauusd_last_pine` توی localStorage
- **کلیپ‌بورد تمیز می‌مونه:** فقط نمایش توی مودال بولد می‌شه — متن کپی‌شده ساده‌ست (آماده برای TradingView)

### راه‌اندازی TradingView

۱. روی **Copy for TradingView** بزن — ۴ خط کپی می‌شه و مودال باز می‌شه.
۲. توی مودال → **Show / Copy Pine Script** رو بزن.
۳. کد Pine رو توی Pine Editor پیست کن → Save → Add to chart.
۴. توی تنظیمات اندیکاتور، هر خط رو توی input مربوطه پیست کن.
۵. خطوط روی چارت ظاهر می‌شن (Strongest = ضخیم، Nearest = خط‌چین).

**نکته:** اعدادی که توی مودال سبز نشون داده می‌شن، از آخرین کپی جدید/تغییرکرده هستن.

### حریم خصوصی

- **API Key** فقط توی `localStorage` مرورگر خودت ذخیره می‌شه.
- **حافظه‌ی Pine** هم فقط توی `localStorage` ذخیره می‌شه.
- **هیچ tracking، آنالیتیکس یا تلمتری** وجود نداره.
- **بدون backend.** همه چیز سمت کاربر اجرا می‌شه.

### تکنولوژی

- HTML/CSS/JavaScript خالص (بدون فریمورک، بدون build)
- Twelve Data API (فید OANDA)
- `Intl.DateTimeFormat` برای سشن‌های DST-aware
- `localStorage` برای ذخیره‌ی زبان، API Key و تاریخچه‌ی Pine

### محدودیت‌ها

- فید داده OANDA هست — ممکنه با بروکرت ۱-۵ دلار اختلاف داشته باشه.
- پلن رایگان Twelve Data محدودیت درخواست داره (~۸ در دقیقه).
- اندیکاتور سفارشی روی MT4/MT5 موبایل پشتیبانی نمی‌شه — برای همین از TradingView استفاده می‌کنیم.
- مقایسه‌ی تاریخچه‌ی Pine بر اساس **ایندکس** هست (موقعیت یکسان = zone یکسان) — چون سطوح همیشه نزولی مرتب می‌شن، این روش قابلاعتماده.

### تاریخچه نسخه‌ها

- **v7.3** — رصد تغییرات Pine (بولد کردن سطوح تغییرکرده)
- **v7.2** — چندزبانه (EN/FA/RU/ZH)، اسم سشن انگلیسی در خروجی AI
- **v7.1** — مودال راهنمای TradingView، تولید Pine Script
- **v7.0** — نسخه انگلیسی، ورودی API Key، حمایت مالی
- **v6.x** — سطوح رتبه‌بندی‌شده، Proximity بر اساس ATR، هم‌رأیی وزن‌دار

### حمایت

اگه این ابزار بهت کمک کرد، یه دونیت کوچیک روی BSC ممنون می‌شم:

```
0x63013226D82d1070eC98fBA2b3fdD6E626e9E8f6
```

⚠️ **فقط توکن‌های BEP-20** (BNB، USDT-BEP20، BUSD) بفرست. شبکه‌های دیگه ممکنه باعث از دست رفتن وجه بشه.

---

## 🇷🇺 Русский

### Обзор

XAUUSD Analyzer — это одностраничный HTML-инструмент, работающий в браузере, который получает цены на золото (через API Twelve Data, фид OANDA), рассчитывает многотаймфреймовые технические индикаторы, определяет ранжированные зоны поддержки/сопротивления и формирует компактный вывод, готовый к использованию в LLM (Claude, GPT, DeepSeek).

Также генерирует готовые числа для индикатора **Pine Script** в TradingView — и теперь отслеживает изменения между сессиями, чтобы вы сразу видели, какие уровни сдвинулись.

### Возможности

- **4 таймфрейма:** 30M, 1H, 4H, Daily
- **Индикаторы:** EMA20/50, RSI, ATR, ADX, MACD, Ichimoku, структура рынка, Fibonacci
- **Взвешенная конвергенция:** Daily (1.6×), 4H (1.3×), 1H (0.8×), 30M (0.6×)
- **Ранжированные зоны:** Ближайшие и Сильнейшие поддержки/сопротивления
- **Итоговый балл:** 60% сила + 40% близость (по ATR)
- **Дивергенция:** RSI vs Price (4H и Daily)
- **Максимум/минимум сессии:** Азия, Лондон, Нью-Йорк (с учётом DST)
- **Фильтр выходных:** Удаляет фальшивые свечи выходных для точного Ichimoku
- **Отслеживание Pine:** Запоминает последние уровни anchor — изменённые числа выделяются (жирный + зелёный) в модальном окне TradingView
- **4 языка:** английский, персидский, русский, китайский
- **Вывод для AI:** Копировать один раз — вставить в любой LLM
- **Интеграция с TradingView:** 4 готовые строки + генератор Pine Script
- **Поддержка:** BSC-кошелёк

### Быстрый старт

1. **Скачайте** HTML-файл.
2. **Откройте** его в любом современном браузере.
3. Получите **бесплатный API-ключ** на [twelvedata.com](https://twelvedata.com) (30 сек, без карты).
4. Вставьте ключ в поле **API Key Setup** → **Save & Test**.
5. Нажмите **Load All**.
6. Нажмите **Copy for AI** → вставьте в ваш LLM.
7. Для уровней на графике: **Copy for TradingView** → следуйте руководству.

### Как работает вывод AI

Вывод содержит:

- **Confluence:** Общий биас + уверенность %
- **Каждый TF:** Тренд, RSI, ADX, MACD, Ichimoku, структура, Fib
- **Зоны Nearest/Strongest:** Zone, Anchor, Dist, Final Score
- **Максимум/минимум сессии**
- **Дивергенции**
- **Инструкции для AI:** Структурированный промпт

Вывод говорит LLM **отвечать на текущем языке интерфейса**, сохраняя заголовки разделов на английском.

### Отслеживание Pine (v7.3)

Когда вы нажимаете **Copy for TradingView**, инструмент запоминает текущий набор уровней anchor. В следующий раз:

- **Неизменённые числа** → обычный текст
- **Изменённые числа** → **жирный + зелёный**

Это помогает сразу видеть, какие уровни поддержки/сопротивления сместились с прошлой сессии анализа.

- **Первый раз:** все числа выделены (не с чем сравнивать)
- **Кнопка "Reset History":** очищает сохранённый снимок, чтобы все числа снова выделялись
- **Снимок хранится под ключом:** `xauusd_last_pine` в localStorage
- **Буфер обмена остаётся чистым:** выделение только в модальном окне — скопированный текст простой (готов для TradingView)

### Настройка TradingView

1. Нажмите **Copy for TradingView** — 4 строки скопированы и открывается модальное окно.
2. В окне → **Show / Copy Pine Script**.
3. Вставьте Pine Script в редактор TradingView → Save → Add to chart.
4. В настройках индикатора вставьте каждую из 4 строк в нужное поле.
5. Линии появятся на графике (Strongest = толстые, Nearest = пунктирные).

**Совет:** числа, выделенные зелёным в модальном окне, новые или изменённые с момента последнего копирования.

### Приватность

- **Ваш API-ключ** хранится только в `localStorage` браузера.
- **Снимок Pine** также хранится только в `localStorage`.
- **Нет отслеживания**, аналитики, телеметрии.
- **Без backend.** Всё работает на стороне клиента.

### Технологии

- Чистый HTML/CSS/JavaScript (без фреймворков и сборки)
- Twelve Data API (фид OANDA)
- `Intl.DateTimeFormat` для сессий с DST
- `localStorage` для языка, API-ключа и истории Pine

### Известные ограничения

- Данные — от OANDA — могут незначительно отличаться от вашего брокера (1-5 USD).
- Бесплатный тариф Twelve Data имеет лимиты (~8 запросов/мин).
- Пользовательские индикаторы не поддерживаются в MT4/MT5 mobile — поэтому используется Pine Script.
- Сравнение истории Pine **по индексу** (одна позиция = одна зона) — так как зоны всегда отсортированы по убыванию, это работает надёжно.

### История версий

- **v7.3** — Отслеживание Pine (выделение изменённых уровней)
- **v7.2** — Многоязычность (EN/FA/RU/ZH), английские названия сессий в выводе AI
- **v7.1** — Модальное окно TradingView, генератор Pine Script
- **v7.0** — Английская версия, ввод API-ключа, поддержка донатами
- **v6.x** — Ранжированные зоны, ATR-based близость, взвешенная конвергенция

### Поддержать

Если инструмент помог, буду признателен за небольшое пожертвование в BSC:

```
0x63013226D82d1070eC98fBA2b3fdD6E626e9E8f6
```

⚠️ **Отправляйте только токены BEP-20** (BNB, USDT-BEP20, BUSD). Другие сети могут привести к потере средств.

---

## 🇨🇳 中文

### 概述

XAUUSD Analyzer 是一款单文件、浏览器端的 HTML 工具。它通过 Twelve Data API（OANDA 数据源）获取黄金现货价格，计算多周期技术指标，识别分级支撑/阻力区域，并生成紧凑的、可供 LLM（如 Claude、GPT、DeepSeek）使用的输出。

同时生成可直接粘贴到 TradingView **Pine Script** 指标的数值 — 并新增会话间变化追踪，让您一眼看出哪些水平发生移动。

### 功能特性

- **4 个时间周期：** 30M、1H、4H、日线
- **指标：** EMA20/50、RSI、ATR、ADX、MACD、一目均衡表、市场结构、斐波那契
- **加权汇合：** 日线（1.6×）、4H（1.3×）、1H（0.8×）、30M（0.6×）
- **分级区域：** 最近与最强支撑/阻力
- **最终评分：** 60% 强度 + 40% 接近度（基于 ATR）
- **背离检测：** RSI 与价格（4H 和日线）
- **时段高/低：** 亚洲、伦敦、纽约（自动处理夏令时）
- **周末过滤：** 移除虚假周末蜡烛，确保 Ichimoku 准确
- **Pine 变化追踪：** 记住上次的锚点水平 — 变化数字在 TradingView 弹窗中以**粗体 + 绿色**高亮显示
- **4 种语言：** 英语、波斯语、俄语、中文
- **AI 就绪输出：** 复制一次，粘贴到任意 LLM
- **TradingView 集成：** 4 行即用数据 + Pine Script 生成器
- **捐赠支持：** BSC 钱包

### 快速开始

1. **下载** HTML 文件。
2. 在任意现代浏览器中**打开**。
3. 从 [twelvedata.com](https://twelvedata.com) 获取**免费 API 密钥**（30 秒，无需信用卡）。
4. 将密钥粘贴到 **API Key Setup** 框中 → 点击 **Save & Test**。
5. 点击 **Load All**。
6. 点击 **Copy for AI** → 粘贴到您喜欢的 LLM。
7. 如需图表水平：点击 **Copy for TradingView** → 按屏幕指南操作。

### AI 输出如何工作

输出包含：

- **Confluence：** 整体偏向 + 置信度 %
- **每个周期：** 趋势、RSI、ADX、MACD、一目均衡表、结构、Fib
- **Nearest/Strongest 支撑阻力区：** 含 Zone、Anchor、Dist、Final Score
- **时段高/低**
- **背离标记**
- **AI 指令：** 结构化提示，告诉 LLM 如何响应

输出会指示 LLM **使用当前界面语言回答**，同时保持小节标题为英文。

### Pine 变化追踪（v7.3）

当您点击 **Copy for TradingView** 时，工具会记住当前的锚点水平集合。下次使用时：

- **未变化的数字** → 普通文本
- **变化的数字** → **粗体 + 绿色**高亮

这帮助您立即看出自上次分析会话以来哪些支撑/阻力水平发生了移动。

- **首次使用：** 所有数字都会高亮（无对比对象）
- **"Reset History" 按钮：** 清除保存的快照，使所有数字再次高亮
- **快照存储键：** localStorage 中的 `xauusd_last_pine`
- **剪贴板保持干净：** 仅弹窗中的显示高亮 — 复制的文本是纯文本（可直接粘贴到 TradingView）

### TradingView 设置

1. 点击 **Copy for TradingView** — 已复制 4 行，并打开弹窗。
2. 在弹窗中 → 点击 **Show / Copy Pine Script**。
3. 将 Pine Script 粘贴到 TradingView 的 Pine 编辑器中 → Save → Add to chart。
4. 在指标设置中，将 4 行分别粘贴到对应输入框。
5. 线条出现在图表上（最强 = 粗线，最近 = 虚线）。

**提示：** 弹窗中绿色高亮的数字是自上次复制以来新增或变化的。

### 隐私

- **您的 API 密钥** 仅存储在浏览器的 `localStorage` 中。
- **Pine 快照** 也仅存储在 `localStorage` 中。
- **无跟踪**、无分析、无遥测。
- **无后端。** 全部在客户端运行。

### 技术栈

- 纯 HTML/CSS/JavaScript（无框架、无构建）
- Twelve Data API（OANDA 数据源）
- `Intl.DateTimeFormat` 用于夏令时时段
- `localStorage` 用于语言、API 密钥和 Pine 历史持久化

### 已知限制

- 数据源为 OANDA，可能与您的经纪商略有差异（部分蜡烛差 1-5 美元）。
- Twelve Data 免费套餐有限速（约 8 次/分钟）。
- MT4/MT5 移动端不支持自定义指标 — 因此使用 TradingView Pine Script。
- Pine 历史对比基于**索引**（相同位置 = 同一区域）— 由于区域始终按降序排列，该方法可靠。

### 版本历史

- **v7.3** — Pine 变化追踪（高亮变化的水平）
- **v7.2** — 多语言（EN/FA/RU/ZH），AI 输出中使用英文时段名称
- **v7.1** — TradingView 设置弹窗，Pine Script 生成器
- **v7.0** — 英文版，API 密钥输入，捐赠支持
- **v6.x** — 分级区域、基于 ATR 的接近度、加权汇合

### 捐赠

如果本工具对您有帮助，欢迎通过 BSC 小额捐赠：

```
0x63013226D82d1070eC98fBA2b3fdD6E626e9E8f6
```

⚠️ **请仅发送 BEP-20 代币**（BNB、USDT-BEP20、BUSD）。其他网络可能导致资金损失。

---

## 📄 License

MIT License

Copyright (c) 2026

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software.

---

## 🤝 Contributing

Suggestions, bug reports, and improvements are welcome. This is a personal project — but ideas that make it more robust, accurate, or user-friendly are always appreciated.

---

## ⚠️ Disclaimer

This tool is for **educational and informational purposes only**. It is **not financial advice**. Trading Gold and other financial instruments carries a high level of risk. Always do your own research and consult a licensed financial advisor before making trading decisions.

---

**Made with ☕ and lots of debugging.**
