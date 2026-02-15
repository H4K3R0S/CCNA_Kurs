

Krecemo sa Network Slojem - IP adresiranjem



Glavna uloga network sloje je logicko adresiranje IP adresama, nasa duznost kao mreznih admi, je da adresiramo uredjaje, koje mreze ce se koristiti, kakvu cemo samu podlogu praviti, tu se takodje radi kapsulacija i enkapsulacija. paketiranje.


Glavni protokol na Network sloju je IP protokol
pored njega imamo i ICMP protokol


IP protokol se moze podeliti u 2 protokola
IPv4
IPv6

IPv4 - je klasican kojii dalje svakodnevno koristimo. 1.33.167.6

IPv6 - je samo malo moderniji 


IANA - Globalna asociacija za dodelu IP adresa, 2011 je ostala bez slobodnih adresa, jos tada su vredali svoje posednje adrese na RIR-ovima.

Ali bez obzira sto su sve razdeljene, Idalje nece moci da se prekunu sa upotrebom jer je jos uvek zavisnost sistema od njih.


U klasicnom nacinom ISP nam dodeljuje bublick IP adresu, koju mozemo da koristimo dok postoji.

CGNat - je jedan od nacina koji moze da proziri opseg uppotrebe IPv4 IP adrese, jer omogucava da na jednu IP adresu stoje vise uredjaja koji su povecazni na taj CGNat.

IP adresa koji od ISP dobijemo preko CGNat-a su zapravo idalje privatne, 
100.x.x.x/10


Ovim nacinom se zapravo radi duplo NAT-ovanje.


Mana je samo da ako blokiraju tu bublick IP adresu - bice blokirani svi koji koriste tu IP adresu, takodje ne mozemo da hostujemo sajt, server.

Mozemo da proverimo na nasem uredjaju WAN Ip adresu, te potom da vidimo sa web wtahismyip , ako se te adrese poklapaju onda na nas IP ako se ne poklapaju onda smo preko CGNat.

----------------------
Svoju IP Public IP adresu moze da se zakupi sako kao Pravno lice.

------------------


Za IPv6 - Uglavnom koristi samo velike kompanije, Google,AWS, isl. Dok sirom sveta tek polako se prelazi na IPv6.

Takodje postoji Dual Stagil - Koji prvenstveno radi na IPv4 a ako treba prebacuje se na IPv6



-----------------
Format IPv4 Adrese
192.168.20.1


IPv4 ima 32bit

koji su podeljeni od po 4 okteda koji ima 8bit-a i svaki oktet odvojen je tackom


To je zato sto racunar ne viti IP adrese vec kao nule i jedinice, tj ova ip adresa se sastoji od 32bit-a tj 32 jedinice i nule.


Recimo da imamo dva racunara PC1 iPC2 koju su prikljuceni na switch

PC1 - 192.162.4.10
PC2 - 192.162.4.20

Da bi moglo da se sazna dali su u istoj mrezi moramo da imamo subnetmask-u


Subnet maska kakodje ima 32bit-a
subnet maska takodje odredjuje kojiko IP adresa mozemo da imamo u nekoj mrezi


Vrednosti koji stoje u IP adresama su od 0-255


---------------------

Sada je vazno da naucimo kako da prevodimo IP adrese u binarni jezik

Ovo je jedna jednostavna tabela za prevodjenje 2na7 itd
2/7 | 2/6 | 2/5 | 2/4 | 2/3 | 2/2 | 2/1 | 2/0 |
128 | 64  | 32  |  16 |  8  |  4  |  2  | 1   |


Zbir ovih brojeva daje 256


Pocinjemo prevoditi od najveci broj u tabeli,
Gde se broj uklapa pisemo 1 a gde se ne uklapa pisemo 0



|   |128  | 64  | 32  |  16 |  8  |  4  |  2  | 1   |

192 |O    |O  	|	x |  x  |  x  | x   | x   | x
168 |O    |x    | O   |  x  | O   |  x  | x   | x
20  |
1   |
192  128 moze tj treba nam u sabiranju


Primer druge adrese


1)

171 
73
149
57


10110001.01001001.10010101.00111001


128+32+16+3 = 179.

64+32+8+4+1 = 109. 

128+64+32+4 = 228

32+16+8+4+1 = 61


10110011.01101101.11100100.00111101
179.109.228.61




==========================================


