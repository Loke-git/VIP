https://github.com/Loke-git/VIP
Virtual Ibsen Platform [VIP]
Primary objectives
    FAIR-conversion
    Access for multiple concurrent users to multiple datasets
        *Worldwide - English language
        Linked open data
    ""Futureproofing"" (see FAIR)
        Markdown...

Secondary objectives
    Integrate external digital holdings at partner institutions through API, such that these holdings are also available through the VIP platform
        Like automated API-calls to partners?
    Create an integrative platform for data sharing and collaboration among users across the globe and from multiple disciplines.
        Async JS client-facing website?

Holdings
    1) Henrik Ibsens Skrifter
    2) IbsenStage
    3) the International Ibsen Bibliography
    4) the Ibsen Archive inherited from the cached National Library Ibsen.net website

21.02.2022
Endelig adgang til filene! Ekstern DTD i Py var kronglete, så jeg har konvertert denne til en csv vi kan referere til for unicode decoding. TODO: bare erstatt alt det der i selve translation.csv-filen så har vi kodet og dekodet unicode.
Programmet leser XML-filene OK. Har tilgang på XML-knaggene, så det skal ikke være for vanskelig å slette hele tagger.
RegEx for å utradere alle resterende tagger uten innhold fungerer fint. Det er siste steg i vaskingen.
Lastet opp prosjektet på GitHub (https://github.com/Loke-git/VIP).

22.02.2022 / v0.0.1
Oppdatert oversettelser. Implementert glob.glob for å finne alle xmler rekursivt. Lagt til OPT-IN sletting av hele tagger (med innhold). Etter regex av alle tagger står vi igjen med noe tjafs i testfilen.
TODO: vi har globglob, og kan sikkert skape et nytt directory fra den for rentekstfiler.
TODO: sjekk hvilke tagger som skal utraderes helt.
TODO: sjekk hvilke notater som må inn og passes på.
TODO: omform tittel- og metadata til noe mer "rent" og prepend filene med disse igjen.

0.0.2
Foreach-loop for å hente fra glob.glob og skrive tilsvarende struktur i ny folder. Funker bra!
TODO: Kombiner globglob med beautifulsoup.
TODO: sjekk hvilke tagger som skal utraderes helt.
TODO: sjekk hvilke notater som må inn og passes på.
TODO: omform tittel- og metadata til noe mer "rent" og prepend filene med disse igjen.

... ja, da glemte jeg å skrive i loggen i et par dager. Uker. Uansett!

xmlStrip 0.1 "Dvergbjerk"
* Metadata hentes ut (men behandles ikke) fra fil og legges i egen undermappe.
* Konverterer alle html/jalla-koder til ASCII. Si i fra om du finner en som ikke er konvertert.
* Sletter all formatering og henter (ideelt sett) kun ut Ibsens egen tekst.
** Sletter alt Ibsen slettet.
* Mange insektfikserier [bugfixes].

xmlStrip 0.1.3

- Fikset i, det var et RegEx som var litt for grådig. 

- Instanser av &typHyp; ble oversatt for tidlig i prosessen. Linjeskift i XML-filene tolkes som mange mellomrom, og typhyp ble fjernet før disse mellomrommene ble komprimert fra mange til ett - det er derfor det ble ett resterende mellomrom ved orddeling. Nå fjernes "&typHyp; " for seg selv etter at alle multimellomrom er borte, og resultatet blir (fra Du41113a-f_NBO):

    Der er to slags åndelige love, to slags samvittigheder, en i manden og en ganske anden i kvinden. De forstår ikke hinanden.

- Programmet sjekker nå om det er en rolleliste. Om det er en rolleliste blir denne hentet ut og satt foran <body>-elementet, som betyr at den (skal) bli sittende foran alt annet og ikke løpe noen risiko for å bli slettet. Vi er også nesten helt garantert at alle XML-filer har et <body>-element! Samme metode kan brukes for å hente ut tittelinformasjon og annet ønskelig. :) Rentekst Du8952 åpner nå slik:

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
- Støtte for <text>-taggen. Kan utvikles til å støtte <brev> eller hva annet det måtte være.
- La til flere parametre for konvertering
- Enda mer skånsom taggfjerning
- Kommentarer fjernes gjennom XML-strukturen (BS4), ikke RegEx
- Samleparanteser fjernes.

* Dikt inkluderer sidetall og innholdsfortegnelse. Innholdsfortegnelsen brukes i blant annet manuskripter.

0.3 HOTFIX
- Tagger ble ikke slettet riktig.