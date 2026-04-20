# Die Protokolle vom Robo-Arm

## Nächstes Meeting

???+ info "Jetzt schon vormerken"

    **Donnerstags ab 18 Uhr im Protolab**

    ```text
    Meeting Nr. 16

    Kamera Aufzeichnung ausprobieren 
    👩‍🔧👩🏽‍🔧 🤖🦾 👨‍🔧👨‍🔧
    ```

Der Link zum [`Termin im Forum`](https://forum.garage-lab.de/t/roboterarm-workshop-donnerstag/22493) 

## 2026-04-11 Meeting Nr 15
### Starten der Umgebung für lerobot
Wir haben die Lerobot-Umgebung auf eines unserer Macbook Air gespielt. Hier die Anweisung für den Start der Umgebung. 
*Hinweis: die IDs für Ernie und Bert sind bereits als Vorlage eingespeichert.*

- Starte das beiliegende MacBook
- Wähle Benutzer „lerobot“ aus (Passwort über Werkstattleiter)
- Öffne das Terminal
- Du landest in der Conda Base
- mit `conda env list` alle conda Umgebungen anzeigen lassen
- Umgebung robot auswählen mit `conda activate robot`
- dann das Verzeichnis `/users/lerobot/repos/lerobot` auswählen
- Schließe die Roboter an das Macbook an.
- prüfe mit `ls -l /dev/tty.u*`ob sie angeschlossen sind
- Es wird eine Liste der angeschlossenen Roboter angezeigt. Es werden die ID-Nummern angezeigt, die auf den Platten, auf denen die Roboter installiert sind, angebracht sind.
- Starte die Kalbibrierung mit dem Follower „Ernie“:
  `lerobot-calibrate lerobot-calibrate \
    --robot.type=so101_follower \
    --robot.port=$ernie
    --robot.id=my_awesome_follower_arm # <- Give the robot a unique name`
- Drücke Enter
- dann drücke `c` und Enter um die Kalibrierung zu starten
- in der Console erscheinen die Anweisungen
- Bringe zunächst Ernie in die Mittelposition
- Bewege jeden Servo von Ernie nach den Anweisungen aus der Mittelposition in die Minimum- und die Extremposition für 
- Dann kalibiere den Leader „Bert“:
  `lerobot-calibrate \
    --teleop.type=so101_leader \
    --teleop.port=$bert
    --teleop.id=my_awesome_leader_arm # <- Give the robot a unique name`
- Drücke Enter
- dann drücke `c` und Enter um die Kalibrierung zu starten
- in der Console erscheinen die Anweisungen
- Bewege jeden Servo den Roboter-Leader „Bert“ nach den Anweisungen aus der Mittelposition in die Minimum- und die Extremposition 

- Wenn alles kalibiert ist, starte die Teleoperation, um den Follower mit Hilfe des Leaders zu bewegen
  `lerobot-teleoperate \
    --robot.type=so101_follower \
    --robot.port=$ernie \
    --robot.id=my_awesome_follower_arm \ # gib hier die ID deiner Kalibierungsdatei ein
    --teleop.type=so101_leader \
    --teleop.port=/$bert \
    --teleop.id=my_awesome_leader_arm \ # gib hier die ID deiner Kalibierungsdatei ein`

Experimentieren mit angeschlossenen Kameras.
Wir haben eine Logitech Kamera nach [Anweisung](https://huggingface.co/docs/lerobot/cameras#setup-cameras) angeschlossen. Wir haben damit begonnen, im [Teleoperating Modus die Kameraaufzeichnung](https://huggingface.co/docs/lerobot/il_robots?teleoperate_so101=Command) zu beginnen. Es öffnet sich eine Software, die Aufzeichnungen über die Kamera aufzeichnet: Ernie kann über Bert im Teleoperations-Modus bewegt werden. Die Bewegungen von Ernie werden über die Kamera aufgezeichnet und er kann damit trainiert werden. Wir haben aber noch nicht systematisch damit begonnen, Trainingsdaten zu erstellen.

### Nächste Schritte
- Lernen, im Teleoperationsmodus Ernie sicher mit Bert zu steuern
- Aufzeichnng erster Trainigsdaten und Versuch der Übertragung zu Hugging Face
- Erstellen relevanter Trainigsdaten für eine eigenständige Programmierung von Ernie
  
## 2025-07-19 Meeting Nr 4

Hier ist der Termin im [Forum-Kalender](https://forum.garage-lab.de/t/4-treffen-robotikarm-am-19-juli-von-14-00-bis-17-00-uhr/19738)

### Tagesordnung

#### 0. Review der gedruckten Teile

Wir untersuchen die einzelnen Bauteile auf `Flächen mit Funktion`. Das hat Auswirkung auf die Positionierung des Teils auf dem Druckbett.

`Flächen mit Funktion` sollten NICHT gestützt werden, um einen sauberen Zusammenbau zu erreichen. 

`Flächen mit Funktion` sind zum Beispiel:

- Löcher zum Fixieren der Servos
- Elemente, die einzelne Bauteile verbinden (zB für den Griff am `Leader`)
- Aufnahmen für den Servo mit den Löchern für die Schrauben

???+ info "Einstellungen für den Druck im Prusa Mini"

    Die Teile wurden mit min. 3 Wänden und 25% Infill gedruckt.

Im Falle einer möglichen Verbesserung stellen wir diese Bauteile in einer neuen Version zusammen, und stellen diese Teile dem `SO-Arm`-Projekt zur Verfügung.

#### 1. Namesgebung

Wir wählen aus den Vorschlägen unsere Favoriten, die wir dem Verein zur Auswahl stellen.

#### 2. Namen auf dem Roboter plazieren

Wir wählen die geeigneten Stellen am Roboter-Arm und passen die Dateien an.

Wir haben den `Upper_Arm` ausgewählt, weil er das größte Bauteile mit ausreichend Flächen und guter Sichtbarkeit hat.

#### 3. Feedback `Servo-Bus-Controller mit Servo testen`

**Verschoben auf ein späteres Meeting**

- Vorschlag 1 `C++`

    Das C++ Repository von feetech.ch von gitee klonen.
    Ist C++ für Linux
    Hat Beispielcode für alle Funktionen
    
- Vorschlag 2 `Python`

    Das Python Repository von gitee klonen.
    Benötigt eine Python-Umgebung
      - evtl. kann man den mkdocs Container nutzen
    Hat nicht alle Funktionen im Beispielcode

#### Diverses

```text
Alles, was uns sonst so auf dem Herzen und der Zunge liegt
```

Die Bauteile brauchen einiges an Nachbearbeitung. Speziell das Entfernen der Stützen ist aufwendig.

#### Call-to-Action

```text
Was gibt es konkret zu erledigen.
```

- `Jens` druckt die noch fehlenden Teile mit langer Druckzeit (approx. 7h 🥴)
- `Marco` sortiert das Repo der `.stl`-Dateien neu

---

## 2025-06-26 Kickoff Meeting "KI-Roboter-Arm"

[Hier geht's zur Diskussion im Forum](https://forum.garage-lab.de/t/ki-roboterarm/19215/64)

### Anwesenheit

Ergibt sich aus dem Termin im internen Kalender.

<!-- 
- [ ] [$name](https://forum.garage-lab.de/u/{$name}/summary) 
-->

### Tagesordnung

#### 1. Wir drucken nicht ohne `jenskursawe`

`Leader` wird in schwarz gedruckt
`Follower` wird in orange gedruckt

Challenge:

Vorlage des `SO-Arm101` ist zu groß.
Wir haben `Prusa Mini` Drucker mit Bettmaß 180 x 180 mm

Wir warten auf `jenskursawe` für den Druck

#### 2. Umgang mit `github`

- hinzufügen von `github`-Usern in die Organisation
- hinzufügen von `Mitgliedern` in Team `SO-Arm101`

#### 3. Die nächsten Schritte

- Wir drucken die Arme
- wir montieren die Arme
- wir nehmen in Betrieb mit minimaler Umgebungsanforderung

### Diverses

- `M2vH` testet:
    - USB Controller instalieren in Container
    - ID an Servo vergeben
    - Servos in Kette ansteuern

- `BzB` Minimale Umgebung finden

### Call to Action

- Wir haben eine To-Do-Liste im GitHub Projekt [SO-Arm101](https://github.com/orgs/garagelab-dus/projects/1) 
- Wir posten Updates im `GarageLab Forum` **NUR** als Link

---
