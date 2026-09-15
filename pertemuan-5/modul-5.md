# PRAK. PENGEMBANGAN GAME (PPG)
### T.A. 2026/2027 — PERTEMUAN 5
## GAME INSTANCE & SAVEGAME

*Locally Rooted, Globally Respected — Universitas Gadjah Mada*

> **[Gambar Sampul]** Slide judul dengan logo UGM di kanan atas, latar putih dengan sketsa garis bangunan bergaya Balairung UGM di sisi kanan, serta bilah warna biru tua dan kuning di sisi kiri.

---

## Save Game

> **[Gambar Sampul Seksi]** Slide judul "Save Game" dengan gaya visual sama seperti sampul sebelumnya.

---

**Save Game**

Digunakan untuk menyimpan data yang dapat digunakan pada sesi permainan yang berbeda.

Cara membuatnya seperti pada langkah pembuatan *Game Instance* tapi pilih pada *Parent Class* SaveGame.

Buat file Blueprint baru, pilih class **"SaveGame"** beri nama **"BP_SaveGame"**.

> **[Gambar 1]** Tangkapan layar jendela "Pick Parent Class" pada Unreal Engine. Bagian atas (COMMON) menampilkan opsi umum seperti Actor, Pawn, Character, Player Controller, Game Mode Base, Actor Component, Scene Component, masing-masing dengan deskripsi singkat. Di bagian bawah (ALL CLASSES), kolom pencarian berisi teks "save" menampilkan hasil filter: SaveGame (disorot kotak merah dan hijau), BP_Savegame, dan LocalPlayerSaveGame — total 4 item, dengan tombol "Select" dan "Cancel" di bawah.

---

**Struct Variable**

Buat structure baru lalu beri nama **"S_PlayerState"**. Tambahkan variabel bertipe *transform* pada structure tersebut.

> **[Gambar 2]** Dua tangkapan layar:
> 1. Menu dropdown "Add" pada Content Drawer menampilkan kategori (Artificial Intelligence, Audio, **Blueprint** diperluas menjadi Blueprint Class/Function Library/Interface/Macro Library, Enumeration, dan **Structure** disorot biru), dengan kategori lain (Cinematics, Editor Utilities, Foliage, FX, Gameplay, Input, Interchange, Material, Media) serta label "User Defined Struct".
> 2. Editor Structure `S_PlayerState` menampilkan tab Structure dan Default Values, dengan satu variabel bernama "Transform" bertipe **Transform** (ditandai kotak merah baik pada nama variabel maupun tipe datanya).

---

**Save Game**

Pada Blueprint **BP_SaveGame** (BP yang telah dibuat di Slide 3), tambahkan variabel dengan nama **"S_PlayerState"** bertipe data **S_PlayerState**.

> **[Gambar 3]** Panel *My Blueprint* pada `BP_SaveGame` menampilkan struktur: Graphs (EventGraph), Functions, Macros, dan bagian **Variables** berisi variabel `S_PlayerState` bertipe "S Player State" (nama variabel dan tombol tambah variabel disorot kotak merah), serta Event Dispatchers (kosong).

---

## Game Instance

> **[Gambar Sampul Seksi]** Slide judul "Game Instance" dengan gaya visual sama seperti sampul-sampul sebelumnya.

---

**Game Instance**

Merupakan elemen dalam Unreal Engine yang pasti akan ada pada setiap *Level* sebelum aktor yang dimainkan muncul. **Game Instance akan selalu muncul tanpa harus diinisiasi.**

Elemen ini sering digunakan untuk menyimpan variabel yang digunakan pada berbagai *Level* dan **dapat diakses secara global**. Bagi yang pernah menggunakan Unity, konsep ini sama seperti *Game Manager*.

Contoh diagram dapat dilihat pada tautan berikut:
https://forums.unrealengine.com/t/how-to-check-which-begin-play-or-something-similar-goes-first-c/1565114/2

---

**Game Instance**

Buat file Blueprint baru dengan class **"GameInstance"**. Beri nama file **"BP_GameInstance"**.

*Game Instance* dapat diatur pada **Edit > Project Settings > Project - Maps & Modes > Game Instance**.

> **[Gambar 4]** Dua bagian:
> 1. Jendela "Pick Parent Class" dengan kolom pencarian berisi "game ins", menampilkan hasil: GameInstance (disorot kotak merah), BP_GameInstance, PlatformGameInstance, TestGameInstance — total 5 item (1 dipilih), dengan tombol "Select" dan "Cancel".
> 2. Panel Project Settings bagian "Game Instance" menampilkan field "Game Instance Class" dengan nilai **BP_GameInstance** terpilih (disorot kotak merah).

---

**Game Instance**

Dalam **BP_GameInstance** yang barusan dibuat, tambahkan variabel dengan nama **"SaveGame"** bertipe data **BP Save Game** (BP yang dibuat di Slide 3).

