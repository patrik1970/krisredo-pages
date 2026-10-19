# KrisRedo – Integritetspolicy

> **GRANSKNINGSUTKAST – INTE SLUTGODKÄND ELLER PUBLICERAD SOM OFFICIELL INTEGRITETSPOLICY**
>
> Version 1.0 (utkast), 19 oktober 2026. Underlaget bygger på en statisk kodgranskning den 19 oktober 2026 av commit `ed6d0885d28bf63d39c68af544c9ca013e899c45` och identifierade lokala ändringar. Detta är inte en verifierad release. Dokumentet ska uppdateras under utvecklingen. GitHub Pages har inte aktiverats genom denna ändring.

## 1. Om KrisRedo

KrisRedo är en mobilapp för svensk krisberedskap med bland annat checklistor, viktiga telefonnummer och skyddsrumssökning. Grundläggande information och register finns lokalt för att stödja användning utan internet.

## 2. Personuppgiftsansvarig och kontakt

KrisRedo utvecklas och tillhandahålls av **Patrik Persson**, som privatperson.

**E-post för integritetsfrågor:** patrik.persson.home@gmail.com

Dessa kontaktuppgifter har godkänts för användning i integritetspolicyn.

## 3. Uppgifter som behandlas

### Platsinformation

När du väljer att söka efter skyddsrum nära dig kan appen begära tillgång till telefonens ungefärliga eller precisa position. Positionen används för lokal sökning i medföljande skyddsrumsregister och för avståndsbedömning. Ingen egen permanent positionshistorik har identifierats i den granskade sökfunktionen. Du kan också söka efter en ort manuellt utan att använda GPS.

Telefonens operativsystem och positionstjänster kan behandla uppgifter enligt sina egna inställningar och villkor. Att appens egen sökning är lokal innebär inte att all systemrelaterad behandling sker utan nätverk.

### Checklistmarkeringar

När du markerar en checklistpunkt sparar appen identifieraren för punkten i telefonens lokala applagring så att markeringen finns kvar mellan appstarter. Den granskade tjänsten sparar inte en separat historik över tidigare markeringar.

### Läkemedelsrelaterade checklistpunkter

Läkemedelsdelen innehåller fasta förberedelsepunkter, bland annat om receptbelagda läkemedel, förbrukningsartiklar, läkemedelslista, förvaring och utgångsdatum. Appen sparar vilka punkter du markerat, **inte** läkemedelsnamn, diagnoser, recept eller innehållet i någon läkemedelslista.

Sådana markeringar kan ändå vara integritetskänsliga. I den granskade implementationen sparas de genom samma lokala Preferences-lagring som övriga checklistor.

### Manuell ortsökning

Ortnamn som du anger används för sökning i lokala ortsregister. Ingen permanent sökhistorik identifierades i den granskade funktionen.

## 4. Lokal lagring och säkerhet

Checklistmarkeringar lagras lokalt genom Androids Preferences/SharedPreferences. Någon särskild appkryptering av checklistvärdena har inte verifierats i den granskade implementationen. Skyddsrums- och ortsregister lagras lokalt.

**Planerade skydd**, bland annat särskild krypterad läkemedelslagring och migrering av äldre markeringar, är ännu inte verifierade som implementerade och beskrivs därför inte som befintliga.

## 5. Android-säkerhetskopiering och telefonöverföring

Checklistmarkeringar, även läkemedelsrelaterade markeringar, **kan omfattas** av Androids säkerhetskopiering och överföring mellan telefoner. Det faktiska beteendet beror på systemversion, inställningar och tjänster. Lokalt framtagna regler för undantag av skyddsrumsdatabasen undantar inte checklistornas SharedPreferences, och deras beteende i en distribuerad release är inte verifierat.

Att radera lokala uppgifter innebär inte att äldre säkerhetskopior automatiskt raderas.

## 6. Externa appar och funktioner

### Kartappar

När du väljer **Hitta hit** skickas det valda skyddsrummets position och beskrivning till en extern kartapp. Den granskade koden skickar inte uttryckligen din aktuella GPS-startpunkt i detta steg, men kartappen kan själv använda din position enligt sina behörigheter och villkor.

