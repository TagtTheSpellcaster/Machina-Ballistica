# Machina Ballistica — Officina degli Enigmi (Macchina N° 002)

![Version](https://img.shields.io/badge/version-1.10-c49a55?style=flat-square)
![License: AGPL v3](https://img.shields.io/badge/License-AGPL_v3-344b3a?style=flat-square)
![HTML5](https://img.shields.io/badge/HTML5-Canvas-21170f?style=flat-square)
![JavaScript](https://img.shields.io/badge/JavaScript-Vanilla-795027?style=flat-square)
![Web Audio API](https://img.shields.io/badge/Audio-Web_Audio_API-a77c42?style=flat-square)

Simulatore di flipper arcade in stile steampunk realizzato in HTML5 Canvas e JavaScript puro, senza dipendenze esterne. Il progetto riproduce la fisica di un tavolo meccanico con lancio a molla caricabile, respingenti, bersagli a scatto, slingshot, sistema di nudge multidirezionale con protezione Tilt, sintesi sonora procedurale e plancia strumentazione a manometri analogici.

[Puoi giocarci qui](https://tagtthespellcaster.github.io/Machina-Ballistica/)

## Caratteristiche principali

- **Motore fisico 2D con sub-stepping**: calcolo continuo delle collisioni segmento-cerchio e cerchio-cerchio per evitare il tunneling della sfera ad alta velocità, con trasferimento angolare reale dalle palette (flipper).
- **Sistema Nudge e Tilt arcade**: spinte istantanee su tre assi (sinistra, destra, dal basso) con risposta elastica del tavolo e accumulo di instabilità (`tiltMeter`), soglia di avviso `DANGER!` e blocco meccanico temporaneo in caso di `TILT`.
- **Plancia analogica steampunk**: batteria di 5 manometri a lancetta per il punteggio (da `×10` a `×100K` con finestrella meccanica), manometro dedicato al record salvato in `localStorage`, indicatore sfere in riserva e lampada di stato.
- **Sintesi audio procedurale (Web Audio API)**: generazione in tempo reale degli effetti meccanici (campane d'ottone per i respingenti, scatti a molla, sfiati di vapore, allarme Tilt) e della colonna sonora di sottofondo, con interruttori indipendenti per effetti e musica.
- **Interfaccia adattiva**: visualizzazione a schermo singolo con plancia laterale su desktop e comandi touch dedicati rilevati automaticamente su dispositivi mobili.

## Struttura dei file

- `index.html` (o `machina-ballistica.html`): applicazione completa self-contained (struttura, stile, motore fisico e sintetizzatore audio).
- `sfondo.jpg`: illustrazione del piano di gioco da posizionare nella stessa directory del file HTML (in assenza del file viene attivato automaticamente un fondale vettoriale di riserva).

## Avvio rapido

1. Scarica o clona il repository assicurandoti che il file HTML e `sfondo.jpg` si trovino nella stessa cartella.
2. Apri il file HTML in qualsiasi browser moderno (Chrome, Firefox, Edge, Safari) oppure servilo tramite un server HTTP locale o GitHub Pages.

## Comandi

### Tastiera (PC)

- **Flipper sinistro**: `Z` oppure `Freccia Sinistra`
- **Flipper destro**: `-` oppure `Freccia Destra`
- **Carica e lancia la sfera**: `Freccia Giù` (tenere premuto per comprimere la molla, rilasciare per lanciare)
- **Nudge da sinistra**: `X`
- **Nudge da destra**: `.` (punto)
- **Nudge dal basso**: `Barra Spaziatrice` (avvia anche il lancio se la sfera è sul pistone)
- **Pausa / Riprendi**: `P`

### Dispositivi touch

- **Flipper SX / DX**: pulsanti dedicati nella fascia inferiore dello schermo
- **Nudge**: pulsante centrale tra i due flipper
- **Carica / Lancia**: pulsante nella plancia comandi

## Regole di punteggio e Tilt

- **Respingenti (Bumper)**: 100, 150 o 250 punti a seconda del componente colpito.
- **Bersagli laterali (Target)**: 50 punti.
- **Slingshot**: 20 punti.
- **Meccanica Tilt**: ogni impulso di nudge aggiunge 35 punti al contatore di instabilità (che decade di 20 punti al secondo). Superati i 65 punti viene segnalato `DANGER!`; al raggiungimento di 100 punti la macchina entra in `TILT`, disabilitando flipper, respingenti e conteggio punti fino alla perdita della sfera in gioco.

## Licenza

Questo progetto è distribuito sotto licenza **GNU Affero General Public License v3.0 (AGPL-3.0)**. Consulta il file `LICENSE` o il testo ufficiale della [GNU AGPL v3.0](https://www.gnu.org/licenses/agpl-3.0.html) per i dettagli su utilizzo, modifica e ridistribuzione.
