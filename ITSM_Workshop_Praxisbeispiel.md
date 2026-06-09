# 🏦 ITSM Workshop: Praxisfall „Cantara Bank AG"

> **Zielgruppe:** Teilnehmende mit Grundkenntnissen in IT Service Management  
> **Dauer:** ca. 3–4 Stunden  
> **Format:** Gemischte Einzel- und Gruppenaufgaben mit ausklappbaren Teillösungen

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

---

## 🧩 Modul 1 – IT-Dienstleistungsstruktur verstehen

### Hintergrundinformation

Im IT-Servicemanagement wird zwischen **Business IT Services (BITS)** und **IT Services (ITS)** unterschieden:

- **BITS** sind die Leistungen, die der Leistungsbezieher (Business) direkt konsumiert und im SLA vereinbart.
- **ITS** sind die darunter liegenden, technischen IT-Services (Plattform, Netzwerk, Storage, Anwendung), die für den Leistungsbezieher meist nicht direkt sichtbar sind.

#### Hauptdienstleistungselemente

Die Informatikdienstleistung lässt sich in **fünf Hauptdienstleistungselemente** unterteilen: *Managed-Arbeitsplatz, Managed-Anwendungen, Anwendungsentwicklung, Informatikberatung* und *Informatikschulung*. Für die IT-Service-Management-Betrachtung – und damit für diesen Workshop – stehen die **beiden ersten** im Vordergrund. Das Unterscheidungskriterium ist *für wen* der Service gedacht ist:

- **Managed-Arbeitsplatz:** die **horizontale** Standard-Arbeitsumgebung, die *jeder* Mitarbeitende mit seinem Arbeitsplatz erhält – z. B. Desktop/Laptop, Büroautomation (Mail & Collaboration), Drucken.
- **Managed-Anwendungen:** die **vertikalen**, *fachspezifischen* Anwendungen, die nur bestimmte Rollen oder Abteilungen benötigen – z. B. ein Kernbanken- oder Trading-System.

Die übrigen drei Elemente (Anwendungsentwicklung, Informatikberatung, Informatikschulung) sind hier nicht im Fokus, runden das Bild der IT-Leistungen aber ab.

> **Faustregel:** „Bekommt das jeder mit seinem Seat?" → Managed-Arbeitsplatz. „Braucht das nur eine bestimmte Rolle?" → Managed-Anwendungen.

#### Varianten

Ein BITS wird oft in mehreren **Varianten** angeboten – also derselbe Service in unterschiedlichen Qualitäts- oder Funktionsstufen. Varianten unterscheiden sich durch:

- **funktionale** Merkmale (z. B. Berechtigungen, Anzahl Applikationen) oder
- **nicht-funktionale** Merkmale (z. B. Service-Zeit, Verfügbarkeit, Reaktionszeit).

So kann z. B. ein Handelsraum eine 24×7-Variante mit höherer SLA-Klasse erhalten als eine Filiale.

> **Tipp zum Vorgehen:** Um die BITS zu finden, frage dich bei jedem Hinweis in der Ausgangslage: *„Was benutzt hier ein Business-Nutzer tatsächlich?"* Die meisten Services stehen wörtlich im Falltext oder ergeben sich aus der Organisationsstruktur.

---

### Aufgabe 1.1 – BITS identifizieren

Identifiziere anhand der Ausgangslage mind. **5 Business IT Services**, die die Cantara Bank AG betreibt. Ordne sie dem jeweiligen **Hauptdienstleistungselement** (Managed-Arbeitsplatz oder Managed-Anwendungen) zu und schlage sinnvolle **Varianten** vor.

| Business IT Service | Hauptdienstleistungselement | Mögliche Varianten |
|---|---|---|
| | | |
| | | |
| | | |
| | | |
| | | |

<details>
<summary>💡 Teillösung Aufgabe 1.1</summary>

| Business IT Service | Hauptdienstleistungselement | Mögliche Varianten |
|---|---|---|
| **Arbeitsplatz-Service (Desktop/Laptop)** | Managed-Arbeitsplatz | Standard, Hohe Sicherheit, High End |
| **Mail & Collaboration BITS** | Managed-Arbeitsplatz | Standard (Filialen), Enhanced (Management) |
| **Trading-Terminal BITS** | Managed-Anwendungen | Standard Trader, Senior Trader |
| **CoreBanking 360 BITS** | Managed-Anwendungen | Filiale Standard, Filiale Erweitert, Back Office |
| **Netzwerkdruck BITS** | Managed-Arbeitsplatz | Lokal, Zentral/Follow-Me-Print |

> **Hinweis:** Varianten können sich durch **funktionale** Merkmale (z.B. Berechtigungen, Anzahl Applikationen) oder **nicht-funktionale** Merkmale (z.B. Service-Zeit, Verfügbarkeit, Reaktionszeit) unterscheiden. Für den Handelsraum wäre z.B. eine 24/7-Verfügbarkeit mit höherer SLA-Klasse vorstellbar als für eine Filiale.

</details>

---

### Aufgabe 1.2 – IT Services zuordnen

Der CoreBanking 360 BITS bricht zusammen, wenn der darunterliegende Datenbankserver nicht erreichbar ist. Erstelle eine vereinfachte **Service-Abhängigkeitskarte** für den „CoreBanking 360 BITS" und ordne den verwendeten IT Services die korrekte **ITS-Kategorie** zu.

> **Orientierung – ITS-Kategorien:** IT Services lassen sich in mehrere Kategorien einteilen:
> - **Basis-IT-Services:** technische Grundlage – Datacenter-, Network-, Storage- und Platform IT Services. Sie bilden die Grundvoraussetzung für alle darüberliegenden Services.
> - **Erweiterte IT Services:** bauen auf den Basis-Services auf, z. B. Mail-, Database- und Print IT Services.
> - **Anwendungsorientierte IT Services:** Wartung & Support von Geschäftsanwendungen (Application Maintenance & Support) sowie Anwendungsentwicklung (Application Development).
> - **End-User-orientierte IT Services:** alles rund um den Arbeitsplatz des Anwenders – Workplace-bezogene IT Services sowie Service Desk & Onsite.
> - **Unterstützende IT Services:** dienstübergreifende Services wie Event & Monitoring sowie Security IT Services.
> - **Cloud IT Services:** aus der Cloud bezogene bzw. ausgelagerte (outgesourcte) IT Services – z. B. SaaS oder PaaS von Anbietern wie Microsoft Azure.
>
> Die ersten Kategorien bilden den vertikalen „Stack" unter einem BITS (Basis → Erweitert → Anwendung); unterstützende Services wirken quer dazu.

