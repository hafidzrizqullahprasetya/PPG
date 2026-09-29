# PRAK. PENGEMBANGAN GAME (PPG)
### T.A. 2026/2027 — PERTEMUAN 7
## ASSET FAB DAN WIDGET BLUEPRINT (UI)

*Locally Rooted, Globally Respected — Universitas Gadjah Mada*

---

## Learning Objectives

Pada pertemuan ini, praktikan akan mempelajari dan mengimplementasikan:
1. **Asset FAB Import**: Melakukan eksplorasi dan proses import aset dari marketplace FAB ke dalam proyek Unreal Engine 5.8.
2. **Landscape Material & Layer Info**: Mengimplementasikan aset material bentang alam multi-layer (`MI_landscape_pro_v2_inst`) dan mengelola data kontainer *Layer Info*.
3. **Foliage Implementation**: Mengimplementasikan aset vegetasi lingkungan (*foliage*) menggunakan metode *Manual Placement* dan *Foliage Mode*.
4. **Widget Blueprint (UMG)**: Merancang komponen antarmuka pengguna (*User Interface* / UI) menggunakan Widget Blueprint, meliputi pembuatan progress bar status kesehatan (`WBP_Health`) dan kanvas HUD utama (`WBP_HUD`).
5. **UI Animation**: Membuat animasi visual dinamis (*shake/jiggle translation*) berdurasi 0,25 detik pada elemen UI menggunakan *Sequencer Animation*.
6. **Decoupled Architecture with Blueprint Interface**: Menghubungkan sistem UI dan gameplay logic secara modular tanpa hard-casting melalui implementasi `BPI_HUD` dan `BPI_Widget`.
7. **Game Instance & Controller Integration**: Menginisialisasi UI pada `BP_ThirdPersonPlayerController`, menyimpan referensi widget pada `BP_GameInstance`, dan memperbarui nilai *HealthBar* saat karakter menerima luka (`Event TakeDamage` pada `BP_ThirdPersonCharacter`).

---

## Prerequisites

- **Basis Proyek:** Proyek praktikum pertemuan sebelumnya (`HAFIDZ_535493_PPG`).
- **Sistem Dasar:** Proyek Pertemuan 5 (*Game Instance & Save Game*) dan Pertemuan 4 (*Interface, Component & Collision*).
- **Integrasi Sistem:** Komponen kesehatan (`BPC_Health`) dan penanganan tabrakan/kerusakan (`BPI_Overlap` / `TakeDamage`) yang telah terpasang pada karakter utama.

---

## Bagian 1: FAB by Epic Games

### 1. Mengenal FAB Marketplace
FAB merupakan marketplace digital terpadu dari Epic Games untuk mencari, membeli, dan menjual aset 3D. Jenis aset yang ditawarkan mencakup:
- Model 3D statis dan skeletal
- Sistem game siap pakai
- Plugin dan ekstensi engine
- Tekstur dan Material fisik (PBR)
- Lingkungan (*Environment*) dan partikel visual (VFX)

Aset yang tersedia di Fab bersifat agnostik dan dapat diintegrasikan ke berbagai engine kreasi konten:
- **Unreal Engine & UEFN (Unreal Editor for Fortnite)**
- **Unity**
- **Blender**
- **Autodesk Maya & 3ds Max**
- **Cinema 4D**
- **Adobe Substance 3D**

### 2. Klaim Monthly Free Asset
Setiap bulan, Fab membagikan aset berbayar berkualitas tinggi secara gratis (*limited-time free*). Aset tersebut dapat diklaim permanen tanpa perlu memasukkan informasi kartu kredit melalui tautan:
`https://www.fab.com/limited-time-free`

### 3. Browsing & Menambahkan Aset "Landscape Pro 2.0"
1. Buka aplikasi **Epic Games Launcher**, lalu klik tab **Fab**.
2. Ketikkan kata kunci `"Landscape Pro 2.0"` pada kolom pencarian.
3. Kembali ke editor **Unreal Engine**, buka tab **Library**, lakukan penyegaran (*refresh*) pada bagian **Fab Library**.
4. Cari aset **Landscape Pro 2.0**, kemudian klik tombol **Add To Project**.

