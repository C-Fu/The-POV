# SPEC-DRIVEN-DEVELOPMENT — Kenapa Spesifikasi Mengatasi Prompt

Bahasa Melayu | [English](SPEC-DRIVEN-DEVELOPMENT.md) · Kembali ke [README](README.ms-MY.md)

**Pembangunan berasaskan spesifikasi (spec-driven development, SDD)** bermaksud menulis *apa* yang ingin dibina — sebagai dokumen Markdown berstruktur — **sebelum** membina, kemudian menjadikan dokumen tersebut sumber kebenaran tunggal yang dirujuk oleh anda dan AI. [START.md](START.ms-MY.md) membawa anda kepada spesifikasi pertama; panduan ini menerangkan kenapa spesifikasi mengatasi "prompt and pray", dan memperkenalkan lima fail spesifikasi yang digunakan dalam toolkit ini.

---

## 1. Prompt lenyap. Spesifikasi kekal.

Kejuruteraan prompt ringkas ialah satu perbualan: terangkan apa yang anda mahu, ulang sehingga kelihatan betul, salin hasilnya. Ia berfungsi — sehingga sesi berakhir. Lepas itu:

- konteks hilang (chat baharu = terangkan semuanya semula),
- tiada siapa boleh menyemak apa yang diputuskan, dan kenapa,
- "siap" bermaksud apa sahaja yang kelihatan betul pada hari itu.

Spesifikasi ialah perbualan yang sama, **ditulis dan di-commit ke git**. Ia ialah prompt yang tidak lenyap: setiap sesi akan datang, agen, atau rakan sepasukan membaca sumber kebenaran yang sama — dan setiap perubahan kepadanya ialah diff yang boleh disemak.

> Prompting tidak hilang dalam SDD — ia menjadi *lebih kecil dan tajam*, kerana ilmu yang kekal hidup dalam spesifikasi, bukan dalam scrollback.

---

## 2. Kenapa spec-driven menang

| | Kejuruteraan prompt ringkas | Pembangunan berasaskan spesifikasi |
|--|-----------------------------|-------------------------------------|
| **Ingatan** | Hidup dalam satu chat; hilang bila sesi baharu | Fail dalam git — kekal walaupun crash, sesi baharu, atau serahan tugas |
| **Guna semula** | Tampal dan terangkan semula konteks setiap kali | Tunjuk fail itu kepada agen sekali sahaja |
| **Konsistensi** | Prompt sama, output berbeza esok | Teks tetap; hanya suntingan sengaja mengubahnya |
| **"Siap"** | Subjektif — "nampak betul bagi saya" | Kriteria penerimaan boleh disemak (GSD mengesahkannya) |
| **Skala** | Satu prompt tidak muat seluruh app | Spesifikasi terbahagi secara semula jadi kepada fasa dan milestone |
| **Semakan** | Keputusan terkubur dalam scrollback | Keputusan boleh di-diff, dikomen, dikembalikan |
| **Pembaikan** | Pertaruhan pada prompt lain lagi | Sunting satu seksyen, commit, bina semula |

---

## 3. Lima fail spesifikasi

Toolkit ini membahagikan spesifikasi kepada lima dokumen. Setiap satu menjawab satu soalan:

| Fail | Menjawab | Menyuburkan |
|------|----------|-------------|
| `BUSINESS-DESIGN-SPECIFICATION.md` | **Kenapa** ini wujud — dan untuk siapa? | Skop, potongan v1, metrik kejayaan |
| `MARKETING-DESIGN-SPECIFICATION.md` | **Bagaimana** orang akan menjumpainya — dan menghiraukannya? | Landing page, pelancaran, bahan demo |
| `DESIGN.md` | **Seperti apa** rupa dan rasanya? | Fasa UI, konsistensi visual |
| `SOFTWARE-DESIGN-SPECIFICATION.md` | **Apa** yang mesti dilakukannya? | Keperluan GSD → fasa → pengesahan |
| `TECHNICAL-DESIGN-SPECIFICATION.md` | **Bagaimana** ia akan dibina? | Seni bina, model data, deployment |

### BUSINESS-DESIGN-SPECIFICATION.md — kenapa

