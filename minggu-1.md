# Minggu 1 — Git & GitHub Basic Bootcamp: Kenalan & Instalasi

**Durasi:** ~2 jam (termasuk praktik)
**Target:** Peserta bisa install Git, konfigurasi, buat akun GitHub, buat repo pertama, dan lakukan commit pertama.

---

## Outline Sesi

| No | Topik | Waktu |
|----|-------|-------|
| 1 | Opening & ice breaking | 10 menit |
| 2 | Kenalan sama Terminal | 15 menit |
| 3 | Apa itu Git & GitHub | 15 menit |
| 4 | Kenapa version control penting | 10 menit |
| 5 | Istirahat / QnA | 10 menit |
| 6 | Instalasi Git & buat akun GitHub | 20 menit |
| 7 | Konfigurasi Git + praktik | 10 menit |
| 8 | Konsep dasar (Repo, Commit, Branch) | 15 menit |
| 9 | Praktik: Buat repo + commit pertama | 20 menit |
| 10 | Penutup & tugas minggu depan | 5 menit |

---

## 1. Opening & Ice Breaking (10 menit)

- Perkenalan diri mentor & peserta
- Tanya ke peserta: "Siapa yang pernah denger Git/GitHub? Siapa yang pernah pakai?"
- Jelaskan roadmap 6 minggu:

| Minggu | Topik |
|--------|-------|
| **1** | **Kenalan, instalasi, repo pertama** ← minggu ini |
| 2 | Alur kerja dasar: add, commit, push, pull |
| 3 | Branching & kerja paralel |
| 4 | Pull Request & Code Review |
| 5 | Merge Conflict & fitur GitHub |
| 6 | Simulasi kerja tim & review |

---

## 2. Kenalan Sama Terminal (15 menit)

**Referensi:** `materi-git-github.md` bagian 0

### Yang perlu dijelaskan:

- Terminal = aplikasi kasih perintah lewat ketikan (bukan "hacker mode")
- Cara buka:
  - **Windows:** Start → ketik `cmd` → Enter
  - **Mac:** Spotlight (`Cmd+Space`) → ketik `Terminal` → Enter
- Aturan dasar: klik di dalam jendela → ketik perintah → tekan Enter
- Kalau salah? Gak masalah, cuma muncul error, coba lagi

### Praktik singkat di kelas:

Suruh semua peserta buka terminal, lalu ketik:
```bash
echo "Halo Dunia"
```
Pastikan semua bisa jalan. Ini bikin peserta gak takut sama terminal.

---

## 3. Apa itu Git & GitHub (15 menit)

**Referensi:** `materi-git-github.md` bagian 1

### Yang perlu dijelaskan:

**Git:**
- Program di laptop yang mencatat setiap perubahan file
- Analogi: seperti "undo history" tapi lebih powerful
- Dibuat Linus Torvalds (pencipta Linux) tahun 2005
- Jalan offline, gak butuh internet

**GitHub:**
- Website (github.com) tempat upload hasil kerja Git
- Bisa dilihat orang lain, bisa kerja bareng tim
- Butuh internet

**Perbedaan kunci (simplifikasi):**

> Git = alat di laptop kamu
> GitHub = tempat online buat naruh & berbagi hasil kerja alat itu

### Analogi yang bisa dipakai:
- Git = kamera yang ambil foto kondisi file
- GitHub = album foto online yang bisa dilihat orang lain

---

## 4. Kenapa Version Control Penting (10 menit)

**Referensi:** `materi-git-github.md` bagian 2

### Poin-poin yang perlu disampaikan:

1. **Riwayat tersimpan otomatis** — bisa lihat file dulu kayak apa, balik ke versi lama
2. **Kerja bareng tanpa saling tindih** — kalau dua orang edit file yang sama lewat WhatsApp, pasti ada yang ketimpa. Git gak gitu.
3. **Eksperimen tanpa takut merusak** — lewat branching (minggu 3), bisa coba hal baru di cabang terpisah
4. **Standar industri** — hampir semua perusahaan software pakai Git & GitHub

### Contoh konkret (biar peserta relate):

```
tugas_final.docx
tugas_final_revisi.docx
tugas_final_revisi2_FIX.docx
tugas_final_revisi2_FIX_beneran.docx
```

> "Ini yang terjadi kalau gak pakai Git. Pakai Git, satu file aja, tapi semua riwayatnya tercatat."

---

## 5. Istirahat / QnA (10 menit)

Buka sesi tanya jawab. Biasanya peserta sudah mulai ada pertanyaan teknis di tahap ini.

---

## 6. Instalasi Git & Buat Akun GitHub (20 menit)

**Referensi:** `materi-git-github.md` bagian 3.1 - 3.3

### Instalasi Git:

