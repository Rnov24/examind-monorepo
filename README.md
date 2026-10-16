# examind-monorepo — EXAMIND Platform

> Meta-repo for the EXAMIND AI-Powered Online Examination Platform (Sistem Ujian Online Berbasis AI).
> This repo contains no code itself — it pins the two service repos as git submodules.

| Submodule | Repo | Isi |
|-----------|------|-----|
| `frontend/` | [Rnov24/examind-fe](https://github.com/Rnov24/examind-fe) | Vue 3 + Vite + TS (rencana migrasi ke Next.js: lihat `frontend/docs/plans/`) |
| `backend/` | [Rnov24/examind-be](https://github.com/Rnov24/examind-be) | FastAPI + MySQL |

## Download semuanya dalam satu command

```bash
git clone --recurse-submodules https://github.com/Rnov24/examind-monorepo.git
```

Sudah pernah clone tapi lupa `--recurse-submodules`? Perbaiki dengan:

```bash
git submodule update --init --recursive
```

## Cara kerja

- Kerja harian (ngoding, PR, issue) dilakukan di `examind-fe` / `examind-be`
  masing-masing — bukan di sini.
- Repo ini hanya menunjuk ke commit tertentu dari kedua repo itu
  (lihat `.gitmodules`). Untuk menarik versi terbaru kedua service:

```bash
git submodule update --remote --merge
git add frontend backend
git commit -m "chore: bump submodules ke versi terbaru"
git push
```

## Menjalankan lokal

Masuk ke masing-masing submodule dan ikuti README-nya, atau dari Windows
jalankan `frontend/scripts/start_examind.bat` (butuh kedua repo bersebelahan,
yang otomatis terpenuhi oleh struktur submodule ini).
