# Panduan dan Progress Screenshot Laporan PPG Pertemuan 5 — Game Instance & SaveGame

> **Status Saat Ini:** ✅ **Selesai Lengkap**. Seluruh 17 screenshot praktikum telah berhasil diambil langsung dari proyek Unreal Engine 5.8 dan dikompilasi sempurna ke dalam dokumen laporan `laporan-5.pdf` serta berkas pengumpulan resmi.

---

## Ringkasan Praktikum
- **Project:** `HAFIDZ_535493_PPG` (template Games > Third Person)
- **Engine:** Unreal Engine 5.8
- **Topik:** Game Instance & SaveGame (Persistent Data Storage, Structure, Blueprint Interface, dan Checkpoint)
- **File Laporan:** `laporan-5.tex`
- **Output Dokumen PDF:**
  - `laporan-5.pdf`
  - `535493_Hafidz Rizqullah Prasetya_PPG_Pertemuan 5.pdf`
  - `535493_Hafidz-Rizqullah-Prasetya_PPG_Pertemuan-5.pdf`

---

## Daftar Kebutuhan Screenshot (17 Screenshot)

Berikut daftar lengkap seluruh tangkapan layar yang dibutuhkan laporan Pertemuan 5, berurutan sesuai alur modul praktikum:

| # | Nama File | Status | Keterangan & Panduan Tampilan di Unreal Engine 5.8 |
|---|-----------|:------:|----------------------------------------------------|
| 1 | `ss-01-create-bp-savegame.png` | ✅ Selesai | Jendela **Pick Parent Class** pada Unreal Engine: di bagian *ALL CLASSES*, cari `SaveGame`, pilih class `SaveGame`, lalu buat Blueprint dengan nama `BP_SaveGame`. |
| 2 | `ss-02-create-struct-playerstate.png` | ✅ Selesai | Pembuatan Structure di Content Drawer (**Add > Blueprint > Structure**) bernama `S_PlayerState`. Tampilkan tab editor struktur yang berisi satu variabel bernama `Transform` dengan tipe data **Transform**. |
| 3 | `ss-03-bp-savegame-variable.png` | ✅ Selesai | Editor `BP_SaveGame`: panel *My Blueprint* bagian **Variables** menampilkan variabel bernama `S_PlayerState` bertipe data **S_PlayerState** (struktur yang dibuat pada langkah 2). |
| 4 | `ss-04-bp-gameinstance-project-settings.png` | ✅ Selesai | Dua bagian: (1) Jendela *Pick Parent Class* memilih `GameInstance` untuk membuat `BP_GameInstance`; (2) Jendela **Project Settings > Project - Maps & Modes**, field **Game Instance Class** diatur ke `BP_GameInstance`. |
| 5 | `ss-05-gameinstance-variables.png` | ✅ Selesai | Editor `BP_GameInstance`: panel *My Blueprint* menampilkan dua variabel: `SaveGame` (tipe objek `BP_SaveGame`) dan `SlotName` (tipe `String` dengan Default Value misalnya `"1"`). |
| 6 | `ss-06-bpi-savedata-functions.png` | ✅ Selesai | Editor Blueprint Interface `BPI_SaveData`: panel *Functions* menampilkan 4 fungsi (`LoadGameData`, `SaveGameData`, `GetGameData`, `SavePlayer`) beserta rincian parameter input/output di panel Details. |
| 7 | `ss-07-gameinstance-implement-interface.png` | ✅ Selesai | Editor `BP_GameInstance`: panel **Class Settings** bagian *Implemented Interfaces* menampilkan `BPI_SaveData`, serta panel kiri memunculkan grup tab **INTERFACES**. |
| 8 | `ss-08-gameinstance-getgamedata.png` | ✅ Selesai | Graph fungsi `GetGameData` di `BP_GameInstance`: alur node `Does Save Game Exist` -> `Branch` -> `Return Node` (mengembalikan data dari `SaveGame` jika True, atau nilai default transform jika False). |
| 9 | `ss-09-gameinstance-saveplayer.png` | ✅ Selesai | Graph fungsi `SavePlayer` di `BP_GameInstance`: node `Event SavePlayer` menerima struct player dan boolean Async -> `SET` variabel struct pada `SaveGame` -> memanggil fungsi `SaveGameData`. |
| 10 | `ss-10-gameinstance-savegamedata.png` | ✅ Selesai | Graph fungsi `SaveGameData` di `BP_GameInstance`: node `Event SaveGameData` -> `Branch` (Async) -> cabang True ke `Async Save Game to Slot` dan cabang False ke `Save Game to Slot`. |
| 11 | `ss-11-gameinstance-loadgamedata.png` | ✅ Selesai | Graph fungsi `LoadGameData` di `BP_GameInstance`: alur `Does Save Game Exist` -> `Branch` -> memuat slot (Async/Sync) -> `Cast To BP_Savegame` -> `SET SaveGame`; jika belum ada, memanggil `Create Save Game Object`. |
| 12 | `ss-12-gameinstance-event-init.png` | ✅ Selesai | Event Graph `BP_GameInstance`: node `Event Init` terhubung langsung ke panggilan node `Load Game Data` (Target: self, Async dimatikan). |
| 13 | `ss-13-character-beginplay-restore-location.png` | ✅ Selesai | Event Graph `BP_ThirdPersonCharacter`: node `Event BeginPlay` -> `Get Game Instance` -> pesan interface `Get Game Data` -> `Branch` pengecekan koordinat non-nol -> `Set Actor Location`. |
| 14 | `ss-14-create-bp-checkpoint.png` | ✅ Selesai | Editor `BP_CheckPoint`: hierarki komponen memuat `Box` (Box Collision), dan Event Graph menampilkan `On Component Begin Overlap (Box)` -> `Do Once` -> `Get Actor Transform` & `Get Game Instance` -> interface `Save Player`. |
| 15 | `ss-15-placement-checkpoint-in-level.png` | ✅ Selesai | Viewport Level editor: satu atau dua instance `BP_CheckPoint` diletakkan di lintasan karakter di arena permainan. Garis batas kotak kawat checkpoint terlihat jelas. |
| 16 | `ss-16-hasil-akhir-trigger-checkpoint.png` | ✅ Selesai | Uji coba Play mode: karakter Third Person digerakkan berjalan melintasi `BP_CheckPoint`, memicu event overlap dan eksekusi fungsi simpan posisi. |
| 17 | `ss-17-hasil-akhir-restore-position-on-play.png` | ✅ Selesai | Uji coba Play kedua (setelah game dihentikan/di-restart): karakter pemain otomatis muncul dan langsung berdiri pada koordinat Checkpoint yang telah tersimpan di disk. |

---

## Petunjuk Penggantian Screenshot

1. Buka project Unreal Engine 5.8 Anda (`HAFIDZ_535493_PPG`).
2. Ambil screenshot sesuai nomor urut di atas menggunakan tool tangkapan layar (misalnya *Snipping Tool*, *Flameshot*, atau tombol *Print Screen*).
3. Simpan file hasil tangkapan layar ke folder:
   ```text
   pertemuan-5/images/
   ```
   Pastikan nama file persis sama dengan nama di tabel (format `.png`).
4. Setelah screenshot diganti, jalankan perintah kompilasi XeLaTeX:
   ```bash
   xelatex -interaction=nonstopmode laporan-5.tex
   xelatex -interaction=nonstopmode laporan-5.tex
   ```
5. Perbarui status checklist di tabel ini menjadi `✅ Selesai`.
