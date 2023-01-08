# Use Cases
## Alle Dateien in neues Commit packen und pushen
```shell
git add --all
git commit -m "Message xy"
git push
```

## Remote Repository klonen
```shell
git clone https://github.com/gitrepo/myrepo.git
```

## Lokales leeres Repository erstellen und mit Remote verbinden
```shell
git init
git remote add origin https://github.com/gitrepo/myrepo.git
git push --set-upstream origin main
```

## Die letzten 10 Commits sehen
```shell
git log --oneline -10
```

## Status erhalten über staged / untracked Dateien
```shell
git status
```

## Aktuellen lokalen Branch herausfinden
```shell
git branch -a
```

## Branch wechseln
```shell
git switch <existing_branch>
```

## Neuen branch erstellen und zu ihm wechseln
```shell
git switch -c <non_existing_branch>
```

# Die meistgenutzten Befehle
## git clone
```git clone:``` Dieser Befehl erstellt eine lokale Kopie eines Git-Repositories auf dem Computer des Benutzers.

Die häufigsten Argumente für den Befehl ```git clone``` sind:

	-b oder --branch, mit dem man einen bestimmten Branch des Repositories klonen kann.
		Beispiel: git clone -b my-branch https://github.com/user/repo.git

	-l oder --local, mit dem man ein lokales Repository klonen kann.
		Beispiel: git clone --local /path/to/repo

	-s oder --shallow, mit dem man nur die letzten X Commits des Repositories klonen kann.
		Beispiel: git clone --shallow 5 https://github.com/user/repo.git

	-o oder --origin, mit dem man den Namen des ursprünglichen Repositories angeben kann.
		Beispiel: git clone -o my-origin https://github.com/user/repo.git

## git add
```git add:``` Dieser Befehl fügt Dateien zum Staging-Bereich hinzu, wo sie für eine spätere Commit-Operation vorbereitet werden.

Die häufigsten Argumente für den Befehl ```git add``` sind:

	-A oder --all, mit dem alle Dateien im Working Tree dem Index hinzugefügt werden.
		Beispiel: git add -A

	-p oder --patch, mit dem man interaktiv bestimmte Änderungen zum Index hinzufügen kann.
		Beispiel: git add -p

	-u oder --update, mit dem man nur Dateien dem Index hinzufügt, die bereits verfolgt werden.
		Beispiel: git add -u

	-f oder --force, mit dem man Dateien dem Index hinzufügt, auch wenn sie in der Datei .gitignore aufgeführt sind.
		Beispiel: git add -f myfile.txt

## git commit
```git commit:``` Dieser Befehl nimmt die Dateien im Staging-Bereich und speichert sie dauerhaft im Git-Repository, inklusive einer Nachricht, die die Änderungen beschreibt.

Die häufigsten Argumente für den Befehl ```git commit``` sind:

	-m oder --message: mit dem eine Nachricht für den Commit angegeben wird.
		Beispiel: git commit -m "Initial commit"

	-a oder --all: mit dem alle geänderten Dateien automatisch dem Commit hinzugefügt werden.
		Beispiel: git commit -a

	-am oder --amend: mit dem ein vorheriger Commit geändert wird.
		Beispiel: git commit --amend -m "Updated commit message"

	-p oder --patch: mit dem man interaktiv bestimmte Änderungen zum Commit auswählen kann.
		Beispiel: git commit -p

## git push
```git push:``` Dieser Befehl überträgt alle Commits vom lokalen Repository zum entfernten Repository auf einem Git-Server.

Die häufigsten Argumente für den Befehl ```git push``` sind:

	-u oder --set-upstream, mit dem man einen neuen Remote-Branch erstellt und diesen als Upstream-Branch festlegt.
		Beispiel: git push -u origin my-branch

	-f oder --force, mit dem man Änderungen auf dem Remote-Repository erzwingt, auch wenn es zu Konflikten kommt.
		Beispiel: git push -f

	-d oder --delete, mit dem man einen Branch im Remote-Repository löscht.
		Beispiel: git push -d origin my-branch

	-v oder --verbose, mit dem man detailliertere Ausgaben erhält.
		Beispiel: git push -v

## git pull
```git pull:``` Dieser Befehl synchronisiert das lokale Repository mit dem entfernten Repository, indem er die neuesten Änderungen herunterlädt und in das lokale Repository einfügt.

Die häufigsten Argumente für den Befehl ```git pull``` sind:

	-r oder --rebase, mit dem man die Änderungen aus dem Remote-Repository als Rebase statt als Merge in den aktuellen Branch integriert.
		Beispiel: git pull -r

	-f oder --force, mit dem man die Änderungen aus dem Remote-Repository auch dann zieht, wenn es zu Konflikten kommt.
		Beispiel: git pull -f

	-p oder --prune, mit dem man lokale Branches löscht, die im Remote-Repository nicht mehr vorhanden sind.
		Beispiel: git pull -p

	-a oder --all, mit dem man Änderungen von allen Branches im Remote-Repository zieht.
		Beispiel: git pull -a

## git status
```git status:``` Dieser Befehl zeigt den aktuellen Status des Git-Repositories an, einschließlich unveränderter und geänderter Dateien sowie Dateien, die für eine Commit-Operation vorbereitet sind.

Die häufigsten Argumente für den Befehl ```git status``` sind:

	-s oder --short:, mit dem man eine kurze Übersicht über den aktuellen Status des Repositorys erhält.
		Beispiel: git status -s

	--b oder --branch:, mit dem man den Namen des aktuellen Branches anzeigt.
		Beispiel: git status -b
	
	--u oder --untracked:, mit dem man untracked (nicht verfolgte) Dateien anzeigt.
		Beispiel: git status -u
	 
	--uno oder --untracked-files=no:, mit dem man Informationen über untracked Dateien ausblendet.
		Beispiel: git status --ignored