# Markdown Notizen zu CSS

Moin, dies sind meine Notizen zu CSS. 
Bei Fehlern oder Lücken würde ich mich freuen, wenn ich eine Rückmeldung von euch erhalten würde, um dies zu korrigieren.


## CSS
Cascading Style Sheets

## Einbinden in HTML

3 verschiedene Möglichkeiten CSS einzubinden (auch kombiniert möglich):
- separate CSS-Datei(en): `<link rel="stylesheet" href="styles.css" media="screen"/>`
- CSS-Vorgaben im `<head>`
- CSS-Code im `<body>` (inline-Code)

- Beispiel Inline-Codierung: `<h2 style="color: orange;">Überschrift</h2>`

:exclamation: Empfohlen: separate CSS-Datei(en)


### Attribut media

- optionales Attribut, um das Ausgabemedium zu bestimmen, für die die CSS-Angaben gelten sollen (wichtig für responsives Design)

- `media="screen"` für die Bildschirmdarstellung
- `media="print"` für den Druck (die Browser verwenden diese CSS-Vorgaben, wenn die Webseite ausgedruckt wird)
- `media="speech"` für die Sprachausgabe
- `media="all"` für alle Medien


## Zeichenkodierung

- @-Regeln sind sozusagen die »Meta-Tags« für CSS-Dateien

- `@charset "utf-8";` -> CSS-Datei mit UFT-8 kodieren (Zeichenkodierung)

- :exclamation: ACHTUNG: Nach charset steht kein Doppelpunkt!

- :exclamation: ACHTUNG: bei mehr als einer CSS-Datei darf diese @-Regel nur in der zuerst referenzierten CSS-Datei stehen, da der Browser alle CSS-Dateien aneinander hängt und zu einer einzigen zusammen fasst


## Kommentare

`/* Kommentare werden in CSS immer so dargestellt, egal ob einzeilig oder mehrzeilig */`


## Syntax

```css
selector {
eigenschaft: wert; 
}
```

```css
selector1, selector2 {
eigenschaft: wert; 
eigenschaft2: wert2; 
}
```

- Die aus HTML bekannten spitzen Klammern gehören nicht ins CSS.
- das Semikolon nach jeder Eigenschaftszuweisung ist zwingend erforderlich


## Vererbung / specificity

- Vererbungsprinzip: Viele CSS-Vorgaben für ein Element gelten auch für alle in ihm enthaltenen Elemente, es sei denn, für eines dieser Elemente wurde etwas anderes definiert.

- ABER: nicht alle CSS-Eigenschaften sind vererbbar

    - So gelten z. B. die Schriftgröße von Überschriften und die Farbe von Links als höherwertig, sodass sie bei Bedarf separat geändert werden müssen. (Das liegt daran, dass jeder Browser bereits ein internes Stylesheet enthält, das das Aussehen jedes einzelnen HTML-Elements exakt definiert — so auch das von Überschriften und Links. Mit unseren CSS-Vorgaben überschreiben wir lediglich diese internen Browser-Styles.)


## Vor-/Nachfahren / Eltern / Kind 

Übergeordnete Elemente werden auch als Ancestor-Elemente (Vorfahren) bezeichnet, direkt übergeordnete als Parent-Elemente (Eltern). Darin enthaltene Elemente werden entsprechend Descendants (Nachfahren), direkt enthaltene Child-Elemente (Kinder) genannt. 

Mehr Spezifikationen, so etwas wie "Großeltern", gibt es nicht.

```html
<main> 
    <section> 
        <div> 
            <p>
            </p>
        </div>
    </section>    
</main>

<!-- main: Vorfahre von div und p, Elternelement von section -->
<!-- section: Kind von main, Elternelement von div, Vorfahre von p -->
<!-- div: Elternelement von p, Kindelement von section, Nachfahre von main -->
<!-- Kindelement von div, Nachfahre von section und main-->
```


## Gewichtung der Vererbung

#### 1. Spezifizierung (specificity)
-> !important > inline styling > id > class > element > * (wildcard)

