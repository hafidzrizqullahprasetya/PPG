# PRAK. PENGEMBANGAN GAME (PPG)  
## T.A. 2026/2027  
### PERTEMUAN 3  
## VARIABLE & CONDITION  

**Slogan/identitas visual:**  
**LOCALLY ROOTED, GLOBALLY RESPECTED**  
**ugm.ac.id**

### Penjelasan bagian gambar/visual pada slide pembuka
Slide pembuka berfungsi sebagai halaman judul materi praktikum ketiga. Pada bagian ini terdapat identitas mata kuliah **Praktik Pengembangan Game (PPG)**, tahun ajaran **2026/2027**, nomor pertemuan **Pertemuan 3**, serta topik utama yaitu **Variable & Condition** (Variabel dan Kondisional/Cabang Logika). Slogan **“Locally Rooted, Globally Respected”** dan alamat **ugm.ac.id** kembali ditampilkan sebagai identitas institusi Universitas Gadjah Mada.

---

## Basic Setup (Persiapan Project)

Instruksi pada slide:
- Buat projek baru dengan template **Third Person**. 
- Hal ini dilakukan karena pada template *IntroToUnreal* terdapat beberapa bug pada 3D model karakter yang mungkin akan mempersulit penyampaian materi Rigging/Retargeting.
- Ubah **Project Name** dengan format: **NAMA_NIU_PPG**

### Penjelasan bagian gambar/visual
Gambar pada bagian ini menampilkan jendela pemilihan template project baru di Unreal Engine (Unreal Project Browser). Pengguna diarahkan untuk memilih kategori **Games** dan memilih template **Third Person**. Pada bagian bawah jendela, terdapat kolom untuk menamai project yang harus diisi dengan format **NAMA_NIU_PPG**.

---

## Basic Setup (Membuat Folder Maps)

Instruksi pada slide:
- Untuk beberapa pertemuan PPG silahkan membuat folder baru bernama **“Maps”**.
- Klik kanan di content drawer > **Level**.

### Penjelasan bagian gambar/visual
Gambar pada bagian ini menampilkan antarmuka **Content Drawer** (atau Content Browser) di Unreal Engine. Visual menunjukkan proses klik kanan pada area kosong di dalam folder untuk membuat folder baru bernama "Maps". Di dalam folder Maps tersebut, pengguna kemudian membuat sebuah file **Level** baru (biasanya berekstensi `.umap`) melalui menu klik kanan.

---

## Basic Setup Lighting Level

Instruksi pada slide:
- Buka Level baru, klik **“Windows”** di atas kiri Unreal Engine, lalu klik **Env. Light Mixer**. 
- Pada window tersebut, klik semua opsi **“Create”**.

### Penjelasan bagian gambar/visual
Gambar pada bagian ini menampilkan menu bar di bagian atas layar Unreal Engine. Pengguna diarahkan untuk mengklik menu **Windows**, lalu mencari dan membuka panel **Env. Light Mixer** (Environmental Light Mixer). Di dalam jendela Light Mixer tersebut, terdapat beberapa opsi pencahayaan lingkungan (seperti Sky Light, Directional Light, Sky Atmosphere, Volumetric Cloud, dan Exponential Height Fog) yang masing-masing memiliki tombol **Create**. Pengguna diminta untuk mengklik semua tombol "Create" tersebut untuk menghasilkan setup pencahayaan dasar yang otomatis dan realistis di dalam level.

---

## Basic Setup (Landscape & Player Start)

Instruksi pada slide:
- Akses **Landscape Mode** lalu tambahkan landscape berukuran **7x7 Quads 8x8 Component** dengan **Section 1x1**, ganti gamemode ke **BP_FirstPersonGameMode**.
- Cari icon ini di sebelah kiri tombol play.
- Tambahkan **Player Start** ke Level.

### Penjelasan bagian gambar/visual
Gambar pada bagian ini menampilkan dua area utama. Pertama, mode **Landscape** (Mode Toolbar di sebelah kiri) beserta panel pengaturannya yang menunjukkan setting ukuran landscape (7x7 Quads, 8x8 Component, Section 1x1). Kedua, area di sebelah kiri tombol **Play** pada toolbar atas (Mode Toolbar), yang memperlihatkan icon **Player Start**. Pengguna diinstruksikan untuk memilih icon Player Start tersebut lalu mengkliknya di dalam Viewport untuk menentukan titik spawn (tempat munculnya) karakter pemain saat game dijalankan.

---

## Inisiasi BP (Blueprint)

