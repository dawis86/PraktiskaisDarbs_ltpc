# 📄 Sociālās aprūpes iestāžu pārvaldības sistēma "Klientu Reģistrs"

> **Modulis:** EIKT produktu izstrāde - grupu darbs  
> **Mācību iestāde:** Latvijas Tālmācības un profesionālās tālākizglītības centrs  
> **Vieta/Gads:** Rīga, 2026

---

## 👥 Komandas sastāvs un lomas

| Vārds Uzvārds | Loma | Atbildība |
| :--- | :--- | :--- |
| **Dāvis Strazds** | Projekta vadītājs / Galvenais arhitekts | Tehniskā realizācija, sistēmas loģika, "Offline-first" arhitektūra. |
| **Zane Ābele** | Biznesa analītiķe | Tirgus analīze, finansiālais pamatojums, komunikācijas stratēģija. |
| **Aleksandrs Pavlovskis** | Sistēmu analītiķis | DB struktūra, algoritmu drošība, tehniskā specifikācija. |
| **Sabīne Pavlovska** | UI/UX & QA | Prototipa dizains, lietojamības testēšana, kvalitātes kontrole. |

---

## 🎯 1. Projekta darba mērķis

Izstrādāt inovatīvu EIKT produktu – **Sociālās aprūpes iestāžu pārvaldības sistēmu**, kas digitalizē sociālās aprūpes centru (SAC) procesus, automatizē dokumentu kaskādes principu un būtiski samazina administratīvo slogu, atbrīvojot laiku tiešajam darbam ar klientu.

---

## 💡 3. Idejas pamatojums un tirgus analīze

### 3.1. Problēmas aktualitāte
Sociālās aprūpes nozarē joprojām dominē neefektīva "papīra kultūra". Ikdienas darbā sociālais darbinieks pavada līdz pat **40% laika**, manuāli pārrakstot datus. Esošie risinājumi bieži ir dārgi un prasa pastāvīgu internetu, kas lauku reģionos ir problēma.

Mūsu risinājums piedāvā **"Offline-first"** arhitektūru – pilnvērtīgu darbu bezsaistē ar automātisku sinhronizāciju, kad tīkls atjaunojas.

### 3.2. Mērķauditorija
1.  **Primārā:** Latvijas pašvaldību sociālās aprūpes centri (SAC).
2.  **Sekundārā:** Privātie aprūpes centri un pansionāti.

### 3.3. Produkta atšķirība un kompetence
*   **Ekspertīze:** 13 gadu pieredze sociālajā aprūpē apvienota ar IT zināšanām.
*   **Dinamiska klienta karte:** Metodoloģisks palīgs, nevis tikai datu arhīvs.
*   **Zero-IT deployment:** Sistēma uzstādāma un uzturama bez dārgu IT speciālistu piesaistes.
*   **Likumdošanas atbilstība:** Iebūvēta atbilstība MK noteikumiem (brīdinājumi par termiņiem).

### 3.4. Finansiālais modelis un ieguvumi

| Pozīcija | Apraksts | Cena (orientējoši) |
| :--- | :--- | :--- |
| **Licence** | Vienreizēja maksa par sistēmas uzstādīšanu | 2 500 – 4 500 EUR |
| **Uzturēšana** | Likumdošanas atjauninājumi un tehniskais atbalsts | 600 EUR / gadā |
| **Ietaupījums** | Darbinieku laika ekonomija uz atskaitēm | ~400 EUR / mēnesī |
| **ROI** | Investīcija atpelnās vidēji **10-12 mēnešu laikā**. | |

---

## 🏗️ 4. Tehnoloģiskā arhitektūra (EIKT specifikācija)

*   **Arhitektūra:** "Offline-First" (darbs bez interneta).
*   **Tehnoloģijas:** Java 21 (LTS), JavaFX (Desktop UI).
*   **Datu bāze:** Hibrīda modelis – H2 (lokāli) + MySQL (centrāli).
*   **Drošība:** BCrypt šifrēšana, RBAC (lomu sistēma), aizsardzība pret SQL injekcijām.
*   **Integrācija:** Excel datu imports/eksports.