- Kenyataan masalah: siapa yang merana, seberapa teruk, berapa kerap
- Pengguna sasaran dan segmen
- Matlamat + metrik kejayaan (apa maksud "berjaya" dari sudut perniagaan)
- Nilai jualan; harga/pendapatan jika ada
- Kekangan: bajet, tarikh akhir, undang-undang/kepatuhan

*Menentukan apa yang dibina langsung — dan dari apa v1 dipotong.*

### MARKETING-DESIGN-SPECIFICATION.md — jangkauan

- Positioning: ayat satu baris dan tagline
- Khalayak: di mana mereka, apa yang mereka respons
- Saluran + pelan pelancaran (media sosial, WhatsApp, risalah QR…)
- Ringkasan salinan landing page; tangkapan skrin/bahan demo

*Ditulis sebelum pelancaran, ia membolehkan AI membina landing page dan senarai app store untuk anda.*

### DESIGN.md — rupa dan rasa

- Jenama: nama, logo, warna, fon, nada suara
- UX: aliran pengguna, skrin, peta navigasi
- UI: komponen, peraturan susun atur, asas aksesibiliti

*Menjaga setiap fasa UI GSD kekal konsisten secara visual — tiada keputusan gaya butang diulang setiap fasa.*

### SOFTWARE-DESIGN-SPECIFICATION.md — apa

- Ciri sebagai mesti-ada / bagus-ada
- User stories berkriteria penerimaan
- Peranan/kebenaran, kes tepi, keadaan ralat
- Senarai "di luar skop" yang jelas

*The contract: GSD menukarkannya kepada keperluan → fasa, dan mengesahkan binaan berdasarkannya.*

### TECHNICAL-DESIGN-SPECIFICATION.md — bagaimana

- Seni bina (gambar rajah atau lakaran ASCII pun cukup)
- Stack + sebab (framework, pangkalan data, hosting)
- Model data, endpoint API, integrasi
- Auth/keselamatan, persekitaran, deployment, sandaran

*Menjawab soalan pelaksanaan agen sebelum soalan itu membazirkan token anda.*

---

## 4. Mulakan dengan tiga

Anda tidak perlu kelima-limanya pada hari pertama. Set minimum yang mencukupi untuk mula membina:

1. **BUSINESS-DESIGN-SPECIFICATION.md** — supaya keputusan skop ada alasan
2. **SOFTWARE-DESIGN-SPECIFICATION.md** — supaya GSD ada sesuatu untuk dibina dan disemak
3. **TECHNICAL-DESIGN-SPECIFICATION.md** — supaya pilihan pelaksanaan tidak dipersoalkan semula

Tambah **DESIGN.md** sebelum fasa yang berat UI, dan **MARKETING-DESIGN-SPECIFICATION.md** sebelum pelancaran. (Mana-mana tiga yang sepadan dengan milestone anda seterusnya pun boleh — pokoknya *yang ditulis mengatasi yang diingat*.)

---

## 5. Menggunakannya dengan OpenCode + GSD

1. **Draf dalam chat AI percuma** — mod interview (lihat [START.md](START.ms-MY.md)): biarkan AI bertanya soalan kepada anda sehingga setiap dokumen menjadi tajam.
2. **Simpan di akar folder projek** — nama `.md` huruf besar di atas; ia fail biasa, di-version bersama kod anda.
3. **Suapkan kepada GSD** — jalankan `/gsd-new-project` dalam projek dan tunjukkan spesifikasi itu; keperluan menjadi fasa, fasa menjadi kerja yang disahkan.
4. **Pastikan ia terus hidup** — bila realiti mengajar anda sesuatu, sunting spesifikasi *dahulu*, commit, kemudian biar GSD mengemas kini pelan. Sejarah git spesifikasi anda ialah log keputusan anda.

---

**Seterusnya:** tulis spesifikasi pertama anda dengan [START.md](START.ms-MY.md), sediakan alat dengan [INSTALL.md](INSTALL.ms-MY.md), kemudian bina dengan [GSD.md](GSD.ms-MY.md). Kembali ke [README](README.ms-MY.md).
