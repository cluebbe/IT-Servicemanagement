# 🏦 ITSM Workshop: Praxisfall „Cantara Bank AG" – Teil 2

> **Zielgruppe:** Teilnehmende mit Grundkenntnissen in IT Service Management  
> **Dauer:** ca. 4–5 Stunden  
> **Format:** Gemischte Einzel- und Gruppenaufgaben mit ausklappbaren Teillösungen  
> **Hinweis:** Dieser Teil ist **eigenständig** aufgebaut. Er kann unabhängig von Teil 1 besucht werden – alle dafür nötigen Fakten aus der Unternehmensanalyse sind unten enthalten. Wer Teil 1 bereits absolviert hat, findet einige dieser Fakten als bekannte Ergebnisse wieder.

---

## 📋 Ausgangslage: Das Unternehmen

Die **Cantara Bank AG** ist eine mittelgrosse Schweizer Retail-Bank mit ca. 2 500 Mitarbeitenden an 35 Standorten. Die IT-Abteilung beschäftigt 180 Personen und betreibt intern alle bankfachlichen Anwendungen sowie die Arbeitsplatz-Infrastruktur.

### Symptome & aktuelle Probleme

In den letzten sechs Monaten häufen sich Beschwerden aus dem Business:

- **Filialmitarbeitende** können das Kernbankensystem „CoreBanking 360" an durchschnittlich 3 Tagen pro Monat nicht nutzen (Ausfälle zwischen 20 Minuten und 4 Stunden).
- **Trader im Handelsraum** erhalten nach einem Passwort-Reset durchschnittlich 6 Stunden keinen Zugriff auf ihr Trading-Terminal.
- Die IT-Abteilung führt mehrmals wöchentlich Notfall-Änderungen am Produktionssystem durch – häufig ohne vorangehende Risikoabschätzung.
- Ein Serverausfall im Datacenter vor drei Wochen traf 15 Business-Anwendungen gleichzeitig. Die IT wusste nicht, welche Anwendungen auf dem betroffenen Server liefen.
- Es existiert **kein Servicekatalog**. Anfragen der Leistungsbezieher werden per E-Mail an verschiedene IT-Teams gesendet; die Bearbeitungszeit ist unvorhersehbar.

### Organisationsstruktur IT (vereinfacht)

```
CIO (= IT-Leitung)
├── Infrastruktur & Betrieb (60 MA)
│   ├── Datacenter & Storage
│   ├── Netzwerk
│   └── Workplace & Printing
├── Anwendungsentwicklung & -betrieb (80 MA)
│   ├── CoreBanking
│   ├── Trading-Systeme
│   └── Collaboration (Mail, Teams)
└── IT-Governance & Prozesse (10 MA)
    └── Service Desk (30 MA, extern vergeben)
```

> **CIO** (*Chief Information Officer*), auch **(oberste) IT-Leitung** genannt → oberste IT-Führung in der Geschäftsleitung; verantwortet IT-Strategie, Budget und den gesamten IT-Bereich.

### Bereits identifizierte Business IT Services (Ergebnis aus Teil 1, Aufgabe 1.1)

Für die Aufgaben in diesem Teil gelten folgende **fünf BITS** als gegeben:

| Business IT Service | Hauptdienstleistungselement | Mögliche Varianten |
|---|---|---|
| Arbeitsplatz-Service (Desktop/Laptop) | Managed-Arbeitsplatz | Standard, Hohe Sicherheit, High End |
| Mail & Collaboration BITS | Managed-Arbeitsplatz | Standard (Filialen), Enhanced (Management) |
| Trading-Terminal BITS | Managed-Anwendungen | Standard Trader, Senior Trader |
| CoreBanking 360 BITS | Managed-Anwendungen | Filiale Standard, Filiale Erweitert, Back Office |
| Netzwerkdruck BITS | Managed-Arbeitsplatz | Lokal, Zentral/Follow-Me-Print |

### Bereits definierte SLA-Eckwerte für CoreBanking 360 BITS (Ergebnis aus Teil 1, Aufgabe 4.1)

| SLA-Kriterium | Filialen | Back-Office | Night-Batch |
|---|---|---|---|
| Service-Zeit | Mo–Fr 07:30–19:00 | Mo–Fr 07:00–20:00 | Täglich 22:00–04:00 |
| Verfügbarkeit/Monat | 99,5% | 99,0% | 99,8% |
| Reaktionszeit P1 | 15 min | 15 min | 30 min (Bereitschaft) |
| Wiederherstellungszeit P1 | 2 Stunden | 3 Stunden | 1 Stunde |

---

## 🧩 Modul 7 – Prozess-Management-Organisation

### Hintergrundinformation

Damit ein IT-Prozess nicht nur auf dem Papier existiert, braucht es zwei **Governance-Rollen**, die von den operativen Prozessrollen (z.B. Change Manager, Incident Manager) zu unterscheiden sind:

- **IT Process Owner:** i.d.R. ein Mitglied der Bereichsleitung. Verantwortet einen oder mehrere Prozesse **strategisch**: stellt sicher, dass ein IT Process Manager bestimmt ist, nimmt grössere Prozessänderungen ab, vertritt Ressourcenbedarf (z.B. für bessere Tool-Unterstützung) im Führungsteam, präsentiert die Prozess-KPIs in Führungs-Meetings und führt periodisch Prozess-Audits durch.
- **IT Process Manager:** verantwortet die **Definition, Umsetzung, Schulung und Kontrolle** eines einzelnen Prozesses im Alltag – erstellt und wartet die Prozessdokumentation, schult die Prozessrollenträger und überwacht die Einhaltung.

