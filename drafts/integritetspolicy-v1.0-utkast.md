# KrisRedo – Integritetspolicy

> **GRANSKNINGSUTKAST – ÄNNU INTE SLUTGODKÄND SOM OFFICIELL INTEGRITETSPOLICY**
>
> Version 1.1 (utkast), 19 oktober 2026. Ursprungligt underlag: statisk kodgranskning av commit `ed6d0885d28bf63d39c68af544c9ca013e899c45` och lokala ändringar. Därefter har läkemedelschecklistans tillfälliga beteende verifierats på Android API 37 (16 KB) enligt KRD-PRIV-005.9 D.3. Den uppdaterade appkoden är fortfarande lokal och inte en verifierad publicerad release. Historisk nyckelrensning har kodgranskats och en test-APK har byggts, men Androidtest av den faktiska rensningen återstår. GitHub Pages-publicering är inte verifierad.

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

För nio vanliga checklistgrupper sparar appen identifierare för markerade punkter i telefonens lokala applagring, så att markeringarna kan finnas kvar mellan appstarter. Den granskade tjänsten sparar inte en separat historik över tidigare markeringar. Läkemedelschecklistan behandlas annorlunda enligt avsnittet nedan.

### Läkemedelsrelaterade checklistpunkter

Läkemedelsdelen innehåller fasta förberedelsepunkter, bland annat om receptbelagda läkemedel, förbrukningsartiklar, läkemedelslista, förvaring och utgångsdatum. Appen låter dig markera fasta punkter, **inte** ange läkemedelsnamn, diagnoser, recept eller innehållet i någon läkemedelslista. Även fasta markeringar kan vara integritetskänsliga.

I den uppdaterade, Androidtestade implementationen är läkemedelsmarkeringarna **tillfälliga per sidbesök**. De kan försvinna när du lämnar sidan och alla sex var omarkerade efter ett verifierat processavslut och en ny kallstart. De skrivs inte till appens permanenta checklistlagring av det nya läkemedelsflödet.

Äldre versioner kan ha sparat sådana markeringar lokalt. Vid appstart försöker den uppdaterade appen ta bort den äldre lagringsnyckeln `emergency-kit.medicine.checklist.v1`. Funktionen är icke-blockerande och kan misslyckas; faktisk rensning av ett historiskt Androidvärde är ännu inte verifierad. Äldre säkerhetskopior kan fortfarande innehålla värden.

### Manuell ortsökning

Ortnamn som du anger används för sökning i lokala ortsregister. Ingen permanent sökhistorik identifierades i den granskade funktionen.

## 4. Lokal lagring och säkerhet

De nio vanliga checklistgruppernas markeringar lagras lokalt genom Capacitor Preferences, som använder Androids SharedPreferences. Någon särskild appkryptering av dessa checklistvärden har inte verifierats. Skyddsrums- och ortsregister lagras lokalt.

Den uppdaterade läkemedelschecklistan håller markeringarna tillfälligt i sidans minne. För äldre permanent sparade läkemedelsmarkeringar görs ett riktat rensningsförsök vid appstart. Detta är inte en garanti för fysisk radering, och äldre säkerhetskopior påverkas inte automatiskt.

## 5. Android-säkerhetskopiering och telefonöverföring

De nio vanliga checklistgruppernas lokala markeringar **kan omfattas** av Androids säkerhetskopiering och överföring mellan telefoner. Läkemedelsmarkeringar från äldre appversioner **kan också finnas** i äldre säkerhetskopior. Det faktiska beteendet beror på systemversion, inställningar och tjänster. Lokalt framtagna regler för undantag av skyddsrumsdatabasen undantar inte checklistornas SharedPreferences, och deras beteende i en distribuerad release är inte verifierat.

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

De nio vanliga checklistgruppernas markeringar sparas lokalt tills du ändrar dem eller appens lokala lagring tas bort. Du kan avmarkera enskilda punkter. Läkemedelsmarkeringarna i den uppdaterade versionen är tillfälliga och kan försvinna när sidan lämnas; de återkom inte efter kallstart i det genomförda Androidtestet. Du kan också rensa appens lagring genom telefonens Android-inställningar; detta kan ta bort andra appuppgifter. Att rensa cache är inte samma sak som att rensa lagring. Äldre säkerhetskopior kan behöva hanteras separat.

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

**Kvar före officiell publicering:** fastställ rättslig grund och eventuell artikel 9-bedömning, verifiera slutlig release och loggning, slutför kontroll av historisk nyckelrensning och backuphantering, besluta kontakt- och rättighetsrutiner samt målgrupp och slutlig Google Play Data Safety-bedömning. Detta utkast är inte ett påstående om full GDPR-efterlevnad. Dokumentet är inte ett påstående om full GDPR-efterlevnad.