Imamo 5 klasa u IPv4 adrese

1klasa = a  ide od 0-127 (0.0.0.0-127.255.255.255) -> subnet maska za te adrese -> 255.0.0.0 ili u CIDR /8  (CID Rotation)
koriste se sa loopback 
0-126 (1.0.0.0-126.255.255.255)


Klasa B - 128-191 (128.0.0.0 - 191.255.255.255) -> subnet maska - (255.255.0.0)  -CID - /16


Klasa C - 192-223 (192.0.0.0 - 223.255.255.255.) -> subnet 255.255.255.255  -> CID -> /24

Klasa D - 224 - 239 (224.0.0.0 - 239.255.255.255) -> subnet nema jer ovde bi bila multicast 

Klasa E - 225-254 (225.0.0.0 - 254.255.255.255) -> Enperimentalne, one se ne koriste 


Na osnovu prvog kvarteta mozemo da dredimo kojoj klasi pribada.


Na primer kada menjamo IP adresu, moze se desiti da racunar sam upise subnet masku koju pripada.


Sta je CIDR (CID Rotacion)
predstavlja koliko imamo nule u subnetmasci
Recimo u prvoj klasi imamo 8 nije u adresi.



Subnet odredjuje koliko netvorka imamo u njemu.

1 klasa imamo 2na 24 imamo ogroman broj
Mask adresa ima 32 bit sto bi omobucavalo da imamo priblizno 4.3milijardi Adressa, nekad su mislili da se nece nikad potrositi ali imak jeste a sada imam IPv6 koji ima 128bit

A host deo koliko imamo kostova u subnet delu

-----------------------------

u adresu 255.255.255.0 - Celo je network a kvartet nula je host


Ono sto je u pocetku subnet postojalo je da smo imali samo Classfull Networks (/8 /16 /24)

Generalno da se nije odradila promena i nesto novo izmislilo te public adrese bi se mnogo mnogo brze potrosile, jer sada su imali

/8 - imali smo 16.000 hostova
/16 - imali i - 65536 ahrese
/24 -  imali bi 24 adresa


Recimo ako nam neko trazi 10 adresa, mogli bi da mu damo /24 subnet

a ako bi nam neko trazio 300IP adresa dali bi mu /16

Ali di nam tako jako brzo ponestalo adresa za dodeljivanja tako je nastalo

CIDR - koji je classless - koji omogucava da pomeramo ozvan klasne liste.


recimo da nam treba sad 10 IP addresa

124                |   2/8 -256
225.225.225.1111   |0000 0000


omogucava da prenesemo recimo 4 bit 
128                |   2/8 -256
225.225.225.1111   |    0000









Takodje postoje NAT 
I Privatne IP Adrese

Za privatni opseg adresa napravljen je RFC1918
opseg je
Klase A - 10.0.0.0 -> 10.255.255.255
Klasa B - 172.16.0.0 -> 172.31.255.255
Klasa C - 192.168.0.0 -> 192.160.255.255

recimo kada dobijemo Ruter od providera imamo recimo 192.168.0.6

takodje mozemo da koristimo /24


Kako je moguce da vise nas koristimo isti opseg, to je zato sto ne mozemo da izadjemo na internet, da bismo to mogli potrebno je da je IP adresa NAT-uje

Svaki ISP blokira ima access listu IP adresa privatne klase, koje blokiraju da pristupe internetu.

Time sprecava da vise racunara na internetu imaju istu IP adresu.


-----------------


Vazno Privatne IP Adrese je produzilo vek trajanja IPv4 kao i NAT-ovanje. 

Jer omogucavaju da recimo 200 racunara pristupi internetu sa 1 IP adreseom.

Bublic IP adresa nije isto sto i Gateway. gateway je adresa koja je na ruteru koji treba da pristupa internetu,tj ISP provajderu.


kako router handluje kome sta treba, zato sto nas racunar generije source porto, i na osnovu tu port adresi salje pakete.

--------
NAT - je izvorni naziv kada je nastao
PAT - je ono sto je zapravo (Port-ovanje) ali je naziv ostao


------------------------
Subnet-ovanje

Kada bismo radili subnetovanje - kada bismo dobili neki opseg public ip adresa od ISP provajdera i zelimo da ih iskoristimo za vise opsega.

192.169.0.0/24