Wird ein Prozess in einem Bereich nicht eingehalten (z.B. weil Mitarbeitende aus einem anderen Bereich ihn ignorieren), kann der IT Process Manager dies **über seinen IT Process Owner** eskalieren – dieser klärt es über die Führungshierarchie.

> **Wichtig:** Die Zuordnung eines Prozesses zu einem Organisationsbereich bedeutet nicht, dass der Prozess nur dort gilt – sie legt nur fest, **wer** die Owner- und Manager-Rolle stellt.

---

### Aufgabe 7.1 – Process Owner und Process Manager zuordnen

Ordnet den sieben aus Teil 1 bekannten ITSM-Prozessen je einen **IT Process Owner** (einen der drei Cantara-Bereiche) und einen **IT Process Manager** (konkrete Rolle/Team) zu. Begründet eure Wahl.

| Prozess | IT Process Owner (Bereich) | IT Process Manager (Rolle/Team) | Begründung |
|---|---|---|---|
| Incident Management | | | |
| Problem Management | | | |
| Change Management | | | |
| Service Level Management | | | |
| Service Asset & Config. Mgmt. | | | |
| Service Request Management | | | |
| Service Catalog Management | | | |

<details>
<summary>💡 Teillösung Aufgabe 7.1</summary>

| Prozess | IT Process Owner (Bereich) | IT Process Manager (Rolle/Team) | Begründung |
|---|---|---|---|
| **Incident Management** | IT-Governance & Prozesse | Incident Manager (Service Desk-nah) | Der Service Desk als Ersteintritt für Incidents ist dort organisatorisch verankert |
| **Problem Management** | Anwendungsentwicklung & -betrieb | Problem Manager, angesiedelt bei CoreBanking/Trading | Grundursachenanalyse ist primär eine technische, entwicklungsnahe Tätigkeit |
| **Change Management** | IT-Governance & Prozesse | Change Manager (siehe Teil 1, Aufgabe 3.2) | CAB-Vorsitz liegt dort, zentrale Koordinationsstelle für alle Bereiche |
| **Service Level Management** | IT-Governance & Prozesse | SLA-Verantwortlicher | Verhandelt Serviceziele mit dem Business, braucht bereichsübergreifenden Blick |
| **SACM** | Infrastruktur & Betrieb | CMDB-Verantwortlicher (Datacenter & Storage) | Technische CIs (Server, Storage, Netzwerk) entstehen und ändern sich primär dort |
| **Service Request Management** | IT-Governance & Prozesse | Service Desk Teamleiter | Anfragen laufen organisatorisch über den Service Desk |
| **Service Catalog Management** | IT-Governance & Prozesse | SLA-Verantwortlicher (Doppelfunktion mit SLM) | Katalog und SLAs hängen inhaltlich eng zusammen (siehe Modul 10) |

> **Hinweis:** Cantaras Organigramm ist bewusst vereinfacht (nur 3 Bereiche statt der klassischen 6 Organisationsbereiche Architektur/Qualität, Entwicklung, Betrieb, Support, Account/Service Management, Stab). Andere plausible Zuordnungen sind möglich – wichtig ist die Begründung, nicht eine „richtige" Lösung.

</details>

---

### 🌟 Zusatzaufgabe 7.2 – Eskalation bei Prozessverletzung (optional)

Ein Entwickler aus der Anwendungsentwicklung & -betrieb spielt wiederholt Notfall-Änderungen direkt ein, ohne den Change Manager zu informieren (vgl. Ausgangslage). Der Change Manager (IT Process Manager) hat ihn bereits zweimal erfolglos direkt angesprochen. Wie sollte er weiter vorgehen?

<details>
<summary>💡 Hinweis / Kurzlösung 7.2</summary>

Der Change Manager eskaliert das Problem an seinen **IT Process Owner** (Bereichsleiter IT-Governance & Prozesse). Dieser klärt den Fall über die **Führungshierarchie** – z.B. direkt mit dem Bereichsleiter Anwendungsentwicklung & -betrieb, notfalls über den CIO. Es handelt sich um ein **Durchsetzungsproblem**, keine fachliche Frage – der Change Manager selbst hat gegenüber dem Entwickler keine disziplinarische Weisungsbefugnis.

</details>

---

## 🧩 Modul 8 – Management-Commitment & Veränderungsmanagement

### Hintergrundinformation

Viele ITSM-Einführungen scheitern, weil sie in der **obersten Führungsebene nicht genügend verankert** sind. Ein echtes Management-Commitment besteht, wenn:

- IT Service Management in der IT-Vision und IT-Strategie aufgeführt ist
- die obere IT-Führungsebene sich aktiv um das ITSM-„Marketing" kümmert – nicht nur intern, auch beim Leistungsbezieher
- Führung und Steuerung der IT auf den Service- und Prozesskennzahlen basiert (statt auf Bauchgefühl)
- die nötigen Ressourcen (Personal, Budget, Zeit) für Umsetzung und laufenden Betrieb bereitgestellt werden
- das mittlere Management die **Ownership** der einzelnen Prozesse übernimmt und Kennzahlen nach oben rapportiert

