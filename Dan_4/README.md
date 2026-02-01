

# CCNA – IANA, MTU, fizički sloj, kablovi i topologije (Novi čas)

Ovaj dokument pokriva ulogu IANA organizacije, dodelu IP adresa, MTU i segmente, brzine prenosa, fizički sloj mreže, prenosne medijume, kablove, konektore, topologije i Ethernet standarde.

---

## 🌍 IANA – Internet Assigned Numbers Authority

**IANA** je globalna organizacija zadužena za:
1. Dodelu **javnih (public) IP adresa**
2. Upravljanje **DNS root zonama**  
   (.com, .org, .gov, .net…)
3. Upravljanje **well-known portovima**

⚠️ IANA **ne dodeljuje IP adrese krajnjim korisnicima**.

---

## 🌐 Hijerarhija dodele IP adresa

1. **IANA**
2. **RIR – Regional Internet Registry**
3. **ISP – Internet Service Provider**
4. **Krajnji korisnici**

### RIR organizacije
| RIR | Region |
|---|---|
| ARIN | Severna Amerika |
| RIPE NCC | Evropa |
| APNIC | Azija / Australija |
| LACNIC | Južna Amerika |
| AFRINIC | Afrika |

---

### NIR – National Internet Registry
- Postoje u pojedinim državama
- Nalaze se između RIR-a i ISP-a
- Primeri zemalja:
  - Kina
  - Japan
  - Južna Koreja
  - Brazil

---

## 📦 MTU i segmentacija paketa

- **MTU (Maximum Transmission Unit)**  
  → maksimalna veličina paketa koju mrežna kartica podržava

### Ethernet MTU
- Standardno: **1500 bajtova**
- Data payload ~1400B
- Ostatak čine IP i TCP headeri

### Primer
- Fajl od **200 MB**
- Deli se na segmente od **1500 B**
- Svaki segment se prenosi posebno

---

## 🚀 Jumbo Frames

- MTU do **9000 B**
- Prednosti:
  - Brži prenos velikih fajlova
  - Manje overhead-a
- Koriste se u:
  - Data centrima
  - NAS sistemima

⚠️ Svi uređaji moraju podržavati Jumbo Frames:
- NIC
- Switch
- Router

Mogu se podesiti:
- Globalno
- Po pojedinačnom portu

---

## 🔀 Multipleksiranje i reordering

- **Multipleksiranje**:
  - Više uređaja koristi isti medijum naizmenično
- Paketi mogu stići **neuređenim redosledom**
- Na odredištu se vrši:
  - **Reordering (preuređivanje segmenata)**

---

## 🔢 Bit i Byte

- **1 Byte = 8 bitova**
- Računari rade sa **byte-ovima**
- Brzine se izražavaju u **bitovima**


Primer:


---

### Hijerarhija veličina


5 B = 40 b
1 TB = 1024 GB
1 GB = 1024 MB
1 MB = 1024 KB
1 B = 8 b


---

### Primer prenosa fajla

- Fajl: **8 MB**
- Brzina: **100 Mb/s**

8 MB × 8 = 64 Mb
64 Mb / 100 Mb/s = 0.64 s


✔️ **Megabiti** → brzina  
✔️ **Megabajti** → veličina fajla

---

## ⚡ Fizički sloj – ključni pojmovi

### Bandwidth (propusni opseg)
- Brzina koju plaćamo provajderu
- Primer: 20, 50, 100 Mb/s

### Throughput
- Stvarna brzina prenosa
- Meri se:
  - Speedtest
  - iPerf

Primer:
- Kartica podržava samo 2.4 GHz → manji throughput
- 5 GHz → veći throughput

---

### Latencija
- Kašnjenje paketa (ms)
- U LAN mreži:
  - Idealno < **1 ms**
- Veća latencija znači:
  - Zagušenje
  - Lošu opremu

#### Tipovi latencije
- **One-way latency**
- **Round-trip time (RTT)**

---

## 🧪 Ping, Traceroute i TTL

- **Ping** – proverava dostupnost
- **Traceroute** – prikazuje put do destinacije

