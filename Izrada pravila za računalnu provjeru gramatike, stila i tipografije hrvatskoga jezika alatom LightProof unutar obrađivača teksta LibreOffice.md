# Izrada pravila za računalnu provjeru gramatike, stila i tipografije hrvatskoga jezika alatom LightProof unutar obrađivača teksta LibreOffice

```
Krunoslav Šebetić (studeni 2026.) kruno.se@gmx.com
```

Može se činiti da je provjera gramatike, tipografije i stila koja se izvodi lokalno u doba umjetne inteligencije zastario koncept, ali paradoks je u tome što je upravo umjetna inteligencija ovakav sustav provjere gramatike učinila aktualnijim negoli se na prvu može činiti: naime umjetna inteligencija u kontekstu obradbe teksta može puno, ali u kontekstu zaštite privatnosti u besplatnim inačicama može izuzetno malo. Za pravnike, liječnike i javnu upravu slanje povjerljivih dokumenata na udaljene poslužitelje mahom u SAD-u u kontekstu GDPR-a jednostavno nije opcija. Moguće je anonimizirati tekst &ndash; a što je ples po rubu jer ostavlja prostor za ljudsku pogrešku &ndash; ili koristiti naplatne (engl. <i>enterprise</i>) planove koji u većoj ili manjoj mjeri jamče privatnost, ali to znači izravnu ovisnost o stranim vlasničkim alatima i uslugama te trošku za nešto što može biti slobodno i besplatno te održavano od strane institucija i jezične zajednice.

S druge pak strane umjetna inteligencije nije uvijek pouzdana jer, iako joj je generativna sposobnosti tekstova dobra, često halucinira te izmišlja pravila i zakonitosti koje u jeziku ne postoje. Nije tajna da umjetna inteligencija uglavnom nije trenirana na hrvatskom jeziku za hrvatski jezik jer je to ekonomski neisplativo; premaleno smo tržište, zato su prijedlozi često razgovorni jezik koji ne prati normu. Lokalni i deterministički provjernici su nužnost koja štiti jezičnu točnost, a u slučaju slobodnih alata pruža korisniku izbor i autonomiju, ali i neovisnost o poslovnim modelima velikih tvrtki pri čemu korisnik tajnost podataka plaća svojim privatnim podatcima na ovaj ili onaj način.

