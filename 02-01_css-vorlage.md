# CSS "VORLAGE"

```css

@charset UFT-8;



html {
    font-size: 100%;
}

body {
    font-family: Helvetica, Arial, sans-serif;
    font-size: 1em;
    color: #000;
    background-color: #ded7d4;
}
```


## Überschriften
```css
h1, h2, h3, h4 {
    font-weight: bold;
}

h1 {
    font-size: 1.5rem;
}

h2 {
    font-size: 1.25rem;
}

h3 {
    font-size: 1.15rem;
}

h4 {
    font-size: 1rem;
}
```


## Darstellung von strong, b, em und i definieren

Diese werden zwar in den meisten Browsern bereits fett bzw. kursiv dargestellt, zur Sicherheit kann man dies nochmals explizit angeben:
```css
strong, b {
    font-weight: bold;
}

em, i {
    font-style: italic;
}
```

