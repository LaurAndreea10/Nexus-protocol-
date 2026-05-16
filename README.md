# NEXUS PROTOCOL

> Endless runner neon × CRM tycoon × Code breaker. Single-file game by Laura Andreea.

[🎮 Live Demo](https://laurandreea10.github.io/nexus-protocol/) · [📖 Case Study](https://laurandreea10.github.io/codepen-portfolio/projects/nexus-protocol.html) · [🇬🇧 English](#english)

---

## 🇷🇴 Română

### Despre proiect

**NEXUS PROTOCOL** este un experiment de fuziune între trei genuri într-un singur joc single-file: un endless runner neon synthwave, un CRM tycoon meta-layer și mini-challenges de cod la checkpoint-uri.

Conduci un hover-car prin sectorul comercial al unui oraș-rețea din 2087. Eviți obstacole holografice, prinzi lead-uri (pickup-uri magenta) și energy capsules. La fiecare 10 lead-uri închise se deschide **CRM Module Store** unde activezi permanent module care îți schimbă regulile run-ului. La fiecare 1000m apare un **Code Breaker checkpoint** cu o întrebare reală despre JavaScript, regex sau CSS — corect → multiplier ×2, greșit → slowdown 3s.

### De ce am construit asta

Voiam să leg explicit zona mea de **CRM/SaaS** de zona de **jocuri arcade** din portofoliu, într-un singur produs care să arate că aceleași principii de design (kanban, flow builder, RBAC, autosave, billing) pot fi traduse în mecanici de joc. Modulele din CRM Store nu sunt decorative — fiecare schimbă comportamentul jocului în mod observabil.

### Stack tehnic

- **Vanilla HTML/CSS/JS** — zero dependențe, zero build step
- **Canvas 2D** — render la 60fps cu DPR-aware scaling
- **Web Audio API** — sound design procedural (zero asset-uri audio)
- **localStorage** — persistență credite, module, leaderboard, achievements, daily streak
- **CSS clip-path + glow** — UI cyberpunk fără SVG-uri sau imagini
- **Single-file delivery** — 74KB, deploy într-un push pe GitHub Pages

### Mecanici cheie

| Layer | Trigger | Rezultat |
|-------|---------|----------|
| Drive | Continuu | Distanță + scor + speed ramp |
| Pickup lead | Coliziune cu pickup magenta | +combo, +credite (50 × combo × multiplier) |
| Pickup energy | Coliziune cu pickup cyan | +200 scor (sau +1 lead cu Flow Builder) |
| Pickup boost | Coliziune cu pickup yellow | 5s boost (10s cu Quantum Core) |
| CRM Upgrade | La fiecare 10 lead-uri | Deschide store, alegi 1 modul |
| Code Breaker | La fiecare 1000m | Întrebare tehnică, 8s timer |
| Combo crash | Coliziune obstacol | -1 viață + combo reset (păstrat cu RBAC) |
| Daily challenge | Seed pe data zilei | Reward 500-1000 credite |

### 8 module CRM (efecte permanente)

1. **KANBAN** (200 CR) — +10% credite din lead-uri
2. **AUTOSAVE** (400 CR) — 50% șansă să nu pierzi viață la crash
3. **RBAC** (400 CR) — combo nu se pierde la coliziune
4. **FLOW BUILDER** (600 CR) — energy dă +1 lead
5. **BILLING** (600 CR) — +25% credite din lead-uri
6. **BOOKING** (800 CR) — magnet pentru lead-uri (atrase spre tine)
7. **AI COPILOT** (1000 CR) — auto-solve la 1 challenge/run
8. **QUANTUM CORE** (1400 CR) — boost durează ×2

### Controale

- **A** / **←** — schimbă lane stânga
- **D** / **→** — schimbă lane dreapta
- **SPACE** — boost (cost 100 CR)
- **P** / **ESC** — pauză
- **Touch** — butoane jos pe mobil + swipe pe canvas

### Decizii tehnice

**De ce single-file?** Aceeași filosofie ca la ARCADE OPS și BASKET VS AI: deploy într-un singur push, fără build pipeline, fără bundler, fără asset management. Util pentru portofoliu — recruiterul poate citi tot codul într-un singur fișier.

**De ce Canvas 2D și nu WebGL/Three.js?** Estetica synthwave funcționează perfect cu efecte 2D + perspectivă falsă (vertical lines spre punct de fugă + grid scrolling). WebGL ar fi adăugat 300KB+ și complexitate fără câștig vizual proporțional.

**De ce localStorage pentru leaderboard?** Single-player, fără backend → match perfect cu portofoliul (zero costuri de hosting). Trade-off: nu există competiție globală, dar adaug pseudo-AGENT entries pentru atmosferă.

**De ce Web Audio API procedural?** Zero asset-uri audio = repo mai curat, sub 100KB total. Toate sunetele sunt generate live: lead pickup = sine wave 880Hz → 1320Hz, crash = sawtooth 80Hz, correct answer = arpeggiu C-E-G.

---

## 🇬🇧 English

### About

**NEXUS PROTOCOL** is a fusion experiment combining three genres in one single-file game: a neon synthwave endless runner, a CRM tycoon meta-layer, and code mini-challenges at checkpoints.

You drive a hover-car through the commercial sector of a 2087 network-city. You dodge holographic obstacles, grab leads (magenta pickups) and energy capsules. Every 10 closed leads unlocks the **CRM Module Store** where you permanently activate modules that change run rules. Every 1000m a **Code Breaker checkpoint** appears with a real JavaScript/regex/CSS question — right → ×2 multiplier, wrong → 3s slowdown.

### Why I built this

I wanted to explicitly bridge my **CRM/SaaS** portfolio area with the **arcade game** area in a single product showing that the same design principles (kanban, flow builder, RBAC, autosave, billing) can be translated into game mechanics. The CRM Store modules are not decorative — each one changes game behavior observably.

### Tech stack

- **Vanilla HTML/CSS/JS** — zero dependencies, zero build step
- **Canvas 2D** — 60fps render with DPR-aware scaling
- **Web Audio API** — procedural sound design (zero audio assets)
- **localStorage** — persists credits, modules, leaderboard, achievements, daily streak
- **CSS clip-path + glow** — cyberpunk UI without SVGs or images
- **Single-file delivery** — 74KB, deploys in one GitHub Pages push

### Controls

- **A** / **←** — lane left
- **D** / **→** — lane right
- **SPACE** — boost (costs 100 CR)
- **P** / **ESC** — pause
- **Touch** — bottom buttons on mobile + canvas swipe

### Tech decisions

**Why single-file?** Same philosophy as ARCADE OPS and BASKET VS AI: deploy in one push, no build pipeline, no bundler, no asset management. Good for portfolio — recruiters can read the entire codebase in one file.

**Why Canvas 2D over WebGL?** Synthwave aesthetic works perfectly with 2D + fake perspective (vertical lines to vanishing point + grid scrolling). WebGL would have added 300KB+ and complexity without proportional visual gain.

**Why localStorage for leaderboard?** Single-player, no backend → perfect match for portfolio (zero hosting cost). Trade-off: no global competition, but I add pseudo-AGENT entries for atmosphere.

**Why procedural Web Audio?** Zero audio assets = cleaner repo, under 100KB total. All sounds generated live: lead pickup = sine 880Hz → 1320Hz, crash = sawtooth 80Hz, correct answer = C-E-G arpeggio.

---

## Deploy

```bash
# Clone
git clone https://github.com/LaurAndreea10/nexus-protocol.git
cd nexus-protocol

# Open locally
open index.html

# Deploy: push to main, enable GitHub Pages → main branch / root
git push origin main
```

## Tags

`canvas` `web-audio-api` `synthwave` `endless-runner` `crm` `gamification` `bilingual` `single-file` `vanilla-js`

---

© 2026 Laura Andreea · [laurandreea10.github.io](https://laurandreea10.github.io/codepen-portfolio/)
