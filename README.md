# pulse-threads — Codex plugin

P.U.L.S.E Threads content engine untuk personal brand Lawrence Philemon, dikemas sebagai plugin OpenAI Codex (format open agent skills standard — kompatibel dengan ekosistem skill Claude).

## Isi

```
pulse-threads/
├── .codex-plugin/
│   └── plugin.json                  # manifest Codex (wajib)
├── skills/
│   ├── pulse-threads/               # skill utama: intake → mode → produksi batch
│   │   ├── SKILL.md
│   │   ├── agents/openai.yaml       # metadata UI di Codex app
│   │   └── references/
│   │       ├── threads-mechanics.md
│   │       ├── baseline-and-modes.md
│   │       └── riset-6-dimensi-keresahan-MASTER-v1.md
│   └── pulse-baseline/              # skill analisis log murni
│       └── SKILL.md
└── README.md
```

## Install — opsi 1: personal marketplace (paling cepat)

1. Copy folder plugin:
   ```
   mkdir -p ~/.codex/plugins-src
   cp -R pulse-threads ~/.codex/plugins-src/pulse-threads
   ```
2. Buat/edit `~/.agents/plugins/marketplace.json` — path relatif ke root marketplace, wajib diawali `./`. Kalau marketplace.json ada di `~/.agents/plugins/`, taruh plugin di dalam folder itu atau sesuaikan path:
   ```json
   {
     "name": "lawrence-plugins",
     "interface": { "displayName": "Lawrence Plugins" },
     "plugins": [
       {
         "name": "pulse-threads",
         "source": { "source": "local", "path": "./pulse-threads" },
         "policy": { "installation": "AVAILABLE", "authentication": "ON_INSTALL" },
         "category": "Productivity"
       }
     ]
   }
   ```
   (kalau pakai layout ini, copy foldernya ke `~/.agents/plugins/pulse-threads`)
3. Restart Codex → `/plugins` → pilih marketplace "Lawrence Plugins" → install pulse-threads → mulai sesi baru.

## Install — opsi 2: lewat repo lawrence-claude-plugins (dual Claude + Codex)

Codex membaca marketplace legacy `.claude-plugin/marketplace.json` DAN `.agents/plugins/marketplace.json`, dan format SKILL.md-nya sama-sama open agent skills standard. Jadi:

1. Tambahkan folder `pulse-threads/` ke repo `lawrence-claude-plugins`.
2. Daftarkan di marketplace file repo (entry sama seperti di atas, `source.path` menunjuk ke folder plugin).
3. Di Codex: `codex plugin marketplace add <owner>/lawrence-claude-plugins` → `/plugins` → install.

Satu repo, dua runtime. `.codex-plugin/plugin.json` dan `agents/openai.yaml` diabaikan oleh Claude; manifest Claude (kalau ada) diabaikan Codex.

## Pakai

- `$pulse-threads jalankan intake untuk batch minggu ini` — flow lengkap: intake → baseline/baseline-building → produksi 12 post.
- `$pulse-baseline` + paste/attach log — analisis angka murni tanpa produksi konten.
- Implicit invocation aktif: menyebut "bikin post threads" atau "batch konten threads" di prompt biasa juga akan men-trigger skill.

## Beda dari versi Claude Project

- Tidak ada memori antar-sesi bawaan project → intake wajib jalan sekali tiap sesi baru (sudah ditulis di SKILL.md).
- Tidak ada koneksi Buffer di-bundle. Posting tetap manual copy-paste (sesuai aturan kerja yang ada). Kalau nanti mau, plugin bisa ditambah `.mcp.json` untuk MCP server — jangan tambahkan tanpa keputusan eksplisit.
- Codex punya shell → validasi karakter/tanda seru/forbidden words dijalankan programatik, lebih ketat dari versi CustomGPT.
- Snapshot algoritma di `references/threads-mechanics.md` berlaku sampai ± Oktober 2026 — ada aturan kedaluwarsa di dalam filenya.

## Update

Edit file di folder sumber plugin → restart Codex supaya local install membaca file terbaru.