> **Catatan Kompatibilitas Versi:**
> Aset *Landscape Pro 2.0* dirilis dengan dukungan resmi hingga UE 5.5, sedangkan proyek praktikum berjalan pada **Unreal Engine 5.8**.
> Untuk menggunakannya pada UE 5.8:
> - Klik opsi **Show all projects**.
> - Pilih proyek praktikum (`HAFIDZ_535493_PPG`).
> - Atur dropdown **Select Version** ke **5.5**.
> - Engine akan secara otomatis mengimpor dan mengonversi aset ke proyek UE 5.8.

### 4. Proses Unduhan dan Inspeksi Aset
- Disarankan menutup jendela proyek Unreal Engine selama proses pengunduhan berlangsung untuk menjaga integritas file.
- Indikator keberhasilan: muncul keterangan **Cache Size** pada launcher, menandakan file aset telah terpasang ke dalam proyek.
- Buka kembali proyek di Unreal Engine 5.8, akses **Content Drawer**, dan arahkan direktori ke:
  `Content > STF > Pack03-LandscapePro > Environment > Foliage`
- Aktifkan filter **Static Mesh** untuk melihat seluruh aset vegetasi/pepohonan yang tersedia.
- Buka salah satu aset foliage (klik dua kali) untuk memverifikasi model 3D dan shader materialnya.

---

## Bagian 2: Implementasi Landscape Material & Foliage

### 1. Penerapan Material Multi-Layer pada Landscape
1. Buka level praktikum yang telah dibuat pada pertemuan sebelumnya: **`LV_Praktikum`**.
2. Pilih aktor **Landscape** di panel Outliner atau langsung pada viewport.
3. Pada panel **Details**, cari kategori **Landscape** dan ubah properti **Landscape Material** menjadi:
   `MI_landscape_pro_v2_inst`

### 2. Konfigurasi Material Layer & Layer Info
1. Ubah mode interaksi engine ke **Landscape Mode** (tekan tombol pintas **Shift + 2**).
2. Masuk ke tab **Paint**.
3. Klik ikon pembuatan layer material otomatis agar engine mengekstrak data layer dari `MI_landscape_pro_v2_inst`.
4. Pada daftar layer yang muncul (misalnya layer tanah, rumput, dan genangan air):
   - Klik dropdown pada layer bertuliskan status `None`.
   - Pilih aset **Layer Info** yang sesuai dari daftar dropdown (pilih opsi teratas).
   
> **Fungsi Layer Info:**
> *Layer Info* merupakan kontainer data khusus yang menyimpan instruksi perilaku (*paint behavior*), data bobot (*weight blending*), dan respons interaksi antara layer material dengan permukaan tanah bentang alam.

### 3. Melakukan Painting pada Bentang Alam
- Pilih salah satu layer pada daftar (misalnya `Grass` atau `Ground`).
- Lakukan pengecatan langsung pada viewport menggunakan kuas (*brush*).
- Untuk menciptakan variasi visual lingkungan, beralihlah ke layer lain seperti `Puddle` (genangan air) atau batuan sebelum mengaplikasikan sapuan kuas berikutnya.

### 4. Implementasi Foliage (Vegetasi Lingkungan)
Terdapat dua metode utama penempatan foliage di atas bentang alam:

#### Metode 1: Penempatan Manual (Manual Placement)
- Buka folder `STF > Pack03-LandscapePro > Environment > Foliage`.
- Pilih model pohon/semak (*Static Mesh*).
- Lakukan operasi *drag and drop* aset langsung ke atas permukaan landscape di viewport. Metode ini cocok untuk penataan objek pohon heroik (*hero assets*) dengan presisi tinggi.

#### Metode 2: Foliage Mode Painting
- Beralih ke **Foliage Mode** (tekan tombol pintas **Shift + 3**).
- Pada Content Drawer, pasang filter **Static Mesh Foliage**.
- Seleksi seluruh aset foliage yang diinginkan, lalu tarik (*drag and drop*) ke dalam area kotak **"Drop Foliage Here"** pada panel Foliage.
- Centang jenis pohon/semak yang ingin diaktifkan, atur kerapatan (*density*), lalu lakukan sapuan kuas (*paint*) di atas landscape untuk menempatkan vegetasi secara masif dan tersebar alami.

---

## Bagian 3: Arsitektur User Interface (Widget Blueprint)

