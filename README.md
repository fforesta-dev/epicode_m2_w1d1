# M2 W1D1: JS basics

## 1. Cos'è un algoritmo?

Un algoritmo è una sequenza di istruzioni da seguire in ordine per risolvere un problema. Tutto qui.

L'esempio che uso sempre è la moka. Svito la caffettiera, riempio d'acqua la caldaia fino alla valvola, metto il filtro, lo riempio di caffè senza pressarlo, riavvito e la metto sul fuoco. Quando comincia a borbottare, spengo. Se salto un passaggio, per esempio l'acqua, il caffè non esce e la moka si rovina.

Perché una lista di passaggi sia davvero un algoritmo, ogni istruzione deve essere così chiara che chiunque la esegua faccia esattamente la stessa cosa, e prima o poi la sequenza deve finire. "Metti un po' di caffè" va bene per una persona, che sa interpretare. Per un computer no: lui vuole sapere quanto.

Dentro un algoritmo ci sono spesso delle scelte ("se l'acqua è finita, riempi la caldaia") e delle ripetizioni ("continua a girare finché lo zucchero non si scioglie"). Programmare vuol dire scrivere algoritmi in una lingua che il computer capisce, come JavaScript.

## 2. Cos'è una variabile?

Immagina una scatola con un'etichetta sopra. Sull'etichetta scrivi un nome, dentro metti qualcosa. Quando ti serve quel contenuto non devi ricordarti cos'era: cerchi la scatola con l'etichetta giusta e la apri.

Una variabile è questo. Un nome che il programma usa per ritrovare un valore salvato in memoria.

Si chiama "variabile" perché il contenuto può cambiare. Se tengo il conto dei caffè bevuti oggi, la scatola parte da 0 e a ogni tazza ci metto dentro il numero nuovo. L'etichetta resta la stessa, il valore no.

```js
let caffeBevuti = 0;
caffeBevuti = caffeBevuti + 1; // adesso vale 1
```

In JavaScript le variabili si creano con `let` quando il valore cambierà e con `const` quando deve restare quello (i giorni della settimana, per esempio, sono sempre 7). C'è anche `var`, il modo vecchio: lo trovi ancora nel codice scritto qualche anno fa, ma oggi conviene lasciarlo stare.

```js
const giorniDellaSettimana = 7;
giorniDellaSettimana = 8; // errore: una const non si può riassegnare
```

## 3. undefined e null sono la stessa cosa?

No, anche se tutti e due vogliono dire "qui non c'è niente".

`undefined` è il valore che JavaScript mette da solo quando qualcosa esiste ma nessuno gli ha ancora dato un valore. Una variabile dichiarata e mai riempita vale `undefined`, e lo stesso succede se chiedo a un oggetto una proprietà che non ha.

`null` invece lo scrive il programmatore, apposta. Significa "qui non c'è niente e lo so". Per tornare alle scatole: `undefined` è una scatola che nessuno ha mai riempito, `null` è una scatola che ho svuotato di proposito, con attaccato un biglietto che dice "vuota".

```js
let nome;
console.log(nome);            // undefined: dichiarata, mai assegnata

const utente = { email: null };
console.log(utente.email);    // null: so che manca e l'ho scritto io
console.log(utente.telefono); // undefined: la proprietà non esiste
```

Anche JavaScript li tratta in modo diverso, e in un paio di casi la differenza fa perdere tempo se non la conosci:

```js
null == undefined;   // true: con l'uguaglianza "larga" valgono uguali
null === undefined;  // false: con quella stretta no, sono di tipo diverso

typeof undefined;    // "undefined"
typeof null;         // "object" (un errore delle prime versioni del linguaggio, mai corretto)

Number(null);        // 0
Number(undefined);   // NaN
```

La regola che mi sono dato è semplice: `undefined` lo lascio a JavaScript, e quando voglio dire che un valore manca uso `null`.
