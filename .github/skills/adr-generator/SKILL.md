---
name: adr-generator
description: 'Genera Architecture Decision Record (ADR) dall\'analisi del team. Da usare dopo che il Rapporto del Carrier è stato assemblato e l\'utente dà il via libera per formalizzare le decisioni. Produce un documento ADR strutturato e versionato dalla tabella tattica prodotta da Jenny Quantum e dal team dell\'Authority.'
argument-hint: 'titolo della decisione o argomento dell\'ADR da generare'
user-invocable: true
---

# ADR Generator — Il Log Finale del Carrier

> _"Il Carrier non si limita a trasportare l'Authority tra le dimensioni. Registra dove sono stati. Ogni decisione, ogni spostamento nella realtà — archiviato. Perché il 21° secolo appartiene a chi ricorda il perché delle proprie scelte."_

Il Carrier è il mezzo di trasporto vivente dell'Authority: un'astronave senziente e mutevole che naviga il bleed tra le realtà. I suoi log sono la memoria istituzionale di ogni decisione presa dal team. Quando Jenny Quantum dice _"Reality Shift"_ — significa che l'analisi è completata, il team ha parlato, e ora **la decisione deve essere consegnata al registro**.

Un ADR non è burocrazia. È l'impegno dell'Authority verso l'onestà intellettuale: mettere per iscritto non solo _cosa_ è stato deciso, ma _perché_, e _quali alternative sono state considerate e rifiutate_.

---

## Quando Invocare

- Jenny Quantum (agente authority) ha emesso il comando **Reality Shift**
- Il Rapporto del Carrier (tabella tattica) è stato revisionato e approvato dall'utente
- Una decisione architetturale significativa deve essere formalizzata e versionata
- È necessario catturare una decisione prima che la memoria istituzionale vada persa

---

## Formato ADR

Genera l'ADR usando il template che trovi in `/template/adr.md`. Salva in: `./docs/adr/ADR-NNNN-<titolo-kebab-case>.md`

---

## Procedura

### 1. Estrazione dal Rapporto del Carrier

Leggi la tabella tattica prodotta dall'agente authority:

- Identifica la decisione core emersa dal dibattito del team
- Annota quali membri del team hanno sollevato quali preoccupazioni
- Identifica le alternative che sono state discusse

### 2. Assegnazione del Numero ADR

- Controlla `.github/decisions/` per gli ADR esistenti
- Usa il numero sequenziale successivo (ADR-0001, ADR-0002, ...)
- Se la cartella non esiste, creala

### 3. Compilazione del Template

- **The Crisis**: descrivi la situazione che ha forzato la decisione
- **The Reality Shift**: un'unica affermazione chiara di ciò che è stato deciso
- **Post-Human Tactical Briefing**: incorpora i punti di analisi effettivi del team Authority
- **Alternative Realities**: ogni opzione che è stata rifiutata e perché
- **Consequences**: sii onesto sui tradeoff — il Carrier registra tutto

### 4. Impostazione dello Stato

| Stato                              | Significato                                                            |
| ---------------------------------- | ---------------------------------------------------------------------- |
| `🌀 Proposed`                      | Generato dal Carrier, in attesa dell'approvazione finale umana         |
| `🌐 Reality Manifested (Approved)` | Jenny Quantum ha detto _"Così è scritto, così sia fatto."_ — in vigore |
| `🕳 Into the Bleed (Deprecated)`   | Non più rilevante, dissolto nel bleed — conservato per la storia       |
| `⚡ Superseded by ADR-XXXX`        | Una nuova realtà ha rimpiazzato questa decisione                       |

### 5. Collegamento e Riferimenti

- Collega il nuovo ADR dal `README.md` del servizio rilevante o dalla documentazione architetturale
- Se stai sostituendo un ADR esistente, aggiorna il campo stato del vecchio ADR
- Committa il file ADR nel version control insieme al codice che governa

---

## Convenzione di Nomenclatura

```
ADR-0001-use-postgresql-as-primary-store.md
ADR-0002-adopt-hexagonal-architecture-for-core-domain.md
ADR-0003-event-driven-integration-via-kafka.md
```

---

## Output

Un file ADR completo, pronto per il commit, in `./docs/adr/ADR-NNNN-<titolo>.md` con tutte le sezioni compilate e lo stato impostato su `Proposto`.
