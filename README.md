# Mac Open Source Radar

Färdig statisk, responsiv webbplats på svenska. Ingen byggprocess, externa bibliotek, externa typsnitt, spårning eller konto behövs. Elva projekt är källkontrollerade den 3 november 2026. Källkontroll är inte samma sak som att ha kört programmen.

## Starta lokalt

Packa upp ZIP-filen. Öppna Terminal i mappen `mac-open-source-radar` och kör:

```sh
python3 -m http.server 8000 --bind 127.0.0.1
```

Öppna http://127.0.0.1:8000 i webbläsaren. Avsluta servern med Ctrl+C. Python 3 behöver finnas installerat. Att dubbelklicka på index.html räcker inte: webbläsare blockerar ofta läsning av JSON via file://. Webbplatsen visar då ett felmeddelande med instruktioner.

För publicering: ladda upp samtliga sex filer till valfri statisk webbserver. Behåll filerna i samma mapp. Ingen serverkod, databas eller hemlig nyckel behövs. Relativa sökvägar gör att den även fungerar i en undermapp. Hosting ska leverera HTML, CSS, JavaScript och JSON med vanliga korrekta MIME-typer.

## Filer

- index.html: redaktionell startsida, navigering och projektvy i en tillgänglig dialog.
- styles.css: magasinsdesign, tekniska illustrationer och mobilanpassning.
- app.js: läser JSON, sökning, kategorier, mognad, Apple Silicon-filter, sortering och delbara projektlänkar.
- projects.json: enda källan för projektkort, faktarutor och bevakningslistor.
- changelog.json: betydelsefulla redaktionella förändringar. Startposterna är tillägg till denna radar, inte projektens grundande- eller releasedatum.
- README.md: drift, metod och uppdateringar.

## Underlag och avgränsning

Den tidigare chattens fullständiga användarspecifikation lästes. Arbetsmappen var tom. Den angivna `/mnt/data/mac-open-source-radar-data-update-2026-11-02.zip` fanns inte tillgänglig i den här miljön; inga filer från den har importerats. Datapatchen beskrevs som separata JSON-uppdateringar, inte som en fullständig webbplats.

Projektens primärkällor finns i varje `source_urls` och visas i projektvyn. Beskrivningar och relevanta plattformsuppgifter har kontrollerats mot dessa. Senaste commit, release, contributors, tillväxt och andra uppgifter lämnas null/Unknown där tillräckligt underlag inte samlats in. Inga hastighetslöften eller spelkompatibilitetsgarantier ges.

FigCraft är här **storytold/figcraft**, det fristående Rust-verktyget i samma familj som VectorCraft. Ett separat Figma-plugin finns på https://github.com/divikwu/figcraft. Användarens ursprungliga namn saknade repo-URL; dessa två projekt får inte slås samman. Bloodborne från den tidigare sammanfattningen har inte importerats eftersom rätt primärkälla inte verifierades i denna körning. GoldenEye-postens formulering följer nuvarande repository, inte den tidigare chattens versionspåståenden.

Status, mognad och 1–5-betyg är redaktionella bedömningar. Varje post har `rating_reason`. Trend är null för samtliga eftersom tillväxt över tid inte har mätts. Trending-sektionen är därför ärligt tom men fullt implementerad för framtida belagda signaler. AI accelerated används bara för AppleBridge, vars README uttryckligen krediterar Claude Sonnet 4.5. nvNova är Revival och visas med utvecklarens datavarning; Apple Silicon via Rosetta räknas inte som native ARM64.

High confidence avser primärkällestöd för den beskrivna kärnfunktionen; det fyller inte automatiskt i okända fält. `null` visas alltid som Unknown. `false` betyder verifierat nej, inte saknat underlag. Licens-Unknown betyder att licensen inte kontrollerats tillräckligt här, inte att projektet saknar licens.

## Dagliga deltauppdateringar

1. Läs befintliga projects.json och changelog.json innan research. Identifiera samma projekt via stabilt id och repository; skapa inte nya poster för namnbyten eller flyttade repos.
2. Verifiera betydelsefulla förändringar mot primärkällor. Spara käll-URL, kontrollens datum och när möjligt faktisk aktivitetsdag/release. Skilj discovery, källkontroll och funktionstest åt.
3. Uppdatera endast relevanta objekt i projects.json. Behåll id stabilt. Alla aktuella fält bör behållas; saknad fakta är null, inte en gissning. `source_urls` och `tags` är listor.
4. Lägg till en post i changelog.json för verkligt nyhetsvärde: date, project, project_id, type, summary, sources. Tillåtna typer: new_project, release, revival, major_update, status_change. Gör ingen loggpost för en oförändrad kontroll.
5. `section` kan vara Radar, Watchlist, Revival eller Trending. Trending ska kräva flera dokumenterade signaler. Status: Established, Growing, Early, Experimental, Revival, Dormant eller Archived. Mognad: Proof of concept, Alpha, Beta, Usable eller Mature. Installation: Easy, Medium, Advanced eller Experimental.
6. Uppdatera betyg endast med motivering i rating_reason. Skalan är 1–5 eller null. Lägg till nya illustrationer i app.js endast vid behov; annars finns en generell reservillustration.
7. Kontrollera giltig JSON, unika id:n, länkar, sökning, filter och mobilvy. Publicera JSON-filerna tillsammans. Återladdning hämtar data utan cache.

Datum för ”Källkollad” i navigeringen hämtas från senaste last_checked. Omslag, utgåvenummer och toppnyhet i index.html är avsiktligt redaktionellt valda och uppdateras när en ny utgåva behöver nytt omslag. Ingen automatisk research eller schemalagd uppdatering startas av denna statiska webbplats.

## Tillgänglighet och kompatibilitet

Semantiska sektioner, hopplänk, synliga fokusmarkeringar, etiketter, live-region för träffantal, tangentbordsanvändbara kontroller och native dialog med Escape-stängning. Dekorativa illustrationer är dolda för skärmläsare. Reduced motion respekteras. Moderna Safari, Firefox, Chrome och Edge med stöd för dialog och fetch förväntas. Projektlänkar använder `#project/id` och fungerar även vid direktladdning.

## Verifiering

JavaScript-syntax och JSON-struktur kontrollerades. Webbläsartester omfattade datahämtning, sökning, kategorifilter, tomt resultat, återställning och projektöppning/stängning. Mobil- och datorlayout granskades separat. Inga av de listade apparna eller spelen installerades eller kördes som del av webbplatstestet.
