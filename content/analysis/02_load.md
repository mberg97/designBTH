---
Title: Analys kmom05
Description: Analys for kmom05
Template: kmom
---


Utvärdera webbplatsers laddningstid och användbarhet
=======================

I denna uppgiften analyserar jag 3 webbplatsers laddningstid och analysera om det finns något som webbplatsen kan förbättra med laddningstiden samt användbarhet.

Urval
-----------------------
Jag valde samma 3 webbplatser som i förra uppgiften eftersom för att få ett resultat som är relevant för mig krävs det att webbplatserna
ska ha ungefär samma syfte. Eftersom bilder också har stor påverkan på laddningstid hade det varit problematiskt att jämföra webbplatser som e-handels affärer med
väldigt många bilder pga annonser med en webbplats som kanske inte ens har någon bild. Det hade inte gått att jämföra direkt. Därför valde jag Amazon, Elgiganten och Media Markt (svenska versionen för alla).

Metod
-----------------------

I denna analysen har jag använt https://developers.google.com/speed/pagespeed/insights/ samt "nätvärk" tabben i devtools för Google Chrome (Firefox fungerade inte speciellt bra för mig). Alla resultaten är tagen från 3 mätningar med medelvärdet publicerat i spreadsheeten.


Resultat
-----------------------
Alla resultaten i spreadsheeten har mäts 3 gånger och räknat ut medelvärdet.
https://docs.google.com/spreadsheets/d/1AODHT41-n8LqcPtDPHxEUZc0QzSbCy1i_LcgrSeN-sk/edit#gid=0

amazon.se
![amazon](%assets_url%/img/amazon.png) {.store-img}

Fältdata
First Contentful Paint (FCP) - 1,1 s
First Input Delay (FID) - 41 ms
Largest Contentful Paint (LCP) - 1,6 s
Cumulative Layout Shift (CLS) - 1,34

Labbdata
First Contentful Paint - 0,7 s
Time to Interactive - 0,7 s
Speed Index - 1,7 s
Total Blocking Time - 0 ms
Largest Contentful Paint - 1,7 s
Cumulative Layout Shift - 0,003


De viktigaste sakerna att förbättra för Amazon på diagnostik (finns inga "möjligheter" för Amazon) är att text förblir synlig medan webbteckensnitten läses in, göra så att passiva lyssnare kan användas för att förbättra rullningsprestanda, undvika ett så stort DOM-träd och slutligen att skicka statistiska tillgångar med en effektiv cachelagringspolicy.

elgiganten.se
![elgiganten](%assets_url%/img/elgiganten.png) {.store-img}

Fältdata
First Contentful Paint (FCP) - 0,8 s
First Input Delay (FID) - 73 ms
Largest Contentful Paint (LCP) - 3,2 s
Cumulative Layout Shift (CLS) - 0,13

Labbdata
First Contentful Paint - 0,5 s
Time to Interactive - 1,7 s
Speed Index - 0,7 s
Total Blocking Time - 340 ms
Largest Contentful Paint - 1,7 s
Cumulative Layout Shift - 0,013

För Elgiganten finns det mer att förbättra än amazon såsom "Möjligheter": Att läsa in viktiga resurser i förväg(0,36s) samt att ta bort resurser som blockerar renderingen(fel). För diagnostik finns det några kritiska saker såsom att göra så att passiva lyssnare kan användas för att förbättra rullningsprestanda, undvika ett så stort DOM-träd och slutligen att skicka statistiska tillgångar med en effektiv cachelagringspolicy.

mediamarkt.se
![mediamarkt](%assets_url%/img/mediamarkt.png) {.store-img}

Fältdata
First Contentful Paint (FCP) - 1,3 s
First Input Delay (FID) - 12 ms
Largest Contentful Paint (LCP) - 3,3 s
Cumulative Layout Shift (CLS) - 0,78

Labbdata
First Contentful Paint - 1,3 s
Time to Interactive - 4,0 s
Speed Index - 2,3 s
Total Blocking Time - 260 ms
Largest Contentful Paint - 2,7 s
Cumulative Layout Shift - 0,353

Mediamarkt har 2 "Möjligheter" att ta bort JavaScript som inte används(0,94s) och att ta bort resurser som blockerar renderingen(0,39s). Därefter finns det flera kritiska saker att förbättra under "Diagnostik" såsom att se till att all text är synlig medan webbteckensnitten läses in, att passiva lyssnare ska användas för att förbättra rullningsprestanda, att undvika "document.write()", inte ha ett så stort DOM-träd, skicka statiska tillgångar med en effektiv cachelagringspolicy och att minska arbetsbelastningen på modertråden(2,8s) samt mindre körningstid för JavaScript(1,6s).



Analys
-----------------------
Baserat på resultaten kan jag konstatera att även om ingen av webbplatserna har ett "grönt" resultat på pagespeed (resultat av 90-100) så finns det ändå väldigt stora skillnader på laddningstider och prestanda på webbplatserna. Amazon baserat på dessa testerna med devtools network och pagespeed är den bäst optimiserade webbplatsen utan tvekan. Det ser vi direkt att de inte ens har några "Möjligheter" på pagespeed ens medan båda Eliganten samt Media Markt har det. Något som alla tre webbplatserna har gemensamt är att alla har problemet att "passiva lyssnare används inte för att förbättra rullningsprestanda" och att de har för stora DOM-träd (Amazon 2083-, Elgiganten 11349- och Media Markt 4069 element). Både Amazon och Media Markt har också problemen att göra så att all text är synlig medan webbteckensnitten läses in samt att. Alla 3 webbplatserna har också problemen att "Skicka statiska tillgångar med en effektiv cachelagringspolicy". Dock har Amazon (16 resurser hittades) och Elgiganten (9 resurser hittades) den som inte ett kritiskt (rött) problem, utan bara gult medan Media Markt (84 resurser hittades) har det som ett kritiskt problem.

Efter att ha analyserat dessa 3 webbplatsers laddningstider och användbarhet kan jag hävda att Amazon är bäst, sedan Eliganten och sist Media Markt. Pagespeed som jag först använde för att analysera webbplatsens laddningstid indikerade att just detta skulle hända från början. Det är dock viktigt att notera att skillnaden angående laddningstiden är väldigt liten mellan Amazon och Elgiganten är 0.16s och att Elgiganten har mer än dubbelt så mycket resurser att ladda in. Elgiganten har dessutom olika tydliga möjligheter att ladda sidan snabbare jämfört med Amazon. Media Markt har aldelles för mycket som de måste förbättra för att bli i samma liga som Amazon och Elgiganten. Det största problemet för Media Markt är JavaScripten på webbplatsen.

Med det sagt tycker jag inte att Media Markts webbplats är problematisk att använda på min dator. Jag märker faktiskt inte att den laddas något längre än Amazon och Elgiganten. Även på mobilen där Media Markt har 11 i betyg finner jag inget problem rent praktiskt. För mig är laddningstiden som är acceptabel beroende på vad för sorts webbplats det är. Men jag skulle säga att mindre än 3 sekunder är snabbt och 5 sekunder eller mer är långsamt.


Referenser
-----------------------
https://developers.google.com/speed/pagespeed/insights/


Övrigt
-----------------------

Mattias Berg
