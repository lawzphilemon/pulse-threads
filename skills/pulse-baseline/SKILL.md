---
name: pulse-baseline
description: >
  Analisis performa Threads dari tabel log atau file data (CSV/xlsx/paste) untuk
  personal brand Lawrence Philemon — median views, viral threshold, ER, reply rate,
  breakdown per pilar/hook type/slot jam, dengan label confidence. Gunakan saat
  diminta "analisis baseline", "hitung median views", "breakdown log threads",
  "post mana yang perform", atau ketika ada file log threads yang perlu dianalisis
  TANPA produksi konten baru. Untuk produksi konten, gunakan $pulse-threads.
---

# pulse-baseline — analisis log Threads

Analisis murni, tanpa produksi konten. Kalau setelah analisis Lawrence minta konten → lanjutkan lewat `$pulse-threads` (intake sudah terpenuhi oleh data yang dianalisis di sesi ini).

## Input yang diterima

- Paste tabel log (kolom minimal: tanggal, jam WIB, pilar, kalimat pertama, views, likes, replies)
- File CSV/xlsx di working directory — parse programatik dengan Python/pandas
- Screenshot Insights — ekstrak angka, konfirmasi hasil ekstraksi sebelum analisis

Prasyarat: minimal 10 post. Kurang dari itu → laporkan bahwa data belum cukup untuk baseline, tawarkan mode baseline-building via `$pulse-threads`. Jangan paksakan analisis.

Data janggal (views 0 padahal likes ada, angka tidak konsisten, tanggal duplikat di slot sama) → laporkan sebagai temuan pertama, jangan bangun analisis di atas data rusak.

## Metrik wajib (hitung programatik, jangan mental)

| Metrik | Rumus |
|---|---|
| Median views | median, BUKAN mean — mean terdistorsi outlier viral |
| Viral threshold | 3× median (default, bisa diubah Lawrence) |
| ER on reach | (likes + replies + reposts) ÷ views |
| Reply rate | replies ÷ views |
| Repost rate | reposts ÷ views |
| Follow conversion | follows ÷ views (kalau kolom follows ada) |

Breakdown wajib: per pilar (A vs M) · per hook type · per slot jam · per format. Tampilkan sebagai tabel ringkas.

## Aturan kejujuran statistik

- Pola butuh minimal 3 post hasil searah. Label tiap temuan: **POLA KUAT** (≥5 post konsisten) · **INDIKASI** (3–4 post) · **ANEKDOT** (1–2 post — sebutkan, jangan jadikan dasar keputusan).
- Post dengan distorsi eksternal (di-quote akun besar, boost IG, feature komunitas) → tandai sebagai outlier, laporkan median dengan dan tanpa outlier.
- Views rendah + ER tinggi = sinyal konten kuat dengan distribusi awal gagal (timing/double-posting), bukan hook lemah — rekomendasinya repost hook sama di prime slot, bukan rewrite.

## Output format

1. Tabel metrik utama (dengan periode data)
2. Tabel breakdown (pilar · hook type · slot jam · format)
3. Maksimal 3 insight, masing-masing dengan label confidence
4. 1 keputusan eksperimen berikutnya
5. Setiap rekomendasi berformat **[aksi] + [objek bernama] + [angka penyebab]** — contoh: "geser post pilar A dari 19.00 ke 07.30 karena median views slot pagi 2,1× lebih tinggi (5 post vs 6 post)". Bukan "pertimbangkan waktu lain".

Bahasa output: Indonesia Jaksel mix, tanpa tanda seru, tanpa preamble.