### Telefonfunktion

När du väljer att ringa ett viktigt nummer öppnar appen telefonfunktionen med ett fördefinierat telefonnummer. Ingen åtkomst till din kontaktlista eller samtalshistorik identifierades i den granskade funktionen.

### Nätverk, analys och annonser

Den aktiva skyddsrumssökningen använder lokala register. Det finns även kod för en extern datakälla, men ingen aktiv produktionsanropsväg identifierades i granskningen. Ingen egen analys-, annons- eller kraschuppladdningsfunktion identifierades i granskad appkod och direkta beroenden. Det är **inte** ett verifierat påstående om att ingen nätverkstrafik eller tredjepartsbehandling någonsin förekommer.

## 7. Teknisk diagnostik

Appen och dess underliggande bibliotek kan använda tekniska loggar. Kodgranskningen har identifierat risker för loggning av positionsinformation och checklistvärden. Loggningen är inte slutligt verifierad i en avsedd release. Därför utlovar denna text inte att sådana värden aldrig förekommer i loggar.

## 8. Ändamål och rättslig grund – ÖPPET FÖRE SLUTGODKÄNNANDE

Ändamålen med behandlingen är att tillhandahålla valda funktioner, såsom att behålla checklistmarkeringar och söka efter närliggande skyddsrum.

**Kräver beslut och juridisk kontroll före officiell publicering:** fastställ rättslig grund enligt GDPR för varje relevant behandling och bedöm om läkemedelsrelaterade markeringar omfattas av reglerna för känsliga personuppgifter samt vilket undantag enligt artikel 9 som i så fall kan tillämpas. Appbehörighet är inte i sig en rättslig grund.

## 9. Lagringstid och radering

Checklistmarkeringar sparas lokalt tills du ändrar dem eller appens lokala lagring tas bort. Du kan avmarkera enskilda punkter. Du kan också rensa appens lagring genom telefonens Android-inställningar; detta kan ta bort andra appuppgifter. Att rensa cache är inte samma sak som att rensa lagring. Äldre säkerhetskopior kan behöva hanteras separat.

Ingen funktion har identifierats som gör att den personuppgiftsansvarige på distans kan läsa eller radera användarens lokala checklistor.

## 10. Dina rättigheter

När GDPR är tillämplig kan du ha rätt till information, tillgång, rättelse, radering och i vissa fall begränsning, invändning eller dataportabilitet. Vilka rättigheter som gäller beror på behandlingen och dess rättsliga grund.

För frågor och begäranden, kontakta **patrik.persson.home@gmail.com**. Du kan lämna klagomål till **Integritetsskyddsmyndigheten (IMY)** på https://www.imy.se/.

**Öppet före slutgodkännande:** rutiner för kontaktärenden, gallring och hantering av rättighetsbegäranden.

## 11. Barn och målgrupp – ÖPPET FÖRE SLUTGODKÄNNANDE

Ingen funktion för användarkonton eller insamling av barns namn och kontaktuppgifter identifierades i den granskade implementationen. Avsedd målgrupp och åldersklassificering ska fastställas innan policyn slutgodkänns.

## 12. Policyns uppdateringar

Detta är ett levande dokument. Texten ska uppdateras när appens funktioner, behandlingar eller säkerhetslösningar ändras. Varje godkänd version ska ha ett tydligt versionsnummer och datum.

## 13. Webbplatsen – ÖPPET FÖRE SLUTGODKÄNNANDE

När en officiell webbplats publiceras ska dess faktiska tekniska uppsättning och eventuella behandling av besöksuppgifter beskrivas. GitHub Pages kan behandla bland annat IP-adresser för säkerhetsändamål. Ingen webbplats- eller trafikverifiering ingår i denna granskning.

---

**Kvar före officiell publicering:** rättslig grund och eventuell artikel 9-bedömning, release- och loggningsverifiering, backuphantering, kontakt- och rättighetsrutiner, målgrupp samt slutlig Google Play Data Safety-bedömning. Dokumentet är inte ett påstående om full GDPR-efterlevnad.
