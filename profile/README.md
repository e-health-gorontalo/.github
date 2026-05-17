# E-Health Gorontalo

**E-Health Gorontalo** adalah ekosistem aplikasi kesehatan digital yang terintegrasi, dikembangkan oleh **M2Code** untuk mendigitalisasi layanan kesehatan di Gorontalo, Indonesia. Ekosistem ini terdiri dari tiga aplikasi yang saling terhubung untuk mendukung apotek, klinik, dan tenaga kesehatan.


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
