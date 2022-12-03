## Commit als Changeset
Commits in Git sind immer ein Changeset von Dateien, die seit dem letzten Commit  geschehen ist. Dabei können Dateien hinzugefügt, entfernt oder editiert werden.

## Eindeutige Identifikation eines Commits
Ein Commit ist immer eindeutig über seine Commit ID (bzw. den Commit SHA) zu identifizieren. Meistens reichen die ersten 8 Stellen, um den Commit zu identifizieren, es gibt nur in seltensten Fellen doppelte Commits mit dem selben Anfang und dann benötigt die gesamte 40 stellige Commit id.

## Der gerichtete azyklische Graph: DAG
Der "Directed Acyclic Graph" in GIT bezeichnet die Struktur, in der Git die Commits managed.

- directed - Ein Commit zeigt auf den nächsten Commit und hat mindestens einen Parent

```ad-note
Ausgenommen von dieser Regel ist der initiale Commit (die Wurzel, die kein Parent hat) und Merge-Commits, die zwei Parents haben (eben aus den beiden Branches, die gemerged wurden).
```

- acyclic - "azyklisch", Es gibt keine Zyklen
	- i.e. keine Kreise in der Historie

## Parents eines Commits finden
```Bash
git cat-file -p <commit_id>
```

Ausgabe für einen Merge Commit könnte sein:
```Bash
tree 3db326c287e5e5130b7864d29699e5f8d49d4eb3
parent 74f3e816ed950da2566cb24cc37a5a33bac11d03
parent 479b28fc657b50ef3c2c1961003be424e7e6e94e
author esener <ertugrul.sener@t-systems.com> 1669208964 +0100
committer esener <ertugrul.sener@t-systems.com> 1669208974 +0100

C6
```

## Größe eines Commits
Ein Commit aus reinen Textdateien ist meist sehr klein, da nur die Änderungen zum letzten Commit im Versionsbaum enthalten sind. Dies gilt aber nun Mal nur für Textdateien, bei Binärdateien kann kein Diff zum alten Branch berechnet werden, also löscht Git die alte Datei und legt eine neue Datei an seiner Stelle an.

Es gibt Optimierungen die dieses Problem bekämpfen (z.B: Git LFS).