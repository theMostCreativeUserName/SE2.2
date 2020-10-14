# SE2.2

## Gliederung
1. Git
2. JavaDoc
3. PMD
4. Checkstyle
5. IntelliJ Line Coverage
6. Mutations
7. CNN Überprüfen
8. SpotBugs


---
### 1. Git
#### git übers Terminal
+ zuerst müsst ihr dieses Repository (=Repo) clonen mit **git clone <URL>**
+ das komplette Projekt wird mit **git pull origin** geupdatet
Änderungen durchführen:
+ wenn ihr etwas an dem Projekt gändert habet, könnt ihr die geänderten Dateien mit dem Befehl **git status** einsehen
+ um die Änderungen auf dieses GitHub-Repo hochzuladen müsst ihr
  1. in eurem lokalen git-Repo die hochzuladenen Dateien per **git add <dateiname>** (oder *git add .*, wenn alle geänderten Dateien hochgeladen werden sollen) in den Modus **Staged** setzen
  1. alle Staged Dateien könnt ihr mit **git commit** als einen upload speichern
        + nachdem ihr diesen Befehl ausführt wird sich ein Editor-Fenster (meistens Nano) öfnen in dem ihr eine passende Commit-Nachricht für den Commit schreiben müsst.
  1. diese Commits könnt ihr dann mit **git push** auf das gitHub-REpo hochladen
 
**WICHTIG**

kreiert für jedes Feature, dass ihr erstellt einen eigenen Zweig. Für diesen wird dann später automatisch ein Pull-Request erstellt, der von allen anderen Teilnehmern überprüft werden kann.
+ ein Branch wird erstellt mit: **git branch <branchname>**
+ ein Branch wird lokal per: **git checkout <branchname>** ausgewählt, auf diesen könnt ihr dann eure Änderungen (wie vorher beschrieben) durchführen
  