### 1. Pembuatan Aset Widget Blueprint
1. Buat folder baru bernama **`Widget`** di direktori utama: `Content/Widget`.
2. Klik tombol **Add > User Interface > Widget Blueprint**.
3. Pada jendela pemilihan root class, pilih **User Widget**.
4. Beri nama berkas: **`WBP_HUD`** (berfungsi sebagai container layar HUD utama).
5. Buat satu Widget Blueprint lagi bertipe User Widget dengan nama: **`WBP_Health`** (berfungsi khusus menampilkan status darah pemain).

### 2. Perancangan Komponen pada `WBP_Health`
1. Buka editor `WBP_Health`.
2. Pada panel **Palette**, cari komponen **Progress Bar** (di bawah kategori *Common*).
3. Seret (*drag and drop*) komponen Progress Bar ke area kanvas/hierarchy.
4. Ganti nama widget tersebut menjadi **`HealthBar`** pada panel Hierarchy.
5. Konfigurasi panel **Details**:
   - **Appearance > Fill Color and Opacity:** Atur warna batang bar menjadi **Hijau terang** (RGB).
   - **Progress > Percent:** Atur nilai awal menjadi **`1.0`** (100% penuh).

### 3. Pembuatan Animasi UI (`onUpdateHealthAnimation`)
Untuk memberikan respons visual saat darah karakter berkurang:
1. Pada sudut kiri bawah editor, buka panel **Animations**, klik tombol **`+ Animation`**, dan beri nama: **`onUpdateHealthAnimation`**.
2. Pilih animasi tersebut, lalu klik tombol **`+ Track`** dan tambahkan track untuk widget **`HealthBar`**.
3. Di samping nama `HealthBar`, tambahkan sub-track **`Transform`** (fokus pada parameter **Translation X** dan **Translation Y**).
4. Atur durasi linimasa animasi menjadi **`0.25` detik** pada framerate **20 fps**.
5. Tambahkan keyframe perubahan nilai translasi (X dan Y) secara berfluktuasi antara detik `0.00` hingga `0.25` detik untuk menghasilkan efek getar visual (*shake/jiggle effect*).

### 4. Perancangan Layout pada `WBP_HUD`
1. Buka editor `WBP_HUD`.
2. Dari panel **Palette**, cari dan tambahkan komponen **`Canvas Panel`** ke dalam hierarki `[WBP_HUD]`.
3. Dari panel Palette atau Content Drawer, tarik widget **`WBP_Health`** ke dalam `Canvas Panel`.
4. Posisikan `WBP_Health` pada area **kiri atas layar** (*top-left corner*) dengan penjangkaran (*anchors*) yang sesuai dan margin yang rapi dari batas layar aman (*safe zone*).

---

## Bagian 4: Pola Desain Blueprint Interface (BPI)

Untuk menghindari kopling ketat (*tight coupling*) dan pemanggilan *hard-cast* yang membebani komputasi, komunikasi antar-sistem dihubungkan menggunakan dua berkas *Blueprint Interface*:

### 1. Pembuatan `BPI_HUD`
- **Lokasi:** `Content/Interfaces` (atau `Content/Widget`)
- **Fungsi:** `UpdateHealthValue`
- **Parameter Input:**
  - `CurrentHealth` (Tipe: `Float`)
  - `MaxHealth` (Tipe: `Float`)
- **Parameter Output:** *None* (kosong)

### 2. Pembuatan `BPI_Widget`
- **Lokasi:** `Content/Interfaces` (atau `Content/Widget`)
- **Fungsi 1:** `SetHUDWidget`
  - Input: `HUD` (Tipe: `User Widget` - Object Reference)
  - Output: *None*
- **Fungsi 2:** `GetHUDWidget`
  - Input: *None*
  - Output: `HUD` (Tipe: `User Widget` - Object Reference)

---

## Bagian 5: Integrasi Logika Program dan Alur Eksekusi

### 1. Implementasi `BPI_HUD` pada `WBP_HUD`
1. Buka `WBP_HUD`, beralih ke mode **Graph** (sudut kanan atas).
2. Buka **Class Settings**, lalu pada bagian **Interfaces > Implemented Interfaces**, tambahkan **`BPI_HUD`**.
3. Pada panel *My Blueprint*, di bawah kelompok *Interfaces*, klik dua kali fungsi **`UpdateHealthValue`** untuk membukanya di Event Graph.
4. Rangkaikan node berikut:
   - Dari pin eksekusi **`Event UpdateHealthValue`**, hubungkan ke node **`Play Animation`**.
   - Pada node `Play Animation`: hubungkan getter variabel `WBP_Health` -> getter `On Update Health Animation` ke pin `In Animation`.
   - Lanjutkan garis eksekusi putih ke node **`Set Percent`** milik komponen `HealthBar` (diakses melalui referensi `WBP_Health`).
   - Lakukan operasi pembagian: ambil pin `CurrentHealth`, bagi (`÷`) dengan `MaxHealth`, lalu sambungkan hasilnya ke pin `In Percent` pada node `Set Percent`.