Instruksi pada slide:
- Buat Folder untuk **Blueprints** yang akan digunakan sebagai tempat untuk membuat kode. 
- Untuk file ini memiliki prefix (nama depan) **BP_** dan tambahkan komponen **cube** agar Blueprint terlihat ketika diletakkan ke dalam map dengan menekan tombol **add** di kiri atas file Blueprint.
- Naming convention (prefix) untuk tiap file Unreal Engine ada di: dokumentasi epic games.

### Penjelasan bagian gambar/visual
Gambar pada bagian ini menampilkan proses pembuatan folder "Blueprints" di Content Drawer, serta pembuatan file Blueprint Class baru dengan awalan nama **BP_**. Di dalam editor Blueprint (Blueprint Editor), terlihat panel **Components** di sebelah kiri. Pengguna diarahkan untuk menekan tombol **+ Add** dan menambahkan komponen **Cube** (Static Mesh Component). Hal ini bertujuan agar Blueprint yang pada dasarnya kosong (hanya berupa titik pivot) memiliki wujud visual berupa kotak ketika di-spawn ke dalam level. Teks juga menyertakan tautan referensi ke dokumentasi Epic Games mengenai *Asset Naming Conventions*.

---

## Unreal Engine Basic Event

Instruksi pada slide:
- Untuk menjalankan kode pada UE5, diperlukan sebuah event seperti **Event BeginPlay** (berjalan sekali) dan **Event Tick** (berjalan tiap frame) yang terletak di tab **Event Graph** pada Blueprint.
- Drag & drop Blueprint sebelumnya ke dalam level dan akan muncul tulisan seperti pada screenshot di bawah ini.

### Penjelasan bagian gambar/visual
Gambar pada bagian ini menampilkan tab **Event Graph** di dalam Blueprint Editor. Terlihat dua node merah bawaan (default) yang sangat penting dalam pemrograman Blueprint, yaitu **Event BeginPlay** (dieksekusi satu kali saat game/objek dimulai) dan **Event Tick** (dieksekusi terus-menerus setiap frame). Selain itu, gambar juga menampilkan Viewport di mana Blueprint yang telah dibuat di-drag and drop ke dalam level, disertai dengan teks *debug* (Print String) yang muncul di layar sebagai bukti bahwa kode di dalam Event Graph berhasil dieksekusi.

---

## Variable

Instruksi pada slide:
- Terdapat banyak jenis variabel yang dapat digunakan di dalam Unreal Engine, seperti tipe variabel primitif dan beberapa tambahan seperti:
  - **Transform** yang berisi 3 variabel (location, rotation, scale)
  - **enum**
  - **user defined class**
  - dan lain-lain
- Tambahkan variabel **boolean** pada **BP_Box**!

### Penjelasan bagian gambar/visual
Gambar pada bagian ini menampilkan panel **My Blueprint** di mana pengguna dapat menambahkan variabel baru dengan mengklik ikon **(+)**. Terlihat daftar *drop-down* tipe data variabel yang tersedia di Unreal Engine, mulai dari tipe primitif (Boolean, Integer, Float, String, Vector) hingga tipe kompleks seperti **Transform** (yang secara otomatis menyimpan data Location, Rotation, dan Scale), **Enum**, dan **Class Reference**. Instruksi spesifik pada slide meminta mahasiswa untuk membuat variabel bertipe **Boolean** di dalam Blueprint yang bernama BP_Box.

---

## Struct Variable (Mirip Python List)

Penjelasan pada slide:
- **Struct Variable**
- Merupakan child dari blueprint yang dapat menampung variabel yang berbeda jenis (dan bebas) dalam satu array mirip dengan array python.
- *\*yang ini sekedar tahu dulu, akan dijelaskan lebih lengkap di pertemuan selanjutnya*

### Penjelasan bagian gambar/visual
Gambar pada bagian ini menampilkan struktur data **Structure (Struct)** di Unreal Engine. Visual ini memperlihatkan bahwa sebuah Struct dapat diisi dengan berbagai variabel yang memiliki tipe data berbeda-beda (misalnya satu variabel String, satu Integer, dan satu Boolean) yang dibungkus dalam satu wadah/kelompok. Slide ini memberikan catatan bahwa konsep ini mirip dengan List atau Dictionary kompleks di bahasa pemrograman Python, dan materinya hanya diperkenalkan sekilas untuk saat ini.

---

## BRANCH (CONDITION) - Menambahkan Node dan Navigasi BP

