# Progress Laporan PPG Pertemuan 2 — Navigate Unreal Engine 5.8

> Update: 2026-09-01 09:51 WIB — 4 / 27 screenshot done (15%)

## Ringkasan
- **Project:** `HAFIDZ_535493_Intro` (template GAMES > Intro To Unreal)
- **Engine:** UE 5.8.1 via Epic Games Launcher
- **Level:** `Lvl_IntroRoom` — 407 actors (386 loaded)
- **Laporan:** `laporan-2.tex` 34 hal, 462KB (xelatex exit 0, commit `65fd91e`)
- **Aturan file:** `535493_Hafidz Rizqullah Prasetya_PPG_Pertemuan 2.pdf`

## Screenshot — Done (4)
| # | File | Status | Keterangan |
|---|------|--------|------------|
| 1 | `ss-01-home-window.jpg` | ✅ | Home Panel UE5.8 — New Project biru, Recent Projects (MyProject2, Hafidz) |
| 2 | `ss-02-lvl-intro-room.jpg` | ✅ | Lvl_IntroRoom — Welcome UE5 overlay (RMB+WASD/QE, Play hijau) |
| 3 | `ss-03-outliner.jpg` | ✅ | Outliner — 407 actors, folder Bridge/Lighting/Room_Animation |
| 4 | `ss-04-details.jpg` | ✅ | Details SM_Cube12 — Loc 150,100,750, Scale 12,3,0.505, SM_Cube, MI_Intro_Colorway |

## Screenshot — Sisa (23 placeholder)
> Placeholder masih pakai `images/placeholder.png` di `laporan-2.tex`

### Persiapan (sisa 4)
- [ ] `ss-launcher` — Epic Launcher > Library (placeholder `fig:ss-launcher`)
- [ ] `ss-fixnow` — Warning .uproject > FIX NOW (fig:ss-fixnow)
- [ ] `ss-launch` — Launch 5.8.1 + MY PROJECTS (fig:ss-launch)
- [x] `ss-01-home-window` — Home Window + New Project (done)
- [ ] `ss-newproject` — GAMES > Intro To Unreal, nama HAFIDZ_535493_Intro (fig:ss-newproject)
- [ ] `ss-loading` — Layar loading project (fig:ss-loading)

### Eksplorasi Editor (sisa 4)
- [x] `ss-02` Welcome + Lvl_IntroRoom (done)
- [x] `ss-03` Outliner (done)
- [x] `ss-04` Details (done)
- [ ] `ss-05-viewport.jpg` — Viewport fly RMB+WASD (fig:ss-viewport)
- [ ] `ss-06-topbar.jpg` — Top Bar Save/Add/Blueprint/Sequencer/Play (fig:ss-topbar)
- [ ] `ss-07-play-stop.jpg` — Play/Escape/SHIFT+F1 (fig:ss-play)

### Manipulasi Objek & Material (8)
- [ ] `ss-08-transform.jpg` — Gizmo Move/Rotate/Scale (fig:ss-transform)
- [ ] `ss-09-grid.jpg` — Grid enable/disable (fig:ss-grid)
- [ ] `ss-10-add-object.jpg` — Add Objects (fig:ss-addobject)
- [ ] `ss-11-content-drawer.jpg` — CTRL+SPACE (fig:ss-contentdrawer)
- [ ] `ss-12-collision.jpg` — Collision di Details (fig:ss-collision)
- [ ] `ss-13-delete-outliner.jpg` — Hapus via Outliner (fig:ss-delete-outliner)
- [ ] `ss-14-material-prop.jpg` — Color/Metallic/Roughness (fig:ss-material-prop)
- [ ] `ss-15-hotswap.jpg` — Hot-swap material slot (fig:ss-hotswap)

### Pencahayaan, Fisika, Partikel, Logika (7)
- [ ] `ss-16-niagara.jpg` — Niagara particle (fig:ss-niagara)
- [ ] `ss-17-physics.jpg` — Physics property (fig:ss-physics)
- [ ] `ss-18-pointlight.jpg` — L+Left Click Point Light (fig:ss-pointlight)
- [ ] `ss-19-sequencer.jpg` — Right Click > Edit Sequencer (fig:ss-sequencer)
- [ ] `ss-20-blueprint.jpg` — Blueprint logic (fig:ss-blueprint)
- [ ] `ss-21-save.jpg` — Save CTRL+S (fig:ss-save)
- [ ] `ss-27-hasil-akhir.jpg` — Hasil akhir level (fig:hasil-akhir)

### Dasar Teori (placeholder 9)
- [ ] `fig:ue-overview`, `fig:one-engine`, `fig:launcher`, `fig:new-project`, `fig:outliner-details-viewport`, `fig:topbar-contentdrawer`, `fig:transform-collision`, `fig:material-physics`, `fig:sequencer-blueprint` — masih placeholder

## Cara Lanjut
1. Screenshot sesuai nama di atas (1 per 1)
2. Kirim ke Hermes — auto simpan `pertemuan-2/images/ss-XX-*.jpg` + ganti `placeholder.png` → `ss-XX` di `laporan-2.tex` + `latexmk -xelatex` + `git push`
3. Workflow sama kayak PPD (commit per screenshot)

## Git Log Terkait
```
952dc19 feat(PPG-2): laporan Navigate UE 5.8 - 32 hal
0d798de feat: ss-04 home window
3a20cc4 fix: rename ss-04 -> ss-01
af1b3fd feat: ss-02 Lvl_IntroRoom Hafidz
6f7c3e7 feat: ss-03 outliner 407 actors
65fd91e feat: ss-04 details SM_Cube12
```

## Build
- `latexmk -xelatex laporan-2.tex` → OK (34 pages, 472KB xdv → 462KB pdf)
- Artifak: `laporan-2.pdf` + 2 varian nama file tugas + `.aux/.log/.toc/.xdv` (gitignore)
