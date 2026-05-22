# 🏦 ITSM Workshop: Praxisfall „Cantara Bank AG"

> **Zielgruppe:** Teilnehmende mit Grundkenntnissen in IT Service Management  
> **Dauer:** ca. 3–4 Stunden (inkl. Gruppenarbeit & Diskussion)  
> **Grundlage:** K4.0047 – IT-Servicemanagement Theorieskript  
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
CIO
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

Laut Theorieskript (Kap. 1.1 & 1.2.2) wird zwischen **Business IT Services (BITS)** und **IT Services (ITS)** unterschieden:

- **BITS** sind die Leistungen, die der Leistungsbezieher (Business) direkt konsumiert und im SLA vereinbart.
- **ITS** sind die darunter liegenden, technischen IT-Services (Plattform, Netzwerk, Storage, Anwendung), die für den Leistungsbezieher meist nicht direkt sichtbar sind.

---

### Aufgabe 1.1 – BITS identifizieren (Einzelarbeit, 10 min)

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

### Aufgabe 1.2 – IT Services zuordnen (Gruppenarbeit, 15 min)

Der CoreBanking 360 BITS bricht zusammen, wenn der darunterliegende Datenbankserver nicht erreichbar ist. Erstelle eine vereinfachte **Service-Abhängigkeitskarte** für den „CoreBanking 360 BITS" und ordne den verwendeten IT Services die korrekte **ITS-Hauptgruppe** (G1–G5 gemäss Theorieskript) zu.

```
CoreBanking 360 BITS
  └── [ITS-Gruppe ?] ...
  └── [ITS-Gruppe ?] ...
  └── [ITS-Gruppe ?] ...
  └── [ITS-Gruppe ?] ...
```

<details>
<summary>💡 Teillösung Aufgabe 1.2</summary>

```
CoreBanking 360 BITS
  └── G3 Anwendungsorientierter ITS:  CoreBanking Application Maintenance & Support
  └── G2 Erweiterter ITS:             Database IT Service (Oracle DB)
  └── G2 Erweiterter ITS:             Middleware IT Service (App-Server)
  └── G1 Basis-ITS:                   Platform IT Service (physische/virtuelle Server)
  └── G1 Basis-ITS:                   Storage IT Service (SAN/NAS)
  └── G1 Basis-ITS:                   Network IT Service (LAN/WAN zu Filialen)
```

> **Wichtige Erkenntnis für den Praxisfall:** Der Serverausfall hat 15 Anwendungen getroffen, weil die IT keine dokumentierte Service-Abhängigkeitskarte führt. Dies ist ein klares Zeichen für fehlendes **Service Asset and Configuration Management (SACM)**.

</details>

---

## 🧩 Modul 2 – Incident Management & Problem Management

### Hintergrundinformation

Laut Theorieskript (Kap. 1.2.3 & 3.3.6/3.3.7):

- **Incident Management** zielt darauf ab, eine Störung **so schnell wie möglich** zu beheben und die Auswirkung auf den BITS zu minimieren.
- **Problem Management** bezweckt, das **wiederholte Auftreten** von Incidents durch proaktive Massnahmen und die Ermittlung von Root Causes zu verhindern.
- Beide Prozesse sind eng verzahnt: Ein Problem entsteht oft aus wiederkehrenden Incidents.

---

### Szenario: Der Montagsausfall

**Sachverhalt:**  
Jeden Montag zwischen 08:15 und 08:45 Uhr fällt „CoreBanking 360" für 20–40 Minuten aus. Der Service Desk registriert jedes Mal 80–120 Anrufe von Filialmitarbeitenden. Das Incident wird jedes Mal durch einen Neustart des Applikationsservers behoben. Eine Ursachenanalyse wird nicht durchgeführt, da der Betrieb um 09:00 Uhr wieder läuft.

---

### Aufgabe 2.1 – Incident vs. Problem abgrenzen (Einzelarbeit, 10 min)

Beantworte folgende Fragen:

