# PRAK. PENGEMBANGAN GAME (PPG)
### T.A. 2026/2027 — PERTEMUAN 6
## LANDSCAPE, RIG, RETARGET, DAN ANIMATION

*Locally Rooted, Globally Respected — Universitas Gadjah Mada*

> **[Gambar Sampul]** Slide judul dengan logo UGM di kanan atas, latar putih dengan sketsa garis bangunan bergaya Balairung UGM di sisi kanan, serta bilah warna biru tua dan kuning di sisi kiri bertuliskan identitas mata kuliah Praktikum Pengembangan Game (PPG) T.A. 2026/2027 Pertemuan 6: "Landscape, Rig, Retarget, dan Animation" (kredit visual: UNAmedia).

---

## Learning Objectives

Pada pertemuan ini, praktikan akan mempelajari:
1. **Landscaping**: Pembuatan dan manipulasi bentang alam (*landscape*), termasuk teknik pembentukan kontur (*sculpting*) dan penerapan material.
2. **Lighting**: Penataan pencahayaan dasar dan atmosfer level menggunakan *Environment Light Mixer*.
3. **Introduction to Rig**: Pemahaman konsep dasar *rigging*, komparasi skeleton Mixamo vs Unreal Engine Mannequin (Manny & Quinn), serta urgensi *retargeting*.
4. **Implementasi Custom Character Mixamo**: Alur pengunduhan aset dari Mixamo, impor FBX ke Unreal Engine, hingga proses *retargeting* animasi.
5. **Animation Montage**: Konsep *montage*, pembuatan *Anim Montage*, dan penerapannya pada karakter gameplay melalui interaksi tombol keyboard.

---

## Landscaping

> **[Gambar Sampul Seksi]** Slide pembuka bagian "LANDSCAPING" dengan latar belakang bertema lingkungan grafis game 3D.

---

**Level**

Merupakan "panggung/stage" tempat semua objek game ditempatkan. *Landscape*, pohon, pencahayaan (*lighting*), karakter, dan *trigger* semuanya hidup dan berinteraksi di dalam level. 

Secara teknis di dalam Unreal Engine, sebuah level disimpan sebagai file berekstensi `.umap`.

> **[Gambar 1]** Ilustrasi analogi panggung pertunjukan teater (*stage*) di mana seluruh elemen game (lingkungan, pencahayaan, prop, dan karakter) berinteraksi bersama (kredit visual: Tinkr Academy).

---

**Membuat Level Baru**

Untuk membuat Level baru pada Unreal Engine 5, gunakan salah satu cara berikut:
1. Dari menu bar utama di bagian atas, buka **File**, lalu pilih **New Level**.
2. Klik kanan pada area kosong di **Content Browser** (atau **Content Drawer**). Kemudian, di bawah kategori **Create Basic Asset**, pilih **Level**.
3. Gunakan *shortcut* keyboard **Ctrl + N**.

---

**Tipe Level UE5**

Unreal Engine 5 menyediakan beberapa opsi *template* level dasar:
- **Open World**: Level yang sudah mengaktifkan fitur *World Partition* secara otomatis.
- **Basic**: Level standar dengan aset-aset dasar bawaan sederhana, seperti lantai *plane*, sistem *lighting*, *atmosphere*, dan *exponential height fog*.
- **Empty Level**: Level kosongan tanpa objek maupun pencahayaan apa pun.

Pilih **Empty Level**, lalu klik tombol **Create**!

---

**Alasan Menggunakan Empty Level (Tanpa World Partition)**

Kenapa praktikum ini menggunakan **Empty Level** dan tidak menggunakan *template* **Open World (World Partition)**?
1. **Skala Kebutuhan**: Level yang akan dibuat untuk kebutuhan praktikum masih berskala kecil (*small-scale prototype*), sehingga sistem *World Partition* belum diperlukan.
2. **Stabilitas Kelas**: Sistem *landscape* dan *material* pada *World Partition* memiliki alur kerja yang cukup berbeda dan cenderung kurang stabil jika dipraktikkan langsung di lingkungan kelas praktikum.