```
CoreBanking 360 BITS
  └── [ITS-Kategorie ?] ...
  └── [ITS-Kategorie ?] ...
  └── [ITS-Kategorie ?] ...
  └── [ITS-Kategorie ?] ...
```

<details>
<summary>💡 Teillösung Aufgabe 1.2</summary>

```
CoreBanking 360 BITS
  └── Anwendungsorientierte IT Services:  CoreBanking Application Maintenance & Support
  └── Erweiterte IT Services:             Database IT Service (Oracle DB)
  └── Erweiterte IT Services:             Middleware/App-Server IT Service
  └── Basis-IT-Services:                  Platform IT Service (physische/virtuelle Server)
  └── Basis-IT-Services:                  Storage IT Service (SAN/NAS)
  └── Basis-IT-Services:                  Network IT Service (LAN/WAN zu Filialen)
  └── Unterstützende IT Services:         Security IT Service (Authentisierung/Login)
  └── Unterstützende IT Services:         Event & Monitoring IT Service
  └── End-User-orientierte IT Services:   Service Desk & Onsite (Anwender-Support)
```

> **Hinweis zur Bewertung:** Die ersten sechs Einträge bilden den vertikalen Stack (Anwendung → Erweitert → Basis). Die letzten drei (Security, Monitoring, Service Desk) liegen quer dazu und unterstützen mehrere Schichten – Gruppen, die diese erkennen, denken bereits in Abhängigkeiten statt nur in Schichten.

> **Wichtige Erkenntnis für den Praxisfall:** Der Serverausfall hat 15 Anwendungen getroffen, weil die IT keine dokumentierte Service-Abhängigkeitskarte führt. Dies ist ein klares Zeichen für fehlendes **Service Asset and Configuration Management (SACM)**.

</details>

---

## 🧩 Modul 2 – Incident Management & Problem Management

### Hintergrundinformation

Im IT-Servicemanagement werden Incident Management und Problem Management klar voneinander abgegrenzt:

- **Incident Management** zielt darauf ab, eine Störung **so schnell wie möglich** zu beheben und die Auswirkung auf den BITS zu minimieren.
- **Problem Management** bezweckt, das **wiederholte Auftreten** von Incidents durch proaktive Massnahmen und die Ermittlung von Grundursachen zu verhindern.
- Beide Prozesse sind eng verzahnt: Ein Problem entsteht oft aus wiederkehrenden Incidents.

---

### Szenario: Der Montagsausfall

**Sachverhalt:**  
Jeden Montag zwischen 08:15 und 08:45 Uhr fällt „CoreBanking 360" für 20–40 Minuten aus. Der Service Desk registriert jedes Mal 80–120 Anrufe von Filialmitarbeitenden. Das Incident wird jedes Mal durch einen Neustart des Applikationsservers behoben. Eine Ursachenanalyse wird nicht durchgeführt, da der Betrieb um 09:00 Uhr wieder läuft.

---

### Aufgabe 2.1 – Incident vs. Problem abgrenzen

Beantworte folgende Fragen:

1. Was ist in diesem Szenario der **Incident**?
2. Was ist das **Problem**?
3. Warum ist es falsch, das Incident durch einen Neustart zu schliessen, ohne ein Problem-Ticket zu eröffnen?
4. Wie würde ein **Known Error** in diesem Kontext definiert?

<details>
<summary>💡 Teillösung Aufgabe 2.1</summary>

1. **Incident:** Der wöchentliche Ausfall des CoreBanking 360 BITS (Nichtverfügbarkeit der Anwendung für Filialmitarbeitende) – jeder einzelne Ausfall ist ein eigenständiger Incident.

2. **Problem:** Die unbekannte, wiederholte Ursache, die jeden Montag zur gleichen Zeit zum Ausfall führt. Das Problem ist die zugrundeliegende, noch nicht identifizierte Grundursache.

3. **Warum falsch:** Durch das Schliessen des Incidents ohne Problemanalyse wird nur der **Symptom** behoben, nicht die Ursache. Das Incident wird sich mit Sicherheit wiederholen, was zu kontinuierlichen Service-Unterbrechungen, Produktivitätsverlust und Vertrauensverlust im Business führt. Incident Management ist für die schnelle Wiederherstellung zuständig – die Ursachenermittlung ist explizit Aufgabe des **Problem Managements**.

