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


## META-TAGS

- werden im Kopfbereich <head> der HTML-Seite notiert
- Infos für Suchmaschinen oder Webbrowser -> für Besucher unsichtbar
- Auswahl an Tags:
    - `<meta charset="UTF-8">` -> Zeichencodierung
    - `<meta name="author" content="Name des Verantwortlichen">`
    - `<meta name="copyright" content="copyright-Inhaber">`
    - `<meta name="viewport" content="width=device-width, initial-scale=1.0">` -> Damit der Viewport nicht automatisch skaliert wird, sondern man selbst das responsive Webdesign erstellt
    - (user-scable=no -> Zoomen mit zwei Fingern deaktiviert)


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
<tag attribut="wert">Inhalt</tag> <!-- Hinweis: "tag" ist kein gültiger Tag -->
Bsp:
<div class="class1 class2">Inhalt des Containers</div>
<img class="class1 class2" src="Quelle.Bildformat" alt="Bildbeschreibung zB für Screenreader oder falls das Bild nicht dargestellt werden konnte">Inhalt des Containers />
```


## KLASSEN UND IDs

Es ist möglich, dass ein Element sowohl Klassen als auch eine ID hat.
- Der Name darf keine Leer- oder Sonderzeichen enthalten und nicht mit einer Zahl beginnen

### CLASS

- Klassen können mehrfach verwendet werden (mit Leerzeichen trennen)
- für sich wiederholende Stile oder Funktionen verwenden

### ID

- Achtung! Es darf jede ID nur einmal pro HTML-Datei verwendet werden.
- D.h. jede ID darf nur einmal vorkommen (nicht wie klassen, die mehrfach vergeben werden), aber mehrere unterschiedliche IDs sind möglich.
- verwende keine IDs für Styling


## BENNENNUNGSREGELN

- verwende beschreibende Namen
- Vermeiden zu lange Namen
- vermeide Abkürzungen, die schwer zu verstehen sind
- keine Leerzeichen
- nicht mit Zahl beginnen
- können Buchstaben, Zahlen, Unterstriche (_) und Bindestriche (-) enthalten
- Case-Sensitive (Groß- und Kleinschreibung wird unterschieden)
- Konsistente Namenskonventionen verwenden (z.B. camelCase)


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


## LINKS - Hyperlinks

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

## FORMULARE

Formular wird zwischen `<form> </form>` geschrieben.

### Festlegen des Ziels

Das Attribut `action` definiert den Zielort für die Formulardaten, wo sie verarbeitet werden sollen. `#` ist ein "Platzhalter".
```html
<form action="#"> </form>
```

### Beschriften von Formularfeldern

Formularelemente können mit Hilfe des `label`-Tags beschriftet werden. Das Attribut `for` bezieht sich auf die ID des Formularelements.

`<label for="nameDerID">Beschriftung des Formularfelds</label>`

### Mögliche Tags

- input -> Input-Feld
- label -> Beschriftung des Input-Felds
- select -> Dropdown-Liste
- textarea -> Mehrzeilige Texteingabe
- button -> klickbares Feld/Button
- fieldset -> Gruppiert Elemente
- legend -> Überschrift für ein `<fieldset>`-Element
- datalist -> Liste vordefinierter Optionen für Autocomplete-Funktion
- output -> Ergebnis einer Berechnung
- option -> Definiert Optionen in der Dropdown Liste `<select>`
- optgroup -> Definiert Gruppierungen innerhalb der Dropdown Liste `<select>`


### Mögliche Attribute

#### Form-Element Attribute

- action: Gibt an, wohin die Formulardaten gesendet werden sollen, wenn das Formular abgesendet wird
- method: Spezifiziert die HTTP-Methode, die beim Senden der Formulardaten verwendet werden soll (GET oder POST)
- autocomplete: Legt fest, ob das Formular automatisch vervollständigt werden soll
- novalidate: Deaktiviert die Validierung des Formulars beim Absenden
- target: Gibt an, wo die Antwort nach dem Absenden des Formulars angezeigt werden soll (_self, _blank, _parent, _top oder ein Frame-Name)