1. Buka [git-scm.com/downloads](https://git-scm.com/downloads)
2. Download sesuai OS (Windows/Mac/Linux)
3. Install seperti biasa: Next → Next → Install → Finish
4. **Biarkan semua opsi default selama instalasi**

### Cek instalasi:

```bash
git --version
```

Harus muncul `git version 2.x.x`. Kalau error, tutup terminal, buka lagi, coba lagi.

### Buat akun GitHub:

1. Buka [github.com](https://github.com)
2. Klik **Sign up**
3. Isi email, password, username
4. Verifikasi email

### ⚠️ Troubleshooting yang sering muncul:

| Masalah | Solusi |
|---------|--------|
| `git is not recognized...` | Tutup cmd, buka lagi. Kalau masih gagal, install ulang Git |
| GitHub gak bisa sign up | Coba email lain, atau cek koneksi internet |
| Lupa password GitHub | Pakai fitur "Forgot password" |

---

## 7. Konfigurasi Git + Praktik (10 menit)

**Referensi:** `materi-git-github.md` bagian 3.4

### Yang dilakukan:

Setelah Git terinstall, kasih tahu Git "siapa kamu":

```bash
git config --global user.name "Nama Kamu"
git config --global user.email "email_github_kamu@email.com"
```

> **Penting:** Email harus sama dengan email akun GitHub yang baru dibuat.

### Cek konfigurasi:

```bash
git config user.name
git config user.email
```

### Praktik di kelas:

Semua peserta langsung jalankan perintah ini di terminal masing-masing. Mentor bisa jalan-jalan cek laptop peserta.

---

## 8. Konsep Dasar yang Wajib Dipahami (15 menit)

**Referensi:** `materi-git-github.md` bagian 4

### Istilah yang perlu dijelaskan:

**Repository (Repo)**
> Folder project yang dilacak riwayat perubahannya oleh Git.
> - Local = di laptop kamu
> - Remote = di GitHub (online)

**Commit**
> "Titik simpan" perubahan, lengkap dengan catatan (commit message).
> Analogi: save point di video game — bisa balik ke titik itu kapan saja.

**Branch (Cabang)**
> Jalur pengembangan terpisah dari kode utama.
> - `main` = jalan raya utama (stabil, sudah jadi)
> - Branch baru = jalan cabang (buat eksperimen, gak ganggu main)
> *(Branching akan dibahas lebih dalam di minggu 3)*

**Staging Area**
> Area "tunggu" sebelum perubahan jadi commit permanen.
> ```
> Working Directory → Staging Area → Repository (Commit)
> (file yang kamu edit)  (ditandai siap simpan)  (riwayat permanen)
> ```

### Analogi untuk peserta:

> Kamu lagi nulis skripsi. `main` itu draft final yang udah di-ACC. Kalau mau coret-coret, jangan langsung di draft final — fotocopy dulu (branch), coret-coret di fotocopy-annya, baru kalau udah fix, salin balik ke draft asli.

---

## 9. Praktik: Buat Repo Pertama & Commit Pertama (20 menit)

Ini bagian paling penting — peserta harus langsung praktik.

### Skenario: Mulai dari nol

**Langkah 1: Buat folder project di Terminal**

```bash
mkdir latihan-git
cd latihan-git
```

**Langkah 2: Jadikan folder ini repo Git**

```bash
git init
```

> Ini bikin folder tersembunyi `.git` — di situ semua riwayat Git disimpan. Jangan dihapus.

**Langkah 3: Buat repo kosong di GitHub**

1. Login ke github.com
2. Klik tombol **+** → **New repository**
3. Isi nama (samakan sama nama folder: `latihan-git`)
4. **Jangan** centang README / .gitignore / license
5. Klik **Create repository**

**Langkah 4: Hubungkan repo lokal ke GitHub**

```bash
git remote add origin https://github.com/USERNAME/latihan-git.git
```

Cek sudah terhubung:
```bash
git remote -v
```

**Langkah 5: Buat file pertama**

```bash
echo "Halo Dunia" > readme.md
```

**Langkah 6: Cek status**

```bash
git status
```

Akan muncul file `readme.md` berwarna merah (belum di-add).

**Langkah 7: Tandai file siap disimpan**

```bash
git add readme.md
```

Cek lagi `git status` — sekarang hijau (sudah masuk staging area).

**Langkah 8: Commit!**

```bash
git commit -m "First Commit"
```

**Langkah 9: Push ke GitHub**

```bash
git push -u origin main
```

**Langkah 10: Buka GitHub di browser, cek hasilnya! 🎉**

File `readme.md` harusnya sudah muncul di repo GitHub.

---

## 10. Penutup & Tugas Minggu Depan (5 menit)

### Ringkasan yang perlu diingat peserta:

| Konsep | Arti |
|--------|------|
| Git | Program di laptop yang catat perubahan file |
| GitHub | Website online buat simpan & berbagi hasil kerja Git |
| Repository | Folder project yang dilacak Git |
| Commit | Titik simpan perubahan |
| `git init` | Jadikan folder jadi repo Git |
| `git add` | Tandai file siap disimpan |
| `git commit -m "pesan"` | Simpan perubahan sebagai riwayat |
| `git push` | Kirim ke GitHub |

### Tugas sebelum minggu ke-2:

1. **Pastikan Git sudah terinstall** dan konfigurasi `user.name` & `user.email` sudah di-set
2. **Buat akun GitHub** (kalau belum)
3. **Buat 1 repo baru** di GitHub, clone ke laptop, tambahin 1 file, commit, dan push
4. **Eksplorasi terminal** — coba beberapa perintah dasar:
   - `pwd` → lihat folder mana kamu berada
   - `ls` → lihat isi folder (Mac/Linux) atau `dir` (Windows)
   - `cd nama-folder` → pindah ke folder lain

### Referensi untuk belajar mandiri:

- Buka kembali file `materi-git-github.md` di repo ini, baca bagian 0 sampai 6
- Kalau stuck, tanya di grup bootcamp

---

*Untuk mentor: file gambar yang tersedia di folder `images/` bisa dipakai untuk presentasi. Lihat daftar lengkap di repo.*
