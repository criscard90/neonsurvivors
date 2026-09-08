# ⚛️ QUARK — Fuga dal Regno Microscopico

Un **Vampire-Survivors-like 2D completo in un singolo file HTML** con [Phaser 3](https://phaser.io/).
Zero asset esterni: **tutta la grafica è generata a runtime con primitive vettoriali** (cerchi, rettangoli, ellissi, poligoni colorati). Niente sprite, niente immagini: solo geometria neon.

> Sei un **Quark** intrappolato nel regno microscopico. Sopravvivi a 10 livelli di ondate, evolviti e fuggi!

---

## 🚀 Come si gioca

**Nessuna installazione.** Apri semplicemente `index.html` nel browser (serve Internet solo per il CDN di Phaser al primo avvio).

In alternativa, servi la cartella in locale:

```bash
python3 -m http.server 8000
# → http://localhost:8000
```

### 🎮 Controlli

| Azione | Tastiera | Touch |
|---|---|---|
| Muoviti | **Frecce** o **WASD** | **Joystick virtuale** (tieni premuto e trascina) |
| Dash quantistico | **SPAZIO** | **Tap** a schermo |
| Scegli upgrade | **1 / 2 / 3** | **Tocca la carta** |
| Start / Rigioca | **INVIO o SPAZIO** | **Tap** |

### 🧬 Struttura della fuga

- **Onde progressive**: il tempo scorre nell'HUD in alto — atomi, batteri, tossine, virus, ioni, prioni e mutanti arrivano in quantità e velocità crescenti.
- **Boss al minuto 02:00**: ogni livello dura 2 minuti; allo scoccare di 02:00 i nemici normali smettono di comparire e arriva il **Boss Molecolare** con attacchi a tema (proiettili mirati, anelli radiali, spirali, nuclei orbitanti, scatti a dardo).
- **10 livelli, 10 boss**:

| # | Boss | Tagline |
|---|---|---|
| 1 | Nicotina | La molecola del fumo |
| 2 | Caffeina | Il segnale che non dorme mai |
| 3 | Alcool | Il solvente che annega i neuroni |
| 4 | Colesterolo | La placca che ostruisce le arterie |
| 5 | Zucchero | La dolcezza che spegne i batteri buoni |
| 6 | Radiazione | Il campo che muta il DNA |
| 7 | Metanfetamina | La scossa che brucia i neuroni |
| 8 | Microplastica | La fibra che non si dissolve |
| 9 | PFAS | Lo scudo chimico eterno |
| 10 | **Caos Molecolare** | BOSS FINALE: l'entropia delle molecole |

Sconfitto il boss si passa al livello successivo, con nemici più forti e un boss più grosso, più rapido e con nuove meccaniche.

---

## ⚛️ Armi & Evoluzioni

Raccogli i **cristalli XP** lasciati dai nemici, sali di livello e scegli tra le carte:

| Arma | Evoluzione | Cosa fa |
|---|---|---|
| 🔵 **Laser Fotonico** | Cannone Fotonico | Raggio istantaneo sul nemico più vicino |
| ⚪ **Campo di Gluoni** | Regno dei Gluoni | Gluoni in orbita che difendono e colpiscono |
| 🟡 **Bosone di Higgs** | Essenza di Higgs | Aura che rallenta e consuma la materia nemica |

**Porta tutte e tre al livello massimo (Lv 5) per sbloccare la ★ SINGOLARITÀ QUANTISTICA**, l'unione delle tre forze!

### Passivi (utili)

- 🟨 **Guanto di Quark** — +5% danno per livello
- 🟪 **Core Strano** — +15 PV massimi per livello
- 🟦 **Spin Accelerato** — +6% velocità per livello
- 🟥 **Flusso di Fuoco** — +6% cadenza per livello
- 🟩 **Antiquark** — +8% raggio di raccolta cristalli per livello

---

## 🛠️ Tecnica

- **Un solo file**: `index.html` (~74 KB) — HTML + CSS + JavaScript di gioco.
- **Phaser 3.85** via CDN (`cdn.jsdelivr.net`) con messaggio di fallback offline.
- **Grafica 100% procedurale**: `add.circle / rectangle / ellipse / polygon` — nessun file immagine o sprite.
- **Risoluzione base 1280×720** con `Scale.FIT + CENTER_BOTH`: si gioca identico su desktop e smartphone.
- **Mondo ampio** (4480×2880) con camera che segue il quark, sfondo microscopico a zone animate (non tinta unita).
- **Zero dipendenze di build**: logica interamente dentro il loop `update()` della scena.
- **Bilanciamento centrale e modificabile** in testa al file:
  - `BOSS_TIME_SEC = 120` (minuto del boss)
  - `EXP_BASE = 56`, `EXP_GROWTH = 1.22` (curva XP)
  - `LEVELS` (boss: HP, velocità, scala, pattern `aim / ring / radial / spiral / orbit / track / bubble / spawn / dash`)
  - `ENEMY_TYPES` (10 tipi di nemici con HP, velocità, XP e danni)

### Test

La logica è verificabile headless (senza browser) con uno stub Phaser:

```bash
# estrai il JS e lancia il flusso: scena → run → armi → upgrade → boss → clear
node --check /tmp/game.js && node /tmp/stub.js
```

---

## 📈 Pronto a diventare virale

- **Un file che si condivide ovunque**: messalo su GitHub Pages, Netlify Drop o inviato in chat, gira subito.
- **Loop a 20+ minuti**: dieci livelli da 2 minuti con boss sempre diversi.
- **Build varietà**: 3 armi + evoluzione segreta + 5 passivi = mille combinazioni.
- **Clip-ready**: dash quantistico, esplosioni a particelle, screen shake e pop-up «SINGOLARITÀ QUANTISTICA!».

*Il quark conta su di te. Scappa dal regno microscopico!* 🧪