#### Eingabe-Element Attribute
- Die folgenden Listen enthält fast alle möglichen Attribute für Eingabeelemente in HTML. Es gibt einige spezielle Attribute, die nur für bestimmte Eingabetypen gelten, aber diese Liste deckt die meisten gängigen und wichtigen Attribute ab.

Allgemeine Attribute

    type: Spezifiziert den Typ des Eingabefelds (z.B. text, password, checkbox, radio etc.)

    name: Gibt den Namen des Eingabefelds an, der für die Datenübertragung verwendet wird

    value: Setzt einen vordefinierten Wert für das Eingabefeld

    id: Eine eindeutige Identifikation für das Element

    class: Klassenbezeichnung für Stilierungszwecke

    style: Inline-Stile für das Element

    data-*: Benutzerdefinierte Datenattribute

    title: Ein Tooltip, der bei Hover angezeigt wird

    tabindex: Die Reihenfolge, in der das Element fokussiert wird

    accesskey: Ein Tastaturkürzel zum Fokussieren des Elements

    hidden: Versteckt das Element

Form-spezifische Attribute

    form: Assoziiert das Element mit einem bestimmten Formular

    formaction: URL für die Formularübermittlung (nur für Submit-Typen)

    formenctype: Codierungstyp für die Formularübermittlung (nur für Submit-Typen)

    formmethod: HTTP-Methode für die Formularübermittlung (nur für Submit-Typen)

    formnovalidate: Umgeht die Validierung beim Absenden (nur für Submit-Typen)

    formtarget: Ziel-Fenster für die Antwort nach dem Absenden (nur für Submit-Typen)

    autocomplete: Aktiviert/deaktiviert die Autocomplete-Funktion

    autofocus: Setzt den Fokus automatisch auf dieses Element beim Laden der Seite

    disabled: Deaktiviert das Element

    readonly: Macht das Feld schreibgeschützt

    required: Macht das Ausfüllen des Feldes obligatorisch

    placeholder: Fügt einen Platzhaltertext ein

    pattern: Definiert ein reguläres Ausdrucksmuster für die Validierung

    min und max: Legen Mindest- und Höchstwerte für numerische Eingaben fest

    step: Definiert den Inkrementalschritt für numerische Eingaben

    multiple: Erlaubt mehrere Werte (für Email und Datei-Eingaben)

    accept: Gibt akzeptierte Dateitypen für Dateieingaben an

    capture: Media-Capture-Modus für Dateieingaben

    checked: Markiert Checkboxen oder Radiobuttons als vorausgewählt

    dirname: Richtungsattribut für bidirektionale Texteingaben

    list: Verlinkt das Eingabefeld mit einer <datalist> für Vorschläge

    maxlength und minlength: Begrenzen die Länge des Eingabetextes

    size: Setzt die Breite des Eingabefelds in Zeichen

    src, height, width: Für Bild-Eingaben (Typ "image")

    alt: Alternativtext für Bild-Eingaben

    usemap: Verbindet das Bild mit einer Client-Side Image Map

    ismap: Erzeugt eine Server-Side Image Map

    align: Positioniert das Bild horizontal oder vertikal

    border: Setzt den Rahmen des Bildes

    hspace und vspace: Abstand vom Bild zu anderen Elementen

    longdesc: Verweis auf eine detaillierte Beschreibung des Bildes

    onchange, onclick, onfocus, onblur, onselect: Ereignishandler


#### Weitere Attribute

- form: Verknüpft ein Formularelement mit einem bestimmten Formular
- disabled: Deaktiviert das Element und macht es nicht auswählbar
- autofocus: Setzt den Fokus automatisch auf dieses Element beim Laden der Seite


[Link zu Form Elements](https://www.w3schools.com/html/html_form_elements.asp)

## LISTEN


## IFRAMES

- in diesem wird eine andere HTML-Seite angezeigt, zB Maps, Youtube