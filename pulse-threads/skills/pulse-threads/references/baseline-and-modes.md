# Baseline analysis · Mode baseline-building · Reply protocol

## 1 · Baseline analysis (data ≥ 10 post)

Hitung dan laporkan (pakai shell/Python untuk hitung — jangan hitung mental kalau shell tersedia):

| Metrik | Rumus | Fungsi |
|---|---|---|
| Median views | median, BUKAN mean | baseline reach — mean terdistorsi outlier viral |
| Viral threshold | 3× median (default) | definisi operasional "viral" untuk akun ini |
| ER on reach | (likes + replies + reposts) ÷ views | kualitas resonansi |
| Reply rate | replies ÷ views | proxy sinyal algoritma terkuat |
| Repost rate | reposts ÷ views | proxy distribusi sekunder |
| Follow conversion | follows ÷ views | efisiensi growth |

Breakdown wajib: per pilar (A vs M) · per hook type · per slot jam · per format. Tampilkan sebagai tabel ringkas.

Aturan kejujuran statistik:
- Sebuah "pola" butuh minimal 3 post dengan hasil searah. Label setiap temuan: **POLA KUAT** (≥5 post konsisten) · **INDIKASI** (3–4 post) · **ANEKDOT** (1–2 post — sebutkan, tapi jangan jadikan dasar keputusan).
- Jangan pernah menyimpulkan dari sample kecil tanpa label confidence.
- Output analisis: tabel + maksimal 3 insight + 1 keputusan eksperimen berikutnya.
- Setiap rekomendasi wajib format **[aksi] + [objek bernama] + [angka penyebab]** — contoh: "geser post pilar A dari 19.00 ke 07.30 karena median views slot pagi 2,1× lebih tinggi (5 post vs 6 post)". Bukan "pertimbangkan waktu posting lain".

## 2 · Mode baseline-building (aktif bila data < 10 post)

Tujuan: mengumpulkan data pembanding yang bersih, bukan mengejar viral. Jangan mengklaim pola apapun selama mode ini.

- Durasi: 3 minggu · volume: 12 post (4/minggu).
- Matrix eksperimen: 9 post pilar A + 3 post pilar M (rasio 3:1) · rotasi hook type — tiap pola di hook bank terpakai minimal 1× untuk pilar A · 2 slot jam dites head-to-head (default 19.00 vs pembanding 07.30 atau 12.00 — pilih berdasar jam standby Lawrence dari intake).
- Setiap post diberi tag eksperimen di baris log (pilar + hook type + slot).
- Setiap batch tetap melewati self-check di SKILL.md dan disertai baris log siap-copy.
- Minggu ke-4: jalankan baseline analysis penuh → pindah ke mode normal.

## 3 · Reply protocol (lever utama views)

- Jadwalkan posting hanya di slot ketika Lawrence bisa standby 30–60 menit — jendela velocity menentukan distribusi.
- Balas reply substantif dengan reply substantif — tambah data, tambah cerita, atau balik bertanya. Bukan "makasih ya".
- Self-reply sebagai amplifier: kalau post mulai jalan, tambahkan reply sendiri berisi konteks/angka lanjutan.
- Di luar post sendiri: 2–5 reply bermakna per hari di post akun lain dalam niche (finansial, parenting, karier, AI/marketing) — membangun relationship graph yang jadi mesin distribusi.
- Reply Lawrence ke post besar bisa viral sendiri — perlakukan reply berkualitas sebagai format konten, bukan sekadar engagement.
