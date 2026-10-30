# CNGneers: Platform Digital Ekosistem CNG untuk Akselerasi Adopsi Energi Bersih & Efisiensi Industri Nasional

> **Master Product Requirement Document (PRD) & Technical Platform Blueprint**  
> **Ajang:** ANGEL Innovation Hackathon 2026  
> **Mitra Industri:** PT Aqua Gas Energy (Infrastruktur CNG) & PT Indmira (Agro-Industri & Bioteknologi)  
> **Status Dokumen:** Version 1.0 — Enterprise Investor & Engineering Blueprint  
> **Tanggal:** Oktober 2026  

---

## DAFTAR ISI
1. [Executive Summary & Visi Strategis](#1-executive-summary--visi-strategis)
2. [Macro Context & Kesenjangan Pasar Nasional](#2-macro-context--kesenjangan-pasar-nasional)
3. [Arsitektur Bisnis Dua Lapisan (PlatformCo vs InfraCo)](#3-arsitektur-bisnis-dua-lapisan-platformco-vs-infraco)
4. [Friksi Ekosistem & Mengapa Modal Industri Tertahan](#4-friksi-ekosistem--mengapa-modal-industri-tertahan)
5. [Spesifikasi 5 Pilar Produk MVP (Unified Portal)](#5-spesifikasi-5-pilar-produk-mvp-unified-portal)
   - [5.1 SIMULATE (Energy Advisor & Baseline Engine)](#51-simulate-energy-advisor--baseline-engine)
   - [5.2 ORDER (Qualified B2B Lead Gen & Off-Take)](#52-order-qualified-b2b-lead-gen--off-take)
   - [5.3 TRACK (Logistics Intelligence & e-POD)](#53-track-logistics-intelligence--e-pod)
   - [5.4 INVENTORY (ERP Stock View & Virtual Pipeline Allocation)](#54-inventory-erp-stock-view--virtual-pipeline-allocation)
   - [5.5 PAY (Automated Invoicing, Reconciliation & ESG Carbon)](#55-pay-automated-invoicing-reconciliation--esg-carbon)
6. [Multi-Channel Data Ingestion Suite (Zero-CAPEX to Industry 4.0)](#6-multi-channel-data-ingestion-suite-zero-capex-to-industry-40)
   - [6.1 Smart Logbook OCR Scanner (AI Vision)](#61-smart-logbook-ocr-scanner-ai-vision)
   - [6.2 Live SCADA / IoT Telemetry Stream (Edge Modbus/MQTT)](#62-live-scada--iot-telemetry-stream-edge-modbusmqtt)
   - [6.3 Batch CSV / Excel Historical Data](#63-batch-csv--excel-historical-data)
   - [6.4 Plant DCS / MES Webhook & REST API](#64-plant-dcs--mes-webhook--rest-api)
   - [6.5 Mitigasi "Biaya Sensor Mahal": Strategi Retrofit Brownfield](#65-mitigasi-biaya-sensor-mahal-strategi-retrofit-brownfield)
7. [Landasan Matematis, Termodinamika & Standar Rekayasa](#7-landasan-matematis-termodinamika--standar-rekayasa)
   - [7.1 Normalisasi Energi Lower Heating Value (LHV)](#71-normalisasi-energi-lower-heating-value-lhv)
   - [7.2 Intensitas Konsumsi Energi (IKE / SEC)](#72-intensitas-konsumsi-energi-ike--sec)
   - [7.3 Regresi Multivariat US DOE & ASHRAE Guideline 14](#73-regresi-multivariat-us-doe--ashrae-guideline-14)
   - [7.4 Deteksi Anomali Operasional (+1.5σ)](#74-deteksi-anomali-operasional-15σ)
   - [7.5 Efisiensi Pembakaran Formulasi Siegert](#75-efisiensi-pembakaran-formulasi-siegert)
   - [7.6 Tekno-Ekonomi Transisi Bahan Bakar & Payback Period](#76-tekno-ekonomi-transisi-bahan-bakar--payback-period)
   - [7.7 Reduksi Emisi Gas Rumah Kaca (IPCC 2006)](#77-reduksi-emisi-gas-rumah-kaca-ipcc-2006)
   - [7.8 Operator Triage & Prompt Investigasi Teknisi](#78-operator-triage--prompt-investigasi-teknisi)
8. [Model Finansial, Monetisasi & Sensitivitas Unit Economics](#8-model-finansial-monetisasi--sensitivitas-unit-economics)
   - [8.1 Komparasi Nilai Riil Panas Berguna (LPG vs CNG)](#81-komparasi-nilai-riil-panas-berguna-lpg-vs-cng)
   - [8.2 Proyeksi GMV Ekosistem (Baseline 50.000 Sm³/hari)](#82-proyeksi-gmv-ekosistem-baseline-50000-smhari)
   - [8.3 Sensitivitas Take-Rate PlatformCo (0.5% - 2.0%)](#83-sensitivitas-take-rate-platformco-05---20)
   - [8.4 Aliran Pendapatan SaaS & Implementasi API](#84-aliran-pendapatan-saas--implementasi-api)
9. [Arsitektur Teknis & Spesifikasi Sistem](#9-arsitektur-teknis--spesifikasi-sistem)
   - [9.1 Technology Stack Summary](#91-technology-stack-summary)
   - [9.2 Diagram Komponen Sistem](#92-diagram-komponen-sistem)
   - [9.3 Kontrak Protocol Buffer (gRPC) & WebSocket](#93-kontrak-protocol-buffer-grpc--websocket)
   - [9.4 Keamanan Data, RBAC & 100% Traceability Audit Trail](#94-keamanan-data-rbac--100-traceability-audit-trail)
10. [Go-To-Market (GTM) Funnel & Roadmap Eksekusi](#10-go-to-market-gtm-funnel--roadmap-eksekusi)
    - [10.1 5-Tahap Komersial Funnel](#101-5-tahap-komersial-funnel)
    - [10.2 Roadmap Eksekusi Berjenjang (Fase 0 s/d Fase 4)](#102-roadmap-eksekusi-berjenjang-fase-0-sd-fase-4)
11. [Manajemen Risiko & Mitigasi Struktural](#11-manajemen-risiko--mitigasi-struktural)
12. [Strategi Pitching Hackathon: Mengapa CNGneers Pemenang Mutlak](#12-strategi-pitching-hackathon-mengapa-cngneers-pemenang-mutlak)
    - [12.1 Keunggulan Mutlak vs Inovasi Hardware (Robot Sampah / Biomassa)](#121-keunggulan-mutlak-vs-inovasi-hardware-robot-sampah--biomassa)
    - [12.2 Lembar Jawaban Tangkas (Q&A Defense Guide) Dewan Juri](#122-lembar-jawaban-tangkas-qa-defense-guide-dewan-juri)

---

## 1. Executive Summary & Visi Strategis

**CNGneers** adalah platform digital orkestrasi ekosistem *Compressed Natural Gas* (CNG) terpadu pertama di Indonesia yang menghubungkan produsen gas (*Mother Station*), armada logistik *virtual pipeline*, dan konsumen industri hilir (B2B) dalam satu arsitektur *asset-light control tower*. 

Platform ini dirancang khusus untuk mempercepat transisi energi industri dari bahan bakar fosil impor yang mahal (LPG Industri dan Solar/HSD) menuju Gas Bumi Domestik (CNG) yang lebih bersih, efisien, dan ekonomis.

```
+----------------------------------------------------------------------------------------------------+
|                                    CNGneers DIGITAL ECOSYSTEM                                      |
+----------------------------------------------------------------------------------------------------+
|   HULU (SUPPLY)        |             DIGITAL CONTROL TOWER (CNGneers)          |    HILIR (DEMAND) |
|                        |                                                       |                   |
|  [ PGN / Gas Wells ]   |  +-------------------------------------------------+  |  [ PT Indmira ]   |
|           |            |  | 1. SIMULATE  : Audit Termal & Kelayakan Finansial|  |  Agro-Boiler &    |
|           v            |  | 2. ORDER     : Onboarding B2B & Kontrak Off-Take|  |  Granulasi Pupuk  |
|  [ Mother Station ]    |  | 3. TRACK     : Optimasi Rute Armada & e-POD     |  |                   |
|  (PT Aqua Gas Energy)  |  | 4. INVENTORY : Stok Mother Station & Alokasi Gas|  |  [ Industri B2B ] |
|           |            |  | 5. PAY       : Faktur Otomatis & Laporan ESG    |  |  Tekstil, F&B,    |
|           v            |  +-------------------------------------------------+  |  Keramik, Horeka  |
|  [ Tube Trailers ] <---+------------ Dispatch, Tracking & e-POD ---------------+-------------------+
+----------------------------------------------------------------------------------------------------+
```

### Problem Statement
Pabrik industri manufaktur dan agro-industri di Indonesia terjebak dalam biaya energi termal yang tinggi akibat pemakaian LPG Industri (Rp16.000/kg) dan solar industri. Meskipun CNG menawarkan biaya energi termal hingga **37% - 58% lebih hemat**, adopsi CNG nasional tersendat parah karena:
1. **Asimetri Informasi & Ketakutan Teknis Konsumen:** Pabrik bingung mengonversi satuan (kg LPG vs Sm³ CNG vs MMBtu) dan takut biaya investasi penggantian burner (*retrofit CAPEX*) tidak balik modal.
2. **Rantai Pasok "Buta" (*Blind Supply Chain*):** Distributor gas dan armada truk *tube trailer* beroperasi manual tanpa sistem pelacakan rute, pemantauan stok tangki *real-time*, dan surat jalan kertas yang memperlambat penagihan (*Days Sales Outstanding / DSO*).
3. **Risiko Investasi Fisik (*CAPEX Underutilization*):** Investor infrastruktur gas (seperti PT Aqua Gas Energy) ragu membangun *mother station* baru senilai puluhan miliar tanpa kepastian komitmen serapan gas (*off-take*) yang terverifikasi secara data.

### Solusi CNGneers
CNGneers hadir bukan untuk menambah beban belanja modal fisik, melainkan menjadi **Orkestrator Digital (PlatformCo)** yang:
- Menganalisis kelayakan ekonomi konversi burner secara presisi berbasis sains termodinamika ASME PTC 4 dan US DOE.
- Membuka akses *onboarding* pelanggan secara mandiri (multi-channel: foto logbook kertas via OCR, live IoT SCADA, batch CSV, atau webhook MES).
- Mengorkestrasi logistik truk pengantar gas CNG berbasis *cycle-time logic* dengan *electronic Proof of Delivery* (e-POD).
- Mengotomatisasi penagihan dan pelaporan emisi karbon ESG (IPCC 2006).

---

## 2. Macro Context & Kesenjangan Pasar Nasional

Berdasarkan data energi nasional per April 2026:
- **Konsumsi LPG Nasional:** Mencapai **8,6 Juta Ton / Tahun**.
- **Ketergantungan Impor LPG:** Menembus **~81%** (impor sekitar 7,0 juta ton/tahun), sementara produksi domestik hanya **~19%** (1,6 - 1,7 juta ton/tahun). Hal ini menimbulkan kerentanan fiskal negara dan beban devisa yang sangat masif.
- **Peluang Substitusi Gas Bumi Domestik:** Indonesia memiliki cadangan gas bumi melimpah yang belum terserap maksimal karena jaringan pipa pipa transmisi belum mencakup seluruh kawasan industri. *Virtual Pipeline* (CNG yang dimampatkan ke tabung bertekanan 200-250 bar dan diangkut truk) adalah satu-satunya solusi tercepat untuk menjangkau kawasan non-pipa.

### Funnel Target Pasar CNGneers
```
+-----------------------------------------------------------------------+
|  Total Volume LPG Nasional: 8.6 Juta Ton / Tahun                      |
+-----------------------------------+-----------------------------------+
                                    |
                                    v
+-----------------------------------------------------------------------+
|  Technically Viable for CNG (B2B Industri, Beban Termal Stabil)       |
|  Contoh: Industri Pengeringan Pupuk (PT Indmira), Tekstil, Makanan,   |
|  Pabrik Pakan Ternak, Keramik, Hotel & Binatu Komersial               |
+-----------------------------------+-----------------------------------+
                                    |
                                    v
+-----------------------------------------------------------------------+
|  Economically Viable (Radius 100 km dari Mother Station)              |
|  Pabrik dengan konsumsi kontinu yang menghasilkan penghematan biaya   |
|  ≥ 20% dan Payback Period Retrofit Burner < 12 Bulan                  |
+-----------------------------------------------------------------------+
```

---

## 3. Arsitektur Bisnis Dua Lapisan (PlatformCo vs InfraCo)

Salah satu kelemahan terbesar inovator energi adalah mencampurkan bisnis perangkat lunak dengan kepemilikan aset fisik yang padat modal. Blueprint CNGneers secara tegas memisahkan entitas menjadi **Dua Lapisan Sinergis (*Corporate Ring-Fencing*)**:

| Parameter Evaluasi | PlatformCo (**CNGneers**) | InfraCo / SPV (**PT Aqua Gas Energy & Mitra**) |
| :--- | :--- | :--- |
| **Aktivitas Inti** | Orkestrasi digital, marketplace SaaS, data analytics, optimasi rute, dan sistem penagihan. | Kompresi gas hulu, transportasi gas bertekanan tinggi, instalasi PRS, dan molekul gas fisik. |
| **Model Pendapatan** | *Transaction take-rate* (0.5% - 2.0% dari GMV gas), langganan SaaS Enterprise, fee integrasi API. | *Physical gas spread* (harga jual gas franko pabrik dikurangi COGS gas pipa hulu). |
| **Profil Modal** | **Asset-Light**, margin kotor tinggi (>75%), skala pertumbuhan eksponensial tanpa beban pabrik. | **Capital Intensive (CAPEX)**, depresiasi aset tetap (kompresor, tube trailer, tabung gas). |
| **Profil Risiko** | Adopsi perangkat lunak, keamanan siber (*cybersecurity*), dan tata kelola data. | Utilisasi aset (*off-take volume*), perizinan migas/K3 (HSSE), dan keselamatan armada jalan raya. |
| **Hubungan Sinergis** | Memberikan kepastian data serapan pasar (*bankable off-take*) sebelum InfraCo menggelontorkan CAPEX. | Menjadi penyedia infrastruktur fisik dan pemenuhan molekul gas bagi pengguna platform. |

---

## 4. Friksi Ekosistem & Mengapa Modal Industri Tertahan

Melalui wawancara dan observasi lapangan di sektor industri, teridentifikasi 3 friksi utama yang membuat modal investasi tertahan (*stuck*):

```
+-------------------+      +-------------------+      +-------------------+
|     CUSTOMERS     |      |     OPERATORS     |      |     INVESTORS     |
|   (Pabrik Klien)  |      |   (Distributor)   |      |  (Mitra Finansial)|
+-------------------+      +-------------------+      +-------------------+
          |                          |                          |
          v                          v                          v
  OPAQUE ECONOMICS           BLIND SUPPLY CHAIN         MISALIGNED CAPEX
- Konversi satuan rumit    - Ketiadaan visibilitas    - Takut bangun Mother
  (kg LPG vs Sm³ CNG)        stok gas pelanggan         Station karena serapan
- Ragu pada klaim efisiensi- Keterlambatan armada truk  pasar belum terjamin
- Takut biaya retrofit       karena rute manual       - Risiko aset nganggur
  burner hangus tanpa balik- Faktur kertas lambat,      akibat proyeksi sales
  modal                      DSO membengkak >45 hari    yang tidak akurat
```

---

## 5. Spesifikasi 5 Pilar Produk MVP (Unified Portal)

Antarmuka CNGneers diwujudkan dalam bentuk **Single Web / PWA Portal** modern terintegrasi yang mencakup 5 modul operasional hulu-ke-hilir:

```
+--------------------------------------------------------------------------------------------------------+
|                                    CNGneers UNIFIED WEB PORTAL                                         |
+-------------------+--------------------+-------------------+--------------------+----------------------+
|    1. SIMULATE    |     2. ORDER       |     3. TRACK      |    4. INVENTORY    |       5. PAY         |
|  Energy Advisor   | Qualified Lead Gen |  Logistics & POD  |  Mother Station ERP|  Automated Billing   |
+-------------------+--------------------+-------------------+--------------------+----------------------+
```

### 5.1 SIMULATE (Energy Advisor & Baseline Engine)
* **Tujuan:** Menghilangkan asimetri informasi konsumen dan membuktikan kelayakan finansial konversi secara ilmiah dan terverifikasi.
* **Fitur Utama:**
  - **Heating Value Normalizer:** Mengonversi data pemakaian LPG (kg), Solar (Liter), atau Gas (Nm³) ke basis energi setara *Lower Heating Value* (GJ & MMBtu).
  - **Multivariate OLS Regression:** Memodelkan konsumsi energi baseline terhadap variabel produksi fisik (Ton) dan jam operasi (Hour) merujuk pada standar **US DOE & ASHRAE Guideline 14**.
  - **Siegert Combustion Analyzer:** Menghitung efisiensi pembakaran riil berdasarkan suhu gas buang (*flue gas temp*) dan sisa oksigen (*excess $O_2$*).
  - **Retrofit CAPEX Payback Simulator:** Mengalkulasi biaya energi berguna (Rp/MJ Useful Heat), proyeksi penghematan biaya tahunan, nilai Payback Period (Bulan), dan ROI.
  - **ESG Carbon Abatement Card:** Menghitung reduksi emisi gas rumah kaca berbasis protokol **IPCC 2006 Stationary Combustion**.
  - **Traceability Matrix:** Menampilkan 100% jejak audit matematis langkah demi langkah agar dapat diverifikasi oleh auditor eksternal.

### 5.2 ORDER (Qualified B2B Lead Gen & Off-Take)
* **Tujuan:** Mengubah ketertarikan calon pelanggan menjadi komitmen *off-take* terstruktur yang dapat diaudit sebelum aset fisik dikerahkan.
* **Fitur Utama:**
  - **Structured Technical Site Survey:** Input kapasitas boiler (Ton Steam/jam), merk burner eksisting (Weishaupt, Riello, Baltur), tekanan gas yang dibutuhkan (Bar), dan profil jam kerja (shift/hari).
  - **Location Geofencing & Feasibility Check:** Memverifikasi apakah koordinat pabrik berada dalam radius ekonomis $\le 100\text{ km}$ dari Mother Station terdekat.
  - **Digital Letter of Intent (LOI) Generator:** Menerbitkan draf kesepakatan pasokan gas volume minimum dengan proyeksi penghematan biaya bergaransi.
  - **Retrofit Financing Application:** Menghubungkan pabrik dengan mitra perbankan/fintech untuk skema pembiayaan CAPEX burner berbunga rendah berbasis penghematan energi (*Shared Savings Model*).

### 5.3 TRACK (Logistics Intelligence & e-POD)
* **Tujuan:** Menghilangkan keterlambatan distribusi dan sengketa volume gas serah terima antara operator truk dengan pihak pabrik.
* **Fitur Utama:**
  - **Fleet Cycle-Time Engine:** Mengalkulasi alokasi waktu armada secara realistis yang membagi siklus menjadi:
    $$\text{Total Cycle Time} = t_{\text{filling}} + t_{\text{travel (traffic)}} + t_{\text{unloading}} + t_{\text{buffer}}$$
  - **Virtual Pipeline Map Tracking:** Menampilkan posisi armada truk *tube trailer* pengangkut gas secara *real-time* berbasis telematika GPS.
  - **Electronic Proof of Delivery (e-POD):** Konfirmasi serah terima digital di mana petugas pabrik dan sopir memvalidasi tekanan gas awal (misal 200 bar), tekanan sisa tabung (misal 30 bar), dan menandatangani berita acara serah terima langsung di layar tablet/ponsel.

### 5.4 INVENTORY (ERP Stock View & Virtual Pipeline Allocation)
* **Tujuan:** Mencegah terjadinya *stock-out* (kehabisan gas) di sisi pabrik dan mengoptimalkan kapasitas kompresor di Mother Station.
* **Fitur Utama:**
  - **Mother Station Capacity Gauges:** Pemantauan kapasitas kompresi terpasang (misal 2.0 - 2.5 MMSCFD) terhadap volume pengisian harian (target 50.000 $\text{Sm}^3$/hari).
  - **Decentralized Storage & PRS Monitoring:** Status tekanan di stasiun penurun tekanan (*Pressure Regulating Station / PRS*) di lokasi pabrik pelanggan.
  - **Predictive Refill Dispatch Alert:** Peringatan otomatis ketika sisa gas di PRS pelanggan diperkirakan habis dalam 6 jam ke depan, memicu perintah pengiriman armada baru secara otomatis.

### 5.5 PAY (Automated Invoicing, Reconciliation & ESG Carbon)
* **Tujuan:** Mempercepat penagihan kas (*cash conversion cycle*) dan menghasilkan pelaporan kepatuhan emisi untuk audit keberlanjutan perusahaan.
* **Fitur Utama:**
  - **Automated Meter-to-Invoice:** Menghitung tagihan riil secara otomatis dari data serah terima e-POD tanpa rekap manual berhari-hari.
  - **Fintech & Virtual Account Settlement:** Pembayaran tagihan gas terintegrasi dengan perbankan nasional, pemantauan status *Pending*, *Overdue*, dan batas kredit (*credit limit enforcement*).
  - **Days Sales Outstanding (DSO) Optimization:** Memangkas siklus penagihan rata-rata industri dari 45 hari menjadi di bawah 14 hari.
  - **Automated Carbon ESG Certification:** Menerbitkan sertifikat audit reduksi ton emisi $CO_2$ bulanan resmi yang siap dilampirkan dalam Laporan Keberlanjutan Tahunan (*Sustainability Report*) emiten pabrik.

---

## 6. Multi-Channel Data Ingestion Suite (Zero-CAPEX to Industry 4.0)

Untuk menjamin **Zero Barrier to Entry**, CNGneers menyediakan **4 Pintu Masuk Data** yang menyesuaikan dengan tingkat kedewasaan digital masing-masing pabrik di Indonesia:

```
+-----------------------------------------------------------------------------------------------+
|                       CNGneers 4-CHANNEL DATA INGESTION SUITE                                 |
+-------------------+-------------------+-----------------------+-------------------------------+
| 1. AI Vision OCR  | 2. Live SCADA     | 3. Batch CSV / Excel  | 4. Industrial Webhook/API     |
| (Industry 2.0)    | (Industry 4.0)    | (Retroactive Audit)   | (Enterprise IT/MES)           |
| Foto Form Kertas  | Stream Sensor     | Rekap Data 90 Hari    | Integrasi Sistem ERP          |
| Catatan Operator  | Modbus/MQTT       | Historis Pabrik       | SAP / Ignition / Node-RED     |
+-------------------+-------------------+-----------------------+-------------------------------+
```

### 6.1 Smart Logbook OCR Scanner (AI Vision)
* **Konteks Lapangan:** Sebagian besar boiler pabrik di Indonesia dioperasikan oleh teknisi shift yang mencatat jarum meteran gas, suhu cerobong, dan tonase produksi di lembar kertas form checklist di papan jalan (*clipboard*).
* **Mekanisme Fitur:** 
  1. Supervisor atau tim audit memotret lembar kertas logbook menggunakan kamera ponsel.
  2. Modul OCR di backend (didukung EasyOCR dan regex parsing cerdas) secara otomatis mendeteksi baris tabel, kolom tanggal, jam shift, meteran bahan bakar, dan hasil produksi.
  3. Data langsung terdigitasi ke tabel terstruktur tanpa perlu pengetikan manual satu per satu.

### 6.2 Live SCADA / IoT Telemetry Stream (Edge Modbus/MQTT)
* **Konteks Lapangan:** Untuk pabrik modern atau demo evaluasi juri yang memerlukan visibilitas detik-ke-detik.
* **Mekanisme Fitur:**
  1. Simulasi denyut data sensor telemetri boiler (laju aliran gas, suhu *flue gas*, konsentrasi $O_2$, tekanan uap).
  2. Data dipancarkan secara terus-menerus melalui koneksi **WebSocket (`/ws/copilot`)**.
  3. Indikator gauge berdetak dinamis, dan jika terjadi lonjakan pemborosan burner, sistem memunculkan **Live Anomaly Alert Flash** secara instan.

### 6.3 Batch CSV / Excel Historical Data
* **Konteks Lapangan:** Digunakan oleh konsultan energi, Manajer Pabrik, atau Bagian Keuangan saat ingin melakukan audit retrospektif terhadap operasional 1 kuartal (90 hari) atau data SCADA 2.160 baris per jam.
* **Mekanisme Fitur:** Fitur *Drag-and-Drop* file `.csv` atau `.xlsx` dengan algoritma pembersihan otomatis (*data autocleaning*) yang mendeteksi baris rusak, nilai minus, dan baris *burner idling* (*zero production with fuel burned*).

### 6.4 Plant DCS / MES Webhook & REST API
* **Konteks Lapangan:** Untuk pabrik yang telah memiliki sistem otomasi komputer (Siemens WinCC, Wonderware, Ignition, atau database ERP SAP/Odoo).
* **Mekanisme Fitur:**
  1. CNGneers menyediakan dokumentasi endpoint REST terbuka: `POST /api/telemetry/v1/ingest`.
  2. Dilengkapi contoh skrip siap pakai (*cURL, Python, dan konfigurasi node Node-RED*) sehingga staf instrumen pabrik dapat mengalirkan data rekap per shift (tiap 8 jam) secara otomatis tanpa intervensi manusia.

### 6.5 Mitigasi "Biaya Sensor Mahal": Strategi Retrofit Brownfield
Pertanyaan paling sering dari manajemen pabrik: *"Sensor industri kan mahal, apakah kami harus keluar uang ratusan juta untuk pasang sensor baru?"*

**Jawaban Tegas CNGneers: TIDAK.**  
Di pabrik yang sudah berjalan (*brownfield*), instrumen penting **sudah terpasang** karena tuntutan keselamatan kerja dan penagihan komersial:
1. **Meteran Gas/Bahan Bakar:** Penyedia gas (PGN atau Aqua Gas Energy) **wajib** memasang *Electronic Volume Corrector* (EVC) atau flow meter ber-transmiter pulsa untuk dasar penagihan tagihan bulanan.
2. **Suhu Cerobong (*Flue Gas*):** Burner standar industri (Riello, Baltur, Weishaupt) selalu dilengkapi sensor termokopel PT100/Type-K untuk *safety shut-off* boiler.
3. **Tekanan Steam:** Sertifikasi Disnaker keselamatan boiler mewajibkan adanya manometer mekanik dan pressure transmitter.
4. **Timbangan Produksi:** Output pupuk granulasi atau barang jadi ditimbang di *bagger hopper* atau jembatan timbang.

> **Pabrik tidak perlu beli sensor baru.** CNGneers hanya menghubungkan port data RS-485 Modbus yang sudah ada di panel burner menggunakan **Industrial IoT Gateway murah seharga Rp 500.000 – Rp 1.500.000 (Non-Invasive Retrofit)**. Jika pabrik tidak ingin mengeluarkan biaya sama sekali, pabrik cukup menggunakan fitur **Smart Logbook OCR** atau **Webhook Harian** dengan **CAPEX Rp 0**.

---

## 7. Landasan Matematis, Termodinamika & Standar Rekayasa

Seluruh kalkulasi di balik CNGneers bersifat deterministik, dapat diaudit (*auditable*), dan merujuk pada standar rekayasa internasional.

### 7.1 Normalisasi Energi Lower Heating Value (LHV)
Semua satuan bahan bakar dikonversi ke basis energi setara *Lower Heating Value* (Gigajoule / GJ):
$$E_{\text{input}} = M_{\text{fuel}} \times LHV_{\text{fuel}}$$

Tabel Nilai Kalor Acuan Industri:
| Bahan Bakar | Satuan Asli | Nilai Kalor Bawah (LHV) | Faktor Konversi ke GJ |
| :--- | :---: | :---: | :---: |
| **LPG Industri** | kg | $46.10\text{ MJ/kg}$ | $0.04610\text{ GJ/kg}$ |
| **Solar Industri (HSD)** | Liter | $35.80\text{ MJ/L}$ | $0.03580\text{ GJ/L}$ |
| **Gas Bumi / CNG** | $\text{Sm}^3$ | $36.00\text{ - }38.00\text{ MJ/Sm}^3$ | $0.03800\text{ GJ/Nm}^3$ |
| **Gas Alam (Basis MMBtu)** | MMBtu | $1.055056\text{ GJ/MMBtu}$ | $1.055056\text{ GJ/MMBtu}$ |

### 7.2 Intensitas Konsumsi Energi (IKE / SEC)
Mengevaluasi efisiensi penggunaan bahan bakar terhadap volume produksi bersih:
$$IKE_i = \frac{E_{\text{input}, i}}{P_i} \quad \left[\frac{\text{GJ}}{\text{Ton}}\right]$$

### 7.3 Regresi Multivariat US DOE & ASHRAE Guideline 14
Mengikuti standar *ASHRAE Guideline 14 Option C* untuk pemodelan fasilitas industri secara menyeluruh, konsumsi energi baseline diposisikan sebagai fungsi variabel produksi fisik ($P$) dan jam operasional ($H$):
$$\hat{E}_i = \beta_1 P_i + \beta_2 H_i + c$$

Vektor parameter koefisien $\vec{\beta} = [\beta_1, \beta_2]^T$ dan intersep $c$ dihitung menggunakan metode *Ordinary Least Squares* (OLS):
$$\vec{\beta} = \left( \mathbf{X}^T \mathbf{X} \right)^{-1} \mathbf{X}^T \vec{Y}$$

Kualitas model diuji terhadap ambang batas kelayakan ASHRAE ($R^2 \ge 0.70$ dan $CV(RMSE) \le 30\%$):
$$R^2 = 1 - \frac{\sum_{i=1}^N (E_i - \hat{E}_i)^2}{\sum_{i=1}^N (E_i - \bar{E})^2}$$
$$CV(RMSE) = \frac{\sqrt{\frac{1}{N-p} \sum_{i=1}^N (E_i - \hat{E}_i)^2}}{\bar{E}} \times 100\%$$

### 7.4 Deteksi Anomali Operasional (+1.5σ)
Deviasi residual antara energi aktual terukur dengan baseline model:
$$e_i = E_i - \hat{E}_i$$

Anomali pemborosan energi ditandai jika deviasi positif melampaui ambang batas 1.5 standar deviasi:
$$\text{Status}_i = \begin{cases} 
\text{ANOMALY (High Waste)}, & \text{jika } e_i > +1.5\sigma_e \\ 
\text{NORMAL}, & \text{lainnya} 
\end{cases}$$

Total energi yang terbuang ($Q_{\text{waste}}$) dan kerugian finansial dihitung dari anomali pembakaran serta kondisi *idle* ($P_i = 0$ saat $E_i > 0$):
$$Q_{\text{waste}} = \sum_{i \in \text{Anomalies}} (E_i - \hat{E}_i) + \sum_{i \in \text{Idle}} E_i$$
$$\text{Kerugian Finansial (IDR)} = Q_{\text{waste}} \times \text{Tarif Bahan Bakar per GJ}$$

### 7.5 Efisiensi Pembakaran Formulasi Siegert
Bila data sensor cerobong tersedia, efisiensi termal pembakaran dihitung menggunakan formula Siegert:
$$q_{\text{stack}} = K \times \frac{T_{\text{flue}} - T_{\text{ambient}}}{21 - O_{2,\text{excess}}}$$
$$\eta_{\text{thermal}} = 100\% - (q_{\text{stack}} + q_{\text{radiation}} + q_{\text{unburnt}})$$
*Untuk bahan bakar gas/hidrokarbon, nilai konstanta $K \approx 0.58$, dengan estimasi kerugian radiasi dinding boiler $12\% - 14\%$.*

### 7.6 Tekno-Ekonomi Transisi Bahan Bakar & Payback Period
Biaya per satuan energi berguna (*Useful Heat*) yang memperhitungkan efisiensi termal pembakaran ($\eta$):
$$C_{\text{useful}} = \frac{\text{Biaya Bahan Bakar per GJ}}{\eta_{\text{thermal}}}$$

Penghematan biaya bahan bakar tahunan akibat konversi ke CNG:
$$\Delta C_{\text{annual}} = E_{\text{annual demand}} \times \left( C_{\text{useful, eksisting}} - C_{\text{useful, CNG}} \right)$$

*Simple Payback Period* (PBP) untuk penggantian burner dan instalasi Pressure Reduction System (PRS):
$$PBP = \frac{\text{CAPEX}_{\text{retrofit}}}{\Delta C_{\text{annual}}} \quad [\text{Tahun}]$$
$$\text{Payback (Bulan)} = PBP \times 12$$

### 7.7 Reduksi Emisi Gas Rumah Kaca (IPCC 2006)
Mengacu pada *IPCC 2006 Guidelines for National Greenhouse Gas Inventories* (Volume 2 Energy, Stationary Combustion):
- Faktor Emisi LPG: $63.10\text{ kg }CO_2/\text{GJ}$
- Faktor Emisi Solar (HSD): $74.10\text{ kg }CO_2/\text{GJ}$
- Faktor Emisi Gas Alam (CNG): $56.10\text{ kg }CO_2/\text{GJ}$

$$\Delta CO_2 = \frac{E_{\text{useful}}}{\eta_{\text{eksisting}}} \times EF_{\text{eksisting}} - \frac{E_{\text{useful}}}{\eta_{\text{CNG}}} \times EF_{\text{CNG}}$$

### 7.8 Operator Triage & Prompt Investigasi Teknisi
Bukan memberikan analisis "kotak hitam" (AI abstrak), CNGneers menerbitkan **Investigation Prompts** berbasis deviasi fisik untuk langsung memandu tindakan teknisi boiler lapangan:
- Jika anomali disertai $O_2 > 5\%$: *"Periksa damper udara burner; kelebihan udara berlebih mendinginkan ruang bakar."*
- Jika anomali disertai kenaikan $T_{\text{flue}}$: *"Indikasi penumpukan jelaga pada pipa penukar panas; jadwalkan soot blowing / pembersihan pipa boiler."*
- Jika kondisi *idle*: *"Burner menyala saat konveyor granulasi pupuk berhenti; evaluasi prosedur interlock shutdown shift."*

---

## 8. Model Finansial, Monetisasi & Sensitivitas Unit Economics

### 8.1 Komparasi Nilai Riil Panas Berguna (LPG vs CNG)
Mengacu pada data Slide 11 Blueprint:

| Parameter Komparasi | Bahan Bakar Eksisting (LPG) | Target Bahan Bakar (CNG) |
| :--- | :---: | :---: |
| **Harga Acuan di Lapangan** | Rp16.000 / kg | Rp10.017 / $\text{Sm}^3$ |
| **Nilai Kalor Bawah (LHV)** | $46\text{ MJ/kg}$ | $36\text{ MJ/Sm}^3$ |
| **Biaya Riil Panas Berguna** | **Rp347.83 / MJ** | **Rp278.25 / MJ** |
| **Persentase Penghematan Biaya** | *Baseline* | **$\ge 20\%$ Penghematan Langsung** |

### 8.2 Proyeksi GMV Ekosistem (Baseline 50.000 Sm³/hari)
Mengacu pada Slide 12 Blueprint:
- **Volume Penyaluran Baseline:** $50.000\text{ Sm}^3/\text{hari}$ (setara 1,50 Juta $\text{Sm}^3$ / bulan).
- **Harga Jual Rata-rata:** Rp10.000 / $\text{Sm}^3$.
- **Gross Merchandise Value (GMV) Bulanan:**  
  $$\text{GMV} = 1.500.000\text{ Sm}^3 \times \text{Rp}10.000 = \mathbf{\text{Rp}15,00\text{ Miliar / Bulan}} \quad (\text{Rp}180\text{ Miliar / Tahun})$$
- *Catatan:* Perkiraan COGS fisik molekul gas adalah Rp10.80 Miliar, menyisakan spread fisik Rp4.20 Miliar untuk InfraCo (PT Aqua Gas Energy).

### 8.3 Sensitivitas Take-Rate PlatformCo (0.5% - 2.0%)
PlatformCo (CNGneers) memonetisasi transaksi digital orkestrasi gas tanpa menanggung risiko fisik:

| Skenario Take-Rate | Pendapatan Platform / Bulan | Pendapatan Platform / Tahun |
| :---: | :---: | :---: |
| **0.5% Take-Rate** | Rp75.000.000 / bulan | Rp900.000.000 / tahun |
| **1.0% Take-Rate (Baseline)** | **Rp150.000.000 / bulan** | **Rp1.800.000.000 / tahun** |
| **2.0% Take-Rate** | Rp300.000.000 / bulan | Rp3.600.000.000 / tahun |

### 8.4 Aliran Pendapatan SaaS & Implementasi API
Selain *take-rate* transaksi gas:
1. **Enterprise SaaS Tier:** Biaya langganan bulanan (Rp5 - 15 Juta/pabrik) untuk dashboard analitik tingkat lanjut, pelaporan otomatis ESG karbon ke auditor, dan alarm anomali real-time.
2. **Implementation Integration Fees:** Biaya penyiapan satu kali (*one-off*) Rp25 - 50 Juta untuk integrasi sistem IT/OT pabrik (SCADA, MES, SAP).

---

## 9. Arsitektur Teknis & Spesifikasi Sistem

### 9.1 Technology Stack Summary
* **Frontend:** React 19, TypeScript, Vite, Tailwind CSS, Lucide React, Recharts (Visualisasi responsif).
* **API Gateway:** FastAPI (Asynchronous Python), Uvicorn, Python WebSockets (`/ws/copilot`), Multipart Form Parsers.
* **Microservices Inter-Communication:** Google Protocol Buffers (Protobuf v3), gRPC over HTTP/2.
* **Analytics & Machine Learning:** NumPy, SciPy, Scikit-learn, Pandas, EasyOCR.
* **Standar Rekayasa:** ASME PTC 4, US DOE ITAC Protocols, ASHRAE Guideline 14-2014, IPCC 2006.

### 9.2 Diagram Komponen Sistem

```
+-----------------------------------------------------------------------------------------+
|                                    CLIENT TIER                                          |
|  [ React 19 + TypeScript + Vite Single Page Application ]                               |
|  Components: 5 Pillars (Simulate, Order, Track, Inventory, Pay) + Multi-Channel Ingestion|
+--------------------------------------------+--------------------------------------------+
                                             | HTTP/REST & WebSocket (/ws/copilot)
                                             v
+-----------------------------------------------------------------------------------------+
|                                   API GATEWAY TIER                                      |
|  [ FastAPI + Uvicorn Gateway (Port 8000) ]                                              |
|  - Ingestion Multiplexer (OCR Parser, File Upload, Live Stream Handler, REST Webhook)   |
|  - WebSocket Session Manager & Real-Time Event Dispatcher                               |
|  - gRPC Client Stubs with In-Process Resilient Fallback Protection                      |
+---------------------+-----------------------------------------+-------------------------+
                      | gRPC Channel (Port 50051)               | gRPC Channel (Port 50052)
                      v                                         v
+-----------------------------------------+ +---------------------------------------------+
|    ANALYTICS ENGINE MICROSERVICE        | |       CNG TRANSITION MICROSERVICE           |
|             (Port 50051)                | |               (Port 50052)                  |
| - Heating Value Energy Normalization    | | - Useful Heat Cost Modeling (Rp/MJ)         |
| - US DOE Multivariate OLS Regression    | | - Retrofit CAPEX Payback Period Simulator   |
| - Statistical Anomaly Detection (+1.5σ) | | - Annual Fuel Cost Differential Calculator  |
| - Data Quality Audit & Idle Filter      | | - IPCC 2006 Carbon Abatement Calculator     |
| - 100% Traceability Matrix Generator    | | - Technical Retrofit Recommendation Engine  |
+-----------------------------------------+ +---------------------------------------------+
```

### 9.3 Kontrak Protocol Buffer (gRPC) & WebSocket
Definisi skema antarmuka antar-layanan didefinisikan dalam `proto/energy_copilot.proto`:

```protobuf
syntax = "proto3";
package energy_copilot;

service EnergyAnalyticsService {
  rpc IngestAndAudit (IngestRequest) returns (QualityReport);
  rpc CalculateBaselineAndAnomalies (BaselineRequest) returns (BaselineResponse);
}

service CNGTransitionService {
  rpc SimulateCNGTransition (CNGSimRequest) returns (CNGSimResult);
}
```

Format komunikasi WebSocket real-time (`ws://localhost:8000/ws/copilot`):
* **Action Request:** `{"action": "RUN_FULL_PIPELINE", "payload": { "csv_raw": "...", "fuel_type": "LPG" }}`
* **Progress Stream:** `{"type": "PROGRESS", "stage": "BASELINE_DOE", "progress": 75, "message": "Menghitung Regresi..."}`
* **Completion Event:** `{"type": "PIPELINE_COMPLETE", "payload": { "quality": {...}, "baseline": {...}, "cng": {...} }}`

### 9.4 Keamanan Data, RBAC & 100% Traceability Audit Trail
- **Role-Based Access Control (RBAC):** Memisahkan akses antara Operator Pabrik (entry data/OCR), Manajer Pabrik (dashboard efisiensi & LOI), Dispatcher Aqua Gas Energy (rute armada), dan Eksekutif (laporan finansial).
- **100% Traceability Audit Trail:** Setiap angka penghematan dan payback period dapat dilacak rumusnya, input nilainya, dan referensi standarnya (ASME, ASHRAE, atau IPCC) untuk kepatuhan audit perbankan/investor.

---

## 10. Go-To-Market (GTM) Funnel & Roadmap Eksekusi

### 10.1 5-Tahap Komersial Funnel
Mengacu pada Slide 13 Blueprint:
```
+-------------------+      +-------------------+      +-------------------+      +-------------------+      +-------------------+
| 1. LEAD QUALIF.   | ---> | 2. TECHNO-ECON.   | ---> | 3. PILOT &        | ---> | 4. FULFILLMENT    | ---> | 5. SCALE GATE     |
|                   |      |    SCREENING      |      |    OFF-TAKE       |      |                   |      |                   |
| KPI: Validasi     |      | KPI: Lokasi lolos |      | KPI: Penandatangan|      | KPI: Pengiriman   |      | KPI: Margin unit  |
| profil konsumsi,  |      | threshold hemat   |      | LOI/Kontrak pasok |      | OTIF, efisiensi   |      | positif & payback |
| tipe burner &     |      | ≥20% dan payback  |      | gas & retensi     |      | km/Sm³, dan DSO   |      | terbukti selama   |
| verifikasi lokasi |      | retrofit terbukti |      | pelanggan         |      | < 14 hari         |      | 3-6 bulan         |
+-------------------+      +-------------------+      +-------------------+      +-------------------+      +-------------------+
```

### 10.2 Roadmap Eksekusi Berjenjang (Fase 0 s/d Fase 4)
Mengacu pada Slide 16 Blueprint:
* **Fase 0: Validasi MVP (Okt - Nov 2026):**
  - Penyelesaian audit HKI (*Intellectual Property*), demo fungsional 5 pilar platform, dan verifikasi algoritma perhitungan termodinamika.
  - *Tollgate 1:* Margin unit positif dan metrik On-Time-In-Full (OTIF) tervalidasi.
* **Fase 1: B2B Pilot Run:**
  - Mengunci 1 kluster industri percontohan (3 off-taker industri, termasuk fasilitas granulasi PT Indmira).
  - Pembuktian penghematan biaya riil di lapangan.
* **Fase 2: Integrasi ERP & Skalabilitas:**
  - Otomasi penagihan terintegrasi bank/fintech, *onboarding* 5 - 10 pabrik industri baru.
  - *Tollgate 2:* Model kelayakan IRR dan *Debt Service Coverage Ratio (DSCR)* disetujui komite investasi perbankan.
* **Fase 3 & 4: Ekspansi Skala Penuh:**
  - Ekspansi infrastruktur InfraCo (pembangunan mother station tambahan berkapasitas 4.0 MMSCFD).
  - Evaluasi adopsi sektor komersial dan UMKM kuliner/binatu.

---

## 11. Manajemen Risiko & Mitigasi Struktural

Mengacu pada Slide 15 Blueprint:

| Kategori Risiko | Potensi Dampak | Mitigasi Struktural Platform CNGneers |
| :--- | :--- | :--- |
| **Asset Utilization Risk** | Truk tube trailer dan kompresor menganggur karena pabrik batal konversi. | **Staged Drawdown & Pre-Conditioned Off-Take:** Infrastruktur fisik baru dikerahkan setelah pabrik menandatangani kontrak serapan gas terverifikasi melalui modul `ORDER`. |
| **Commercial & Receivables Risk** | Pabrik menunda pembayaran tagihan gas, mengganggu arus kas operasional. | **Automated Invoicing & Limit Kredit:** Sistem penagihan otomatis via virtual account dengan penerapan deposit jaminan awal dan penegakan limit kredit ketat di modul `PAY`. |
| **Logistics & Safety Risk** | Keterlambatan pengiriman gas akibat kemacetan atau insiden keselamatan armada. | **Cycle-Time Simulation & Telematics:** Optimasi rute berbasis waktu tempuh dinamis, audit kepatuhan HSSE berkala, dan e-POD real-time di modul `TRACK`. |
| **Cyber & Platform Risk** | Kebocoran data sensitif volume produksi pabrik atau manipulasi tagihan. | **Data Governance & RBAC:** Enkripsi end-to-end data telemetri, pembatasan akses berbasis peran, dan audit berkala independen. |

---

## 12. Strategi Pitching Hackathon: Mengapa CNGneers Pemenang Mutlak

### 12.1 Keunggulan Mutlak vs Inovasi Hardware (Robot Sampah / Biomassa)

Dalam ajang inovasi tingkat korporat seperti **ANGEL Innovation Hackathon**, inovasi fisik (seperti robot pemilah sampah otomatis atau mesin pelet biomassa) sering kali memikat pandangan visual pertama, namun memiliki kelemahan mendasar di depan juri korporat dan investor:

1. **Relevansi Pasar dengan Tuan Rumah (The Host Advantage):**
   - Penyelenggara hackathon ini adalah **PT Aqua Gas Energy** (perusahaan gas CNG) dan **PT Indmira** (agro-industri yang membakar bahan bakar setiap hari).
   - Robot sampah atau biomassa tidak ada hubungannya dengan rantai nilai gas PT Aqua Gas Energy.
   - **CNGneers secara langsung memecahkan masalah ekspansi bisnis PT Aqua Gas Energy dan efisiensi biaya pabrik PT Indmira.**

2. **Jebakan Modal (CAPEX Trap) vs Skalabilitas SaaS:**
   - Robot atau mesin pelet biomassa butuh bengkel perakitan, komponen mekanik impor yang rawan aus, logistik fisik berat, dan margin laba tipis (15% - 20%).
   - CNGneers adalah **Asset-Light Software Platform** dengan margin kotor tinggi (>75%), dapat digunakan di ribuan pabrik tanpa perlu membangun pabrik perakitan, dan menghasilkan pendapatan berulang (*recurring revenue*) dari *take-rate* transaksi gas.

3. **Skala Dampak Nasional:**
   - Isu yang diselesaikan CNGneers adalah **kebocoran devisa impor LPG 8,6 juta ton per tahun (81% impor)**, sebuah isu prioritas kedaulatan energi nasional.

---

### 12.2 Lembar Jawaban Tangkas (Q&A Defense Guide) Dewan Juri

#### Pertanyaan Juri 1: *"Mengapa membuat software, bukan membuat alat hardware/sensor fisik baru?"*
> **Jawaban:**  
> *"Bapak/Ibu dewan juri, masalah terbesar industri hari ini bukan ketiadaan sensor, melainkan **ketiadaan orkestrasi data**. Boiler pabrik seperti di PT Indmira sudah memiliki flow meter gas, termokopel, dan manometer steam. Gas CNG di PT Aqua Gas Energy sudah siap dialirkan. Hambatan utamanya adalah ketakutan pabrik akan biaya konversi burner dan rantai pasok distribusi yang masih manual. Jika kami membuat hardware baru, kami menambah beban CAPEX pabrik. Dengan platform digital asset-light, kami menghubungkan aset yang sudah ada hari ini dengan biaya adopsi nol rupiah."*

#### Pertanyaan Juri 2: *"Bagaimana jika pabrik masih tradisional dan tidak punya koneksi internet di ruang boiler?"*
> **Jawaban:**  
> *"Itulah keunggulan **Multi-Channel Ingestion** kami. Operator tidak perlu mengubah kebiasaan mereka: mereka tetap mencatat angka di kertas logbook seperti biasa. Supervisor cukup memotret kertas tersebut dengan ponsel, dan **Smart Logbook OCR** kami yang akan mengekstrak data menjadi audit energi digital secara otomatis."*

#### Pertanyaan Juri 3: *"Bagaimana platform ini menghasilkan uang untuk investor?"*
> **Jawaban:**  
> *"PlatformCo mengambil **1.0% transaction take-rate** dari penyaluran gas. Untuk kapasitas 50.000 Sm³/hari saja, GMV transaksi gas mencapai Rp15 Miliar/bulan, menghasilkan pendapatan perangkat lunak **Rp1,80 Miliar per tahun** dengan margin kotor di atas 75% tanpa menanggung biaya fisik molekul gas atau depresiasi armada truk."*

---

*(Dokumen ini menjadi rujukan tunggal pengkodean, pengujian, dan materi presentasi panggung tim CNGneers dalam ajang ANGEL Innovation Hackathon 2026).*
