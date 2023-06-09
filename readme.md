# IbsensXMLStrip/variant
## OBS
Denne versjonen av skriptet beholder følgende tags: body, div type="act" n=True, head type="act", HIS:hisStage, HIS:hisSp who=True, HIS:spOpener, speaker, p rend="noIndent"
## Merk
Hei! Dette skriptet er ganske foreldet per i dag.

## Intro
IbsensXMLStrip er et Python-script som lager rentekstfiler av XML-filer i TEI-format, spesifikt de som finnes ved Ibsensenteret. Dersom nye kompatible XML-filer introduseres bør disse legges inn i eksisterende folderstruktur - du kan fint lage nye mapper så lenge de følger eksisterende normer, altså. Resultatet er ren fulltekst som er lettere å kjøre tekstanalyser på og som kan brukes i fulltekstsøk.

Utviklet av vit. ass. Loke Sjølie

xmlStrip 0.1 "Dvergbjerk"
* Metadata hentes ut (men behandles ikke) fra fil og legges i egen undermappe.
* Konverterer alle html/jalla-koder til ASCII. Si i fra om du finner en som ikke er konvertert.
* Sletter all formatering og henter (ideelt sett) kun ut Ibsens egen tekst.
** Sletter alt Ibsen slettet.
* Mange insektfikserier [bugfixes].

xmlStrip 0.1.3

- Fikset i, det var et RegEx som var litt for grådig. 

- Instanser av typHyp; ble oversatt for tidlig i prosessen. Linjeskift i XML-filene tolkes som mange mellomrom, og typhyp ble fjernet før disse mellomrommene ble komprimert fra mange til ett - det er derfor det ble ett resterende mellomrom ved orddeling. Nå fjernes "typHyp; " for seg selv etter at alle multimellomrom er borte, og resultatet blir (fra Du41113a-f_NBO):

    Der er to slags åndelige love, to slags samvittigheder, en i manden og en ganske anden i kvinden. De forstår ikke hinanden.

- Programmet sjekker nå om det er en rolleliste. Om det er en rolleliste blir denne hentet ut og satt foran body-elementet, som betyr at den (skal) bli sittende foran alt annet og ikke løpe noen risiko for å bli slettet. Vi er også nesten helt garantert at alle XML-filer har et body-element! Samme metode kan brukes for å hente ut tittelinformasjon og annet ønskelig. :) Rentekst Du8952 åpner nå slik:

    Personerne: Advokat Helmer. Nora, hans hustru. Doktor Rank. Fru Linde. Sagfører Krogstad. Helmers tre små børn. Anne-Marie, barnepige hos Helmers. Stuepigen sammesteds. Et bybud. FØRSTE AKT.

En liten obs: det finnes noen steder hvor Ibsen har krysset ut ganske mange ting, som i Br4262I11. Punktum og slikt er ofte ikke omkranset av en hisdel-tagg, som fører til litt løsøre i rentekstfilen:

    halvmætt Mund, skal skifte Deles Del af sit ; . . – ! ; . , – . .) med dem, som intet har at bide.

Vi kan fjerne mye (kan håpe på alt) av denne merkelige morsekoden med RegEx eller lignende - om det ikke finnes instanser der det er ment å være slike enkelttegn. Jeg prøver også å finne ut av hvorfor det kom ett komma inn på en av rollelistene - det var ikke der før...

BETA 0.2
- Inkluderer forsideinformasjon
- Fjerner supra- og infralineære notater
- Skånsom fjerning av tagger
- Diverse

BETA 0.3
- Fikset diverse encoding-feil som hadde med &ampersand å gjøre. Alt SKAL nå oversettes til ren UTF-8.. SKAL det altså.
- Ny dynamisk rekkefølge på forsider. Støtter flere forsider og tekster i én fil.
- Lettere optimisering (fortsatt tregt, altså). Fjernet ca 600 linjer kode
- Støtte for text-taggen. Kan utvikles til å støtte brev eller hva annet det måtte være.
- La til flere parametre for konvertering
- Enda mer skånsom taggfjerning
- Kommentarer fjernes gjennom XML-strukturen (BS4), ikke RegEx
- Samleparanteser fjernes.

* Dikt inkluderer sidetall og innholdsfortegnelse. Innholdsfortegnelsen brukes i blant annet manuskripter.

0.3 HOTFIX
- Tagger ble ikke slettet riktig.

RELEASE 1.0.0
- Litt kodevask for økt brukervennlighet.
- Sjekket konvertert Brand, Episk Brand, Solness, Gildet, SS, C2, diktsamling '48 med mer mot tekstene på HIS.
 Bruk IbsensXMLstrip.ipynb, ikke beta eller alfa.

1.0.1 (Hotfix)
- Fikset en skrivefeil som induserte total systemsvikt.
- Metadata får nå en lett språkstell. Det blir ikke akkurat lettere å lese, men det er nå der.
- En finner dato og versjon på programmet som utførte konversjonen i samtlige metadata-filer. Dette reduserer faren for at noen bruker utdaterte versjoner.

1.0.25 Variant
- Noen tagger bør nå beholdes.
