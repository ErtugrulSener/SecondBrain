## DAG
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