# Minggu 2 — Alur Kerja Dasar: Add, Commit, Push, Pull

**Durasi:** ~2 jam (termasuk praktik)
**Target:** Paham alur kerja Git (add → commit → push), biasa pakai `git status`, paham staging area, dan bisa tarik perubahan dari GitHub (`git pull`).

---

## Outline Sesi

| No | Topik | Waktu |
|----|-------|-------|
| 1 | Recap minggu 1 & ice breaking | 10 menit |
| 2 | Konsep Staging Area secara visual | 10 menit |
| 3 | Alur kerja dasar: add, commit, push | 20 menit |
| 4 | Praktik: Edit file, add, commit, push | 20 menit |
| 5 | Istirahat / QnA | 10 menit |
| 6 | `git pull` — ambil perubahan dari GitHub | 15 menit |
| 7 | Commit message yang baik vs buruk | 10 menit |
| 8 | Praktik: Simulasi edit → commit → push → pull | 20 menit |
| 9 | Kesalahan umum & cara mengatasinya | 10 menit |
| 10 | Penutup & tugas minggu depan | 5 menit |

---

## 1. Recap Minggu 1 & Ice Breaking (10 menit)

### Tanya ke peserta:

- "Siapa yang sudah install Git? Coba ketik `git --version` sekarang."
- "Siapa yang sudah punya akun GitHub?"
- "Siapa yang sudah buat repo pertama & push ke GitHub?"

### Ringkasan cepat minggu 1:

| Topik | Ingat lagi |
|-------|-----------|
| Terminal | Aplikasi kasih perintah lewat ketikan |
| Git | Program di laptop yang catat perubahan file |
| GitHub | Website online buat simpan & berbagi hasil kerja Git |
| `git init` | Jadikan folder jadi repo Git |
| `git add` | Tandai file siap disimpan |
| `git commit -m "pesan"` | Simpan perubahan sebagai riwayat |
| `git push` | Kirim ke GitHub |

> "Minggu ini kita bakal lebih dalam soal alur add → commit → push, dan belajar satu perintah baru: `git pull`."

---

## 2. Konsep Staging Area Secara Visual (10 menit)

**Referensi:** `materi-git-github.md` bagian 4.5

### Penjelasan:

Banyak pemula bingung soal staging area. Mari visualisasikan:

```
┌─────────────────┐    git add     ┌─────────────────┐    git commit    ┌─────────────────┐
│ Working Directory│ ────────────→ │  Staging Area   │ ────────────→  │   Repository    │
│                  │               │                  │                │                  │
│ (folder project  │               │ (file yang       │                │ (riwayat yang    │
│  yang kamu edit) │               │  "ditandai"      │                │  udah permanen   │
│                  │               │  siap disimpan)  │                │  tersimpan)      │
└─────────────────┘               └─────────────────┘                └─────────────────┘
```

### Analogi sederhana:

> Bayangkan kamu lagi nyusun album foto.
>
> - **Working Directory** = semua foto yang ada di laptop kamu
> - **Staging Area** = foto-foto yang kamu pilih & masukin ke dalam Map (belum dicetak)
> - **Repository** = album foto yang sudah jadi, dicetak, dan permanen

### Kenapa ada staging area?

- **Selektif**: Kamu bisa pilih file mana yang mau di-commit (gak harus semua sekaligus)
- **Porses staging**: Kamu bisa mengelompokkan perubahan ke commit yang berbeda-beda
- **Review sebelum commit**: Bisa cek dulu file mana yang masuk sebelum commit

### Cara cek status:

```bash
git status
```

Perintah ini menunjukkan:
- File mana yang berubah (merah = belum di-add)
- File mana yang sudah di-staging (hijau = sudah di-add)
- File mana yang sudah di-commit

---

## 3. Alur Kerja Dasar: Add, Commit, Push (20 menit)

**Referensi:** `materi-git-github.md` bagian 6

### Alur lengkap:

```
1. Edit file           (di Working Directory — folder biasa di laptop kamu)
2. git add             (pindahkan ke Staging Area)
3. git commit          (simpan sebagai riwayat)
4. git push            (kirim ke GitHub)
```

### Langkah 1: Cek Status

```bash
git status
```

Kalau belum ada perubahan, hasilnya bersih. Kalau sudah ada file berubah, akan muncul daftar file.

### Langkah 2: `git add` — Menandai File Siap Disimpan

```bash
git add nama_file.txt        # tambah satu file spesifik
git add .                    # tambah SEMUA file yang berubah (titik artinya "semua")
```

