# E-Health Gorontalo

**E-Health Gorontalo** adalah ekosistem aplikasi kesehatan digital yang terintegrasi, dikembangkan oleh **M2Code** untuk mendigitalisasi layanan kesehatan di Gorontalo, Indonesia. Ekosistem ini terdiri dari tiga aplikasi yang saling terhubung untuk mendukung apotek, klinik, dan tenaga kesehatan.

---

## Aplikasi dalam Ekosistem

### ObatPedia
Pusat data obat dan sistem manajemen apotek. ObatPedia berperan sebagai **hub integrasi** yang menghubungkan seluruh ekosistem — mengelola data master obat, stok per apotek, transaksi penjualan, resep dari klinik, serta autentikasi terpusat.

**Fitur utama:**
- Manajemen stok obat per apotek dengan batch tracking
- Sistem inventory double-ledger untuk audit trail lengkap
- Manajemen resep dari klinik (reservasi, dispensing)
- Integrasi dengan aplikasi Kasir dan Klinik
- Role-based access (PSA, Apoteker, Pegawai, Admin)

**Tech Stack:** Laravel 12, Blade, MySQL, DomPDF, JWT Auth

### Kasir (Obat Pedia Kasir)
Aplikasi **Point of Sale (POS)** untuk transaksi apotek yang terintegrasi penuh dengan ObatPedia. Digunakan oleh apoteker untuk melayani pembelian obat walk-in maupun dispensing resep dari klinik.

**Fitur utama:**
- POS dengan pencarian produk dan scan barcode/QR
- Manajemen resep (cari, reserve, checkout)
- Cetak struk via printer thermal atau browser
- Dashboard analitik penjualan dan omset
- Integrasi real-time stok dengan ObatPedia

**Tech Stack:** Laravel 11, Filament 3, Livewire, MySQL, Thermal Printer

### E-Clinic
Sistem **manajemen klinik multi-tenant** dengan **enkripsi end-to-end (E2EE)** untuk keamanan rekam medis. Dirancang untuk klinik yang membutuhkan pencatatan medis digital yang aman dan sesuai standar.

**Fitur utama:**
- Rekam medis terenkripsi (XChaCha20-Poly1305)
- Multi-tenant: satu instalasi untuk banyak klinik
- Visit lifecycle: dari pendaftaran hingga selesai
- Daily sessions & manajemen antrian real-time
- Portal pasien untuk akses riwayat kunjungan
- Workspace dokter dengan pencatatan SOAP
- Integrasi resep dengan ObatPedia
- Audit trail lengkap

**Tech Stack:** Laravel 12, Inertia.js + React 19, Reverb WebSocket, MySQL, Libsodium

---

## Arsitektur Integrasi

Ketiga aplikasi saling terhubung melalui **ObatPedia** sebagai pusat integrasi:

| Antara | Metode | Data |
|--------|--------|------|
| **ObatPedia ↔ Kasir** | REST API + HMAC + JWT | Produk, stok, transaksi, resep |
| **ObatPedia ↔ E-Clinic** | REST API + HMAC + JWT | Resep, stok obat, reservasi |
| **SSO** | Redirect + JWT Token | Autentikasi terfederasi |

Keamanan dijamin dengan:
- **Federated Login**: Login cukup sekali di ObatPedia, akses semua aplikasi
- **HMAC-SHA256 Signature**: Setiap request integrasi ditandatangani
- **JWT Token**: Token akses dengan refresh mechanism
- **E2EE**: Data medis terenkripsi ujung-ke-ujung

---

## Memulai

Setiap aplikasi memiliki petunjuk instalasi sendiri:

| Aplikasi | Panduan |
|----------|---------|
| **ObatPedia** | `obatpedia-v2/README.md` — `composer setup` untuk instalasi penuh |
| **Kasir** | `cashier/README.md` — konfigurasi .env dan migrasi database |
| **E-Clinic** | `e-clinic/README.md` — seed clinic roles & permissions |

---

## Teknologi Umum

| Lapisan | Teknologi |
|---------|-----------|
| Backend | PHP 8.2+, Laravel 11 / 12 |
| Frontend | Blade + Livewire / Filament 3 / Inertia.js + React 19 |
| Database | MySQL 8+ |
| Build Tools | Vite, Tailwind CSS 4 |
| Real-time | Laravel Reverb (E-Clinic) |
| Queue | Database-driven |
| Auth | Laravel Session, JWT, Sanctum, Spatie Permission |

---

*© 2026 E-Health Gorontalo. Seluruh hak cipta dilindungi undang-undang.*