1. Was ist in diesem Szenario der **Incident**?
2. Was ist das **Problem**?
3. Warum ist es falsch, das Incident durch einen Neustart zu schliessen, ohne ein Problem-Ticket zu eröffnen?
4. Wie würde ein **Known Error** in diesem Kontext definiert?

<details>
<summary>💡 Teillösung Aufgabe 2.1</summary>

1. **Incident:** Der wöchentliche Ausfall des CoreBanking 360 BITS (Nichtverfügbarkeit der Anwendung für Filialmitarbeitende) – jeder einzelne Ausfall ist ein eigenständiger Incident.

2. **Problem:** Die unbekannte, wiederholte Ursache, die jeden Montag zur gleichen Zeit zum Ausfall führt. Das Problem ist die zugrundeliegende, noch nicht identifizierte Root Cause.

3. **Warum falsch:** Durch das Schliessen des Incidents ohne Problemanalyse wird nur der **Symptom** behoben, nicht die Ursache. Das Incident wird sich mit Sicherheit wiederholen, was zu kontinuierlichen Service-Unterbrechungen, Produktivitätsverlust und Vertrauensverlust im Business führt. Gemäss Theorieskript ist Incident Management für die schnelle Wiederherstellung zuständig – die Ursachenermittlung ist explizit Aufgabe des **Problem Managements**.

