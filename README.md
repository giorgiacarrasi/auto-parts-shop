# Database Module - Exam 

## Preface
Si desidera automatizzare il sistema di gestione di un magazzino di ricambi per auto.
Le specifiche del sistema, acquisite attraverso intervista, sono quelle nel seguito riportate.
Analizzare tali specifiche, filtrare le ambiguità presenti e poi raggrupparle in modo omogeneo.
Individuare i collegamenti esistenti tra i vari gruppi di specifiche così ottenuti.
Realizzare la progettazione del modello concettuale e rappresentare le specifiche (dopo la fase di
riorganizzazione) con uno schema del modello Entità-Relazione. Effettuare la progettazione logica
della base di dati del sistema informativo e una sua implementazione sia nel modello relazionale
che in un modello non relazionale basato sulla gestione dei documenti.

## Specifications
Si consideri una base di dati che contiene informazioni sugli acquisti dei clienti di un negozio di
ricambi per auto.
Dei clienti interessano il codice fiscale o la partita iva, che li identifica, il nome, l’indirizzo di residenza
completo di CAP, città, provincia e regione.
Di ogni spesa di un cliente interessano il numero della fattura, che la identifica, la data, il totale della
spesa, la modalità del pagamento (elettronico, contante) e, per ogni prodotto, la quantità, il prezzo
pagato e l’eventuale sconto praticato (prodotto in promozione).
Di ogni ricambio interessano il codice, che lo identifica, la descrizione, la categoria, i veicoli
compatibili, il costo unitario e il prezzo di vendita. I prodotti possono essere interessati da
promozioni, con riduzione temporanea del prezzo, a partire da una certa data e per un numero
prefissato di giorni.

## Required SQL queries 

1. Per uno specifico cliente, determinare le quantità di ciascun prodotto acquistato in un
determinato periodo;
2. Per un determinato prodotto, determinare il numero dei clienti distinti che lo hanno
acquistato in un determinato periodo;
3. Individuare tutti i clienti che hanno acquistato un prodotto in promozione, indicandone il
CAP di residenza;
4. Per uno specifico CAP, individuare i clienti che hanno fatto acquisti in un determinato
periodo;
5. Per uno specifico modello d’auto, individuare il fatturato degli articoli in un determinato
periodo;
6. Per ciascun articolo in promozione determinarne la quantità venduta in un determinato
periodo;
7. I clienti che non hanno effettuato un pagamento elettronico nell’anno in corso;
8. Il cliente che ha speso di più in un determinato periodo;
9. Per uno specifico CAP la spesa media per fattura in un determinato periodo;
10. Per ciascuna categoria di prodotti il totale del prezzo pagato per quelli venduti in un
determinato periodo.

## Analysis 

### Assumptions
Dato il corrente database si effettuano le seguenti assunzioni: 
-	Si assume che all’interno del database sono presenti tutte le Regioni, Province, Città e CAP italiani. 
-	Ogni cliente presente nel database ha acquistato almeno una volta presso il magazzino di ricambi per auto;
-	Ogni prodotto appartiene a una sola categoria;
-	Ogni ricambio è compatibile a uno o più veicoli; 
-	Il numero fattura equivale allo scontrino di avvenuto acquisto;
-	A una promozione appartengono uno o più prodotti;
-	Un prodotto può avere 0 o N promozioni;
-	Se il Brand è presente ha almeno un veicolo nel database;
-	
## Key-points related to the main entities: 
-	Key-points related to Customer: For each customer it’s known about name, surname, identifiy code and residence address. A customer could be a Company or a Private Customer.
-	Key-points related to Order: For each order that is placed it’s known a identify code and the data where order has been placed. Each order contains one or more products.
-	Key-points related to Vehicle: For each vehicle it’s known a identify code and the name vehicle. Each vehicle is producted by a Brand that we identify with a ID code and the brand name. 
-	Key-points related to Product: Each product is marked with a identify code, the name, a short description, the selling price, the unit cost price. A product could be on sale or not. If the product is on sale it’s known a identifier code that mark the product on sale, the percentage off, and the data where promotion starts and ends. 
-	Key-points related to Payment: When an order is placed the customer does the payment. The payment could be with cash or electronic. For the last one we know also the identifier transaction code.
