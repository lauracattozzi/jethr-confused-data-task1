# jethr-confused-data-task1

Task per candidatura Jet HR - Analisi dati ATS

\# Jet HR - Recruiting Funnel Data Analysis



\# 📊 Jet HR - Confused Data Task (Analisi ATS \& Ottimizzazione Funnel)



Benvenuto nella mia analisi per la task di Jet HR. Questo repository contiene l'analisi esplorativa, la pulizia dei dati e le raccomandazioni strategiche per ristrutturare i processi di selezione del team Talent.



\---



\## 🧹 1. Data Cleaning \& Metriche Chiave (KPI)



\### Pulizia dei Dati

\- \*\*Standardizzazione Ruoli:\*\* Sono stati unificati i doppioni presenti nel dataset grezzo (es. fusione di `SWE` in `Software Engineer` e di `Business Development Representative` in `BDR`).

\- \*\*Gestione Date e Valori Mancanti:\*\* Normalizzazione delle date di candidatura e fine processo per calcolare con precisione i tempi di permanenza nei singoli step (\*Time-in-Stage\*). Filtraggio dei record incompleti per evitare distorsioni nei tassi di conversione.



\### KPI Adottati

1\. \*\*Pass-Through Rate (Conversion Rate):\*\* Percentuale di candidati che superano con successo una fase e accedono alla successiva.

2\. \*\*Drop-off Rate:\*\* Tasso di abbandono o scarto dei candidati in ciascuno step.

3\. \*\*Time-to-Hire / Time-in-Stage:\*\* Durata media di permanenza in giorni per valutare dove il processo subisce rallentamenti critici.



\---



\## 🔍 2. Analisi del Funnel e Colli di Bottiglia per Ruolo



Dall'analisi delle \*\*9.995 righe\*\* del dataset ATS, emergono le seguenti criticità basate sulle specificità dei ruoli:



\- \*\*Web Designer \& Chief of Staff (Ruoli Chiusi):\*\* 

&#x20; - \*Criticità:\* L'assenza dello Screening iniziale e l'invio immediato della Task generano un collo di bottiglia operativo. Il team di recruiting spende ore a valutare task tecniche di candidati che spesso non possiedono i requisiti di base presenti nel CV.

\- \*\*Product Designer:\*\*

&#x20; - \*Criticità:\* La task viene inviata dopo la prima intervista e il processo prevede solo due interviste. Sebbene riduca i tempi rispetto allo standard, la mancanza di uno screening iniziale formale appesantisce la prima interview con candidati non idonei.

\- \*\*Software Engineer (Senza Task):\*\*

&#x20; - \*Criticità:\* Essendo il ruolo con più volume nel dataset, l'assenza di una task tecnica preliminare sposta tutto il peso della valutazione sulle interviste tecniche (`Tech Interview`), sovraccaricando i Tech Lead e allungando i tempi di decisione.

\- \*\*Ruoli Standard (Screening -> Task -> 3 Interviste):\*\*

&#x20; - \*Criticità:\* Il funnel standard è eccessivamente lungo e ridondante (ben 3 fasi di intervista successive alla task). Questo causa un forte \*drop-off\* e la perdita dei candidati migliori sul mercato a causa della lentezza dell'iter.



\---



\## 🎯 3. Valutazione del Sistema di Valutazione

\- I dati mostrano una disallineamento tra le valutazioni dei CV e il rendimento effettivo nelle fasi successive, evidenziando criteri di screening iniziale poco oggettivi.

\- Le troppe fasi di intervista nei ruoli standard non aggiungono valore incrementale predittivo sulle performance del candidato, ma aumentano drasticamente il \*Time-to-Hire\*.



\---



\## 💡 4. Raccomandazioni \& Proposta di Ristrutturazione



1\. \*\*Introduzione di un Pre-screening Automatizzato / Kill-questions:\*\* Anche per i ruoli senza screening iniziale (o con volumi alti), introdurre un filtro rapido per proteggere il tempo dei recruiter.

2\. \*\*Ottimizzazione del Funnel Standard:\*\* Ridurre le 3 interviste finali a un massimo di 2 (es. \*Culture Fit / Hiring Manager\* + \*Deep Dive Tecnico/Funzionale\*), accorciando drasticamente il time-to-hire.