### 2. Implementasi `BPI_Widget` pada `BP_GameInstance`
1. Buka `BP_GameInstance`, masuk ke **Class Settings**, lalu tambahkan interface **`BPI_Widget`**.
2. Buat variabel baru:
   - **Nama Variabel:** `AddedWidget`
   - **Tipe Variabel:** `User Widget` (Object Reference)
3. Implementasi fungsi **`GetHUDWidget`**:
   - Rangkai pin eksekusi langsung ke `Return Node`.
   - Sambungkan getter variabel `AddedWidget` ke pin input output `HUD` pada `Return Node`.
4. Implementasi event **`Event SetHUDWidget`**:
   - Tarik pin eksekusi ke node **`SET AddedWidget`**.
   - Hubungkan pin input `HUD` dari event ke pin data input `AddedWidget` pada setter.

### 3. Inisialisasi Tampilan Layar pada `BP_ThirdPersonPlayerController`
1. Buka `BP_ThirdPersonPlayerController` pada Event Graph awal (setelah alur `Add Mapping Context`).
2. Buat node **`Create Widget`**:
   - Class: **`WBP_HUD`**
   - Owning Player: hubungkan ke node **`Self`**.
3. Panggil node **`Get Game Instance`**, lalu tarik kabel untuk memanggil fungsi antarmuka **`Set HUDWidget (Target: BPI_Widget)`**.
   - Sambungkan nilai *Return Value* dari `Create Widget` ke pin input `HUD`.
4. Dari pin *Return Value* widget tersebut, panggil node **`Add to Player Screen`** agar UI dirender langsung ke layar pemain saat permainan dimulai.

### 4. Pembaruan Status Darah pada `BP_ThirdPersonCharacter`
1. Buka `BP_ThirdPersonCharacter`, temukan logika **`Event TakeDamage`** (dari pertemuan sebelumnya).
2. Setelah node **`Modify Health`** pada komponen `BPC_Health`:
   - Panggil node **`Get Game Instance`**.
   - Tarik ke fungsi interface **`Get HUDWidget (Target: BPI_Widget)`**.
   - Dari pin output `HUD`, panggil pesan interface **`Update Health Value (Target: BPI_HUD)`**.
   - Ambil nilai dari getter `BPC_Health`: sambungkan variabel `CurrentHealth` dan `MaxHealth` ke parameter fungsi `Update Health Value`.

---

## Ketentuan dan Format Laporan

### Format Dokumen
- Laporan disusun menggunakan template resmi LaTeX UGM (kompilasi XeLaTeX).
- Memuat halaman judul, daftar isi, tujuan praktikum, dasar teori komprehensif, langkah dokumentasi praktikum dengan screenshot asli, kesimpulan, dan daftar pustaka aktif.

### Format Nama File
- `NIU_Nama Lengkap_PPG_Pertemuan 7.pdf`
  *Contoh:* `535493_Hafidz Rizqullah Prasetya_PPG_Pertemuan 7.pdf`
- Batas ukuran file: Maksimal **10 MB**.

### Tautan Pengumpulan
`https://docs.google.com/forms/d/e/1FAIpQLSd6MD62ApUjhCbB8MwM83nrY5EmAqYPB864Du5vKI36D3IseA/viewform?usp=publish-editor`

---

## Referensi Pembelajaran
1. Fab by Epic Games: *About Fab Marketplace* (`https://www.fab.com/o/about`).
2. Epic Games Blog: *Fab Content Marketplace Launch & Publishing Portal*.
3. Unreal Engine Documentation: *UMG UI Designer & Widget Blueprints*.
4. Unreal Engine Documentation: *Blueprint Interfaces & Cross-Blueprint Communication*.
5. Unreal Engine Documentation: *Landscape Materials and Foliage Tooling*.
