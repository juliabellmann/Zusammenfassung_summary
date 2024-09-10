# Markdown Notizen zu Git und GitHub

Moin, dies sind meine Notizen zu Git und GitHub. 
Bei Fehlern oder Lücken würde ich mich freuen, wenn ich eine Rückmeldung von euch erhalten würde, um dies zu korrigieren.


## Definitionen

- Git: Versionskontrollsystem/-tool
- GitHub: Hosting-Plattform, die Versionskontrolle und das Zusammenarbeiten an Projekten (remote), also Git-Repositories ermöglicht
- commit: "Schnappschuss" quasi im Repro zwischenspeichern, kann man dann pushen "hochladen"
- CLI: command-line interface -> Kommandozeile

## Infos zu commit

- man kann auf vorherige Commits, d.h. Speicherstände zurückgreifen

- Regeln zu Commits:
    - kurz und beschreibend
    - IMMER auf Englisch
    - Das erste Wort sollte ein Verb sein: "add", "remove", etc.
    - Imperativ & Präsens: "add xy" anstatt "added xy"
    - Kein Punkt "." am Ende der Commit-Nachricht

## ACHTUNG :exclamation:

:exclamation: NIEMALS ein Repsitory in einem andern Repository verschachteln!

## Lokalen Ordner zu Git-Repository umwandeln

`git init` -> Inizialisiert Git


## lokales Git-Repo rückgängig machen

`rm -rf .git` -> rm: remove (entfernen); -r: rekursives Löschen; f: force (erzwingen); \<Datei>

## Status überprüfen (optional)

`git status` -> Überprüft den Git Status

> Kein Git-Repo:
>
> ```shell
> fatal: not a git repository (or any of the parent directories): .git
> ```
>
> Git-Repo:
>
> ```shell
> On branch main
> nothing to commit, working tree clean
> ```

## lokalen Git-Repo Ordner mit GitHub verbinden


1. Im Terminal in den lokalen Ordner gehen, den man zum Repo umwandeln möchte. ACHTUNG: Repos nicht verschachteln! <br />
`git init` -> Inizialisiert Git
2. Bereits vorhandene Dateien hinzufügen: <br />
`git add .` -> add: hinzufügen; ".": alle Dateien von dem Ordner, in dem man sich gerade befindet (inkl. aller enthaltenen Dateien)
3. Commit erstellen: <br />
`git commit -m "<Inhalt des Commits>"` -> -m: Nachricht, welche in den Anführungszeichen stehen muss (Regeln hierzu: siehe oben)
4. Auf GitHUb ein neues Repository erstellen.
5. Kopiere von GitHUb die SHH Adresse und kopiere sie hinter diesen Befehl:<br />
`git remote add origing <ssh-adresse>`
6. Optional: Kontrolliere, ob die Verlinkung funktioniert: <br />
`git remote -v`

    > Es sollte jetzt folgendes im Terminal erscheinen:
    > ```shell
    > origin  git@github.com:author/repo-name.git (fetch)
    > origin  git@github.com:author/repo-name.git (push)
    > ```

7. Benennung des Hauptzweis auf main: <br />
`git branch -M main` -> branch: Zweig, -M: Abkürzung für --move --force
8. Commit in GitHub verschieben "push":<br />
`git push -u origin main` -> push: hochladen, -u: set upstream (überträgt Änderungen vom lokalen Repository in das Remote-Repository und richtet die Upstream-Tracking-Beziehung ein);  origin: Kurzbezeichnung für das remote Repo, von dem das Projekt ursprünglich geklont wurde; main: Branch-Bezeichnung

HINWEIS Bei der folgenden Fehlermeldung wurden voraussichtlich die Schritte 2+3 ausgelassen. Einfach wiederholen/nachholen und dann diesen Befehl nochmals eingeben: 
```shell
$ git push -u origin main
error: src refspec main does not match any
error: failed to push some refs to 'github.com:user/repo.git'
```

9. GitHub-Seite aktualisieren. Nun sollte das Repo die gewünschten Inhalte enthalten.

## Branches

### neuen Branch erstellen und darauf arbeiten

`git switch -c <branchname>` -> erstellt einen Zweig und wechselt gleich zu ihm <br />

`git push -u origin <branchname>` -> pusht die Änderungen und den neuen Branch, danach nur noch folgendes notwendig:
`git push`

vor einem push wie gewohnt: 
- `git add .`
- `git commit -m <message>`


### Änderungen vom "working" Branch auf den Main Branch pushen

ACHTUNG hiermit "überspringt" man den Schritt des Mergens!

`git push origin working:main`


### "Working"-Branch löschen

1. vorher wieder auf den main-Branch wechseln (der aktive Branch kann nicht gelöscht werden)<br />
`git switch main`

2. Branch löschen
    - einen lokalen Branch löschen, der bereits gemerged wurde: <br /> 
        `git branch -d <branchname>`
    - Branch noch nicht gemerged, soll trotzdem gelöscht werden: <br />
        `git branch -D <branchname>`
    - remote Branch löschen: <br />
        `git push origin --delete <branchname>` oder `git push origin :<branchname>` 


Überprüfen der Branches

`git branch -a`




## Cheatsheet

[Cheatsheet-Link](https://github.com/arslanbilal/git-cheat-sheet/blob/master/other-sheets/git-cheat-sheet-de.md)
