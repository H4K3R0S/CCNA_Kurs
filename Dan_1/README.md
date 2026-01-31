# CCNA – Osnove Networkinga (1. čas)

Ovaj dokument sadrži sređene beleške sa prvog časa CCNA kursa. Namenjen je kao **README.md** fajl za lakše učenje i ponavljanje gradiva.

---

## 📌 Uvod i resursi za učenje

- **DevNet** – Network Automation Engineer
- **Boson** – vežbanje CCNA ispita
- **9tut(e).com** – CCNA test pitanja

### Polaganje CCNA ispita
- Prijava minimum **5 dana ranije** (najkasnije dan pre ispita)
- Polaganje:
  - Online
  - U IT Centru (**preporučeno**)

---

## 🛠️ Alati i problemi
- Problemi sa instalacijom:
  - Wireshark
  - SolarWinds  
- Razlog: internet greška

---

## 🔧 Cisco uređaji – osnovna konfiguracija
- Neophodna inicijalna konfiguracija:
  - Username
  - Password
- Dalja administracija:
  - **SSH (enkriptovana konekcija – preporučeno)**

---

## 🔄 Modeli mrežne komunikacije

### Peer-to-Peer (P2P)
- Svi uređaji imaju jednaka prava
- Nema centralnog servera
- Svaki uređaj može biti klijent i server
- Primeri:
  - BitTorrent
  - Skype (ranije)
- Moguće uloge:
  - DHCP server / DHCP klijent
  - FTP klijent

---

### Client–Server
- Jedan uređaj pruža usluge (server)
- Ostali uređaji koriste te usluge (klijenti)
- Primeri servera:
  - Web server
  - Mail server
  - Database server
- Bez switch-a nema komunikacije

Primer:
- Pristup `youtube.com` → HTTP/HTTPS zahtev ka serveru

---

## 🔐 Protokoli i bezbednost

### HTTP vs HTTPS
- **HTTP**
  - Neenkriptovan
  - Podaci vidljivi u Wireshark-u
- **HTTPS**
  - Enkriptovan (TLS/SSL)
  - Preporučena opcija

---

### Telnet, SSH, FTP
| Protokol | Port | Bezbednost |
|--------|------|------------|
| Telnet | 23 | ❌ Ne |
| FTP | 20/21 | ❌ Ne |
| SSH | 22 | ✅ Da |
| SFTP | 22 | ✅ Da |

**Preporuke:**
- Administracija → SSH  
- Prenos fajlova → SFTP  

---

## 🛡️ Osnovi sajber bezbednosti
- Izbegavati HTTP sajtove
- Paziti na phishing mejlove
- Paziti na lažne domene (npr. `faceb00k.com`)
- Pretnje:
  - Trojan
  - Worm
  - Ransomware

### Pravilo 3-2-1 (Backup)
- 3 kopije podataka
- 2 različita medijuma
- 1 offline kopija

**Najbolja zaštita:**  
- Immutable backup (fajl se ne može menjati, čak ni od strane admina)

---

## 🌐 Mrežna infrastruktura

### Uređaji
- **Mrežni uređaji:**
  - Router
  - Switch
  - Access Point
  - Firewall
- **End devices:**
  - Laptop
  - Telefon
  - Štampač
  - Kamera

---

### Medijumi za prenos
- UTP (Copper)
- Fiber Optic
- Koaksijalni kabl
- Serijski kabl (T1)
- Radio frekvencija (Wi-Fi)

---

### Servisi
- DHCP
- DNS
- SSH
- FTP
- Telnet

---

## 📡 DHCP i IP adresiranje
- DHCP dodeljuje:
  - IP adresu
  - Subnet Mask
  - Default Gateway
  - DNS
- Primer mreže:
  - `192.168.1.0/24`
  - Maksimalno 254 IP adrese

### Statičke IP adrese (obavezno)
- Router
- Switch
- NAS
- Štampači
- Kamere

### Dinamičke IP adrese
- Laptopi
- Telefoni
- Privremeni uređaji

---

## 🌍 DNS – Domain Name System
- Prevodi ime domena u IP adresu
- Primer:
  - `youtube.com` → `24.1.55.12`
- Računari komuniciraju isključivo preko IP adresa

---

## 🏢 Kancelarijska mreža – praktičan primer

### MDF / Rack
- Centralni rack (MDF – Main Distribution Facility)
- Sadrži:
  - Patch panel
  - Switch
  - Router
  - ISP opremu

---

### Patch utičnice i patch panel
- RJ45 utičnice u kancelarijama
- Kablovi vode do patch panela u rack-u
- Patch kablovi (30 cm):
  - Patch panel ↔ Switch

**Važno:**
- Obeležavati kablove i portove (PC1, kancelarija, port)

---

### Organizacija kablova
- Preporučene boje:
  - Plava → switch ↔ router
  - Crvena → korisnički uređaji
- Koristiti najviše 2–3 boje

---

## ➕ Proširenje mreže
- Dodavanje switch-a u kancelariji
- Switch se povezuje na patch panel
- Uređaji se povezuju na taj switch

---

## ⚠️ Bezbednosni rizici u mreži
- Neovlašćeni switch-evi
- VLAN hopping napadi
- STP (Spanning Tree) napadi
- Mrežne petlje (loop)

### Zaštita
- Port security
- Blokada neovlašćenih portova
- Kontrola krajnjih uređaja

⚠️ Čak i običan računar može biti pretnja:
- Kali Linux
- VirtualBox
- Mogućnost rušenja mreže

---

## ✅ Napomena
Ovo su **osnove networkinga** koje predstavljaju temelj za dalje CCNA lekcije:
- VLAN
- Routing
- STP
- Security
- Automation

