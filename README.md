#KITplayground

## Einrichten der Wordpress-Installation

### Repository klonen

Zuerst muss das Repository in den richtigen XAMPP-Ordner geklont werden. Der Dateibaum sollte später so aussehen:

	.../xampp/
			htdocs/
				wordpress/
				docs/
				README.md

Wenn ihr über `git clone` euch das Repository holt, legt git einen Unterordner an. Dann kann es Probleme mit der Datenbank geben (wo wir da den Pfad ändern müssen wissen wir gerade nicht). Einfach alle(!) Inhalte aus dem Unterordner (inklusive des versteckten `.git`-Ordners) eine Ebene höher schieben und alles sollte passen.

### Datenbank aufsetzen

#### Windows

Damit Wordpress auf die richtige Datenbank zugreift, müsst ihr eine Datenbank anlegen. Startet sowohl den Apache-Server als auch MySQL über das XAMPP-Control Panel und ruft `localhost/phpmyadmin/` auf.

Dort müsst ihr eine neue Datenbank namens `wp` anlegen, bei Kollation/Collation haben wir `utf8mb4_unicode_ci` vewendet. Dann wählt ihr die Datenbank in der linken Spalte aus, geht auf Import und importiert das Dump (`docs/wp.sql`).

#### Mac

Am einfachsten ist vermutlich folgende Vorgehensweise:

1. Über das Terminal MariaDB Monitor starten (kommt mit XAMPP for Mac): `/Applications/XAMPP/xamppfiles/bin/mysql -u root`
2a. Falls DB noch nicht vorhanden, anlegen: `create database wp`
2b. Für einen Data-Dump erst Database löschen und neu anlegen: `drop database wp; create database wp;`
3. Mit der Datenbank verbinden: `connect wp`
4. Dump einspielen: `source /Applications/XAMPP/xamppfiles/htdocs/docs/wp.sql`
5. Beenden von MariaDB Montior über `Ctrl + C`

Sollte zu irgendeinem Zeitpunkt ein `->` erscheinen, ist ein SQL-Statement noch nicht beendet. Also einfach `;` eingeben und `Enter` drücken.

### Wordpress-Seite aufrufen

Unter `localhost/wordpress/` sollte nun die Seite fehlerfrei mit zwei Beiträgen erscheinen. Unten auf der Seite findet ihr den Login.

## Wordpress-Installation gemeinsam nutzen

So haben wir jetzt zwar alle eine eigene Datenbank, das ist zum Entwicklen ja aber nicht so wild. Vielleicht müssen wir am Anfang häufiger ein Dump austauschen, damit jeder mit ähnlichen Kategorien etc. arbeitet. Für die Arbeit am Theme sollte das aber nicht so wild sein.

### Themes
#### wp_test
Dieses Theme ist [underscores.me](http://www.underscores.me), welches als Grundlage für eine eigene Entwicklung genutzt werden kann.

#### [Bootstrap Four](https://wordpress.org/themes/bootstrap-four/)
Ebenfalls ein Theme welches sich an Entwickler richtet, sieht aber schonmal mehr nach irgendwas aus als wp_test.


### Plugins installieren
Das geht nicht über die normale Installation, da wir vom lokalen Server keinen Zugriff auf FTP haben. In der `wp-config.php` gibt es den Befehl `define('FS_METHOD', 'direct');`. Wird dieser einkommentiert, wird kein FTP von Wordpress benötigt.

Das Plugin kann aber manuell heruntergeladen werden und in `wordpress/wp-content/plugins` abgelegt werden. Das Plugin liegt dann auch im Repository, muss in den Wordpress-Einstellungen aber erst noch aktiviert werden.

#### vorinstallierte Plugins
- Akismet (deaktiviert)
- Hello Dolly (deaktiviert)

#### installierte Plugins
- Event Organiser (aktiviert)