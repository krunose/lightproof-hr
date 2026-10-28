# Jednostavna računalna provjera gramatike, pravopisa, tipografije i stila za hrvatski jezik LightProofom

> [!WARNING]
> **OVISNOST O NOVOM RJEČNIKU ZA PROVJERU PRAVOPISA:** 
> Ovaj dodatak **više ne radi** na principu čistih pravilnih izraza (regexp). Uspjelo se označiti (POS tag) infinitive u Hunspellovu rječniku. Pravila će od **inačice 0.5.5.9** raditi isključivo ako vaš LibreOffice koristi tagiran hrvatski rječnik. **Prije instalacije ovog dodatka**, obavezno izbrišite stari dodatak s rječnikom za provjeru pravopisa i instalirajte [dodatak s tagiranim rječnikom](https://extensions.libreoffice.org/en/extensions/show/99660) ~iz repozitorija [hunspell-hr](https://github.com)~. Ponovno pokrenite LibreOffice, također i u sistemskoj traci ako je aktivan (Windows). Primam pitanja i pružam pomoć na [ask.libreoffice.org Hrvatski](https://ask.libreoffice.org/c/croatian/15)

---

LightProof je računalni alat ugrađen u LibreOffice i služi za računalnu provjeru gramatike, pravopisa i stila. Dobra je dopuna Hunspellu jer dok potonji provjerava riječi isključivo u izolaciji, LightProof nudi ograničenu mogućnost provjeravanja okoline i konteksta. Temelji se na pravilnim izrazima (engl. regular expressions) i ne razumije duboku semantičku i gramatičku strukturu rečenice, pa određene pravopisno-gramatičke pa i stilske probleme njime nije jednostavno ili nije uopće moguće riješiti, recimo pisanje zareza u hrvatskome jeziku.

Ovaj repozitorij sadrži dodatak (`OXT datoteka`) koji omogućuje brzu i jednostavnu integraciju pravila za provjeru gramatike, pravopisa i stila (`hr.dat`) u LibreOffice Writer.

Ambicija ovoga projekta nije napraviti sveobuhvatnu provjeru pravopisa i gramatike jer to s obzirom na vrijeme, ljudstvo, ovaj alat, ali i na ostalo što nam je na raspolaganju (rječnik nije označen) jednostavno nije moguće. Ovo je samo mala (pri)pomoć svakome tko je želi. Nešto čemu ne treba bezrezervno vjerovati, ali će (možda) ipak biti od koristi (hrvatski bolje nema); dakle samo pripomoć rječniku za provjeru pravopisa. Pitanja, komentare i prijedloge možete ostaviti na [ask.libreoffice.org](https://ask.libreoffice.org/t/provjera-gramatike-tipografije-i-stila-lightproofom-za-hrvatski-jezik/137656).

## Instalacija i pokretanje

Dodatak je pripremljen kao **OXT datoteka** i spreman je za instalaciju na svim operacijskim sustavima koji podržavaju LibreOffice (v4.0 ili noviji).

1. Izbrišite dodatak s rječnikom za računalnu provjeru pravopisa hrvatskoga jezika koji sada imate. Ponovno pokrenite LibreOffice.
2. Preuzmite i dvoklikom instalirajte rječnik [`Hunspell-hr-v2.1-20260921.oxt`](https://github.com/krunose/hunspell-hr/tree/master/tools) s GitHuba; ili ga potražite na [`extensions.libreoffice.org`](https://extensions.libreoffice.org/). Ponovno pokrenite LibreOffice.
3. Preuzmite odavde dodatak [`Lightproof_hr-0.5.5.29.oxt`](https://github.com/krunose/lightproof-hr/blob/main/Lightproof_hr-0.5.5.29.oxt) i instalirajte dvoklikom. Ponovno pokrenite LibreOffice.

Ako ste slijedili upute i pazili na redoslijed. Pravila za provjeru gramatike moraju raditi.

Trenutačno najnovija inačica dodatka nije u službenom LibreOfficeovu repozitoriju dodataka jer **da bi dodatak od inačice 0.5 nadalje radio kako je zamišljeno, potrebno je preuzeti (djelomično) označen Hunspellov rječnik za hrvatski jezik s [github.com/krunose/hunspell-hr](https://github.com/krunose/hunspell-hr)!** Onaj Hunspellov rječnik koji *već imate na računalu* nije označen i dodatak od inačice 0.5 (uključujući i nju) neće raditi.

### Instalacija Hunspellovog rječnika

1. preuzmite datoteke `hr_HR.dic` i `hr_HR.aff` s ponuđenoga mrežnoga mjesta
2. smjestite ih u mapu
    - `/usr/share/hunspell` koristite li GNU/Linux
    - `C:\Users\VAŠE_KORISNIČKO_IME\AppData\Roaming\LibreOffice\4\user\wordbook\` i pronađite mapu s jezičnim paketima i u njih smjestite ove dvije datoteke.
    - na macOS-u su to datoteke `~/Library/Application Support/LibreOffice/4/user/wordbook/` za aktivnu instalaciju LibreOfficea ili `~/Library/Spelling/` za provjeru na razini cijeloga sustava (sve aplikacije)
3. ponovno pokrenite LibreOffice


## Kako ova pravila pokušavaju pomoći

* **Ispravak krnjega infinitiva u futuru I. i konstrukcijama s modalnim glagolima:** Sustav automatski dodaje krajnje *-i* u infinitivima koji ne dolaze ispred oblika glagola *htjeti* (npr. *moram radit* → *moram raditi*), dok ispred pomoćnoga glagola *htjeti* reže puni infinitiv u krnji oblik (npr. *kupiti ću* → *kupit ću*).
* **Uklanjanje suvišne zamjenice "si" u futuru:** Prepoznaje i briše pleonastičnu zamjenicu *si* unutar futur konstrukcija (npr. *kupit ću si* → *kupit ću*, *ću si kupiti* → *ću kupiti*).
* **Kontrola infinitiva u niječnom povratnom futuru:** Osigurava da se u nijeku povratnih glagola upotrebljava puni infinitiv na *-ti* (npr. *neću se vratit* → *neću se vratiti*).
* **Upozorenje na konstrukciju "da li":** Prepoznaje nepreporučenu upitnu česticu *da li* i predlaže preoblikovanje rečenice u duhu hrvatskoga jezika (npr. *da li znaš* → *znaš li*).
* **Uklanjanje konstrukcije prijedlog + infinitiv (na -ti i -ći):** Pronalazi i označava pogrešnu uporabu prijedloga *za, bez, umjesto, osim* ispred glagola te sugerira zamjenu glagolskom imenicom ili preformulaciju (npr. *za učiti* → *za učenje*, *za obući se* → *za odijevanje*).
* **Bezlični oblik glagola "trebati" ispred infinitiva:** Ispravlja pogrešno sklanjanje glagola *trebati* po licima kada se nalazi u funkciji modalnoga glagola ispred drugog infinitiva, u sadašnjosti i prošlosti (npr. *mi trebamo raditi* → *treba raditi*, *trebali smo raditi* → *trebalo je raditi*).
* **Zabrana vremenskoga značenja prijedloga "kroz":** Upozorava na pogrešnu vremensku upotrebu prijedloga *kroz* uz imenice koje označavaju vrijeme i predlaže zamjenu prijedlogom *tijekom* ili padežnim oblicima (npr. *kroz cijelu godinu* → *tijekom cijele godine*).
* **Razlikovanje pridjeva "sljedeći" i priloga "slijedeći":** Ispravlja pogrešno pisanje *slijedeći* (s dugim *ije*) u *sljedeći* kada se odnosi na iduće ili naredne vremenske i prostorne pojmove te unutar prijedložnih izraza (npr. *slijedeći mjesec* → *sljedeći mjesec*, *u slijedećem koraku* → *u sljedećem koraku*).
* **Detekcija dvostruko upisanih istih riječi:** Pronalazi i uklanja pogreške u tipkanju kada se ista riječ ponovi dvaput zaredom (npr. *u u školu* → *u školu*), uz dopuštenu iznimku za izraz *malo*.
* **Pravilna zamjena i naveza prijedloga "s/sa" i "k/ka":** Ispravlja fiksne konstrukcije poput *s menom* u *sa mnom*, dodaje navezno *a* ispred suglasnika s, z, š, ž i teških skupina, uklanja suvišno *a* ispred ostalih glasova te dodaje *a* prijedlogu *k* ispred glasova k, g, h (npr. *sa ocem* → *s ocem*, *k kući* → *ka kući*).
* **Ispravak velikoga početnog slova u malom unutar rečenice:** Prepoznaje i ispravlja nazive jezika, tečajeve, rječnike, gramatike te ustaljene opće sintagme koje su pogrešno napisane velikim slovom (npr. *Hrvatski jezik* → *hrvatski jezik*, *Paški sir* → *paški sir*, *Francuska salata* → *francuska salata*).
* **Spajanje rastavljenih oblika kondicionala (bismo/biste):** Prepoznaje pogrešno razdvojeno pisanje aorista glagola *biti* sa zamjenicama u potvrdnim i niječnim rečenicama te ih spaja u jednu riječ (npr. *bi smo* → *bismo*, *bi ste* → *biste*).
* **Uklanjanje pleonazama, stilskih viškova i pogrešnih parova veznika:** Čisti tekst od niza ustaljenih pleonastičnih izraza i gomilanja istoznačnica poput *čak štoviše*, *no međutim*, *oko cca*, *vratiti natrag*, *sići dolje*, *zato jer*, *oba dvoje*, *ukoliko* (bez *utoliko*) i slično.
* **Uklanjanje suvišnoga "je" uz povratnu zamjenicu "se":** Automatizirano izbacuje suvišan pomoćni glagol *je* u perfektu, pasivu i uz glagolske priloge kada se u rečenici već nalazi povratna zamjenica *se* (npr. *vratio se je* → *vratio se*, *se je smijući* → *se smijući*).
* **Sintaksička kontrola navodnika, zagrada, interpunkcije i neprekidajućih razmaka (NBSP):** Upozorava na nezatvorene navodnike i zagrade, uklanja suvišne bjelina unutar njih, ispravlja dvostruke točke i razmake te automatski umeće neprekidajući razmak (NBSP) između brojeva i mjernih jedinica, oznaka valuta ili postotaka (npr. *50%* → *50 %*, *100eur* → *100 EUR*).
* I još ponešto, da se ne nabraja...



## Za one koji žele znati više

### Postupak pripreme i izrada dodatka za LibreOffice

Problem je s alatom iz repozitorija [github.com/karelin/lightproof](https://github.com/karelin/lightproof) to što se dodatak nije mogao napraviti jer je skripta `make.py` izvorno napisana za `Python 2`. Zbog promjena (nekih) parametara u Pythonu 3, skriptu sam uspješno prilagodio i modernizirao pomoću AI-a, koji je ujedno pomogao generirati i `hr.cfg` datoteku. Dakle tko želi raditi pravila i treba ih kompajlirati zbog testa, mora preuzeti `make.py` iz **ovoga repozitorija**, odnosno treba mu `lightproof.zip`. Više o tome u sljedećem dijelu.

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

Složena pravila i dio „Kako ova pravila pokušavaju pomoći” pisana su uz pomoć umjetne inteligencije kako bi se uštedjelo vrijeme.

---
**Autor:** Krunoslav Šebetić (2026.)

**Licenca:** MPL 2.0 / LGPLv3 (Otvoreni kod kompatibilan s LibreOffice ekosustavom)

