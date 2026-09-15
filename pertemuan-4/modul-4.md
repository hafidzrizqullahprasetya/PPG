# PRAK. PENGEMBANGAN GAME (PPG)
### T.A. 2026/2027 — PERTEMUAN 4
## INTERFACE, COMPONENT & COLLISION

*Locally Rooted, Globally Respected — Universitas Gadjah Mada*

> **[Gambar Sampul]** Slide judul dengan logo UGM di kanan atas, latar putih dengan sketsa garis bangunan bergaya Balairung UGM di sisi kanan, serta bilah warna biru tua dan kuning di sisi kiri.

---

## Component

**Component**

Bersifat seperti Blueprint tapi memerlukan Blueprint lainnya untuk ditumpangi. Biasanya digunakan untuk implementasi fitur modular yang dapat berubah sewaktu-waktu.

Silahkan inisiasi component bernama **"BPC_Health"** yang berisi variabel `currentHealth` (float), `maxHealth` (float), fungsi `ModifyHealth`, serta memiliki event dispatcher berupa `onDeath`.

> **[Gambar 1]** Tiga tangkapan layar berdampingan:
> 1. Panel "Add" pada Content Drawer Unreal Engine menampilkan menu tambah aset baru (New Folder, Animation Blueprint, Blueprint Class, Level, Level Sequence, dll).
> 2. Jendela pemilihan kelas komponen ("ALL CLASSES") dengan opsi *Actor Component* dan *Scene Component* disorot, serta daftar turunan seperti ActorSequenceComponent, BrainComponent, StateTreeComponent, HealthComponent, dan lainnya, dengan tombol "Select".
> 3. Panel *My Blueprint* menampilkan struktur Blueprint komponen: Graphs (EventGraph berisi Event Begin Play dan Event Tick), Functions (ModifyHealth, dapat di-*override*), Variables (CurrentHealth dan MaxHealth bertipe Float), serta Event Dispatchers (OnDeath) — semuanya ditandai kotak merah sebagai bagian penting.

---

**Component**

Pada tab Event Graph, tambahkan set `CurrentHealth == MaxHealth` di node *BeginPlay*.

> **[Gambar 2]** Tangkapan layar Event Graph berisi node "Event Begin Play" yang terhubung ke node "SET" untuk variabel *Current Health*, dengan pin *Max Health* dihubungkan sebagai nilai input ke node SET tersebut.

---

**Component**

Isi fungsi `ModifyHealth` seperti ini:

> **[Gambar 3]** Diagram blueprint fungsi ModifyHealth: 
> - Node fungsi `ModifyHealth` dengan input `Health` mengalir ke operasi pengurangan (`Current Health` dikurangi `Health`, dengan pin tambahan/"Add pin").
> - Hasil pengurangan masuk ke node `Branch` pertama dengan kondisi pembanding terhadap nilai `100.0` (True/False).
> - Jika kondisi terpenuhi, nilai di-*set* ke `Current Health`.
> - Hasil SET kemudian dicek lagi oleh `Branch` kedua dengan kondisi `<= 0.0`.
> - Jika True, alur berlanjut ke node `Call On Death` dengan target `self`.

---

**Component**

Tambahkan komponen **"BPC_Health"** yang sudah dibuat tadi ke dalam `BP_ThirdPersonCharacter` dengan melakukan Drag and Drop dari Content Drawer.

> **[Gambar 4]** Dua tangkapan layar:
> 1. Struktur folder Content Drawer: LevelPrototyping, ThirdPerson > Blueprints, Engine, dengan thumbnail Blueprint Class bernama "BP_ThirdPersonCharacter".
> 2. Panel Components pada `BP_ThirdPersonCharacter (Self)` menampilkan hierarki komponen: Capsule Component (CollisionCylinder), CameraBoom > FollowCamera, Mesh (CharacterMesh0), Arrow Component (Arrow), **HealthComponent** (disorot biru sebagai komponen baru yang ditambahkan), dan Character Movement (CharMoveComp).

---

**Component**

Bind `onDeath` di dalam `BP_ThirdPersonCharacter`.

> **[Gambar 5]** Tiga bagian tangkapan layar Blueprint Editor:
> 1. Panel Components dengan klik kanan pada BPC_Health menampilkan menu konteks (Find References, **Add Event > OnDeath** disorot, Cut/Copy/Paste/Duplicate/Delete/Rename).
> 2. Event Graph menampilkan alur: node "On Death (BPC_Health)" → "Get Actor Scale 3D" → "Set Actor Scale 3D" (Target: self) → node "SET" yang menghubungkan `Max Health` dan `BPC Health` ke `Current Health`.
> 3. Detail node "Set Actor Scale 3D" menunjukkan pin Target (self) dan New Scale 3D (0.0, 0.0, 0.0), dengan referensi ke variabel `self`.

---

## Interface