### TTL (Time To Live)
- Svaki ruter smanjuje TTL za 1
- Kada TTL = 0:
  - Paket se odbacuje
  - ICMP šalje *Time Exceeded*

⚠️ Sprečava beskonačne petlje u mreži

---

## 🔁 Loop problemi

- **Layer 2 loop**:
  - Može izazvati totalnu zagušenost
- **Layer 3 uređaji**:
  - Kontrolišu petlje (TTL, routing)

---

## 🔌 Prenosni medijumi

### Žični
- UTP / FTP / STP (upredene parice)
- Koaksijalni kabl
- Optički kabl

### Bežični
- Wi-Fi
- Radio talasi

---

## 🧵 UTP / FTP / STP kablovi

- Maksimalna dužina: **100 m**
- Kategorije:
  - Cat5 → 100 Mb/s
  - Cat5e → 1 Gb/s
  - Cat6 → 10 Gb/s

### Razlike
- **UTP** – bez zaštite
- **STP** – metalna zaštita (otporniji)
- **FTP** – osnovna zaštita

---

## 🌈 Optički kablovi

- Prenos putem **svetlosti**
- Otporni na elektromagnetne smetnje

### Tipovi
#### Single-mode (9/125)
- Laser
- Velike distance (10+ km)
- ISP, data centri

#### Multi-mode (50/125)
- LED
- Kraće distance
- LAN, zgrade

---

### Simplex & Duplex
- **Simplex** – jedan smer
- **Duplex** – dva vlakna (TX/RX)

---

## 🔗 Fiber konektori

- Patch panel: **ST**
- Router/Switch: **SFP**
- LC konektori:
  - TX – narandžasti
  - RX – crveni

⚠️ Kabl + SFP moraju podržavati istu brzinu (npr. 10G)

### DAC kabl
- Sve u jednom
- Kratke distance
- 10G / 25G / 40G

---

## 🔌 RJ-45 standardi

- TIA/EIA 568A
- TIA/EIA 568B

### Tipovi kablova
- **Straight-through** – isti raspored
- **Crossover** – ukršten

✔️ Moderni uređaji imaju auto-MDI/MDIX

---

## 🖧 Konzolni kabl

- Za inicijalno podešavanje uređaja
- Ranije: RJ-45 → DB-9
- Danas: USB → RJ-45

⚠️ Ako su povezani RJ-45 i USB → USB ima prioritet

---

## 🧠 Topologije mreže

### Bus topologija
- Jedan koaksijalni kabl
- 10Base5
- Terminatori na krajevima
- Problem:
  - Kolizije
  - Kvar kabla ruši celu mrežu

### Token Ring
- Prsten
- Token Passing
- Bez kolizija

### Star topologija
- Centralni uređaj (switch)
- Najčešće korišćena danas

---

## 🔄 Auto-negotiation

Switch-evi pregovaraju o:
- Brzini (10M / 100M / 1G / 10G)
- Duplex-u (Half / Full)

Ako jedan uređaj ne podržava opciju:
- Oba prelaze na niži zajednički nivo

⚠️ Loš kabl → Half-duplex → packet loss

---

## 📡 Ethernet i IEEE 802.3

- IEEE 802.3 standard
- LAN i MAN mreže
- Definiše:
  - L1
  - Donji deo L2

Ethernet = IEEE 802.3

---

## 🆔 MAC adresa

- 48 bita (6 bajtova)
- Hexadecimalni zapis (0–9, A–F)

Primeri:
- Cisco: `0060.ba31.ab19`
- Windows: `A8-B1-3B-7B-14-B3`

Svaki hex karakter = **4 bita**

---

## 🧩 Ethernet okvir (Frame)

- Preambula – sinhronizacija
- MAC adrese
- Type / Length polje
- Data
- FCS

### PAD polje
- Ako je data < 46 B
- Dopunjava se do minimuma

### Type / Length
- < 0x600 → Length
- ≥ 0x600 → Type

---

## ✅ Zaključak

Ovaj čas pokriva:
- Globalnu dodelu IP adresa
- MTU i segmentaciju
- Brzinu i latenciju
- Kablove i konektore
- Topologije i Ethernet standarde

Osnova za razumevanje **fizičkog i data-link sloja** CCNA mreža.




