# Value by Alpha Maps in QGIS

## Datenquelle (Wahlgeometrien & Wahlergebnisse)
[Bundestagswahl 2021](https://www.bundeswahlleiterin.de/bundestagswahlen/2021/ergebnisse/opendata.html)

Tabelle (kerg.csv) mit Wahlergebnissen bereinigen

![image](https://github.com/s91581/DTM/assets/134683755/f62eaf44-d151-4c8c-90a6-a6a1b32ea20d)

in QGIS

1.) Vergleich SPD vs CDU: Stimmenstärkere Partei regelbasiert darstellen

Regel "Olaf"
```
"SPD > "CDU"
```
Regel "Armin"
```
"SPD > "CDU"
```

2.) Ebene "Alpha" ergänzen und auf Symbolebene 1 setzen

![image](https://github.com/s91581/DTM/assets/134683755/4d8daff3-38a9-4043-a089-7917bc0dec8d)

3.) Regel für Ebene "Alpha": über "Einfache Füllung" unter "Füllfarbe" > "Datendefinierte Übersteuerung" > "Bearbeiten" 

![image](https://github.com/s91581/DTM/assets/134683755/edc09e99-bb38-4ff1-9f3c-efea337607be)

"Grundprinzip":
```
set_color_part(
 'black',
 'alpha',
 126)
```

Statt eines festen Alpha-Wertes, werden diese wertebasiert auf einem anderen Attribut für jede Bezugseinheit berechnet
```
set_color_part(
 'black',
 'alpha',
scale_linear( 
  "BTW_G",
  100000, 200000,
  230, 0)
 )
 ```
