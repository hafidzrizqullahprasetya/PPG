# Panduan dan Progres Screenshot Laporan PPG Pertemuan 7 — Asset FAB dan Widget Blueprint (UI)

> **Status Saat Ini:** 🟡 **Scaffolding Siap (0/19 Screenshot Terpasang)**. Struktur folder, modul, dan dokumen laporan telah disiapkan. Menunggu pengambilan tangkapan layar praktikum di Unreal Engine 5.8.

---

## Ringkasan Praktikum
- **Project:** `HAFIDZ_535493_PPG` (Unreal Engine 5.8, template Third Person)
- **Level Target:** `LV_Praktikum`
- **Topik Utama:**
  1. Integrasi Aset Marketplace FAB (`Landscape Pro 2.0`)
  2. Penerapan Material Multi-Layer & Layer Info pada Landscape
  3. Penataan Vegetasi Lingkungan (*Foliage* manual & Foliage Mode)
  4. Perancangan UI UMG (`WBP_Health` & `WBP_HUD`)
  5. Pembuatan Animasi UI Translasi (*Shake Effect* 0.25 detik)
  6. Arsitektur Komunikasi Modular via Blueprint Interface (`BPI_HUD` & `BPI_Widget`)
  7. Integrasi Sistem Darah dengan UI via `BP_GameInstance`, `BP_ThirdPersonPlayerController`, dan `BP_ThirdPersonCharacter`
- **File Laporan:** `laporan-7.tex`
- **Output Berkas PDF:**
  - `laporan-7.pdf`
  - `535493_Hafidz Rizqullah Prasetya_PPG_Pertemuan 7.pdf`
  - `535493_Hafidz-Rizqullah-Prasetya_PPG_Pertemuan-7.pdf`

---

## Daftar Kebutuhan Screenshot (19 Screenshot)

Berikut daftar lengkap seluruh tangkapan layar yang dibutuhkan laporan Pertemuan 7, berurutan sesuai alur modul pembelajaran:

| # | Nama File | Status | Keterangan dan Panduan Tampilan di Unreal Engine 5.8 |
|---|-----------|:------:|-----------------------------------------------------|
| 1 | `ss-01-fab-browsing-landscapepro.png` | ✅ Selesai | Tab **Fab** pada Epic Games Launcher / Fab Library: pencarian aset **Landscape Pro 2.0**. |
| 2 | `ss-02-fab-add-to-project-version-55.png` | ✅ Selesai | Jendela **Add To Project**: memilih proyek `HAFIDZ_535493_PPG` dan mengatur versi ke **5.5**. |
| 3 | `ss-03-content-drawer-foliage-assets.png` | ✅ Selesai | Content Drawer membuka folder `Content/STF/Pack03-LandscapePro/Environment/Foliage` dengan filter Static Mesh. |
| 4 | `ss-04-landscape-material-assigned.png` | ✅ Selesai | Level `LV_Praktikum`: panel Details aktor Landscape dengan slot **Landscape Material** diisi `MI_landscape_pro_v2_inst`. |
| 5 | `ss-05-landscape-paint-layer-info.png` | ✅ Selesai | Landscape Mode (Shift+2) tab **Paint**: daftar material layer yang telah terisi kontainer **Layer Info**. |
| 6 | `ss-06-landscape-painting-variation.png` | ✅ Selesai | Tampilan Viewport hasil sapuan kuas (*painting*) variasi layer tanah, rumput, dan genangan air (*puddle*). |
| 7 | `ss-07-foliage-manual-placement.png` | ✅ Selesai | Penempatan aset model pohon (*foliage*) secara manual dengan cara drag & drop langsung ke atas landscape. |
| 8 | `ss-08-foliage-mode-painting.png` | ✅ Selesai | Panel **Foliage Mode** (Shift+3): daftar Static Mesh Foliage aktif dan tampilan viewport setelah foliage di-paint secara masif. |
| 9 | `ss-09-create-wbp-hud-and-health.png` | ✅ Selesai | Content Drawer membuka folder `Content/Widget` memperlihatkan aset **`WBP_HUD`** dan **`WBP_Health`**. |
| 10 | `ss-10-wbp-health-progress-bar.png` | ✅ Selesai | Editor `WBP_Health`: komponen **`HealthBar`** di Hierarchy, Details: Fill Color hijau dan Percent 1.0. |
| 11 | `ss-11-timeline-onupdatehealthanimation.png` | ✅ Selesai | Panel Animations: animasi **`onUpdateHealthAnimation`** (durasi 0.25s) dengan keyframe Translation X/Y (*shake*). |
| 12 | `ss-12-wbp-hud-canvas-panel-hierarchy.png` | ✅ Selesai | Editor `WBP_HUD`: panel Hierarchy `[WBP_HUD] > [Canvas Panel] > [WBP_Health]` di sudut kiri atas kanvas viewport. |
| 13 | `ss-13-bpi-hud-interface-setup.png` | ✅ Selesai | Editor `BPI_HUD`: fungsi **`UpdateHealthValue`** dengan input `CurrentHealth` (Float) dan `MaxHealth` (Float). |
| 14 | `ss-14-bpi-widget-interface-setup.png` | ✅ Selesai | Editor `BPI_Widget`: fungsi **`SetHUDWidget`** (input: HUD) dan fungsi **`GetHUDWidget`** (output: HUD). |
| 15 | `ss-15-wbp-hud-event-updatehealthvalue.png` | ✅ Selesai | Graph `WBP_HUD`: alur eksekusi Event `UpdateHealthValue` memanggil `Play Animation` dan `Set Percent (Current/Max)`. |
| 16 | `ss-16-gameinstance-bpi-widget-setup.png` | ✅ Selesai | Blueprint `BP_GameInstance`: variabel `AddedWidget` (User Widget) serta implementasi fungsi `SetHUDWidget` & `GetHUDWidget`. |
| 17 | `ss-17-playercontroller-create-hud.png` | ✅ Selesai | Graph `BP_ThirdPersonPlayerController`: alur `Create Widget WBP_HUD` -> `Set HUDWidget` (GameInstance) -> `Add to Player Screen`. |
| 18 | `ss-18-character-takedamage-update-hud.png` | ⏳ Pending | Graph `BP_ThirdPersonCharacter`: alur `Event TakeDamage` -> `Modify Health` -> `Get HUDWidget` -> `Update Health Value`. |
| 19 | `ss-19-hasil-akhir-gameplay-ui-healthbar.png` | ⏳ Pending | Uji coba gameplay pada level `LV_Praktikum`: HUD HealthBar hijau muncul di kiri atas, berkurang dan bergetar saat terkena collider hazard. |

---

## Petunjuk Pengambilan dan Pemasangan Screenshot

1. Buka project Unreal Engine 5.8 (`HAFIDZ_535493_PPG`).
2. Tangkap layar sesuai nomor urut di atas menggunakan tool screenshot.
3. Simpan berkas hasil tangkapan layar ke folder:
   ```text
   pertemuan-7/images/
   ```
   Pastikan nama berkas persis sama dengan nama di tabel di atas (format `.png`).
4. Setelah screenshot terpasang, jalankan perintah kompilasi XeLaTeX:
   ```bash
   cd /home/hafidzprasetya/Kuliah/PPG/pertemuan-7
   xelatex -interaction=nonstopmode laporan-7.tex
   xelatex -interaction=nonstopmode laporan-7.tex
   ```
5. Perbarui status checklist di tabel ini menjadi `✅ Selesai`.
