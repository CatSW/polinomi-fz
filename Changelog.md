---
title: Changelog TurboAI
copyright: "© 2026 Stefano Vesco (IK0VCK) - CatSW. All rights reserved."
author: IK0VCK
type: changelog
product: polinomi-fz
license: MIT
updated: 2026-11-06
---
# Changelog Esploratore di Polinomi

Redatto seguendo le convenzioni di [Keep a Changelog](https://keepachangelog.com/it-IT/1.1.0/)

## [1.3] - 2026-11-05

### Added
- Pannello «Controlli piano»: pulsante «Radice dal piano», collegato alla stessa funzione (`startPick`) del pulsante nell'editor f(z). Con l'editor chiuso o in Forma normale/Testo apre l'editor, passa a «Forma a radici» con i gestori esistenti e avvia la scelta sul piano. Resta disabilitato, con tooltip che ne spiega il motivo, se la scelta è già in corso, se il grado totale è già 8 o se f(z) è costante.
- Grafico sull'asse reale, pulsante «Auto» (attivo di default): sceglie l'intervallo x in modo che i valori molto grandi di |f| non schiaccino radici, minimi e massimi. I valori della funzione non vengono alterati; le caratteristiche rimaste fuori intervallo sono elencate sotto il grafico e «Auto» disattivato ripristina [−R, R].
- Grafico sull'asse reale, coefficienti non tutti reali: frecce arancioni verticali nei punti in cui si annulla solo Re f(x), con l'etichetta «Im f(x) = n» sul lato della coda e anti-sovrapposizione tra etichette. Le vere radici reali (Re f = Im f = 0) sono disegnate come punto rosso, senza freccia.
- Box «Punto scelto», con i bacini di Newton attivi: scritta blu in grassetto «Modalità fase», cliccabile (anche da tastiera) per disattivare i bacini.

### Changed
- Pannello f(z) della vista 3D: «Esporta JSON» e «Condividi questa vista» sono in una riga comune (`#ed-act`), esterna alle sezioni che cambiano con la combo, e sono quindi disponibili in Forma normale, Forma a radici e Testo (prima solo in Testo). Stessi id, gestori e stato dei due comandi.
- Editor f(z), «Forma a radici»: il pulsante «Dal piano» è ora «Radice dal piano».
- Versione dell'app da 1.2 a 1.3 (i file JSON della 1.2 restano caricabili).

### Fixed
- Bacini di Newton (shader WebGL): il test di convergenza usava una soglia fissa |f| < 1e-5, inferiore al rumore di arrotondamento fp32 di f(z) dove i termini del polinomio sono grandi (qui vicino alla radice z₅ ≈ 3.94 − 0.46i, con |z| ≈ 4). La soglia è ora max(1e-5, 4e-7·Σ|c_k||z|^k). La zona risultava nera o granulosa a seconda dell'hardware; ora è classificata allo stesso modo ovunque.

## [1.2] - 2026-11-05

### Changed

**Vista 3D accelerata (WebGL2)**
- Superficie, piano di quota e curva di livello |f| = quota sono disegnati con WebGL2. I vertici vengono caricati sulla GPU solo quando cambiano funzione, dominio, R, altezza, scala logaritmica o palette; ruotare, zoomare o spostare il grafico aggiorna solo la camera.
- La geometria resta calcolata in FP64 sulla CPU (radici, punti critici, valori di sella, Newton, grafico reale, colori); alla GPU va una copia FP32 in coordinate normalizzate.
- Profondità reale (z-buffer). Sopra quota «trasparente»: alpha 0,3 con tessere ordinate da lontano a vicino. Assi, scala |f|, curve reali, punto di Newton, cerchi di riferimento e radici restano disegnati in 2D con gli stessi livelli di prima.
- Poligoni concavi (mesh deformata vicino alle radici) triangolati con ear clipping, così non restano buchi nella superficie.
- Buffer di profondità azzerato a ogni disegno (più disegni nello stesso frame, ad esempio all'avvio o trascinando le radici, non si influenzano).
- Senza WebGL2 accelerato (assente, solo software, shader non compilato, contesto perso) la vista usa il disegno Canvas 2D della 1.1 e lo dice sotto la figura.

**Altre ottimizzazioni**
- Un solo ridisegno 3D per frame anche con molti eventi di puntatore/rotella.
- Colori del tema in cache (niente `getComputedStyle` a ogni frame).
- Quota |f| e «Anima |f|» aggiornano solo testo, piano e 3D (non più Newton e grafico reale).
- Ricalcolo delle altezze senza costruire stringhe colore per quad.

**Compatibilità**
- JSON e link espongono versione 1.2; i file della 1.1 si aprono invariati.
- La rotazione automatica resta di 0,008 rad per frame, come nella 1.1 (non dipende dal tempo).

### Fixed

- Piano di Gauss: dopo il cambio di risoluzione dell'anteprima durante il trascinamento di una radice il canvas WebGL viene ridisegnato subito (prima restava vuoto per un frame: lampo bianco).

## [1.1] - 2026-11-02

### Added

- Pubblicazione dell’app su GitHub Pages.
- Pulsante Info con collegamento al README.
- Pulsante “Condividi questa vista” copia nella clipboard di sistema URL con parametri codificati in Base64.

### Changed

- Aggiornamento del manuale con le nuove funzionalità.

### Fixed

- Correzione dei collegamenti all’app nel README.
- Aggiunta di `index.html` con reindirizzamento all’app dall’indirizzo base del sito.

## [1.0] - 2026-10-31

### Added

- Esploratore_di_Polinomi_Ver_1.0.html - App html5 utilizzabile su computer o mobile
- Manuale_Esploratore_polinomi.md
- Cubica.md - alcune note sulla funzione cubica usata come spunto iniziale per la realizzazione di questa app.
- 
- Pubblicazione prima versione pubblica. Sviluppata nei CatSW labs su workstation HAL9000-MK2
  - (versione alpha CR interna prima della pubblicazione 7.8)

---  

[@IK0VCK]: https://github.com/IK0VCK

