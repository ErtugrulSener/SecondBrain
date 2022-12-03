# EditorConfig

EditorConfig bietet eine Struktur um Konfigurationen für Coderichtlinien über IDE's und Textbearbeitungstools sowie Build Tools zu teilen.

Hauptziel ist es, konsistenten Code zu haben. Siehe folgende Möglichkeiten.

# Kommentare

In frühereren Versionen konnte man ein Semikolon (;) oder eine Raute (#) für die Einleitung von Inlinekommentaren nutzen, allerdings wussten User dann nicht wie sie Texte mit Semikolon als Value eines Pairs abbilden sollten. Daher gibt es seit set Version *0.15.0* keine Inlinekommentare. Seit dieser Version, muss das Kommentarzeichen das erste Zeichen der Zeile sein, ergo:

```EditorConfig
# Ich bin ein Kommentar
key1 = value1

; Und ich auch!
key2 = value2
```

# Warum nicht .gitattributes nutzen?

1) Es gibt keine Möglichkeit das Charset anzugeben per .gitattributes
2) Wenn die Datei nicht eingecheckt wird, werden die Regeln auch nicht applied für die Dateien, ein git add bzw. git commit selbst macht noch nichts im File Tree.
3) Bei Nutzung von EditorConfig + .gitattributes hat man zwei Sources of True, keine Vereinheitlichung, die Einstellungen welche Datei mit welchem Line Ending gelesen / gespeichert wird ist verstreut.
4) .gitattributes kann mitunter beim Klonen eines großen Repos sehr viel Zeit kosten, weil jede Datei mit seinem bestimmten File Ending gespeichert werden muss, dafür muss sie natürlich auch konvertiert werden.

# Zur Spezifikation
[Spezifikation](https://editorconfig-specification.readthedocs.io/)

# Glossar
| Wort              | Bedeutung                                                                                                                                                                             |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Editor            | Ein Editor ist im folgenden Kontext ein Sammelbegriff für jegliche Tools, mit denen man Source Code editieren kann. z.B: Notepad++, Eclipse aber auch CLI-Tools wie vim gehören dazu. |
| Pair              | Ein Key-Value Paar, bezeichnet eine Option in EditorConfig. z.B: tab_width = 4 mit "tab_width" als key und "4" als value.                                                             |
| Value             | Ein Value ist der rechte Teil eines Pairs. Value's gibt es nur in Bezug auf Pairs.                                                                                                                                                                                      |
| Global Expression | Eine global Expression ist eine in Klammern geschriebene Zeichenkette, welche spezifiziert für welche Dateitypen die folgenden Pairs (Einstellungen) gelten. z.B: [*.txt*]            |

# Editoren
## Für PLX relevante Editoren
- Eclipse
- Notepad++
- Atom

## Zusätzliche unterstützte Editoren
- IntelliJ IDEA
- VSCode

```
IntelliJ IDEA ist zum Stand Erstellung dieses Dokumentes noch nicht in weitflächiger Benutzung innerhalb der PLX Developer Community und Notepad++ eignet sich am ehesten um kleine Dateien anzusehen.

VSCode dagegen ist nach meiner Erfahrung bei der Java und C# - Entwicklung ein riesiger Aufwand, den man zunächst leisten muss, um überhaupt etwas build und debugfähiges zu erhalten.
```

# Plugins
| Editor  | Link                                                   |
| ------- | ------------------------------------------------------ |
| Eclipse | https://github.com/ncjones/editorconfig-eclipse#readme | 

# Probleme bei Nutzung des Plugins mit Eclipse
- Das Plugin wird nicht mehr weiterentwickelt, auch EditorConfig selbst (das Repo) ist vom selben Source und wird nicht mehr weiterentwickelt
- Die .editorconfig Datei wird nur beim Start von Eclipse gelesen, danach nicht mehr
- Bei einem fehlerhaften Encodingstart wie "CP-1252" setzt das Plugin das Encoding von Eclipse auf genau diesen Wert, bei erstellen einer Datei erhält man die wenig hilfreiche Nachricht:

```ad-note
Reason:
CP-1252
```

- z.B: das € - Symbol kann nicht im Source Code genutzt werden, weil Latin-1 dieses Zeichen nicht unterstützt. Siehe hier:

![[Eclipse-Latin1-Euro-Symbolerror.png]]

Bei cp-1252 bzw. windows-1252 wäre es drin gewesen.

# Konfigurationsparameter
## Line Endings festlegen
*option* = lf | cr | crlf

end_of_line = *option*

## Charset festlegen
*option* = latin1 | utf-8 | utf8-bom | utf-16be | utf-16le

chrset = *option*

## Tab weite festlegen
*default* = Wert von indent_size Parameter

tab_width = 4

## Whitespaces am ende der Zeile entfernen
trim_trailing_whitespace

## Neue Zeile am Ende einfügen
insert_final_newline = true

## Parameter wieder löschen und default-Werte nutzen
insert_final_newline = unset