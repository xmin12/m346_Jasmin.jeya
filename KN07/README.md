# KN07: Kostenberechnung
<hr>

# A) Kostenrechnung erstellen 

## - 1) Rehosting

## AWS
![image](https://github.com/xmin12/m346_Jasmin.jeya/assets/112725311/1cb6c996-a5d0-429f-bb63-d833abb7dd3f)
## Azuru
![image](https://github.com/xmin12/m346_Jasmin.jeya/assets/112725311/a280c616-3528-4da0-9487-696573046ab2)
### Vergleich:
AWS ist bei gleicher Dienstleistung günstiger als Azure. AWS bietet schnellere Backups und einen
leistungsstarken Webserver, aber der Load Balancer ist kostenpflichtig und der Datenbankserver teurer als bei Azure.

Azure hingegen bietet einen kostenlosen Load Balancer und eine 
günstigere Datenbank mit 128 GB Speicher. Allerdings erfordert der Webserver 
zusätzlichen Speicher, ohne dass zusätzliche Ressourcen hinzugefügt werden können.

### Auswahl:
Die Wahl zwischen AWS und Azure hängt von individuellen Anforderungen und Budgets ab.
Beide Anbieter haben Vor- und Nachteile, daher ist es wichtig, die spezifischen Bedürfnisse
sorgfältig zu prüfen, um die beste Option auszuwählen.
<hr>

## - 2) Replatforming
## Heruko
![Screenshot 2023-10-02 111112](https://github.com/xmin12/m346_Jasmin.jeya/assets/112725311/425404ff-fc91-4eb3-8e18-ad7666edac15)

### Auswahl:
Aufgrund der begrenzten Konfigurationsmöglichkeiten bei Heroku habe ich 
stets die Konfiguration gewählt, die die Mindestanforderungen erfüllt. Dies hat jedoch dazu geführt,
dass meine Konfiguration oft teurer ist als notwendig. Eco und Basic waren zu$
knapp bemessen, daher habe ich die Production-Stufe genutzt. Bei Standard 2x ist 
der 1GB RAM etwas knapp, aber die nächsthöhere Stufe wäre zu teuer. Die Datenbank 
verfügt über 256GB Speicher, da die kleinere Option nur 64GB bietet. Andere Optionen 
wurden ausgelassen, da sie nicht benötigt wurden.
<hr>

## - 3) Repurchasing
## Zoho CRM 
![Screenshot 2023-10-03 113204](https://github.com/xmin12/m346_Jasmin.jeya/assets/112725311/a9a73c31-5b94-4cae-9489-bb96b69cb4c3)
- 23 x 16 = 368 Euro per Monat 
## SalesForce Sales Cloud
![Screenshot 2023-10-03 112906](https://github.com/xmin12/m346_Jasmin.jeya/assets/112725311/c96de5c8-35c6-4a12-9a9b-4ba251d66ae8)
- 25 x 16 = 400 Euro per Monat
  
### Auswahl:
Ich habe mich für die kostengünstigste Option, nämlich Zoho, entschieden. 
Obwohl die Preise immer noch recht hoch sind, bietet Zoho mehr Features als Salesforce.

##  Welches wählen Sie und wieso? Was müsste man zusätzlich beachten?
- ### SaaS (Software as a Service):
  Ein Beispiel für SaaS ist Zoho. Bei SaaS-Diensten ist keine Hintergrundkonfiguration erforderlich;
  stattdessen erhält man im Grunde genommen ein fertiges Produkt. SaaS-Lösungen sind in der Regel einfach einzurichten,
  aber sie können auch relativ teuer sein.

- ### PaaS (Platform as a Service):
  Heroku ist ein Beispiel für PaaS. Bei PaaS-Diensten muss man sich nicht um die Serverkonfiguration kümmern,
  benötigt jedoch Programmierkenntnisse im Gegensatz zu SaaS. Die Einrichtung von PaaS ist nicht so komplex wie
  bei IaaS und oft kostengünstiger als SaaS, solange man nicht die Software selbst entwickeln muss.

- ### IaaS (Infrastructure as a Service):
  AWS EC2 ist ein Beispiel für IaaS. Hier muss man alles selbst konfigurieren und aufsetzen.
  IaaS bietet mehr Möglichkeiten als die anderen Optionen und ist oft die kostengünstigste Wahl.
  Allerdings ist es auch deutlich komplexer und erfordert ein gewisses Maß an Fachwissen, um eingerichtet zu werden.

<hr>

# B) Interpretation der Resultate 

## Interpretieren Sie die Resultate der Varianten u.a. mit den folgenden Fragen: 
### - wie stark unterscheiden sich die Angebote? 
Die drei Optionen (Rehosting, Replatforming und Repurchasing) weisen zwar Unterschiede auf. 
Die Preisunterschiede zwischen den verschiedenen Optionen sind signifikant.
Das Rehosting bei AWS ist die kostengünstigste Option,
während das Replatforming von Heroku am teuersten ist. 
Dies liegt daran, dass bei Heroku eine bessere Konfiguration ausgewählt wurde, 
da die Auswahlmöglichkeiten begrenzt sind.

### - Welches ist das billigste? 
Wenn man die Wahl auf eine der beiden Optionen, AWS oder Zoho, 
beschränken müsste, wäre AWS aufgrund seiner niedrigeren Preise die wahrscheinlichere Wahl.

### - Wieso ist eines davon viel teurer? Ist es aber wirklich teurer?
Die Angebote unterscheiden sich in erster Linie aufgrund der
Dienstleistungen und Konfigurationen, die sie bieten.
Ein höherer Preis kann durch zusätzliche Funktionen, Leistung oder Ressourcen gerechtfertigt sein, was in einigen Fällen sinnvoll sein kann. Es ist wichtig, 
die individuellen Anforderungen und Budgets zu berücksichtigen, um die beste Option auszuwählen. In diesem Fall ist "teurer" nicht zwangsläufig schlechter, 
sondern kann auf eine höhere Leistung oder 
erweiterte Funktionen hinweisen, die möglicherweise erforderlich sind.


















