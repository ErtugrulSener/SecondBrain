# Ansprechpartner im Incident Fall
| Rolle | Vollständiger Name | Rufnummer (Geschäftlich) | E-Mail                          | SF? | Know-How                                      |
| ----- | ------------------ | ------------------------ | ------------------------------- | --- | --------------------------------------------- |
| PO    | Arno Rogowsky      | +49 308 353 84 343       | arno.rogowsky@t-systems.com     | -   | #Serverentwicklung                            |
| H     | Ertugrul Sener     | +49 170 766 15 00        | ertugrul.sener@t-systems.com    | -   | #Git, #Gitlab, #History-Rewrite #EditorConfig |
| S     | Andreas Schampera  | +49 308 353 23 231       | andreas.schampera@t-systems.com | -   | #Git, #Gitlab, #Pipelines                     |
| S     | Björn Walther      | +49 308 353 84 298       | bjoern.walther@t-systems.com    | -   | #ClearCase                                    |
| S     | Manuel Bernhardt   | +49 170 764 69 29        | manuel.bernhard@t-systems.com   | -   | #Git, #Gitlab, #GPipelines, #Jira-Tooling     |
| S     | Peter Esser        | +49 151 724 74 055       | peter.esser@t-systems.com       | -   |                                               |
| S     | Hagen Magister     | +49 308 353 23 729       | hagen.magister@t-systems.com    | -   | #Terminmanagement                             |

# Rollenkürzel
| Kürzel | Rolle                 |
| ------ | --------------------- |
| PO     | Project Owner         |
| H      | Hauptverantwortlicher |
| S      | Stellvertreter        | 

# Glossar
| Wort | Bedeutung           |
| ---- | ------------------- |
| SF   | Sicherheitsfreigabe | 

# Im Falle eines akuten Sicherheitsvorfalls
1. Melde dich umgehend per Mail beim PO und dem Hauptverantwortlichen, die Daten entnehme dafür aus der Tabelle oben. Bitte setzte unsere Stellvertreter in CC für eine schnelle Bearbeitung. (Falls Hauptverantwortlicher im Urlaub, übernehmen die Stellvertreter.)

2. Folgende Informationen werden (mindestens) benötigt:
	- Welche Datei wurde eingecheckt?
	- In welchem Branch wurde eingecheckt?
	- Ist die Datei bereits im Main-Branch gelandet durch MR?
	- Wer ist der Ansprechpartner für weitere Fragen?

	Nutze bitte auch diese Fragen und antworte kurz darauf. Im Falle eines Sicherheitsvorfalls muss es schnell gehen, es ist nicht viel Zeit für tam tam.

# Der Unterschied zwischen Autor und Commiter

Der *Autor* der Commits steht im Commit selbst und kann leicht geändert werden (Wie untenstehend gezeigt).

Der *Commiter* ist Derjenige, der den Commit auf den Remote Branch pusht. Ermittelt wird dies anhand der Git Parameter "user.name" und "user.email". Deshalb müssen diese übrigens auch immer gesetzt werden, bevor man einen Push machen kann. Git braucht einen eindeutigen Commiter.

So könnte folgende Konstallation entstehen für ein Beispiel-Commit:

- Commiter: Ertugrul Sener <ertugrul.sener@telekom.de>
- Autor: Arno Rogowsky <arno.rogowsky@t-systems.com>

Gitlab zeigt dann folgende Nachricht in der Ansicht:

```
arno.rogowsky@t-systems.com authored 5 minutes ago and ertugrul.sener@telekom.de committed 5 minutes ago
```

# Achtsames Force Push

## Push erzwingen, ohne neue Commits auf dem Remote zu überschreiben
Es könnte natürlich passieren, dass während ich einen Commit bearbeite (z.B: Dateien aus ihm entferne oder ändere) jemand anderes ein neues Commit in den Remote pusht.

Damit wir beim Force-Push unseres Branches nicht seinen Commit überschreiben (und damit ausversehen verwerfen) gibt es seit Git Version 1.8.5 die Möglichkeit "dies vorher prüfen zu lassen". 

```Bash
git push --force-with-lease
```

Diesen Befehl werde ich in den folgenden Beispielen auch stets bevorzugt nutzen. Wenn ein neuer Commit eingecheckt wäre auf dem Remote würde man übrigens folgenden Output erhalten:

```Bash
λ git push --force-with-lease
To https://gitlab.devops.telekom.de/pfv/plx/testing-rewrite-history.git
 ! [rejected]        main -> main (stale info)
error: failed to push some refs to 'https://gitlab.devops.telekom.de/pfv/plx/testing-rewrite-history.git'
```

Der entscheidende Hinweis hierbei steckt in Klammern "stale info", was soviel heißt wie "alte Info".
Jetzt wäre es angebracht ein "git pull" zu machen und dann den Befehl erneut auszuführen. Beim Pullen wird in aller Regel ein Merge-Commit erstellt und mitgepusht. Man pusht also:
- Den Merge-Commit und
- Die neuen durch uns veränderten Commits

# Nützliche Befehle

Die folgenden Befehle helfen einem, die aktuelle Situation zu verstehen. In einem großen Projekt, kasnn dies schon Mal sehr unübersichtlich werden, es schadet daher nicht einige Befehle in seinem persönlichen Toolkasten zu kennen.

## Die letzten Commits ansehen (Eine Zeile pro Commit)

```Bash
git log --oneline [, limit]
```

Limit ist optional, falls nicht gesetzt, werden alle Commits ausgegeben.
Um nur die letzten 30 zu reviewen, kann man zum Beispiel folgendes machen:

```Bash
git log --oneline 30
```

## Auch diejenigen Commits sehen, die in keinem Branch existieren

