# START — Daripada Idea ke Spec dengan AI Chat Percuma

Bahasa Melayu | [English](START.md) · Kembali ke [README](README.ms-MY.md)

Sebelum menulis sebarang kod, anda perlukan masalah yang jelas dan spec bertulis. Alat AI chat percuma paling sesuai untuk sampai ke situ — panduan ini menunjukkan caranya.

---

## 1. Alat AI chat percuma

Mana-mana satu daripada ini sesuai untuk mengolah idea dan menulis spec:

| Alat | Pautan |
|------|--------|
| Microsoft Copilot | <https://copilot.microsoft.com> |
| Google Gemini | <https://gemini.google.com> |
| DeepSeek Chat | <https://chat.deepseek.com> |

> Tier percuma memadai — pengolahan masalah dan penulisan spec tidak memerlukan model berbayar.

---

## 2. Aliran kerja

1. **Mula dengan masalah seharian** — sesuatu yang menyusahkan anda atau orang yang anda kenal.
2. **Olah bersama AI chat** — gunakan *mod temu bual*: biarkan AI bertanya kepada *anda* sehingga idea menjadi tajam (lihat frasa ajaib di bawah).
3. **Tulis spec** — simpan hasilnya sebagai dokumen Markdown yang ringkas.
4. **Bina ia** — berikan spec kepada OpenCode + GSD dan biarkan workflow mengambil alih (lihat [GSD.md](GSD.md)).

---

## 3. Asas penjimatan token

Empat tabiat yang menjaga penggunaan AI anda supaya pantas dan jimat:

1. **Jangan tampal PDF — tukar kepada Markdown atau teks biasa dahulu.**
   Sebab: PDF memenuhi konteks dengan sisa susun atur dan menelan lebih banyak token.

2. **Tamatkan prompt anda dengan:** `ask me relevant questions`
   ```text
   ask me relevant questions
   ```
   Sebab: ia menyebabkan AI menemu bual anda untuk mendapatkan butiran yang anda terlupa — berbanding meneka dan menghasilkan output yang salah.

3. **Tampal petikan yang berkaitan sahaja, bukan keseluruhan dokumen.**
   Sebab: ruang konteks terhad; setiap baris yang tidak berkaitan membazirkan token dan tumpuan model.

4. **Satu topik bagi setiap perbualan — mulakan chat baharu untuk masalah baharu.**
   Sebab: topik yang bercampur mencemarkan konteks dan mengelirukan model.

---

## 4. Spec-driven development

**Spec-driven development** bermaksud menulis *apa* yang perlu dibina sebelum membina — kemudian memberikan dokumen itu kepada agen pengaturcara sebagai sumber kebenaran:

**masalah → senarai keperluan (mesti ada vs bagus jika ada) → aliran pengguna → dokumen spec ringkas → berikan kepada OpenCode + GSD**

Salin kerangka ini ke dalam chat AI anda (atau fail `.md` kosong) dan isikannya:

```markdown
# [Nama projek]

## Problem
[Satu dua ayat: siapa yang menghadapi masalah ini dan kenapa ia menyusahkan.]

## Requirements

### Must-have
- [Aplikasi tidak berfungsi tanpa ini]

### Nice-to-have
- [Boleh tunggu sehingga versi 2]

## User flow
1. [Pengguna membuka aplikasi dan melihat ...]
2. [Pengguna melakukan ... dan aplikasi ...]
3. [Pengguna akhirnya mendapat ...]

## Out of scope
- [Memang TIDAK membina ini, supaya v1 kecil]
```

Pastikan v1 kecil: 3–5 keperluan mesti-ada ialah milestone pertama yang sangat baik.

---

**Seterusnya:** pasang peralatan dengan [INSTALL.md](INSTALL.md), kemudian pelajari workflow pembinaan dalam [GSD.md](GSD.md). Kembali ke [README](README.ms-MY.md).