Zusätzlich braucht jede grössere Einführung ein **Veränderungsmanagement**, weil sie für viele Mitarbeitende Unsicherheit bedeutet. Eine oft zitierte Studie zeigt, dass die Produktivität während einer Veränderung von ca. 60% auf bis zu 15% einbrechen kann, bevor sie sich stabilisiert. Ein bekanntes Zitat dazu: *„Wenn Sie eine Transformationsbemühung starten, bekämpfen etwa 70 Prozent der Leute die Änderung oder sind ihr gegenüber gleichgültig eingestellt."*

---

### Szenario: Der zögerliche CIO

Der CIO der Cantara Bank AG hat den Massnahmenplan aus der Ist-Analyse (Teil 1) gesehen und ist grundsätzlich einverstanden. Ein Bereichsleiter kommentiert im Führungsmeeting jedoch: *„ITSM einzuführen finden wir eine gute Idee – dann startet doch mal, das läuft sicher nebenbei mit, dafür brauchen wir kein eigenes Projekt und keine zusätzlichen Leute."* Der CIO selbst äussert zudem: *„Das ist doch ein internes IT-Thema, da müssen wir das Business nicht einbeziehen."*

---

### Aufgabe 8.1 – Management-Commitment bewerten

1. Bewertet anhand der fünf Commitment-Kriterien, ob bei Cantara aktuell ein echtes Management-Commitment vorliegt.
2. Was würdet ihr dem CIO konkret empfehlen, bevor die Massnahmen aus Teil 1 gestartet werden?

<details>
<summary>💡 Teillösung Aufgabe 8.1</summary>

| Kriterium | Ist bei Cantara? |
|---|---|
| ITSM in IT-Vision/Strategie verankert | ✗ – wird bisher nicht erwähnt |
| Obere Führung betreibt aktiv ITSM-„Marketing" | ✗ – Aussage „läuft nebenbei mit" zeigt das Gegenteil |
| Führung/Steuerung basiert auf Kennzahlen | ✗ – siehe Teil 1: kein Prozess hat definierte KPIs |
| Ressourcen (Personal, Budget, Zeit) bereitgestellt | ✗ – „dafür brauchen wir kein eigenes Projekt" widerspricht dem |
| Mittleres Management übernimmt Ownership | ◑ – erst ansatzweise, siehe Modul 7 |

