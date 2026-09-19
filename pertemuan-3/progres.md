# Progress Laporan PPG Pertemuan 3 — Variable & Condition

> Update: 2026-09-20 — 12 / 12 screenshot done (100% COMPLETE! 🎉)

## Ringkasan
- **Project:** `HAFIDZ_535493_PPG` (template GAMES > Third Person)
- **Engine:** Unreal Engine 5.8
- **Level:** Level baru di dalam folder `Maps` (`L_Main`)
- **Laporan:** `laporan-3.tex` (xelatex exit 0)
- **Aturan file:** `535493_Hafidz Rizqullah Prasetya_PPG_Pertemuan 3.pdf`

## Screenshot — Done (12/12)
| # | File | Status | Keterangan |
|---|------|--------|------------|
| 1 | `ss-01-project-thirdperson.png` | ✅ | Jendela New Project: kategori Games, template Third Person, Project Name `HAFIDZ_535493_PPG` |
| 2 | `ss-02-maps-level.png` | ✅ | Folder Maps di Content Drawer beserta file Level baru (`L_Main`) |
| 3 | `ss-03-env-light-mixer.png` | ✅ | Panel Env. Light Mixer dengan semua opsi pencahayaan yang sudah di-Create |
| 4 | `ss-04-landscape-playerstart.png` | ✅ | Landscape 7x7 di Level serta penempatan actor Player Start sebagai titik spawn |
| 5 | `ss-05-bp-box-cube.png` | ✅ | Blueprint editor `BP_Box`: komponen Cube yang ditambahkan lewat tombol Add |
| 6 | `ss-06-event-beginplay-tick.png` | ✅ | Event Graph `BP_Box`: Event BeginPlay terhubung ke Print String |
| 7 | `ss-07-variabel-boolean.png` | ✅ | Panel My Blueprint: variabel Boolean `IsActive` beserta drop-down tipe data |
| 8 | `ss-08-add-node-branch.png` | ✅ | Menu klik kanan penambahan node di Event Graph dengan pencarian Branch |
| 9 | `ss-09-rangkaian-keyboard-branch.png` | ✅ | Untaian Event Tick, Keyboard R, Set/Get Boolean, Branch, dan Print String |
| 10 | `ss-10-scale-target.png` | ✅ | Variabel float `ScaleTarget` dengan default value 0.1 di panel My Blueprint |
| 11 | `ss-11-tugas-tick-scale.png` | ✅ | Rangkaian Event Tick tugas: scale mesh bergeser real-time menuju 0.1 dengan Set Relative Scale 3D |
| 12 | `ss-12-hasil-akhir-play.png` | ✅ | Hasil akhir saat simulasi Play: cube di world dan teks debug Print String di layar |

Semua screenshot telah lengkap 100% dan terkompilasi ke dokumen PDF resmi!

### 4. Tugas: Aplikasi If/Else Pengubah Scale Real-Time (2)
- [ ] `ss-10-scale-target.png` — Variabel float `scale target` dengan default value 0.1 di panel My Blueprint (`fig:ss-scaletarget`)
- [ ] `ss-11-tugas-tick-scale.png` — Rangkaian Event Tick tugas: scale mesh bergeser real-time menuju 0.1 dengan pin konektor dikonversi ke float (`fig:ss-tickscale`)

### 5. Hasil Akhir (1)
- [ ] `ss-12-hasil-akhir-play.png` — Hasil akhir saat simulasi Play: cube berubah skala secara real-time dan feedback tombol R terlihat (`fig:hasil-akhir`)

### 2. Blueprint, Event, dan Variabel (3)
- [ ] `ss-05-bp-box-cube.png` — Blueprint editor `BP_Box` di folder Blueprints, komponen Cube yang ditambahkan lewat tombol Add (`fig:ss-bpbox`)
- [ ] `ss-06-event-beginplay-tick.png` — Event Graph `BP_Box`: Event BeginPlay dan Event Tick beserta teks debug Print String di viewport (`fig:ss-event`)
- [ ] `ss-07-variabel-boolean.png` — Panel My Blueprint: pembuatan variabel Boolean baru pada `BP_Box` beserta drop-down tipe data (`fig:ss-variable`)

### 3. Branch dan Input Keyboard (2)
- [ ] `ss-08-add-node-branch.png` — Menu klik kanan penambahan node di Event Graph dengan pencarian Branch / If (`fig:ss-addnode`)
- [ ] `ss-09-rangkaian-keyboard-branch.png` — Untaian Event Tick, Keyboard R, Set/Get Boolean, Not, Branch, dan dua Print String (`fig:ss-keyboard`)

### 4. Tugas: Aplikasi If/Else Pengubah Scale Real-Time (2)
- [ ] `ss-10-scale-target.png` — Variabel float `scale target` dengan default value 0.1 di panel My Blueprint (`fig:ss-scaletarget`)
- [ ] `ss-11-tugas-tick-scale.png` — Rangkaian Event Tick tugas: scale mesh bergeser real-time menuju 0.1 dengan pin konektor dikonversi ke float (`fig:ss-tickscale`)

### 5. Hasil Akhir (1)
- [ ] `ss-12-hasil-akhir-play.png` — Hasil akhir saat simulasi Play: cube berubah skala secara real-time dan feedback tombol R terlihat (`fig:hasil-akhir`)

## Cara Lanjut
1. Ambil screenshot di Unreal Engine sesuai slot di atas (bisa 1 per 1 atau sekaligus).
2. Kirim screenshot ke agent — otomatis disimpan ke `pertemuan-3/images/ss-XX-*.png` + ganti `images/placeholder.png` → `images/ss-XX-*.png` di `laporan-3.tex` + build PDF laporan.
