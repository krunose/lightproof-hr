# Jednostavna računalna provjera pravopisa i gramatike hrvatskoga jezika LightProofom

## Kako instalirati dodatak

1. preuzmite `Lightproof_hr-0.1.zip`
2. preimenujte datoteku u `Lightproof_hr-0.1.oxt`
3. instalirajte dodatak (običan dvoklik)
4. ponovno pokrenite LibreOffice


## Postupak pripreme za izradu dodatka za LibreOffice

1. Preuzeti `lightproof.zip`, 
2. raspakirati ga
3. u mapu `~/lightproof/src/hr/` dodati `hr.dat`
4. urediti `hr.cfg`
5. unutar mape `~/lightproof` pokrenuti naredbu
6. `python3 make.py src/hr/hr.cfg`

Problem je što se dodatak nije mogao napraviti jer je skripta `make.py` bila napravljena za `python2`, promijenili su se neki parametri u Pythonu inačice tri tako da sam uspješno prilagodio skriptu pomoću AI-a. Umjetna inteligencija je generirala i `hr.cfg`.


## Najpametnije za napraviti

Trebalo bi klonirati reposzitorij sa [karelin/lightproof](https://github.com/karelin/lightproof), zamijeniti u vlastitoj inačici skriptu

1. `make.py` onom koja je u [mojem repozitoriju](https://github.com/krunose/lightproof-hr/make.py)
2. dodati mapu `lightproof/src/hr/`
3. u nju smjestiti vlastite datoteke `hr.dat` i `hr.cfg`
4. iz mape `lightproof` pokrenuti skriptu `make.py` sa `python3 make.py src/hr/hr.cfg`
5. instalirati dodatak u `.oxt` datotečnom formatu, koji će bit generiran u mapi `~/lightproof/`

kruno [točka] se [na gmx na] comu