**Ergebnis:** Aktuell fehlt das Commitment nahezu vollständig – die Aussagen des Bereichsleiters sind klassische Negativbeispiele einer fehlenden Verankerung. Empfehlung an den CIO: ITSM explizit in die IT-Strategie aufnehmen, ein Einführungsprojekt mit eigenem Budget/Ressourcen aufsetzen (statt „nebenbei"), und das Business aktiv einbeziehen – insbesondere weil die Massnahmen aus Teil 1 (z.B. SLAs, Servicekatalog) den Leistungsbezieher direkt betreffen.

</details>

---

### Aufgabe 8.2 – Widerstände erkennen und adressieren

Nennt für zwei Mitarbeitergruppen der Cantara Bank AG (z.B. Service Desk Agenten, Entwickler in der Anwendungsentwicklung) je einen typischen **Widerstand oder eine Angst** gegenüber der ITSM-Einführung, und wie das Veränderungsmanagement darauf reagieren sollte.

<details>
<summary>💡 Teillösung Aufgabe 8.2</summary>

| Gruppe | Typischer Widerstand | Reaktion des Veränderungsmanagements |
|---|---|---|
| Service Desk Agenten | Sorge vor mehr Kontrolle/Dokumentationsaufwand durch neue Eskalations- und Priorisierungsregeln (→ Aufgabe 2.2/2.3) | Frühzeitig einbeziehen, zeigen, dass klare Regeln auch **entlasten** (keine Einzelfallentscheidungen mehr), gezielte Schulung |
| Entwickler (Anwendungsentwicklung) | Wahrnehmung, dass der neu eingeführte (ITIL-)Change-Management-**Prozess** (→ Modul 3) ihre gewohnte Schnelligkeit bei Notfall-Änderungen bremst | Kommunizieren, dass der Emergency-Change-Pfad (→ Aufgabe 3.1/3.2) weiterhin schnelles Handeln erlaubt, nur mit nachträglicher Dokumentation statt völliger Kontrolllosigkeit |

**Nutzen:** Gutes Veränderungsmanagement schafft Verständnis und Akzeptanz, macht aus Betroffenen Beteiligte, verhindert einen grösseren Leistungseinbruch während der Einführung und sichert einen nachhaltigen Veränderungsprozess.

> **Begriffsklärung:** „Change Management" (ITIL-**Prozess**, Modul 3: CAB, RFC, Change-Klassen) und „Veränderungsmanagement" (organisatorische **Begleitung** der ITSM-Einführung durch Kommunikation, Schulung, Stakeholder-Einbezug) sind zwei unterschiedliche Disziplinen, die im Deutschen sprachlich leicht verwechselt werden – im obigen Beispiel ist der *Widerstand* gegen den Change-Management-Prozess gerichtet, die *Reaktion* darauf kommt vom Veränderungsmanagement.

</details>

---

## 🧩 Modul 9 – Messen & kontinuierlich Verbessern

### Hintergrundinformation

Das Messen der erbrachten Dienstleistung erfolgt auf **zwei Ebenen**:

- **Service-Ebene:** Was hier gemessen wird, ergibt sich aus den SLAs (Business IT Service) bzw. OLAs (IT Service) – z.B. Verfügbarkeit, Reaktionszeit.
- **Prozess-Ebene:** Je IT-Prozess werden eigene KPIs definiert (z.B. mit Rot/Gelb/Grün-Bewertung) – sie messen, wie gut der Prozess selbst funktioniert, unabhängig vom einzelnen Service.

Darauf baut der **Continual Improvement-Prozess (COI)** auf – ein 7-Schritt-Verbesserungskreislauf (angelehnt an Plan-Do-Check-Act):

1. Improvement-Strategie erstellen und warten
2. Definieren, was gemessen wird (Service- und Prozessebene)
3. Messdaten sammeln
4. Messdaten aufbereiten
5. Messdaten analysieren
6. Informationen präsentieren (operative / taktische / strategische Ebene)
7. Verbesserungen und Optimierungen vornehmen
8. (laufend) Überwachen, Steuern und Rapportieren des COI-Prozesses selbst

---

### Aufgabe 9.1 – Service- vs. Prozesskennzahlen unterscheiden

Ordnet folgende Kennzahlen der **Service-Ebene** oder der **Prozess-Ebene** zu und begründet:

| Kennzahl | Ebene | Begründung |
|---|---|---|
| Monatliche Verfügbarkeit von CoreBanking 360 für Filialen | | |
| Anteil P1-Incidents mit eingehaltener Reaktionszeit (15 min) | | |
| Anzahl Changes mit vollständiger Dokumentation | | |
| Wiederherstellungszeit bei einem konkreten Ausfall | | |
| Anzahl KEDB-Einträge pro Quartal | | |

> **KEDB** (*Known Error Database*): Datenbank, in der Problem Management jeden **Known Error** dokumentiert – ein Problem mit identifizierter Grundursache und bekanntem Workaround/Lösung. Der Service Desk konsultiert die KEDB bei neuen Incidents, um wiederkehrende Störungen schneller zu beheben.

<details>
<summary>💡 Teillösung Aufgabe 9.1</summary>

| Kennzahl | Ebene | Begründung |
|---|---|---|
| Verfügbarkeit CoreBanking 360 (Filialen) | **Service-Ebene** | Direkt aus dem SLA von Aufgabe 4.1 abgeleitet, betrifft den Business IT Service als Ganzes |
| Reaktionszeit-Einhaltung bei P1 | **Prozess-Ebene** | Misst, wie gut der Incident-Management-**Prozess** funktioniert, unabhängig davon, welcher Service betroffen ist |
| Vollständigkeit der Change-Dokumentation | **Prozess-Ebene** | Reine Prozessqualität des Change Managements |
| Wiederherstellungszeit bei einem Ausfall | **Service-Ebene** | Teil des SLA-Ziels für den betroffenen BITS |
| KEDB-Einträge pro Quartal | **Prozess-Ebene** | Misst die Aktivität/Reife des Problem-Management-Prozesses |

</details>

---

### Aufgabe 9.2 – Den 7-Schritt-Verbesserungsprozess anwenden

Wendet den 7-Schritt-Verbesserungsprozess auf den **„Montagsausfall"** (siehe Teil 1, Modul 2) an: Füllt für jeden Schritt einen konkreten Cantara-Bezug aus.

<details>
<summary>💡 Teillösung Aufgabe 9.2</summary>

| Schritt | Anwendung auf den Montagsausfall |
|---|---|
| 1. Improvement-Strategie | Ziel festlegen: „Wiederkehrende CoreBanking-Ausfälle bis Quartalsende eliminieren" |
| 2. Definieren, was gemessen wird | Service-Ebene: Verfügbarkeit Montag 08:00–09:00; Prozess-Ebene: Anzahl Incidents ohne vorgelagerte Problem-Analyse |
| 3. Messdaten sammeln | Ticketdaten der letzten Wochen aus dem Service-Desk-Tool zusammentragen |
| 4. Messdaten aufbereiten | Ausfallzeiten und Ursachenhinweise (Batch-Job, DB-Verbindungen) tabellarisch aufbereiten |
| 5. Messdaten analysieren | Grundursache ermitteln (→ Problem Management, Aufgabe 2.1): blockierender Batch-Job |
| 6. Informationen präsentieren | Ergebnis auf operativer Ebene (Team), aber auch taktisch (IT-Leiter) präsentieren, da wiederkehrender Business-Impact |
| 7. Verbesserungen vornehmen | Known-Error-Eintrag + Change zur Entkopplung von Batch-Job und Online-Zugriffen initiieren (→ Change Management) |
| 8. COI überwachen | Prüfen, ob sich die Ausfallhäufigkeit nach der Massnahme tatsächlich reduziert |

</details>

---

## 🧩 Modul 10 – Service Catalog Management

### Hintergrundinformation

Der **Service Catalog Management (SCM)-Prozess** stellt sicher, dass ein aktueller, vollständiger **Service-Katalog** existiert – basierend auf den angebotenen BITS- und ITS-Varianten. Wichtige Prinzipien:

- Es gibt **einen zentralen** Service-Katalog fürs ganze Unternehmen.
- Der Katalog unterscheidet i.d.R. zwei Hauptansichten: eine **Leistungsbezieher-Ansicht** (Business IT Services, gruppiert nach Managed-Arbeitsplatz/Managed-Anwendungen) und eine **Leistungserbringer-Ansicht** (IT Services, IT-intern).
- Der Katalog repräsentiert stets das **aktuelle** Angebot und dokumentiert Änderungen über eine Historie (Audit-Trail).
- Jeder Service/jede Variante wird mind. **einmal jährlich validiert**.
- Der Katalog kann auch **SLAs/OLAs** sowie – falls vorhanden – **Preise** und **Bestellmöglichkeiten** (über Service Request Management) enthalten.

---

### Aufgabe 10.1 – Leistungsbezieher-Ansicht entwerfen

Entwerft für die Cantara Bank AG die **Leistungsbezieher-Ansicht** des Service-Katalogs: Gruppiert die fünf bekannten BITS (siehe Ausgangslage oben) nach „Managed-Arbeitsplatz" und „Managed-Anwendungen" und ergänzt je Service die bekannten Varianten.

<details>
<summary>💡 Teillösung Aufgabe 10.1</summary>

```
Leistungsbezieher-Ansicht – Service-Katalog Cantara Bank AG

Managed-Arbeitsplatz
  ├─ Arbeitsplatz-Service (Desktop/Laptop)
  │    Varianten: Standard, Hohe Sicherheit, High End
  ├─ Mail & Collaboration BITS
  │    Varianten: Standard (Filialen), Enhanced (Management)
  └─ Netzwerkdruck BITS
       Varianten: Lokal, Zentral/Follow-Me-Print

Managed-Anwendungen
  ├─ CoreBanking 360 BITS
  │    Varianten: Filiale Standard, Filiale Erweitert, Back Office
  │    SLA-Eckwerte: siehe Ausgangslage (99,5%/99,0%/99,8% Verfügbarkeit)
  └─ Trading-Terminal BITS
       Varianten: Standard Trader, Senior Trader
```

**Hinweis zur Bewertung:** Die Gruppierung nach Managed-Arbeitsplatz/-Anwendungen erleichtert den Leistungsbeziehern die Navigation im Katalog (Faustregel aus Teil 1: „Bekommt das jeder mit seinem Seat?" vs. „Braucht das nur eine bestimmte Rolle?"). Wer zusätzlich SLA-Kurzinfos direkt im Katalog aufführt, hat verstanden, dass der Katalog auch Service-Level-Informationen transportieren soll.

</details>

---

### 🌟 Zusatzaufgabe 10.2 – Leistungserbringer-Ansicht (optional)

Skizziert ergänzend die **Leistungserbringer-Ansicht** (IT-interne Sicht) für „CoreBanking 360 BITS", basierend auf der ITS-Dekomposition aus Teil 1, Aufgabe 1.2. Wozu kann diese Ansicht genutzt werden?

<details>
<summary>💡 Hinweis / Kurzlösung 10.2</summary>

```
Leistungserbringer-Ansicht – IT Services für CoreBanking 360 BITS
  ├─ Anwendungsorientiert: CoreBanking Application Maintenance & Support
  ├─ Erweitert: Database IT Service (Oracle DB), Middleware/App-Server IT Service
  ├─ Basis: Platform IT Service, Storage IT Service, Network IT Service
  └─ Unterstützend: Security IT Service, Event & Monitoring IT Service
```

**Nutzen:** Diese Ansicht reflektiert das gesamte IT-interne Dienstleistungsangebot. Lösungs-Designer oder Architekten können darauf basierend – wie mit einem Baukastensystem – die passenden IT-Service-Varianten auswählen, um die Anforderungen eines **neuen** Business IT Service zusammenzustellen, ohne jedes Mal bei null zu beginnen.

</details>

---

## 🧩 Modul 11 – Service Request Management

### Hintergrundinformation

Der **Service Request Management (SRM)-Prozess** wickelt **standardisierte, wiederkehrende Anfragen** der Leistungsbezieher ab – zur Abgrenzung: Incident Management behandelt eine ungeplante **Störung**, Requirement Management ein **nicht standardisiertes** Bedürfnis (z.B. eine neue Applikationsfunktion). Alle drei sind eigenständige Eingangskanäle vom Business zur IT.

Zwei Anliegentypen werden unterschieden:
- **Auftragsanliegen:** hat eine definierte Reaktions- und **Erbringungszeit**, z.B. Passwort-Reset, Zugriffsrechte-Mutation, Mailbox-Erweiterung, Arbeitsplatz-Installation.
- **Informationsanliegen:** Statusanfragen oder „How do I"-Fragen.

Prozessschritte: Service-Request-Katalog erstellen & warten → Request eröffnen → genehmigen → ausführen/weiterleiten → schliessen → überwachen/rapportieren.

Wichtiges Prinzip: Auftragsanliegen gelten als **Standard Change (Kategorie 5)** – sie werden **einmalig** über den Change-Management-Prozess freigegeben (→ Modul 3) und laufen danach als im Voraus genehmigt, ohne dass jeder einzelne Request nochmals das CAB durchläuft.

---

### Aufgabe 11.1 – Service Request für den Trader-Passwort-Reset gestalten

Erinnerung Ausgangslage: *„Trader im Handelsraum erhalten nach einem Passwort-Reset durchschnittlich 6 Stunden keinen Zugriff auf ihr Trading-Terminal."* In Teil 1, Aufgabe 3.1 wurde der Passwort-Reset bereits als **Standard Change** eingestuft.

1. Ordnet den Passwort-Reset einem der beiden SRM-Anliegentypen zu und begründet.
2. Definiert eine angemessene **Erbringungszeit** für den Passwort-Reset im Handelsraum und begründet unter Berücksichtigung, dass das Trading-Terminal BITS zur höchsten SLA-Klasse gehört (24×7, business-vital).
3. Beschreibt, wer den Request typischerweise genehmigen muss, und warum bei Passwort-Resets ein vereinfachter oder automatisierter Genehmigungsschritt sinnvoll ist.

<details>
<summary>💡 Teillösung Aufgabe 11.1</summary>

1. **Auftragsanliegen** – klar definierbare Reaktions-/Erbringungszeit und ein Standardablauf, im Gegensatz zu einer offenen Statusanfrage.
2. Erbringungszeit z.B. **15 Minuten**, statt der aktuellen 6 Stunden – gerechtfertigt durch die hohe SLA-Klasse des Trading-Terminal BITS und den unmittelbaren Umsatzausfall während der Handelszeit bei fehlendem Zugriff.
3. Genehmigung: in der Praxis oft automatisiert bzw. direkt durch den Service Desk (Identifikation z.B. via Rückruf oder Vorgesetzten-Bestätigung), da es sich um einen bereits im Voraus genehmigten Standard Change (Kategorie 5) handelt – ein Warten auf individuelle Managementfreigabe würde die geforderte kurze Erbringungszeit unmöglich machen.

**Bezug:** Der aktuelle 6-Stunden-Missstand ist ein Symptom dafür, dass bei Cantara kein SRM-Prozess mit definierten Erbringungszeiten existiert – Anfragen laufen unstrukturiert per E-Mail (siehe Ausgangslage).

</details>

---

### 🌟 Zusatzaufgabe 11.2 – Eingangskanäle unterscheiden (optional)

Ordnet folgende Anliegen dem richtigen Eingangskanal zu: **Incident Management**, **Service Request Management** oder **Requirement Management**.

| Anliegen | Kanal |
|---|---|
| CoreBanking 360 reagiert für alle Filialen nicht mehr | |
| Ein Filialmitarbeiter benötigt 2 GB mehr Mailbox-Speicher | |
| Das Business fordert eine neue Funktion „Multi-Currency-Konten" für CoreBanking | |
| Ein Trader hat sein Passwort vergessen | |
| Ein Mitarbeiter fragt nach dem Status seines letzten Tickets | |

<details>
<summary>💡 Hinweis / Kurzlösung 11.2</summary>

- CoreBanking-Totalausfall → **Incident Management** (ungeplante Störung)
- Mailbox-Erweiterung → **Service Request Management** (standardisiertes Auftragsanliegen)
- Multi-Currency-Konten-Funktion → **Requirement Management** (nicht standardisiertes, neues Bedürfnis mit Kosten-Nutzen-Abschätzung und Projekt-/Release-Planung)
- Passwort vergessen → **Service Request Management** (Standard-Auftragsanliegen, siehe Aufgabe 11.1)
- Statusanfrage → **Service Request Management** (Informationsanliegen)

</details>

---

## 🧩 Modul 12 – Supplier Management

### Hintergrundinformation

Der **Supplier Management (SUM)-Prozess** überwacht und steuert die **IT-Lieferanten** eines Unternehmens. Prozessschritte: neue Lieferanten evaluieren & einführen → Lieferantenverträge verwalten (in einer Lieferanten- und Vertragsdatenbank, **SCDB**) → Leistung der Lieferanten überwachen → Verträge erneuern/beenden → überwachen & rapportieren.

Wichtig: SUM grenzt sich vom **allgemeinen Einkaufsprozess** des Unternehmens ab – SUM deckt nur ab, was der generelle Einkauf nicht bereits regelt (z.B. die laufende Leistungsüberwachung anhand von OLAs).

Zentraler Zusammenhang: Bezieht die IT eine Leistung von einem externen Lieferanten, wird dessen Leistung über ein **OLA (Operational Level Agreement)** vereinbart – analog zum SLA gegenüber dem Business, aber intern zwischen IT und Lieferant. Hält der Lieferant sein OLA nicht ein, kann das direkt zu einer **SLA-Verletzung** gegenüber dem Leistungsbezieher führen.

---

### Aufgabe 12.1 – OLA für den externen Service Desk definieren

Aus der Ausgangslage: Cantaras **Service Desk (30 MA) ist extern vergeben**. Der Service Desk ist als L1 für die Einhaltung der Reaktionszeit P1 (**15 Minuten**, siehe SLA-Eckwerte oben bzw. Teil 1, Aufgabe 2.2/2.3) mitverantwortlich.

1. Erklärt den Unterschied zwischen dem **SLA** (Cantara ↔ Business) und dem **OLA**, das mit dem externen Service-Desk-Anbieter vereinbart werden müsste.
2. Welche konkrete OLA-Kennzahl müsste mit dem Lieferanten vereinbart werden, damit die 15-Minuten-Reaktionszeit realistisch eingehalten werden kann?
3. Nennt zwei SUM-Prozessschritte, die Cantara gegenüber diesem Lieferanten aktiv betreiben müsste, die laut Ausgangslage aktuell offensichtlich fehlen.

<details>
<summary>💡 Teillösung Aufgabe 12.1</summary>

1. Das **SLA** regelt die Leistung, die **Cantara IT dem Business** verspricht (z.B. Reaktionszeit P1 = 15 Min. für die Filialen). Das **OLA** regelt die interne Zulieferleistung, die der **externe Service-Desk-Anbieter der Cantara IT** liefern muss, damit die IT dieses SLA überhaupt einhalten kann – das OLA liegt inhaltlich „unter" dem SLA.
2. Z.B. „Anrufannahmezeit L1 ≤ X Sekunden" plus „Ticket-Erstreaktion/Weiterleitung an L2 innerhalb von 10 Minuten" – so bleibt genug Zeitpuffer innerhalb der 15-Minuten-SLA-Reaktionszeit.
3. **Leistung des Lieferanten überwachen** (aktuell offenbar nicht systematisch, da laut Ausgangslage die Bearbeitungszeit generell „unvorhersehbar" ist) und **Verwalten der Lieferantenverträge/SCDB** (nicht ersichtlich, dass ein vereinbartes OLA überhaupt dokumentiert und nachverfolgt wird).

**Wichtig:** Ohne dieses OLA weiss Cantara nicht, ob eine SLA-Verletzung an einem eigenen Prozessproblem liegt oder am externen Lieferanten – eine zentrale Blindstelle, die SUM schliesst.

</details>

---

### 🌟 Zusatzaufgabe 12.2 – Lieferanten in der CMDB (optional)

Verknüpft Supplier Management mit SACM (→ Teil 1, Aufgabe 5.1): Der „blinde Serverausfall" traf 15 Business-Anwendungen, weil die IT nicht wusste, welche Anwendungen auf dem betroffenen Server liefen. Angenommen, der betroffene Server wird von einem externen Hardware-Lieferanten gewartet. Welche Information müsste zusätzlich in der CMDB hinterlegt sein, damit Supplier Management im Ernstfall sofort greifen kann?

<details>
<summary>💡 Hinweis / Kurzlösung 12.2</summary>

Jedes **CI** (hier: der Server) müsste in der CMDB einen Verweis auf den zuständigen **Lieferanten/Vertrag** (z.B. aus der SCDB) sowie das zugehörige **OLA** (Reaktionszeit des Hardware-Supports) enthalten. So kann im Störungsfall sofort der richtige Lieferantenkontakt inkl. vereinbarter Reaktionszeit ermittelt werden, statt diesen erst manuell zu suchen – genau die Art von Zusammenhang, die laut Aufgabe 5.1 bei Cantara aktuell fehlt.

</details>

---

## 🧩 Modul 13 – Information Security Management

### Hintergrundinformation

Der **Information Security Management (ISM)-Prozess** richtet die Informationssicherheit (inkl. IT-Sicherheit) auf die Unternehmensbedürfnisse aus und überwacht sie. Prozessschritte: Information Security Policy (ISP) erstellen & warten → Security-Bedrohungen/-Schwächen/-Risiken analysieren → Schutzmassnahmen planen & einführen → Schutzmassnahmen betreiben → Security Incidents behandeln → überwachen/auditieren/rapportieren.

Die **ISP** gliedert sich meist in drei Ebenen: **Security Statement** (Grundsätze, vergleichbar mit einer Verfassung), **Security Standards** (vergleichbar mit Gesetzen) und **Security Procedures** (konkrete Umsetzungsanweisungen).

Wichtige Abgrenzung: Ein **Security Incident** wird zwar wie jeder andere Incident zunächst über **Incident Management** wiederhergestellt (→ Modul 2) – zusätzlich erfolgt aber eine **vertiefte Analyse durch die Security-Spezialisten**, und nötigenfalls werden ISP oder Schutzmassnahmen angepasst.

Rollen: **Security Manager** (Statement-/Standard-Teil der ISP, Audits, Ausbildung), **Security Analyst** (Procedure-Teil je Verantwortungsbereich, Risikoanalyse), **Security-Spezialist** (operativer Betrieb der Schutzmassnahmen).

---

### Szenario: Der weitergegebene Zugang

Ein Trader ruft beim Service Desk an: Er habe letzte Woche sein Passwort telefonisch einem Kollegen mitgeteilt, der kurzfristig für ihn einspringen musste. Heute stellt er fest, dass unter seiner Benutzer-ID auch Transaktionen ausgeführt wurden, die er selbst nicht getätigt hat.

---

### Aufgabe 13.1 – Security Incident einordnen und behandeln

1. Ist dies ein normaler Incident oder ein **Security Incident**? Begründet anhand der Hintergrundinformation.
2. Welche zwei Prozesse sind an der Behandlung beteiligt, und was ist jeweils ihre Aufgabe dabei?
3. Nennt zwei Punkte, die in Cantaras **Security Procedures** zum Thema Passwörter (Teil der ISP) explizit geregelt sein sollten, damit ein Vorfall wie dieser künftig verhindert wird.

<details>
<summary>💡 Teillösung Aufgabe 13.1</summary>

1. **Security Incident** – die Weitergabe eines Passworts und dessen Nutzung durch eine nicht autorisierte Person ist eine klassische Verletzung der Information Security Policy (vergleichbar mit den Skript-Beispielen „gehackte Webseite" oder „gestohlener Laptop").
2. **Incident Management** stellt zunächst den ordentlichen Betrieb wieder her (z.B. Passwort sofort zurücksetzen, betroffene Transaktionen prüfen lassen). **Information Security Management** übernimmt die vertiefte Analyse (Wie kam es dazu? Sind weitere Konten betroffen?) und entscheidet über Anpassungen an der ISP oder den Schutzmassnahmen.
3. Z.B.: „Passwörter dürfen unter keinen Umständen mündlich oder schriftlich an Dritte weitergegeben werden – auch nicht an Vorgesetzte" sowie „Bei Abwesenheitsvertretung ist ein individueller Vertretungs-Zugang über den Service Desk zu beantragen" (Bezug zu Modul 11: das wäre selbst ein Service Request).

**Bezug:** Auch das Passwort-Reset-Verfahren bei Cantara (→ Aufgabe 11.1) hat eine Sicherheitsdimension – die Identifikation des Antragstellers muss zweifelsfrei sichergestellt sein, sonst wird der SRM-Prozess selbst zum Einfallstor für genau diese Art von Vorfall.

</details>

---

### 🌟 Zusatzaufgabe 13.2 – Security Statement entwerfen (optional)

Entwerft in Stichworten die wichtigsten Punkte eines **Security Statements** (oberste ISP-Ebene) für die Cantara Bank AG – berücksichtigt dabei den Bankenkontext (hochsensible Kunden- und Transaktionsdaten, regulatorisches Umfeld).

<details>
<summary>💡 Hinweis / Kurzlösung 13.2</summary>

Mögliche Punkte: Management-Statement zur Wichtigkeit der Informationssicherheit für das Vertrauen der Bankkunden; Zweck und Geltungsbereich (alle Mitarbeitenden, alle BITS); Definition, was geschützt wird (Kunden-, Transaktionsdaten, Handelsgeheimnisse); Verweis auf regulatorische Vorgaben (z.B. FINMA-Anforderungen im Schweizer Bankenumfeld); jährliche Revalidierung der Policy; Konsequenzen bei Verstoss (bis zur fristlosen Kündigung, siehe Szenario oben).

</details>

---

## 📝 Abschluss & Lernkontrolle

### Kernbegriffe – Kurzdefinitionen

Erkläre folgende Begriffe ohne Hilfsmittel in 1–2 Sätzen:

1. **IT Process Owner**
2. **IT Process Manager**
3. **Management-Commitment**
4. **Service-Kennzahl vs. Prozess-Kennzahl**
5. **Continual Improvement**
6. **Service-Katalog**
7. **Service Request vs. Requirement**
8. **OLA (Operational Level Agreement)**
9. **Security Incident**

<details>
<summary>💡 Musterdefinitionen</summary>

1. **IT Process Owner:** Meist ein Mitglied der Bereichsleitung, das einen oder mehrere Prozesse strategisch verantwortet – u.a. Ressourcenbedarf vertritt, Prozessänderungen abnimmt und Prozess-KPIs in der Führung präsentiert.

2. **IT Process Manager:** Verantwortet Definition, Umsetzung, Schulung und Kontrolle eines einzelnen Prozesses im operativen Alltag.

3. **Management-Commitment:** Die nachweisbare Verbindlichkeit der obersten Führung gegenüber der ITSM-Einführung – sichtbar u.a. durch Verankerung in der IT-Strategie, bereitgestellte Ressourcen und kennzahlenbasierte Steuerung.

4. **Service-Kennzahl vs. Prozess-Kennzahl:** Service-Kennzahlen messen die Erbringung eines Business IT Service/IT Service gemäss SLA/OLA; Prozess-Kennzahlen (KPIs) messen die Qualität eines einzelnen ITSM-Prozesses, unabhängig vom betroffenen Service.

5. **Continual Improvement:** Ein fortlaufender, 7-schrittiger Verbesserungs- und Optimierungsprozess für die Informatikdienstleistungen, der auf gesammelten und analysierten Mess­daten aus Service- und Prozessebene aufbaut.

6. **Service-Katalog:** Ein zentrales, aktuelles Verzeichnis aller angebotenen Business IT Services (und optional IT Services) inkl. Varianten, das Leistungsbeziehern die Übersicht und ggf. die Bestellung ermöglicht.

7. **Service Request vs. Requirement:** Ein Service Request ist ein standardisiertes, wiederkehrendes Auftrags- oder Informationsanliegen mit definierter Erbringungszeit; ein Requirement ist ein nicht standardisiertes, neues Bedürfnis, das erst analysiert und einer Umsetzungsart (Projekt, Release, Change) zugeteilt werden muss.

8. **OLA (Operational Level Agreement):** Eine interne Vereinbarung zwischen der IT und einem Lieferanten (oder einer anderen internen IT-Einheit), die eine für ein SLA nötige Zulieferleistung regelt – ohne eingehaltenes OLA kann das darüberliegende SLA gegenüber dem Business nicht garantiert werden.

9. **Security Incident:** Ein Incident, der eine Verletzung der Information Security Policy darstellt (z.B. Passwort-Missbrauch, gestohlenes Gerät) – wird über Incident Management wiederhergestellt, zusätzlich aber vom Information Security Management vertieft analysiert.

</details>

---

> **Workshop-Ende Teil 2**
