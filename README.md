# Ai-Thinker-ESP32-CAM ist nicht gleich Ai-Thinker-ESP32-CAM
Die Ursache allen Übels ist eine veränderte Schaltung die sich aber nicht in den Beschreibungen widerspiegelt

Da ich eine kleine Armada an Ai-Thinker-ESP32-Cams habe und mir das Leben vereinfachen wollte habe ich mir ein Bundle bestehend aus Cam und dem ESP32-CAM-MB Programmer gekauft. Gleich einen Doppelpack. Alles funktionierte wunderbar automagisch. Wie es immer läuft, man achtet bei vielen gleich aussehenden Devices nicht unbedingt welches wann womit kam also kam es wie es kommen musste die Cam auf den Programmer gesteckt, nix ging. Nichts mehr mit automagisch. Nicht mal der Reset Button des Programmers funktionierte mehr. Gut, mit etwas Logistik und Fingeracrobatik kann man trotzdem programmieren:

1. in Arduino den richtigen Port aktivieren
2. den seriellen Monitor aufrufen
3. den IO0 Button drücken und gedrückt halten
4. den Reset Button auf der Cam kurz drücken und danach den IO0 Button los lassen
5. im seriellen Monitor beobachten ob die Cam auf das File wartet
6. wenn ja, in Arduino die Kompilation und Upload starten
7. wenn hochgeladen den Reset Button an der Cam noch mal kurz drücken und alles wird gut

Nun hat es mich echt gewurmt wieso der Programmer kaputt sein soll. Also im Internet nach der Shematic gesucht und tatsächlich auch gefunden. Nur, irgendwie kann das doch gar nicht sein das da ein Masse-Pin als Reset verwendet wird! 
Dann müssten ja die Cams unterschiedlich sein!
Ja, sie sind tatsächlich unterschiedlich! Die Entwickler haben still und heimlich einen der Kritikpunkte das der Reset nicht nach aussen geführt wurde behoben aber weder in der offiziellen Shematic dokumentiert noch gibt es bei den Kaufangeboten für die Bundles einen Hinweis. 
Also, wenn man neu kauft immer ein Bundle mit Programmer nehmen dann ist die Wahrscheinlichkeit hoch das es die neue Revision der Cam mit Reset-Pin ist.

Ok, fairerweise muss ich anmerken das die Revision unterschiedlich ist. Die Version mit Reset-Pin ist 2366 und die ohne 2368. Muss ich nicht verstehen.
Aber wenigstens ist der Aufdruck an dem Pin nicht GND sondern GND/R wenn man Reset hat.

![20230330_124918](https://user-images.githubusercontent.com/55184135/228832775-0be4f105-e7c0-4734-b983-364d2cb34589.jpg)
Beide Revisionen nebeneinander

![20230330_124843](https://user-images.githubusercontent.com/55184135/228832921-b5cbc80c-ec52-42a9-a008-3725931c7110.jpg)
Die Revision OHNE Reset

![20230330_124817](https://user-images.githubusercontent.com/55184135/228833015-e9392964-1a29-4009-8ded-80d22c83acb1.jpg)
Die Revision MIT Reset

Oben links in der Ecke kann man schön die Hardwarerevisionen ablesen und an dem Pin der am nächsten zur Power-LED ist die unterschiedlichen Aufdrucke. Ein guter Hinweis ist auch die Anzahl der Widerstände in dem Block nahe dem Pin. Wenn es nur 4 Widerstände sind dann kein Reset. Ich hoffe es sind Widerstände denn einen Bestückungsplan habe ich nicht.