> **[Gambar Sampul Seksi]** Slide judul "Interface" dengan gaya visual sama seperti sampul sebelumnya (sketsa bangunan UGM, bilah biru-kuning).

---

**Interface**

Digunakan ketika mengimplementasikan fungsi pada sebuah Blueprint Class yang sudah pasti ada, akan tetapi bersifat berbeda tergantung pada Blueprint Class yang mengimplementasikan.

```
Lingkaran.Luas() != Segitiga.Luas()
```

---

**Interface**

Silahkan membuat *Interface Class* dengan cara:
- Buat Folder "Interfaces" di *root directory*
- Klik "Add" pada tab Content Drawer
- Pilih Blueprint > Blueprint Interface

> **[Gambar 6]** Dua tangkapan layar:
> 1. Content Drawer kosong dengan tombol "Add" disorot kotak merah, tooltip "Create new content in /All/Game...", dan folder-folder yang ada (Characters, Input, Level Prototyping, Pertemuan2, Pertemuan4).
> 2. Menu dropdown "Add" menampilkan kategori (Animation, Artificial Intelligence, Audio, **Blueprint**) yang diperluas menampilkan submenu: Blueprint Class, Blueprint Function Library, **Blueprint Interface** (disorot biru), Blueprint Macro Library, Enumeration, Structure.

---

**Interface**

Berikan nama dengan Prefix **"BPI_"**. BPI berarti Blueprint Interface.

> **[Gambar 7]** Ikon aset Blueprint Interface berbentuk gerigi dengan panah, diberi nama "BPI_Overlap", berlabel "Blueprint Interface" di bawahnya.

---

**Interface**

Tambahkan fungsi pada Interface yang sudah dibuat (tombol add ada di sebelah kanan atas), dan tambahkan input berupa variabel `AmountDamage` dengan tipe data float.

> **[Gambar 8]** Dua panel:
> 1. Panel *My Blueprint* dengan tombol "Add" disorot dan daftar Functions berisi fungsi `TakeDamage`.
> 2. Panel Details untuk fungsi tersebut menampilkan Graph (Description, Category: Default, Keywords, Compact Node Title, Call In Editor, Advanced), serta bagian Inputs dengan variabel `AmountDamage` bertipe Float (disorot kotak merah), dan Outputs kosong.

---

## Implementasi Interface

> **[Gambar Sampul Seksi]** Slide judul "Implementasi Interface" dengan gaya visual sama seperti sampul-sampul sebelumnya.

---

**Implementasi Interface**

Pada `BP_ThirdPersonCharacter` silahkan implementasikan `BPI_Overlap` pada menu Class Settings. Pada bagian tab Details cari "Implemented Interfaces" lalu klik "Add" dan tambahkan *interface* yang sudah diinisiasi sebelumnya.

> **[Gambar 9]** Tangkapan layar Blueprint Editor `BP_ThirdPersonCharacter` dengan toolbar (Compile, Diff, Find, Hide Unrelated, **Class Settings** disorot kotak merah, Class Defaults, Simulation). Panel Details di kanan menampilkan Class Options (Parent Class: Character), Blueprint Options, dan bagian **Interfaces > Implemented Interfaces** (disorot kotak merah) dengan tombol "Add" dan entri "BPI Touch Interface" yang sudah ada.

---

**Implementasi Interface**

Pada implement interface maka akan muncul fungsi pada menu interface seperti pada gambar paling bawah setelah Blueprint di-*compile* ulang.

> **[Gambar 10]** Tiga panel:
> 1. Dropdown "Add" dengan opsi "Implement Interface" menampilkan input pencarian "bpi_overlap" dan hasil "BPI_Overlap" (1 item).
> 2. Panel "Implemented Interfaces" menampilkan dua entri: "BPI Touch Interface" dan "BPI Overlap" (keduanya disorot kotak kuning/merah), masing-masing dengan ikon dan tombol hapus (X).
> 3. Panel Functions menunjukkan daftar fungsi yang dapat di-*override* (Construction Script, Move, Aim) dan bagian **Interfaces** berisi kategori "Touch" dan fungsi `TakeDamage` (disorot kotak kuning).

---

**Implementasi Interface**

Implementasikan fungsi `HealthComponent` pada Interface (caranya klik 2x pada fungsi interface atau klik kanan lalu pilih Implement Event).

> **[Gambar 11]** Dua bagian:
> 1. Panel Functions/Interfaces menampilkan Construction Script, Move, Aim, kategori Interfaces "Touch", dan fungsi `TakeDamage`.
> 2. Event Graph menampilkan alur: node "Event TakeDamage" (From BPI Overlap) dengan output "Amount Damage" → node "Modify Health" (Target is BPC Health, terhubung dari `BPC Health` dan `Current Health`) → node "Print String" (In String, ditandai "Development Only").

---

## Collision

> **[Gambar Sampul Seksi]** Slide judul "Collision" dengan gaya visual sama seperti sampul-sampul sebelumnya.

---

**Collision**