---

## 📱 5. Produkta prototips un darbības algoritms

### 1.5. Galvenie moduļi

#### 1.5.1. Galvenais skats (Dashboard)
Sistēmas centrālais vadības panelis.
*   **Paziņojumu centrs:** Brīdina par dokumentu termiņiem (pases, VDEĀVK).
*   **Operatīvie logrīki:** Dzimšanas dienas, klientu kustība.
*   **Aktivitāšu plūsma:** Reāllaika žurnāls par kolēģu darbībām.

#### 1.5.2. Administratora rīki (Drošības komandcentrs)

| Funkcija | Apraksts |
| :--- | :--- |
| **Datu imports** | Masveida datu ielāde no Excel failiem. |
| **Rezerves kopijas** | Datu dublēšana un atjaunošana (Backup/Restore). |
| **Kļūdu labošana** | "Recycle Bin" dzēsto klientu atjaunošanai. |
| **Audits** | Visu darbību fiksēšana (GDPR atbilstība). |
| **Datu dzēšana** | "Tiesības tikt aizmirstam" un neatgriezeniska dzēšana. |

#### 1.5.3. Klientu reģistrs
Atbilst MK noteikumiem Nr. 338.
*   **Reģistra žurnāls:** Juridiskā uzskaite ar termiņu indikāciju (Sarkans/Zaļš).
*   **Operatīvā vadība:** Ātrā meklēšana un filtrēšana (Aktīvie/Arhīvs).
*   **Datu ievade:** Validācija personas kodam, automātiska dzimšanas datuma noteikšana.

#### 1.5.4. Klienta karte
Digitāla personlieta, kas apvieno visu informāciju vienuviet.
*   **Personas identifikācija:** Juridiskie dati.
*   **Dokumentu kontrole:** Vizuāls saraksts (Pase, ID).
*   **Ģimene un kontakti:** Piederīgo saraksts ārkārtas gadījumiem.
*   **Veselība un vide:** Tehniskie palīglīdzekļi, pārvietošanās režīms.

#### 1.5.5. Novērtēšana (MK Nr. 138)
*   **Vēsture:** Progresa izsekojamība dinamikā.
*   **Veidlapa:** Strukturēta anketa (Bartela indekss u.c.).
*   **Rezultāts:** Automātisks punktu aprēķins un aprūpes līmeņa noteikšana.

#### 1.5.6. Starpprofesionāļu protokols
*   **Trīs skatupunkti:** Sociālais, Medicīnas, Aprūpes.
*   **Riski:** Kritienu, klaiņošanas riski.
*   **Plānošana:** Rekomendācijas tālākajam darbam.

#### 1.5.7. Sarunu žurnāls
*   **Strukturēta fiksēšana:** Saturs -> Secinājumi -> Vienošanās.
*   **Slodzes uzskaite:** Precīza ilguma fiksēšana.

#### 1.5.8. Nodarbību žurnāls
*   **Kaskādes izvēle:** Bloks -> Speciālists -> Joma -> Līmenis.
*   **Automātika:** Mērķi un uzdevumi aizpildās automātiski no metodikas.
*   **Vērtējums:** Motivācija, gaita, noskaņojums.

#### 1.5.9. Plāni (Aprūpes un Rehabilitācijas)
*   **Dinamika:** Salīdzinājums "Pirms" un "Aktuālais".
*   **Plāna saturs:** Mērķi, uzdevumi, atbildīgie, termiņi.
*   **Špikeris:** Automātiskas rekomendācijas no protokola.

