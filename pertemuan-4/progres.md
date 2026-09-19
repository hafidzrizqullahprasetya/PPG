# Progress Laporan PPG Pertemuan 4 — Interface, Component & Collision

> Update: 2026-09-20 — 16 / 16 screenshot selesai (100% LENGKAP & VALID! 🎉)

## Ringkasan Praktikum
- **Project:** `HAFIDZ_535493_PPG` (template GAMES > Third Person)
- **Engine:** Unreal Engine 5.8
- **Topik:** Interface, Component & Collision
- **Laporan:** `laporan-4.tex` (XeLaTeX exit 0, terkompilasi bersih, 20 halaman, ukuran ~5.3 MB < batas 10 MB)
- **Output Dokumen PDF:**
  - `laporan-4.pdf`
  - `535493_Hafidz Rizqullah Prasetya_PPG_Pertemuan 4.pdf`
  - `535493_Hafidz-Rizqullah-Prasetya_PPG_Pertemuan-4.pdf`

---

## Daftar Kebutuhan Screenshot (16/16 Selesai)

| # | Nama File | Status | Keterangan & Bagian Tampilan di Unreal Engine |
|---|-----------|:------:|-----------------------------------------------|
| 1 | `ss-01-create-bpc-health.png` | ✅ | Inisiasi Actor Component `BPC_Health`, variabel `CurrentHealth` & `MaxHealth` (Float), fungsi `ModifyHealth`, dan Event Dispatcher `OnDeath` di panel My Blueprint |
| 2 | `ss-02-bpc-health-beginplay.png` | ✅ | Event Graph `BPC_Health`: node `Event BeginPlay` terhubung ke `SET CurrentHealth` dengan input dari `MaxHealth` (100.0) |
| 3 | `ss-03-fungsi-modify-health.png` | ✅ | Graph fungsi `ModifyHealth`: input `Health`, pengurangan `CurrentHealth - Health`, Branch validasi/clamp, assignment `CurrentHealth`, Branch `CurrentHealth <= 0.0`, dan `Call OnDeath` |
| 4 | `ss-04-add-bpc-to-character.png` | ✅ | Hierarki panel Components `BP_ThirdPersonCharacter` yang memuat komponen `BPC_Health` |
| 5 | `ss-05-bind-ondeath-character.png` | ✅ | Event binding `OnDeath (BPC_Health)` di `BP_ThirdPersonCharacter` terhubung ke `Set Actor Scale 3D` (0.0, 0.0, 0.0) |
| 6 | `ss-06-create-folder-interfaces.png` | ✅ | Pembuatan folder `Interfaces` di Content Drawer dan aset Blueprint Interface `BPI_Overlap` |
| 7 | `ss-07-fungsi-take-damage.png` | ✅ | Definisi fungsi `TakeDamage` di dalam `BPI_Overlap` dengan parameter input `AmountDamage` bertipe Float |
| 8 | `ss-08-implement-interface-character.png` | ✅ | Panel Class Settings pada `BP_ThirdPersonCharacter` bagian Implemented Interfaces menambahkan `BPI_Overlap` |
| 9 | `ss-09-take-damage-in-myblueprint.png` | ✅ | Panel My Blueprint `BP_ThirdPersonCharacter` setelah di-compile, menampilkan kategori Interfaces dan fungsi `TakeDamage` |
| 10 | `ss-10-event-take-damage-character.png` | ✅ | Event Graph `BP_ThirdPersonCharacter`: `Event TakeDamage` meneruskan `AmountDamage` ke `ModifyHealth` (`BPC_Health`) dan memanggil `Print String` ("Damage Taken!") |
| 11 | `ss-11-create-bp-collision.png` | ✅ | Actor Blueprint `BP_Collision` berisi komponen Box Collision, event `OnComponentBeginOverlap` memanggil interface `TakeDamage (Target is BPI Overlap)` |
| 12 | `ss-12-box-hidden-in-game.png` | ✅ | Panel Details komponen Box pada `BP_Collision`, uncheck opsi Rendering `Hidden in Game` agar garis batas terlihat saat play |
| 13 | `ss-13-instance-editable-damage.png` | ✅ | Variabel `Damage` (Float) pada `BP_Collision` dengan opsi `Instance Editable` aktif (ikon mata terbuka) terhubung ke pin `AmountDamage` |
| 14 | `ss-14-set-damage-in-level.png` | ✅ | Instance `BP_Collision` di Level Viewport dengan nilai parameter `Damage` diatur menjadi `30.0` pada panel Details level |
| 15 | `ss-15-hasil-akhir-overlap-damage.png` | ✅ | Uji coba Play saat karakter masuk ke dalam Box Collision: menerima damage 30.0, health berkurang, dan teks debug Print String "Damage Taken!" muncul |
| 16 | `ss-16-hasil-akhir-ondeath-scale.png` | ✅ | Uji coba Play saat health mencapai 0: event dispatcher `OnDeath` terpicu dan skala karakter menyusut menjadi (0.0, 0.0, 0.0) |

---

## Verifikasi Akhir
- Seluruh 16 file screenshot resolusi tinggi dari project `HAFIDZ_535493_PPG` telah diperiksa dan disinkronkan ke dalam deskripsi laporan.
- Teks laporan disusun dengan kaidah humanizer (gaya bahasa natural mahasiswa, bebas kata klise AI, tanpa em-dash, narasi berbasis fakta visual riil).
- Seluruh 10 daftar pustaka aktif dan lolos uji aksesibilitas (HTTP 200).
- Ukuran file PDF (5.3 MB) memenuhi syarat maksimal 10 MB dari Google Forms pengumpulan tugas.
