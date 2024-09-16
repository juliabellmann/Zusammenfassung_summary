# Markdown Notizen zu HTML

Moin, dies sind meine Notizen zu HTML. 
Bei Fehlern oder Lücken würde ich mich freuen, wenn ich eine Rückmeldung von euch erhalten würde, um dies zu korrigieren.

## HTML-TAGS

- HTML Datein haben die Endung: ".html"
- Die Startseite sollte "index.html" genannt werden, da der Browser voreingestellt danach als erstes sucht
- Für plattformunabhängige Kompatibilität dürfen in Dateinamen keine Leer- und Sonderzeichen und keine Umlaute verwendet werden & es muss auf Groß- und Kleinschreibung geachtet werden. Am besten ausschließlich Kleinbuchstaben verwenden.
- `<tags>` auch "Etiketten" (unsichtbare) => Steuerbefehle ("Auszeichnungen")
- Interpretation dieser Befehle => "parsen" ("analysieren") oder rendern ("übersetzen", "wiedergeben")

- `<start-tag>`Inhalt`</end-tag>` => HTML-Element, bzw. HTML-Container

- sog. "inhaltsleere" Tags besitzen kein End-Tag, Bps: `<br>`<br>
    ->   man kann jedoch auch `<br />` schreiben, um Verwechslungen mit "normalen" Start-Tags auszuschließen

    [Link zu Übersicht HTML-Tags](https://www.mediaevent.de/html/html5-tags.html)

## KOMMENTARE 

```html
<!-- (mehrzeiliger) 
 Kommentar
 -->
```

## HTML-GRUNDGERÜST

```html
<!DOCTYPE html> <!-- Dokumenttypdefinition (DTD) (-> fehlt DTD nutzt der Browser den Quriks-Modus. Dieser ist NICHT gewünscht.) -->

<html lang="de"> <!-- Äußerer alles umschließende Container => teilt dem Browser mit, dass es sich um eine HTML-Datei handelt-->

<meta charset="UTF-8"> <!-- zur Darstellung von Sonderzeichen /Zeichenkodierung -->

<head> <!-- enthält Informationen über das Dokument, die im Browser NICHT angezeigt werden-->
    <title>Reiter-Bezeichnung</title> <!-- Browser-Reiter / Lesezeichen-->
</head>

<body> <!-- Inhalt der Webseite für den Besucher-->

</body>

</html>

```
Hinweis: Das Grundgerüst lässt sich in VScode durch die Eingabe vom Ausrufezeichen "!" + Enter aufgerufen. Die Sprache ist dort jedoch auf Englisch voreingestellt und sollte gem. Seiteninhalt angepasst werden: `<html lang="de">`.

## VERSCHACHTELTE TAGS

Tags dürfen ineinander verschachtelt werden, jedoch nicht "verdreht" ("Tupperware-Prinzip")

## BLOCK-ELEMENT

- erzeugt automatisch eien Absatz
- nehmen gesamte verfügbare Breite ein
- Bsp.: `<p> </p>`, `<h1> </h1>`, ...

## INLINE-ELEMENT

- erzeugen keinen Absatz
- werden normalerweise auf Text oder andere Objekte _innerhalb_ eines Block-Elements angewandt
- Bsp.: `<b> </b>`, `<strong> </strong>`, `<a> </a>`, ...

## ATTRIBUTE

- Attribute stehen immer nur innerhlab des Start-Tags
- Wertzuweisungen müssen immer in Anführungszeichen stehen
- vor und nach dem Gleichheitszeichen dürfen keine Leerzeichen stehen
- bei mehreren Attributen ist die Reihenfolge irrelevant

```html
<tag attribut="wert">Inhalt</tag>
Bsp:
<div class="class1 class2">Inhalt des Containers</div>
<img class="class1 class2" src="Quelle.Bildformat" alt="Bildbeschreibung zB für Screenreader oder falls das Bild nicht dargestellt werden konnte">Inhalt des Containers />
```


## KLASSEN UND IDs

Es ist möglich, dass ein Element sowohl Klassen als auch eine ID hat.
- Der Name darf keine Leer- oder Sonderzeichen enthalten und nicht mit einer Zahl beginnen

### CLASS

- Klassen können mehrfach verwendet werden

### ID

- Achtung! Es darf jede ID nur einmal pro HTML-Datei verwendet werden.
- D.h. jede ID darf nur einmal vorkommen (nicht wie klassen, die mehrfach vergeben werden), aber mehrere unterschiedliche IDs sind möglich.
- verwende keine IDs für Styling


## BENNENNUNGSREGELN

- verwende beschreibende Namen
- vermeide Abkürzungen



## HTML-CODE VALIDIEREN

Der Code sollte nach fertiger Bearbeitung validiert ("auf Gültigkeit geprüft") werden. 

Hier ein Seitenvorschlag: [HTML-Validator](https://validator.w3.org/nu/#textarea)

## SONDERZEICHEN (ENGL.: ENTITY)

Um Sonderzeichen darstellen zu können sollte folgender Meta-Tag verwendet werden 

```html
<meta charset="UTF-8">
```
### Beispiele
| Entity       | Darstellung  |
| ------------ | ------------ |
| `&amp;`      | &amp;        |
| `&gt;`       | &gt;         |
| `&lt;`       | &lt;         |
| `&copy;`     | &copy;       |

Weitere Sonderzeichen: [Link zu W3scools](https://www.w3schools.com/html/html_symbols.asp)

## FIGURE-TAG

- wird genutzt, um ein Bild als Abbildung zu kennzeichnen

```html
<figure>
    <img src="grafik.jpg" alt="Beschreibung" />
    <figcaption>Sichtbare Bildunterschrift</figcaption>
</figure>
```

- empfohlenes Attribut: `loading="lazy"` -> es werden nicht alle Bilder auf einmal geladen, sodass die Lade-Geschwindigkeit erhöht wird

- im `<img />` width & height immer Pixelwerte

- Bildgröße -> Darstellung &#8800; Auflösung -> reale Dateigröße


## LINKS

### Verknüpfung von Seiten

```html
<a a href="andererDateiname.html">Benennung des Links</a> <!-- Verknüpfung zu einer anderen HTML-Datei -->
```

### Verknüpfung von Texten/Bildern

```html
<p id="verknuepfung1">Verknüpfter Text</p> <!-- hierfür wird eine ID benötigt (Hinweis: IDs sind nur einmal pro HTML-Datei zu vergeben) -->
<a a href="andererDateiname.html#verknuepfung1">Text, der zum Link zum verknüpften Text wird</a> <!-- Verknüpfung zu Text in einer anderen HTML-Datei -->
<a a href="#verknuepfung1">Text, der zum Link zum verknüpften Text wird</a> <!-- Verknüpfung zu Text in der selben HTML-Datei -->
```
### target-Attribute
Links könenn ein target-Attribut enthalten. Es gibt 5 Optionen:
- `target="_self"`: verknüpfte Seite wird im selben Browserfenster (selber Reiter) geöffnet
- `target="_blank"`: verknüpfte Seite wird in einem neuen Tab geöffnet
- `target="_parent"`: verknüpfte Seite wird in einem übergeordneten iframe geöffnet
- `target="_top"`: verknüpfte Seite wird im Hauptfenster geöffnet (dem obersten übergeordneten)
- `target="_name"`: verknüpfte Seite wird im iframe mit dem Namen "name" geöffnet

## TABELLEN

```html
    <table>
        <caption>Tabellen-Überschrtift</caption>
        <thead>
            <tr>
                <th>Überschrift 1</th>
                <th>Überschrift 1</th>
            </tr>
        </thead>
        <tbody>

        </tbody>
        <tfoot>

        </tfoot>
    </table>
```

## LISTEN


## IFRAMES

- in diesem wird eine andere HTML-Seite angezeigt, zB Maps, Youtube

## META-TAGS

- werden im Kopfbereich <head> der HTML-Seite notiert
- Infos für Suchmaschinen oder Webbrowser -> für Besucher unsichtbar
- Auswahl an Tags:
    - `<meta charset="UTF-8">` -> Zeichencodierung
    - `<meta name="author" content="Name des Verantwortlichen">`
    - `<meta name="copyright" content="copyright-Inhaber">`
    - `<meta name="viewport" content="width=device-width, initial-scale=1.0">` -> Damit der Viewport nicht automatisch skaliert wird, sondern man selbst das responsive Webdesign erstellt
    - (user-scable=no -> Zoomen mit zwei Fingern deaktiviert)
