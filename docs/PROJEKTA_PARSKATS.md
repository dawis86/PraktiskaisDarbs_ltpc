# 📄 Projekta Dokumentācija

> **Modulis:** EIKT produktu izstrāde  
> **Projekts:** Sociālās aprūpes iestāžu pārvaldības sistēma

---

## 🎯 1. Projekta Darba Mērķis

Projekta mērķis ir izstrādāt jauna EIKT nozares produkta ideju – **Sociālās aprūpes iestāžu pārvaldības sistēmu**, pamatot tās aktualitāti tirgū, izveidot produkta prototipu un sagatavot tehnisko dokumentāciju. 

Sistēma paredzēta sociālās aprūpes centru (SAC) darba optimizācijai:
* 📂 Digitalizējot klientu lietu pārvaldību.
* 🔄 Automatizējot dokumentu apriti.
* 🛡️ Nodrošinot drošu, strukturētu pieeju aprūpes procesiem.

---

## 👥 2. Darba Forma un Organizācija (Komanda)

Projekta izstrādi veica komanda ar sadalītām atbildības jomām:

| Dalībnieks | Loma | Atbildība |
| :--- | :--- | :--- |
| **Zane Ābele** | Biznesa analītiķe | • Idejas izstrāde un tirgus izpēte.<br>• Problēmu definēšana un mērķauditorijas analīze.<br>• Komunikācijas plāna izstrāde. |
| **Aleksandrs Pavlovskis** | Sistēmu analītiķis | • Tehniskā specifikācija un arhitektūra.<br>• Tehnoloģiju izvēles pamatojums (Java, SQL).<br>• Sistēmas algoritmu un drošības risinājumu apraksts. |
| **Sabīne** | UI/UX & QA | • Produkta prototipa izstrāde un lietotāja ceļa (User Journey) definēšana.<br>• Vizuālā identitāte un lietojamības testēšana.<br>• Kvalitātes kontroles (QA) apraksts. |
| **Dāvis Strazds** | Projekta vadītājs | • Projekta koordinēšana un tehniskā realizācija. |

---

## 📝 3. Projekta Darba Saturs un Posmi

### 3.1. Idejas Izstrāde un Tirgus Izpēte
*(Balstīts uz Biznesa plāna analīzi)*

#### A. Kādas problēmas produkts risina
* **Sadrumstalota informācija:** Nav vienota klientu reģistra, dati ir izkaisīti. Sistēma nodrošina centralizētu datubāzi, kur visa informācija par klientu ir vienkopus.
* **Laikietilpīga dokumentu meklēšana:** Vēsturiskās veidlapas un informācija jāmeklē manuāli papīra arhīvos ("seifos"). Sistēma piedāvā tūlītēju piekļuvi vēsturiskajiem datiem ar meklēšanas un filtrēšanas iespējām "neatejot no darba vietas".
* **Manuāla datu ievade un dubults darbs:** Darbinieki tērē daudz laika, aizpildot papīra veidlapas un pārrakstot informāciju. Sistēma automatizē datu ielasīšanu veidlapās un izmanto klasifikatorus.
* **Neefektīvi aprēķini:** Aprēķini Excel veidlapās ir manuāli un lēni. Sistēmā ir iestrādātas formulas, kas automatizē aprēķinus.
* **Procesa necaurspīdīgums:** Grūti kontrolēt un uzraudzīt dokumentu apriti. Sistēma nodrošina pilnu darbību auditu ("Audit logs") un piekļuves kontroli.
* **Zema datu drošība:** Papīra dokumenti var pazust. Sistēmā dati tiek aizsargāti ar paroli, piekļuve ir ierobežota, un tiek veidotas regulāras datu rezerves kopijas.
* **Laikietilpīgas atskaites:** Manuāla atskaišu gatavošana ir lēna. Sistēmā ir iebūvēts atskaišu modulis (KPI, demogrāfija).
* **Mazāk laika klientam:** Lielais administratīvais slogs samazina laiku komunikācijai. Sistēma atbrīvo darbinieku laiku, automatizējot rutīnas uzdevumus.

