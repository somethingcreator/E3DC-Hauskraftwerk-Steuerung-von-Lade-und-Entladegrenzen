# Intro
Aktuell fehlen mir im Bereich der Speicherladung von E3DC Hauskraftwerk (S10X) folgende zwei Funktionen:
1. Ladezustandsbegrenzung zur Vermeidung der Aufladung auf 100%. Es ist die häufigste kritische Rückfrage, wofür die Begrenzung des Ladezustands gut sein soll. E3DC habe sich doch was beim ausgeklügelten BMS gedacht. Am besten möchte ich auf die Erklärung aus "erster Hand" unter (https://www.youtube.com/watch?v=GsWnoaxhQII) hinweisen. Sinngemäße Aussage vom CEO von E3DC: "Der hohe Ladezustand ... insbesondere bei Sommertemperaturen... ist wie Zigaretten rauchen und keinen Sport treiben...". Damit ist, denke ich, alles gesagt.  Wetterprognose-basierte Verfahren sind aus meiner Sicht noch entweder unzuverlässig oder recht aufwendig einzurichten. Daher habe ich für mich diese einfache Funktion entwickelt. Diese macht nichts anders, als die Ladesperre beim Erreichen eines Grenzwerts z.B. (80%) zu setzen. Fällt der Ladezustand auf den Grenzwert - Offset (z.B. 20%) = 60%, wird die Ladesperre wieder aufgehoben. Dies soll häufige Modi-Wechsel verhindern. 

2. Genau so, aber mit dem umgekehrten Vorzeichen funktioniert die Entladesperre. Diese soll verhindern, dass der Ladezustand des Speichers unter den eingestellten Grenzwert (z.B. 40%) fällt. Die im E3DC vorhandene Notstromreserve-Funktion führt dazu, dass der Speicher ständig nachgeladen wird, um die Notstromreserve zu erhalten. Die Erfahrung zeigt, dass ein paar sonnige Tage im Winter ausreichen, um ohne Nachladen aus dem Netz mit dieser Funktion einen ausreichenden Ladezustand als Reserve zu erhalten. Umgekehrt wird die Entladesperre aufgehoben, wenn der Ladezustand auf Grenzwert + Offset (z.B. 20%) = 60% steigt. Die Notstromreserve im E3DC kann so auf 0% eingestellt werden. Die automatische Entladesperre hat somit eine dopplete Funktion. Zum Einen wird die Speicher-Tiefentladung verhindert. Zum Anderen ist sie eine stromsparende Alternative zur Notstrom-Reserve von E3DC. In diesem Winter hatte ich trotz des überwiegend ungünstigen Wetters und relativ geringer installierter kWP-Leistung immer eine ausreichende Speicherladung als Notreserve (40%-60%) und musste kein einziges Mal aus dem Netz nachladen.   

Zudem kann mit den beiden Automaten der Speicherladezustand automatisch in einem Bereich z.B. zwischen 20%-80% gehalten werden. Der Grenzwert für Entladesperre kann im Sommer z.B. auf 20% oder auch 10% abgesenkt werden, ohne die Autarkie zu schmälern.

Alle Parameter (Grenzen, Offsets) sind konfigurierbar. Beide Automaten lassen sich einzeln sich an- und ausschalten.

**Wichtiger Hinweis:** ich entwickelte diese Funktion nur für meinen eigenen Bedarf. Ich leiste weder Support, noch übernehme ich Garantie oder Haftung für irgendwelche Schäden, sollte jemand meine Entwicklung bei sich einsetzen. Ich bin auch kein Experte für raspberry/js/iobroker, sondern mache das seit einiger Zeit als Lückenfüller-Hobby.
Der Code kann frei genutzt und eigenständig weiterentwickelt werden. Verbesserungsvorschläge, Ideen gerne willkommen, ohne dass ich ihre Umsetzung versprechen kann. Ich werde es nach Möglichkeit versuchen, gerne in Kooperation ;). 

# Voraussetzungen
- Iobroker (bei mir auf raspberry PI 5)
- Adapter (Nutzer-individuell konfiguriert)
  - Javascipt mit blockly
  - vis.2.0 (optional, falls Steuerung über view erfolgen soll)
    - vis-justgage
    - vis-materialdesign
    - vis-material-advanced
    - vis-inventwo
    - vis-2-widgets-gauges
  - e3dc-rscp
  - web
  - **Im E3DC-Portal/App soll für jeden Wochentag je !1! Eintrag für Ladesperrzeit und Entladesperrzeit mit Zeit von 00:00 bis 00:00 eingestellt werden**


# Einrichtung

1.	Importieren datapoints
2.	Importieren blockly-scripts
3.	Importieren views (optional, falls Steuerung über view erfolgen soll)
4.	Aktivierung javascript

Steuerung entweder über view oder über Datapoints. Diese sind, denke ich, selbsterklärend.
   
![Unbenannt](https://github.com/somethingcreator/E3DC-Hauskraftwerk-Steuerung-von-Lade-und-Entladegrenzen/assets/160220332/92723e0f-1cd6-45ab-8bd9-4364ce196985)


Ich habe für mich unter Einsatz von history und flot noch ein paar Diagramme erstellt. Ich überlasse es aber euch, sich davon (un)inspirieren zu lassen :)

![Unbenannt](https://github.com/somethingcreator/E3DC-Hauskraftwerk-Steuerung-von-Lade-und-Entladegrenzen/assets/160220332/200b127a-472c-4bb2-88eb-0c4004cbd45f)