Imamo router i na njega prikljuceni LAN1-4 svaki od njih treba da ima 50 racunara tj po 50 IP dresa


u ovim opsegom koji smo dobili imamo 256 adresa, ali ovaj opseg mozemo da dodelimo samo jednim LAN-u, ali sta je sa ostalima. morali bi ponovo da uzmemo drugi od ISP provajdera.

drugo je svakom VLAN nam treba 50 adresa i imamo 260, te bi to bilo previse skupo.

Sta subneting to je kada iz jedne mreze pretvaramo u nekoliko manje mreze.


Tako sto pozamljujemo bit-ove iz host dela i time smanjujemo broj racunara hostova.


Najlaksi korak je u tri koraka da se radi subnetovanje.

1 korak da mrezu 192.169.0.0/24 podelimo na onoliko delova koliko nam treba, u nazem slicaju treba nam 4 podmreze

trebam da vidimo koliko bit-a iz host dela treba da pozajmim da nam bude 4 mreze.
2 na 2 je 4, sto zanci nam treba 2 bit-a

2. Korak je da da napravimo nasu subnet masku

imamo 
						   Inicialna 
11111111.11111111.11111111.00000000.
			Networks	  | Host

Kada pozajmimo 2 bit-a iz host dela bice
						   Inicialna 
11111111.11111111.11111111.11 000000.
			Networks	  |  | Host

sto nam ostaje /26

2 na 6 daje nam 64, znaci svaki mreza bi imala 64 Adrese.


Staka od ovih mreza mora da ima mreznu adresu - Network adresu, Za nasu glavnu to bi bila 0.0

Mora da ima mreznu adresu i bradcast adresu.

Pravilan pormula da racunanje subnetovanje bi bila za validan broj adresa recimo 2na 6 - 2, jed je potrebno i adresa za Network i jedna za Broadcast.



3 Korak - prva adresa bi bila 

sad nam je potreban dekrament

izmeno najmanju vrednost ucetvrdom oktetu 1100000000

druga jedinica ima vrednost 64

1 Mreza : 192.268.0.0/26
2 Mreza : 192.168.0.64/26
3 Mreza : 192.168.0.128/26
4 Mreza : 192.168.0.192/26



sada nam je potrebno za saznamo koje su to valide iP adrese koje mozemo da dodeljujemo racunarima


Vazno potrenno ma je Netwoork IP adres  i Broadcast adresa.



za 1 Mrezu
Broadcast IP adresa bi bila zadnja adresa u toj mrezi.
Netvork : 192.168.0.0/26
Broadcast : 192.168.0.63
Validne : 192.168.0.1 - 62

Tako da nam ostale adresu ostaju validne ip adrese
Mreza 2
Netvork : 192.168.0.64/26
Broadcast : 192.168.127.63
Validne : 192.168.0.65 - 126


Mreza 3
Netvork : 192.168.0.128/26
Broadcast : 192.168.0.191
Validne : 192.168.0.129 - 190

Mreza 4
Netvork : 192.168.0.192/26
Broadcast : 192.168.0.255
Validne : 192.168.0.193 - 254


Za zadnju mrezu kada saberemo dostupni opseg ispada 256, time se oduzima od zadnje moguce 255-1 = 254


-----------------------

Primer adrese imamo 216.21.5.0/24


imamo 3 rutere i pet vlan mreza


Dakle bilo bi nam potrebno 2na3 = 8 imacemo 8 mreza iako cemo da koristimo samo 5.
dakle uzimo t bita iz adrese

						   Inicialna 
11111111.11111111.11111111.111 00000.
			Networks	  | Host

tako sa imamo 2na5 - 2 = 32-2 = 30 
svaka nasa mreza moze da ima 30 IP adresa.


sad da vidimo nase mreze


- koristimo inkrement 32 da dalje
1 Mreza 216.21.5.0/27   V- 216.21.5.1-30  B-216.21.5.31/27
2 Mreza 216.21.5.32/27  V- 216.21.5.33-62  B- 216.21.5.63
3 Mreza 216.21.5.64/27  V- 216.21.5.65-94  B- 216.21.5.95
4 Mreza 216.21.5.96/27  V- 216.21.5.97-126 B- 216.21.5.127
5 Mreza 216.21.5.128/27 V- 216.21.5.125-158  B- 216.21.5.159

