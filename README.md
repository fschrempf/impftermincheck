Dieses Repository stellt einen einfachen Benachrichtigungsservice für den Service zum Reservieren von COVID-19 Impfterminen unter https://www.impfterminservice.de bereit. Als Infrastruktur wird [`GitHub Actions`](https://docs.github.com/de/actions) und [Actionsflow](https://github.com/actionsflow/actionsflow) verwendet.

Diese Software steht in keinem Zusammenhang mit den Betreibern von https://www.impfterminservice.de oder sonstigen offiziellen Stellen.

Alle 5 Minuten (kleinstes Intervall, das bei GitHub Actions möglich ist) wird die API des Impftermin-Service abgefragt und bei positivem Ergebnis (Termine verfügbar) eine E-Mail über den konfigurierten Server an die angegebenen Empfänger versendet.

**Achtung**: Bei meinen Tests wurde trotz Schedule im 5-Minuten-Intervall nur sehr unregelmäßig mit größeren Abständen der Job getriggert. Offenbar ist GitHub hier nicht wirklich zuverlässig und es kann daher dazu kommen, dass verfügbare Impftermine, die schnell ausgebucht sind verpasst werden.

This is a workflow repository powered by [Actionsflow](https://github.com/actionsflow/actionsflow), generated from [actionsflow/actionsflow-workflow-default](https://github.com/actionsflow/actionsflow-workflow-default)

# Setup

1. Dieses Repository forken (Button oben rechts)
2. In den Repository-Einstellungen Secrets auswählen und folgende Werte anlegen:
  * `IMPFSTOFFE`  
    Ein kommagetrennte Liste von Impstoff-IDs. Verfügbare Impstoffe können [hier als JSON abgerufen](https://www.impfterminservice.de/assets/static/its/vaccination-list.json) werden (Property `qualification`).  
    Beispiel: `L920,L921,L922`
  * `IZ_ID`  
    URL-ID des Impfzentrum-Servers. Verfügbare Impfzentren können [hier als JSON abgerufen](https://www.impfterminservice.de/assets/static/impfzentren.json) werden (Dresitellige Ziffer am Anfang der URL).  
    Beispiel: `229`
  * `PLZ`  
    Postleitzahl des Impfzentrums  
    Beispiel: `72469`
  * `MAIL_SERVER`  
    E-Mail Server  
    Beispiel: `smtp.gmail.com`
  * `MAIL_PORT`  
    E-Mail Server Port  
    Beispiel: `465`
  * `MAIL_USERNAME`  
    E-Mail Konto Benutzername  
    Beispiel: `max.mustermann@gmail.com`
  * `MAIL_PASSWORD`  
    E-Mail Konto Passwort  
    Beispiel: `12345678`
  * `MAIL_RECIPIENTS`  
    E-Mail Empfänger  
    Beispiel: `max.mustermann@gmail.com,max.musterfrau@gmail.com`