*Catatan Teknis Perbedaan:*
- Jika mencoba level **Open World (World Partition)**, *landscape* yang dihasilkan berupa **"Instanced Landscape"**.
- Sebaliknya, pada **Basic Level** atau **Empty Level**, saat membuat *landscape* baru, hanya akan ada satu objek **"Landscape"** murni (bukan *instanced landscape*).
- Objek *Instanced Landscape* tersebut berpotensi menimbulkan masalah kompatibilitas dan kendala teknis pada materi pertemuan-pertemuan praktikum berikutnya.
- Jika menggunakan *template* Open World, *World Partition* aktif secara otomatis. Namun jika menggunakan Basic/Empty Level, *World Partition* sebenarnya dapat diaktifkan manual lewat panel **World Settings**, meskipun biasanya rentan memicu kerusakan pengaturan (*something breaks*).

---

**Menyimpan Level**

Simpan level yang baru dibuat dengan menekan tombol **Ctrl + S** pada keyboard:
1. Beri nama file level: **"LV_Praktikum"**.
2. Tentukan lokasi penyimpanan di dalam folder **ThirdPerson** (atau folder *Maps* yang telah disiapkan).
3. Klik tombol **Save** untuk menyimpan file `.umap`.

---

**Lighting & Atmosphere**

Setelah membuat *Empty Level*, tampilan *Viewport* masih gelap total (hitam pekat) karena level belum memiliki sumber pencahayaan.

Untuk mengatur tata cahaya dengan cepat:
1. Buka menu bar atas: **Window > Env. Light Mixer**.
2. Pada jendela dialog *Environment Light Mixer*, klik **semua tombol "Create"** yang tersedia:
   - *Create Directional Light* (cahaya matahari langsung)
   - *Create Sky Light* (pencahayaan ambient langit)
   - *Create Sky Atmosphere* (lapisan atmosfer dan langit)
   - *Create Volumetric Cloud* (awan 3D volumetrik)
   - *Create Exponential Height Fog* (kabut kedalaman level)

Dengan cara ini, semua komponen pencahayaan dasar langsung aktif dan siap digunakan secara instan tanpa proses konfigurasi manual yang rumit.

> **[Gambar 2]** Tampilan jendela *Environment Light Mixer* pada Unreal Engine 5 yang menampilkan status kelima komponen pencahayaan lingkungan beserta tombol "Create" pada masing-masing komponen.

---

**Membuat Landscape Baru**

Untuk membuat permukaan bentang alam (*landscape*):
1. Masuk ke **Landscape Mode** dengan memilih ikon Landscape pada *Toolbar Mode* di kiri atas (atau tekan shortcut **Shift + 2**).
2. Pada panel pengaturan *Manage / New Landscape*:
   - Ubah parameter **Section Size** menjadi **"15x15 Quads"**.
   - Biarkan nilai pengaturan lainnya tetap pada nilai *default*.
3. Klik tombol **Create** di bagian bawah panel.

---

**Sculpting Landscape**

Setelah grid *landscape* terbuat, lakukan manipulasi permukaan tanah menggunakan *tools sculpting* yang tersedia pada mode Landscape:
- **Sculpt**: Menambah atau menaikkan elevasi kontur permukaan tanah.
- **Erase**: Menghapus atau menurunkan kembali elevasi yang telah dinaikkan.
- **Smooth**: Menghaluskan lekukan atau area permukaan tanah yang terlalu tajam/bergerigi.
- **Flatten**: Meratakan ketinggian permukaan tanah berdasarkan titik elevasi acuan.
- **Ramp**: Membuat jalan landai/tanjakan miring yang menghubungkan dua titik ketinggian berbeda.
- **Erosion & Hydro**: Mensimulasikan efek pengikisan tanah secara alami akibat cuaca dan aliran air.
- **Noise**: Memberikan variasi acak (tekstur bergelombang kasar/tidak rata) pada permukaan tanah.

Silakan bereksperimen dengan kombinasi *brush* dan *tools* tersebut untuk membentuk kontur terrain.

---

**Mengganti Material Landscape**

Agar permukaan *landscape* tidak hanya berupa grid kosong berwarna abu-abu:
1. Kembali ke **Selection Mode** (klik ikon kursor di toolbar atau tekan shortcut **Shift + 1**).
2. Klik objek **Landscape** yang ada di Viewport atau melalui panel *Outliner*.
3. Pada panel **Details** di sisi kanan, cari bagian properti **Landscape Material**.
4. Ganti slot material tersebut dengan material bawaan engine: **"CausticsBaseMesh"**.