Buat juga variabel dengan nama **"SlotName"** bertipe data **string**. Variabel ini digunakan untuk nama yang akan diimplementasikan pada *interface*. Set Slot Name bebas!

> **[Gambar 5]** Dua panel:
> 1. Panel Variables menampilkan dua variabel: `SaveGame` bertipe "BP Save..." dan `SlotName` bertipe "String", dengan panah merah dari `SlotName` mengarah ke panel kedua.
> 2. Panel "Default Value" menampilkan field "Slot Name" berisi teks "1" sebagai contoh nilai default.

---

**Membuat Blueprint Interface**

Buat file Blueprint Interface, beri nama **"BPI_SaveData"**.

Dalam BPI yang barusan dibuat, tambahkan 4 fungsi serta sesuaikan input/outputnya:
- **LoadGameData**
  - Input ("Async", tipe data *Boolean*)
- **SaveGameData**
  - Input ("Async", tipe data *Boolean*)
- **GetGameData**
  - Output ("S_PlayerState", tipe data *S Player State*)
- **SavePlayer**
  - Input ("S_PlayerState", tipe data *Player State*)
  - Input ("Async", tipe data *Boolean*)

> **[Gambar 6]** Panel *My Blueprint* pada Interface `BPI_SaveData` menampilkan daftar Functions: LoadGameData, **SaveGameData** (disorot biru sebagai fungsi aktif), GetGameData, SavePlayer. Panel Details di bawahnya menampilkan pengaturan Graph (Description, Category: Default, Keywords, Compact Node Title, Call In Editor) serta bagian **Inputs** (variabel "Async" bertipe Boolean) dan **Outputs** (kosong, dengan instruksi "Please press the + icon above to add parameters") — kedua bagian Inputs/Outputs disorot kotak merah.

---

**Game Instance**

Buka **BP_GameInstance**, lalu implement **BPI_SaveData**.

Setelah berhasil menambahkan BPI, akan muncul tab *interfaces* di menu *myblueprint* seperti ini.

> **[Gambar 7]** Tangkapan layar Blueprint Editor `BP_GameInstance` dengan anotasi panah merah: "Klik Class Settings" mengarah ke tombol Class Settings pada toolbar, dan "Implement BPI disini" mengarah ke bagian panel Details berjudul "Implemented Interfaces" berisi entri "BPI Save Data". Panel kiri (My Blueprint) menampilkan Graphs (EventGraph), Functions, Interfaces, Macros, dan Variables (SaveGame bertipe BP Save, SlotName bertipe String). Di kanan, sebuah panel terpisah menampilkan hasil setelah interface diimplementasikan: bagian **INTERFACES** berisi SavePlayer, GetGameData, SaveGameData, LoadGameData.

---

**Game Instance**

Klik 2x pada fungsi *GetGameData* untuk mengimplementasikan Interface.

*GetGameData* mengambil dan mengembalikan struct data pemain (Player State) yang sedang aktif untuk dibaca oleh Actor lain (contohnya saat player melakukan spawn dalam Level).

> **[Gambar 8]** Panel kiri menampilkan daftar Interfaces (SavePlayer, **GetGameData** disorot kotak merah, SaveGameData, LoadGameData). Panel kanan menampilkan Event Graph fungsi GetGameData: node "GetGameData" → "Does Save Game Exist" (dengan input Slot Name dan User Index) → node "Branch" (True/False) → jika True, node "Return Node" mengembalikan "Player State"; ada juga alur kedua dari variabel "Save Game" menuju node "Return Node" kedua yang mengembalikan nilai default Player State Position (Location, Rotation, Scale) dengan nilai numerik default (0.0 dan 1.0).

---

**SavePlayer Function**

Klik 2x pada fungsi *SavePlayer* untuk mengimplementasikan Interface.