Instruksi pada slide:
- Untuk menambahkan node di dalam event graph dapat dilakukan dengan klik kanan dan ketik kata kunci seperti **“if”**, **“get <nama_variabel>”**, **“set <nama_variabel>”**, **“print string”**, dsb.
- Navigasi blueprint dilakukan dengan menahan klik kanan dan menggerakkan mouse.
- **Unreal Engine Branch**: Bersifat seperti *if* pada pseudo-code, diperlukan parameter boolean atau padanannya. Akan menjalankan kode hanya ketika kondisi terpenuhi atau sebaliknya (sesuai kebutuhan).

### Penjelasan bagian gambar/visual
Gambar pada bagian ini menampilkan area kanvas **Event Graph**. Visual menunjukkan proses klik kanan pada area kosong untuk memunculkan menu pencarian node, di mana pengguna bisa mengetik kata kunci seperti "Branch" (yang berfungsi sebagai logika *If*), "Get", "Set", atau "Print String". Visual juga memberikan petunjuk cara navigasi kanvas (panning) dengan menahan klik kanan mouse dan menggesernya. Node **Branch** itu sendiri diperlihatkan dengan satu pin eksekusi masuk, satu pin kondisi (Boolean), dan dua pin eksekusi keluar yaitu **True** dan **False**.

---

## BRANCH (CONDITION) - Implementasi Keyboard

Instruksi pada slide:
- Pada praktikum ini, contoh paling sederhananya adalah penambahan branch pada event tick yang akan menghasilkan print string yang berbeda dengan kondisi boolean sesuai dengan variabel sebelumnya.
- Variabel menjadi true/false apabila kita menekan tombol **“R”** (ketik **“Keyboard R”**).
- Cari fungsi ini dengan keyword “keyboard”.
- Kalo ini **“not boolean”**.

### Penjelasan bagian gambar/visual
Gambar pada bagian ini menampilkan susunan *node graph* (untaian logika) di Event Graph. Terlihat **Event Tick** dihubungkan ke logika penekanan tombol menggunakan node **Keyboard R** (dari kategori Input Events). Hasil dari penekanan tombol tersebut (Pressed/Released) digunakan untuk mengubah nilai variabel Boolean (menggunakan node **Set**). Variabel Boolean tersebut kemudian dibaca (menggunakan node **Get**) dan dimasukkan ke dalam pin kondisi pada node **Branch**. Terdapat juga node **Not Boolean** untuk membalik nilai logika. Dari pin True dan False pada Branch, kabel eksekusi dihubungkan ke dua node **Print String** yang berbeda untuk mencetak teks yang berbeda di layar tergantung pada apakah tombol R sedang ditekan atau tidak.

---

## Kondisi Lainnya (SWITCH, DO ONCE, FLIP FLOP, GATE)

Teks pada slide (ditandai sebagai opsional/mandiri):
- **SWITCH (CONDITION)** \*opsional aja (dicari mandiri/ gausah di pertemuan ini kalo waktu gak cukup)
- **DO ONCE (CONDITION)** \*opsional aja (dicari mandiri/ gausah di pertemuan ini kalo waktu gak cukup)
- **FLIP FLOP (CONDITION)** \*opsional aja (dicari mandiri/ gausah di pertemuan ini kalo waktu gak cukup)
- **GATE (CONDITION)** \*opsional aja (dicari mandiri/ gausah di pertemuan ini kalo waktu gak cukup)

### Penjelasan bagian gambar/visual
Gambar pada bagian ini menampilkan ikon atau bentuk visual dari berbagai node *Flow Control* (pengontrol alur logika) lainnya di Unreal Engine Blueprint. 
- **Switch**: Node dengan satu input dan banyak output (Case 0, Case 1, dst) untuk mencocokkan nilai tertentu.
- **Do Once**: Node yang hanya akan mengeksekusi alur satu kali saja hingga di-*reset*.
- **Flip Flop**: Node dengan dua output (A dan B) yang akan bergantian aktif setiap kali dieksekusi.
- **Gate**: Node yang berfungsi seperti pintu gerbang, yang bisa dibuka (Open), ditutup (Close), atau di-*toggle* untuk mengontrol apakah alur eksekusi boleh lewat atau tidak.

---

## Tugas Laporan Praktikum (Aplikasi If/Else)

Instruksi pada slide:
- Dari yang sudah dijelaskan, kita bisa mengaplikasikan if/else untuk mengubah scale/ rotasi/ lokasi mesh secara real time (bukan best practice, hanya untuk keperluan praktikum saja) dengan mengubah kodingan pada event tick BP_Box yang sebelumnya sudah ditambahkan variabel float dengan nama **scale target** yang memiliki default value **0.1**.
- Pada bagian ini dari slide sebelumnya, konversikan return value scale ke float pada bagian pengurangan dengan klik kanan pada pin konektor operasi bilangan untuk mendapatkan hasil seperti pada gambar di bawah.