---

**Challenge: Custom Landscape Material**

Tantangan latihan mandiri:
1. Carilah sebuah gambar tekstur permukaan tanah bebas dari internet (misalnya tekstur *ground*, *grass*, *rock*, atau tanah/batu).
2. Buat material baru menggunakan tekstur tersebut, lalu pasangkan ke slot *Landscape Material* pada *landscape* yang telah dibuat.
3. *Catatan:* Untuk latihan ini cukup gunakan satu tekstur sederhana. Teknik pengecatan multi-tekstur (*Landscape Material Painting* dengan *Layer Blend*) akan dipelajari lebih mendalam pada **Pertemuan 7**.

---

## Introduction to Rig

> **[Gambar Sampul Seksi]** Slide pembuka bagian "INTRODUCTION TO RIG" yang menampilkan anatomi kerangka digital karakter 3D.

---

**Rigging**

*Rigging* adalah proses memasang dan menghubungkan kerangka tulang (*skeleton*) ke dalam model 3D (*mesh*) supaya model tersebut dapat digerakkan dan dianimasikan.

Tanpa *rig*, sebuah model 3D hanyalah patung kaku (*Static Mesh*). Namun dengan adanya *rig*, model tersebut berubah menjadi *Skeletal Mesh* yang dapat berjalan, berlari, melompat, hingga mengekspresikan emosi.

> **[Gambar 3]** Ilustrasi anatomi skeletal mesh karakter 3D yang memperlihatkan struktur sendi dan tulang (*bones/joints*) di dalam tubuh karakter (kredit visual: Epic Games).

---

**Mixamo**

