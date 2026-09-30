# GSD — Panduan Ringkas Workflow

Bahasa Melayu | [English](GSD.md) · Kembali ke [README](README.ms-MY.md)

**GSD (Get Shit Done)** ialah workflow pembangunan berasaskan spec yang berjalan di dalam [OpenCode](INSTALL.md). Anda nyatakan hasil yang diingini; GSD membuat kajian, merancang, membina, dan menyemak — dengan anda meluluskan pada ketika yang tepat.

---

## Cara Ia Berfungsi

Perjalanan penuh daripada "saya ada idea" sehingga "siap dihantar" — enam langkah:

### 1. Cipta projek

```text
/gsd-new-project
```

Satu aliran berpandukan: Soalan → Kajian (agen selari) → Keperluan (v1 / v2 / di luar skop) → Peta Jalan (fasa). Ia mencipta `PROJECT.md`, `REQUIREMENTS.md`, `ROADMAP.md`, `STATE.md`, dan `.planning/research/`.

Dah ada kod? Jalankan `/gsd-map-codebase` dahulu supaya GSD memahami apa yang sedia ada.

### 2. Bincang fasa

```text
/gsd-discuss-phase 1
```

Merakam keutamaan pelaksanaan anda **sebelum** perancangan. GSD mengenal pasti bahagian kabur bagi jenis fasa anda — visual (susun atur, kepadatan, interaksi), API (format respons, flags), kandungan (struktur, nada), atau organisasi (pengelompokan, penamaan) — dan bertanya tentangnya. Mencipta `{phase}-CONTEXT.md`.

### 3. Rancang fasa

```text
/gsd-plan-phase 1
```

Membuat kajian tentang codebase dan ekosistem anda (dibimbing oleh `CONTEXT.md`), kemudian mencipta 2–3 pelan tugas atom dalam format XML berstruktur, dan menyemak setiap pelan terhadap keperluan secara berulang. Mencipta `{phase}-RESEARCH.md` dan `{phase}-{N}-PLAN.md`. Setiap pelan cukup kecil untuk dilaksanakan dalam satu context window baharu.

### 4. Laksanakan fasa

```text
/gsd-execute-phase 1
```

Melaksanakan pelan mengikut gelombang tertib kebergantungan — pelan yang bekerja secara selari, yang bergantung secara berurutan. Setiap pelan berjalan dalam context baharu, setiap task mendapat commit Git atom, dan hasilnya disemak terhadap matlamat pelan. Mencipta `{phase_num}-{N}-SUMMARY.md` dan `{phase_num}-VERIFICATION.md`.

### 5. Semak hasil kerja

```text
/gsd-verify-work 1
```

Ujian penerimaan pengguna: GSD menyenaraikan hasil kerja yang boleh diuji dan membawa anda menyemaknya satu persatu, membuat diagnosis automatik atas apa-apa yang gagal, dan mencipta pelan pembetulan. Mencipta `{phase}-UAT.md`.

### 6. Ulang dan tamatkan

```text
/gsd-complete-milestone
```

Ulang bincang → rancang → laksanakan → semak bagi setiap fasa. Apabila milestone siap, `/gsd-complete-milestone` mengarkibkan kerja dan menandakan keluaran (release tag); gunakan `/gsd-new-milestone` untuk memulakan versi seterusnya.

---

## Mod pantas

```text
/gsd-quick
```

Untuk task ad-hoc yang tidak memerlukan satu fasa penuh — dengan kualiti planner + executor yang sama, tetapi melangkau langkah kajian/penyemak/pengesah. Task pantas direkodkan dalam `.planning/quick/`, bukan dalam fasa.

Gunakannya untuk: pembetulan bug, ciri kecil, perubahan konfigurasi, task sekaliguna.

---

## Kenapa Ia Berfungsi

### Context Engineering

GSD mengekalkan kualiti dengan memberi OpenCode tepat konteks yang diperlukan — dan tiada lagi:

- `PROJECT.md` — visi, sentiasa dimuatkan.
- `research/` — pengetahuan ekosistem yang dikumpulkan lebih awal.
- `REQUIREMENTS.md` — skop v1/v2, supaya scope creep kelihatan jelas.
- `ROADMAP.md` — ke mana anda menuju dan apa yang sudah siap.
- `STATE.md` — keputusan, sekatan, dan ingatan merentas sesi.
- `PLAN.md` — satu task atom dengan pengesahan.
- `SUMMARY.md` — apa yang berlaku, untuk agen seterusnya.
- `todos/` — idea yang dirakam menunggu giliran.

Setiap fail ada had saiz, berdasarkan titik di mana kualiti OpenCode terbukti merosot.

### Format Prompt XML

Setiap pelan ialah XML berstruktur dengan medan `name`, `files`, `action`, `verify`, dan `done`. Maksudnya: arahan yang tepat dan bukan tanggapan, tiada tekaan, dan pengesahan dibina ke dalam setiap task.

### Orkestrasi Berbilang Agen

Orkestrator nipis melahirkan subagen khusus: 4 penyelidik selari, gelung planner + checker, executor selari yang setiap satunya mendapat context baharu sebanyak 200k, kemudian verifier dan debugger. Oleh kerana kerja sebenar berlaku dalam konteks subagen baharu, context utama anda kekal pada 30–40% penuh.

### Commit Git Atom

Setiap task dicommit serta-merta dengan commit tersendiri. `git bisect` menjumpai task yang gagal dengan tepat, mana-mana task boleh dikembalikan secara berasingan, dan sejarah repo mudah dibaca.

### Modular secara Reka Bentuk

Tambah fasa apabila perlu, selitkan kerja mendesak di antara fasa, tamatkan milestone, dan ubah suai pelan — tanpa membina semula apa-apa.

---

## Apa seterusnya

Perlu pasang peralatan dahulu? Ikuti [INSTALL.md](INSTALL.md) — kemudian kembali dan jalankan `/gsd-new-project`. Konteks lanjut dalam [START.md](START.md) (AI chat percuma + menulis spec anda) dan [README](README.ms-MY.md).