4. **Known Error:** Sobald die Grundursache identifiziert ist (z.B. „Montags läuft ein Batch-Job, der alle DB-Verbindungen blockiert") und ein Workaround oder eine Lösung bekannt ist, wird das Problem zum **Known Error**. Der Known Error wird in der Known Error Database (KEDB) dokumentiert und ermöglicht dem Service Desk, bei erneutem Auftreten schneller zu reagieren.

</details>

---

### Aufgabe 2.2 – Eskalationspfad definieren

Basierend auf dem Szenario und der Organisationsstruktur der Cantara Bank AG: Entwerft einen **Incident-Eskalationspfad** für einen kritischen CoreBanking-Ausfall (Priority 1).

Berücksichtigt dabei:
- Stufen der funktionalen Eskalation (Level 1 → Level 2 → Level 3)
- Wann wird eine **hierarchische Eskalation** ausgelöst?
- Welche **Prozessrollen** sind beteiligt?
- Welche **Zeitlimiten** (Reaction Time, Resolution Time) schlagt ihr vor?
- Benennt die Stationen der **hierarchischen Eskalationskette** anhand des Organigramms (siehe Ausgangslage). Wer steht an deren Spitze, wofür steht das Kürzel **CIO**, und welche Entscheidungen dürfen *nur* auf dieser Ebene getroffen werden?

> **Wichtig – funktionale vs. hierarchische Eskalation:** Diese beiden Begriffe meinen unterschiedliche Dinge und dürfen nicht verwechselt werden.
>
> | | **Funktionale Eskalation** | **Hierarchische Eskalation** |
> |---|---|---|
> | Achse | Fach-Kompetenz / Spezialisierung | Führungs- und Entscheidungs**befugnis** |
> | Beispiel | Level 1 → Level 2 → Level 3 | Incident Manager → IT-Leiter → CIO |
> | Leitfrage | „Wer kann es technisch **lösen**?" | „Wer darf **entscheiden** / Ressourcen freigeben?" |
> | Richtung | *seitwärts* zu anderen Spezialisten | *nach oben* in die Führung |
>
> Die Stufung **L1 → L2 → L3 ist trotz des Namens „Level" keine Hierarchie**: L2 ist nicht der Vorgesetzte von L1, sondern hat lediglich mehr Fachwissen. Die Störung wandert in Richtung des *Wissens*, das sie lösen kann – nicht die Karriereleiter hinauf. Erst wenn nicht mehr *Wissen*, sondern *Befugnis* fehlt (kritischer Business-Impact, Regulatorik-Risiko, Ressourcenfreigabe), greift die hierarchische Eskalation. Beide Achsen können **gleichzeitig** laufen.

<details>
<summary>💡 Teillösung Aufgabe 2.2</summary>

**Incident-Eskalationspfad – Priority 1 (CoreBanking 360 komplett unavailable)**

| Stufe | Rolle/Funktion | Aufgabe | Zeitlimit (ab Meldung) |
|---|---|---|---|
| **L1** | Service Desk Agent | Aufnahme, Klassifizierung, Sofortmassnahmen prüfen, KEDB konsultieren | 0–15 min |
| **L2** | Incident Analyst (Anwendungsbetrieb CoreBanking) | Tiefenanalyse, Workaround einleiten, Neustart falls bekannt | 15–30 min |
| **L3** | CoreBanking-Spezialist / Hersteller | Sourcecode-Analyse, DB-Tuning, Hersteller-Support einschalten | 30–90 min |
| **Hierarch.** | Incident Manager → IT-Leiter → CIO | Eskalation wenn: L2 nach 30 min keine Lösung, Business-Impact kritisch, Medien-/Regulatorik-Risiko | Ab 45 min |

**Typische Prozessrollen im Incident Management:**
- **Incident-Erfasser** (Service Desk Agent): Ticket aufnehmen, Basisdaten erfassen
- **Incident Analyst:** Analyse und Behebung
- **Incident Queue Manager:** Stellt sicher, dass Incidents korrekt zugewiesen werden und SLA-Zeiten nicht überschritten werden
- **Incident Manager:** Koordiniert bei Maj. Incidents, kommuniziert ans Business

**Hierarchische Eskalationskette (laut Organigramm):**
- **Incident Manager** → koordiniert den Major Incident, ruft die nächste Stufe
- **IT-Leiter** (Leitung des betroffenen Bereichs, z.B. Anwendungsbetrieb) → setzt Bereichsressourcen frei
- **CIO** (*Chief Information Officer*), im Theorieskript auch **(oberste) IT-Leitung** genannt → oberste IT-Führung in der Geschäftsleitung; **Spitze der Kette**. *Hinweis: nicht zu verwechseln mit dem **IT-Leiter** eine Stufe darunter – dieser leitet nur den betroffenen Bereich, während die **IT-Leitung/CIO** die gesamte Informatik verantwortet.*

Nur auf CIO-Ebene zu entscheiden (Beispiele): Aktivierung des Geschäfts-Notfallbetriebs/Fallback, Kommunikation an Vorstand und **Aufsichtsbehörde**, Freigabe grosser Budgets oder Hersteller-Notfallverträge, Eskalation als Krise mit Unternehmensreichweite. Der CIO **löst die Störung nicht technisch** (das bleibt bei L3), sondern entscheidet auf der geschäftlichen Achse.

**Empfohlene SLA-Ziele für Priority 1:**
- Reaction Time: 15 Minuten
- Resolution Time: 2 Stunden
- Business Communication: alle 30 Minuten

> **Hinweis:** Die hierarchische Eskalation ist kein Versagen – sie ist ein bewusstes Steuerungsinstrument, um Ressourcen freizuschalten und Entscheidungsträger einzubinden.
>
> **Funktional und hierarchisch laufen parallel – sie ersetzen sich nicht.** Wenn ab 45 min hierarchisch eskaliert wird, bleibt das Ticket technisch bei L3; der Spezialist arbeitet ununterbrochen weiter. Die Führungsebene debuggt nicht, sondern handelt auf der geschäftlichen Achse (Fallback aktivieren, Business/Aufsicht informieren, Emergency Change autorisieren). L3 wird dadurch **nicht abgeschnitten**.
>
> Im Gegenteil: Die hierarchische Eskalation kann **schon vor Ende der L3-Bearbeitung unterstützend wirken** – etwa indem sie zusätzliche Ressourcen freischaltet, die L3 helfen (z.B. Premium-Support des Herstellers aktivieren, weitere Spezialisten abziehen, Überstunden genehmigen). Löst L3 das Problem rechtzeitig, war die frühe Einbindung eine reine Vorsichtsmassnahme – verloren ist dabei nichts.

</details>

---

### Aufgabe 2.3 – Prioritätsmatrix erstellen und Incidents einordnen

In den bisherigen Aufgaben wurde mehrfach von einem **P1-Incident** gesprochen, ohne dass definiert ist, *was* einen Incident zu P1 macht. Genau diese Lücke schliesst ihr jetzt.

Das Theorieskript empfiehlt zur Prioritätsbestimmung **Ansatz 1** (Abb. 3.20). Dieser kombiniert zwei Achsen, die sich direkt aus den BITS und der CMDB ableiten lassen:

> **Priorität = Kritikalität des BITS × Anzahl betroffener Leistungsbezieher (Benutzer)**
>
> - **Kritikalität des BITS:** aus dem SLA – *Business-vital → Business-kritisch → Business-wichtig → Business-neutral*
> - **Anzahl betroffener Benutzer:** Klassen *1–30 / 31–80 / 81–250 / >250*
>
> *Hinweis: Das Skript nennt auch einen Ansatz 2 (Dringlichkeit × Auswirkung), rät davon aber ab, weil die „Dringlichkeit" aus Anwendersicht fast immer hoch ist und damit schwer objektivierbar bleibt.*

Optional kann eine dritte Achse, der **Auswirkungsgrad** (Tab. 3.14), die Priorität abschwächen:

| Auswirkungsgrad | Bedeutung | Wirkung |
|---|---|---|
| betriebsverhindernd | Total-Ausfall, kein Arbeiten möglich | Priorität bleibt |
| betriebsbehindernd | eingeschränkt nutzbar, Mehraufwand | +1 Prio-Stufe (max. P4) |
| geringe Einschränkung | nur Teilfunktionen betroffen | +2 Prio-Stufen (max. P4) |

**Teil A – Prioritätsmatrix ausfüllen:** Tragt in die Matrix die Prioritätsstufen **P1–P4** ein (P1 = höchste).

| Kritikalität BITS ↓ \ Benutzer → | 1–30 | 31–80 | 81–250 | >250 |
|---|---|---|---|---|
| **Business-vital** | | | | |
| **Business-kritisch** | | | | |
| **Business-wichtig** | | | | |
| **Business-neutral** | | | | |

**Teil B – Incidents der Cantara Bank AG einordnen:** Bestimmt Kritikalität des betroffenen BITS, Anzahl Benutzer und die resultierende Priorität.

| Incident | Kritikalität BITS | Anzahl Benutzer | Priorität |
|---|---|---|---|
| CoreBanking 360 fällt für alle Filialen komplett aus, der Handel steht still | | | |
| Ein einzelner Trader hat während der Handelszeit keinen Zugriff auf sein Terminal | | | |
| Das Mailsystem ist für die gesamte Bank stark verlangsamt, funktioniert aber noch | | | |
| Ein Drucker im Back-Office ist defekt, ein Ersatzdrucker steht daneben | | | |

<details>
<summary>💡 Teillösung Aufgabe 2.3</summary>

**Teil A – Prioritätsmatrix (beispielhafte Ausprägung):**

| Kritikalität BITS ↓ \ Benutzer → | 1–30 | 31–80 | 81–250 | >250 |
|---|---|---|---|---|
| **Business-vital** | **P1** | **P1** | **P1** | **P1** |
| **Business-kritisch** | **P2** | **P2** | **P1** | **P1** |
| **Business-wichtig** | **P3** | **P3** | **P2** | **P2** |
| **Business-neutral** | **P4** | **P4** | **P3** | **P3** |

> Das Skript betont ausdrücklich: *Welche Kombination welche Priorität ergibt, ist unternehmensspezifisch* und muss im Incident-Prozess festgelegt werden. Obige Belegung ist eine plausible Ausprägung für die Cantara Bank, kein fixer Standard.

**Teil B – Einordnung:**

| Incident | Kritikalität BITS | Anzahl Benutzer | Priorität |
|---|---|---|---|
| CoreBanking 360 für alle Filialen komplett aus, Handel steht | Business-vital | >250 | **P1** |
| Einzelner Trader ohne Terminal-Zugriff während Handelszeit | Business-vital (Trading) | 1–30 | **P1** |
| Mailsystem bankweit stark verlangsamt, aber funktionsfähig | Business-wichtig | >250 | **P2** → mit Auswirkungsgrad *betriebsbehindernd* (+1): **P3** |
| Defekter Drucker mit Ersatz daneben | Business-neutral | 1–30 | **P4** |

**Wichtige Erkenntnisse:**
- **Die Service-Kritikalität dominiert, nicht die Benutzerzahl.** Ein *einzelner* Trader auf dem business-vitalen Trading-BITS ergibt **P1** – obwohl nur eine Person betroffen ist. Die naive Logik „wenige Nutzer = niedrige Priorität" greift zu kurz.
- Umgekehrt ist ein business-neutraler Service (Drucker) selbst mit Workaround maximal P4.
- Der **Auswirkungsgrad** wirkt nur abschwächend: Das langsame, aber nutzbare Mailsystem (betriebsbehindernd) rutscht von P2 auf P3 – bei Total-Ausfall bliebe es P2.
- Die so ermittelte Priorität steuert direkt die **SLA-Ziele und den Eskalationspfad** aus Aufgabe 2.2: P1 = Reaction 15 min / Resolution 2 h + sofortige Eskalation, P4 = keine oder erst sehr späte Eskalation.

> **Hinweis:** Die Kritikalitäts-Einstufung der BITS stammt idealerweise aus den **SLAs**, die Benutzerzahl aus der **CMDB** – beides fehlt der Cantara Bank bislang, weshalb die Priorisierung heute willkürlich erfolgt.

</details>

---

## 🧩 Modul 3 – Change Management

### Hintergrundinformation

Der **Change Management-Prozess** stellt sicher, dass Veränderungen auf **kontrollierte und nachvollziehbare Art** von der Entwicklung bis in die Produktion gelangen. Er schützt stabile Services vor unkontrollierten Eingriffen.

**Change-Typen (typisch in ITSM-Frameworks):**
- **Standard Change:** Vordefinierter, risikoarmer Change mit bekanntem Ablauf (z.B. Passwort-Reset, Software-Installation)
- **Normal Change:** Muss den Change Advisory Board (CAB) durchlaufen; Planung, Risikoabschätzung, Genehmigung
- **Emergency Change:** Sofortmassnahme bei kritischem Incident; nachträgliche Dokumentation und CAB-Review

**Was ist der Change Advisory Board (CAB)?**
Der CAB ist ein **beratendes und genehmigendes Gremium**, das Normal Changes vor der Umsetzung bewertet und freigibt. Es vereint Fach-, Infrastruktur-, Business- und ggf. Security-Vertreter, um **Risiko, Auswirkung und Abhängigkeiten** einer Änderung gemeinsam zu beurteilen. Der CAB *führt Changes nicht selbst durch*, sondern entscheidet, ob, wann und unter welchen Auflagen sie umgesetzt werden dürfen. So wird verhindert, dass riskante Eingriffe ungeprüft in die Produktion gelangen. (Wie ein CAB konkret zusammengesetzt wird, erarbeitet ihr in Aufgabe 3.2.)

---

### Szenario: Die unkontrollierten Notfall-Änderungen

Die IT-Abteilung führt mehrmals pro Woche Änderungen am Produktionssystem durch – meistens um aktuelle Störungen zu beheben. Diese Änderungen werden direkt von den Entwicklern eingespielt, ohne Risikoabschätzung, Test oder Freigabe. Zweimal wurden dadurch neue Störungen verursacht.

---

### Aufgabe 3.1 – Change-Typen zuordnen

Ordne folgende Änderungsvorhaben der Cantara Bank AG dem richtigen **Change-Typ** zu und begründe deine Wahl:

| Änderungsvorhaben | Change-Typ | Begründung |
|---|---|---|
| Rollout des neuen CoreBanking-Release 4.2 auf alle Filialen | | |
| Passwort-Reset für einen gesperrten Trader | | |
| Notfall-Patch, weil ein kritischer Fehler im Produktionssystem einen Ausfall verursacht | | |
| Erweiterung der Firewall-Regeln für eine neue Bankfunktion | | |
| Hinzufügen eines neuen Druckers im Back-Office | | |

<details>
<summary>💡 Teillösung Aufgabe 3.1</summary>

| Änderungsvorhaben | Change-Typ | Begründung |
|---|---|---|
| Rollout CoreBanking 4.2 | **Normal Change** | Grosses Release, hoher Impact, Risiko, braucht CAB-Freigabe, ausgiebige Tests |
| Passwort-Reset Trader | **Standard Change** | Vordefinierter, risikoarmer Prozess, bekannte Schritte, keine CAB-Genehmigung nötig |
| Notfall-Patch bei aktivem Ausfall | **Emergency Change** | Kritische Situation erfordert Schnelligkeit; nachträgliches CAB-Review obligatorisch |
| Firewall-Erweiterung neue Bankfunktion | **Normal Change** | Sicherheitsrelevante Änderung, potenziell hoher Impact, Risikoabschätzung nötig |
| Neuer Drucker Back-Office | **Standard Change** | Standardisierter, risikoarmer Prozess mit bekanntem Ablauf |

> **Wichtig für den Praxisfall:** Die aktuellen „Notfall-Änderungen" der Cantara Bank sind de facto **undokumentierte Normal oder Emergency Changes**. Fehlt der Change-Prozess, werden neue Incidents durch unkontrollierte Eingriffe provoziert – ein klassisches Teufelskreis-Muster.

</details>

---

### Aufgabe 3.2 – Change Advisory Board (CAB) aufbauen

Der CIO der Cantara Bank AG beauftragt euch, einen **Change Advisory Board (CAB)** zu konzipieren.

Beantwortet folgende Fragen:
1. Welche Rollen/Funktionen sollten im CAB der Cantara Bank vertreten sein?
2. Wie oft sollte der CAB tagen?
3. Nach welchen Kriterien werden Changes priorisiert/genehmigt/abgelehnt?
4. Wie wird mit **Emergency Changes** umgegangen, wenn der CAB nicht tagen kann?

<details>
<summary>💡 Teillösung Aufgabe 3.2</summary>

**CAB-Zusammensetzung (Cantara Bank AG):**

| Rolle | Vertreten durch | Begründung |
|---|---|---|
| Change Manager (Vorsitz) | IT-Governance & Prozesse | Koordination und Entscheidungsführung |
| Vertreter CoreBanking | Anwendungsbetrieb | Fachliche Risikobeurteilung Kernanwendungen |
| Vertreter Infrastruktur | Datacenter & Netzwerk | Technische Abhängigkeiten & Impact |
| Vertreter Workplace | Workplace & Printing | Arbeitsplatz-Changes |
| Business-Vertreter | z.B. Filialbetrieb, Handel | Business-Impact-Beurteilung |
| Security Officer (bei Bedarf) | IT-Governance | Sicherheitsrelevante Änderungen |

**Taktung:** Wöchentliches reguläres CAB-Meeting; bei dringenden Normal Changes: Emergency CAB (ECAB) via Videokonferenz innert 2 Stunden einberufbar.

**Genehmigungskriterien:**
- Risikobeurteilung (Low / Medium / High / Critical)
- Rollback-Plan vorhanden?
- Testnachweis (DEV/Test-Umgebung)?
- Kommunikationsplan für Betroffene?
- Wartungsfenster eingeplant?

**Emergency Changes:**
- ECAB mit mind. Change Manager + 2 Fachvertretern genehmigt per Mail/Chat
- Vollständige Dokumentation und reguläres CAB-Review innert 48 Stunden
- Grundursache des auslösenden Incidents wird an Problem Management übergeben

</details>

---

### Aufgabe 3.3 – Change-Prozessrollen zuordnen

Beim Rollout des **CoreBanking-Release 4.2** (ein Normal Change) sind mehrere Prozessrollen beteiligt. Ordnet jede Tätigkeit der richtigen Change-Rolle zu (**Change Owner, Change Analyst, Change Approver, Change Manager**) und überlegt, **welche Stelle/welches Team der Cantara Bank AG** die Rolle übernehmen sollte.

| Tätigkeit | Change-Rolle | Bei Cantara: wer? |
|---|---|---|
| Nimmt den RfC an, prüft ihn auf Vollständigkeit und weist ihn zu | | |
| Beurteilt die technischen Auswirkungen auf die Trading-Systeme | | |
| Erstellt den detaillierten Einführungs- und Rollback-Plan | | |
| Erteilt die finale Freigabe im Gremium | | |
| Leitet das CAB-Meeting und führt nach Go-live das PIR durch | | |

**Zusatzfrage:** Was passiert mit dieser Rollenverteilung, wenn der Change als **Emergency Change** läuft?

<details>
<summary>💡 Teillösung Aufgabe 3.3</summary>

| Tätigkeit | Change-Rolle | Bei Cantara (Beispiel) |
|---|---|---|
| RfC annehmen, prüfen, zuweisen | **Change Manager** | IT-Governance & Prozesse (zentrale Stelle) |
| Technische Auswirkungen beurteilen | **Change Analyst** | Spezialist Trading-Systeme / Anwendungsbetrieb |
| Einführungs- und Rollback-Plan erstellen | **Change Owner** | Verantwortlicher aus Anwendungsentwicklung CoreBanking |
| Finale Freigabe im Gremium | **Change Approver (= CAB)** | CAB als höchste Genehmigungsstelle |
| CAB leiten + PIR durchführen | **Change Manager** | IT-Governance & Prozesse |

**Reihenfolge im Normalfall:** Change Manager (Annahme/Zuweisung) → Change Owner (Analyse & Plan, unterstützt vom Change Analyst) → Change Approver/CAB (Freigabe) → Umsetzung → Change Manager (PIR & Abschluss).

**Bei Emergency Change:** Wegen Zeitdruck/Abwesenheiten übernimmt oft **eine Person mehrere Rollen** (z. B. Change Owner = Change Analyst). Die Genehmigung erfolgt durch das **ECAB** statt durch das reguläre CAB; Dokumentation und CAB-Review werden **nachgelagert** durchgeführt.

</details>

---

## 🧩 Modul 4 – Service Level Management & SLA

### Hintergrundinformation

Das **Service Level Agreement (SLA)** hält die vereinbarten Serviceziele zwischen Leistungserbringer (IT) und Leistungsbezieher (Business) fest. Es definiert:
- **Service-Zeit** (wann ist der Service verfügbar?)
- **Verfügbarkeit** (z.B. 99,5% pro Monat)
- **Reaktionszeit / Wiederherstellungszeit** bei Störungen
- **Kapazitäts- und Performanceziele**

---

### Aufgabe 4.1 – SLA-Ziele definieren

Definiert ein **SLA-Entwurf** für den Business IT Service „CoreBanking 360 BITS" der Cantara Bank AG. Berücksichtigt dabei die unterschiedlichen Anforderungen der Leistungsbeziehergruppen:

- **Filialmitarbeitende** (Schalter, Beratung): Mo–Fr 07:30–19:00 Uhr
- **Back-Office** (Verarbeitung, Buchhaltung): Mo–Fr 07:00–20:00 Uhr
- **Night-Batch-Verarbeitung** (automatisiert): täglich 22:00–04:00 Uhr

Füllt folgende Tabelle aus:

| SLA-Kriterium | Filialen | Back-Office | Night-Batch |
|---|---|---|---|
| Service-Zeit | | | |
| Verfügbarkeit (Ziel, pro Monat) | | | |
| Max. Ausfallzeit pro Monat | | | |
| Reaktionszeit bei P1-Incident | | | |
| Wiederherstellungszeit P1 | | | |
| Geplante Wartungsfenster | | | |

<details>
<summary>💡 Teillösung Aufgabe 4.1</summary>

| SLA-Kriterium | Filialen | Back-Office | Night-Batch |
|---|---|---|---|
| **Service-Zeit** | Mo–Fr 07:30–19:00 | Mo–Fr 07:00–20:00 | Täglich 22:00–04:00 |
| **Verfügbarkeit/Monat** | 99,5% | 99,0% | 99,8% |
| **Max. Ausfall/Monat** | ca. 2,2 Std. | ca. 4,4 Std. | ca. 0,9 Std. |
| **Reaktionszeit P1** | 15 min | 15 min | 30 min (Bereitschaft) |
| **Wiederherstellungszeit P1** | 2 Stunden | 3 Stunden | 1 Stunde |
| **Wartungsfenster** | Sa 06:00–08:00 | Sa 06:00–08:00 | Täglich 04:00–06:00 |

> **Methodischer Hinweis:** Die Verfügbarkeit beim Night-Batch ist höher (99,8%), weil eine Unterbrechung der Nachtverarbeitung am Folgetag zu massiven Buchungsproblemen führt. Die kurze Wiederherstellungszeit von 1 Stunde ist daher ebenfalls kritisch.

> **Berechnungsbeispiel:** Bei einer Service-Zeit von Mo–Fr 07:30–19:00 = 11,5h/Tag × ~22 Arbeitstage = 253h/Monat. 99,5% Verfügbarkeit = max. 0,5% Ausfall = **ca. 75 Minuten (1,25 Std.)** tolerierter Ausfall pro Monat.

</details>

---

## 🧩 Modul 5 – Service Asset and Configuration Management (SACM)

### Hintergrundinformation

Der **SACM-Prozess** verwaltet alle Configuration Items (CIs) – vom Business IT Service bis zur physischen Infrastrukturkomponente – in der **Configuration Management Database (CMDB)**. Die CMDB erlaubt es, bei einem Incident sofort zu erkennen, welche Services und Leistungsbezieher betroffen sind.

---

### Szenario: Der blinde Serverausfall

Ein Storage-Server fällt aus. Die IT weiss nicht, welche 15 Anwendungen darauf laufen. Die Kommunikation ans Business erfolgt mit 2 Stunden Verzögerung, weil erst durch Anrufe der Filialen klar wird, welche Services ausgefallen sind.

---

### Aufgabe 5.1 – CMDB-Struktur konzipieren

Konzipiert eine vereinfachte **CMDB-Hierarchie** für die Cantara Bank AG. Definiert:

1. Welche **CI-Typen** sollen erfasst werden? (mind. 5 Ebenen)
2. Welche **Beziehungstypen** zwischen CIs sind relevant?
3. Wie hätte eine funktionierende CMDB beim Szenario „blinder Serverausfall" geholfen?

<details>
<summary>💡 Teillösung Aufgabe 5.1</summary>

**CI-Hierarchie (von oben nach unten):** Die Ebenen folgen dem Service-Modell und den **ITS-Kategorien aus Aufgabe 1.2**; die unterste Ebene bildet die technischen CIs nach den **CI-Haupttypen des Skripts** (Service, Hardware, Software, Gebäude) ab.

```
Ebene 1 – Business IT Service (BITS)
  └─ z.B. "CoreBanking 360 BITS", "Mail & Collaboration BITS"

Ebene 2 – Anwendungsorientierter IT Service
  └─ z.B. "CoreBanking AMS ITS" (Application Maintenance & Support)

Ebene 3 – Erweiterter IT Service
  └─ z.B. "Oracle Database ITS"

Ebene 4 – Basis-IT Service
  └─ z.B. "Platform/Server ITS", "Storage ITS", "Network ITS"

Ebene 5 – Technische CIs (Haupttypen: Hardware / Software / Gebäude)
  └─ z.B. Server "SRV-APP-01" (HW), Betriebssystem "RHEL 8.5" (SW),
     Storage-Array "SAN-01" (HW), Switch "NETSW-DC-03" (HW), DC-Gebäude
```

**Relevante Beziehungstypen:**
- `hängt ab von` (BITS → ITS → technisches CI)
- `läuft auf` (Anwendung → Server → Storage)
- `verbunden mit` (Server → Netzwerk-Switch)
- `gehört zu` (CI → Leistungsbezieher-Gruppe)

**Nutzen beim Serverausfall:**
Mit einer vollständig gepflegten CMDB wäre beim Ausfall des Storage-CI „SAN-01" (Ebene 5, Hardware) über die `hängt ab von`-Beziehungen sofort ersichtlich:
- Welche Basis-IT Services (Platform/Server) das Storage nutzen (Ebene 5 → 4)
- Welche erweiterten und anwendungsorientierten IT Services darauf aufbauen (Ebene 4 → 3 → 2)
- Welche BITS – und damit welche Leistungsbezieher-Gruppen – betroffen sind (Ebene 2 → 1)
- Welche Gruppen sofort proaktiv informiert werden müssen

**Ergebnis:** Statt 2 Stunden blinder Reaktion hätte die IT innerhalb von 5 Minuten eine vollständige Impact-Liste gehabt und proaktiv kommunizieren können.

</details>

---

## 🧩 Modul 6 – Gesamtreflexion & Massnahmenplan

### Aufgabe 6.1 – ITSM-Einführungsstand analysieren

Bewertet, wie weit jeder Prozess der Cantara Bank AG im **Einführungsmodell des Skripts** (Abb. 2.1, Abschnitt 2.1) bereits gekommen ist. Das Modell unterscheidet vier **Einführungsbereiche** und – innerhalb der Definitionsphase – drei **Levels**:

> **Einführungsbereiche:** Dokumentation · Prozess · Tool/Hilfsmittel · Organisation
>
> **Definitions-Levels:** Level 1 = Prozessbeschreibung (Ziele, Schritte, Rollen, KPIs) · Level 2 = Umsetzungsgrundlagen (Tools, Rollen-Zuteilung, Rot/Gelb/Grün-KPIs) · Level 3 = Arbeitsinstruktionen (WINs) + Tool-Workflow

Bewertet je Prozess die vier Bereiche (✓ vorhanden / ◑ teilweise / ✗ fehlt) und bestimmt die **erreichte Stufe** (noch nicht begonnen · vor Level 1 · Level 1 · Level 2 · Level 3 · produktiv etabliert). Begründet mit konkreten Aussagen aus der Ausgangslage.

| ITSM-Prozess | Doku | Prozess | Tool | Organisation | Erreichte Stufe |
|---|---|---|---|---|---|
| Incident Management | | | | | |
| Problem Management | | | | | |
| Change Management | | | | | |
| Service Level Management | | | | | |
| Service Asset & Config. Mgmt. | | | | | |
| Service Request Management | | | | | |
| Service Catalog Management | | | | | |

<details>
<summary>💡 Teillösung Aufgabe 6.1</summary>

| ITSM-Prozess | Doku | Prozess | Tool | Org. | Erreichte Stufe | Begründung |
|---|---|---|---|---|---|---|
| **Incident Management** | ✗ | ◑ | ◑ | ✓ | **vor Level 1** | Service Desk (Organisation) und Ticket-Aufnahme existieren, aber keine dokumentierte Prozessbeschreibung, keine Rollen/KPIs/Eskalation definiert |
| **Problem Management** | ✗ | ✗ | ✗ | ✗ | **nicht begonnen** | Wiederkehrende Incidents werden nicht analysiert, keine KEDB |
| **Change Management** | ✗ | ◑ | ✗ | ◑ | **vor Level 1** | Changes werden durchgeführt (Entwickler), aber unkontrolliert – ohne Dokumentation, Tool-Workflow oder CAB |
| **Service Level Management** | ✗ | ✗ | ✗ | ✗ | **nicht begonnen** | Keine definierten SLAs, kein Monitoring/Reporting |
| **SACM** | ✗ | ✗ | ✗ | ✗ | **nicht begonnen** | Keine CMDB; beim Serverausfall war unbekannt, welche Services betroffen waren |
| **Service Request Management** | ✗ | ◑ | ✗ | ◑ | **vor Level 1** | Anfragen werden bearbeitet, aber per E-Mail, unstrukturiert, ohne Prozess/Tool |
| **Service Catalog Management** | ✗ | ✗ | ✗ | ✗ | **nicht begonnen** | Kein Servicekatalog vorhanden (explizit in der Ausgangslage) |

**Kernbotschaft:** Nach dem Einführungsmodell des Skripts hat Cantara bei **keinem** Prozess auch nur **Level 1** (eine vollständige Prozessbeschreibung) erreicht. Drei Aktivitäten werden zwar *gelebt* (Incident, Change, Service Request), aber ohne Dokumentation, Prozessdefinition und Tool-Unterstützung – im Sinne des Modells sind sie damit **noch nicht eingeführt**, sondern bestenfalls „vor Level 1". Das unterstreicht den dringenden Handlungsbedarf.

</details>

---

### Aufgabe 6.2 – Roadmap für die ITSM-Einführung

Erstellt eine priorisierte **ITSM-Roadmap** für die nächsten 12 Monate der Cantara Bank AG. Berücksichtigt dabei:
- Welche Prozesse haben den **höchsten Business-Impact**, wenn sie fehlen?
- In welcher Reihenfolge würdet ihr die Einführung angehen (Quick Wins vs. Langfristprojekte)?
- Welche **Erfolgsmessgrössen (KPIs)** definiert ihr für die ersten 3 Monate?

<details>
<summary>💡 Teillösung Aufgabe 6.2</summary>

**Empfohlene Einführungsreihenfolge (nach dem Phasenmodell des Skripts, Abschnitt 2.3):**

> Das Skript gruppiert die Prozesse nach Wichtigkeit in drei Phasen (Phase 1 = „sehr wichtig", Phase 2 = „wichtig", Phase 3 = „empfehlenswert"). *Innerhalb* einer Phase gibt es laut Skript **keine bewertete Reihenfolge** – die zeitliche Sequenzierung legt das Unternehmen anhand seiner Schmerzpunkte fest.

**Phase 1 – Fundament („sehr wichtig"):** Alle sechs Kernprozesse gehören laut Skript in Phase 1:
1. **Service Level Management** – mind. rudimentär, damit die IT weiss, was der Leistungsbezieher fordert.
2. **Change Management** – sofortiger Schutz vor unkontrollierten Änderungen (CAB).
3. **Service Asset & Configuration Management** – CMDB als Grundlage für Impact-Analysen.
4. **Incident Management** – Prioritätsmatrix (→ Aufgabe 2.3), Eskalationspfade (→ Aufgabe 2.2).
5. **Problem Management** – KEDB, Ursachenanalyse wiederkehrender Incidents.
6. **Service Request Management** – strukturierte, nachverfolgbare Anfragen.

*Pragmatische Sequenzierung für Cantara innerhalb Phase 1:* Change + Incident zuerst (akute Schmerzpunkte), parallel SLM rudimentär; dann SACM/CMDB als Voraussetzung für die Impact-Analyse; anschliessend Problem Management und Service Request Management.

**Phase 2 – Ausbau („wichtig"):**
- **Service Catalog Management** – Leistungsbezieher wissen, was sie bestellen können.
- *(weitere Skript-Phase-2-Prozesse ausserhalb des Workshop-Scopes: u.a. IT Financial, Release, Information Security, Availability, Capacity, Operational Level, Event, Access, Risk Management)*

**Phase 3 – Optimierung („empfehlenswert"):**
- **Continual Improvement** – fortlaufende Optimierung über KPI-Reviews.
- *(weitere: Business Relationship, Service Portfolio, Supplier, Knowledge, IT Architecture Management …)*

> **Abweichungs-Hinweis:** Eine rein „Quick-Wins"-orientierte Roadmap würde den **Servicekatalog** gern vorziehen (schnell sichtbarer Nutzen) und **Service Request Management** nach hinten schieben. Das Skript ordnet beides anders ein (Catalog → Phase 2, Service Request → Phase 1). Diese Roadmap folgt bewusst der **Skript-Einteilung**.

**KPIs für die ersten 3 Monate (Fokus Phase-1-Start: Change + Incident + SLM):**

| KPI | Ziel |
|---|---|
| Anteil Changes mit vollständiger Dokumentation | > 90% |
| Ungeplante Produktions-Ausfälle durch unkontrollierte Changes | < 1/Monat |
| Incident P1 Wiederherstellungszeit (Ø) | < 2 Stunden |
| Incidents ohne Schliessungsnachweis nach 5 Tagen | < 5% |
| SLA-Entwürfe für die kritischsten BITS erstellt | mind. 3 |

</details>

---

## 📝 Abschluss & Lernkontrolle

### Kernbegriffe – Kurzdefinitionen

Erkläre folgende Begriffe ohne Hilfsmittel in 1–2 Sätzen:

1. **Business IT Service (BITS)**
2. **Service Level Agreement (SLA)**
3. **Known Error**
4. **Configuration Item (CI)**
5. **Emergency Change**
6. **Grundursache**

<details>
<summary>💡 Musterdefinitionen</summary>

1. **BITS:** Eine IT-Dienstleistung, die für den Leistungsbezieher (Business) direkt sichtbar und konsumierbar ist. Sie basiert auf einem definierten Preis, funktionalen Anforderungen und vereinbarten Qualitätsmerkmalen (Service Levels).

2. **SLA:** Ein formales Dokument zwischen IT-Leistungserbringer und Leistungsbezieher, das die vereinbarten Serviceziele (Verfügbarkeit, Reaktions- und Wiederherstellungszeiten, Service-Zeiten) verbindlich festlegt.

3. **Known Error:** Ein Problem, dessen Grundursache bereits identifiziert wurde und für das ein Workaround oder eine definitive Lösung bekannt ist. Wird in der Known Error Database (KEDB) dokumentiert.

4. **Configuration Item (CI):** Jedes verwaltete Element innerhalb der CMDB – von einem Business IT Service über einen Server bis hin zu einem Netzwerkkabel. CIs werden mit ihren Attributen und Beziehungen zueinander dokumentiert.

5. **Emergency Change:** Eine dringende Änderung am Produktionssystem, die ausserhalb des regulären Change-Prozesses durchgeführt wird, um einen kritischen Incident zu beheben. Erfordert nachträgliche Dokumentation und CAB-Review.

6. **Grundursache:** Die eigentliche, zugrundeliegende Ursache eines Problems oder Incidents – im Gegensatz zum Symptom. Die Ermittlung der Grundursache ist das Hauptziel des Problem Management-Prozesses.

</details>

---

> **Workshop-Ende**
