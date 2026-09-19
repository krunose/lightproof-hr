# Jednostavna računalna provjera pravopisa i gramatike hrvatskoga jezika LightProofom

> [!WARNING]
> **OVISNOST O RJEČNIKU (Inačica 0.5.5.9):** 
> Ovaj dodatak više NE RADI na bazi čistog teksta. Pravila se pokreću isključivo ako vaš LibreOffice koristi tagirani hrvatski rječnik. Prije instalacije ovog dodatka, obavezno osvježite svoj Hunspell rječnik datotekama iz repozitorija [hunspell-hr](https://github.com).

LightProof je računalni alat ugrađen u LibreOffice i služi za računalnu provjeru gramatike, pravopisa i stila. Dobra je dopuna Hunspellu jer dok potonji provjerava riječi isključivo u izolaciji, LightProof nudi ograničenu mogućnost provjeravanja okoline i konteksta. Temelji se na pravilnim izrazima (engl. regular expressions) i ne razumije duboku semantičku i gramatičku strukturu rečenice, pa određene pravopisno-gramatičke pa i stilske probleme njime nije jednostavno ili nije uopće mguće riješiti, recimo pisanje zareza u hrvatskome jeziku.

Ovaj repozitorij sadrži dodatak (`OXT datoteka`) koji omogućuje brzu i jednostavnu integraciju pravila za provjeru gramatike, pravopisa i stila (`hr.dat`) u LibreOffice Writer.

Ambicija ovoga projekta nije napraviti sveobuhvatnu provjeru pravopisa i gramatike jer to s obzirom na vrijeme, ljudstvo, ovaj alat, ali i druge alate koji su nam na raspolaganju (rječnik nije označen) jednostavno nije moguće. Ovo je samo mala (pri)pomoć svakome tko je želi. Nešto čemu ne treba bezrezervno vjerovati, ali će (možda) ipak nekome biti od koristi; dakle samo pripomoć rječniku za provjeru pravopisa. Pitanja, komentare i prijedloge možete ostaviti na [ask.libreoffice.org](https://ask.libreoffice.org/t/provjera-gramatike-tipografije-i-stila-lightproofom-za-hrvatski-jezik/137656).

## Instalacija i pokretanje

Dodatak je pripremljen kao **OXT datoteka** i spreman je za instalaciju na svim operacijskim sustavima koji podržavaju LibreOffice (v4.0 ili noviji).

1. Preuzmite dodatak s platforme [LibreOffice Extensions](https://extensions.libreoffice.org/en) ili izravno sa [GitHub repozitorija](https://github.com/krunose/lightproof-hr).
2. Instalirajte dodatak dvoklikom na datoteku.
3. Ponovno pokrenite LibreOffice.

Trenutačno najnovija inačica dodatka nije u službenom LibreOfficeovu repozitoriju dodataka jer **da bi dodatak od inačice 0.5 nadalje radio kako je zamišljeno, potrebno je preuzeti (djelomično) označen Hunspellov rječnik za hrvatski jezik s [github.com/krunose/hunspell-hr](https://github.com/krunose/hunspell-hr)!** Onaj Hunspellov rječnik koji *već imate na računalu* nije označen i dodatak od inačice 0.5 (uključujući i nju) neće raditi.

### Instalacija Hunspellovog rječnika

1. preuzmite datoteke `hr_HR.dic` i `hr_HR.aff` s ponuđenoga mrežnoga mjesta
2. smjestite ih u mapu
    - `/usr/share/hunspell` koristite li GNU/Linux
    - `C:\Program Files\LibreOffice\share\extensions\` i pronađite mapu s jezičnim paketima i u njih smjestite ov dvije datoteke.
3. ponovno pokrenite LibreOffice


## Kako ova pravila pokušavaju pomoći

1. Ispraviti probleme u pisanju infinitiva u futuru I.
2. Sastavljeno i nesastavljeno pisanje
3. Upozoriti na konstrukciju 'da li'
4. Donekle razlikovati 'slijedeći' i 'sljedeći'
5. Pomoći oko pleonazama
6. Ispravak pisanja 's/sa' i 'k/ka'
7. Kondicional: mi bi > mi bismo
8. Klasični tipfeleri


## Za one koji žele znati više

### Postupak pripreme i izrada dodatka za LibreOffice

Problem je s alatom iz repozitorija [github.com/karelin/lightproof](https://github.com/karelin/lightproof) to što se dodatak nije mogao napraviti jer je skripta `make.py` izvorno napisana za `Python 2`. Zbog promjena (nekih) parametara u Pythonu 3, skriptu sam uspješno prilagodio i modernizirao pomoću AI-a, koji je ujedno pomogao generirati i `hr.cfg` datoteku. Dakle tko želi raditi pravila i treba ih kompajlirati zbog testa, mora preuzeti `make.py` iz **ovoga repozitorija**, odnosno treba mu `lightproof.zip`. Više o tome u sljedećm dijelu.

### Kako samostalno kompajlirati dodatak
1. Klonirajte repozitorij s [karelin/lightproof](https://github.com).
2. Zamijenite skriptu `make.py` onom koja se nalazi u [mojem repozitoriju](https://github.com/krunose/lightproof-hr).
3. Dodajte mapu `lightproof/src/hr/`.
4. U nju smjestite vlastite datoteke `hr.dat` i `hr.cfg`.
5. Iz korijenske mape `lightproof` pokrenite skriptu naredbom:

   ```bash
   python3 make.py src/hr/hr.cfg
   ```
6. Spreman dodatak u `.oxt` datotečnom formatu bit će generiran unutar mape `~/lightproof/`.

---
**Autor:** Krunoslav Šebetić (2026.)

**Licenca:** MPL 2.0 / LGPLv3 (Otvoreni kod kompatibilan s LibreOffice ekosustavom)

