
# CCNA – Uređaji pre switch-eva, switch-evi, ruteri i wireless (2. čas)

Ovaj dokument sadrži beleške sa drugog časa CCNA kursa. Fokus je na razvoju mrežnih uređaja (Hub → Bridge → Switch), osnovama rutiranja, wireless mrežama i firewall-ima.

---

## 📜 Uređaji pre switch-eva – HUB

Pre pojave switch-eva koristili su se **HUB-ovi**.

### Karakteristike HUB-a
- Funkcija: povezivanje uređaja u mrežu
- Nisu inteligentni uređaji
- Rade kao **repeater (pojačivač signala)**
- Paket koji primi:
  - Šalje **na sve portove**
- Ne zna kome je paket namenjen
- Radi na **OSI Layer 1 (Physical Layer)**

### Mane HUB-a
- Ne razume protokole
- Ne razume adrese
- Svi portovi su u:
  - **Istom collision domenu**
  - **Istom broadcast domenu**
- Deljenje bandwidth-a:
  - Ako je HUB 100 Mb/s i ima 5 računara → svaki dobija ~20 Mb/s

---

### Collision Domain i Half-Duplex
- **Collision domain**:
  - Ako dva uređaja šalju podatke u isto vreme → dolazi do kolizije
- HUB radi u **Half-Duplex** režimu
  - U jednom trenutku ili šalje ili prima podatke

---

### Ethernet i CSMA/CD
- Standard: **Ethernet (IEEE 802.3)**
- Mehanizam: **CSMA/CD**
  - Carrier Sense
  - Multiple Access
  - Collision Detection
- Kada se desi kolizija:
  - Svi prestaju sa slanjem
  - Uređaji čekaju nasumično vreme
  - Ponovo pokušavaju slanje

---

### Bezbednosni problemi HUB-a
- Svi uređaji primaju sve pakete
- Sniffing alati (Wireshark) lako hvataju podatke
- FTP / Telnet lozinke se vide kao plain text
- Nepotrebno opterećenje mreže

Primer:
- Fajl od 100 MB
- MTU = 1500 B  
→ oko **70.000 paketa** koji se šalju svim uređajima

---

## 🌉 Bridge – prelazno rešenje

Nakon HUB-ova pojavili su se **Bridge uređaji**.

### Karakteristike Bridge-a
- Rade na **OSI Layer 2**
- Prepoznaju **MAC adrese**
- Deli mrežu na segmente
- Manje kolizija nego kod HUB-a

### MAC adresa
- Jedinstvena hardverska adresa
- Dužina: **48 bitova (6 bajta)**
  - Prvih 24 bita – proizvođač
  - Drugih 24 bita – jedinstveni broj
- Može se:
  - Promeniti
  - Maskirati (MAC spoofing)

### Mana Bridge-a
- Softverska obrada paketa
- Vremenom postaju spori

➡️ Rešenje:
- Prelazak na hardversku obradu  
- **ASIC čipovi**  
- Nastanak **switch-eva**

---

## 🔀 Switch

### Osnovna uloga
- Povezivanje uređaja unutar mreže
- Radi na **OSI Layer 2**
- Prosleđuje pakete na osnovu **MAC adresa**

---

### MAC (CAM) tabela
- Čuva:
  - MAC adresu
  - Port
- Tabela je u **RAM memoriji**
- Nakon restartovanja:
  - Tabela je prazna
- MAC zapisi se brišu posle ~5 minuta neaktivnosti

---

### Kako switch uči MAC adrese
- Switch uči **isključivo iz Source MAC adrese**
- Ako ne zna Destination MAC:
  - Ponaša se kao HUB
  - Šalje paket na sve portove (flooding)

Struktura Ethernet frame-a:
| Preamble | S-MAC | D-MAC | DATA |



---

### Prednosti switch-eva
1. Svaki port je **zaseban collision domain**
2. **Full-Duplex** komunikacija
3. Maksimalni bandwidth po portu
4. Veća bezbednost od HUB-a

---

### VLAN (osnovno)
- Podrazumevano:
  - Svi portovi su u **VLAN 1**
- Kasnije:
  - Segmentacija mreže pomoću VLAN-ova

---

### Tipovi switch-eva
#### Neupravljivi (Unmanaged)
- Plug & Play
- Kućna upotreba
- Ne mogu sprečiti loop petlje