für weitere Informationen/Tutorials:
[Git Branching Tutorial](https://learngitbranching.js.org/?locale=de_DE "learngitbranching.js.org"), 
[Git und GitHub Video-Tutorials](https://www.youtube.com/watch?v=3RjQznt-8kE&list=PL4cUxeGkcC9goXbgTDQ0n_4TBzOO0ocPR "youtube.com/TheNetNinja")

 


### 2. JavaDoc 
1. IntelliJ Menüpunkt **"Tools"** --> "Generate JavaDoc"
1. Wählt eine "Output directory", dort wird die Dokumentation gespeichert.
1. Im Feld "Other command line arguments:" müsst ihr folgendes einfügen: "--enable-preview --release 14". Danach könnt ihr auf "OK" klicken. Sollte es keinen Fehler geben, sollte sich der Browser mit der Dokumentation öffnen. Geschieht dies nicht, exestieren Fehler, welche im Terminal ausgelesen werden können. In diesem Fall ist die entsprechende Zelle mit "Fehler" zu kennzeichnen.

### 3. PMD
1. Herunterladen/Speichern von PMD-Vorlagen
1. INtelliJ Menüpunkt **"Files"** --> Settings --> Other Settings --> PMD --> beim Seitenlabel *RuleSet* auf das '+' --> auf "Browse" --> PMD-File auswählen
1. Laufen lassen könnt ihr das PMD indem ihr, auf den zu testenden Ordner rechts-klickt und Run **PMD auswählt** --> Custom Rules --> eure PMD-Datei

### 4. Checkstyle
1. Herunterladen/Speichern con Checkstyle-Vorlagen
**stellt sicher dass ihr die neuste Version des Checkstyle-Plugins habt**
1. IntelliJ Menüpunkt **"Files"** --> Settings --> Other Settings --> Checkstyle --> auf '+' bei "Configuration File" --> im Pop-Up Fenster einen Namen eingeben und über "Browse" Checkstyle-File auswählen
####falls ihr trotzdem noch Probleme habt
1. versucht Bestandteile von Java 14 Preview aus zu kommentieren. Beachtet bei Fehlern, welche Auswirkungen sie auf den auskommentierten Teil haben.
1. versucht eure Java-Version auf "13 - SDK default" zu setzen und nochmal zu parsen. (siehe unten)
1. prüft ob ihr Rechtschreibfehler in der Datei habt (grün unterringelt von IntelliJ) --> Worte wie *Electro* könnt ihr zum Wörtebuch von IntelliJ hinzufügen. (siehe unten)
##### Ändern der Java-Version
1. intelliJ Menüpunkt **"Files"** --> Project Settings
1. heir auf **Project** und dann die Projekt SDK ändern
##### Aufnehmen neuer Worte ins Wörterbuch
1. klickt auf das Wort, dass ihr hinzufügen wollt
1. presst **ALT** + **ENTER** auf der Tastatur oder klickt auf die Glühbirne, die in der Zeile des Wortes erscheint 
1. wählt: save "Wort" in project-level dictionary

### 5. IntelliJ Line Coverage
#### Normal
In IntelliJ oben rechts neben dem grünen Run-Button auf das Schild-Symbol mit Button klicken
![Coverage Tool](https://i.stack.imgur.com/sW22A.gif)

#### Mit JaCoCo
1. Lasst einmal alle Tests mit Coverage durchlaufen.
1. Anschließen klickt auf "Run" in der Menüleiste und klickt dort auf "Profile".
1. Nun müsstet ihr ein Auswahlfenster bekommen, klickt auf einen Eintrag nach dem folgenden Muster: "All in \<euer Projektname\>". Es öffnet sich ein weiteres Menü, klickt dort auf "Edit".
1. In dem jetzt geöffneten Fenster ändert ihr den Namen auf "JaCoCo", damit ihr die Konfiguration wieder findet. Klickt danach auf den Menüpunkt "Code Coverage" und wählt dort als "Choose coverage runner:" "JaCoCo" aus.
1. Nun könnt ihr das Profil mit Klick auf "Apply" speichern und das Fenster mit "Close" verlassen.
1. Wählt nun unter "Run" den Punkt "Run...". Bei dem geöffneten Fenster klickt auf den kleinen Pfeil neben dem Profil "JaCoCo" und wählt dort "Cover".
1. Hinweis: JaCoCo ist ab den 2020 Versionen von IntelliJ verfügbar. 
1. Schaut euch die Class, Method, Line and Branch in % an. Mit klicken auf einen Ordner könnt ihr euch genauere Informationen bekommen. Beachtet: Asserts können ignoriert werden (Zählen -2 bei Branch) und die damit meist nicht verbundene Abnahme der Klasse (-1).
1. Ihr könnt zum einfacheren Überblick eure Farben der Coverage ändern, fragt dafür bei den Projektleitungen an.

### 6. Mutations
1. instaliert das **"PIT Runner"** Plugin für IntelliJ
1. in IntelliJ --> auf **Edit Configuration**, im Drop-Down Menü neben dem Run-Symbol
1. im Pop-Up Fenster auf das '+' --> im Drop-Down Menü "Pit Runner" auswählen
1. bennent diese Datei und tragt folgende Daten ein:

|im Feld | Daten | wird automatisch generiert |
| --- | --- | --- |
| Target classes | edu.hm.Severin.SE.* | Nein |
| Target tests | edu.* | Nein |
| Source dir | < Euer-PATH-zum-Project > | Ja |
| Report dir | < Euer-PATH-zum-Project >/report | Ja |
| Other params | --jvmArgs "--enable-preview" --outputFormats XML,HTML | Nein |
      
1. Apply und OK
1. um Mutations-Tests laufen zu lassen, wählt im Drop-Down Menü eure Pit Konfiguration und lasst diese laufen
1. Sobald die Tests abgeschlossen wurden, erscheint im Terminal mit weißer Schrift "Im Browser öffnen". Im geöffneten Browserfenster könnt ihr dann die ermittelt Coverage sowie die Mutation einsehen und weitere Informationen bekommen.

**Wichtig**: wenn ihr euer Projekt auf GitHub hochladet -> löscht vorher den report-Ordner, der durch die Mutationen entstanden ist

### 7. CNN Überprüfen
das Plugin von IntelliJ, dass automatisch den CNN zählt heißt **Code Metrics**
1. File --> Other Settings --> Code Metrics
1. im Seiten-Label stellt ihr folgendes ein:

|Name | Daten |
|--- | --- |
| Complexity level low | 0|
| Complexity level normal | 3 |
| Complexity level high | 5 |
| Complexity level extreme | 10 |
| Show metrics above complexity | 1|

für die Auswahlmöglichkeiten darunter wählt ihr alle aus
1. im Seiten-Label Advanced setzt ihr die folgenden Optionen aus **1** und jeglichen Rest auf **0**
      1. anonymous Class
      1. break statement
      1. class
      1. conditional expression
      1. continue satement
      1. do while
       1. for
       1. foreach
       1. if
      1. labeled statement
      1. method
      1. switch
      1. catch
      1. while
      1. polyadic expr.
1. Apply + OK

Das Plugin zählt den CNN der kompletten Klasse relativ unschön, hier müssen die einzelnen Zahlen im Drop-Down Menü aufaddiert werden
1. im Kopf der Klasse --> klickt auf den Code Metrics Kommentar (das orangene Feld) 
1. dann öffnet sich ein Drop-Down Menü in dem die CNN-Zahlen der einzelnen Methoden angezeigt werden
1. diese müssen dann aufaddiert werden

### 8. SpotBugs
1. Installiert das **SpotBugs** Plugin
1. in IntelliJ unten rechts klickt ihr dann auf das SpotBugs-Käfer Symbol
1. klickt auf **"Anylize Project files not including Test sources"** (das blaue Quadrat mit grünen Pfeil)

