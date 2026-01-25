# Tehniskā specifikācija  
**Projekts: Klientu Aprūpes Sistēma sociālās aprūpes centriem**  
**Studentu patstāvīgais darbs**  
**Versija: 1.0**  
**Autors: Aleksandrs Pavlovskis**  
**Datums: 2026. gada 25. janvāris**  

## 1. Projekta pārskats un arhitektūra

Sistēma ir **desktop lietojumprogramma** sociālās aprūpes centru (SAC) vajadzībām. Tā digitalizē klientu datu pārvaldību, aizstājot papīra reģistrus un Excel failus ar drošu, centralizētu risinājumu – no klienta uzņemšanas līdz izrakstīšanai.

**Arhitektūra**:  
- **Multi-tier** ar **MVC** paraugu (Model-View-Controller)  
- Prezentācijas slānis: JavaFX (FXML + CSS)  
- Biznesa loģika: Java servisi un kontrolieri  
- Datu piekļuve: JDBC + Repository/DAO  
- Datubāze: MySQL (centrālā) + H2 (lokālā offline režīmam)  

Šī struktūra nodrošina moduļainību, vieglu testēšanu un uzturēšanu.

## 2. EIKT nozares aktualitātes un attīstības tendences (Vadlīniju 3.3. punkts)

Sociālās aprūpes un veselības aprūpes digitālās sistēmas Latvijā/ES attīstās strauji:  
- **Digitālā transformācija** (Eiropas Digitālā dekāde 2030, Latvijas e-veselības plāns) – pāreja no papīra uz elektroniskiem reģistriem.  
- **GDPR un datu aizsardzība** – sensitīvi dati (veselība, sociālais stāvoklis) prasa stingru šifrēšanu un piekļuves kontroli.  
- **Offline-first un hibrīda risinājumi** – daudzas iestādes (īpaši reģionos) saskaras ar nestabilu internetu.  
- **Datu analītika un automatizācija** – KPI, prognozēšana, resursu plānošana ar reāllaika dashboardiem.  
- **Mākoņtehnoloģiju integrācija** ar lokālu fallback, lai nodrošinātu pieejamību.  

Avoti: Eiropas Komisijas ziņojumi, Latvijas MK noteikumi par sociālo aprūpi (Nr. 138, Nr. 291), reālā SAC pieredze.

## 3. Izmantotās tehnoloģijas un to pamatojums 

| Tehnoloģija       | Versija       | Pamatojums (saistība ar nozares tendencēm)                                                                 | Konkrēts pielietojums sistēmā                          |
|-------------------|---------------|-------------------------------------------------------------------------------------------------------------|----------------------------------------------------------|
| Java              | 21 (LTS)      | Stabila enterprise valoda Latvijā/ES (veselības sistēmas, bankas); ilgtspējīga un droša                  | Visa loģika, servisi, kontrolieri                        |
| JavaFX            | 21            | Cross-platform GUI desktop aplikācijām; responsīvs dizains, animācijas                                    | Lietotāja saskarne (dashboard, kartes, tabulas)          |
| MySQL             | 8.0+          | Uzticama relāciju DB vidēja mēroga sistēmām; labi transakcijas un indeksi                                 | Centrālā datu glabātuve                                  |
| H2 Database       | Iegultā       | Embedded offline DB – ideāli nestabilam internetam (offline-first tendence)                               | Lokālā datu glabātuve bez savienojuma                    |
| HikariCP          | Jaunākā       | Ātrākais connection pool; samazina latentumu pie biežiem vaicājumiem                                      | Savienojumu pārvaldība ar MySQL                          |
| Apache POI        | Jaunākā       | Standarts Excel ģenerēšanai Latvijā (SAC, bāriestības izmanto Excel veidnes)                              | Plānu, pieprasījumu eksports                             |
| BCrypt            | –             | NIST ieteikta paroļu hešēšana; aizsardzība pret brute-force (GDPR prasība)                               | Autentifikācija                                          |
| Logback/SLF4J     | –             | Standarta auditējamā žurnālošana enterprise sistēmās                                                      | Audita žurnāls (visas darbības fiksētas)                 |
| Maven             | –             | Atkarību pārvaldība un būvēšana; veicina reproducējamību un komandas darbu                               | Projekta būvēšana un atkarības                           |

Visas tehnoloģijas ir **atvērtā pirmkoda**, **bezmaksas** un **plaši dokumentētas** – tas atbilst ilgtspējīgas izstrādes principiem sociālajā sektorā.

## 4. Sistēmas algoritmi un loģika 

### 4.1. Autentifikācijas algoritms
1. Lietotājs ievada login/paroli  
2. Parole hešēta ar BCrypt → salīdzināta ar DB  
3. Veiksmīga → sesijas izveide (SessionManager) ar 30 min timeout  
4. Katrs pieprasījums pārbauda sesiju → beigusies → redirect uz login  

### 4.2. Offline sinhronizācijas loģika (store-and-forward)
1. Periodiska savienojuma pārbaude (ping ik pēc 2–3 s)  
2. Bez savienojuma → izmaiņas lokālajā H2 + buferī  
3. Savienojums atjaunots → buferētie vaicājumi nosūtīti secīgi (transakcijās)  
4. Konfliktu risināšana: prioritāte administratoram vai jaunākajam timestamp  
5. Veiksmīga sinhronizācija → buferis iztīrīts  

### 4.3. Klienta personas koda validācija un unikālums
1. Ievadīts 11 ciparu kods  
2. Formāta pārbaude (ddmmyy-xxxxx) + kontrolcipars (Latvijas standarts)  
3. DB vaicājums: SELECT COUNT(*) WHERE pk = ?  
4. Ja >0 → kļūda "Klients jau reģistrēts"  

### 4.4. Termiņu un brīdinājumu loģika (dashboard)
1. Katram klientam datumi (plāns, dokuments, dzimšanas diena)  
2. Aprēķins: current_date + X dienas → krāsu kods (zaļš OK, dzeltens tuvosies, sarkans nokavēts)  
3. Agregācija: GROUP BY statuss, COUNT(*) → dashboard tiles  

Šie algoritmi ir vienkārši, bet droši – tie nodrošina datu integritāti un samazina cilvēciskās kļūdas.

## 5. Drošība un paplašināšanas iespējas

- **Drošība**: BCrypt paroles, lomas (admin/sociālais darbinieks/vadītājs), audits (visas darbības ierakstītas), prepared statements (pret SQL injection), GDPR principi.  
- **Paplašināšana**: Mākoņa sinhronizācija (AWS/Azure), AI risku analīze, mobilā versija, integrācija ar e-veselību.

