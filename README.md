# HelpDesk Pro

Internes Ticket-Management-System mit integriertem Server-Monitoring –
entwickelt als betriebliche Projektarbeit im Rahmen der IHK-Abschlussprüfung
zum Fachinformatiker für Anwendungsentwicklung.

---

## Projektbeschreibung

HelpDesk Pro ist eine webbasierte Anwendung für ein fiktives
IT-Dienstleistungsunternehmen (TechSolutions GmbH). Mitarbeiter können
Support-Anfragen (Tickets) erstellen und deren Bearbeitungsstatus verfolgen.
Techniker bearbeiten zugewiesene Tickets und verwalten Benutzer sowie den
überwachten Server.

Ergänzend überwacht ein Python-Modul kontinuierlich die Erreichbarkeit und
CPU-Auslastung eines Servers (Ping + SSH/paramiko) und erstellt bei
Nichterreichbarkeit automatisch ein Ticket – ohne manuelles Eingreifen.

---

## Funktionen

- Ticket-Erstellung, -Verfolgung und -Kommentierung
- Zwei Rollen: **Benutzer** (Tickets erstellen/einsehen) und **Techniker** (Tickets bearbeiten, zuweisen, Status ändern)
- Kategorisierung und Priorisierung von Tickets
- Automatisches Server-Monitoring (Ping-Erreichbarkeit + CPU-Auslastung per SSH)
- Automatische Ticket-Erstellung bei Server-Ausfall

---

## Technologie-Stack

| Bereich        | Technologie                              |
|----------------|------------------------------------------|
| Backend        | PHP 8.x (OOP, MVC-Architektur)           |
| Datenbank      | MariaDB (auf Hyper-V-VM, Linux)          |
| Frontend       | HTML5, CSS3, JavaScript                  |
| Monitoring     | Python 3.x, paramiko (SSH)               |
| IDE            | PhpStorm (PHP), PyCharm (Python)         |
| Testumgebung   | Microsoft Hyper-V (zwei Linux-VMs)       |
| Versionierung  | Git / GitHub                             |

---

## Projektstruktur

```
HelpDeskPro/
├── docs/                              → Projektplanung & Dokumentation
│   ├── Lastenheft.txt                 → Anforderungen des Auftraggebers
│   ├── Pflichtenheft.txt              → technische Umsetzung
│   ├── Meilensteine.txt               → Projektkontrollpunkte
│   ├── Netzplan.txt                   → Vorgangsabhängigkeiten, krit. Pfad
│   ├── Anforderungsanalyse.txt        → "Was brauche ich?" (Entwicklersicht)
│   ├── Arbeitspakete.txt              → Aufgliederung der Netzplan-Phasen
│   └── Netzplan_Vorgangsknoten.drawio → Netzplan-Diagramm (draw.io)
├── src/                               → PHP-Anwendung (Backend + Frontend)
├── monitoring/                        → Python-Monitoring-Skript
├── sql/                               → Datenbankschema (CREATE TABLE)
└── README.md
```

---

## Projektplanung

Die vollständige Planung (Lastenheft, Pflichtenheft, Netzplan, Meilensteine,
Arbeitspakete) befindet sich im Ordner [`docs/`](./docs).

**Zeitbudget:** 80 Stunden  
**Kritischer Pfad (Netzplan):** 68 Stunden (A → B → C → E → F → G)  
**Puffer Python-Monitoring (D):** 24 Stunden  

| Phase | Beschreibung      | Stunden |
|-------|-------------------|---------|
| A     | Analysephase      | 10 Std. |
| B     | Entwurfsphase     | 8 Std.  |
| C     | Backend (PHP)     | 22 Std. |
| D     | Python-Monitoring | 12 Std. |
| E     | Frontend          | 14 Std. |
| F     | Testphase         | 8 Std.  |
| G     | Dokumentation     | 6 Std.  |

---

## Aktueller Stand

- [x] Projektantrag erstellt und mit Ausbilder abgestimmt
- [x] Lastenheft, Pflichtenheft erstellt
- [x] Netzplan (inkl. FAZ/FEZ/SAZ/SEZ/Puffer) erstellt
- [x] Meilensteine und Arbeitspakete definiert
- [x] Anforderungsanalyse (Grob) erstellt
- [ ] Datenbankschema (SQL) umgesetzt
- [ ] Backend (PHP) – Authentifizierung, Ticket-CRUD, Rollen
- [ ] Python-Monitoring-Modul
- [ ] Frontend (Dashboard, Formulare)
- [ ] Testphase
- [ ] Finale IHK-Dokumentation

---

## Installation (lokal)

> **Getestet mit:** XAMPP (Apache + PHP 8.x) unter Windows und PhpStorm als IDE.  
> Alternativ kann jede Umgebung mit PHP 8.x, einem Webserver (Apache/Nginx)
> und MariaDB verwendet werden – z. B. eine native Linux-Installation oder Docker.

1. PHP 8.x + Apache bereitstellen (z. B. über XAMPP)
2. Repository klonen:
   ```bash
   git clone https://github.com/SonerGarip/HelpDeskPro.git
   ```
3. Datenbankschema aus `sql/` in MariaDB importieren
4. Datenbankzugangsdaten in `src/config/db.php` eintragen
5. Projektordner in `htdocs/` ablegen und über `http://localhost/HelpDeskPro` aufrufen

---

## Sicherheitsmaßnahmen

- Passwort-Hashing über `password_hash()` (bcrypt)
- Schutz vor SQL-Injection durch Prepared Statements (PDO)
- Schutz vor XSS durch `htmlspecialchars()`
- Rollenbasierte Zugriffskontrolle (Benutzer / Techniker)

---

## Autor

**Soner Garip**  
Umschulung Fachinformatiker Anwendungsentwicklung  
BBQ GmbH Berlin