#### 2. Reihenfolge (order)

#### 3. Vererbung (inheritance)
- einige Eigenschaften werden automatisch vererbt
- eigenschaft: inhertit; in dem Selector, in dem das von weiter oben vererbt werden soll


## Schriftarten

`font-family: "schriftart1", "schrift art2", sans-serif;`

- die Schriftalternativen werden durch Kommas getrennt
- Schriftarten mit Leerzeichen im Namen müssen in Anführungszeichen stehen
- mehrere Schriftalternativen sind sinnvoll -> der Browser verwendet die erste, die er auf dem System findet
- sans-serif (serifelnose Schrift) oder auch serif () möglich-> "letzte Notlösung", d.h. falls keine der zuvor genannten Schriftarten installiert sind, sucht sich der Browser eine (beliebige) vorhandene Schrift aus 

Man könnte auch spezielle Schriftarten einbinden. Ergänze ich später.

## Maßeiheiten

HINWEIS: Zwischen dem Wert und der Maßangabe darf KEIN Leerzeichen stehen.

Auswahl an Maßeiheiten:
| Kürzel       | Einheit                       |
| ------------ | ------------                  |
| px           | Pixel                         |
| %            | Prozent                       |
| em           | Vielfaches der Schriftgröße   |
| rem          | Vielfaches der Schriftgröße außgehend von der verwendeten Schriftgröße im "document root" |
| vw, vh       | viewport width, viewport height: prozentualer Anteil der Breite bzw. Höhe des Anzeigefensters (Viewport) |

(Die Einheiten: in, cm, mm, pt, pc und deg sind auch möglich, aber für uns aktuell nicht üblich, sondern in der Druckdarstellung relevant)

### em und rem

- können auch mit Dezimalstellen angegeben werden (z.B. `2.5rem`)
    - :exclamation: WICHTIG: Mit Punkt als Dezimaltrennzeichen

- em: bezieht sich immer auf die Schriftgröße des nächsthöheren Vorfahrenelements

- rem: funktioniert wie em, bezieht sich jedoch immer auf die Schriftgröße des document root (Dokumentstamm)


## Hyperlinks formatieren & Pseudoklassen

Hierfür gibt es spezielle Pseudoklassen. Diese werden mit einem Doppelpunkz an den Selektor angehängt (ohne Leerzeichen).

:exclamation: Die Reihenfolge muss eingehalten werden. Es brauch jedoch nicht jeder Linkzustand definiert werden.

- `a:link` -> noch nicht besuchte Seiten
- `a:visited` -> bereits besuchte Seiten
- `a:focus` -> mit der Tabulatortaste fokussiert
- `a:hover` -> Maus darüber
- `a:active` -> Maus gedrückt

Dies sind keine frei wählbaren Namen, sondern fest vorgegebene Schlüsselwörter.

### Pseudoklassen :focus und :hover
:exclamation: Die Pseudoklassen :focus und :hover gelten nicht nur für Hyperlinks


## Selektoren

### Klassen ansprechen

- der Selektor für eine Klasse beginnt mit einem Punkt

### IDs ansprechen

- der Selektor für eine Klasse beginnt mit einer #

### verknüpfen


```css
selector.class {eigenschaft: wert} 

selector .class {eigenschaft: wert} 

selector#id {eigenschaft: wert} 
```




## Browserspezifische Eigenschaften mit Herstellerpräfix

"Irgendwann haben die Browserhersteller damit begonnen, neue CSS-Eigenschaften oder -Werte zu unterstützen, die sich noch im experimentellen Stadium befinden, also noch bevor sie vom W3C offiziell verabschiedet worden sind. Um jedoch bereits im Vorfeld Konflikte zu vermeiden, die sich bei einer etwaigen Änderung der Spezifikationen seitens des W3C ergeben könnten, werden diese experimentellen Features als proprietäre, browserspezifische Features implementiert, die mit einem sogenannten Vendor Specific Prefix (Herstellerpräfix) versehen werden müssen." 

Per caniuse.com kann man überprüfen, welche Browser die Eigenschaften kennen.



