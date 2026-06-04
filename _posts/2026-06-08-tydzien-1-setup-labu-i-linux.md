---
title: "Tydzień 1 — setup labu i fundamenty Linuksa"
date: 2026-06-08
week: 1
phase: "Faza 1 — Fundamenty"
skills:
  - "uruchamianie i przywracanie maszyn wirtualnych (snapshots)"
  - "nawigacja po systemie plików Linux z CLI"
  - "zarządzanie uprawnieniami (chmod/chown)"
tags: ["linux", "lab", "thm"]
---

Pierwszy tydzień zgodnie z planem: postawienie środowiska i wejście w Linuksa.

## Co zrobiłem

- Postawiłem lab: Kali + Ubuntu + Windows 10 (trial) w VirtualBox, z migawkami.
- Przerobiłem THM *Linux Fundamentals 1–3*.
- OverTheWire *Bandit* 0–15.

## Czego się nauczyłem

Najwięcej dała mi praca bez GUI — `find`, potoki i przekierowania nagle „kliknęły". Uprawnienia (`chmod`, bit SUID) przestały być magią.

```bash
# przykład z tego tygodnia: znajdź pliki z SUID
find / -perm -4000 -type f 2>/dev/null
```

## Na co uważać / co dalej

Muszę popracować na `awk`/`sed` — na razie kopiuję z notatek. W przyszłym tygodniu: scripting w bashu + sieci od strony ataku.

---

> **To jest też szablon wpisu.** Skopiuj ten plik do `_posts/`, zmień nazwę na `RRRR-MM-DD-tytul.md`, podmień front-matter (szczególnie `skills:`) i treść.
