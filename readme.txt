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