4. **Known Error:** Sobald die Root Cause identifiziert ist (z.B. „Montags läuft ein Batch-Job, der alle DB-Verbindungen blockiert") und ein Workaround oder eine Lösung bekannt ist, wird das Problem zum **Known Error**. Der Known Error wird in der Known Error Database (KEDB) dokumentiert und ermöglicht dem Service Desk, bei erneutem Auftreten schneller zu reagieren.

</details>

---

### Aufgabe 2.2 – Eskalationspfad definieren (Gruppenarbeit, 20 min)

Basierend auf dem Szenario und der Organisationsstruktur der Cantara Bank AG: Entwerft einen **Incident-Eskalationspfad** für einen kritischen CoreBanking-Ausfall (Priority 1).

Berücksichtigt dabei:
- Stufen der funktionalen Eskalation (Level 1 → Level 2 → Level 3)
- Wann wird eine **hierarchische Eskalation** ausgelöst?
- Welche **Prozessrollen** sind beteiligt?
- Welche **Zeitlimiten** (Reaction Time, Resolution Time) schlagt ihr vor?

<details>
<summary>💡 Teillösung Aufgabe 2.2</summary>

**Incident-Eskalationspfad – Priority 1 (CoreBanking 360 komplett unavailable)**

| Stufe | Rolle/Funktion | Aufgabe | Zeitlimit (ab Meldung) |
|---|---|---|---|
| **L1** | Service Desk Agent | Aufnahme, Klassifizierung, Sofortmassnahmen prüfen, KEDB konsultieren | 0–15 min |
| **L2** | Incident Analyst (Anwendungsbetrieb CoreBanking) | Tiefenanalyse, Workaround einleiten, Neustart falls bekannt | 15–30 min |
| **L3** | CoreBanking-Spezialist / Hersteller | Sourcecode-Analyse, DB-Tuning, Hersteller-Support einschalten | 30–90 min |
| **Hierarch.** | Incident Manager → IT-Leiter → CIO | Eskalation wenn: L2 nach 30 min keine Lösung, Business-Impact kritisch, Medien-/Regulatorik-Risiko | Ab 45 min |

**Prozessrollen laut Theorieskript:**
- **Incident-Erfasser** (Service Desk Agent): Ticket aufnehmen, Basisdaten erfassen
- **Incident Analyst:** Analyse und Behebung
- **Incident Queue Manager:** Sicherstellt, dass Incidents korrekt zugewiesen werden und SLA-Zeiten nicht überschritten werden
- **Incident Manager:** Koordiniert bei Maj. Incidents, kommuniziert ans Business

**Empfohlene SLA-Ziele für Priority 1:**
- Reaction Time: 15 Minuten
- Resolution Time: 2 Stunden
- Business Communication: alle 30 Minuten

> **Hinweis:** Die hierarchische Eskalation ist kein Versagen – sie ist ein bewusstes Steuerungsinstrument, um Ressourcen freizuschalten und Entscheidungsträger einzubinden.

</details>

---

## 🧩 Modul 3 – Change Management

### Hintergrundinformation

Laut Theorieskript (Kap. 1.2.3 & 3.3.4) stellt der **Change Management-Prozess** sicher, dass Veränderungen auf **kontrollierte und nachvollziehbare Art** von der Entwicklung bis in die Produktion gelangen. Er schützt stabile Services vor unkontrollierten Eingriffen.

**Change-Typen (typisch in ITSM-Frameworks):**
- **Standard Change:** Vordefinierter, risikoarmer Change mit bekanntem Ablauf (z.B. Passwort-Reset, Software-Installation)
- **Normal Change:** Muss den Change Advisory Board (CAB) durchlaufen; Planung, Risikoabschätzung, Genehmigung
- **Emergency Change:** Sofortmassnahme bei kritischem Incident; nachträgliche Dokumentation und CAB-Review

---

### Szenario: Die unkontrollierten Notfall-Änderungen

Die IT-Abteilung führt mehrmals pro Woche Änderungen am Produktionssystem durch – meistens um aktuelle Störungen zu beheben. Diese Änderungen werden direkt von den Entwicklern eingespielt, ohne Risikoabschätzung, Test oder Freigabe. Zweimal wurden dadurch neue Störungen verursacht.

---

### Aufgabe 3.1 – Change-Typen zuordnen (Einzelarbeit, 10 min)

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

### Aufgabe 3.2 – Change Advisory Board (CAB) aufbauen (Gruppenarbeit, 15 min)

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
- Root Cause des auslösenden Incidents wird an Problem Management übergeben

</details>

---

## 🧩 Modul 4 – Service Level Management & SLA

### Hintergrundinformation

Laut Theorieskript (Kap. 3.3.1) hält das **Service Level Agreement (SLA)** die vereinbarten Serviceziele zwischen Leistungserbringer (IT) und Leistungsbezieher (Business) fest. Es definiert:
- **Service-Zeit** (wann ist der Service verfügbar?)
- **Verfügbarkeit** (z.B. 99,5% pro Monat)
- **Reaktionszeit / Wiederherstellungszeit** bei Störungen
- **Kapazitäts- und Performanceziele**

---

### Aufgabe 4.1 – SLA-Ziele definieren (Gruppenarbeit, 20 min)

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

Laut Theorieskript (Kap. 3.3.5) verwaltet der **SACM-Prozess** alle Configuration Items (CIs) – vom Business IT Service bis zur physischen Infrastrukturkomponente – in der **Configuration Management Database (CMDB)**. Die CMDB erlaubt es, bei einem Incident sofort zu erkennen, welche Services und Leistungsbezieher betroffen sind.

---

### Szenario: Der blinde Serverausfall

Ein Storage-Server fällt aus. Die IT weiss nicht, welche 15 Anwendungen darauf laufen. Die Kommunikation ans Business erfolgt mit 2 Stunden Verzögerung, weil erst durch Anrufe der Filialen klar wird, welche Services ausgefallen sind.

---

### Aufgabe 5.1 – CMDB-Struktur konzipieren (Gruppenarbeit, 25 min)

Konzipiert eine vereinfachte **CMDB-Hierarchie** für die Cantara Bank AG. Definiert:

1. Welche **CI-Typen** sollen erfasst werden? (mind. 5 Ebenen)
2. Welche **Beziehungstypen** zwischen CIs sind relevant?
3. Wie hätte eine funktionierende CMDB beim Szenario „blinder Serverausfall" geholfen?

<details>
<summary>💡 Teillösung Aufgabe 5.1</summary>

**CI-Typen Hierarchie (von oben nach unten):**

```
Level 1: Business IT Service (BITS)
  └─ z.B. "CoreBanking 360 BITS", "Mail & Collaboration BITS"

Level 2: Anwendungs-IT Service
  └─ z.B. "CoreBanking Application ITS", "Oracle DB ITS"

Level 3: Plattform-IT Service
  └─ z.B. "Server-Cluster Applikation", "Virtual Machine CoreBanking"

Level 4: IT-Komponente (Hardware/Software)
  └─ z.B. physischer Server "SRV-APP-01", Betriebssystem "RHEL 8.5"

Level 5: Infrastruktur-Komponente
  └─ z.B. Storage-Array "SAN-01", Switch "NETSW-DC-03"
```

**Relevante Beziehungstypen:**
- `hängt ab von` (BITS → ITS → Komponente)
- `läuft auf` (Anwendung → Server → Storage)
- `verbunden mit` (Server → Netzwerk-Switch)
- `gehört zu` (Komponente → Leistungsbezieher-Gruppe)

**Nutzen beim Serverausfall:**
Mit einer vollständig gepflegten CMDB wäre beim Ausfall von „SAN-01" sofort ersichtlich:
- Welche Server von diesem Storage abhängen (Level 4→5 Beziehung)
- Welche Anwendungen auf diesen Servern laufen (Level 3→4)
- Welche BITS davon betroffen sind (Level 1→2→3)
- Welche Leistungsbezieher-Gruppen sofort kommuniziert werden müssen

**Ergebnis:** Statt 2 Stunden blinder Reaktion hätte die IT innerhalb von 5 Minuten eine vollständige Impact-Liste gehabt und proaktiv kommunizieren können.

</details>

---

## 🧩 Modul 6 – Gesamtreflexion & Massnahmenplan

### Aufgabe 6.1 – ITSM-Reifegradanalyse (Gruppenarbeit, 20 min)

Bewertet den aktuellen ITSM-Reifegrad der Cantara Bank AG für jeden der folgenden Prozesse auf einer Skala von **0 (nicht vorhanden) bis 5 (optimiert)**. Begründet eure Einschätzung mit konkreten Aussagen aus der Ausgangslage.

| ITSM-Prozess | Reifegrad (0–5) | Begründung |
|---|---|---|
| Incident Management | | |
| Problem Management | | |
| Change Management | | |
| Service Level Management | | |
| Service Asset & Config. Mgmt. | | |
| Service Request Management | | |
| Service Catalog Management | | |

<details>
<summary>💡 Teillösung Aufgabe 6.1</summary>

| ITSM-Prozess | Reifegrad | Begründung |
|---|---|---|
| **Incident Management** | **2** | Incidents werden behandelt (Service Desk existiert), aber kein strukturierter Eskalationspfad, keine SLA-Überwachung, keine Verbindung zu Problem Management |
| **Problem Management** | **0–1** | Praktisch nicht vorhanden. Wiederkehrende Incidents werden nicht analysiert. Keine KEDB. |
| **Change Management** | **1** | Notfall-Änderungen finden statt, aber unkontrolliert, ohne Risikoabschätzung, kein CAB. |
| **Service Level Management** | **1** | Keine definierten SLAs vorhanden. Kein systematisches SLA-Monitoring oder -Reporting. |
| **SACM** | **0–1** | Keine CMDB erkennbar. Beim Serverausfall war unbekannt, welche Services betroffen waren. |
| **Service Request Management** | **1** | Anfragen per E-Mail, unstrukturiert, keine definierten Bearbeitungszeiten. |
| **Service Catalog Management** | **0** | Kein Servicekatalog vorhanden (explizit erwähnt in der Ausgangslage). |

</details>

---

### Aufgabe 6.2 – Roadmap für die ITSM-Einführung (Gruppenarbeit, 20 min)

Erstellt eine priorisierte **ITSM-Roadmap** für die nächsten 12 Monate der Cantara Bank AG. Berücksichtigt dabei:
- Welche Prozesse haben den **höchsten Business-Impact**, wenn sie fehlen?
- In welcher Reihenfolge würdet ihr die Einführung angehen (Quick Wins vs. Langfristprojekte)?
- Welche **Erfolgsmessgrössen (KPIs)** definiert ihr für die ersten 3 Monate?

<details>
<summary>💡 Teillösung Aufgabe 6.2</summary>

**Empfohlene Prioritätenreihenfolge:**

**Phase 1 – Quick Wins (Monate 1–3):**
1. **Change Management (Basis):** Einfachen Change-Prozess mit CAB einführen. Sofortiger Schutz vor unkontrollierten Änderungen.
2. **Incident Management verbessern:** Klare Prioritätsmatrix, Eskalationspfade, SLA-Ziele definieren.
3. **Service Catalog (Basiskatalog):** Wichtigste BITS dokumentieren → Leistungsbezieher wissen, was sie bestellen können.

**Phase 2 – Fundament legen (Monate 4–8):**
4. **SLA / Service Level Management:** SLA-Entwürfe je BITS verhandeln und unterzeichnen.
5. **CMDB (Basiskonfiguration):** Kritische CIs und Abhängigkeiten erfassen (CoreBanking, Trading, Mail).
6. **Problem Management:** Problem-Prozess aufsetzen, KEDB aufbauen, wöchentliche Problem-Review.

**Phase 3 – Optimierung (Monate 9–12):**
7. **Service Request Management:** Standardisierte Formulare, automatisierte Workflows.
8. **Continual Improvement:** Monatliche SLA-Reports, Prozess-KPI-Reviews, Optimierungsrunden.

**KPIs für die ersten 3 Monate:**

| KPI | Ziel |
|---|---|
| Anteil Changes mit vollständiger Dokumentation | > 90% |
| Anzahl ungeplanter Produktions-Ausfälle durch unkontrollierte Changes | < 1/Monat |
| Incident P1 Wiederherstellungszeit (Ø) | < 2 Stunden |
| Anzahl Incidents ohne Schliessungsnachweis nach 5 Tagen | < 5% |
| Servicekatalog veröffentlicht (Ja/Nein) | Ja |

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
6. **Root Cause**

<details>
<summary>💡 Musterdefinitionen</summary>

1. **BITS:** Eine IT-Dienstleistung, die für den Leistungsbezieher (Business) direkt sichtbar und konsumierbar ist. Sie basiert auf einem definierten Preis, funktionalen Anforderungen und vereinbarten Qualitätsmerkmalen (Service Levels).

2. **SLA:** Ein formales Dokument zwischen IT-Leistungserbringer und Leistungsbezieher, das die vereinbarten Serviceziele (Verfügbarkeit, Reaktions- und Wiederherstellungszeiten, Service-Zeiten) verbindlich festlegt.

3. **Known Error:** Ein Problem, dessen Root Cause bereits identifiziert wurde und für das ein Workaround oder eine definitive Lösung bekannt ist. Wird in der Known Error Database (KEDB) dokumentiert.

4. **Configuration Item (CI):** Jedes verwaltete Element innerhalb der CMDB – von einem Business IT Service über einen Server bis hin zu einem Netzwerkkabel. CIs werden mit ihren Attributen und Beziehungen zueinander dokumentiert.

5. **Emergency Change:** Eine dringende Änderung am Produktionssystem, die ausserhalb des regulären Change-Prozesses durchgeführt wird, um einen kritischen Incident zu beheben. Erfordert nachträgliche Dokumentation und CAB-Review.

6. **Root Cause:** Die eigentliche, zugrundeliegende Ursache eines Problems oder Incidents – im Gegensatz zum Symptom. Die Ermittlung der Root Cause ist das Hauptziel des Problem Management-Prozesses.

</details>

---

> **Workshop-Ende** | Weiterführende Lektüre: K4.0047 Kap. 3.3 (Prozessdetails), insb. 3.3.4 (Change), 3.3.5 (SACM), 3.3.6 (Incident), 3.3.7 (Problem), 3.3.1 (SLM)