Platform berbasis web dari Adobe ([mixamo.com](https://www.mixamo.com/)) yang menyediakan ratusan karakter 3D dan pustaka animasi siap pakai secara gratis dan cepat untuk kebutuhan *prototyping*.

*Kelemahan:* Mixamo memiliki sistem *rigging* yang sangat sederhana dan tidak menyertakan rig pada area wajah (*facial rig*), sehingga karakter tidak memiliki kontrol ekspresi muka atau *lip-sync*.

---

**MetaHuman**

Karakter manusia digital fotorealistik dengan standar kualitas produksi film bioskop (*film-grade production*). Struktur *rig* tubuh dan wajahnya sangat kompleks, mencakup detail artikulasi ekspresi mikro, *lip-sync*, pergerakan bola mata, gigi, hingga simulasi helai rambut (*strand-based hair*).

> **[Gambar 4]** Contoh visual karakter digital MetaHuman dengan fidelitas tinggi pada detail kulit dan ekspresi wajah (kredit visual: LodhongKrupuk Interactive & purplepuppet).

*Catatan: MetaHuman tidak dipraktikkan dalam sesi kelas, materi ini hanya sebagai wawasan pengenalan (introduction).*

---

**Ekosistem MetaHuman**

Beberapa teknologi utama dalam ekosistem MetaHuman:
- **MetaHuman Creator**: Aplikasi berbasis *cloud/browser* untuk merancang model 3D manusia digital secara parametrik tanpa perlu *sculpting* manual dari nol.
- **Mesh to MetaHuman**: Fitur untuk mengubah data hasil pemindaian (*3D scan*) wajah asli menjadi karakter MetaHuman beranimasi lengkap di Unreal Engine.
- **MetaHuman Animator**: Teknologi untuk merekam performa ekspresi wajah aktor secara langsung hanya menggunakan kamera iPhone, lalu menyinkronkannya ke karakter MetaHuman di Unreal Engine secara akurat.

*(Sumber: Anthony Koithra & XboxViewTV. Catatan: Hanya materi pengenalan).*

---

**Komparasi Rig: UE5 Mannequin vs Mixamo**

- Karakter **Manny** dan **Quinn** merupakan karakter referensi standar industri (*industry standard reference*) bawaan Unreal Engine 5.
- Karakter dari **Mixamo** menggunakan pose dasar **T-Pose** (kedua tangan merentang horizontal lurus).
- Karakter **Manny & Quinn** di Unreal Engine 5 menggunakan pose dasar **A-Pose** (kedua tangan menyerong ke bawah membentuk huruf A).

Struktur penamaan tulang, orientasi sendi, dan hierarki *rig* antara Mixamo dan Manny/Quinn memiliki perbedaan mendasar. Perbedaan inilah yang melandasi pentingnya proses **Retargeting**.

> **[Gambar 5]** Diagram perbandingan pose dasar: karakter Unreal Engine (Manny/Quinn) dengan pose "A-Pose" berdampingan dengan karakter Mixamo dengan pose "T-Pose".

---

**Retargeting**

*Retargeting* merupakan teknik mentransfer data gerakan animasi antar-*skeleton* yang berbeda, meskipun nama tulang, hierarki kerangka, serta proporsi ukuran fisiknya tidak sama.

Dengan teknik *retargeting*, satu aset animasi dapat digunakan kembali (*reusable*) oleh berbagai karakter yang memiliki bentuk tubuh dan struktur kerangka yang beragam tanpa harus membuat ulang animasi dari awal.

> **[Gambar 6]** Ilustrasi alur kerja IK Retargeter yang mentransfer pose dan animasi dari skeleton sumber (*source*) ke skeleton target (*target*) secara dinamis (kredit visual: Epic Games).

---

**Struktur Rig Manny/Quinn UE5**

Struktur karakter beranimasi pada Unreal Engine 5 terdiri atas beberapa lapisan komponen:
1. **Tulang / Kerangka (Skeleton)**: Fondasi hierarki tulang yang mendefinisikan sendi dan rotasi gerak.
2. **Skin / Mesh (Skeletal Mesh)**: Model visual permukaan 3D yang terikat (*skinned*) ke kerangka tulang.
3. **Collision (Physics Asset)**: Kapsul tabrakan untuk simulasi fisika (*ragdoll*) dan deteksi benturan.
4. **Animasi (Animation Sequence / Montage)**: Rekaman data transformasi posisi dan rotasi tulang per waktu.
5. **Logika Animasi (Animation Blueprint)**: Graph pemrograman untuk mengendalikan *state machine*, pembauran (*blend spaces*), dan logika transisi pose saat *runtime*.

---

## Implementasi Custom Character dari Mixamo

> **[Gambar Sampul Seksi]** Slide pembuka bagian "Download & Implementasi Aset Mixamo ke Unreal Engine".

---

**Download Aset Mixamo**

Buka peramban dan akses situs resmi [mixamo.com](https://www.mixamo.com/).

> **PERHATIAN: Ikuti alur navigasi Mixamo secara berurutan!**  
> **Characters > Animations > Download**  
> Jika terlanjur memilih animasi terlebih dahulu sebelum karakter, kembalilah ke tab *Characters* lalu pilih ulang karakter yang diinginkan. Langkah ini wajib dilakukan agar data animasi memiliki pose *default* yang sesuai dengan proporsi karakter tersebut.

Langkah pengunduhan:
1. Buka tab **Characters**, pilih satu karakter bebas yang disukai (misal: "Aure").
2. Buka tab **Animations**, pilih satu animasi bebas yang diinginkan (misal: animasi *emote*, tarian, atau aksi).
3. Klik tombol **Download** di pojok kanan atas.
4. Pada jendela konfirmasi unduhan, atur opsi:
   - **Format**: `FBX Binary (.fbx)`
   - **Skin**: `With Skin`
   - **Frames per Second (FPS)**: `30` atau `60` (bebas)
   - **Keyframe Reduction**: `none` (opsional)
5. Klik **Download** dan simpan file FBX ke komputer.

> **[Gambar 7]** Tangkapan layar antarmuka situs Mixamo yang memperlihatkan urutan langkah: 1) Pemilihan tab Characters, 2) Pemilihan tab Animations, 3) Tombol Download, dan 4) Pengaturan dialog unduhan FBX With Skin.

---

**Import File Format FBX ke Unreal Engine**

