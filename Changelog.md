---
title: Changelog TurboAI
copyright: "© 2026 Stefano Vesco (IK0VCK) - CatSW. All rights reserved."
author: IK0VCK
type: changelog
product: polinomi-fz
license: MIT
updated: 2026-11-07
---
# Changelog Esploratore di Polinomi

Redatto seguendo le convenzioni di [Keep a Changelog](https://keepachangelog.com/it-IT/1.1.0/)

## [1.8] - 2026-11-07

### Added

- «Range pdg» (ex «Finestra R», tooltip «Range Piano di Gauss»): il fondo scala può arrivare a 100. Un clic sull'etichetta, blu e in grassetto come «Attiva la spunta», alterna il fondo scala 10 ↔ 100 senza cambiare il valore né la vista.
- Il valore è ora un input numerico modificabile (frecce e rotella con passo 0,05, valori al centesimo, fino a 100). Oltre 10 la scala estesa si attiva da sola.
- Import da JSON e da link: R fino a 100 rispettato subito. Oltre 10 si sceglie la scala 100, fino a 10 la scala 10.

### Changed

- Con scala 10 attiva e R > 10 (valore digitato o importato), la scala resta estesa: il valore non viene mai troncato. Si può tornare alla scala 10 solo quando R rientra in 0,1–10.
- All'avvio il controllo mostra il valore reale di R (1,8): prima lo slider indicava 2,0 mentre lo stato interno era 1,8.

### Fixed

- Readout del cursore: il separatore «·» alla fine di una riga che va a capo viene nascosto. Vale per il piano di Gauss, la vista sezione e il pannello a schermo intero.
- Importazione di R: il valore era limitato a 10 e arrotondato a 0,1 (vedi causa sotto).

## [1.7] - 2026-11-07

### Added

- Aggiunto nella vista sezione un pannello sovrapposto, visibile in full screen, con tutti i dati del cursore e la stessa formattazione del readout normale.
- Su vista Sezione, aggiunto un pulsante per spostare il pannello della sezione in alto o in basso al centro dell'area del modulo, senza invadere il diagramma della fase e con un controllo utilizzabile anche su mobile.

### Changed

- Differenziato lo sfondo del diagramma della fase da quello del modulo nella vista sezione con una tenue tinta crema, adattata al tema scuro e presente anche in full screen, senza modificare i colori delle curve.
- Spostato il pannello esistente del piano di Gauss in full screen dal basso a sinistra all'alto al centro, mantenendo entrambe le righe con dati del cursore e informazioni tecniche.
- Uniformato lo stile dei pannelli in full screen della sezione e del piano di Gauss: cornice nera sottile, angoli arrotondati, titolo centrato sul bordo superiore e spaziatura compatta. Mantenuti sfondi opachi distinti, grigio molto chiaro per la sezione e bianco per il piano di Gauss, con testo nero in entrambi i temi e visualizzazione sopra gli elementi del grafico.

### Fixed

- Ripristinato il piano di sezione sull'asse reale (offset d = 0 e angolo θ = 0°) alla sostituzione completa della funzione, incluso il caricamento di un esempio, sincronizzando controlli, stato interno e rappresentazione nelle varie viste.
- Preservata la sezione corrente durante l'aggiunta, lo spostamento o la modifica di singole radici, senza interferire con il ripristino di sezioni esplicitamente salvate in viste condivise o importate.

## [1.6] - 2026-11-06

### Added

- Nella vista sezione agiunta la curva Im f(Z) verde puntinata e nel cursore aggiunti Re f(z) e Im f(z) (stessi separatori), aggiunti anche nel cursore del piano di Gauss.
- Nel pannello aperto dall'ingranaggio, aggiunti due checkbox, per defualt marcati, per attivare/disattivare il plot di Re f(z) e Im f(z).
.

## [1.5] - 2026-11-06

### Added

- Lettura dinamica del cursore nella vista sezione, con valore di z complesso, modulo di z, arg di z espressa in gradi, modulo |f(z| e fase arg f(z) espressa in gradi.

### Changed

- Uniformate le letture del cursore della vista sezione e del piano di Gauss nella prima riga delle rispettive didascalie, con prefisso fisso 'Cursore:' e impaginazione stabile.
- Adottato il puntatore a crocetta nel grafico della vista sezione.
- Uniformata la notazione delle etichette comprese quelle accanto alle frecce arancioni e l’etichetta arg f(z) del grafico della fase, senza modificare parametrizzazione o calcoli.

### Fixed

- Corretta la notazione nelle etichette accanto alle frecce della vista sezione: f(z) al posto di f(x).

## [1.4] - 2026-11-06

### Added

- **Vista intersezione piano di sezione** (ex «Vista asse reale»): la terza vista mostra f lungo una retta qualunque del piano di Gauss; il piano di sezione resta ortogonale al piano di Gauss. L'asse reale è il caso d=0, θ=0° (default, identico alla 1.3). Un'icona a ingranaggio apre il pannello di configurazione.
- Geometria condivisa z(t) = u·(t + i·d), con u = e^(iθ): la usano piano di Gauss, vista 3D e grafico di sezione. L'asse orizzontale è etichettato «t — coordinata lungo la sezione»; t=0 è il piede della perpendicolare dall'origine (z₀ = i·d·u), non z=0.
- Modalità A «Offset e angolo»: slider d (da −10 a 10, passo 0,05; l'intervallo si allarga se il valore corrente lo supera) e θ (0°–360°, passo 1°, orientamento geometrico della retta e non fase di f); pulsante «Taglio sull'asse reale (d=0, θ=0°)».
- Modalità B «Due punti»: per ciascuno dei due punti una combo («Punto libero» oppure «Radice k: coordinate») e due slider Re/Im (passo 0,01), disabilitati quando il punto è collegato a una radice. Verso positivo da P₁ a P₂; il pannello mostra t₁, t₂, d e θ derivati. I punti collegati seguono le radici in tempo reale.
- Casi degeneri: con punti coincidenti o numericamente indistinguibili (distanza ≤ 1e-9·(1+|P|)) compare «Servono due punti distinti», viene conservata l'ultima sezione valida e la condizione è segnalata anche nelle altre due viste. Se una radice collegata sparisce o cambia, il punto diventa libero con le ultime coordinate e il pannello lo dice.
- Passaggio tra modalità senza salti: da B ad A gli slider ripartono da d e θ derivati; da A a B si ripristinano i punti precedenti se descrivono ancora lo stesso taglio, altrimenti si creano due punti liberi sulla retta (a t = ∓R/2). Le radici non vengono mai spostate.
- Grafico della fase sotto il grafico principale della terza vista (altezze 3:1, stesso asse t, stesso zoom e panoramica): arg f(z(t)) in [0°, 360°) con atan2. La polilinea si interrompe ai salti 360°↔0° (raccordandosi ai bordi, senza segmenti verticali) e dove la fase non è definita, cioè alle radici note e dove |f| ≤ 1e-9·max|f|; le radici sono segnate con linee rosse punteggiate.
- Piano di Gauss: retta di sezione magenta tratteggiata, ritagliata ai bordi della finestra, con tacchetta «t=0» in z₀.
- Vista 3D: stessa traccia sul piano di Gauss, contorno tratteggiato del piano di sezione ortogonale e tacchetta «t=0».
- Terza vista: pulsante schermo intero a destra di «Zoom radici», con lo stesso comportamento delle altre due viste (espande entrambi i grafici, mantiene il rapporto 3:1).
- Grafico di sezione: i massimi e minimi relativi di Re f compaiono anche quando il polinomio composto lungo la retta ha coefficienti reali (riconosciuti con tolleranza relativa 1e-9, per esempio per θ=180°). Con coefficienti composti complessi non vengono etichettati.
- Editor f(z): tre pulsanti a selezione esclusiva, zⁿ (Forma normale), (z−a) (Forma a radici) e TXT (Testo), con tooltip, nome accessibile, `aria-checked`, bordo verde e segno ✓ sul selezionato.
- Stato: nuovo campo `view.section` (`mode`, `offset`, `angleDeg`, `points` con `root`, `re`, `im`) incluso in salvataggio, «Esporta JSON», «Condividi questa vista» e Annulla/Ripristina.

### Changed

- «Condividi questa vista» è ora un'icona a tre nodi collegati accanto al titolo, a sinistra di «Readme - Ver. x.y», con tooltip; funziona anche con il pannello f(z) chiuso. Il vecchio pulsante nel pannello f(z) è stato rimosso; «Esporta JSON» resta nel pannello in tutte e tre le forme.
- Terza vista: la curva rossa tratteggiata è documentata come Re f(z(t)) (parte reale), non come la funzione complessa; il modulo |f(z(t))| resta blu. Frecce arancioni e pallini rossi seguono la coordinata t; i pallini rossi indicano le radici che appartengono davvero alla retta (tolleranza 1e-9·(1+|z|)).
- Vista 3D: le «Curve reali nel 3D» seguono la retta di sezione e sono limitate al dominio |z| ≤ R (con |d| ≥ R non si disegnano).
- Versione dell'app da 1.3 a 1.4. I file JSON e i link della 1.3 (e precedenti), privi di `view.section`, restano caricabili e ripristinano il taglio sull'asse reale.

### Removed

- Terza vista: pulsante «Auto». L'adattamento automatico dell'intervallo t resta attivo internamente; «Zoom radici» è invariato.

### Known limitations

- Il collegamento di un punto a una radice è per indice, non per identificatore persistente: se le radici vengono rinumerate senza cambiare il loro numero, il punto resta sull'indice.
- Passando da B ad A con un θ non intero lo slider mostra il valore arrotondato; il taglio non salta, ma al primo movimento dello slider l'angolo si aggancia al grado intero.
- Verifiche automatiche eseguite in Chromium headless (desktop e mobile); non eseguite prove su dispositivi reali.

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