#### B. Kāpēc problēma ir aktuāla
Risinājums nodrošina, ka visa informācija par klientu ir vienkopus, viegli atrodama, uzraugāma un izsekojama. Process tiek paātrināts, un darbinieki ietaupītajā laikā var vairāk veltīt komunikācijai ar klientu, uzlabojot aprūpes kvalitāti.

#### C. Mērķauditorija
1. **Sociālās aprūpes iestādes.**
2. **1. kārta:** Pašvaldības iestādes.
3. **2. kārta:** Privātie aprūpes centri.

#### D. Produkta atšķirība no līdzīgiem risinājumiem (Tirgus izpēte)
* **Latvijas Samariešu apvienība:** Esošais risinājums nav bijis lietotājam draudzīgs, darbinieki atgriezušies pie papīra formāta.
* **Latvijas Sarkanis Krusts:** Ir savs iekšējs risinājums, taču intervijas ar lietotājiem nav veiktas.
* **Mūsu priekšrocība:** Fokusēts uz lietojamību (UX), specifiskām SAC vajadzībām (medikamenti, nodarbības) un **offline** režīma atbalstu.

#### E. Komunikācijas plāns
Sākotnēji plānota komunikācija ar vadošajiem lēmuma pieņēmējiem, prezentējot ieguvumus iestādei. Vēlāk vadītāji risinājuma nepieciešamību "kaskadē" uz zemāka līmeņa darbiniekiem, uzsverot ikdienas darba atvieglošanu.

---

### 3.2. Informācijas un Tehnoloģiju Izmantošana
*(Balstīts uz Tehnisko specifikāciju)*

Sistēma veidota kā **darbvirsmas (desktop)** lietojumprogramma, balstoties uz "Multi-tier" arhitektūru un MVC (Model-View-Controller) projektēšanas paraugu.

#### A. EIKT nozares aktualitātes
* 🌍 **Digitālā transformācija:** Pāreja no papīra uz elektroniskiem reģistriem (ES Digitālā dekāde 2030).
* 🔒 **GDPR un datu aizsardzība:** Sensitīvu datu šifrēšana un stingra piekļuves kontrole.
* 📶 **Offline-first un hibrīda risinājumi:** Darbības nodrošināšana reģionos ar nestabilu internetu.
* 📊 **Datu analītika un automatizācija:** Reāllaika KPI paneļi, prognozēšana.

#### B. Izmantotās tehnoloģijas un pamatojums
Visas izmantotās tehnoloģijas ir atvērtā pirmkoda, bezmaksas un plaši dokumentētas:

* **Java 21 (LTS):** Stabila, droša enterprise valoda backend loģikai.
* **JavaFX 21:** Moderns, platformu neatkarīgs darbvirsmas interfeiss.
* **MySQL 8.0+:** Uzticama centrālā datubāze.
* **H2 Database:** Iegultā datubāze darbam bezsaistes (offline) režīmā.
* **HikariCP:** Augstas veiktspējas savienojumu pūls.
* **Apache POI:** Excel atskaišu un veidlapu ģenerēšanai.
* **BCrypt:** NIST ieteikts standarts paroļu hešēšanai.
* **Logback/SLF4J:** Standarta auditējamā žurnālošana.
* **Maven:** Atkarību pārvaldība.

---

### 3.3. Produkta Prototipa Izstrāde
*(Balstīts uz Prototips_UIUX_QA un Tehnisko specifikāciju)*

#### A. Prototipa apraksts un Lietotāja ceļš
1. **Autorizācija:** Droša piekļuve ar lietotājvārdu un paroli.
2. **Galvenais panelis (Dashboard):** Pārskats par KPI (jauni klienti, termiņi, dzimšanas dienas).
3. **Klientu reģistrs:** Saraksts ar meklēšanu, filtrēšanu un statusa indikāciju.
4. **Klienta karte:** Centralizēta lieta (Personas dati, Ģimene, Veselība, Dokumenti).
5. **Aktivitātes:** Nodarbību žurnāls, rehabilitācijas un aprūpes plāni.
6. **Medicīna:** Medikamentu pasūtījumu veidošana un veidlapas slimnīcai.
7. **Statistika:** Datu vizualizācija un analītika vadībai.