Setelah `git add`, jalankan `git status` lagi — file yang tadi merah akan berubah jadi hijau.

**Tips:**
- `git add .` = tambah semua file yang berubah
- `git add nama-file.txt` = tambah file tertentu saja
- `git add *.txt` = tambah semua file .txt

### Langkah 3: `git commit` — Menyimpan Perubahan

```bash
git commit -m "pesan commit"
```

`-m` diikuti pesan singkat yang menjelaskan **apa** yang diubah.

**Contoh:**

```bash
git commit -m "feat: tambahkan file readme"
```

### Langkah 4: `git push` — Mengirim ke GitHub

```bash
git push origin main
```

Ini mengirim semua commit yang belum ter-upload ke branch `main` di GitHub.

**Untuk push pertama kali** di branch baru, pakai:

```bash
git push -u origin main
```

Setelah itu, cukup `git push` saja (sudah tahu lokasi push-nya).

---

## 4. Praktik: Edit File, Add, Commit, Push (20 menit)

### Skenario praktik:

Kita akan membuat perubahan pertama di repo yang sudah dibuat minggu lalu.

**Langkah 1: Pastikan berada di folder project**

```bash
cd latihan-git
```

**Langkah 2: Cek status**

```bash
git status
```

Pastikan branch `main` dan tidak ada perubahan (bersih).

**Langkah 3: Buat file baru**

```bash
echo "Selamat datang di Komandro" > halo.md
```

**Langkah 4: Cek status lagi**

```bash
git status
```

Akan muncul file `halo.md` berwarna merah (untracked / belum di-add).

**Langkah 5: Tandai file siap disimpan**

```bash
git add halo.md
```

**Langkah 6: Cek status lagi**

```bash
git status
```

Sekarang `halo.md` berwarna hijau (sudah masuk staging area).

**Langkah 7: Commit!**

```bash
git commit -m "feat: tambahkan file halo.md"
```

**Langkah 8: Push ke GitHub**

```bash
git push origin main
```

**Langkah 9: Buka GitHub di browser, cek hasilnya!**

File `halo.md` harusnya sudah muncul di repo GitHub.

---

## 5. Istirahat / QnA (10 menit)

Buka sesi tanya jawab. Pastikan semua peserta sudah berhasil push file baru ke GitHub.

---

## 6. `git pull` — Ambil Perubahan dari GitHub (15 menit)

**Referensi:** `materi-git-github.md` bagian 6 (Langkah 5)

### Kenapa perlu `git pull`?

Kalau kamu kerja tim, teman kamu mungkin sudah push perubahan ke GitHub. Supaya laptop kamu sinkron, kamu perlu "tarik" perubahan itu ke komputer kamu.

### Cara pakai:

```bash
git pull origin main
```

Perintah ini:
1. Mengambil riwayat commit terbaru dari GitHub
2. Langsung menggabungkannya ke branch lokal kamu

### Kapan harus pakai `git pull`?

- **Sebelum mulai kerja** — supaya kamu kerja dari versi terbaru
- **Setelah teman push** — supaya kamu punya perubahan terbaru
- **Sebelum bikin branch baru** — supaya branch baru dari versi terbaru

### Praktik singkat:

1. Buka repo di GitHub lewat browser
2. Klik tombol **pencil/edit** di file `readme.md` atau `halo.md`
3. Edit sedikit isinya, lalu klik **Commit changes**
4. Kembali ke Terminal, jalankan:

```bash
git pull origin main
```

5. Cek file di folder project — perubahan harusnya sudah muncul!

---

## 7. Commit Message yang Baik vs Buruk (10 menit)

### Kenapa penting?

Commit message adalah "catatan sejarah" dari project kamu. Kalau jelek, orang (termasuk kamu sendiri nanti) gak akan paham perubahan apa yang dilakukan.

### Contoh commit message yang baik vs kurang jelas:

| ✅ Jelas | ❌ Kurang jelas |
|---|---|
| `fix: perbaiki tombol submit yang tidak berfungsi` | `update` |
| `feat: tambahkan validasi form pendaftaran` | `asdasd` |
| `docs: perbarui panduan instalasi di README` | `fix lagi` |
| `style: rapikan format kode di main.js` | `udah` |
| `refactor: pisahkan fungsi authentication` | `edit` |

### Konvensi penamaan commit (Conventional Commits):

Gunakan prefix untuk menjelaskan **jenis** perubahan:

```
feat:     → fitur baru
fix:      → perbaikan bug
docs:     → dokumentasi
style:    → format/style (gak ngubah fungsi)
refactor: → ubah struktur kode (gak ngubah fungsi)
test:     → tambah/ubah test
chore:    → maintenance (config, dependencies, dll)
```

