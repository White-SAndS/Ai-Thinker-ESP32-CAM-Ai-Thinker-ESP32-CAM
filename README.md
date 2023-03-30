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

Nun hat es mich echt gewurmt wieso der Programmer kaputt sein soll. Also im Internet nach der Shematic gesucht und tatsächlich auch gefunden. Nur, irgendwie kann das doch gar nicht sein das da ein Masse-Pin als Reset verwendet wird! Dann müssten ja die Cams unterschiedlich sein!
Ja, sie sind tatsächlich unterschiedlich! Die Entwickler haben still und heimlich einen der Kritikpunkte das der Reset nicht nach aussen geführt wurde behoben aber weder in der offiziellen Shematic dokumentiert noch gibt es bei den Kaufangeboten für die Bundles einen Hinweis. 
Also, wenn man neu kauft immer ein Bundle mit Programmer nehmen dann ist die Wahrscheinlichkeit hoch das es die neue Revision der Cam mit Reset-Pin ist.
