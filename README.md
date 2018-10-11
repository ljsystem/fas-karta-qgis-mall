# FAS Karta QGIS-mall

## Filer

* **Namngivning**
	* **Projektfilen**
		* Namnet på filen får endast innehålla bokstäverna **a-z**, **_** samt **-**.
		* Namnet måste vara i gemener.
		* Namnet bör vara den aktuella kyrkogårdens namn minus ordet "kyrkogård".
	* **Lagerfiler** (shape-filer)
		* Namnet på filen får endast innehålla bokstäverna **a-z**, **_** samt **-**.
* **Filstruktur**
	* Projektets lagerfiler (shape-filer) ska placeras i en mapp som heter `SHP`.
	* Mappen `SHP` ska ligga på samma nivå som projektfilen.
* **Ortofoto** För att FAS Karta ska kunna visa ett ortofoto så måste det importeras som antingen `.tiff` eller `.jpg` _(ej testat)_.

_Exempel: Kyrkbyns kyrkogård_

```
.
├── kyrkbyn.qgs
└── kyrkbyn.qgs~
    ├── Trad.dbf
    ├── Trad.prj
    ├── Trad.qpj
    ├── Trad.shp
    ├── Trad.shx
    ├── Yttergravhack.dbf
    ├── Yttergravhack.prj
    ├── Yttergravhack.qpj
    ├── Yttergravhack.shp
    └── Yttergravhack.shx
```

## Projektet

* **Referenskoordinatsystem**
	* **Projektet** Projektets referenskoordinatsystem ska vara **EPSG:3857** (WGS 84 / Pseudo Mercator)
	* **Lager** Importerade lager kan vara något av följande referenskoordinatsystem:
		* **EPSG:3857** (WGS 84 / Pseudo Mercator)
		* **EPSG:3006** (SWEREF99 TM)
		* **EPSG:3008** (SWEREF99 13 30)
* **Lager**
	* **Namngivning**
		* **"Svenska tecken"** Till skillnad från filnamnet på lagerfilerna där det inte är tillåtet att använda andara bokstäver än a-z så är det fullt tillåtet att namnge lagerna i projektet med "svenska tecken".
			* _Exempel: Träd, Yttergravhäck_
		* **Ortofoto** Om projektet innehåller ett ortofoto så måste detta heta exakt "Ortofoto". _Annars kan inte FAS Karta identifiera lagret och presentera det korrekt._
* **OWS-server** Följande inställningar måste vara gjorda i projektegenskaperna under fliken "OWS-server":
	* **Egenskaper för tjänst** Behöver endast vara ikryssat. Ingen vidare information behöver fyllas i.
	* **WMS-egenskaper**
		* **Utanonnsera utsträckning** Denna utsträckning används av FAS Karta för att initialt zooma in på rätt ställe när kartan öppnas. Använd med fördel knappen "Används kartfönstrets nuvarande utsträckning" för att ställa in rimliga värden.
		* **Referenskoordinatsystemsbegränsning** Skall endast innehålla **EPSG:3857** i listan.
	* **WFS-kapacitet** Alla importerade lager (förutom ev. ortofoto) ska publiceras som WFS. "Uppdatera", "Lägg till" och "Ta bort" behövs ej.
		