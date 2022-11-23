# Rebasing
In Git gibt es grundsätzlich zwei Wege um Änderungen von einem Branch in einen Anderen zu integrieren, diese sind:
- merge
- rebase

Um Letzteres kümmern wir uns hier.

![[rebase_1.png]]

Wenn wir uns ein Beispielfoto ansehen, wie ein Merge funktioniert, dann sehen wir das der Merge-Befehl einfach einen Drei-Wege-Merge zwischen den beiden letzten Zweig Snapshots C3 & C4 macht und dem letzten gemeinsamen Vorfahren der beiden C2. Dazu erstellt er einen neuen Commit C5.

![[rebase_2.png]]

Eine Alternative dazu ist das Rebasing. Bei diesem wird der Patch der Änderungen in C4 auf die Spitze von C3 angewendet. Damit werden alle Änderungen in Branch A zu Branch B übernommen. Folgend würden die Befehle dann aussehen:

```bash
$ git checkout experiment
$ git rebase master

First, rewinding head to replay your work on top of it...
Applying: added staged command
```

```ad-note
Intern funktioniert das übrigens folgendermaßen:

Git geht zum letzten gemeinsamen Vorfahren der beiden Branches (in diesem Falle C2), sammelt dann die Änderungen welche im aktuellen Branch (experiment) gemacht wurden, speichert diese in temporären Dateien, setzt den aktuellen Branch auf den gleichen Commit wie den Branch auf den ich rebasen möchte (hier Commit C3) und führt dann alle Änderungen erneut durch.
```

Anschließend gehen wir noch zurück auf den Master und führen einen Fast-Forward-Merge durch. Konflikte wären schon im Branch "experiment" aufgefallen.

```bash
$ git checkout master
$ git merge experiment
```

![[rebase_3.png]]

# Interessante Anwendungsfälle für ein Rebase
## Feature Branches von Feature Branches in main einpflegen

Man kann den Rebase Befehl auch verwenden, um die Commits von einem Feature Branch eines Feature Branches in den Main-Branch zu übertragen. Ergo:

main -> feature/X -> feature/Y

Wir übertragen hierbei die Commits von feature/Y direkt in main bzw. erstellen intern Patches und spielen sie auf den HEAD aus dem main-Branch auf.

Die Ausgangslage ist folgende:

![[extended_rebase_1.png]]

Wir haben einen Feature Branch server erstellt, einen Commit auf diesem gemacht und dann einen weiteren Feature Branch client aus diesem. Nun können wir das oben beschriebene folgendermaßen umsetzen:

```Bash
git rebase --onto master server client
```

```ad-note
Der Befehl heißt so viel wie "Checke den client Branch aus, finde die Patches der gemeinsamen Vorgänger client und server heraus und wende sie erneut auf den Master an."
```

Jetzt muss der Master-Branch noch vorgespult werden.

```Bash
$ git checkout master
$ git merge client
```

## Rebase ohne Branch vorher auszuchecken

Struktur:
git rebase \<Basis-Branch\> \<Themen-Branch\>

```Bash
git rebase master server
```

sprich "Rebase die Änderungen aus server in master"

# Referenzen
[Git Book](https://git-scm.com/book/de/v2)