### Penjelasan bagian gambar/visual
Gambar pada bagian ini menampilkan susunan node Blueprint untuk tugas praktikum yang lebih kompleks. Terlihat **Event Tick** dihubungkan ke node matematika (seperti pengurangan atau *Lerp*) untuk mengubah nilai **Scale** mesh secara real-time menuju *scale target* 0.1. Slide ini memberikan instruksi visual yang sangat spesifik: pengguna harus **klik kanan pada pin konektor** (kabel penghubung pada node operasi bilangan) untuk melakukan **konversi tipe data** (misalnya mengubah Vector menjadi Float, atau sebaliknya) agar operasi matematika tidak error (merah) dan dapat berjalan dengan benar. Catatan "bukan best practice" diberikan karena mengubah transformasi di dalam Event Tick tanpa *Delta Time* atau *Timeline* bisa menyebabkan performa yang tidak optimal atau pergerakan yang tidak konsisten di berbagai frame rate.

---

## FORMAT TUGAS

Struktur laporan mengikuti format laporan praktikum pada kelas lainnya, dengan ketentuan minimal memuat:

### 1. Dokumentasi Praktikum
a. Cantumkan screenshot setiap langkah penting pada sesi praktikum ini.  
b. Berikan keterangan singkat mengenai apa yang dilakukan pada screenshot.

### 2. Hasil Akhir
Bagian ini menampilkan hasil akhir dari praktikum yang telah dilakukan.

### 3. References
Bagian ini memuat referensi yang digunakan dalam pengerjaan laporan atau praktikum.

### Penjelasan bagian gambar/visual
Bagian format tugas ini ditampilkan dalam bentuk poin-poin struktur laporan. Intinya, laporan praktikum harus memiliki dokumentasi langkah-langkah kerja berupa screenshot (terutama susunan node Blueprint), keterangan singkat untuk setiap screenshot, hasil akhir (misalnya video atau gif objek yang berubah skala saat tombol R ditekan), serta daftar referensi.

---

## ATURAN TUGAS

Slide ini berisi aturan pengumpulan tugas.

### LINK PENGUMPULAN
Tautan pengumpulan tugas yang tertera pada slide adalah:
> https://docs.google.com/forms/d/e/1FAIpQLSe-Z5kJV4kzWsSe3-xUhf_gOr3HfLnMlBW0hxA6ubw0JKG83w/viewform?usp=dialog

### Format nama file
Format nama file yang digunakan:
> **NIU_Nama Lengkap_PPG_Pertemuan X**

Contoh (sesuai teks di slide):
> **123456_Sugeng Semar_PPG_Pertemuan 2** *(Catatan: Meskipun ini materi Pertemuan 3, contoh format yang tertulis di slide asli menggunakan angka 2, namun mahasiswa harus menyesuaikan dengan pertemuan saat ini yaitu Pertemuan 3).*

### Format file yang diterima
File tugas harus berformat:
> **PDF**

Batas ukuran file:
> Maksimal **10 MB**

Jika file melebihi batas tersebut, maka:
> Silakan compress.

### Deadline
Pada bagian slide tertulis:
> **Deadline:**
*(Namun berdasarkan teks yang tersedia, nilai/waktu deadline belum/tidak tercantum secara eksplisit).*

### Penjelasan bagian gambar/visual
Bagian aturan tugas menampilkan tautan Google Form, ikon format PDF, dan peringatan batas ukuran file 10 MB. Visual ini bertujuan memastikan mahasiswa mengumpulkan tugas dengan format yang benar, ukuran file tidak melebihi batas, dan menggunakan nama file sesuai ketentuan agar mudah di-rekap oleh asisten praktisi.

---

## References

Referensi yang tercantum pada slide adalah:
1. https://dev.epicgames.com/documentation/unreal-engine/recommended-asset-naming-conventions-in-unreal-engine-projects

### Penjelasan bagian gambar/visual
Bagian referensi berisi tautan ke dokumentasi resmi Epic Games. Referensi ini sangat penting karena mengarahkan mahasiswa pada panduan standar industri mengenai **Recommended Asset Naming Conventions** (Konvensi Penamaan Aset yang Disarankan), seperti penggunaan prefix `BP_` untuk Blueprint, `M_` untuk Material, `T_` untuk Texture, dan lain-lain, agar project game tetap rapi dan mudah dikelola.

---

## Penutup

Slide penutup menampilkan:

> **LOCALLY ROOTED, GLOBALLY RESPECTED**  
> **ugm.ac.id**  
> **Sekian Matur thank you**