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

