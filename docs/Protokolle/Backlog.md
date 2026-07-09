# Die Protokolle vom Robo-Arm

## Nächstes Meeting

???+ info "Jetzt schon vormerken"

    **Donnerstags ab 18 Uhr im Protolab**

    ```text
    Nächstes Meeting: Nr. 30

    Endlich mal was mit KI 
    👩‍🔧👩🏽‍🔧 🤖🦾 👨‍🔧👨‍🔧
    ```

Der Link zum [`Termin im Forum`](https://forum.garage-lab.de/t/roboterarm-workshop-donnerstag/22493) 

## 2026-07-09

```zsh
# run in terminal
./run_a_teleop.sh
```

wait for update

## 2026-7-02

### Shell Befehle zum Starten einer Session mit lerobot
Wir haben verschiedene Scripte vorbereitet, damit das starten einer Session mit lerobot schneller geht.
- *run_a_teleoperation.sh* startet den Teleoperationsmodus; startet das Programm rerun.io;
- *run_a_trainig.sh* startet den Trainingsmodus.
- *run_a_policy.sh* startet eine Policy Session.

## 2026-6-18
### Checkliste zum Starten von Ernie und Bert
- [ ] Kameradeckel abgemacht
- [ ] Strom Lichtleiste
- [ ] USB Hub mit Mac verbinden
- [ ] Roboter USB Hub
- [ ] Overshoulder Kamera
- [ ] USB Roboter Bert
- [ ] Strom Roboter Bert
- [ ] Strom Netzteil eingeschaltet
- [ ] Kamera Roboter Ernie
- [ ] USB Roboter Ernie
- [ ] Strom Roboter Ernie

## 2026-04-21 Meeting Nr 16
### Training eines ersten Modells auf dem MacBook
Wir haben die vorhandene LeRobot-Aufzeichnung auf dem MacBook benutzt, um zum ersten Mal ein lokales Modell zu trainieren. Ziel war zunächst nicht maximale Qualität, sondern ein stabil laufendes Training auf Apple-Hardware.

#### Ausgangspunkt

- Es gibt bereits eine aufgezeichnete LeRobot-Datenbasis
- Die Daten liegen lokal im LeRobot-Cache des Arbeitsverzeichnisses
- Das Training lief **nur lokal**, also ohne Upload zu Hugging Face
- Das Training lief auf einem MacBook mit Apple Silicon

#### Start des Trainings

Wir haben das Training mit folgendem Befehl gestartet:

```sh
lerobot-train \
  --policy.type=act \
  --policy.device=mps \
  --policy.push_to_hub=false \
  --policy.dim_model=128 \
  --policy.chunk_size=20 \
  --policy.n_action_steps=20 \
  --dataset.repo_id=garagelab-duesseldorf/record-test-02 \
  --wandb.enable=false \
  --batch_size=1 \
  --num_workers=0 \
  --steps=40000 \
  --log_freq=10 \
  --save_freq=1000 \
  --output_dir=policies/record-test-02
```

#### Warum diese Parameter auf dem MacBook wichtig waren

- `--policy.type=act`
  Wir nutzen das ACT-Modell. Das war für den ersten Versuch einfacher zu überblicken als schwerere Alternativen.

- `--policy.device=mps`
  Damit nutzt LeRobot die Apple-GPU über Metal. Ohne diesen Parameter würde das Training deutlich langsamer oder unnötig auf der CPU laufen.

- `--policy.push_to_hub=false`
  Verhindert, dass das trainierte Modell zu Hugging Face hochgeladen wird. Für unseren Versuch sollte alles lokal bleiben.

- `--policy.dim_model=128`
  Das ist kleiner als die großen Standardwerte und reduziert Rechenlast und Speicherbedarf deutlich. `128` war ein brauchbarer Kompromiss: klein genug für das MacBook, aber groß genug für ein ernsthaftes Training.

- `--policy.chunk_size=20`
  Das Modell sagt immer 20 Aktionen auf einmal voraus. Ein kleinerer Wert macht das Training deutlich leichter als die Default-Konfiguration.

- `--policy.n_action_steps=20`
  Passt hier zum `chunk_size`. Das Modell arbeitet also mit 20er Action-Blöcken und bleibt damit in einer einfachen, gut nachvollziehbaren Konfiguration.

- `--dataset.repo_id=garagelab-duesseldorf/record-test-02`
  Damit wird das lokale, bereits vorhandene Datenset ausgewählt.

- `--wandb.enable=false`
  Wir haben kein Weights & Biases benutzt. Für den ersten Lauf reichten uns Terminal-Logs und Checkpoints.

- `--batch_size=1`
  Das war wichtig für den Speicherbedarf. Mit größerer Batch Size wäre das MacBook deutlich schneller an seine Grenzen gekommen.

- `--num_workers=0`
  Keine zusätzlichen DataLoader-Prozesse. Das spart RAM. Gerade auf dem MacBook war das wichtig, weil sonst schnell zu viel Speicher belegt wird.

- `--steps=40000`
  Wir haben die Schrittzahl so gewählt, dass das Training ungefähr in eine längere Laptop-Session passt. Das ergab in der Praxis ungefähr 10 Stunden Laufzeit.

- `--log_freq=10`
  Alle 10 Schritte wird ein Zwischenstand ausgegeben. So kann man sehen, ob das Training läuft oder hängt.

- `--save_freq=1000`
  Alle 1000 Schritte wird ein Checkpoint gespeichert. Das ist wichtig, um später ältere Stände zu vergleichen oder bei Bedarf fortzusetzen.

- `--output_dir=policies/record-test-02`
  Hier landen die Checkpoints und die Trainingskonfiguration.

#### Beobachtungen beim Training

Mit den anfänglichen Default-Werten war das Training auf dem MacBook zu langsam und zu schwergewichtig. Mit der kleineren Konfiguration lief es stabil.

Ein typischer Stand während des Trainings sah etwa so aus:

```text
step:40K smpl:40K ep:22 epch:4.45 loss:0.088 grdn:19.369 lr:1.0e-05 updt_s:0.864 data_s:0.068
```

Wichtig daran:

- `loss:0.088` zeigt, dass das Modell etwas gelernt hat
- `epch:4.45` bedeutet ungefähr 4,45 Durchläufe durch die Daten
- `updt_s:0.864` zeigt die Rechenzeit pro Trainingsschritt
- `data_s:0.068` zeigt, dass die Datenzufuhr nicht das Hauptproblem war

#### Ergebnis

Nach dem Training liegt ein fertiges Modell im Ausgabeordner, zum Beispiel hier:

```text
policies/record-test-02/checkpoints/040000/pretrained_model
```

Dieses Modell kann anschließend für Inferenz mit dem Roboter benutzt werden.

### Nächste Schritte
- Ein oder mehrere Checkpoints am echten Roboter testen
- Beispiel für einen ersten Inferenz-Lauf mit einem trainierten Checkpoint:
  ```sh
  lerobot-record \
    --robot.type=${ernie_type} \
    --robot.port=${ernie_port} \
    --robot.id=${ernie_id} \
    --policy.path=policies/record-test-02/checkpoints/040000/pretrained_model \
    --policy.device=mps \
    --dataset.repo_id=garagelab-duesseldorf/eval-record-test-02 \
    --dataset.push_to_hub=false \
    --dataset.num_episodes=5 \
    --dataset.single_task="Test des trainierten Modells mit Ernie"
  ```
- Evaluationsläufe getrennt von den Trainingsdaten aufzeichnen
- Prüfen, ob 20k / 30k / 40k Schritte einen merklichen Unterschied machen
- Später bessere oder vielfältigere Trainingsdaten aufnehmen

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