1. Pada jendela Unreal Engine, buka panel **Content Drawer** (shortcut `Ctrl + Space`).
2. Masuk ke direktori `Characters`, lalu buat folder baru bernama **"Mixamo"** (sehingga jalurnya menjadi `Content/Characters/Mixamo`).
3. Buka folder `Mixamo` tersebut, kemudian lakukan **Drag & Drop** file FBX yang telah diunduh dari Mixamo ke dalam Content Drawer.
4. Pada jendela dialog **FBX Import Options**:
   - Klik tombol **Use Pipeline Defaults** untuk mereset opsi ke nilai standar yang aman.
   - Klik tombol **Import**.

---

**Ubah Nama File (Naming Convention)**

Setelah proses impor selesai, engine akan menghasilkan beberapa jenis aset (Skeletal Mesh, Skeleton, Physics Asset, Material, dan Textures). 

Ubah nama masing-masing aset sesuai dengan standar konvensi penamaan Unreal Engine:
- **Skeletal Mesh**: `SKM_<NamaKarakter>` (contoh: `SKM_Aure`)
- **Skeleton**: `SK_<NamaKarakter>` (contoh: `SK_Aure`)
- **Physics Asset**: `PHYS_<NamaKarakter>` (contoh: `PHYS_Aure`)
- **Animation Sequence**: `AS_<NamaAnimasi>` atau `A_<NamaAnimasi>`
- **Material**: `M_<NamaMaterial>`
- **Texture**: `T_<NamaTekstur>`

> **[Gambar 8]** Tampilan Content Drawer yang menunjukkan aset-aset hasil impor Mixamo yang telah dirapikan namanya mengikuti format prefiks standar (SKM, SK, PHYS, M, T).

---

**Retarget Animations**

Untuk menerapkan animasi bawaan Mannequin UE5 ke karakter Mixamo yang baru diimpor:
1. Buka folder animasi Mannequin pada direktori:
   `Characters/Mannequins/Anims/Unarmed`
2. Cari aset animasi *idle* bernama **"MM_idle"**.
3. Klik kanan pada aset `MM_idle`, lalu pilih opsi **Retarget Animations**.
4. Pada jendela **Retarget Animations** yang muncul:
   - Pada kolom **Target Skeletal Mesh**, pilih Skeletal Mesh karakter Mixamo yang telah diimpor (contoh: `SKM_Aure`).
   - Tinjau pratinjau pose untuk memastikan gerakan kedua karakter sinkron.
   - Klik tombol **Export Retarget Assets** (atau *Export Retarget Mesh*).
5. Pada jendela pemilihan folder ekspor, pilih folder tujuan `Mixamo` (`Content/Characters/Mixamo`), lalu klik tombol **Export**.

> **[Gambar 9]** Jendela *Retarget Animations* di Unreal Engine 5 yang menampilkan jendela komparasi dua viewport: karakter sumber (Mannequin Manny) di sebelah kiri dan karakter target Mixamo (SKM_Aure) di sebelah kanan, dengan tombol *Export Retarget Assets* di pojok kanan bawah.

---

**Membuat Animation Blueprint**

1. Di dalam folder `Content/Characters/Mixamo`, klik kanan pada area kosong di Content Drawer.
2. Pilih menu **Animation > Animation Blueprint**.
3. Pada jendela pemilihan kerangka (*Target Skeleton*), pilih skeleton milik karakter Mixamo: **SK_Aure**.
4. Beri nama file Animation Blueprint tersebut: **"ABP_Aure"**.

---

**Edit Animation Blueprint untuk Retarget**

1. Buka file **ABP_Aure** dengan klik ganda, lalu buka tab **AnimGraph**.
2. Klik kanan pada area kosong di graph, cari dan tambahkan node **Retarget Pose From Mesh**.
3. Hubungkan pin pose keluaran dari node *Retarget Pose From Mesh* ke pin **Result** pada node **Output Pose**.
4. Klik node **Retarget Pose From Mesh** untuk membuka panel Details di sisi kanan:
   - Pada bagian pengaturan, set properti **IKRetargeter Asset** ke aset **RTG** (*IK Retargeter*) yang telah dibuat secara otomatis saat proses ekspor retarget sebelumnya.
5. Klik **Compile** dan **Save**.

> **[Gambar 10]** Tampilan AnimGraph pada `ABP_Aure` yang memperlihatkan koneksi sederhana: node "Retarget Pose From Mesh" terhubung langsung ke node "Output Pose", dengan panel Details di sisi kanan menyoroti referensi aset IK Retargeter yang terpilih.