3\. \*\*Bilanciamento per i Software Engineer:\*\* Introdurre una task asincrona leggera e automatizzata (es. test di logica o coding rapido) per filtrare i candidati prima di impegnare i Senior Engineer nelle interviste live.


## 🧹 1. Metti in Ordine: Data Cleaning & Metriche Chiave

### A. Data Cleaning (Processo di pulizia dei dati)
Il dataset grezzo esportato dall'ATS presentava diverse incoerenze strutturali che sono state corrette per garantire l'affidabilità dell'analisi:
1. **Normalizzazione dei Ruoli:** Sono state uniformate le nomenclature duplicate generate nel sistema (es. fusione del ruolo `SWE` in `Software Engineer` e di `Business Development Representative` in `BDR`).
2. **Standardizzazione Temporale:** Le date di candidatura e di fine processo sono state convertite in formato standard (`YYYY-MM-DD`) per calcolare con precisione i tempi di attraversamento (*Time-in-Stage* e *Time-to-Hire*).
3. **Gestione dei Valori Mancanti:** Sono stati isolati e trattati i record incompleti o con timestamp anomali per evitare distorsioni nei tassi di conversione.
4. **Segmentazione per Categoria:** Il perimetro è stato diviso seguendo le regole di business di Jet HR:
   * *Ruoli Chiusi:* Web Designer e Chief of Staff (processi conclusi durante l'anno, senza screening iniziale).
   * *Ruoli Sempre Aperti:* Tutti gli altri ruoli.
   * *Eccezioni di Funnel:* Software Engineer (privi di task tecnica) e Product Designer (task post-prima intervista).

### B. KPI (Metriche Essenziali Calcolate)
Per valutare l'efficacia e l'efficienza dei processi di selezione sul totale dei **9.995 record** analizzati, sono stati monitorati i seguenti indicatori:
* **Pass-Through Rate (Conversion Rate):** Percentuale di candidati che superano con successo una specifica fase per accedere alla successiva, evidenziando i punti di sbarramento critici.
* **Drop-off Rate:** Tasso di abbandono o scarto dei candidati per singolo step, utile a quantificare l'attrito del funnel.
* **Time-in-Stage / Time-to-Hire:** Durata media in giorni trascorsa dai candidati in ogni fase e durata complessiva del processo fino allo status finale (`Hired`, `Rejected`, `Dropped`, `Active`).

## 🔍 2. Analisi del Funnel e Colli di Bottiglia (Approfondimento)

Analizzando i dati dei processi di selezione, emergono dinamiche differenti a seconda della categoria di ruolo:

1. **Ruoli Standard (Screening -> Task -> 3 Interviste):**
   * *Il problema:* Questo funnel è il più pesante. La presenza di ben 3 interviste successive alla task genera un **drop-off cumulativo elevatissimo**. I candidati migliori ricevono offerte altrove prima di superare l'ultimo step.
   * *Collo di bottiglia:* Le fasi finali di colloquio allungano il *Time-to-Hire* in modo ingiustificato.

2. **Web Designer & Chief of Staff (Ruoli Chiusi):**
   * *Il problema:* L'assenza di screening iniziale e l'invio immediato della Task sovraccaricano il team di recruiting. Vengono corrette task di candidati che non possiedono le competenze di base riscontrabili da un rapido controllo del CV.

3. **Product Designer (Task dopo la 1ª Interview, 2 Interviste totali):**
   * *Il punto di forza:* Strutturalmente è più snello (sole 2 interviste). Tuttavia, manca un filtro iniziale (screening), il che significa che la prima intervista viene sprecata talvolta con candidati non idonei.

4. **Software Engineer (Senza Task, alto volume):**
   * *Il problema:* Essendo il ruolo con più candidature nel dataset, l'assenza di una task tecnica asincrona sposta tutto il carico di lavoro sulle spalle dei Technical Interviewer, rallentando drasticamente la pipeline e creando un collo di bottiglia insostenibile per i senior engineer.

---

## 🎯 3. Valutazione del Sistema di Valutazione
- I dati evidenziano un disallineamento tra le valutazioni iniziali (CV) e l'effettivo superamento delle fasi successive, segno di criteri di screening non sufficientemente standardizzati.
- Gli step attuali in alcuni ruoli creano attrito e frustrazione nei candidati, allungando i tempi senza aggiungere valore predittivo sull'effettiva performance lavorativa.

