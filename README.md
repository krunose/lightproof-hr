# Jednostavna računalna provjera gramatike, pravopisa, tipografije i stila za hrvatski jezik LightProofom

> [!WARNING]
> **OVISNOST O NOVOM RJEČNIKU ZA PROVJERU PRAVOPISA:**
> Ovaj dodatak za pravilno funkcioniranje traži označeni rječnik. Uspjelo se označiti (POS tag) infinitive u Hunspellovu rječniku. Pravilo od inačice 0.5.5.9 radi isključivo ako LibreOffice koristi označen rječnik. Prije instalacije ovoga dodatka instalirajte dodatak s (djelomično) [označenim rječnikom za računalnu provjeru riječi](https://extensions.libreoffice.org/en/extensions/show/99660) iz LibreOfficeova službena [repozitorija dodatcima](https://extensions.libreoffice.org/en/extensions/show/99660). Ponovno pokrenite LibreOffice, također i u sistemskoj traci ako je aktivno (Windows). Primam pitanja i pružam pomoć na [ask.libreoffice.org Hrvatski](https://ask.libreoffice.org/c/croatian/15).

---

LightProof je računalni alat ugrađen u LibreOffice i služi za računalnu provjeru gramatike, tipografije i stila. Dobra je dopuna Hunspellu jer dok potonji provjerava riječi isključivo u izolaciji, LightProof nudi ograničenu mogućnost provjeravanja okoline i konteksta. Temelji se na pravilnim izrazima (engl. <i>regular expressions</i>) i ne razumije duboku semantičku i gramatičku strukturu rečenice, pa određene pravopisno-gramatičke pa i stilske probleme njime nije jednostavno ili nije uopće moguće riješiti; recimo pisanje zareza u hrvatskome jeziku.

Ovaj repozitorij sadrži dodatak (`OXT datoteka`) koji omogućuje brzu i jednostavnu integraciju pravila za provjeru gramatike, pravopisa i stila (`hr.dat`) u LibreOffice Writer.

Ambicija ovoga projekta nije napraviti sveobuhvatnu provjeru pravopisa i gramatike jer to je s obzirom na vrijeme, ljudstvo, ovaj alat, ali i na ostalo što nam jest ili nije na raspolaganju (rječnik nije označen) jednostavno nemoguće. Ovo je samo mala (pri)pomoć svakome tko je želi. Nešto čemu ne treba bezrezervno vjerovati, ali će (možda) ipak biti od koristi (hrvatski bolje nema); dakle samo pripomoć rječniku za provjeru pravopisa.

## Instalacija i pokretanje

Dodatak je pripremljen kao **OXT datoteka** i spreman je za instalaciju na svim operacijskim sustavima koji podržavaju LibreOffice (v4.0 ili noviji).

Ako bi tko želio testirati ova pravila, potrebno je:

* Obrisati stari rječnik ako je instaliran kao dodatak
	* pomoću `Upravitelja dodatcima` tako što se otvara izbornik `Tools` → `Extensions...` te se odabere se dodatak s rječnikom i zatim klikne `Remove`. Odabirom `Close` u dijaloškom okviru `Upravitelja dodatcima` ponovno se pokreće LibreOffice odabirom `Restart Now`.
* Instalirati novi dodatak s označenim rječnikom
	* preuzimanjem iz [službenoga repozitorija dodataka LibreOfficea](https://extensions.libreoffice.org/en/extensions/show/99660) klikom na zeleni gumb `Download`. Zatim se odlazi u `Tools` → `Extensions...` i klikne se na `Add`. Odabere se ododatak s rječnikom. Klikne se na `Close` i odabere se `Restart Now`.
* Preuzima se dodatak s [pravilima za provjeru gramatike](https://extensions.libreoffice.org/en/extensions/show/99654) i instalira se prema uputama iz prethodnoga koraka.

Ako ste slijedili upute i pazili na redoslijed. Pravila za provjeru gramatike moraju raditi.

### Instalacija Hunspellovog rječnika podmetanjem rječničkih datoteka (ne kao OXT)

1. [preuzmite datoteke](https://github.com/krunose/hunspell-hr) `hr_HR.dic` i `hr_HR.aff`
2. smjestite ih u mapu
    - `/usr/share/hunspell` koristite li GNU/Linux
    - `C:\Users\VAŠE_KORISNIČKO_IME\AppData\Roaming\LibreOffice\4\user\wordbook\` i pronađite mapu s jezičnim paketima i u njih smjestite ove dvije datoteke.
    - na macOS-u su to datoteke `~/Library/Application Support/LibreOffice/4/user/wordbook/` za aktivnu instalaciju LibreOfficea ili `~/Library/Spelling/` za provjeru na razini cijeloga sustava (sve aplikacije)
3. ponovno pokrenite LibreOffice

## Kako ova pravila pokušavaju pomoći

* Ispravak krnjega infinitiva u futuru I. i konstrukcijama s modalnim glagolima
* Uklanjanje suvišne zamjenice "si" u futuru
* Kontrola infinitiva u niječnom povratnom futuru
* Upozorenje na konstrukciju "da li"
* Uklanjanje konstrukcije prijedlog + infinitiv
* Bezlični oblik glagola "trebati" ispred infinitiva
* Zabrana vremenskoga značenja prijedloga "kroz"
* Razlikovanje pridjeva "sljedeći" i priloga "slijedeći"
* Detekcija dupliranja riječi
* Pravilna zamjena i naveza prijedloga "s/sa" i "k/ka"
* Ispravak velikoga početnog slova u malom unutar rečenice
* Spajanje rastavljenih oblika kondicionala (bismo/biste)
* Uklanjanje pleonazama, stilskih viškova i pogrešnih parova veznika
* Uklanjanje suvišnoga "je" uz povratnu zamjenicu "se"
* Sintaksička kontrola navodnika, zagrada, interpunkcije i neprekidajućih razmaka (NBSP)
* I još ponešto, da se ne nabraja...

## Za one koji žele znati više

### Postupak pripreme i izrada dodatka za LibreOffice

Problem je s alatom iz repozitorija [github.com/karelin/lightproof](https://github.com/karelin/lightproof) to što se dodatak nije mogao napraviti jer je skripta `make.py` izvorno napisana za `Python 2`. Zbog promjena (nekih) parametara u Pythonu 3, skriptu sam uspješno prilagodio i modernizirao pomoću AI-a, koji je ujedno pomogao generirati i `hr.cfg` datoteku. Dakle tko želi raditi pravila i treba ih kompajlirati zbog testa, mora preuzeti `make.py` iz **ovoga repozitorija**, odnosno treba mu `lightproof.zip`. Više o tome u sljedećem dijelu.

### Kako samostalno kompajlirati dodatak
1. Klonirajte repozitorij s [karelin/lightproof](https://github.com).
2. Zamijenite skriptu `make.py` onom koja se nalazi u [ovom repozitoriju](https://github.com/krunose/lightproof-hr).
3. Dodajte mapu `lightproof/src/hr/`.
4. U nju smjestite vlastite datoteke `hr.dat` i `hr.cfg`.
5. Iz korijenske mape `lightproof` pokrenite skriptu naredbom:

   ```bash
   python3 make.py src/hr/hr.cfg
   ```
6. Spreman dodatak u `.oxt` datotečnom formatu bit će generiran unutar mape `~/lightproof/`.

---

Složena pravila i dio „Kako ova pravila pokušavaju pomoći” pisana su uz pomoć umjetne inteligencije kako bi se uštedjelo vrijeme.

---
**Autor:** Krunoslav Šebetić (2026.)

**Licenca:** MPL 2.0 / LGPLv3 (Otvoreni kod kompatibilan s LibreOffice ekosustavom)