### Tips:

- **Singkat tapi jelas** — cukup 1 baris, gak perlu panjang lebar
- **Pakai bahasa Inggris** — standar industri
- **Jangan pakai pesan generik** seperti `update`, `fix`, `changes`
- **Gunakan imperative mood** — "tambahkan", bukan "menambahkan"

---

## 8. Praktik: Simulasi Edit → Commit → Push → Pull (20 menit)

### Skenario:

Kita simulasi kerja tim di mana kamu dan "teman" (mentor) edit file yang sama.

### Langkah untuk peserta:

**Langkah 1: Buat perubahan pertama**

```bash
echo "Baris pertama dari readme" > notes.md
git add notes.md
git commit -m "feat: tambahkan file notes"
git push origin main
```

**Langkah 2: Mentor edit file yang sama di GitHub**

Mentor akan edit file `notes.md` langsung di GitHub (tambahkan baris baru).

**Langkah 3: Peserta tarik perubahan**

```bash
git pull origin main
```

**Langkah 4: Cek file `notes.md`**

Buka file `notes.md` di text editor. Harusnya sudah ada perubahan dari mentor.

**Langkah 5: Peserta tambah perubahan lagi**

```bash
echo "Baris kedua dari peserta" >> notes.md
git add notes.md
git commit -m "feat: tambahkan baris kedua"
git push origin main
```

### Yang dipelajari dari praktik ini:

- Alur edit → add → commit → push
- Cara pakai `git pull`
- Bagaimana perubahan dari banyak orang bisa digabungkan
- Pentingnya `git pull` sebelum mulai kerja

---

## 9. Kesalahan Umum & Cara Mengatasinya (10 menit)

**Referensi:** `materi-git-github.md` bagian 12

| Masalah | Penyebab | Solusi |
|---|---|---|
| `fatal: not a git repository` | Belum `git init`/`clone`, atau salah folder | Pastikan berada di folder yang benar |
| `rejected... failed to push` | Ada perubahan di remote yang belum ditarik | `git pull origin main` dulu, baru push lagi |
| `Permission denied` saat push | Autentikasi GitHub belum benar | Cek koneksi akun GitHub (pakai Personal Access Token/SSH) |
| File besar/salah ikut ter-commit | Lupa buat `.gitignore` | Buat file `.gitignore`, tambahkan nama file yang tidak perlu dilacak |
| Salah edit di branch yang salah | Lupa cek branch aktif | Selalu `git status`/`git branch` sebelum mulai edit |
| Lupa `git pull` sebelum kerja | Perubahan teman belum di-pull | Selalu `git pull origin main` sebelum mulai edit |

---

## 10. Penutup & Tugas Minggu Depan (5 menit)

### Ringkasan yang perlu diingat peserta:

| Konsep | Arti |
|--------|------|
| Working Directory | Folder project yang kamu edit sehari-hari |
| Staging Area | Area "tunggu" tempat file ditandai sebelum commit |
| Repository | Riwayat permanen yang sudah di-commit |
| `git add .` | Tandai semua file siap disimpan |
| `git commit -m "pesan"` | Simpan perubahan sebagai riwayat |
| `git push origin main` | Kirim commit ke GitHub |
| `git pull origin main` | Tarik perubahan terbaru dari GitHub |
| `git status` | Cek status file (berubah/belum di-add/sudah di-commit) |

### Tugas sebelum minggu ke-3:

1. **Praktik alur add → commit → push** minimal 5 kali di repo yang sama
2. **Buat minimal 3 commit** dengan commit message yang berbeda-beda (pakai konvensi `feat:`, `fix:`, `docs:`)
3. **Coba `git pull`** — edit file langsung di GitHub lewat browser, lalu tarik ke komputer pakai `git pull`
4. **Buat branch baru** di GitHub lewat browser (kita akan bahas lebih dalam minggu depan)
5. **Eksplorasi** — coba `git log --oneline` untuk melihat riwayat commit

### Pertanyaan refleksi untuk peserta:

- "Kapan kamu harus pakai `git pull`?"
- "Apa beda `git add .` dan `git add nama-file.txt`?"
- "Kenapa commit message harus jelas?"

---

## Referensi Lanjutan

- Buka kembali `materi-git-github.md` bagian 4, 5, dan 6
- Minggu depan kita bahas **Branching & Kerja Paralel** — bagian paling seru!

---

*Untuk mentor: file gambar yang tersedia di folder `images/` bisa dipakai untuk presentasi. Lihat daftar lengkap di repo.*
