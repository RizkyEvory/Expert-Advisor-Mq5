# ⚡ M4DI~UciH4 Bot v2.1

## M4DI~UciH4 Bot v2.1 - Enhanced with BOS & CHOCH Detection + Modern Dashboard

[![Version](https://img.shields.io/badge/Version-2.11-blue.svg)](https://github.com/RizkyEvory/Expert-Advisor-Mq5/releases)
[![Platform](https://img.shields.io/badge/Platform-MetaTrader%205%20(MT5)-green.svg)](https://www.mql5.com)
[![Author](https://img.shields.io/badge/Author-Madi%20Ganz%20(M4DI~UciH4)-darkblue.svg)](https://t.me/madiganzz)

---

## 🎯 Pendahuluan

**M4DI~UciH4 Bot v2.1** adalah Expert Advisor (EA) canggih untuk MetaTrader 5 yang dirancang untuk menggabungkan kekuatan strategi *breakout* dengan kecanggihan analisis institusional modern, dikenal sebagai **Smart Money Concepts (SMC)**.

EA ini tidak hanya mengandalkan indikator klasik, tetapi juga secara dinamis memetakan struktur pasar (BOS & CHOCH) dan zona harga institusional (Order Blocks & FVG) untuk memastikan entri yang terkonfirmasi dan berpotensi tinggi. Dilengkapi dengan Dasbor Real-time modern untuk pemantauan performa dan status pasar yang komprehensif.

## ✨ Fitur Utama

EA ini dibangun di atas fondasi multi-lapisan yang mencakup:

### 🧠 Smart Money & Struktur Pasar
* **Deteksi BOS (Break of Structure):** Mengidentifikasi kelanjutan tren yang kuat.
* **Deteksi CHOCH (Change of Character):** Menandakan potensi pembalikan tren awal.
* **Order Blocks (OB):** Mencari zona permintaan/penawaran institusional untuk entri presisi.
* **Fair Value Gaps (FVG):** Menggunakan ketidakseimbangan harga sebagai target atau zona entri.

### 📈 Strategi & Manajemen Posisi
* **Sistem Breakout Dinamis:** Menggunakan pivot ZigZag dan hitungan lilin berturut-turut untuk entri awal.
* **Advanced Martingale / Position Scaling:** Logika penggandaan lot yang terkelola dengan batas maksimum perdagangan.
* **Target Basket Profit:** Mengelola dan menutup seluruh keranjang perdagangan pada target profit kumulatif.
* **Trailing Stop Canggih:** Melindungi profit secara otomatis setelah ambang batas tertentu tercapai.

### 🛡️ Filter & Manajemen Risiko
* **Max Daily Loss/Profit:** Mekanisme penghenti dan target harian yang penting.
* **Multi-Timeframe (MTF) Alignment:** Memastikan tren di TF yang lebih tinggi sejalan dengan sinyal entri.
* **Volatility Filter:** Menghindari lonjakan harga (spikes) dan kondisi pasar yang terlalu lebar atau terlalu sempit (ATR-based).
* **Trading Hours Filter:** Membatasi perdagangan pada sesi yang paling menguntungkan (misalnya, menghindari Sesi Asia).

### 🖥️ Visualisasi Modern
* **Dasbor Real-time:** Menampilkan status akun, performa harian, tren, dan kekuatan sinyal secara visual.
* **On-Chart Drawing:** Secara otomatis menandai level ZigZag, Order Blocks, FVG, BOS, dan CHOCH pada grafik.

---

## ⚙️ Parameter Input

EA ini menawarkan kontrol yang sangat detail melalui parameter input yang dikelompokkan.

| Grup Parameter | Parameter | Tipe | Deskripsi |
| :--- | :--- | :--- | :--- |
| **Trading Settings** | `EnableBuy`, `EnableSell` | `bool` | Mengaktifkan/menonaktifkan perdagangan beli atau jual. |
| | `UseSmartMoneyFilter` | `bool` | Menggunakan filter Order Block & FVG. |
| | `UseMultiTimeframeFilter` | `bool` | Menggunakan filter Multi-Timeframe (MTF). |
| **First Trade Settings** | `FirstTrade_Candles` | `int` | Jumlah minimum lilin berturut-turut untuk entri awal. |
| | `FirstTrade_Distance` | `int` | Jarak (dalam poin) dari harga pasar untuk menempatkan order stop. |
| | `ConfirmBreakByClose` | `bool` | Konfirmasi breakout hanya jika lilin sebelumnya ditutup di atas/bawah level. |
| **Martingale Settings** | `Martingale_Candles` | `int` | Jumlah lilin berturut-turut untuk entri Martingale berikutnya. |
| | `Martingale_LotMultiplier` | `double` | Pengganda lot untuk setiap perdagangan Martingale baru (mis. 1.5). |
| | `Martingale_MaxTrades` | `int` | Jumlah maksimum perdagangan Martingale dalam satu keranjang. |
| | `Martingale_Step` | `int` | Jarak (dalam poin) antara perdagangan Martingale. |
| **Lot and Profit Settings** | `LotSize_FirstTrade`, `LotSize_Martingale` | `double` | Ukuran lot awal dan lot dasar Martingale. |
| | `TargetProfit_Buy`, `TargetProfit_Sell` | `double` | Target profit basket (dalam mata uang deposit) untuk menutup semua posisi. |
| | `UseTrailingStop` | `bool` | Mengaktifkan Trailing Stop untuk keranjang. |
| | `TrailingStopActivation`, `TrailingStopDistance` | `double` | Profit aktivasi dan jarak Trailing Stop (dalam mata uang deposit). |
| **Advanced Risk Management** | `UseMaxDailyLoss` | `bool` | Mengaktifkan batas kerugian harian. |
| | `MaxDailyLossUSD` | `double` | Batas kerugian harian maksimum (dalam USD/mata uang deposit). |
| | `UseMaxDailyProfit` | `bool` | Mengaktifkan target profit harian. |
| | `MaxDailyProfitUSD` | `double` | Target profit harian maksimum (dalam USD/mata uang deposit). |
| **Volatility Filter** | `Use_VolatilityFilter` | `bool` | Menggunakan filter volatilitas harian dan lilin. |
| | `MaxDailyRange` | `int` | Rentang harian maksimum yang diizinkan (dalam poin). |
| | `Use_ATR_Filter` | `bool` | Menggunakan Average True Range untuk memfilter lilin. |
| **Smart Money Concepts** | `UseOrderBlocks`, `UseFVG`, `UseLiquidity` | `bool` | Mengaktifkan masing-masing filter SMC. |
| **BOS & CHOCH Settings** | `UseBOS`, `UseCHOCH` | `bool` | Mengaktifkan deteksi Break of Structure dan Change of Character. |
| | `RequireBOSConfirmation` | `bool` | Mengharuskan konfirmasi BOS/CHOCH sebelum entri. |
| | `DrawBOS`, `DrawCHOCH` | `bool` | Menggambar level BOS/CHOCH pada grafik. |
| **Multi-Timeframe Settings** | `MTF_Higher1`, `MTF_Higher2` | `ENUM_TIMEFRAMES` | Dua Timeframe yang lebih tinggi untuk filter alignment. |
| | `RequireAllTFAlign` | `bool` | Mengharuskan kedua TF MTF selaras (vs. salah satunya). |
| **Trading Hours Settings** | `EnableTradingHours` | `bool` | Membatasi perdagangan pada jam tertentu. |
| | `StartHour`, `EndHour` | `int` | Jam mulai dan akhir perdagangan. |
| | `AvoidAsianSession` | `bool` | Secara eksplisit menghindari jam-jam Sesi Asia (00:00 - 08:00). |
| **Visualization** | `Show_Dashboard` | `bool` | Mengaktifkan Dasbor Informasi Real-time. |
| | `Draw_ZZ_Levels` | `bool` | Menggambar level High/Low ZigZag pada grafik. |
| | `DrawOrderBlocks`, `DrawFVG` | `bool` | Menggambar zona Order Block dan FVG pada grafik. |

---

## 🚀 Instalasi & Penggunaan

1.  **Unduh File:** Unduh file yang sudah dikompilasi (`v2FIX.ex5`) atau kompilasi file sumber (`breakout_v2.1_fixed.mq5`) di MetaEditor 5 Anda.
2.  **Penempatan:** Pindahkan file `.ex5` ke folder `MQL5/Experts`.
3.  **Attach ke Grafik:** Buka MetaTrader 5, pilih pasangan mata uang dan Timeframe yang diinginkan, seret EA dari Navigator ke grafik.
4.  **Konfigurasi:** Sesuaikan parameter input sesuai dengan preferensi risiko dan strategi Anda, lalu pastikan **"Allow Algo Trading"** dicentang.
5.  **Running:** EA akan mulai memonitor pasar dan mengeksekusi perdagangan sesuai dengan logika yang dikodekan dan filter yang Anda tetapkan.

---

> **Penting:** EA ini menggunakan logika Martingale/Position Scaling. Pastikan Anda memahami dan mengelola parameter risiko (terutama `LotSize_Martingale`, `Martingale_MaxTrades`, dan `MaxDailyLossUSD`) dengan hati-hati. Selalu uji coba di akun Demo terlebih dahulu.

**© Copyright 2025, Madi Ganz (M4DI~UciH4)**
