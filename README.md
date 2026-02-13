# 📈 Automated Stock Market Data Pipeline (ETL)

## 📌 Project Overview
Project ini adalah sebuah **End-to-End ETL (Extract, Transform, Load) Pipeline** yang dirancang untuk mengambil data historis harga saham secara otomatis setiap hari. 

Alih-alih mengunduh data CSV secara manual, sistem ini berjalan di Cloud (GitHub Actions) untuk menarik data terbaru dari API, membersihkannya, dan menyimpannya ke dalam database SQLite yang siap digunakan untuk analisis lanjutan atau *dashboarding*.

## 🏗️ Architecture & Tech Stack
* **Extract:** Python (`yfinance` API) menarik data pergerakan harga saham perusahaan top Indonesia (BBCA, TLKM, GOTO).
* **Transform:** `Pandas` digunakan untuk membersihkan data, menormalisasi struktur tabel, dan menambahkan *timestamp* proses ETL.
* **Load:** Menyimpan data yang sudah bersih ke dalam Relational Database (`SQLite`).
* **Orchestration / Automation:** `GitHub Actions` dikonfigurasi menggunakan Cron Job (`0 9 * * 1-5`) untuk menjalankan script secara otomatis setiap hari Senin-Jumat jam 16:00 WIB (setelah bursa saham tutup).

## 🚀 Business Value
* **Efisiensi Waktu:** Menghilangkan 100% intervensi manual dalam pengumpulan data harian.
* **Data Reliability:** Memastikan analis selalu mendapatkan data H+0 yang bersih dan terstruktur untuk pelaporan keuangan.

## 📁 File Structure
* `etl_stock.py`: Script utama Python untuk proses ETL.
* `market_data.db`: Database SQLite yang diperbarui secara otomatis oleh server.
* `.github/workflows/main.yml`: Konfigurasi CI/CD untuk penjadwalan robot GitHub Actions.
