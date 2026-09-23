# 📊 XAUUSD Analyzer v7.5.1

[![Live Demo](https://img.shields.io/badge/🌐_Live_Demo-Open_Tool-success?style=for-the-badge)](https://mohsen-mollahasani.github.io/xauusd-analyzer/)
[![Version](https://img.shields.io/badge/version-7.5.1-blue?style=flat-square)](https://github.com/mohsen-mollahasani/xauusd-analyzer)
[![License](https://img.shields.io/badge/license-MIT-green?style=flat-square)](./LICENSE)
[![Languages](https://img.shields.io/badge/languages-EN%20%7C%20FA%20%7C%20RU%20%7C%20ZH-orange?style=flat-square)](#)

**A single-file, multilingual technical analysis tool for Gold (XAUUSD) with AI-ready output and TradingView integration.**

🌐 **[Try it live →](https://mohsen-mollahasani.github.io/xauusd-analyzer/)**

[🇬🇧 English](#-english) · [🇮🇷 فارسی](#-فارسی) · [🇷🇺 Русский](#-русский) · [🇨🇳 中文](#-中文)
---

## 🇬🇧 English

### Overview

XAUUSD Analyzer is a client-side, single-file HTML tool that fetches Gold spot prices (via Twelve Data API, OANDA feed), computes multi-timeframe technical indicators, identifies ranked support/resistance zones, and generates a compact, AI-ready output for use with LLMs like Claude, GPT, or DeepSeek.

It also generates ready-to-paste numbers for a companion **Pine Script** indicator on TradingView.

### Features

- **5 Timeframes:** 30M, 1H, 4H, Daily, Weekly
- **Indicators:** EMA20/50, RSI, ATR, ADX, MACD, Ichimoku Cloud, Market Structure, Fibonacci
- **Weighted Confluence:** Weekly (1.5×), Daily (1.2×), 4H (1.0×), 1H (0.6×), 30M (0.4×)
- **Ranked Zones:** Nearest & Strongest Supports/Resistances
- **Final Score:** 60% Strength + 40% Proximity (ATR-based)
- **Tier System:** A/B/C based on Age + Touch + Strength
- **Daily/Weekly Cache:** Reduces API calls, faster repeat loads
- **Force Refresh:** Clear cache with one click
- **Divergence Detection:** RSI vs Price (4H & Daily)
- **Session High/Low:** Asia, London, NY (DST-aware)
- **Weekend Filter:** Removes fake weekend candles for accurate Ichimoku
- **Pine History Tracking:** Remembers last anchor levels
- **4 Languages:** English, Persian, Russian, Chinese
- **AI-Ready Output:** Copy once, paste into any LLM
- **TradingView Integration:** 40-value single-line + Pine Script generator
- **Donation Support:** BSC wallet

### Quick Start

1. **Download** the HTML file.
2. **Open it** in any modern browser.
3. **Get a free API key** from [twelvedata.com](https://twelvedata.com) (30 sec, no credit card).
4. **Paste the key** into the "API Key Setup" box → click **Save & Test**.
5. Click **Load All** to fetch data.
6. Click **Copy for AI** → paste into your preferred LLM.
7. For chart levels: click **TradingView Guide** → **Copy Line** → paste into Pine input.

### How the AI Output Works

The output includes:

- **Confluence:** Overall bias + confidence % (5 TF weighted)
- **Per-TF snapshots:** Trend, RSI, ADX, MACD, Ichimoku, Structure, Fib
- **Nearest/Strongest S/R zones:** with Zone, Anchor, Dist, Final Score, Tier
- **Session High/Low**
- **Divergence flags**
- **Cache status**
- **AI Instructions:** A structured prompt that tells the LLM exactly how to respond

The output instructs the LLM to **respond in your current UI language** (English section headings are kept).

### Tier System (v7.5.1)

Each S/R zone gets a **Tier** based on three factors:

- **Age** — how many days since the first Daily swing confirmed it
- **Touch** — how many times Daily price reacted to it
- **Strength** — structural strength (0-100)

**Scoring:**
- Age ≥ 30 days → +1 | 14-30 days → +0.5
- Touch ≥ 3 → +1 | 2 → +0.5
- Strength ≥ 50 → +1 | 40-49 → +0.5

**Tier:**
- **A** = score ≥ 2.0 (old + tested)
- **B** = score ≥ 1.0 (medium)
- **C** = score < 1.0 (new/untested)

### Cache System (v7.5.1)

- **Daily** and **Weekly** timeframes are cached in `localStorage`
- **Cache is time-based:** refetched only when the candle period changes
  - Daily: once per UTC day (00:00)
  - Weekly: once per UTC week (Saturday 00:00)
- **Force Refresh** button clears all cache and re-fetches everything
- **Cache status badge** on each card: 📦 Cached / 🔴 Fresh

**Result:** ~60% fewer API calls on repeat loads.

### Pine History Tracking

When you click **Copy for TradingView**, the tool remembers the current set of anchor levels. Next time:

- **Unchanged numbers** → normal text
- **Changed numbers** → **bold + green** highlight

### TradingView Setup

1. Click **TradingView Guide** — modal opens.
2. Click **Show / Copy Pine Script** → paste into TradingView Pine Editor → Save → Add to chart.
3. Click **Copy Line** → 40-value single line is copied.
4. In the indicator settings, paste it into the "All Zones" field.
5. Lines appear on your chart:
   - 🟡 Tier A (thick/gold)
   - 🟠 Tier B (medium/orange)
   - ⚪ Tier C (thin/gray)
   - 🔵 Weekly (blue, thickest)

### Privacy

- **Your API key** is stored only in your browser's `localStorage`.
- **Pine snapshot** and **Daily/Weekly cache** are also in `localStorage`.
- **No tracking**, no analytics, no telemetry.
- **No backend.** Everything runs client-side.

### Technical Stack

- Pure HTML/CSS/JavaScript (no frameworks, no build step)
- Twelve Data API (OANDA feed)
- `Intl.DateTimeFormat` for DST-aware sessions
- `localStorage` for language, API key, Pine history, and cache

### Known Limitations

- Data feed is Twelve Data's OANDA source — may differ slightly from your broker (1-5 USD on some candles).
- Twelve Data free tier has rate limits (~8 requests/min).
- Custom indicators are not supported on MT4/MT5 mobile — that's why we use TradingView Pine Script.
- Weekly data limited to last 200 candles (~4 years).
- Tier calculation is Daily-based (industry standard).

### Version History

- **v7.5.1** — Weekly TF, Daily/Weekly Cache, Fixed Tier (Daily-only Age/Touch)
- **v7.5** — Weekly timeframe added, cache system
- **v7.4** — Tier system (Age + Touch + Strength), 40-value Pine
- **v7.3** — Pine history tracking
- **v7.2** — Multilingual (EN/FA/RU/ZH), English session names in AI output
- **v7.1** — TradingView modal, Pine Script generator
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

همچنین اعداد آماده برای یه اندیکاتور **Pine Script** روی TradingView تولید می‌کنه.

### ویژگی‌ها

- **۵ تایم‌فریم:** 30M، 1H، 4H، Daily، Weekly
- **اندیکاتورها:** EMA20/50، RSI، ATR، ADX، MACD، Ichimoku، ساختار بازار، فیبوناچی
- **هم‌رأیی وزن‌دار:** Weekly (1.5×)، Daily (1.2×)، 4H (1.0×)، 1H (0.6×)، 30M (0.4×)
- **سطوح رتبه‌بندی‌شده:** نزدیک‌ترین و قوی‌ترین حمایت/مقاومت
- **Final Score:** ۶۰٪ قدرت + ۴۰٪ نزدیکی (بر اساس ATR)
- **سیستم Tier:** A/B/C بر اساس Age + Touch + Strength
- **کش Daily/Weekly:** کاهش مصرف API، لود سریع‌تر
- **Force Refresh:** پاک کردن کش با یه کلیک
- **تشخیص واگرایی:** RSI vs Price روی 4H و Daily
- **سقف/کف سشن:** آسیا، لندن، نیویورک (با DST خودکار)
- **فیلتر آخر هفته:** حذف کندل‌های تعطیل
- **رصد تغییرات Pine:** آخرین سطوح anchor رو به یاد می‌سپاره
- **۴ زبانه:** انگلیسی، فارسی، روسی، چینی
- **خروجی آماده AI:** یه بار کپی، پیست توی هر LLM
- **یکپارچگی TradingView:** خط ۴۰ مقداری + تولید Pine Script
- **حمایت:** ولت BSC

### شروع سریع

۱. فایل HTML رو **دانلود** کن.
۲. توی هر مرورگر مدرن **بازش کن**.
۳. یه **API Key رایگان** از [twelvedata.com](https://twelvedata.com) بگیر.
۴. کلید رو توی **API Key Setup** پیست کن → **Save & Test**.
۵. روی **Load All** بزن.
۶. روی **Copy for AI** بزن → توی LLM مورد نظرت پیست کن.
۷. برای سطوح روی چارت: **TradingView Guide** → **Copy Line** → توی Pine پیست کن.

### سیستم Tier (نسخه ۷.۵.۱)

هر zone یه **Tier** می‌گیره بر اساس سه معیار:

- **Age** — چند روز از اولین تأیید Daily می‌گذره
- **Touch** — چند بار قیمت Daily بهش واکنش داده
- **Strength** — قدرت ساختاری (0-100)

**امتیاز:**
- Age ≥ ۳۰ روز → +1 | ۱۴-۳۰ روز → +0.5
- Touch ≥ ۳ → +1 | ۲ → +0.5
- Strength ≥ ۵۰ → +1 | ۴۰-۴۹ → +0.5

**Tier:**
- **A** = امتیاز ≥ ۲.۰ (قدیمی + تست‌شده)
- **B** = امتیاز ≥ ۱.۰ (متوسط)
- **C** = امتیاز < ۱.۰ (جدید)

### سیستم کش (نسخه ۷.۵.۱)

- **Daily** و **Weekly** توی `localStorage` کش می‌شن
- **کش زمان‌محوره:** فقط وقتی کندل جدید بسته می‌شه، دوباره fetch می‌شه
  - Daily: هر روز UTC (00:00)
  - Weekly: هر هفته UTC (شنبه 00:00)
- دکمه‌ی **Force Refresh** همه‌ی کش رو پاک می‌کنه
- **Cache badge** روی هر کارت: 📦 Cached / 🔴 Fresh

**نتیجه:** ~۶۰٪ کاهش مصرف API.

### راه‌اندازی TradingView

۱. روی **TradingView Guide** بزن — مودال باز می‌شه.
۲. **Show / Copy Pine Script** → توی Pine Editor پیست کن → Save → Add to chart.
۳. **Copy Line** → خط ۴۰ مقداری کپی می‌شه.
۴. توی تنظیمات اندیکاتور، توی فیلد "All Zones" پیست کن.
۵. خطوط ظاهر می‌شن:
   - 🟡 Tier A (ضخیم/طلایی)
   - 🟠 Tier B (متوسط/نارنجی)
   - ⚪ Tier C (نازک/خاکستری)
   - 🔵 Weekly (آبی، ضخیم‌ترین)

### حریم خصوصی

- **API Key** فقط توی `localStorage` مرورگر خودت ذخیره می‌شه.
- **حافظه‌ی Pine** و **کش Daily/Weekly** هم توی `localStorage`.
- **هیچ tracking، آنالیتیکس یا تلمتری** وجود نداره.
- **بدون backend.** همه چیز سمت کاربر اجرا می‌شه.

### محدودیت‌ها

- فید OANDA هست — ممکنه با بروکرت ۱-۵ دلار اختلاف داشته باشه.
- پلن رایگان Twelve Data محدودیت درخواست داره (~۸ در دقیقه).
- اندیکاتور سفارشی روی MT4/MT5 موبایل پشتیبانی نمی‌شه.
- Weekly محدود به ۲۰۰ کندل آخر (~۴ سال).
- Tier بر اساس Daily حساب می‌شه (استاندارد صناعت).

### تاریخچه نسخه‌ها

- **v7.5.1** — Weekly، کش Daily/Weekly، Tier اصلاح‌شده
- **v7.5** — Weekly اضافه شد، سیستم کش
- **v7.4** — سیستم Tier، Pine با ۴۰ مقدار
- **v7.3** — رصد تغییرات Pine
- **v7.2** — چندزبانه (EN/FA/RU/ZH)
- **v7.1** — مودال TradingView، تولید Pine Script
- **v7.0** — نسخه انگلیسی، ورودی API Key، حمایت مالی
- **v6.x** — سطوح رتبه‌بندی‌شده، Proximity بر اساس ATR

### حمایت

اگه این ابزار بهت کمک کرد، یه دونیت کوچیک روی BSC ممنون می‌شم:

```
0x63013226D82d1070eC98fBA2b3fdD6E626e9E8f6
```

⚠️ **فقط توکن‌های BEP-20** (BNB، USDT-BEP20، BUSD) بفرست.

---

## 🇷🇺 Русский

### Обзор

XAUUSD Analyzer — это одностраничный HTML-инструмент, работающий в браузере, который получает цены на золото (через API Twelve Data, фид OANDA), рассчитывает многотаймфреймовые технические индикаторы, определяет ранжированные зоны поддержки/сопротивления и формирует компактный вывод, готовый к использованию в LLM.

Также генерирует готовые числа для индикатора **Pine Script** в TradingView.

### Возможности

- **5 таймфреймов:** 30M, 1H, 4H, Daily, Weekly
- **Индикаторы:** EMA20/50, RSI, ATR, ADX, MACD, Ichimoku, структура рынка, Fibonacci
- **Взвешенная конвергенция:** Weekly (1.5×), Daily (1.2×), 4H (1.0×), 1H (0.6×), 30M (0.4×)
- **Ранжированные зоны:** Ближайшие и Сильнейшие
- **Итоговый балл:** 60% сила + 40% близость (по ATR)
- **Система Tier:** A/B/C на основе Age + Touch + Strength
- **Кеш Daily/Weekly:** Меньше запросов к API
- **Force Refresh:** Очистка кеша одним кликом
- **Дивергенция:** RSI vs Price (4H и Daily)
- **Максимум/минимум сессии:** Азия, Лондон, Нью-Йорк
- **Фильтр выходных:** Удаляет фальшивые свечи
- **4 языка:** английский, персидский, русский, китайский
- **Вывод для AI:** Копировать один раз — вставить в LLM
- **Интеграция с TradingView:** 40 значений + Pine Script
- **Поддержка:** BSC-кошелёк

### Быстрый старт

1. **Скачайте** HTML-файл.
2. **Откройте** в браузере.
3. Получите **бесплатный API-ключ** на [twelvedata.com](https://twelvedata.com).
4. Вставьте ключ → **Save & Test**.
5. Нажмите **Load All**.
6. **Copy for AI** → вставьте в LLM.
7. Для уровней: **TradingView Guide** → **Copy Line** → вставьте в Pine.

### Система Tier (v7.5.1)

Каждая зона получает **Tier** на основе трёх факторов:

- **Age** — сколько дней с первого Daily swing
- **Touch** — сколько раз Daily цена реагировала
- **Strength** — структурная сила (0-100)

**Оценка:**
- Age ≥ 30д → +1 | 14-30д → +0.5
- Touch ≥ 3 → +1 | 2 → +0.5
- Strength ≥ 50 → +1 | 40-49 → +0.5

**Tier:**
- **A** = балл ≥ 2.0 (старые + проверенные)
- **B** = балл ≥ 1.0 (средние)
- **C** = балл < 1.0 (новые)

### Система кеша (v7.5.1)

- **Daily** и **Weekly** кешируются в `localStorage`
- **Кеш по времени:** обновляется только при смене свечи
  - Daily: раз в день UTC (00:00)
  - Weekly: раз в неделю UTC (суббота 00:00)
- Кнопка **Force Refresh** очищает кеш
- **Cache badge** на каждой карточке: 📦 Cached / 🔴 Fresh

### Настройка TradingView

1. **TradingView Guide** — открывается модальное окно.
2. **Show / Copy Pine Script** → в редактор Pine → Save → Add to chart.
3. **Copy Line** → копируется строка из 40 значений.
4. В настройках индикатора вставьте в поле "All Zones".
5. Линии:
   - 🟡 Tier A (толстые/золото)
   - 🟠 Tier B (средние/оранж)
   - ⚪ Tier C (тонкие/серые)
   - 🔵 Weekly (синие, толстейшие)

### Приватность

- **API-ключ** хранится только в `localStorage`.
- **История Pine** и **кеш Daily/Weekly** тоже в `localStorage`.
- **Без отслеживания**, аналитики, телеметрии.
- **Без backend.**

### Ограничения

- Данные от OANDA — могут отличаться от брокера (1-5 USD).
- Бесплатный тариф Twelve Data: ~8 запросов/мин.
- Weekly ограничен последними 200 свечами (~4 года).
- Tier рассчитывается по Daily (стандарт отрасли).

### История версий

- **v7.5.1** — Weekly, кеш Daily/Weekly, исправлен Tier
- **v7.5** — Weekly добавлен, кеш
- **v7.4** — Система Tier, Pine 40 значений
- **v7.3** — Отслеживание Pine
- **v7.2** — Многоязычность (EN/FA/RU/ZH)
- **v7.1** — Модальное окно TradingView
- **v7.0** — Английская версия, API-ключ
- **v6.x** — Ранжированные зоны

### Поддержать

```
0x63013226D82d1070eC98fBA2b3fdD6E626e9E8f6
```

⚠️ **Только токены BEP-20.**

---

## 🇨🇳 中文

### 概述

XAUUSD Analyzer 是一款单文件、浏览器端的 HTML 工具。它通过 Twelve Data API（OANDA 数据源）获取黄金现货价格，计算多周期技术指标，识别分级支撑/阻力区域，并生成紧凑的、可供 LLM 使用的输出。

同时生成可直接粘贴到 TradingView **Pine Script** 指标的数值。

### 功能特性

- **5 个时间周期：** 30M、1H、4H、日线、周线
- **指标：** EMA20/50、RSI、ATR、ADX、MACD、一目均衡表、市场结构、斐波那契
- **加权汇合：** 周线 (1.5×)、日线 (1.2×)、4H (1.0×)、1H (0.6×)、30M (0.4×)
- **分级区域：** 最近与最强支撑/阻力
- **最终评分：** 60% 强度 + 40% 接近度（基于 ATR）
- **Tier 系统：** A/B/C 基于 Age + Touch + Strength
- **Daily/Weekly 缓存：** 减少 API 调用
- **Force Refresh：** 一键清除缓存
- **背离检测：** RSI 与价格（4H 和日线）
- **时段高/低：** 亚洲、伦敦、纽约（自动处理夏令时）
- **周末过滤：** 移除虚假周末蜡烛
- **4 种语言：** 英语、波斯语、俄语、中文
- **AI 就绪输出：** 复制一次，粘贴到任意 LLM
- **TradingView 集成：** 40 值单行 + Pine Script 生成器
- **捐赠支持：** BSC 钱包

### 快速开始

1. **下载** HTML 文件。
2. 在浏览器中**打开**。
3. 从 [twelvedata.com](https://twelvedata.com) 获取**免费 API 密钥**。
4. 将密钥粘贴到 **API Key Setup** → **Save & Test**。
5. 点击 **Load All**。
6. 点击 **Copy for AI** → 粘贴到 LLM。
7. 图表水平：**TradingView Guide** → **Copy Line** → 粘贴到 Pine。

### Tier 系统 (v7.5.1)

每个区域基于三个因素获得 **Tier**：

- **Age** — 自第一个 Daily swing 以来的天数
- **Touch** — Daily 价格反应次数
- **Strength** — 结构强度 (0-100)

**评分：**
- Age ≥ 30天 → +1 | 14-30天 → +0.5
- Touch ≥ 3 → +1 | 2 → +0.5
- Strength ≥ 50 → +1 | 40-49 → +0.5

**Tier：**
- **A** = 评分 ≥ 2.0（旧 + 已测试）
- **B** = 评分 ≥ 1.0（中等）
- **C** = 评分 < 1.0（新的）

### 缓存系统 (v7.5.1)

- **Daily** 和 **Weekly** 缓存在 `localStorage`
- **基于时间的缓存：** 仅在蜡烛周期变化时刷新
  - Daily：每个 UTC 日（00:00）
  - Weekly：每个 UTC 周（周六 00:00）
- **Force Refresh** 按钮清除缓存
- 每张卡片上的 **Cache badge**：📦 Cached / 🔴 Fresh

### TradingView 设置

1. 点击 **TradingView Guide** — 打开弹窗。
2. **Show / Copy Pine Script** → 粘贴到 TradingView Pine 编辑器 → Save → Add to chart。
3. **Copy Line** → 复制 40 值单行。
4. 在指标设置中粘贴到 "All Zones" 字段。
5. 线条显示：
   - 🟡 Tier A（粗/金色）
   - 🟠 Tier B（中/橙色）
   - ⚪ Tier C（细/灰色）
   - 🔵 Weekly（蓝色，最粗）

### 隐私

- **API 密钥** 仅存储在 `localStorage`。
- **Pine 历史** 和 **Daily/Weekly 缓存** 也在 `localStorage`。
- **无跟踪**、无分析、无遥测。
- **无后端。**

### 已知限制

- 数据源为 OANDA，可能与经纪商略有差异（1-5 美元）。
- Twelve Data 免费套餐：约 8 次/分钟。
- Weekly 限制为最近 200 蜡烛（约 4 年）。
- Tier 基于 Daily 计算（行业标准）。

### 版本历史

- **v7.5.1** — Weekly、Daily/Weekly 缓存、修复 Tier
- **v7.5** — 添加 Weekly、缓存系统
- **v7.4** — Tier 系统、40 值 Pine
- **v7.3** — Pine 变化追踪
- **v7.2** — 多语言（EN/FA/RU/ZH）
- **v7.1** — TradingView 弹窗
- **v7.0** — 英文版、API 密钥
- **v6.x** — 分级区域

### 捐赠

```
0x63013226D82d1070eC98fBA2b3fdD6E626e9E8f6
```

⚠️ **仅发送 BEP-20 代币。**

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