---

**Implementasi ABP ke ThirdPerson Character**

1. Buka Blueprint karakter utama pemain, yaitu **BP_ThirdPersonCharacter** (terletak pada folder `Content/ThirdPerson/Blueprints`).
2. Masuk ke tab *Viewport* atau lihat panel **Components** di sisi kiri atas.
3. Pilih komponen **Mesh (CharacterMesh0)**.
4. Pada panel **Details**:
   - Ganti aset **Skeletal Mesh Asset** menjadi **SKM_Aure** (atau lakukan drag & drop aset `SKM_Aure` dari Content Drawer ke slot mesh).
   - Pada bagian **Animation**, ubah properti **Anim Class** menjadi **ABP_Aure**.

---

**Menyembunyikan Mesh Mannequin (Hide Mesh Mannequin)**

Jika karakter custom ditambahkan berdampingan atau menimpa mesh lama sehingga terdapat dua karakter yang saling bertumpuk:
1. Pada panel **Components** di `BP_ThirdPersonCharacter`, pastikan memilih komponen **Mesh (CharacterMesh0)**.
2. Pada panel **Details** di sisi kanan:
   - Cari bagian **Rendering**, lalu **hilangkan centang** pada opsi **Visible** (agar mesh Mannequin bawaan tidak terlihat dalam game).
   - Cari bagian **Optimization**, lalu pada opsi **Visibility Based Anim Tick Option**, pilih pengaturan **Always Tick Pose and Refresh Bones**.

*Urgensi Pengaturan:* Opsi **Always Tick Pose and Refresh Bones** wajib diaktifkan agar mesin game tetap menghitung dan memperbarui pose kerangka tulang Mannequin di latar belakang meskipun wujud fisiknya disembunyikan (*invisible*). Tanpa opsi ini, node *Retarget Pose From Mesh* pada karakter Mixamo akan membeku dan tidak dapat menerima data pose pergerakan saat dimainkan.

---

## Implementasi Animasi Pada Karakter (Montage)

> **[Gambar Sampul Seksi]** Slide pembuka bagian "MONTAGE" yang membahas teknik pemutaran animasi modular sesaat.

---

**Animation Montage**

Merupakan "pembungkus" (*wrapper*) dari *Animation Sequence* yang dapat dipicu (*trigger*) kapan saja melalui alur logika Blueprint, lalu dimainkan menimpa (*overlay/blend*) animasi yang sedang berjalan dengan transisi pembauran (*blending in* dan *blending out*) yang halus.

*Anim Montage* sangat cocok untuk aksi-aksi sesaat yang dipicu oleh input pemain, seperti:
- *Emote* atau gerakan ekspresi
- Serangan senjata (*attack combo*)
- Penggunaan kemampuan (*cast skill / spell*)
- Pengisian peluru (*reload weapon*)
- Menghindar (*dodge / roll*)

**Perbedaan Utama:**
- **Animation Sequence**: Mengambil alih karakter secara kaku; jika diputar langsung, state *Animation Blueprint* utama akan terhenti.
- **Anim Montage**: Disisipkan secara modular di atas *Animation Blueprint* menggunakan sistem slot, dengan transisi *blending* yang halus tanpa memutus logika pergerakan dasar (misalnya karakter tetap bisa berjalan sambil mengayunkan pedang).

> **[Gambar 11]** Ilustrasi aksi karakter game saat memicu animasi khusus sesaat (kredit visual: Orpheus Joshua; Square Enix, Ltd.).

---

**Convert Animation Sequence ke Montage**

1. Di dalam folder `Mixamo`, cari file *Animation Sequence* yang telah diimpor/dihasilkan (misal animasi tarian atau aksi tertentu).
2. Klik kanan pada aset *Animation Sequence* tersebut, lalu pilih opsi menu:
   **Create > Create AnimMontage**
3. Beri nama file montage baru tersebut: **"AM_Emote"**.

---

**Konfigurasi Slot pada Animation Blueprint**

Agar *Animation Montage* dapat dimainkan melalui *Animation Blueprint*:
1. Buka kembali file **ABP_Aure** pada tab **AnimGraph**.
2. Klik kanan pada area kosong di antara node *Retarget Pose From Mesh* dan node *Output Pose*, lalu cari dan tambahkan node:
   **Slot 'DefaultSlot'**