### 1.6. Pašdziedinošā sinhronizācija (Self-Healing)
"Smart Sync" algoritms nodrošina datu konsistenci. Ja internets pazūd, dati tiek saglabāti lokāli. Kad tīkls atjaunojas, notiek automātiska sinhronizācija un konfliktu risināšana (Optimistic Locking).

---

## ✅ 6. Kvalitātes kontroles un testēšanas plāns (QA)

| Kategorija | Apraksts |
| :--- | :--- |
| **Datu Integritāte** | "Soft Delete", kaskādes dzēšana. |
| **Drošība** | RBAC, SQL injekciju testi, XSS aizsardzība. |
| **UI/UX** | FXML ielāde, responsivitāte, "Smoke" testi. |
| **Disaster Recovery** | Rezerves kopiju atjaunošana. |
| **Veiktspēja** | Testi ar 50 000+ ierakstiem. |

---

## 📊 7. SVID analīze

| Stiprās puses | Vājās puses |
| :--- | :--- |
| • "Offline-First" arhitektūra.<br>• Nozares specifiska kompetence.<br>• Intuitīvs UX (Excel-like).<br>• Datu drošība (GDPR).<br>• Ekonomiskā pievilcība (CapEx). | • Jauns produkts tirgū.<br>• Sākotnējais resursu patēriņš (migrācija).<br>• Lokālā servera atkarība. |

| Iespējas | Draudi |
| :--- | :--- |
| • Likumdošanas prasību pieaugums.<br>• Tirgus paplašināšana (Baltija).<br>• Integrācija ar valsts reģistriem. | • Konkurence no valsts sistēmām.<br>• Likumdošanas krasas izmaiņas.<br>• Kiberapdraudējumi. |

---

## 🛡️ 8. Risku analīze

| Risks | Līmenis | Risinājums |
| :--- | :--- | :--- |
| **Lietotāju pretestība** | Kritisks | "Excel-like" saskarne, vienkāršotas rokasgrāmatas. |
| **Interneta pārrāvumi** | Kritisks | "Offline-First" arhitektūra. |
| **Likumdošanas maiņa** | Augsts | Ārējo šablonu dzinējs (Excel veidnes). |
| **Datu noplūde** | Augsts | Šifrēšana, RBAC, Audita pēdas. |
| **Datu konflikti** | Vidējs | Ierakstu bloķēšana (Locking). |

---

## 🚀 9. Nākotnes attīstības perspektīva

1.  **Mobilā ekosistēma:** Android aplikācija ar "6 pogu principu" aprūpētājiem.
2.  **AI Analītika:** Agrīnās brīdināšanas sistēma (veselības riski).
3.  **Kaskādes automatizācija:** Viens klikšķis aizpilda 5 dokumentus.
4.  **Balss vadība:** Offline Voice-to-Text diktēšanai.

---

## 📅 10. Izstrādes plāns

**Kopējais ilgums:** 6-8 mēneši.

| Posms | Darbi | Ilgums |
| :--- | :--- | :--- |
| **1. Arhitektūra** | DB shēma, Drošības kodols. | 2 mēneši |
| **2. UI/UX** | Paneļi, Formas, Ergonomika. | 1.5 mēneši |
| **3. Biznesa loģika** | Algoritmi, Validācija, Atskaites. | 1 mēnesis |
| **4. Offline dzinējs** | Buferēšana, Sinhronizācija (Kritiskais ceļš). | 3 nedēļas |
| **5. QA un Drošība** | Slodzes testi, Penetration testing. | 3 nedēļas |
| **6. Ieviešana** | Rokasgrāmatas, Pilotprojekts. | 2 nedēļas |

---

## 🏁 11. Secinājumi

"Klientu Reģistrs" ir dzīvotspējīgs, drošs un ekonomiski pamatots risinājums, kas:
*   **Samazina birokrātiju** par 40%.
*   **Garantē darbību** bez interneta.
*   **Nodrošina atbilstību** GDPR un MK noteikumiem.
*   **Atmaksājas** 10-12 mēnešu laikā.