Salah satu *state machine* yang digunakan untuk berkomunikasi antar aktor yang berada di dalam Level Unreal Engine. Silahkan membuat Actor Blueprint dengan nama **"BP_Collision"** yang berisi *box collision*. Tambahkan blueprint `onBeginOverlap` pada Blueprint ini dan manfaatkan *interface* untuk melakukan modifikasi terhadap komponen *health* yang dimiliki *player*.

> **[Gambar 12]** Dua panel:
> 1. Blueprint Editor `BP_Collision` menampilkan panel Components (BP_Collision (Self) > DefaultSceneRoot > Box) dan panel Details untuk komponen "Box" — bagian Collision (Generate Overlap Events dicentang) dan Events dengan tombol tambah "On Component Begin Overlap" disorot kotak merah.
> 2. Event Graph menampilkan node "On Component Begin Overlap (Box)" dengan output Overlapped Component, Other Actor, Other Comp, Other Body Index, From Sweep, Sweep Result → terhubung ke node "Take Damage" (Target is BPI Overlap) dengan Amount Damage = 10.0.

---

**Collision**

Tambahkan `BP_Collision` ke dalam *level* dengan melakukan *drag and drop* dari Content Browser. Coba mainkan gamenya (Play), Box Collision yang telah dibuat tidak kelihatan dalam Level.

> **[Gambar 13]** Tangkapan layar viewport permainan (perspektif orang ketiga) menunjukkan lantai bertekstur ubin abu-abu dengan dinding hijau di latar belakang, serta gizmo transform (panah biru/hijau/merah) menandai posisi objek — namun *bounding box* dari Box Collision tidak terlihat secara visual saat permainan dijalankan.

---

**Collision**

Ubah pengaturan ini pada komponen box collision agar *boundaries*-nya terlihat ketika game dimainkan.

> **[Gambar 14]** Tangkapan layar Blueprint Editor `BP_Collision`: panel Components (Box disorot), viewport menampilkan kotak collision dengan gizmo panah, dan panel Details dengan pencarian "hidden" menampilkan opsi **Rendering > Hidden in Game** (kotak centang dikosongkan/dimatikan, disorot kotak merah) serta Hidden In Scene Capture dan Collision > Consider for Actor Placement.

---

**Collision**

Untuk sedikit variasi, tambahkan *instance editable* variabel *float* agar variabel dapat diubah di dalam *level* yang terhubung ke *input parameter* fungsi `takeDamage`.

> **[Gambar 15]** Dua panel:
> 1. Event Graph menampilkan alur: "On Component Begin Overlap (Box)" → node "Take Damage" (Target is BPI Overlap) dengan variabel "Damage" (bulat oranye) dihubungkan ke pin Amount Damage.
> 2. Panel Details variabel menampilkan Variable Name: "Damage", Variable Type: Float, dan opsi **Instance Editable** dicentang (disorot kotak merah), beserta opsi lain (Blueprint Read Only, Expose on Spawn, Private, Expose to Cinematics) yang tidak dicentang.

---

**Collision**

Silahkan ubah *value* variabel sebelumnya melalui *level*.

> **[Gambar 16]** Panel Details untuk instance `BP_Collision` di dalam level, menampilkan Transform (Location: 340.0, 110.0, 320.0; Rotation: 0°, 0°, 0°; Scale: 3.0, 3.25, 3.25) dan bagian **Default > Damage** dengan nilai `30.0` (disorot kotak merah) yang dapat diubah langsung dari level.

---

## FORMAT TUGAS

Struktur laporan mengikuti format laporan praktikum pada kelas lainnya, dengan ketentuan minimal memuat:

- **Dokumentasi Praktikum**
  a. Cantumkan screenshot setiap langkah penting pada sesi praktikum ini.
  b. Berikan keterangan singkat mengenai apa yang dilakukan pada screenshot.
- **Hasil Akhir**
- **References**

---

## ATURAN TUGAS

- **LINK PENGUMPULAN:**
  https://docs.google.com/forms/d/e/1FAIpQLSf-oZRs38Iaek1-Sk0fFdS4d8hUuNMMpGzRbJT3qireZmzPfw/viewform?usp=publish-editor
- **Format nama file:** `NIU_Nama Lengkap_PPG_Pertemuan X`
  (Contoh: `123456_Sugeng Semar_PPG_Pertemuan 4`)
- **Format file yang diterima:** PDF, maksimal 10 MB. Kalau melebihi, silakan compress.
- **Deadline:**
  Deadline mengikuti jadwal kelas masing-masing, yaitu sebelum jam pertemuan minggu berikutnya.
  - Kelas A1 dan B2: deadline minggu depannya sebelum jam 7.30
  - Kelas A2 dan B1: deadline minggu depannya sebelum jam 12.30

---

## Sumber Materi

Ali Elzoheiry — https://www.youtube.com/watch?v=EQfml2D9hwE

---

*Sekian, matur thank you.*