#### Upravljivi (Managed)
- Port security
- VLAN
- STP (sprečavanje petlji)
- Kontrola saobraćaja

---

### Switch stacking (Cisco)
- **StackWise** tehnologija
- Više switch-eva rade kao jedan
- Jedan je **master**
- Master se bira po:
  - MAC adresi
  - Ili ručno (preporučeno)

---

## 🌐 Layer 2 vs Layer 3
- **Layer 2**:
  - MAC adrese
- **Layer 3**:
  - IP adrese
  - Rutiranje
  - Napredne funkcije

---

## 🚦 Router

### Uloga routera
- Povezuje **različite mreže**
- Omogućava pristup internetu
Switch → Router → Internet


### Osnovne osobine
- Svaki interface = posebna mreža
- Routing tabela:
  - Po defaultu prazna
- Cisco router:
  - Svi portovi su po defaultu **DOWN**

---

### Routing tabela – primer
192.168.0.0/24 → G0/0
192.168.1.0/24 → G0/1
192.168.10.0/24 → G1/1



Router:
- Gleda **destination IP**
- Upoređuje sa routing tabelom
- Prosleđuje paket odgovarajućim interfejsom

---

### Default ruta
- `0.0.0.0/0`
- Koristi se za internet
- Paket se prosleđuje ISP-u

---

## 📢 Broadcast domain
- Router razdvaja broadcast domene
- ARP i DHCP broadcast:
  - Ne prolaze kroz router

### Tipovi komunikacije
- **Unicast** – 1 na 1
- **Multicast** – 1 na više
- **Broadcast** – 1 na sve

---

### Osnovni mrežni parametri računara
- IP adresa
- Subnet maska
- Default gateway (IP routera)

⚠️ IP i gateway moraju biti u istoj mreži

---

## 📡 Wireless Access Point (AP)

### Uloga AP-a
- Bežično povezivanje uređaja
- Prevod:
  - **802.11 (Wi-Fi)** ↔ **802.3 (Ethernet)**

### Tipovi AP-a
- **Standalone AP**
- **Lightweight AP (LAP)**
- **Wireless Router (SOHO)**

---

### Frekvencije
- 900 MHz
- 2.4 GHz
- 5 GHz

### 2.4 GHz kanali
- Ukupno 14 kanala
- Nepreklapajući:
  - **1, 6, 11**
- Preklapanje = manji bandwidth

---

### CSMA/CA (Wi-Fi)
- Collision Avoidance
- RTS – Request To Send
- CTS – Clear To Send

---

### Wi-Fi standardi
- 802.11b
- 802.11a
- 802.11g
- 802.11n
- **802.11ax (Wi-Fi 6)** – 9.6 Gb/s
- **802.11be (Wi-Fi 7)** – do 46 Gb/s  
  - Multi-link (više frekvencija istovremeno)

---

## 🎛️ Wireless LAN Controller (WLC)
- Centralna kontrola AP-ova
- Koristi se kod velikog broja AP-ova
- LAP se konfigurišu isključivo preko WLC-a
- Omogućava seamless roaming

---

## 🔥 Firewall (osnovno)

### Uloga firewall-a
- Dozvoljava ili blokira saobraćaj
- Stateful inspekcija
- Filtriranje paketa

### Cisco ASA Firewall
- Po defaultu:
  - Sve blokira
  - Dozvoljava samo definisana pravila

### Firewall vs Router
- Router:
  - Dozvoljava sve
  - Blokira samo ono što mu kažemo
- Firewall:
  - Blokira sve
  - Dozvoljava samo dozvoljeno

---

### Firewall modovi
#### Router Mode
- Layer 3
- NAT + routing

#### Transparent Mode
- Layer 2
- Nevidljiv u mreži

---

### Security Levels
- Inside: 100
- DMZ: 50
- Outside (Internet): 0

Saobraćaj:
- Viši → niži level = dozvoljen
- Niži → viši level = blokiran

---

### Moderne FW funkcije
- IDS – Intrusion Detection System
- IPS – Intrusion Prevention System
- Zaštita od:
  - DHCP spoofing
  - Kali Linux napada
  - Malware-a

---

## ✅ Zaključak
Ovaj čas pokriva temeljno razumevanje:
- Razvoja mrežnih uređaja
- Funkcionisanja switch-eva i rutera
- Wireless mreža
- Osnova mrežne bezbednosti




















