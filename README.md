# FAS Karta QGIS-mall

## Filer

* **Namngivning**
	* **Projektfilen**
		* Namnet på filen får endast innehålla bokstäverna **a-z**, **_** samt **-**.
		* Namnet måste vara i gemener.
		* Namnet bör vara den aktuella kyrkogårdens namn minus ordet "kyrkogård".
	* **Lagerfiler** (shape-filer)
		* Namnet på filen får endast innehålla bokstäverna **a-z**, **_** samt **-**.
	* **Lager**
		* **Ortofoto** Har kartan ett Ortofoto måste detta lagret heta just `Ortofoto` för att FAS Karta ska kunna identifiera lagret som ett bakgrundslager.
* **Filstruktur**
	* Projektets lagerfiler (shape-filer) ska placeras i en mapp som heter `SHP`.
	* Mappen `SHP` ska ligga på samma nivå som projektfilen.
* **Ortofoto** För att FAS Karta ska kunna visa ett ortofoto så måste det importeras som antingen `.tiff` eller `.jpg` _(ej testat)_.
* **print** Mappen `print` måste finnas med i filstrukturen och ska innehålla filerna `fas-logo.svg` samt `north.svg`.

_Exempel: Kyrkbyns kyrkogård_

```
.
├── print
│   ├── fas-logo.svg
│   └── north.svg
├── SHP
│   │   ...
│   ├── Trad.dbf
│   ├── Trad.prj
│   ├── Trad.qpj
│   ├── Trad.shp
│   ├── Trad.shx
│   │   ...
│   ├── Trad.shx
│   ├── Yttergravhack.dbf
│   ├── Yttergravhack.prj
│   ├── Yttergravhack.qpj
│   ├── Yttergravhack.shp
│   └── Yttergravhack.shx
│       ...
├── kyrkbyn.qgs
└── kyrkbyn.qgs~
```

## Projektet

* **Variabler** Projektet ska ha följande variabler som används vid utskrift:
	* `parish` Detta fältet ska innehålla församlings/pastoratets namn.
		* _Exempel: Kyrkbyns församling_
	* `cemetery` Detta fältet ska innehålla kyrkogårdens namn.
		* _Exempel: Kyrkbyns kyrkogård_
* **Referenskoordinatsystem**
	* **Projektet** Projektets referenskoordinatsystem ska vara **EPSG:3857** (WGS 84 / Pseudo Mercator)
	* **Lager** Importerade lager kan vara något av följande referenskoordinatsystem:
		* **EPSG:3857** (WGS 84 / Pseudo Mercator)
		* **EPSG:3006** (SWEREF99 TM)
		* **EPSG:3007** (SWEREF99 12 00)
		* **EPSG:3008** (SWEREF99 13 30)
		* **EPSG:3009** (SWEREF99 15 00)
		* **EPSG:3010** (SWEREF99 16 30)
		* **EPSG:3011** (SWEREF99 18 00)
		* **EPSG:3012** (SWEREF99 14 15)
		* **EPSG:3013** (SWEREF99 15 45)
		* **EPSG:3014** (SWEREF99 17 15)
		* **EPSG:3015** (SWEREF99 18 45)
		* **EPSG:3016** (SWEREF99 20 15)
		* **EPSG:3017** (SWEREF99 21 45)
		* **EPSG:3018** (SWEREF99 23 15)
* **Lager**
	* **Namngivning**
		* **"Svenska tecken"** Till skillnad från filnamnet på lagerfilerna där det inte är tillåtet att använda andara bokstäver än a-z så är det fullt tillåtet att namnge lagerna i projektet med "svenska tecken".
			* _Exempel: Träd, Yttergravhäck_
		* **Grav** Lagret där gravar/gravplatser ritas in ska heta `Grav`. Lagret ska även använda sig av etikettstilen `Grav.gml`som styr etikettens utseende vid utskrift.
			* **Fält** Lagret `Grav` ska dessutom har följande fält:
				* `label` Detta är den text som kommer användas som etikett. _Bör bara gravens nummer eller gravplatsens namn._
				* `g_id` Gravens unika numeriska ID från FAS Kyrkogård. _Ej samma som gravens nummer!_
				* `gg_id` Gravplatsens unika numeriska ID från FAS Kyrkogård. _Ej samma som gravplatsens namn!_ 
		* **Ortofoto** Om projektet innehåller ett ortofoto så måste detta heta exakt `Ortofoto`. _Annars kan inte FAS Karta identifiera lagret och presentera det korrekt._
* **OWS-server** Följande inställningar måste vara gjorda i projektegenskaperna under fliken "OWS-server":
	* **Egenskaper för tjänst** Behöver endast vara ikryssat. Ingen vidare information behöver fyllas i.
	* **WMS-egenskaper**
		* **Referenskoordinatsystemsbegränsning** Skall endast innehålla **EPSG:3857** i listan.
	* **WFS-kapacitet** Alla importerade lager (förutom ev. ortofoto) ska publiceras som WFS. `Uppdatera`, `Lägg till` och `Ta bort` behövs ej.
		