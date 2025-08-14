Működés leírása és a tetsz felépítése:
-----------------------------------------------


Eredetileg úgy épült fel a projekt, (2009-ben készítettem!) hogy létrehoztam túlírt lemezeket ismétlődő, de ellenőrizhetően változó adatokkal! (Ellenőrzés: CRC-MD5)

Ezek a fájlok tömörítve az ismétlődés miatt jelentős mértékben zsugorodtak le, így tömörített Fájl mérete töredéke az eredeti File méretnek!
2X3 MB-ból lesz egy túlírt DVD, és egy túlírt Cd kép File!
Ehhez a későbbiekben készíteni fogok Blu Ray lemezképet is, de egyelőre Cd és DVD van, tehát azokra addig (csak) azok tesztelésére alkalmas.


Story:
Használt számítástechnikával foglalkozó időm java része az alkatrészek tesztelésével telt.
Eközben keletkezett olyan igény, mellyel az optikai meghajtókat lehet letesztelni, hogy megbízható-e, el lehet-e adni.
Mivel akkorriban egy teszt sem volt erre a feladatra kielégítő, így kialakítottam a sajátomat, és most ezt osztom meg.


------> Megjegyzés: Mivel a meghajtók árai igen lementek, már üzletileg nem éri meg tesztelni, mert többe kerül a teszt elvégzésének munka óradíja,
mint amennyi egy új meghajtó, de bizonyos esetekben meg lehet vele találni a hiba valódi okát! (Pl: hibás telepítések oka lehet!!!)
Természetesen saját magának otthon az ember le tudja tesztelni, az nem kerül pénzbe! <------



Optikai meghajtók lehetséges hibaforrásai:
----------------------------------------------------

- Olvasó fej,
- Fejmozgató motor,
- korong mozgató motor,
- Cache (Ideiglenes tár.)

A legjellemzőbbek ezek. Persze sokkal többrétű, de szempontunkból a többi most mellékes, tesztelni ezeket szeretnénk.
Ha ezeken hiba nélkül átmegy, akkor nincsen meghibásodás a meghajtóban, ha bármi gondja van a meghajtónak, valahol elvérzik ezeken a teszteken...



Az elv, a következő:
----------------------------------------

Minden Optikai meghajtónál el kell végezni az összes alapvető funkciójának az elemzését.
Ezek a következőek:

* Az adatokat hibamentesen olvassa-e: Erre van az elkészített Teszt DVD - Cd Párosom! A korongok minimális túlírással készültek, tehát teljesen tele vannak.
  Ezt minden hibamentes meghajtónak végig kell tudnia olvasni! TotalCommander (Régi WinCommander is jó!) kell a használatához,
  ott a korong tartalmából a "DVD_Ellenozes.md5" nevű/kiterjesztésű, és a "Cd_Ellenozes.md5" nevű/kiterjesztésű Fájlt kell használni!
  Enterrel elindítva azonnal nekiáll a tesztelésnek! A legminimálisabb bit hibát is jelzi! Tehát nem csak a byte-okat, hanem már a biteket is! (Ugyebár 8 bit = 1 byte)
  Fontos, hogy a DVD, és a CD Teszteket külön-külön el kell végezni, mert olvashatja az egyiket, és nem a másikat. Bizonyosság csak mindkét korong végigfuttatásával lesz!
  (Mellékelt Képek: 001.jpg - 002.jpg)
  A hibát okozhatja a karcos DVD/Cd, az olvasófej hibája, piszkossága is!

* Az olvasás sebessége egyenletes, vagy változó: (Ha bizonyos futó processek nem kapnak időben adatot, akkor leállnak. Pl.: Telepítések.
  Ugyanakkor a DVD - Cd tartalma maradéktalanul felmásolható a HDD-re.) Erre használjuk a Nero Speed Tesztjét, vagy a DVD/Cd Infó nevezetű program Speed-Tesztjét.
  Minden esetben az Adott Teszt korongot használjuk, mert az tele van írva, és csak ez fogja kimozgatni az olvasó fejet a korong végéig!!!
  (Mellékelt Képek: 003.jpg - Nero Speed Teszt. Mint látható"EKG"-t rajzol tehát gond van. Bár jelen esetben ez a karcos korong miatt volt! DVD/Cd Infó-ról most nincsen Kép)
  Itt a hiba lehet a karcos DVD/Cd-, a Cache-, az Olvasófej hibája is!

* Az adott eszköz tud-e Boot-olni!? Itt szintén külön-külön ki kell próbálni, hogy bootol-e DVD-ről, és Bootol-e Cd-ről!


Továbbá Író esetén:
* Az írás hibátlan-e, (Itt szintén külön meg lehet próbálni az Újraírható korongokkal, mert az egyiket írhatja attól, hogy a másikat nem!) és itt emelném ki,
  hogy ha látszólag megírta, attól az adat még lehet olvashatatlan! Erre megoldás a Nero adat-visszaellenőrzés pipája (Írás közben válik bekapcsolhatóvá!
  Ez minden egyes bitet leellenőriz, hogy ugyanaz-e, mint a Forrás médián!!! Csak ez ad 100%-os garanciát a hibátlan írásra!!!)




Mint a fentiekből kitűnik, nagyon fontos, hogy a Teszt korongok teljesen karcmentesek legyenek!!! Csak így adnak valós eredményt, ráadásul nem árt jobb minőségű korongokra dolgozni...
Régebben ezt ajánlottam: "A CD Teszt korongot Neró-val (.nrg) tudod kiírni, a DVD Teszt korongját PowerIso-val (.daa) tudod kiírni."
Most utána fogok nézni, hogy milyen megoldás lehet jó, de figyelembe kell venni, hogy az ajánlás oka az enyhén túlírt korong (Az alapos teszt végett erre szükség is van!),
amire nem minden író program képes!!!


A Teszt folyamatos fejlesztés alatt van! Minden ötletet/segítséget szívesen fogadok!

Tervben van, hogy Operációs rendszer nélkül is, és rendszer alól is (Valószínűleg a mellékelt Live!) lefusson majd-minden Teszt.
Ezek röviden:
- boot képesség,
- sebességet mérés,
- Hibás olvasás detektálása: md5-öt ellenőrzés!
- puffer számolása és tesztelése,
- A túlírás azért szükséges, mert így a fejmozgató elektronika hibája is kiderül! Amennyiben nem tudja a szélére is kimozgatni a fejet az olvasó,
  akkor mechanikai, vagy elektronikai hiba valószínű, amit ez a teszt így kimutat.



Későbbi tervek:
- Gyorsított teszt: Véletlenszerű fájl olvasás össze-vissza, nem a teljes tartalom beolvasáa. boot szekció olvasása md5-tel! A fej kimozgatáa a szélére, puffer írás-olvasás, stb.
- menüből boot olvasás teszt, nem szükséges újraindítani a boot teszthez!
- menüből Flash/FW lekérdezése és kiírása, (Később akár automatizált frissítés keresés is!)
- Beépített író szoftver (Nagyon esetleges...)


Kérdésekkel/ötletekkel lehet keresni!


.