*SavePlayer* menerima struct data terbaru dari player actor, memasukkannya ke dalam variabel objek Save Game di memori (RAM), lalu meneruskan/*execute* fungsi SaveGameData (yang di dalamnya berisi *logic* menyimpan informasi save game ke disk via file *.sav*).

> **[Gambar 9]** Panel kiri menampilkan daftar Interfaces (**SavePlayer** disorot kotak merah, GetGameData, SaveGameData, LoadGameData). Panel kanan menampilkan Event Graph: node "Event SavePlayer" (From BPI Save Data) dengan output Player State dan Async → node "SET" (mengeset S Player State dan Target) → node "Save Game Data" (Target is BP Game Instance) dengan input Target (self) dan Async; ada juga koneksi dari variabel "Save Game" menuju node SET.

---

**SaveGameData Function**

Klik 2x pada fungsi *SaveGameData* untuk mengimplementasikan Interface.

*SaveGameData* mengeksekusi *write* objek Save Game ke storage lokal (file *.sav*) pada nama slot.

> **[Gambar 10]** Panel kiri menampilkan daftar Interfaces (SavePlayer, GetGameData, **SaveGameData** disorot kotak merah, LoadGameData). Panel kanan menampilkan Event Graph: node "Event SaveGameData" (From BPI Save Game) dengan output Async → node "Branch" (True/False) → jika True, node "Async Save Game to Slot" dengan input Save Game Object, Slot Name, User Index, dan output Completed/Success; jika False, node "Save Game to Slot" (fungsi biasa/sinkron) dengan input serupa dan output Return Value. Variabel "Slot Name" dan "Save Game" terhubung ke kedua node tersebut.

---

**LoadGameData Function**

Klik 2x pada fungsi *LoadGameData* untuk mengimplementasikan Interface.

Memuat data file *.sav* dari disk ke dalam memori RAM saat game pertama kali dibuka.

> **[Gambar 11]** Panel kiri menampilkan daftar Interfaces (SavePlayer, GetGameData, SaveGameData, **LoadGameData** disorot kotak merah). Panel kanan menampilkan Event Graph yang kompleks: node "Event LoadGameData" (From BPI Save Data) dengan output Async dan Slot Name → node "Does Save Game Exist" → node "Branch" pertama → jika True, node "Branch" kedua bercabang ke:
> - node "Async Load Game from Slot" (Slot Name, User Index, output Completed, Save Game, Success) → "Cast To BP_Savegame" → "SET" (Save Game).
> - node "Load Game from Slot" (versi sinkron) → "Cast To BP_Savegame" → "SET" (Save Game).
> Jika save game belum ada, alur menuju node "Create Save Game Object" (Save Game Class: BP Savegame) → "SET" (Save Game).

---

**Game Instance Event Init**

Setelah beberapa implementasi interface untuk kebutuhan save game selesai, maka pada **BP_GameInstance** lalu tambahkan *Event Init* untuk load save game.

> **[Gambar 12]** Event Graph sederhana menampilkan node "Event Init" yang terhubung langsung ke node "Load Game Data" (Target is BP Game Instance) dengan pin Target (self) dan Async (dikosongkan/dimatikan).

---

**Set Actor Location Dari Game Instance**

Tambahkan *logic* ini ke dalam **BP_ThirdPersonCharacter**.

*Logic* ini berfungsi untuk *restore* (memindahkan) posisi karakter ke koordinat terakhir yang tersimpan saat level mulai dimainkan (Event BeginPlay), dengan proteksi agar tidak menimpa posisi default PlayerStart jika belum ada data save.

> **[Gambar 13]** Event Graph menampilkan alur: node "Event BeginPlay" → node "Get Game Data" (Target is BP Save Data) dengan output Player State Position Location, Rotation, Scale → node "Branch" (True/False, dengan nilai kondisi dari pembanding koordinat 0.0, 0.0, 0.0) → jika True, node "Set Actor Location" (Target: self, New Location, Sweep, Teleport dikosongkan) dengan output Sweep Hit Result dan Return Value. Node "Get Game Instance" terhubung sebagai Target ke node Get Game Data.

---

**Membuat Check Point**

Tambahkan *Blueprint Actor* baru dengan nama **"BP_CheckPoint"** berisi *Box collision* yang akan dicoba sebagai *checkpoint* di dalam Level.

> **[Gambar 14]** Dua panel:
> 1. Panel Components `BP_CheckPoint (Self)` menampilkan hierarki: DefaultSceneRoot > Box, dengan panah merah menunjuk ke node "On Component Begin Overlap (Box)" pada panel kanan.
> 2. Event Graph menampilkan alur: node "On Component Begin Overlap (Box)" (dengan output Overlapped Component, Other Actor, Other Comp, Other Body Index, From Sweep, Sweep Result) → node "Do Once" (Completed, Reset, Start Closed) → node "Get Actor Transform" (Target: Self, output Return Value Location/Rotation/Scale) dan node "Get Game Instance" (output Return Value) → node "Save Player" (Target is BPI Save Data) dengan input Target, Player State Transform Location/Rotation (0.0)/Scale (1.0), dan Async (dicentang).

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
  https://docs.google.com/forms/d/e/1FAIpQLSdINEaeVa_ymH3xgJQv8SokTH7JN6eImfwIPJAHNbMmANI77w/viewform?usp=publish-editor
- **Format nama file:** `NIU_Nama Lengkap_PPG_Pertemuan X`
  (Contoh: `123456_Sugeng Semar_PPG_Pertemuan 5`)
- **Format file yang diterima:** PDF, maksimal 10 MB. Kalau melebihi, silakan compress.
- **Deadline:**
  Deadline mengikuti jadwal kelas masing-masing, yaitu sebelum jam pertemuan minggu berikutnya.
  - Kelas A1 dan B2: deadline minggu depannya sebelum jam 7.30
  - Kelas A2 dan B1: deadline minggu depannya sebelum jam 12.30

---

*Sekian, matur thank you.*