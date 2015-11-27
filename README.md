#KITplayground

## Einrichten der Wordpress-Installation

### Repository klonen

Zuerst muss das Repository in den richtigen XAMPP-Ordner geklont werden. Der Dateibaum sollte später so aussehen:

	.../xampp/htdocs/
					wordpress/
					README.md

Wenn ihr über `git clone` euch das Repository holt, legt git einen Unterordner an. Dann kann es Probleme mit der Datenbank geben (wo wir da den Pfad ändern müssen wissen wir gerade nicht). Einfach alle(!) Inhalte aus dem Unterordner (inklusive des versteckten `.git`-Ordners) eine Ebene höher schieben und alles sollte passen.

### Datenbank aufsetzen

Damit Wordpress auf die richtige Datenbank zugreift, müsst ihr eine Datenbank anlegen. Startet sowohl den Apache-Server als auch MySQL über das XAMPP-Control Panel und ruft `localhost/phpmyadmin/` auf.

Dort müsst ihr eine neue Datenbank namens `wp` anlegen, bei 