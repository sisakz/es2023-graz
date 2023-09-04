# Bemutató összefoglaló

## Alapsztori

Van egy cégünk, amely háromféle AI API-t kínál:

- **Chatbot**
- **Képgeneráló**
- **Képfelismerő**

---

## A Modul

### Feladatok

1. **Bemutatkozó oldal**
2. **AI Szolgáltatások bemutatása**
3. **Team oldal**
4. **Árak oldal**

> Megjegyzés: Adnak szövegeket és képeket (asseteket), de a dizájnt a versenyzőknek kell elkészíteni.

---

## B Modul

### Feladatok

1. **Login oldal** _(semmi extra)_
2. **Token generálás és visszavonás** - Oldal, ahol az egyes szolgáltatásokhoz lehet tokeneket generálni és visszavonni (X-API-TOKEN), illetve limitációkat beállítani. **A token csak először látszik**, később már nem lehet megjeleníteni (csak visszavonni.)
3. **Számlázás oldal** - Oldal, ahol a felhasználó aktuális számláját lehet megtekinteni.
4. Adnak CSV-t, ami nem normalizát, ezt kell bevarázsolni az adatbázisba. Az adatbázis design-ra is lesznek pontok.


---

## C Modul

### Feladatok

- Beintegrálni a három, már kész AI szolgáltatást.
- Az autentikáció a felhasználó számára szükséges.
- Szolgáltatásonként különböző módszerrel kell adatot gyűjteni a számlázáshoz.
- adnak 

> Megjegyzés: A képgeneráló tűnt a legbonyolultabbnak.

### API-k, amit adnak
- Természetesen nem lesz valós AI mögötte, csak valami fake system.
- **Lesz olyan API, ami nem működik tökéletesen, ez valahogy le lesz dokumentálva, a commercial API-ban valami workaround-dal javítani kell a funkciót. Állítólag nem nagyon bonyolult case.**
- Adnak db dumpot, ezzel működik majd az ő API-juk. A db kiegészíthető az adott db részek módosítása nélkül (gondolom pl. a tokenekhez, meg a számlázáshoz), azaz a versenyzői backend is használja a db-t. 


#### Chatbot API
Erről nem sok maradt meg, hogy ez mit tud, de remélhetőleg semmi extra. A részletek valószínűleg itt is az OpenAPI yml-ből fognak kiderülni.

#### Képgenerálő API
Itt van több fázis. Először az API generál egy preview-t, amit fade effecttel kell megjeleníteni, utáni pollozni kell a státuszt, ha jól emlékszem 2 percenként, és a progrest is meg kell jeleníteni, hogy hány százalékon áll a generálás.

#### Képfelismerő API
Képet kell tudni elpostolni, az API json-ban visszaadja, hogy milyen tárgyakat ismert fel a képen.

## D Modul
4 lapból álló webapp-ot kell összerakni a C modul commercial API-jaira épülően:
1. **Nyitóoldal**: itt ki lehet választani a három szolgáltatás közül valamelyiket (valami dashboard-szerű dolog)
2. **Chatbot page**: valami egyszerű UI a chatbothoz

3. **Képgeneráló page**: a preview-t fade effecttel kell megjeleníteni, utáni pollozni kell a státuszt, ha jól emlékszem 2 percenként, és a progrest is meg kell jeleníteni, hogy hány százalékon áll a generálás.
4. **Képfelismerő page**: képfeltölő felület + a visszaadott tárgyak megjelenítése

## E Modul
### Testing
Itt semmi extra nem derült ki. Adnak valami JS kódot, szerintem nem biztos, hogy köze lesz az előző modulokhoz. Full coverage kell és a mutationon el kell failelnie. Az nem derült ki, hogy adnak-e esetleg mutationt is.
### PWA
- Valami egyzerű backendről lehet fetcheni article-ket és ezeket kell majd megjeleníteni. Ha jól emlékszem csak az első 10-et. 
- Lehessen telepíteni
- Cache-elje, amit lefetchelt
- Pollozza a backendet, és ha van új article, akkor azt notification-ben kell megjeleníteni :)
### Web Component
Három különböző komponenst kell legyártani
1. egy modal néhány proppal (title, text, button). A button click kivált egy eseményt
2. Egy szövegdoboz, ami limitált mennyiségű karakter bevitelére szolgál. Propként megadható, hogy mennyi a limit. A doboz alatt van egy számláló, ami mutatja, hogy hány karakter van még hátra. Ha 10(?)-nál kevesebb van hátra, akkor pirosra vált. Ha jól emlékszem le mehet mínuszba is.
3. Talán egy countdown volt a harmadik, aminek egy dátumot lehetett beadnim de ez valahogy kiesett. De bármi is volt, nem tűnt különösebben veszélyesnek. :)

## Infrastruktúra
Lesz helyi npm cache, az összes itteni modul szabadon telepíthető.



