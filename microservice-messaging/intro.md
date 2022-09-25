Asynchrone Microservices
------------------------

![](https://github.com/mc-b/duk/raw/master/data/jupyter/demo/images/Microservices-Messaging.png)

Quelle: Buch Microservices Rezepte
- - -

Das System besteht aus einem Microservice **order**, der eine Bestellung über die Weboberfläche entgegennimmt. 

Die Bestellung schickt der Bestellprozess dann als Record über Kafka an den Microservice für den Versand **shipping** und den Microservice für die Erstellung der Rechnung **invoicing**.

Die Bestellung wird als JSON übertragen. So können der Rechnungs-Microservice und der Versand-Microservice aus der Datenstruktur jeweils die Daten auslesen, die für den jeweiligen Microservice relevant sind.

Der Versand-Microservice und der Rechnungs-Microservice speichern die Informationen aus den Records in ihren eigenen Datenbank-Schemata. Alle Microservices nutzen eine gemeinsame Postgres-Datenbank.