## Branch als Snapshot
Ein Branch in Git ist ein Snapshot eines Commits im Versionsbaum. Es ist ein Pointer auf einen Commit.

## Remote vs. local Branch
Der Remote Branch ist der Branch, der auf dem Repository verwaltet wird. Git ist ein dezentralisiertes Versionsverwaltungssystem, das heißt man hat einen vollständigen Stand bei sich lokal und arbeitet auf dem.

## Historie des Branches
Die Historie des Branches ist nicht im Branch gespeichert. Für die Historie, muss man einfach alle Commits bis zum Root-Commit im Graphen "besichtigen" und den Namen ausgeben.

## Git Checkout Interna

![[versionsbaum.png]]

Wenn man z.B: einen neuen Branch auscheckt mit dem Befehl:

```Bash
git checkout branch-a
```

Dann muss Git, je nach dem ob der HEAD-Commit des Branches in der Zukunft oder in der Vergangenheit liegt, Commits vor oder zurücklaufen. Deswegen kann ein Checkout sehr lange dauern, wenn man an eine sehr frühe Version eines Branches zurückläuft.

```ad-note
Das stimmt aber nur teilweise, Git stellt hier intern auch Optimierungen an und nutzt Caching Mechanismen.
```