6 Mreza 216.21.5.160/27
7 Mreza 216.21.5.192/27
8 Mreza 216.21.5.224/27
9 Mreza 216.21.6.0 



Nama je ovde potrebno 5 mreza i imacemo 3 dodatne mreZe  ako nam bude potrebno za prosirenje firme.

----------------------------


195.5.20.0/24 - treba nam 50 podmreze

1 Korak - za 50 podmreza treba ma 2na6 = 64

2. Korak
						   Inicialna 
11111111.11111111.11111111.11111100.
			Networks	  | Host

tako da imamo 2 na drudi = 4 -2 = 2 svaki mreza imace 2 ip drese


3 Korak
1 Mreza : 195.5.20.0/30  V-  195.5.20.1-2  B-  195.5.20.3
2 Mreza:  195.5.20.4/30  V-   195.5.20.5-6  B-  195.5.20.7

I tako dalje



--------------------
150.5.0.0/16 - treba nam 100 podmreza


1. Korak - treba nam 2na7 - 128bit

2. Korak 

				 Inicialna 
11111111.11111111.1111111  0.0000000.  /23
	Network 	 | host   |

2 na 9-2 = 512-2 = 510 adresa


3.Korak
1Mreza- 150.5.0.0/23  V- 150.5.0.1-1.254  B- 150.5.1.255
2Mreza 150.5.2.0/23   V- 
3Mreza 150.5.4.0/23
4Mreza 150.5.6.0/23



u ovim slicajevima kada je subnet maska/24 150.5.1.0

samo zadnji oktet subnetmaske kada su /23 ili /22
oba okteta mogu da budu validne adrese 


10.0.0.0/8 - za 1000 adresa

1korak - treba nam 2na10 = 1024bit

2Korak 

				 Inicialna 
11111111.11111111.11  000000.0000000.  /18
	Network 	 | host   |

2na 14-2 = 16.384-2 = 16.382


3korak
 Network
10.0.0.0/18   V-10.0.0.1-10.0.63.254      B- 10.0.63.255
10.0.64.0/18  V-10.0.64.1-10.0.129.254    B- 10.0.127.255 
10.0.128.0.18 V-10.0.128.1-10.0.191.254  B- 10.0.191.255





ZADACI
========================================

1) Zadatak 200.1.1.0/24 - za 40 podmreze

1 Korak - za 40 podmreza treba ma 2na6 = 64


2. Korak
						   Inicialna 
11111111.11111111.11111111.111111 00.
			Networks	  | Host

tako da imamo 2 na drudi = 4 -2 = 2 svaki mreza imace 2 ip drese

3 Korak
1 Mreza : 200.1.1.0/30  V-  200.1.1.1-2  B-  200.1.1.3
2 Mreza:  200.1.1.4/30  V-   200.1.1.5-6  B-  200.1.1.7

I tako dalje









2) Zadatak 199.9.10.0/24 - za 14 podmreze
1 Korak - za 14 podmreza treba ma 2na4 = 16

2Korak
						   Inicialna 
11111111.11111111.11111111.1111 0000.
			Networks	  | Host

3 Korak
1 Mreza : 199.9.10.0/28  V-  199.9.10.1   B- 199.9.10.15
2 Mreza:  199.9.10.16/28  V-   199.9.10.4  B- 199.9.10.31

I tako dalje






3) Zadatak 170.5.0.0/16 - za 1000podmreza
1korak - treba nam 2na10 = 1024bit

2Korak 

				 Inicialna 
11111111.111111   00.00000000.00000000.  /16
	Network      | host   |

2na 16-2 = 65.536-2 = 65534


3korak
 Network

170.5.0.0/16    V-10.0.0.1-10.0.63.254      B- 10.0.63.255

170.5.0.16/16    V-170.5.0.17-170.5.0.30     B- 170.5.0.31
170.5.0.32/16    V-170.5.0.33-170.5.0.46     B- 170.5.0.47 
170.5.0.48/16    V-170.5.0.49-170.5.0.62     B- 170.5.0.63






4)12.0.0.0/8 - 12 podmreza

1. Korak 2⁴ = 16 ✅
11111111.1111  0000.00000000.00000000


1 Mreza 12.0.0.0/12  V-12.0.0.1-12.15.255.254  B- 12.15.255.255
2 mreza 12.16.0.0/12 V- 12.16.0.1 - 12.31..255.254 - 12.331.255.255


