Diese Commits würden irgendwann vom Garbage Collector von Git (Default 2 Wochen) aufgeräumt, falls sie nicht mehr referenziert werden.

```Bash
git log --oneline --reflog
```

## Branches finden, in denen ein Commit referenziert wird (Können auch temporäre, detached Branches sein)

```Bash
git name-rev --name-only <commit_id>
```


# Use Cases

## 1. Die Message des letzten Commits ändern
Use Case: Man hat ausvserehen einen Typo in der letzten Commitnachricht, der so entscheidend ist - Das man hier eine Änderung vornehmen muss.

Satzzeichen können übrigens Leben retten..

Davor: "Komm, wir essen Opa."
Danach: "Komm, wir essen, Opa."

```Bash
git commit --amend -m "Neuer Commitname"
git push --force-with-lease
```

```ad-note
"amend" ist übrigens Englisch und steht für "etwas ändern / ergänzen".
```

## 2. Den Autor des letzten Commits ändern
Use Case: Man hat einen Git Client genutzt (z.B: Eclipse) und hier fälschlicherweise die private E-Mail Adresse "playboyno.1@hotmail.de" hinterlegt. Blöd nur, dass diese Information nun auf dem Remote Branch verweilt. In unserem Falle würde die E-Mail abgeblockt, durch andere Gitlab Einstellungen.

Der Wert für den Autor des Commits muss folgende Form haben:
*Name \<E-Mail\>*

zum Beispiel:
esener \<esener@provider.de\>

```Bash
git commit --amend --author "Benjamin Blümchen <benjamin.bluemchen@tötörötöö.de" --no-edit
```

```ad-note
Wir benutzen hier --no-edit um nicht im Nachhinein in den Default Edtior zu wechseln, um auch die Commitnachricht anzupassen. Dies ist Git-Standartverhalten.
```

## 3. Einen beliebigen Commit ändern mit Interactive Rebase (Einfachere Alternative zu 4.)
Use Case: Wir möchten einen Commit ändern, das kann der Name des Commits sein oder dessen Inhalt? Alles kein Problem! Dazu einfach nur folgendes in der Kommandozeile eingeben:

```Bash
git rebase -i <base_commit_id>
```

*base_commit_id* ist hierbei der Commit, bis zu dem Interactive Rebase vom HEAD aus gesehen schaut, man kann hier auch Commit Ranges angeben ergo: \<hash_1\>..\<hash_2\>

Wir erhalten folgende Ansicht in der Konsole:

```Bash
pick 49ccc43 Second commit - Corrected
pick d9f149b Third commit

# Rebase 2e4b683..d9f149b onto 2e4b683 (2 commands)
#
# Commands:
# p, pick <commit> = use commit
# r, reword <commit> = use commit, but edit the commit message
# e, edit <commit> = use commit, but stop for amending
# s, squash <commit> = use commit, but meld into previous commit
# f, fixup [-C | -c] <commit> = like "squash" but keep only the previous
#                    commit's log message, unless -C is used, in which case
#                    keep only this commit's message; -c is same as -C but
#                    opens the editor
# x, exec <command> = run command (the rest of the line) using shell
# b, break = stop here (continue rebase later with 'git rebase --continue')
^G Help         ^O Write Out    ^W Where Is     ^K Cut          ^T Execute      ^C Location
^X Exit         ^R Read File    ^\ Replace      ^U Paste        ^J Justify      ^
/ Go To Line
```

Nun können wir folgende Dinge tun:
1. Wir können die Commits neu sortieren, dazu einfach die Reihenfolge in dieser Ansicht verändern, also z.B:

```Bash
pick d9f149b Third commit
pick 49ccc43 Second commit - Corrected
```

2. Da der Name "Second commit - Corrected" nach dem "Third commit" natürlich keinen Sinn macht, können wir ihn mit "edit" auch umbenennen zu z.B: "Last commit"

```Bash
pick d9f149b Third commit
edit 49ccc43 Second commit - Corrected
```

3. Mit "drop" könnten wir den Commit und dessen Changes auch komplett aus der History streichen, das brauchen wir nun für unser Vorhaben! Wir löschen den second sowie den third commit.

```Bash
drop d9f149b Third commit
drop 49ccc43 Second commit - Corrected
```

Für mehr Informationen, siehe: [Git Rebase - Docs](https://git-scm.com/docs/git-rebase)

## 4. Einen beliebigen Commit ändern
Beispiel aus: [StackOverflow](https://stackoverflow.com/questions/3042437/how-to-change-the-commit-author-for-a-single-commit)

Use Case: Manchmal funktioniert ein "git rebase -i <commit_id>" nicht, das hat vor allem mit der Git History zutun. Auch ein "git commit --amend .." ist hier nicht hilfreich, da der Commit nicht der letzte in der History ist.

Commits und Erklärungen:

| Commit   | Erklärung                                               |
| -------- | ------------------------------------------------------- |
| 03f482d6 | Der alte Commit, der angepasst werden soll              |
| 42627abe | Der neue Commit, der entsteht wenn wir den alten ändern | 

Vogehen:
1. Wir checken den Commit aus, den wir bearbeiten wollen
```Bash
git checkout 03f482d6
```

2. Wir ändern den Commit (Ich ändere hier z.B: die Commitnachricht, siehe auch 2. "Die Message des letzten Commits ändern")
```Bash
git commit --amend -m "My corrected message"
```

3. Wir merken uns die neue Commit ID "42627abe" und checken den original branch aus
```Bash
git checkout main
```

4. Wir ersetzen den alten Commit "03f482d6" mit dem neuen Commit von eben "42627abe"
```Bash
git replace 03f482d6 42627abe
```

5. Den alten Commit löschen
```Bash
git replace -d 03f482d6
```

6. Auf Remote pushen
```Bash
git push --force-with-lease
```
