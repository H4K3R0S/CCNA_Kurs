

# CCNA – Tipovi komunikacije, OSI/TCP-IP modeli i tok paketa (3. čas)

Ovaj dokument sadrži beleške sa trećeg časa CCNA kursa. Fokus je na tipovima mrežne komunikacije, OSI i TCP/IP modelima, protokolima, portovima i načinu na koji paket putuje kroz mrežu i internet.

---

## 🔄 Tipovi mrežne komunikacije

### 1. Unicast (1 → 1)
- Komunikacija jedan prema jedan
- Najčešći tip komunikacije
- Primer:
  - PC1 ↔ PC2 (preko switch-a)

---

### 2. Multicast (1 → više)
- Jedan uređaj šalje podatke ka više određenih uređaja
- Koriste ga ruteri i routing protokoli

Primer:
- **OSPF routing protokol**
- Multicast adrese:
  - `224.0.0.5`
  - `224.0.0.6`

Ruteri koriste ove adrese za međusobno slanje routing update-a.

---

### 3. Broadcast (1 → svima)
- Poruka se šalje svim uređajima u mreži
- Primeri:
  - **ARP** – pronalaženje MAC adrese na osnovu IP adrese
  - **DHCP** – dobijanje mrežnih parametara

⚠️ Router ne prosleđuje broadcast poruke (razdvaja broadcast domene)

---

### 4. Anycast (1 → najbliži)
- Najčešće se koristi u **cloud okruženjima**
- Primer:
  - AWS, CDN servisi
- Korisnik se povezuje sa **geografski najbližim serverom**
- Prednost:
  - Manja latencija
  - Brži odziv sajta

---

## 🧱 OSI Model (7 slojeva)

| Sloj | Naziv |
|----|------|
| L7 | Application |
| L6 | Presentation |
| L5 | Session |
| L4 | Transport |
| L3 | Network |
| L2 | Data Link |
| L1 | Physical |

---

## 🌐 TCP/IP Model

| TCP/IP sloj | Odgovarajući OSI slojevi |
|------------|-------------------------|
| Application | L7, L6, L5 |
| Transport | L4 |
| Internet | L3 |
| Network Access | L2, L1 |

- TCP/IP model je stariji i **aktivno se koristi**
- Pogodan za **troubleshooting**
- Paket prolazi:
  - Od L7 ka L1 (enkapsulacija)
  - Od L1 ka L7 (de-enkapsulacija)

---

## 📦 Terminologija
- **Layer 2** → Frame
- **Layer 3** → Packet
- **Layer 4** → Segment

---

## 🛒 Primer iz prakse – Web kupovina

### Application Layer (L7)
- Web browsing
- HTTP / HTTPS
- YouTube, online kupovina, društvene mreže

---

### Presentation Layer (L6)
- Formatiranje podataka:
  - HTML
  - PHP
  - Slike, video
- Enkripcija:
  - SSL / TLS

Uloge:
1. Da obe strane razumeju format podataka
2. Enkripcija komunikacije

---

### Session Layer (L5)
- Održava sesiju između:
  - Browsera
  - Web servera

⚠️ U TCP/IP modelu L5–L7 su objedinjeni u jedan sloj

---

## 🚚 Transport Layer (L4)

### Glavne funkcije
- Izbor protokola
- Upravljanje portovima

Aplikacije određuju:
- Koji protokol se koristi
- Koji port se koristi

---

### TCP vs UDP

#### TCP (Transmission Control Protocol)
- Pouzdan protokol
- Garantuje isporuku podataka
- Segmentacija podataka
- ACK potvrde za svaki segment
- Koriste ga:
  - HTTPS
  - MySQL
  - Email servisi

---

#### UDP (User Datagram Protocol)
- Brži, ali nepouzdan
- Nema potvrde isporuke
- Koristi se za:
  - VoIP
  - Streaming
  - Online igre

---

## 🔢 Portovi

- Portovi omogućavaju:
  - Više aplikacija
  - Više tabova u browseru
- Operativni sistem generiše **source port**
- Raspon portova:
  - 0 – 65.535

Primer:
- HTTPS koristi **destination port 443**
- Source port se dinamički dodeljuje (npr. 4444)

Jedan tab u browseru:
- Može koristiti više source portova
- Ako se portovi iscrpe → ne mogu se otvoriti novi tabovi

---

## 🌍 Network Layer (L3)

- Logičko adresiranje
- Source IP i Destination IP
- **End-to-End komunikacija**
- IP adrese se ne menjaju tokom puta

### NAT (izuzetak)
- Kada izlazimo na internet
- Privatna IP → Javna IP

Primer:
192.168.1.10:3333 ↔ 212.5.6.7:3333


---

## 🔗 Data Link Layer (L2)

- Hop-to-Hop komunikacija
- Koristi:
  - MAC adrese
- Standardi:
  - Ethernet
  - MPLS
  - Point-to-Point

MAC adrese se menjaju na svakom hop-u, IP adrese ostaju iste.

---

## ⚡ Physical Layer (L1)
- Pretvaranje podataka u:
  - 0 i 1
- Prenos preko:
  - Kablova
  - Optike
  - Bežičnih talasa

---

## 🧮 FCS i CRC

- **FCS (Frame Check Sequence)**
- Koristi CRC algoritam
- Proverava:
  - Integritet paketa

Greške mogu nastati zbog:
- Loših kablova
- Predugačkih linkova
- Man-in-the-Middle napada

---

## 📦 Enkapsulacija i de-enkapsulacija
- Dodavanje zaglavlja (L7 → L1)
- Skidanje zaglavlja (L1 → L7)
- Ovo je proces prolaska paketa kroz OSI slojeve

---

## 🌐 Kako funkcioniše Internet

- Lokalna mreža → Router → ISP
- ISP routeri su povezani međusobno
- Protokol između ISP-a:
  - **BGP**

### IP adrese
- Dinamička IP (default)
- Statička IP (plaća se)
  - Serveri
  - Kamere
  - Hosting

---

## 🌎 Dynamic DNS (DDNS)

- Rešenje za dinamičke IP adrese
- Servisi:
  - No-IP
  - DynDNS

Primer:
camera.ddns.net
webserver.ddns.net


Ime ostaje isto, IP se menja automatski.

---

## 🏗️ Principi dizajna mreže

### 1. Otpornost (Redundancy)
- Alternativne rute
- EtherChannel (više linkova kao jedan)

---

### 2. Skalabilnost
- Lako proširenje mreže
- Dodavanje switch-eva bez prekida rada

---

### 3. QoS – Quality of Service
- Po defaultu isključen
- Dodeljuje prioritete saobraćaju

Primer:
- VoIP ima prioritet nad YouTube saobraćajem

---

### QoS metode
- **FIFO** – First In First Out (loša opcija)
- **LLQ** – Low Latency Queuing (preporučeno)

---

## ✅ Zaključak
Treći čas daje razumevanje:
- Kako paket putuje kroz mrežu
- Uloge OSI i TCP/IP modela
- Razlike TCP i UDP protokola
- Osnova rada interneta i QoS-a






