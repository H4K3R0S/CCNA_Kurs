
# 🌐 Network Layer – IP Adresiranje i Subnetovanje

Ovaj dokument pokriva:
- Network sloj (Layer 3)
- IPv4 i IPv6
- IANA i dodelu IP adresa
- NAT i privatne opsege
- CIDR
- Subnetovanje sa primerima i zadacima

---

# 📌 Network Layer (OSI Layer 3)

Glavna uloga Network sloja je:

- Logičko adresiranje (IP adrese)
- Rutiranje paketa između mreža
- Enkapsulacija paketa
- Određivanje najbolje rute

Glavni protokoli:
- **IP (Internet Protocol)**
- **ICMP (Internet Control Message Protocol)**

---

# 🌍 IP Protokol

Postoje dve verzije:

## IPv4
- 32-bitna adresa
- Primer: `192.168.1.1`
- Ukupno: ~4.3 milijarde adresa

## IPv6
- 128-bitna adresa
- Primer: `2001:0db8::1`
- Ogroman broj dostupnih adresa

---

# 🌎 IANA i dodela IP adresa

**IANA (Internet Assigned Numbers Authority)** upravlja globalnim IP adresnim prostorom.

2011. godine ostala je bez slobodnih IPv4 adresa.

Hijerarhija dodele:

1. IANA  
2. RIR (Regional Internet Registry)  
3. ISP  
4. Krajnji korisnici  

---

# 🌐 CGNAT (Carrier-Grade NAT)

CGNAT omogućava da više korisnika deli jednu javnu IP adresu.

Prepoznaje se po opsegu:

100.64.0.0/10


Karakteristike:
- Duplo NAT-ovanje
- Ne može se hostovati server
- Ako IP bude blokirana → svi korisnici su blokirani

Provera:
- Pogledati WAN IP na ruteru
- Uporediti sa sajtom tipa whatismyip

Ako se ne poklapaju → koristiš CGNAT.

---

# 📘 Format IPv4 adrese

IPv4 ima:

- 32 bita
- 4 okteta
- Svaki oktet: 8 bita
- Opseg po oktetu: 0–255

Primer:
192.168.20.1


---

# 🔢 Binarni sistem

Tabela vrednosti:

|128|64|32|16|8|4|2|1|

Primer:
192 = 128 + 64 = `11000000`

---

# 📚 IPv4 klase (Classful)

| Klasa | Opseg | Default maska |
|-------|--------|---------------|
| A | 1–126 | 255.0.0.0 (/8) |
| B | 128–191 | 255.255.0.0 (/16) |
| C | 192–223 | 255.255.255.0 (/24) |
| D | 224–239 | Multicast |
| E | 240–255 | Eksperimentalne |

⚠️ Danas se koristi **CIDR (classless)** adresiranje.

---

# 📌 Privatne IP adrese (RFC1918)

| Klasa | Opseg |
|--------|--------|
| A | 10.0.0.0/8 |
| B | 172.16.0.0 – 172.31.255.255 (/12) |
| C | 192.168.0.0/16 |

Privatne adrese ne mogu direktno na internet bez NAT-a.

---

# 🔁 NAT vs PAT

- NAT – Network Address Translation
- PAT – Port Address Translation (najčešće korišćen)

Omogućava:
- 200 računara → 1 javna IP adresa

Gateway ≠ Public IP  
Gateway je adresa rutera u lokalnoj mreži.

---

# 📐 CIDR

CIDR označava broj bitova mrežnog dela.

Primer:
/24 = 255.255.255.0

Formula:
2^host_bitova - 2
(-2 zbog Network i Broadcast adrese)

---

# 🔥 SUBNETOVANJE – PRIMERI

---

## Primer 1  
192.168.0.0/24  
Potrebno: 4 mreže

### Korak 1
2² = 4 → pozajmljujemo 2 bita

Nova maska:
/26
255.255.255.192

### Broj adresa po mreži:
2^6 = 64
64 - 2 = 62 validne


### Mreže:

| Mreža | Opseg | Broadcast |
|--------|--------|-----------|
| 192.168.0.0/26 | 1–62 | 192.168.0.63 |
| 192.168.0.64/26 | 65–126 | 192.168.0.127 |
| 192.168.0.128/26 | 129–190 | 192.168.0.191 |
| 192.168.0.192/26 | 193–254 | 192.168.0.255 |

---

## Primer 2  
216.21.5.0/24  
Potrebno: 5 mreža

2³ = 8 → /27

Maska:
255.255.255.224

Broj hostova:
2^5 - 2 = 30


Mreže:

- 216.21.5.0/27 (1–30)
- 216.21.5.32/27 (33–62)
- 216.21.5.64/27
- 216.21.5.96/27
- 216.21.5.128/27
- 216.21.5.160/27
- 216.21.5.192/27
- 216.21.5.224/27

---

## Primer 3  
195.5.20.0/24  
Potrebno: 50 podmreža

2⁶ = 64 → /30

Maska:
255.255.255.252

Hostovi po mreži:
2^2 - 2 = 2 hosta


Primer prve dve:
- 195.5.20.0/30 → 1–2
- 195.5.20.4/30 → 5–6

---

## Primer 4  
150.5.0.0/16  
Potrebno: 100 podmreža

2⁷ = 128

Nova maska:
/23
255.255.254.0

Hostova po mreži:
2^9 - 2 = 510


Primer:
- 150.5.0.0/23
- 150.5.2.0/23
- 150.5.4.0/23

Inkrement = 2 u trećem oktetu.

---

## Primer 5  
10.0.0.0/8  
Potrebno: 1000 mreža

2¹⁰ = 1024

Nova maska:
/18
255.255.192.0

Hostova po mreži:
2^14 - 2 = 16382


Primer:
- 10.0.0.0/18
- 10.0.64.0/18
- 10.0.128.0/18

---

# 📚 Zadaci

## 1️⃣ 200.1.1.0/24 → 40 podmreža

2⁶ = 64  
Nova maska: /30  
255.255.255.252  

---

## 2️⃣ 199.9.10.0/24 → 14 podmreža

2⁴ = 16  
Nova maska: /28  
255.255.255.240  

Hostova:
2⁴ - 2 = 14

---

## 3️⃣ 170.5.0.0/16 → 1000 podmreža

2¹⁰ = 1024  
Nova maska: /26  

---

## 4️⃣ 12.0.0.0/8 → 12 podmreža

2⁴ = 16  

Nova maska:
/12
255.240.0.0


---

# ✅ Zaključak

Danas smo prošli:

- Network Layer
- IPv4 i IPv6
- IANA i CGNAT
- Privatne IP adrese
- NAT i PAT
- CIDR
- Subnetovanje
- Kompleksne subnet zadatke

Ovo je osnova za:
- CCNA
- Network administraciju
- Enterprise mrežni dizajn

















