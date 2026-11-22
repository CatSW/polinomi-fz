# Esplorazione delle Radici Complesse dei Polinomi

> Prendendo in mano una calcolatrice capace di eseguire calcoli nel dominio complesso, se si calcola la radice $n$-esima di un numero negativo, si ottiene un singolo valore. Usiamo l'Esploratore di Polinomi per vedere dove sono finite le altre radici!

Questo documento raccoglie i fondamenti teorici, il metodo di calcolo (con riferimenti all'HP 28S) e gli esempi pratici per ricavare tutte le radici nel piano complesso.

---

## 1. Fondamenti Teorici

### Teorema Fondamentale dell'Algebra
Ogni polinomio di grado $n$ a coefficienti complessi (e quindi anche a coefficienti reali) ammette **esattamente $n$ radici** nel piano complesso (piano di Gauss), contate con la loro molteplicità.

### Teorema di Coniugazione Complessa
Se un polinomio ha **tutti i coefficienti reali**, le sue eventuali radici non reali si presentano sempre in **coppie di numeri complessi coniugati** (ovvero della forma $a + ib$ e $a - ib$, simmetriche rispetto all'asse reale).

---

## 2. Metodo Operativo per la Calcolatrice (Ricerca di tutte le radici)

Molte calcolatrici scientifiche (come la HP 28S), quando viene richiesta la radice $n$-esima di un numero, restituiscono esclusivamente la **soluzione principale** (quella con l'argomento minimo).

Per ricavare tutte le altre $n-1$ radici distribuite simmetricamente sul piano complesso:

1. **Calcolo dell'angolo di rotazione ($\Delta\theta$):**
   Si divide l'angolo giro ($360^\circ$ o $2\pi$ radianti) per l'indice $n$ della radice:
   $$\Delta\theta = \frac{360^\circ}{n}$$

2. **Moltiplicazione per il versore di rotazione:**
   Si moltiplica ripetutamente la soluzione principale per un numero complesso unitario (versore) di modulo $1$ e argomento $\Delta\theta$ (in forma cartesiana $\cos(\Delta\theta) + i\sin(\Delta\theta)$). 
   *Nota:* È fondamentale **moltiplicare** e non sommare, poiché nel piano complesso la moltiplicazione per un versore equivale a una rotazione pura.

---

## 3. Esempi Pratici

### Caso A: Radice cubica di un numero negativo ($\sqrt[3]{-27}$)
Equazione associata: $x^3 + 27 = 0$ (Polinomio di grado $n = 3$ a coefficienti reali).

* **Radice reale:** Calcolabile direttamente (o tramite il trucco del segno applicato al valore assoluto dell'inverso della potenza: $\text{sgn}(-27) \cdot |-27|^{1/3} = -3$).
* **Radici complesse:** Essendo un polinomio di grado 3 con una radice reale, le restanti due devono formare una coppia complessa coniugata.
  * La calcolatrice fornisce la radice principale: $z_1 = 1.5 + 2.598i$ (modulo $3$, angolo $60^\circ$).
  * Per trovare la seconda radice complessa ($z_2$), è sufficiente calcolare il **complesso coniugato** di $z_1$ (o ruotare di $\frac{360^\circ}{3} = 120^\circ$): $z_2 = 1.5 - 2.598i$ (angolo $-60^\circ$ o $300^\circ$).

🔗 **Link al programma (Esploratore di polinomi - Caso A):**

[🚀 Radice cubica di -27 -> f(z) = z^3 + 27](https://catsw.github.io/polinomi-fz/Esploratore_di_Polinomi.html#v=eyJhcHAiOiJwb2xpbm9taS1meiIsInZlcnNpb24iOiIyLjgiLCJmIjp7ImNvZWZmcyI6W1syNywwXSxbMCwwXSxbMCwwXSxbMSwwXSxbMCwwXSxbMCwwXSxbMCwwXSxbMCwwXSxbMCwwXV19LCJ2aWV3Ijp7IlIiOjYuNCwibGV2ZWwiOjEwOC41NCwiaGVpZ2h0IjoxLCJvZmZzZXQiOjAuMTIsImRvbWFpbiI6InBvbGFyIiwiaGFsZlBsYW5lIjpmYWxzZSwiYWJvdmVMZXZlbCI6ImdoIiwicGhhc2VQYWxldHRlIjoiYXR0IiwiYmFuZHMiOnRydWUsImxvZ0hlaWdodCI6dHJ1ZSwicmVhbEN1cnZlczNEIjp0cnVlLCJhdXRvUm90YXRlIjpmYWxzZSwiYW5pbWF0ZSI6ZmFsc2UsImxheW91dCI6IjEiLCJuZXd0b24iOnsib24iOmZhbHNlLCJpdGVyYXRpb25zIjoyMCwiYmFzaW5QYWxldHRlIjoiYXR0In0sInNlY3Rpb25WaXNpYmxlIjp0cnVlLCJncmFwaGljcyI6eyJzbW9vdGgiOmZhbHNlLCJ1cHBlckxpZ2h0IjpmYWxzZSwibG93ZXJMaWdodCI6ZmFsc2UsInNvZnRib3hVcHBlciI6ZmFsc2UsInNvZnRib3hMb3dlciI6ZmFsc2UsImludGVuc2l0eSI6eyJzcG90VXBwZXIiOjgxLCJzb2Z0Ym94VXBwZXIiOjgxLCJzcG90TG93ZXIiOjgxLCJzb2Z0Ym94TG93ZXIiOjgxfSwibGlnaHRNYXJrZXJzIjpmYWxzZSwibWF0ZXJpYWwiOiJtYXR0ZSJ9LCJjYW1lcmEiOnsieWF3IjowLjM4OTUyLCJwaXRjaCI6MC4xNjA5NSwiem9vbSI6MX0sImNlbnRlcjNEIjp7InJlIjowLCJpbSI6MH0sInBsYW4iOnsiY3giOjAsImN5IjowLCJzY2FsZSI6Ni40fSwicHJvYmUiOlswLjU1LDAuODVdLCJzZWN0aW9uIjp7Im1vZGUiOiJBIiwib2Zmc2V0IjowLCJhbmdsZURlZyI6MCwic2hvd1JlIjp0cnVlLCJzaG93SW0iOnRydWUsInBvaW50cyI6W3sicm9vdCI6bnVsbCwicmUiOi0xLCJpbSI6MH0seyJyb290IjpudWxsLCJyZSI6MSwiaW0iOjB9XX0sInNlY3Rpb25WaWV3Ijp7Im1vZGUiOiJhdXRvIn19fQ)

---

### Caso B: Radice quarta di un numero negativo ($\sqrt[4]{-81}$)
Equazione associata: $x^4 + 81 = 0$ (Polinomio di grado $n = 4$ con $81 = 3^4$, a coefficienti reali).

* **Radici reali:** Nessuna (un numero elevato a potenza pari non può dare un risultato negativo nel campo reale).
* **Radici complesse:** Ci sono $4$ radici complesse (due coppie di complessi coniugati), disposte ai vertici di un quadrato inscritto in una circonferenza di raggio $3$.
* **Procedimento sulla calcolatrice:**
  1. **Radice principale ($z_1$):** La calcolatrice restituisce $2.121 + 2.121i$, che in forma polare corrisponde a modulo $3$ e angolo $45^\circ$.
  2. **Angolo di rotazione:** $\Delta\theta = \frac{360^\circ}{4} = 90^\circ$. Il versore corrispondente è $0 + 1i$, ovvero $(0, 1)$ in notazione cartesiana.
  3. **Seconda radice ($z_2$):** Moltiplicando $z_1$ per $(0, 1)$ si ruota di $90^\circ$ arrivando a $45^\circ + 90^\circ = 135^\circ$ (II quadrante):
     $$z_2 = -2.121 + 2.121i$$
  4. **Terza radice ($z_3$):** Moltiplicando ancora per $(0, 1)$ si ruota a $135^\circ + 90^\circ = 225^\circ$ (III quadrante):
     $$z_3 = -2.121 - 2.121i$$
  5. **Quarta radice ($z_4$):** Moltiplicando un'ultima volta per $(0, 1)$ si ruota a $225^\circ + 90^\circ = 315^\circ$ o $-45^\circ$ (IV quadrante):
     $$z_4 = 2.121 - 2.121i$$

🔗 **Link al programma (Esploratore di polinomi - Caso B):**

[🚀 f(z) = z^4 + 81](https://catsw.github.io/polinomi-fz/Esploratore_di_Polinomi.html#v=eyJhcHAiOiJwb2xpbm9taS1meiIsInZlcnNpb24iOiIyLjgiLCJmIjp7ImNvZWZmcyI6W1s4MSwwXSxbMCwwXSxbMCwwXSxbMCwwXSxbMSwwXSxbMCwwXSxbMCwwXSxbMCwwXSxbMCwwXV19LCJ2aWV3Ijp7IlIiOjQsImxldmVsIjoyMTUsImhlaWdodCI6MSwib2Zmc2V0IjowLjA1LCJkb21haW4iOiJwb2xhciIsImhhbGZQbGFuZSI6ZmFsc2UsImFib3ZlTGV2ZWwiOiJnaCIsInBoYXNlUGFsZXR0ZSI6ImF0dCIsImJhbmRzIjp0cnVlLCJsb2dIZWlnaHQiOmZhbHNlLCJyZWFsQ3VydmVzM0QiOnRydWUsImF1dG9Sb3RhdGUiOmZhbHNlLCJhbmltYXRlIjpmYWxzZSwibGF5b3V0IjoiMSIsIm5ld3RvbiI6eyJvbiI6ZmFsc2UsIml0ZXJhdGlvbnMiOjIwLCJiYXNpblBhbGV0dGUiOiJhdHQifSwic2VjdGlvblZpc2libGUiOnRydWUsImdyYXBoaWNzIjp7InNtb290aCI6ZmFsc2UsInVwcGVyTGlnaHQiOmZhbHNlLCJsb3dlckxpZ2h0IjpmYWxzZSwic29mdGJveFVwcGVyIjpmYWxzZSwic29mdGJveExvd2VyIjpmYWxzZSwiaW50ZW5zaXR5Ijp7InNwb3RVcHBlciI6ODEsInNvZnRib3hVcHBlciI6ODEsInNwb3RMb3dlciI6ODEsInNvZnRib3hMb3dlciI6ODF9LCJsaWdodE1hcmtlcnMiOmZhbHNlLCJtYXRlcmlhbCI6Im1hdHRlIn0sImNhbWVyYSI6eyJ5YXciOi0wLjE5NzE0LCJwaXRjaCI6MC4zMzA0OCwiem9vbSI6MX0sImNlbnRlcjNEIjp7InJlIjowLCJpbSI6MH0sInBsYW4iOnsiY3giOjAsImN5IjowLCJzY2FsZSI6NH0sInByb2JlIjpbMC41NSwwLjg1XSwic2VjdGlvbiI6eyJtb2RlIjoiQSIsIm9mZnNldCI6MCwiYW5nbGVEZWciOjAsInNob3dSZSI6dHJ1ZSwic2hvd0ltIjp0cnVlLCJwb2ludHMiOlt7InJvb3QiOm51bGwsInJlIjotMSwiaW0iOjB9LHsicm9vdCI6bnVsbCwicmUiOjEsImltIjowfV19LCJzZWN0aW9uVmlldyI6eyJtb2RlIjoiYXV0byJ9fX0)

---

## 4. Note Aggiuntive e Osservazioni Personali

- Nel caso della radice cubica di -27 `dal Manuale HP 28S: §hp28s-om-en.pdf:284`

```TXT
Q: When I calculate the cube root of —27, why isn’t the result —3?

A: Every number has three cube roots, two of which are complex
numbers. The HP-28S returns one of the three roots, called the 
principal value. For positive real arguments the principal value 
is the real root; for negative real arguments the principal value 
is one of the complex roots. To calculate the real bth root of 
a real number a, key in the following program:

   <<  -> a b 'SIGN(a)*ABS(a)^INV(b)' >>

Press 

   'RROOT STO

to store the program in a variable RROOT (real root). 
You can then find the real cube root of —27 by typing:

   27 CHS ENTER 3 RROOT ENTER

P. 284
```

Qui usa il trucchetto indicato al §3 ma se vogliamo generalizzare conviene moltiplicare la radice calcolata per un versore con argomento pari a 360° / n dove n è la molteplicità della radice. Ad ogni moltiplicazione avremo una rotazione della nostra radice attorno all'origine ed otterremo così tutte le nostre n radici. Per una generica radice ennesima di un numero negativo avremo sempre una radice reale negativa se $n$ dispari più (n-1)/2 coppie coniugate di radici complesse.
Per $n$ pari (con un numero reale negativo, come $-81$) non ci sono radici reali e ci sono $n/2$ coppie coniugate.  

Possiamo vedere che tutte le radici giacciono su un cerchio con centro nell'origine e raggio pari all'abs di una qualsiasi radice. Possiamo vedere le radici come n vettori applicati nell'origine tutti con stesso modulo pari all'abs della radice e con fase, che presa la prima radice con argomento minore, viene ruotata ad ogni radice di 360°/n (lo puoi vedere sul piano di Gauss nell'esploratore di polinomi).
