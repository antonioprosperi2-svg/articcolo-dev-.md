<p align="center">
  <img src="https://beeenginejs.com/wp-content/uploads/2026/09/Gemini_Generated_Image_c81o98c81o98c81o.jpg" alt="BeeLadybug" width="720">
</p>

## 🐝 → 🐞 Il Distacco: da modulo interno a pacchetto universale

`BeeLadybug` nasce **dentro** BeeEngine (v2.4.0): un modulo di debug scritto per
conoscere già le entità, le hitbox e il ciclo di vita del motore. Comodo per chi
usa BeeEngine, ma inutilizzabile ovunque altro — la stessa logica di ispezione non
poteva funzionare su una pagina web qualsiasi o su un processo Python.

Per questo è stato **estratto in un pacchetto a parte**: [`bee-ladybug`](https://www.npmjs.com/package/bee-ladybug),
ridisegnato attorno a un principio diverso — il *Core* non sa più nulla
dell'ambiente che sta osservando, e sono gli *Adapter* (Canvas, DOM, Python) a
tradurre ciò che vedono in pacchetti generici.

Oggi convivono due strumenti distinti, con scopi diversi:

| | `enableLadybug()` (integrato in BeeEngine) | `bee-ladybug` (pacchetto universale) |
|---|---|---|
| **Dove funziona** | Solo dentro BeeEngine | Canvas, DOM, Python — qualsiasi ambiente |
| **Cosa disegna** | Hitbox AABB native del motore | Overlay generico, nessuna conoscenza del contenuto |
| **Quando usarlo** | Stai già sviluppando con BeeEngine | Vuoi ispezionare qualcosa che non è BeeEngine |

Non è un modulo che ha sostituito l'altro: sono due livelli — uno specifico e
integrato, uno generico e portabile — nati dalla stessa idea ma con obiettivi
diversi.