#### B. Produkta darbības algoritms
* **Autentifikācija:** Parole hešēta ar BCrypt, sesija ar 30 min noildzi.
* **Offline sinhronizācija (Store-and-Forward):** Periodiska savienojuma pārbaude. Bez savienojuma izmaiņas saglabā lokālajā H2 DB. Atjaunojoties savienojumam, dati tiek sinhronizēti.
* **Validācija:** Personas koda formāta un unikāluma pārbaude.
* **Termiņu loģika:** Aprēķins (Current_date + X dienas) -> Krāsu kods (Zaļš/Dzeltens/Sarkans).

#### C. Biznesa plāns
Stratēģisks piedāvājums pašvaldībām kā prioritārajam klientam, nodrošinot ātrāku ieviešanu.

#### D. Produkta dokumentācija
Sagatavota tehniskā specifikācija, lietotāja rokasgrāmata un testēšanas dokumentācija.

---

### 3.4. Papildu Sistēmas Funkcionalitāte (Administrēšana un Drošība)

#### A. Administratora rīki un drošība
* Administratora paroles pārvaldība.
* Programmas aizsardzības mehānismi.
* Piekļuves uzraudzība un aizsardzība pret SQL injekcijām ("Prepared Statements").

#### B. Licencēšana un piekļuves kontrole
* Licencēšanas modulis juridiskai aizsardzībai.
* Lietotāja identifikācija un audits.

#### C. Sistēmas konfigurācija
* Aktivitāšu klasifikatoru administrēšana.
* Offline režīma iestatījumi.
* Padziļināta analītika.

#### D. Nākotnes attīstības iespējas
* Mākoņa sinhronizācija (AWS/Azure).
* AI risku analīze.
* Mobilā versija un integrācija ar e-veselību.

---

### 3.5. Kvalitātes Kontrole un Testēšana
*(Balstīts uz Testēšanas dokumentāciju)*

#### A. Testēšanas stratēģija un rīki
* **Vienībtesti (Unit Tests):** JUnit 5, Mockito (atsevišķu klašu pārbaude).
* **Integrācijas testi:** Komponentu sadarbība ar DB (H2/MySQL).
* **UI/E2E testi:** TestFX (lietotāja simulācija).
* **Drošības un stresa testi:** "Chaos Monkey", SQL injekciju simulācijas, veiktspēja ar 50k+ ierakstiem.

#### B. Testu pārklājums
* **Drošība:** Autentifikācija, sesijas, RBAC.
* **Datu integritāte:** Transakcijas, kaskādes dzēšana, Concurrency.
* **Noturība (Resilience):** Offline buferis un sinhronizācija.
* **Dokumentācija:** "Līguma testi" koda atbilstībai.

#### C. Manuālā testēšana
Vizuālā pārbaude, Excel atskaišu ģenerēšana un drukāšana.

---

## 🚀 4. Gala Prezentācija un Secinājumi

Izstrādātais prototips demonstrē funkcionālu un praksē pielietojamu digitālu risinājumu sociālās aprūpes iestāžu vajadzībām. Tas parāda sistēmas galveno lietotāja plūsmu, datu pārvaldības principus un būtiskākos moduļus.

**Galvenie secinājumi:**
* Prototips palīdz novērtēt sistēmas lietojamību pirms pilnas izstrādes.
* Samazināts kļūdu risks un administratīvais slogs.
* Papildu administrēšanas un drošības moduļi demonstrē produkta tehnisko briedumu.
* Sistēma ir gatava darbam apstākļos ar ierobežotu interneta pieejamību (**Offline-first**).