# Minggu 3 — Branching: Kerja Paralel Tanpa Saling Ganggu

**Durasi:** ~2 jam (termasuk praktik)
**Target:** Paham konsep branch, bisa buat branch baru, pindah branch, push branch ke GitHub, dan merge branch ke main.

---

## Outline Sesi

| No | Topik | Waktu |
|----|-------|-------|
| 1 | Recap minggu 2 & ice breaking | 10 menit |
| 2 | Kenapa perlu branch? | 10 menit |
| 3 | Perintah dasar branching | 15 menit |
| 4 | Alur kerja dengan branch — contoh lengkap | 15 menit |
| 5 | Konvensi penamaan branch | 5 menit |
| 6 | Istirahat / QnA | 10 menit |
| 7 | Praktik: Bikin fitur di branch baru | 20 menit |
| 8 | Merge branch ke main | 15 menit |
| 9 | Hapus branch yang sudah selesai | 5 menit |
| 10 | Kesalahan umum & tips | 10 menit |
| 11 | Penutup & tugas minggu depan | 5 menit |

---

## 1. Recap Minggu 2 & Ice Breaking (10 menit)

### Tanya ke peserta:

- "Siapa yang sudah push minimal 5 kali ke GitHub?"
- "Siapa yang sudah coba `git pull`?"
- "Apa yang terjadi kalau lupa `git pull` sebelum kerja?"

### Ringkasan minggu 1 & 2:

| Konsep | Arti |
|--------|------|
| `git add` | Tandai file siap disimpan (masuk staging area) |
| `git commit -m "pesan"` | Simpan perubahan sebagai riwayat permanen |
| `git push` | Kirim commit ke GitHub |
| `git pull` | Tarik perubahan terbaru dari GitHub |
| `git status` | Cek status file |
| Commit message yang baik | Pakai prefix: `feat:`, `fix:`, `docs:`, dll |

> "Minggu ini kita belajar sesuatu yang lebih powerful: **branching** — bikin jalur terpisah buat kerja tanpa ganggu kode utama."

---

## 2. Kenapa Perlu Branch? (10 menit)

**Referensi:** `materi-git-github.md` bagian 7.1

### Analogi sederhana:

> Bayangkan `main` itu draft final skripsi yang udah di-ACC.
>
> Kalau kamu mau coba-coba coret-coret, **jangan langsung edit di draft final**.
>
> Kamu fotocopy dulu (branch), coret-coret di fotocopy-annya. Kalau udah fix, baru salin balik ke draft asli.

### Skenario tanpa branch:

```
Kamu: "Gw mau coba tambahin fitur translate inggris"
→ Edit langsung di main
→ Kodenya error!
→ Main jadi rusak
→ Temen gak bisa kerja karena main error
→ 😱
```

### Skenario dengan branch:

```
Kamu: "Gw mau coba tambahin fitur translate inggris"
→ Bikin branch baru: translate-inggris
→ Kerja di situ sepuasnya
→ Kalau berhasil, merge ke main
→ Kalau gagal, buang branch-nya, main aman
→ 😎
```

### Poin kunci:

| Tanpa Branch | Dengan Branch |
|---|---|
| Semua orang edit di `main` | Masing-masing punya branch sendiri |
| Kalau error, semua terdampak | Error hanya di branch sendiri |
| Sulit koordinasi | Kerja paralel tanpa ganggu |
| Merge jadi rumit | Merge lebih rapi & terkontrol |

---

## 3. Perintah Dasar Branching (15 menit)

**Referensi:** `materi-git-github.md` bagian 7.2

### Melihat branch yang ada:

```bash
git branch
```

Hasil default (belum bikin branch lain):

```
* main
```

Tanda `*` artinya itu branch yang aktif (kamu berada di situ sekarang).

### Membuat branch baru sekaligus pindah ke situ:

```bash
git switch -c nama-branch
```

Contoh:

```bash
git switch -c feat/translate-inggris
```

Pesan yang muncul:

```
Switched to a new branch 'feat/translate-inggris'
```

### Pindah ke branch lain:

```bash
git switch main                    # balik ke main
git switch feat/translate-inggris  # balik ke branch fitur
```

### Ringkasan perintah:

