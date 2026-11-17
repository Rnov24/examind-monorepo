# examind-monorepo — EXAMIND Platform

> Meta-repo for the EXAMIND AI-powered online examination platform (Sistem Ujian Online Berbasis AI).
> This repo contains no code of its own. It pins the two service repos as git submodules, so one clone gives you the whole platform at a known pair of commits.

## Submodules

| Submodule | Repo | Stack | What it holds |
|-----------|------|-------|---------------|
| `frontend/` | [Rnov24/examind-fe](https://github.com/Rnov24/examind-fe) | Next.js 15 + React 19 + TypeScript 5.7, pnpm, Tailwind 3.4, MediaPipe on-device proctoring | Web app: exams, proctoring, grading workspace, admin |
| `backend/` | [Rnov24/examind-be](https://github.com/Rnov24/examind-be) | FastAPI + SQLAlchemy 2.0 + PyMySQL against TiDB Cloud (Singapore), deployed on Modal; LLM adapters + Respan essay grader | API: auth, exams, sessions, grading, AI grading |

## Live

- App: https://examind.rijal.work
- API (edge): https://examind-api.rijal.work
- API (Modal, direct): https://rnov24--examind-be-api.us-east.modal.run

## Clone

```bash
git clone --recurse-submodules https://github.com/Rnov24/examind-monorepo.git
```

Cloned without submodules? Fix it with:

```bash
git submodule update --init --recursive
```

## How syncing works

Daily work (code, PRs, issues) happens in `examind-fe` / `examind-be`, never here. CI also lives in the service repos (GitHub Actions test + build in each); this meta-repo has no CI of its own.

This repo only records which commit of each service is current. After any push to `examind-fe` or `examind-be`, the pointers here must be synced:

```bash
git submodule update --remote --merge
git add frontend backend
git commit -m "chore: bump submodules ke versi terbaru"
git push
```

To run the app locally, go into each submodule and follow its own README. Do not treat either repo as production on localhost; production is the live links above.

## Repo map

```
examind-monorepo/
├── README.md          # this file
├── .gitmodules        # submodule URLs (frontend, backend)
├── frontend/          # submodule → Rnov24/examind-fe
└── backend/           # submodule → Rnov24/examind-be
```
