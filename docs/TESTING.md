# 🧪 Testēšanas Dokumentācija

Šajā dokumentā apkopota informācija par automatizētajiem testiem, kas nodrošina sistēmas "Klientu Reģistrs" stabilitāti, drošību un datu integritāti.

## Testu Pārklājums

| Testa Klase | Kategorija | Apraksts |
| :--- | :--- | :--- |
| **ActivityRepositoryTest** | Datu Integritāte | Pārbauda, vai sistēma korekti veic datu filtrēšanu un "soft delete" darbības. |
| **AdminServiceTest** | Drošība (RBAC) | Pārbauda piekļuves tiesību ierobežojumus (darbinieks vs vadītājs). |
| **AllFxmlLoadTest** | UI/UX | Veic visu FXML failu ielādes pārbaudi, garantējot, ka logi atveras bez kļūdām. |
| **ApplicationSmokeTest** | Smoke Test | Pārbauda "dzīvības procesus" – datubāzes savienojumu un skatu pārvaldnieku. |
| **BackupRestoreTest** | Disaster Recovery | Simulē datu zudumu un pārbauda atjaunošanu no rezerves kopijas. |
| **ChaosMonkeyTest** *(Buffer Overflow)* | Drošība | Pārbauda noturību pret pārmērīgi garu datu ievadi. |
| **ChaosMonkeyTest** *(XSS)* | Drošība | Testē aizsardzību pret skriptu injekcijām ievades laukos. |
| **ChaosMonkeyTest** *(SQL Injection)* | Drošība | Pārbauda drošību pret ļaunprātīgām SQL komandām. |
| **ChaosMonkeyTest** *(Null/Empty)* | Validācija | Pārbauda obligāto lauku validāciju. |
| **ChaosMonkeyTest** *(Emoji/Special)* | Datu Apstrāde | Pārbauda spēju apstrādāt speciālos simbolus un emocijikonas. |
| **UserSessionRepositoryTest** | Drošība | Analizē sesiju dzīves ciklu un drošību. |
| **DocumentationConsistencyTest** | Kvalitāte | Pārbauda atbilstību starp kodu un tehnisko dokumentāciju. |
| **ClientCardServiceTest** | Transakcijas | Pārbauda kartes datu apstrādi un "rollback" mehānismu. |
| **ClientChangeDetectorTest** | Audits | Seko līdzi izmaiņām klienta datos auditācijas pierakstiem. |
| **ClientHistoryValidationTest** | Loģika | Kontrolē hronoloģisko secību (piem., iestāšanās/izstāšanās). |
| **ConcurrentDataAccessStressTest** | Concurrency | Simulē vienlaicīgu piekļuvi, pārbaudot "Locking" mehānismu. |
| **DatabaseMigrationTest** | Migrācija | Pārbauda atjaunināšanos uz jaunāku versiju bez datu zuduma. |
| **DatabaseResilienceTest** | Stabilitāte | Pārbauda izturību pret tīkla pārrāvumiem datu sūtīšanas brīdī. |
| **DataFilesAvailabilityTest** | Konfigurācija | Pārbauda, vai visi palīgfaili un Excel sagataves ir pieejamas. |
| **DataIntegrityTest** | Datu Integritāte | Pārbauda "Cascade Delete" saistītajiem datiem. |
| **DeepDocumentationAuditTest** | Dokumentācija | Padziļināta pārbaude, vai dokumentācija atbilst kodam. |
| **ExcelFunctionalityTest** | Eksports | Pārbauda atskaišu ģenerēšanu un failu saglabāšanu. |
| **FullSystemFlowTest** | E2E | Pārbauda visu ķēdi: DB -> saraksts -> klienta karte. |
| **KarteDuplicateDetectionServiceTest** | Validācija | Meklē potenciālus dublikātus pēc personas koda vai vārda. |
| **KarteValidationServiceTest** | Validācija | Pārbauda ievades datu formātu (e-pasti, tālruņi). |
| **KlientsRepositoryIntegrationTest** | Integrācija | Pārbauda pilnu ciklu ar reālu DB (CRUD operācijas). |
| **KlientsRepositoryOfflineTest** | Tīkla kļūdas | Simulē nestabilu tīklu un pārbauda "Retry" mehānismu. |
| **LargeScaleDataPerformanceTest** | Veiktspēja | Ātruma tests ar 50 000 ierakstiem. |
| **ListRepositoryOfflineTest** | UX/Offline | Pārbauda reakciju uz tīkla zudumu sarakstu ielādē. |
| **LockingStressTest** | Concurrency | Precīzs "Race Condition" tests bloķēšanas mehānismam. |
| **MainExitTest** | Resursi | Pārbauda korektu programmas aizvēršanos un resursu atbrīvošanu. |

## Kā palaist testus

Lai palaistu visus testus, izmantojiet Maven komandu:
`mvn test`