| Perintah | Fungsi |
|----------|--------|
| `git branch` | Lihat semua branch |
| `git branch nama-branch` | Buat branch baru (tapi belum pindah) |
| `git switch -c nama-branch` | Buat branch baru + pindah ke situ |
| `git switch nama-branch` | Pindah ke branch yang sudah ada |
| `git branch -d nama-branch` | Hapus branch (yang sudah di-merge) |

### ⚠️ Penting: Cek branch aktif sebelum edit!

```bash
git branch
```

Pastikan tanda `*` ada di branch yang benar sebelum mulai edit file. Ini sering bikin masalah kalau lupa!

---

## 4. Alur Kerja dengan Branch — Contoh Lengkap (15 menit)

**Referensi:** `materi-git-github.md` bagian 7.3

### Langkah lengkap dari nol:

```bash
# 1. Pastikan mulai dari main dan sudah versi terbaru
git switch main
git pull origin main

# 2. Buat branch baru khusus untuk fitur
git switch -c feat/translate-inggris

# 3. Edit file seperti biasa
echo "Welcome to Komandro" >> readme.md

# 4. Commit perubahan
git add .
git commit -m "feat: tambahkan terjemahan inggris"

# 5. Push branch BARU ke GitHub (bukan ke main!)
git push -u origin feat/translate-inggris
```

### Yang terjadi di GitHub:

Setelah langkah 5, buka repo di GitHub. Akan ada dropdown branch baru bernama `feat/translate-inggris`.

**Poin penting:** Push ke branch `feat/translate-inggris` **tidak mengubah** isi `main` sama sekali!

```
main                    → masih sama seperti sebelumnya
feat/translate-inggris  → ada perubahan baru
```

### Visualisasi:

```
main:      A ─ B ─ C
                    \
feat/               D ─ E
```

`main` tetap di `C`, branch fitur mulai dari `C` dan jalan sendiri sampai `D` dan `E`.

---

## 5. Konvensi Penamaan Branch (5 menit)

**Referensi:** `materi-git-github.md` bagian 7.4

Supaya rapi kalau kerja tim, pakai format:

```
feat/nama-fitur       → untuk fitur baru
fix/nama-bug          → untuk perbaikan bug
docs/nama-dokumen     → untuk dokumentasi
```

### Contoh:

| Branch | Untuk |
|--------|-------|
| `feat/translate-inggris` | Fitur terjemahan bahasa Inggris |
| `fix/tombol-login-error` | Perbaikan tombol login yang error |
| `docs/update-readme` | Update dokumentasi README |
| `feat/halaman-profil` | Fitur halaman profil baru |
| `fix/validasi-form` | Perbaikan validasi form |

### Tips penamaan:

- **Pakai huruf kecil** semua
- **Pakai strip `-`** sebagai pemisah (bukan spasi atau underscore)
- **Singkat tapi jelas** — langsung tahu isinya apa
- **Jangan pakai nama branch**: `test`, `cobain`, `abc123`

---

## 6. Istirahat / QnA (10 menit)

Buka sesi tanya jawab. Pastikan semua peserta paham kenapa branch diperlukan.

---

## 7. Praktik: Bikin Fitur di Branch Baru (20 menit)

### Skenario praktik:

Kita akan membuat fitur baru di branch terpisah, lalu push ke GitHub.

### Langkah untuk peserta:

**Langkah 1: Mulai dari main**

```bash
git switch main
git pull origin main
```

**Langkah 2: Buat branch baru**

```bash
git switch -c feat/tambah-bio
```

**Langkah 3: Cek branch aktif**

```bash
git branch
```

Pastikan tanda `*` di `feat/tambah-bio`.

**Langkah 4: Edit file**

```bash
echo "Saya adalah peserta Komandro 2026" > bio.md
```

**Langkah 5: Commit**

```bash
git add bio.md
git commit -m "feat: tambahkan file bio.md"
```

**Langkah 6: Push branch baru ke GitHub**

```bash
git push -u origin feat/tambah-bio
```

**Langkah 7: Cek di GitHub**

Buka repo di GitHub lewat browser. Klik dropdown branch — `feat/tambah-bio` harusnya sudah muncul.

**Langkah 8: Cek main tetap aman**

Klik branch `main` di GitHub. File `bio.md` **tidak ada** di `main` — karena kita push ke branch `feat/tambah-bio`.

---

## 8. Merge Branch ke Main (15 menit)

**Referensi:** `materi-git-github.md` bagian 8

