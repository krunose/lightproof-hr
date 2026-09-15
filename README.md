# Jednostavna računalna provjera pravopisa i gramatike hrvatskoga jezika LightProofom

**LightProof je jednostavan alat za provjeru gramatike, tipografije i stila baziran na pravilnim izrazima (regular expression).**

Ovaj dodatak omogućuje brzu, laganu i nativnu provjeru teksta izravno unutar programa LibreOffice Writer, prilagođenu svakodnevnim potrebama izvornih govornika hrvatskoga jezika.

Alat je kalibriran za prepoznavanje najčešćih jezičnih i stilskih previda u praksi:
* **Gramatika i oblici:** Krnji infinitiv u futurima (*radit ću* vs. *neću raditi*), pravilna uporaba enklitika u kondicionalu (*mi bismo*, *vi biste*) i ispravak konstrukcije *da li*.
* **Stil i pleonazmi:** Uklanjanje suvišnih riječi i dvostrukih izraza (*no međutim*, *čak štoviše*, *oko cca*, *vremensko razdoblje*, *sići dolje*).
* **Pravopis i tipografija:** Spajanje odvojeno pisanog superlativa (*naj bolji* -> *najbolji*), ispravak alternacija *ije/je* u pridjevu *sljedeći*, pravilna uporaba prijedloga *s/sa* (uključujući izuzetak *sa mnom*) te uklanjanje višestrukih razmaka i interpunkcijskih znakova.

## Instalacija i preuzimanje

Dodatak je spakiran kao službeni **OXT paket** i spreman je za instalaciju na svim operacijskim sustavima koji podržavaju LibreOffice (v4.0 ili noviji).

1. Preuzmite najnoviju verziju dodatka iz [LibreOffice Extensions platforme](https://libreoffice.org) ili izravno iz našeg [GitHub izdanja (Releases)](https://github.com).
2. Dvaput kliknite na preuzetu `.oxt` datoteku.
3. LibreOffice će automatski otvoriti *Upravitelj upravljačkih programa (Extension Manager)* i instalirati dodatak.
4. Ponovno pokrenite LibreOffice i provjera teksta će postati aktivna.

### Alternativni način instalacije (iz izvornog kôda)
1. Preuzmite `Lightproof_hr-0.1.zip` iz repozitorija.
2. Preimenujte datoteku u `Lightproof_hr-0.1.oxt`.
3. Instalirajte dodatak običnim dvoklikom.
4. Ponovno pokrenite LibreOffice.

## Postupak pripreme i izrada dodatka za LibreOffice

Problem s originalnim alatom je što se dodatak nije mogao napraviti jer je skripta `make.py` izvorno napisana za `Python 2`. Zbog promjena parametara u Pythonu 3, skriptu sam uspješno prilagodio i modernizirao pomoću AI-a, koji je ujedno pomogao generirati i `hr.cfg` datoteku.

### Kako sami možete kompajlirati dodatak:
1. Klonirajte repozitorij s [karelin/lightproof](https://github.com).
2. Zamijenite skriptu `make.py` onom koja se nalazi u [mojem repozitoriju](https://github.com).
3. Dodajte mapu `lightproof/src/hr/`.
4. U nju smjestite vlastite datoteke `hr.dat` i `hr.cfg`.
5. Iz korijenske mape `lightproof` pokrenite skriptu naredbom:
   ```bash
   python3 make.py src/hr/hr.cfg
   ```
6. Spreman dodatak u `.oxt` datotečnom formatu bit će generiran unutar mape `~/lightproof/`.

---
**Autor:** Krunoslav Šebetić (2026.) – kruno [točka] se [na gmx com]

**Licenca:** MPL 2.0 / LGPLv3 (Otvoreni kod kompatibilan s LibreOffice ekosustavom)

