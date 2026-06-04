---
layout: page
title: postęp
subtitle: "mierniki i kamienie milowe (plan 18 mies.)"
permalink: /progress/
---

**Aktualny etap:** {{ site.data.progress.phase }} · **tydzień {{ site.data.progress.current_week }} / 78**

## Mierniki (KPI)

<div class="bars">
{% for m in site.data.progress.metrics %}
{% assign pct = m.current | times: 100 | divided_by: m.target %}
<div class="bar">
  <div class="bar__head">
    <span class="bar__name">{{ m.name }}</span>
    <span class="bar__val">{{ m.current }}/{{ m.target }} · {{ pct }}%</span>
  </div>
  <div class="bar__track"><div class="bar__fill" style="width: {{ pct }}%"></div></div>
</div>
{% endfor %}
</div>

## Certyfikaty

<div class="certs">
{% for c in site.data.progress.certs %}
<span class="cert cert--{{ c.status }}">{% if c.status == 'done' %}[x]{% elsif c.status == 'in-progress' %}[~]{% else %}[ ]{% endif %} {{ c.name }}</span>
{% endfor %}
</div>

## Kamienie milowe

| Faza | Tygodnie | Cel |
|------|----------|-----|
| 1 — Fundamenty | 1–12 | Linux + sieci + Python → **eJPT/PJPT** |
| 2 — Specjalizacja | 13–26 | Active Directory, RE, 1. analiza malware → **PNPT/PJPT** |
| 3 — Projekty + OSCP | 27–52 | **OSCP**, tooling C#, portfolio malware |
| 4 — Zaawansowane | 53–78 | **CRTO**, threat intel, wejście na rynek |

<!-- Edytuj liczby w pliku _data/progress.yml — paski i statusy zaktualizują się automatycznie po git push. -->
