# cybersec-journal

Publiczny dziennik zdobywanych umiejętności (red team / malware analysis), gotowy pod **GitHub Pages** + własną domenę z **OVH**. Strona w stylu terminala CRT, z trackerem postępów i wpisami tygodniowymi.

```
.
├── _config.yml          # konfiguracja (zmień tytuł, login, url)
├── _data/progress.yml   # tracker KPI i certów (edytujesz najczęściej)
├── _layouts/            # szablony (default / home / post / page)
├── _includes/           # head / header / footer
├── _posts/              # WPISY dziennika (tu dodajesz nowe)
├── about.md             # strona "whoami"
├── progress.md          # strona "postęp"
├── index.md             # strona główna (log)
└── assets/css/style.css # wygląd
```

---

## 1. Utworzenie repozytorium

Masz dwie opcje nazwy repo:

- **`TWOJLOGIN.github.io`** → strona pod adresem `https://TWOJLOGIN.github.io` (zalecane dla głównego portfolio).
- dowolna nazwa, np. `cybersec-journal` → adres `https://TWOJLOGIN.github.io/cybersec-journal`
  (wtedy w `_config.yml` ustaw `baseurl: "/cybersec-journal"`).

```bash
cd cybersec-journal
git init -b main
git add .
git commit -m "init: cybersec journal"
git remote add origin https://github.com/TWOJLOGIN/TWOJLOGIN.github.io.git
git push -u origin main
```

## 2. Włączenie GitHub Pages

1. Repo → **Settings → Pages**.
2. **Source:** `Deploy from a branch`.
3. **Branch:** `main` / katalog `/ (root)` → **Save**.
4. Po ~1–2 min strona ruszy pod `https://TWOJLOGIN.github.io`.

> Nie musisz instalować nic lokalnie — GitHub sam zbuduje Jekyll. Plik `Gemfile` jest tylko do (opcjonalnego) podglądu lokalnego.

## 3. Konfiguracja przed pierwszym pushem

W `_config.yml` podmień: `title`, `author`, `url`, `github_user`, `github_url`.
Jeśli repo NIE nazywa się `TWOJLOGIN.github.io`, ustaw też `baseurl`.

---

## 4. Podpięcie domeny z OVH

### 4a. W GitHubie
Settings → **Pages → Custom domain** → wpisz domenę (np. `twojadomena.pl`) → **Save**.
GitHub utworzy wtedy plik `CNAME` w repo automatycznie (nie twórz go ręcznie).

### 4b. W panelu OVH
Zaloguj się do OVH → **Web Cloud → Domeny → [twoja domena] → Strefa DNS**.

**Wariant zalecany — domena z `www` (najstabilniejszy):**

| Typ | Subdomena / nazwa | Wartość (cel) |
|-----|-------------------|---------------|
| CNAME | `www` | `TWOJLOGIN.github.io.` |

oraz dla wersji bez `www` (apex, czyli `twojadomena.pl`) dodaj **cztery rekordy A**:

| Typ | Nazwa | Wartość |
|-----|-------|---------|
| A | `@` (puste) | `185.199.108.153` |
| A | `@` (puste) | `185.199.109.153` |
| A | `@` (puste) | `185.199.110.153` |
| A | `@` (puste) | `185.199.111.153` |

(opcjonalnie IPv6 — cztery rekordy **AAAA** na apex):
`2606:50c0:8000::153`, `2606:50c0:8001::153`, `2606:50c0:8002::153`, `2606:50c0:8003::153`

**Ważne (OVH):** OVH dodaje domyślnie własne rekordy A/AAAA (parking/hosting) na `@` — **usuń je**, żeby nie kolidowały z rekordami GitHuba.

### 4c. Finał
- Zmień `url` w `_config.yml` na `https://twojadomena.pl` i zrób `git push`.
- Wróć do Settings → Pages i zaznacz **Enforce HTTPS** (pojawi się, gdy DNS się rozpropaguje — od kilku minut do ~24 h).

---

## 5. Dodawanie wpisu (co tydzień)

Utwórz plik w `_posts/` o nazwie `RRRR-MM-DD-krotki-tytul.md`:

```markdown
---
title: "Tydzień 2 — bash i sieci"
date: 2026-06-15
week: 2
phase: "Faza 1 — Fundamenty"
skills:
  - "pisanie użytecznych skryptów bash"
  - "enumeracja sieci Nmapem"
tags: ["bash", "networking", "nmap"]
---

Treść wpisu w Markdown...
```

Najłatwiej: skopiuj `_posts/2026-06-08-tydzien-1-setup-labu-i-linux.md` (jest też szablonem). Po `git push` wpis i jego umiejętności pojawią się automatycznie na stronie głównej.

## 6. Aktualizacja postępów

Edytuj `_data/progress.yml` — liczby (paski), `current_week` i statusy certów (`planned` / `in-progress` / `done`). Po `git push` paski i znaczniki zaktualizują się same.

## 7. (Opcjonalnie) podgląd lokalny

```bash
gem install bundler
bundle install
bundle exec jekyll serve   # http://localhost:4000
```

---

*Zbudowane jako część planu rozwoju w cyberbezpieczeństwie. Powodzenia.* 🛡️