3. Hubungkan pin keluaran dari *Retarget Pose From Mesh* ke pin masukan *Source* pada node **Slot 'DefaultSlot'**, kemudian hubungkan keluarannya ke pin **Result** pada node **Output Pose**.
4. Klik **Compile** dan **Save**.

> **[Gambar 12]** Diagram rangkaian AnimGraph pada `ABP_Aure`: node "Retarget Pose From Mesh" → node "Slot 'DefaultSlot'" → node "Output Pose".

---

**Play Animation Montage Saat Gameplay**

Untuk memicu pemutaran montage melalui input tombol keyboard pemain:
1. Buka Blueprint **BP_ThirdPersonCharacter**.
2. Masuk ke tab **Event Graph**.
3. Tambahkan alur logika pemanggilan montage berikut:
   - Klik kanan di area kosong Event Graph, cari dan tambahkan node input: **Keyboard Event E**.
   - Tarik garis dari pin eksekusi **Pressed** pada node *Keyboard Event E*, lalu hubungkan ke node **Play Anim Montage**.
   - Pada node **Play Anim Montage**:
     - Atur slot parameter **Anim Montage** ke aset **AM_Emote**.
     - Pastikan pin *In Skeletal Mesh Component* (Target) terhubung ke komponen mesh karakter (atau dibiarkan terhubung ke referensi *self*).
4. Klik **Compile** dan **Save**.
5. Klik tombol **Play** di Viewport Unreal Engine untuk mencoba memainkan game. Tekan tombol **E** pada keyboard untuk melihat karakter Mixamo memainkan animasi emote secara mulus saat gameplay!

> **[Gambar 13]** Tangkapan layar Event Graph pada `BP_ThirdPersonCharacter` yang menampilkan koneksi: node "Keyboard Event E" (pin Pressed) terhubung ke input node "Play Anim Montage" dengan properti Anim Montage diset ke "AM_Emote".

---

## FORMAT TUGAS

Struktur laporan mengikuti format laporan praktikum pada kelas lainnya, dengan ketentuan minimal memuat:

- **Dokumentasi Praktikum**
  a. Cantumkan *screenshot* setiap langkah penting pada sesi praktikum ini (pembuatan landscape, lighting, import Mixamo, retargeting, konfigurasi ABP, dan pengujian montage).
  b. Berikan keterangan singkat mengenai apa yang dilakukan pada setiap *screenshot*.
- **Hasil Akhir**
- **References**

---

## ATURAN TUGAS

- **LINK PENGUMPULAN:**  
  [Form Pengumpulan Tugas Pertemuan 6](https://docs.google.com/forms/d/e/1FAIpQLScBUuQaJMe7OxLexKSeA72ORSpaWUfEonWfSz8Up1vsNYh68w/viewform?usp=dialog)  
  `https://docs.google.com/forms/d/e/1FAIpQLScBUuQaJMe7OxLexKSeA72ORSpaWUfEonWfSz8Up1vsNYh68w/viewform?usp=dialog`
- **Format nama file:** `NIU_Nama Lengkap_PPG_Pertemuan X`  
  (Contoh: `535493_Hafidz Rizqullah Prasetya_PPG_Pertemuan 6`)
- **Format file yang diterima:** PDF, maksimal 10 MB. Kalau melebihi batas ukuran, silakan lakukan kompresi PDF terlebih dahulu.
- **Deadline:**  
  Deadline mengikuti jadwal kelas masing-masing, yaitu sebelum jam pertemuan minggu berikutnya:
  - **Kelas A1 dan B2**: deadline minggu depannya sebelum jam 07.30
  - **Kelas A2 dan B1**: deadline minggu depannya sebelum jam 12.30

---

## References

- Epic Games Developer Documentation — *Working with Levels in Unreal Engine*:  
  https://dev.epicgames.com/documentation/unreal-engine/working-with-levels-in-unreal-engine
- The Real Unreal — *Anim Montage Tutorial*:  
  https://www.youtube.com/@therealunreal6799

---

*Locally Rooted, Globally Respected — Universitas Gadjah Mada*  
*Sekian, thank suwun.*
