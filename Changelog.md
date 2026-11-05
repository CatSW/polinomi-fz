---
title: Changelog TurboAI
copyright: "© 2026 Stefano Vesco (IK0VCK) - CatSW. All rights reserved."
author: IK0VCK
type: changelog
product: polinomi-fz
version: 1.0.0 
license: MIT
updated: 2026-11-05
---
# Changelog Esploratore di Polinomi

Redatto seguendo le convenzioni di [Keep a Changelog](https://keepachangelog.com/it-IT/1.1.0/)

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