### Kenapa perlu merge?

Branch fitur sudah selesai dikerjakan. Sekarang saatnya masukin ke `main` supaya semua orang bisa pakai.

### Cara merge via Terminal:

```bash
# 1. Pindah ke branch tujuan (main)
git switch main

# 2. Pastikan main sudah versi terbaru
git pull origin main

# 3. Gabungkan branch fitur ke main
git merge feat/tambah-bio

# 4. Push main yang sudah di-merge
git push origin main
```

### Cara merge via Pull Request (GitHub):

Cara ini lebih disarankan untuk kerja tim karena ada proses review.

1. Buka repo di GitHub
2. Klik tab **Pull requests**
3. Klik **New pull request**
4. Pilih branch: **base** = `main`, **compare** = `feat/tambah-bio`
5. Isi judul & deskripsi
6. Klik **Create pull request**
7. Review → klik **Merge pull request**
8. Klik **Confirm merge**

### Perbedaan kedua cara:

| Terminal (`git merge`) | Pull Request (GitHub) |
|---|---|
| Cepat, langsung gabung | Ada proses review dulu |
| Untuk kerja sendiri / kecil | Untuk kerja tim |
| Gak ada record diskusi | Ada diskusi & komentar |
| Cocok untuk prototype | Cocok untuk production |

---

## 9. Hapus Branch yang Sudah Selesai (5 menit)

### Setelah merge, branch fitur sudah tidak diperlukan:

```bash
# Hapus branch lokal
git branch -d feat/tambah-bio

# Hapus branch di GitHub (opsional)
git push origin --delete feat/tambah-bio
```

### Cek branch yang tersisa:

```bash
git branch
```

Harusnya hanya ada `main` sekarang.

---

## 10. Kesalahan Umum & Tips (10 menit)

| Masalah | Penyebab | Solusi |
|---|---|---|
| Salah edit di branch yang salah | Lupa cek branch aktif | Selalu `git branch` sebelum edit |
| Push ke main padahal harusnya ke branch | Lupa pindah branch | `git switch -c nama-branch` dulu, baru edit |
| Branch gak muncul di GitHub | Belum push branch | `git push -u origin nama-branch` |
| Conflict waktu merge | Edit file yang sama di dua branch | Selesaikan conflict dulu (minggu 4/5) |
| Branch名 aneh/spesial karakter | Salah penamaan | Pakai huruf kecil + strip |

### Tips penting:

1. **Selalu cek branch aktif** sebelum mulai kerja
2. **`git pull` dulu** sebelum buat branch baru
3. **Commit dalam potongan kecil** — jangan menumpuk banyak perubahan
4. **Push branch baru ke GitHub** supaya ada backup online
5. **Hapus branch setelah merge** supaya rapi

---

## 11. Penutup & Tugas Minggu Depan (5 menit)

### Ringkasan yang perlu diingat peserta:

| Konsep | Arti |
|--------|------|
| Branch | Jalur pengembangan terpisah dari kode utama |
| `main` | Branch utama, versi stabil |
| `git switch -c nama-branch` | Buat branch baru + pindah |
| `git push -u origin nama-branch` | Push branch baru ke GitHub |
| `git merge` | Gabungkan branch ke branch lain |
| `git branch -d nama-branch` | Hapus branch yang sudah di-merge |

### Tugas sebelum minggu ke-4:

1. **Buat minimal 2 branch** di repo yang sama:
   - Branch `feat/bio-saya` → buat file bio
   - Branch `docs/catatan` → buat file catatan
2. **Push kedua branch** ke GitHub
3. **Merge salah satu** branch ke `main` (pakai Terminal)
4. **Buat Pull Request** untuk branch satunya lagi (lewat GitHub)
5. **Hapus branch** yang sudah di-merge

### Pertanyaan refleksi:

- "Kapan kamu harus pakai branch?"
- "Apa beda `git merge` via Terminal vs Pull Request?"
- "Kenapa harus hapus branch setelah merge?"

---

## Referensi Lanjutan

- Buka `materi-git-github.md` bagian 7 dan 8
- Minggu depan kita bahas **Pull Request & Code Review** — bagian penting dalam kerja tim!

---

*Untuk mentor: file gambar yang tersedia di folder `images/` bisa dipakai untuk presentasi. Lihat daftar lengkap di repo.*