Alati poput [Ispravi.me](https://ispravi.me) hvale su vrijedni projekti, ali ne pružaju provjeru riječi i gramatike izravno unutar obrađivača teksta. U kontekstu navedenoga dolazi se do [LanguageToola](https://languagetool.org/): otvorenoga alata koji omogućuje da se napredna provjera gramatike preko dodataka za Microsoftov Word, LibreOfficeov Writer, ali i internetske preglednike kao što su Firefox, Edge i Chrome dovede na gotovo svako računalo i operacijski sustav. U plaćenoj inačici zaštita privatnosti je usklađena s GDPR-om, no postoji mogućnost pokretanja ovoga alata izravno s vlastitog poslužitelja. Međutim hrvatski unutar LanguageToola nije podržan jezik. Budući da se radi o alatu otvorenoga koda, netko bi ta pravila trebao napraviti, a institucije šute. Pravila za neke jezike unutar ovoga alata održava cijeli tim lingvista, stručnjaka za strojno učenje i zajednica entuzijasta. Hrvatski nema ništa. Zar je moguće da danas nitko ne brine o digitalnoj opstojnosti hrvatskoga jezika? Hrvatsko jezično područje malo je tržište i velike tvrtke za njega ne mare često ga stavljajući u isti koš s bliskim jezicima u okruženju. Dotjerati LanguageTool na razinu engleskoga ili njemačkoga nije posao za pojedinca, nego za tim stručnjaka s kakva fakulteta, instituta ili vijeća, koji bi trebali brinuti o tome da svaki govornik hrvatskoga jezika ima slobodu provjeriti tekst ne brinući o ograničenjima vlasničkoga softvera kada postoji besplatno rješenje, ali i slobodna infrastruktura.

## LightProof: besplatna i lokalna provjera gramatike unutar LibreOfficea

Dok je LanguageTool za pojedinca nedostižan ideal koji čeka institucionalnu potporu i angažman, praktično i trenutačno rješenje jest LightProof: besplatan i slobodan podsustav izravno ugrađen u isto tako slobodan i besplatan alat za obradbu teksta LibreOffice. Ovaj se alat izvodi lokalno (engl. <i>client-side</i>) i zasnovan je na pravilnim izrazima (engl. <i>regular expressions</i>) unutar programskoga jezika Python, čime se osigurava potpuna privatnost a bez ikakvih popratnih troškova. Jedini nedostatak ovoga alata jest u činjenici što je vezan isključivo za LibreOffice i nije ga moguće koristiti u drugim obrađivačima teksta ili internetskim preglednicima; međutim nudi brzu i jednostavnu, slobodnu i besplatnu provjeru gramatike, tipografije i stila unutar LibreOfficea na svim važnijim operacijskim sustavima kao što su Windows, macOS i GNU/Linux.

Istina jest da se LightProof danas više aktivno ne razvija, izvorni kod se samo održava, ali još uvijek je integralni dio LibreOfficea. Prednost u odnosu na LanguageTool jest to što korisnik, ako bi se pravila uključila u izvorni kod spomenutoga obrađivača teksta, ne treba preuzimati posebne dodatke ili dodatno postavljati obrađivač teksta, instalacijom LibreOfficea provjera gramatike radila bi odmah (engl. <i>Out-of-the-box</i>).

LightProof je u stanju mirovanja i po značajkama zaostaje za LanguageToolom, ali ipak je riječ o moćnom alatu koji omogućuje da se naprednija pravila pišu programskim jezikom Python, a koje se onda kao funkcije može pozvati u datoteci s pravilima, što omogućuje pisanje prilično složenih uvjeta, slično kao što se to radi u LanguageToolu programskim jezikom Java.

Važno je naglasiti da LightProof nije samo skup pravilnih izraza i koda pisanoga Pythonom, nego je ovaj podsustav usko vezan uz Hunspellov rječnik: moguće je, ako su riječi u rječniku označene, dobiti podatke o vrsti riječi i drugim gramatičkim obilježjima čime se mogu pisati pravila za provjeru slaže li se pridjev uz imenicu uz koju stoji u rodu, broju i padežu. Nevolja je samo u tome što trenutačno nemamo označen Hunspellov rječnik; posao je to koji također čeka institucionalnu podršku ili veći angažman zajednice.

Iz današnje se perspektive LightProof može činiti zastarjelim alatom u koji ne vrijedi ulagati, no smatramo da je za prvu ruku dostatan jer se pravila izvršavaju brzo i lokalno, čime se eliminiraju potrebe za velikim hardverskim zahtjevima, stalnom internetskom vezom i korisnik dobiva provjeru gramatike bez žrtvovanja privatnosti, a jednostavnost izrade pravila omogućuje da se praznina u kontekstu provjere gramatike, stila i tipografije popuni relativno brzo i bezbolno. Uostalom, ako ova pravila postanu dovoljno složena i stabilna, njihovo prebacivanje u LanguageTool više ne znači voditi bitku s ispravnošću pravila i rješavanju lažnih uzbuna, već rutinsko prepisivanje pravila iz Pythona i pravilnih izraza u Javu i &ndash; pravilne izraze unutar XML-a.

## Kako pokrenuti LightProof i izraditi dodatak

Budući da se ovaj sustav nalazi u fazi održavanja, postojale su određene prepreke pri pokretanju. Naime, jednom kada se pravila napišu i kada se pretvore u dodatak (datoteka `OXT`), sustav radi besprijekorno, no problem je što ne postoji dobra i ažurirana službena dokumentacija. Ovome svjedoči i činjenica da tek šačica jezika ima razrađena pravila za LightProof: engleski, mađarski, ruski i čini nam se portugalski u brazilskoj varijanti. S druge strane, mnogi drugi jezici imaju ili LanguageTool (pa zanemaruju LightProof) ili i LanguageTool i LightProof; hrvatski (do sada) nije imao ni jedno ni drugo. Mahom zbog toga što veći jezici imaju označene rječnike za LanguageTool, ali malo ih ima (ako tko uopće) označen rječnik za Hunspell, a što je preduvjet za napredniju provjeru gramatike.

### Što je zapravo LightProof

Riječ je podsustavu (engl. <i>framework</i>) pisanome programskim jezikom Python temeljenom na pravilnim izrazima i koji je usko vezan uz provjeru pravopisa [slobodnim sustavom Hunspell](https://github.com/krunose/hunspell-hr/blob/master/tools/Izrada%20rje%C4%8Dnika%20za%20ra%C4%8Dunalnu%20provjeru%20rije%C4%8Di%20hrvatskoga%20jezika%20Hunspellom.pdf), a nastao je kao laka alternativa naprednijem LanguageToolu, koji je ovisan o programskom jeziku Java. Budući da pravilni izrazi imaju svoja ograničenja, LightProof dopušta sastavljaču pravila da koristi Python za izradu složenih uvjeta i operacija.

U svojoj suštini ovaj provjernik gramatike je zapravo generator dodatka: LightProof uzima konfiguracijsku datoteku (recimo `hr.cfg`) i upari je s popisom pravilnih izraza i uvjeta pisanih u Pythonu (recimo `hr.dat`) i iz njih generira dodatak za LibreOffice. Iako ta jednostavnost znači da LightProof nije moćan kao LanguageTool ili kakav veliki jezični model, upravo je njegova jednostavnost ono što ga čini pogodnim da se hrvatskom, barem za prvu ruku, dâ kakav-takav provjernik gramatike, tipografije i stila.

### Kloniranje repozitorija i izrada testnoga dodatka

Treba naglasiti da pravila za LightProof za nekoga tko nije po zanimanju programer a bez dobre dokumentacije ne bi bio moguć bez umjetne inteligencije. To i jest razlog zašto se pravila nisu pojavila prije desetak godina. Tada jednostavno nismo znali od kuda krenuti i kako uopće postaviti sustav. Zato smo u rujnu 2026. odlučili uposliti umjetnu inteligenciju kako bismo shvatili kako ovaj alat radi. Preuzeli smo izvorni kod iz repozitorija [https://github.com/karelin/lightproof](https://github.com/karelin/lightproof) naredbom

```
git clone https://github.com/karelin/lightproof.git
```

i slijedili upute u datoteci `README`. Ono što stoji u toj datoteci jest da treba pokrenuti naredbu `python make.py src/en/en.cfg` kako bi se izgradio dodatak za engleski jezik. Međutim skripta `make.py` vraćala je grešku pri izradi dodatka. Budući da ne programiramo u Pythonu toliko da bismo znali prepraviti pogrešku u datoteci, jednostavno smo datoteku `make.py` proslijedili umjetnoj inteligenciji, priložili opis greške iz naredbenog retka i zatražili da nam umjetna inteligencija vrati ispravljenu skriptu.

Greška je bilo još pa se umjetnoj inteligenciji proslijedila i datoteka `lightproof_compile___implname__.py` iz direktorija `pythonpath`. I to je riješilo problem.

Dakle nakon kloniranje repozitorija potrebno je preuzeti datoteke `make.py` i `lightproof_compile___implname__.py` s [github.com/krunose/lightproof-hr](https://github.com/krunose/lightproof-hr) i prvu postaviti u krovni direktorij kloniranoga repozitorija, a drugu unutar mape `pythonpath` i zatim izgraditi dodatak za engleski jezik naredbom `python3 make.py src/en/en.cfg`.

### Izrada dodatka za hrvatski jezik

Sada kada izrada dodatka prolazi bez greške, potrebno je unutar mape `src` napraviti mapu `hr/` i u nju postaviti datoteke `hr.dat` i `hr.cfg` iz [ovoga repozitorija](https://github.com/krunose/lightproof-hr). Izraditi dodatak s hrvatskim pravilima sada se može naredbom

```
python3 make.py src/hr/hr.cfg
```

Datoteku `hr.cfg` također je pripremila umjetna inteligencija po uzoru na sličnu englesku datoteku. Budući da dobre dokumentacije za ovu fazu prilagodbe nema, nije preostalo drugo nego poslužiti se tim trikom.

Nakon izvršenja naredbe za generiranje dodatka u krovnom direktoriju stvorit će se datoteka `Lightproof_hr-0.5.8.30.oxt` ili sličlno, ovisno o tome koja se brojčana oznaka upisala u datoteci `hr.cfg` u redak `version = 0.5.8.30`.

Za instalaciju dodatka potrebno je otvoriti LibreOffice Writer i odabrati `Tools` → `Extensions...` te označiti dodatak `Osnovna provjera gramatike...` ako je instaliran već od ranije i odabrati `Remove` te ponovno pokrenuti LibreOffice. Zatim se ponovimo `Tools` → `Extensions...`, ali sada odaberemo `Add` i pronađemo gdje se nalazi novogenerirani dodatak i odaberemo ga dvoklikom. Potrebno je ponovno pokrenuti LibreOffice klikom na `Close` u dijaloškom okviru dodataka te odabirom `Restart Now`.

Pravila koja smo do sada uspjeli napraviti nisu u izvornom kodu LibreOffice jer je proces uključivanja u izvorni kod spor i to je proces koji je izvan naših mogućnosti, a ni pravila još nisu sazrela jer nemamo povratnih informacija stvarnih korisnika na stvarnim tekstovima. Zato ih nudimo kao [dodatak LibreOfficeu](https://extensions.libreoffice.org/en/extensions/show/99654). Na ovaj način možemo brzo i bezbolno ispravit nedostatke i obavijestiti korisnike o postojanju novije inačice, ne treba čekati novo izdanje LibreOfficea a da bi se ispravilo pojavljivanje koje lažne uzbune.

Valja samo naglasiti da je ovaj dodatak izravno ovisan o djelomično označenom Hunspellovu rječniku dostupnom na [github.com/krunose/husnpell-hr](https://github.com/krunose/hunspell-hr). Naime, uspjeli smo rudimentarno označiti barem infinitive kako bismo mogli provjeravati pisanje krnjega infinitiva u futuru I.

## Proces instalacije dodatka radi testiranja pravila

Ako bi tko želio testirati ova pravila, potrebno je:

* Obrisati stari rječnik ako je instaliran kao dodatak
	* pomoću `Upravitelja dodatcima` tako što se otvara izbornik `Tools` → `Extensions...` te se odabere se dodatak s rječnikom i zatim klikne `Remove`. Odabirom `Close` u dijaloškom okviru `Upravitelja dodatcima` ponovno se pokreće LibreOffice odabirom `Restart Now`.
* Instalirati novi dodatak s označenim rječnikom
	* preuzimanjem iz [službenoga repozitorija dodataka LibreOfficea](https://extensions.libreoffice.org/en/extensions/show/99660) klikom na zeleni gumb `Download`. Zatim se odlazi u `Tools` → `Extensions...` i klikne se na `Add`. Odabere se ododatak s rječnikom. Klikne se na `Close` i odabere se `Restart Now`.
* Preuzima se dodatak s [pravilima za provjeru gramatike](https://extensions.libreoffice.org/en/extensions/show/99654) i instalira se prema uputama iz prethodnoga koraka.

Nakon ponovnoga pokretanja LibreOfficea, provjera gramatike trebala bi biti aktivna.

## Anatomija pravila za LightProof

Štura dokumentacija o tome kako se pišu pravila za LightProof nalaze se u mapi `doc` u repozitoriju [github.com/karelin](https://github.com/karelin/lightproof/tree/master/doc) u datoteci `syntax.txt`. Osnovna struktura nije komplicirana: na lijevoj strani nalazi se pravilni izraz koji će LightProof prepoznati kao pogrešku, u sredini je uvjet koji mora biti ispunjen da bi se pravilni izraz aktivirao, a na desnoj je zamjena i poruka korisniku, shematski se struktura pravila može prikazati na sljedeći način:

```
pravnilni izraz <- uvjet -> zamjena # Poruka korisniku vezano za pogrešku.
```

### Jednostavna zamjena s prijedlogom korisniku bez uvjeta i pravilnih izraza

U svojoj strukturi pravila ne moraju uvijek sadržavati uvjet ni složeni pravilni izraz, evo primjera s pogreškom u pisanju instrumentala društva osobne zamjenice:

```
s menom -> sa mnom # Instrumental društva osobne zamjenice 'ja' glasi 'sa mnom'.
```

U ovom slučaju LightProof podcrtava `s menom` i bez ikakva uvjeta predlaže korisniku `sa mnom` i istovremeno nudi poruku `Instrumental društva osobne zamjenice 'ja' glasi 'sa mnom'`. Znak `#` na kojem god drugom mjestu u kodu označava običan komentar, ali ne i ako se nalazi s desne strane prijedloga za ispravak.

### Jednostavna zamjena bez prijedloga korisniku i bez uvjeta i pravilnoga izraza

Općenito se vodimo načelom da ako bi koji prijedlog korisniku mogao uništiti tekst zbog lažnih uzbuna (engl. <i>false positive</i> i(li) <i>false negative</i>), bolje je ne predložiti ništa, već samo upozoriti korisnika da koja konstrukcije nije u duhu hrvatskoga standardnoga jezika. Takva je konstrukcije `da li`; ona se može naći na početku upitne rečenice, može se naći u sredini rečenice, a kao pogreška uvijek dolazi kada se čestica `li` nalazi iza `da`. Međutim prilikom ispravljanja dolazi do ispadanja `da` i premetanja riječi, što komplicira prijedlog korisniku. Umjesto krivih prijedloga, odlučili smo se za ovaj pristup:

```
da li -> _ # Konstrukcija 'da li' nije u duhu hrvatskoga standardnoga jezika, preformulirajte rečenicu.
```

Ovo će pravilo podcrtati konstrukciju `da li`, ali zbog znaka `_` korisniku ne nudimo čvrstu zamjenu, već samo uputu: ` # Konstrukcija 'da li ' nije u duhu...`

### Uvođenje jednostavnoga pravilnoga izraza

Oštrije oko će primijetiti da će LightProof podcrtati `da li` ako je pisano malim slovom, u sredini rečenice, ali će zanemariti ovu konstrukciju ako se nalazi na početku upitne rečenice kada je pisana velikim slovom. Tomu možemo doskočiti uvođenjem pravilnih izraza:

```
\b[dD]a li -> _ # Konstrukcija 'da li' nije u duhu hrvatskoga standardnoga jezika.
```

Ovako napisano pravilo hvata konstrukciju `da li` bilo gdje u tekstu. Duljiti se o pravilnim izrazima neće jer je ovaj tekst ionako pozamašan i ne možemo u njega ugurati još i tutorijal o pravilnim izrazima. Pretpostavka je da se pravilni izrazi znaju i mogu pisati.

### Nuđenje više zamjena za jednu pogrešku

Ponekad jedna pogreška može tražiti da se korisniku ponudi više zamjena. U sljedećem primjeru je važno primijetiti da su riječi koje će biti ponuđene u zamjeni obavijene zagradama kako bismo se na te riječi mogli pozvati u zamjeni i komentaru korisniku:

```
(no) (međutim) -> \1|\2 # Konstrukcija '\1 \2' je pleonazam, odaberite '\1' ili '\2'.
```

Pravilni izraz na lijevoj strani možemo upotpuniti uvjetom u sredini kako bismo dobili još složenija pravila.

### Uvođenje uvjeta u pravilo

Uzet ćemo pravilo za ispravljanje infinitiva u futuru I: `Pisati ću pravila.` > `Pisat ću pravila.` Naravno, ovo nije pravilo doslovno prepisano iz `hr.dat` datoteke jer je odviše jednostavno, ali za primjer će poslužiti:

```
\b(\w+t)i\s(ću|ćeš|će|ćemo|ćete)\b <- morph(\1, "po:glagol", False) -> \1 \2 # Infinitiv ispred pomoćnoga glagola htjeti dolazi u krnjem obliku.
```

Pravilni izraz hvata koju god riječ koja završava na `-ti` ako iza nje slijede razmak (`\s`) i koji od nenaglašenih oblika pomoćnoga glagola htjeti. Iako pravilni izraz hvata bilo koju grupu koja završava na `-ti`, zagrade nam dozvoljavaju da u grupi `\1` uzmemo riječ bez završnoga `-i` jer se ono nalazi izvan zagrade. Tako smo dobili krnji infinitiv bez ikakva kompliciranja. Sada nam pravilni izraz dalje filtrira korisnički unos jer riječ na `-ti` će biti podcrtana samo ako iza nje slijede razmaka i, recimo, nenagl. oblika pomoć. gl. htjeti `ću`.

Međutim navedeno nije dovoljno jer ne završavaju samo glagoli (infinitivi) na `-ti`, već i neke imenice, recimo imenica <i>osti</i> u značenju, prema Hrvatskom jezičnom portalu, <i>trozubi čelični šiljak pričvršćen na dug štap, služi za hvatanje ribe i glavonožaca</i> [ove osti]. Kako bismo razlikovali je li riječ o imenici ili glagolu, svim infinitivima smo u [Hunspellovu rječniku](https://github.com/krunose/hunspell-hr) dodijelili oznaku `po:glagol`. Sada uvjet u sredini izraza dodatno filtrira pravilni izraz i s većom točnošću hvata upravo infinitiv ispred nenagl. oblika pom. gl. <i>htjeti</i>.

#### Funkcija morph()

Za relativnu robusnost ovoga pravila zaslužna je funkcija `morph()` koja prima tri argumenta: prvi je, u konkretnom primjeru, prva grupa unutar zagrada (`\1`), drugi je oznaka (engl. <i>part-of-speech tag</i>), a treći može imati vrijednost `True` ili `False`. U našem primjeru funkcija `morph()` provjerava samo postoji li u rječniku za koju riječ oznaka `po:glagol`, i zato je treći argument `False`. Međutim, ako je on `True`, onda je moguće drugi argument pisati kao pravilni izraz.

Trenutačno to ne čini razliku jer rječnik nije označen, ali ako bi bio označen `MulText-East` oznakama (`v6`), one bi se mogle pretraživati pomoću pravilnih izraza: funkcija `morph(\1, "N...an", True)` provjerila bi znači li imenica (`N`) u grupi `\1` nešto neživo (`n`) u akuzativu (`a`). Tri točke označavaju pravilni izraz koji preskače `tip`, `rod` i `broj`. Ta se informacija može koristiti za ispravak `automobil kojega vozim` u `automobil koji vozim`:

```
(\w+)\skojeg(a)? <- morph(\1, "N...an", True) -> \1 koji
```

Istina jest da LightProof nije moćan kao LanguageTool, ali kada bismo imali označen rječnik, značajke koje ovaj provjernik gramatike posjeduje bile bi i više nego dovoljne da se provjera gramatike za hrvatski jezik postavi na zdrave noge. Ključ napretka nije u samom alatu koliko u činjenici da trebamo označiti Hunspellov rječnik.

#### Funkcija stem()

Funkcija `stem()` prepoznaje osnovni, kanonski oblik riječi bez obzira na to u kojem je obliku riječ napisana na lijevoj strani izraza. Naravno, o ovome možemo pisati samo teorijski jer nemamo upisane kanonske oblike riječi (stemove) u rječnik uz troslovnu oznaku `st:`. Ovaj dio teksta treba proširiti kada se u rječnik uvedu ove oznake.

#### Funkcija affix()

Trenutačno u rječnik nije pripremljen za korištenje ove funkcije, a onda ju ne koristimo ni u pravilima za LightProof, no ono što smo učinili jest ubacili datoteku `LightProof.py` u umjetnu inteligenciju zajedno s onih par šturih natuknica u službenoj dokumentaciji i umjetna inteligencija je složila sljedeći odgovor:

> Funkcija **`affix()`** je specijalizirana varijanta funkcije `morph()` koja služi za morfološku analizu riječi preko integriranog Hunspell rječnika. Njezina glavna zadaća je da iz morfoloških rezultata potpuno filtrira i izbriše korijen (bazu) riječi, ostavljajući isključivo polja s gramatičkim oznakama nastavaka (prefiksa i sufiksa). Na taj se način osigurava da sam tekstualni sadržaj korijena riječi ne može lažno aktivirati pravilo, već se provjera vrši isključivo nad čistim gramatičkim oznakama.

> Da bi funkcija uopće imala što analizirati, Hunspell rječnik mora biti morfološki označen. U datoteci s pravilima nastavaka (`.aff`) svakom se sufiksu ili prefiksu mora dodati eksplicitna oznaka pomoću znaka `+` (primjer: `SFX X 0 a . +sfx:f_sg`), dok se u datoteci s riječima (`.dic`) osnovni oblici povezuju s tim pravilima preko zastavica (primjer: `žena/X`). Kada Lightproof preko funkcije `affix()` pošalje upit za riječ `žena`, on iz rječnika povlači samo izolirani znakovni niz (engl. <i>string</i>) oznake afiksa: `"sfx:f_sg"`.

> Sama funkcija ima dva oblika s obzirom na broj argumenata i način rada:

> * `affix(word, regex_pattern)` – Radi u zadanom (engl. <i>default</i>) načinu rada `all`. Zahtijeva da svi morfološki oblici riječi (ako ih rječnik nudi više) obvezno zadovoljavaju zadani regularni izraz kako bi funkcija vratila `True`.
* `affix(word, regex_pattern, False)` – Dodavanjem parametra `False` aktivira se mod `if exists`. U ovom je načinu rada dovoljno da barem jedno morfološko tumačenje riječi sadrži traženi afiks da bi funkcija vratila `True`, što je ključno za jezike s bogatom morfologijom i čestim homonimima.

```
# Tražimo bilo koju riječ (\1) iza koje slijedi riječ "koji" (\2)
(\w+) (koji)

# UVJET: Izoliramo afikse riječi \1 i tražimo oznaku ženskog roda.
# False prebacuje funkciju u mod "if exists" (dovoljno je jedno podudaranje).
<- affix(\1, r"sfx:f_sg", False) ->

# AKCIJA: Prvu riječ prepisujemo, a zamjenicu "koji" mijenjamo u "koja".
= \1 + " koja"

# PORUKA KORISNIKU
## Provjerite slaganje zamjenice s imenicom ženskog roda.
```

#### Funkcija spell()

LightProof ima i ugrađenu funkciju `spell()` koja provjerava nalazi li se određeni znakovni niz u Hunspellovu rječniku, odnosno provjerava je li riječ ispravno napisana. Ovu funkciju koristimo za provjeru spajanja prefiksoida ako je napisan odvojeno od riječi uz koju stoji. Opet, primjer je pojednostavljen i nije izravno izvučen iz `hr.dat` datoteke, ali poslužit će:

```
\b(\w+)\s(\w+) <- spell(\1 + \2) -> \1\2 # Prefikosid '\1' piše se sastavljeno s riječi '\2'.
```

### Sekcije `[code]`, `[word]` i `[char]`

Ipak, ovako napisano pravilo postavljeno je preširoko i davalo bi lažne uzbune; potrebno ga je suziti. To se napravilo slaganjem liste prefiksoida i pravilo se aktivira samo ako je prva riječ na popisu prefiksoida. Na vrh datoteke dodali smo sekciju `[code]` i unutar nje postavili polje (engl. <i>array</i>). Nakon postavljanja popisa prefiksoida promijenili smo sekciju u `[word]` i dodali pravilo koje u svom uvjetu provjerava spomenuti popis:

```
[code]

prefiksoidi = set(["kontra", "auto", "makro"])


[word]

\b(\w+)\s(\w+) <- \1.lower() in prefiksoidi and spell(\1 + \2) -> \1\2 # Prefiksoid '\1' piše se sastavljeno s riječju '\2'.
```

Zamislimo li pogrešku `auto mehaničar`, ovako postavljeno pravilo će provjeriti je li riječ `auto` na popisu prefiksoida, a jest (`\1.lower() in prefiksoidi`); zatim će provjeriti postoji li u Hunspellovu rječniku riječ koja je ispravna ako se prefiksoid spoji s drugom riječi u izrazu (`spell(\1 + \2`); ispuni li se uvjet, prijedlog korisniku će biti `automehaničar`.

Sekcija `[code]` dozvoljava da se ispod nje piše arbitrarni kod u Pythonu, čime se proširuju ugrađene mogućnosti LightProofa. Sekcija je aktivna sve dok ne naiđe na sekciju `[word]`. U ovom je dijelu moguće pisati prilagođene funkcije koje primaju parametre i koje je moguće pozivati u sekciji `[word]`.


Dok je `[code]` rezerviran za čisti Python, sekcija `[word]` kao tokene uzima riječi između bjelina, ali `[char]` operira na razini znaka, rečenicu promatra kroz niz znakova, ne popis riječi (tokena). Ovu sekciju koristimo za ispravljanje dvostrukih razmaka i sličnih pravila:

```
[char]

[\s]{2,3} -> " " # Jeste li slučajno unijeli dva ili tri razmaka, a htjeli ste jedan?
```

U sekcijama treba spomenuti još `[Word]` (veliko `W`) koja operira (tokenizira) na razini riječi, ali ne vodeći računa o razlici između maloga i velikoga slova. Ako sekcija `[word]` tokenizira na razini riječi i osjetljiva je na razliku između maloga i velikoga slova, onda sekcija `[Char]` operira na razini znaka ne vodeći računa o razlici između velikih i malih slova.

#### Primjer funkcije u sekciji `[code]` pozvane u sekciji `[word]`

```
[code]

# Funkcija prima riječ i provjerava počinje li na tvrdo slovo 'č'
def pocinje_na_c(tekst):
return tekst.startswith("č") or tekst.startswith("Č")


[word]

# Tražimo riječ od dva slova koja počinje na 'č' (npr. ču ili Ču)
\b([čČ]u)\b <- pocinje_na_c(\1) -> ću # Vjerojatno ste mislili na pomoćni glagol 'htjeti' (ću). Riječ 'ču' je aorist glagola 'čuti'.
```

### Postavljanje if-else bloka u ispravak

Relativno je jednostavno uhvatiti pravilni izraz koji u sebi sadrži veliko ili malo slovo, ali malo je teže dati prijedlog ovisno o tome je li izraz počeo velikim ili malim slovom. Zato se u prijedlozima može pisati `if-else` kod:

```
([uU]) vezi toga -> = "U vezi s tim" if \1.istitle() else "u vezi s tim" # Konstrukcija 'u vezi' traži instrumental:
```

### Pozivanje konstrukcije `any`

```
[word]

\b(\w+)\s+(\w+)\b <- morph(\2, "po:glagol", False) and any(\1.lower() == oblik for oblik in ["trebam", "trebaš", "trebamo", "trebate", "trebaju"]) -> treba \2 # Kada glagol 'trebati' dolazi ispred infinitiva, u strogom standardu je bezličan (npr. umjesto 'trebamo raditi' pravilno je 'treba raditi').
```

### Pozivanje funkcija modula Calc u prijedlozima ispravaka

Zanimljivo je što se unutar LightProofa mogu pozivati i funkcije LibreOffice Calca kao `tuple`. Treba samo voditi računa o tome da ispred desnih zagrada poslije posljednjega argumenta stoji zarez i da se prije pozivanja funkcije upotrijebi znak jednakosti. Evo primjera:

```
Oko (deset|dvadeset|trideset|pedeset|šezdeset|sedamdeset|osamdeset|devedeset|stotinj)ak -> = calc("PROPER", (\1 + "ak",)) # Pleonazam. I 'oko' i '\1' znače isto, treba pisati:
```

### Primjer provjere unutar cijeloga odlomka

Varijabla `s` po svemu sudeći vraća cijeli odlomak, evo kako se pomoću nje riješilo pitanje nezatvaranja navodnika:

```
(^|(?<=\s))„(\w+)\b <- s.count("„") != s.count("”") -> _ # Provjerite navodnike. Čini se da niste zatvorili navodne znakove negdje u odlomku.
```

Nije jasno kako se varijabla `s` odnosi prema varijabli `p` jer umjetna inteligencija spominje obje. Za prvu tvrdi da vraća cijelu rečenicu, a druga cijeli odlomak, ali to nismo uspjeli potvrditi na primjerima u praksi. Nezatvaranje navodnika varijablom `s` provodi se nad cijelim odlomkom. Treba provesti dodatne testove kako bi se utvrdilo što zapravo sadržava varijabla `p`; možda vrijednosti varijabli ovisi o tome pozivaju li se unutar sekcija `[word]` ili `[char]`.

### Word(-1) i word(1) odnosno word(n)

Unutar LightProofa moguće je provjeravati kontekst izrazima `word(-1)`, koji vraća riječ ispred (cijelog) pogotka pravilnoga izraza i funkcijom `word(1)`, koja vraća riječ poslije cijeloga pravilnoga izraza. Tako za provjeru futura I koristimo

```
\b(\w+t)i\b <- word(1).lower() in ["ću", "ćeš", "će", "ćemo", "ćete"] -> \1 # Ispred pomoćnoga glagola 'htjeti' infinitiv mora biti u krnjem obliku.
```

Prednost ovoga načina provjeravanja konteksta jest u tome što ne označavamo plavom linijom više negoli je potrebno. Ako je sve što želimo podcrtati i ispraviti `čitati` u `čitat` ako slijedi `ću`, `ćeš`..., onda `word(1)` radi odličan posao.

Budući da je krnji infinitiv kada stoji samostalno pogreška (kada nije dio futura I), treba ga razlikovati od glagolskoga pridjeva trpnoga koji završava na `-t`. To radimo tako što provjeravamo prethodi li riječi koja završava na `-t`, recimo, pomoćni glagol, jer u tom slučaju je najčešće riječ o glagolskom pridjevu trpnom i tada ne ispravljamo `-t` u `-ti`:

```
\b(\w+t)\b <- word(-1) not in ["sam", "si", "je"] -> \1i # Ako je riječ o infinitivu, ne o glag. prid. trpnom na -t, treba pisati '\1i'.
```

## LightProof je ipak rudimentaran alat

Iako ima pokoji trik u rukavu, LightProof je vrlo rudimentaran alat. Čak ako bi se pretvarali da imamo označen rječnik (a nemamo), nevolja je u tome što te oznake ne bismo mogli iskoristiti u LightProofu za generiranje prijedloga ispravaka korisniku. Koliko smo se mi uspjeli upoznati s ovim alatom, ne postoji mogućnost da se LightProofu zada da uzme riječ pogođenu pravilnim izrazom te da mu se zadaju morfološke oznake i da prema njima generira novu riječ. Recimo, želimo rečenicu `Gledam automobil kojega vozi.` ispraviti u `Gledam automobil koji vozi.`, ali u LightProofu ne postoji način da iskoristimo oznake pa da sustav sam generira `koji` iz `kojega`. Evo što bismo htjeli imati:

```
\b(\w+) (kojega)\b <- morph(\1, "imenica:muški:neživo:akuzativ", True) -> generate(stem(\2), "zamjenica:muški:akuzativ") # Rezultat bi trebao biti 'automobil koji' jer uz imenice muškoga roda koje znače neživo, akuzativ je jednak nominativu.
```

Ono što bismo sada mogli jest označiti rječnik i napraviti nešto ovako:

```
\b(\w+) kojega\b <- morph(\1, "imenica:muški:neživo:akuzativ", True) -> \1 koji # Rezultat bi trebao biti 'automobil koji' jer uz imenice muškoga roda koje znače neživo, akuzativ je jednak nominativu.
```

Iako se može činiti da pretjerujemo, činjenica jest da ako se već ima označen rječnik, onda ovakve zamjene ne bi trebalo pisati ručno.

Uza sve upute i hvalu treba priznati da je LightProof &ndash; a nije se ni skrivalo &ndash; rudimentaran alat zamišljen da bude brz pri lokalnom izvršavanju i jednostavan za pisanje pravila, ali zato i ispravlja samo najosnovnije. Relikt je to nekih prošlih vremena koji je u vrijeme umjetne inteligencije i činjenice da bolje nemamo zapravo &ndash; paradoksalno &ndash; neophodan.

## Drska kritika za kraj

Cijeli ovaj podnaslov mogao bi se svesti na jednu rečenicu: **Hrvatski nema ništa!** U rječnik za računalnu provjeru pravopisa uloženo je mnogo vremena i truda, ali još uvijek nije označen. Pitanje je hoće li i biti. Ono što za druge jezike odrađuju fakulteti, instituti i vijeća, kod nas se rade pojedinci u slobodno vrijeme bez ikakvih resursa. Zašto se alati i rječnici iskorišteni za istraživanja nisu pretočili u označen Hunspellov rječnik i pravila za računalnu provjeru gramatike LanguageToolom? Ne bi bilo teško. Evo koliko je složeno u GNU/Linuxu izvući prva tri retka iz [hrLex_v1.3](https://www.clarin.si/repository/xmlui/handle/11356/1232) i dobiti format rječnika pogodan za LanguageTool:

```
awk -F'\t' '{print $1, $2, $3}' hrLex_v1.3 > prva_tri_stupca_hrLex
```

i to je to. Imamo označen rječnik. Onda bi netko sa kakva fakulteta, instituta ili vijeća trebao razgovarati sa tvorcima [Ispravi.me](https://ispravi.me/) i napisati pravila za LanguageTool u XML-u a nije teško i u kratko vrijeme hrvatski bi po tom pitanju bio u rangu sa drugim svjetskim jezicima. Svi oni u Chromeu i Firefoxu koriste ovaj rječnik s kojim se mi borimo; vjerojatno ga svi i kritiziraju, ali nitko ništa po tom pitanju ne poduzima. Svi oni koriste upravo rječnik na koji mi trošimo svoje slobodno vrijeme i vjerojatno mu se smiju, ali po tom pitanju se ne radi ništa. Nije više pitanje jesmo li zadovoljni i znamo li bolje kada je činjenica da ovo i jest najbolje što imamo.

## Vanjski izvori

* [github.com/karelin/lightproof](https://github.com/karelin/lightproof)
* [github.com/krunose/lightproof-hr](https://github.com/krunose/lightproof-hr)
* [github.com/krunose/hunspell-hr](https://github.com/krunose/hunspell-hr)
* [Dodatak za provjeru gramatike LightProofom u LibreOfficeu](https://extensions.libreoffice.org/en/extensions/show/99654)
* [Izrada rječnika za računalnu provjeru riječi hrvatskoga jezika Hunspellom](https://github.com/blob/master/tools/Izrada%20rje%C4%8Dnika%20za%20ra%C4%8Dunalnu%20provjeru%20rije%C4%8Di%20hrvatskoga%20jezika%20Hunspellom.pdf)
* [hrLex v1.3](https://www.clarin.si/repository/xmlui/handle/11356/1232)
* [Ispravi.me](https://ispravi.me/)
* [LanguageTool.org](https://languagetool.org)







