# Intro
Aktuell fehlen mir im Bereich der Speicherladung von E3DC Hauskraftwerk (S10X) folgende zwei Funktionen:
1. Ladezustandsbegrenzung zur Vermeidung der Aufladung auf 100%. Wetterprognose-basierte Verfahren sind aus meiner Sicht entweder unzuverlässig oder recht aufwendig einzurichten. Daher habe ich für mich diese einfache Funktion entwickelt. Diese macht nichts anders, als die Ladesperre beim Erreichen eines Grenzwerts z.B. (80%) zu setzen. Fällt der Ladezustand auf den Grenzwert-Offset (z.B. 20%) = 60%, wird die Ladesperre wieder aufgehoben. Dies soll häufige Modi-Wechsel verhindern.

2. Genau so, aber mit dem umgekehrten Vorzeichen funktioniert die Entladesperre. Diese soll verhindern, dass der Ladezustand des Speichers unter den eingestellten Grenzwert (z.B. 40%) fällt. Die im E3DC vorhandene Notstromreserve-Funktion führt dazu, dass der Speicher ständig nachgeladen wird, um die Notstromreserve zu erhalten. Die Erfahrung zeigt, dass ein paar sonnige Tage im Winter ausreichen, um ohne Nachladen aus dem Netz mit dieser Funktion einen ausreichenden Ladezustand als Reserve zu erhalten. Umgekehrt wird die Entladesperre aufgehoben, wenn der Ladezustand auf Grenzwert + Offset (z.B. 20%) = 60% steigt.

Zudem kann mit den beiden Automaten der Speicherladezustand völlig automatisch im Bereich zwischen 20%-80% gehalten werden. Der Grenzwert für Entladesperre kann im Sommer z.B. auf 20% abgesenkt werden, ohne die Autarkie zu schmälern.

Wichtiger Hinweis: ich entwickelte diese Funktion nur für meinen eigenen Bedarf. Ich leiste weder Support, noch übernehme ich Garantie oder Haftung für irgendwelche Schäden, sollte jemand meine Entwicklung bei sich einsetzen. Ich bin auch kein Experte für raspberry/js/iobroker, sondern mache das seit ca. einem Monat als Lückenfüller-Hobby.
Der Code kann frei genutzt und eigenständig weiterentwickelt werden. Verbesserungsvorschläge, Ideen gerne willkommen ohne, dass ich ihre Umsetzung versprechen kann.

# Voraussetzungen für den Einsatz
- Iobroker (bei mir auf rasperry PI 5)
- Adapter (Nutzer-individuell konfiguriert)
  - Javascipt mit blockly
  - vis.2.0
  - vis-justgage
  - vis-materialdesign
  - vis-material-advanced
  - vis-inventwo
- e3dc-rscp
- web
- **Im E3DC-Portal/App soll für jeden Wochentag je !1! Eintrag für Sperrzeit/Entsperrzeit mit Zeit von 00:00 bis 00:00 eingestellt werden**


# Einrichtung:

1.	Importieren datapoints
2.	Importieren blockly-scripts
3.	Importieren views
4.	Aktivierung javascript

![scrsh](https://github.com/somethingcreator/e3dc_chargelimitmanager/assets/160220332/1254350b-c2c5-4d4e-8a5d-5bb56f226602)

Ich habe für mich unter Einsatz von history und flot noch ein paar Diagramme erstellt. Ich überlasse es aber euch, sich davon zu(un)inspieieren :)

![diagramme](https://github.com/somethingcreator/e3dc_chargelimitmanager/assets/160220332/2b440320-9958-4195-8794-e392a10304f5)
