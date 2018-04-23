---
layout: post
title:  "Schroedinger HTML CSS JS"
date:   2000-01-01 00:00:00 +0100
categories: Tutorial
---
# Schrödinger  HTML5 und CSS3
**DNS** steht für Domain Name System und ist ein System von Servern, deren Aufgabe es ist, Domänennamen in sogenannte IP-Adressen zu übersetzen.
Mit dieser IP- Adresse kann dann der richtige Server erreicht werden. 
**URL** steht für Uniform Resource Locator
ist eher eine Anweisung, wie man zu der Adresse gelangt. Es gibt neben HTTP viele weitere Protokolle, alle mit einem speziellen Einsatzgebiet: FTP für Dateitransfer, SMTP, um E-Mails zu versenden, XMPP für Instant Messaging 
**HTTP** steht für **Hypertext Transfer Protocol**
Ein verwandtes Protokoll ist HTTPS. Das „S“ steht für Secure
file://. Das File-Protokoll greift auf das lokale Dateisystem zu.
Mit einem #, am Ende einer URL angehängt, gibt das Fragment an, zu welcher Sprungmarke des Dokuments gesprungen werden soll.Falls es die genannte Sprungmarke nicht gibt, wird das Fragment ignoriert. Es gibt in diesem Fall keinen Fehler.
Und dann gibt es noch ein Element: den Query String. Nur Protokoll und Domäne müssen in einer absoluten URL zwingend vorhanden sein, alle anderen Teile sind optional. http://www.schoedingersseite.de?suche=katze#suchergebnis hat zum Beispiel Query String und Fragment, aber keinen Pfad. Trotzdem ist die URL gültig.
noch ein URL-Bestandteil: der Port. Man muss den Port fast nie in einer URL angeben, weil es für die meisten Protokolle einen Standardport gibt. HTTP liegt zum Beispiel fast immer auf Port 80. Wenn HTTP auf einem anderen Port liegt, gibt es eigentlich nur zwei Mög- lichkeiten, warum: Entweder der Server wird nur zur Ent- wicklung benutzt und soll vom Internet aus nicht erreichbar sein, oder der Besitzer wollte den HTTP-Dienst verstecken,
80 ist der Standardport für HTTP.
443 für HTTPS.
Dabei ist HTTP zustandslos (**stateless**). Mit jedem Request müssen wieder alle deine Informationen mitgegeben werden.

Header Beispiel **GET**
GET /index.html HTTP/1.1
User-Agent: Mozilla/5.0 (Windows NT 5.2; WOW64; rv:15.0) Gecko/20100101 Firefox/15.0.

GET , lädt die Ressource. Der relative Anteil der zu ladenden URL – der Server weiß ja schon, wer er ist, also brauchen wir den Hostname nicht. 
Der User-Agent-Header teilt dem Server mit, welcher Webbrowser und welches Betriebssystem die Anfrage stellen. Ein Request kann beliebig viele Header enthalten.
Und die Antwort des Servers dazu
HTTP/1.1 200 OK
Content-Length: 17438
Content-Type: text/html; charset=UTF-8

Antwort: wieder die Protokoll-version, falls wir sie inzwischen vergessen haben, Der Statuscode. Hieran erkennt der Browser, ob alles funktioniert hat, 
Statusmeldung: dieselbe Information wie der Statuscode, aber für uns Nicht-Computer nett aufbereitet,Und auch die HTTP-Response kann Header enthalten. 
Content-Length sagt uns, wie viele Byte die Antwort enthält (ausgenommen Header und Statuszeile). 
Content-Type gibt an, dass in diesem Fall ein HTML-Dokument mit Encoding UTF-8 geliefert wird. Und das Document
**Statuscodes** 200 OK - bedeutet, dass alles funktioniert hat und die Ressource, die wir sehen wollen, geliefert wird
Statuscode      302  Found Es gibt den Inhalt zwar, aber nicht hier. Der Header Location enthält die Information, wo das Dokument jetzt zu finden ist Status 302 ist der richtigste Weg, den Leser auf eine andere Seite weiterzuleiten (Redirect).
304 Not Modifed - Der Inhalt wurde gefunden, aber wir haben die aktuelle Version des Inhalts schon im Cache (welche Version des Inhalts wir kennen, weiß der Server aus anderen Headern, die wir senden).
400 Bad Request - An unserem Request war etwas faul. Das kann ein Header oder Parameter sein, den wir nicht oder falsch gesetzt haben, oder ziemlich alles andere, das dem Server nicht passt.
401 Unauthorized - Nur angemeldete User dürfen diesen Inhalt sehen, und wir sind nicht angemeldet.
403 Forbidden Jetzt sind wir zwar angemeldet, aber dieser Inhalt ist für uns nicht freigegeben.
404 Not Found Diesen Inhalt gibt es nicht.
500 Internal Server Error Der Server ist beim Versuch, den Request zu verarbeiten, vor eine Wand gelaufen. Status 500 wird dir häufiger begegnen, wenn du eigene Server-Anwendungen schreibst, zum Beispiel in PHP oder Java.
   
Dazu kommen Bilder, Stylesheets, JavaScripts und einiges andere. Das alles sind eigenständige Ressourcen, die mit einem eigenen Request geladen werden müssen. 
20 oder mehr Requests für eine Seite sind keine Seltenheit:
Apache-Server ist schon auf mac.. fur Linux XAMMP..

**ARPANET** 
Am Anfang, lange bevor es Webseiten gab oder jemand seinen Computer zu Hause an ein Telefon angeschlossen hat, gab es das ARPANET. Das ARPANET wurde von der Advanced Research Projects Agency (ARPA) des US Verteidigungsministeriums entwickelt, und es war damals ein revolutionärer Schritt: Es war das erste paketbasierte (packet switched) Computernetzwerk. Es war auch vorher möglich, Computer miteinander zu verbinden, aber die Verbindungen waren leitungsbasiert (circuit switched): Es wurde eine durchgehende elektrische Leitung von einem Computer zum anderen her- gestellt. Es funktionierte, aber die Leitung war belegt und stand für andere Computer nicht zur Verfügung.
Die revolutionäre Idee des ARPANET war es, die zu übertragenen Daten in Pakete zu zerlegen und jedes Paket mit einer Empfängeradresse zu versehen, genau wie ein Postpaket
Die erste Nachricht im ARPANET wurde am 29.10.1969 gesendet
Mit dem Wissen, das aus und mit ARPANET gewon- nen wurde, wurde 1982 eine Sammlung von Protokollen mit dem Namen Internet Protocol Suite standardisiert. Diese Protokolle sind bis heute im Einsatz und halten das weltweite Computernetz Internet zusammen.
Während der 1980er Jahre wurde das Internet weiter ausgebaut, Dienste wie E-Mail und Newsgroups gab es schon, auch Datentransfer von einem Computer zum anderen war natürlich möglich, aber Informationen waren noch immer unabhängig voneinander, genau wie einfache Textdateien im Dateisystem.
Tim Berners-Lee. Er schrieb den ersten Projektvorschlag für das World Wide Web 1989 und überarbeitete ihn 1990.August 1991 entwickelte Tim den ersten Webserver (CERN HTTPd), den ersten Webbrowser (der gleichzeitig auch der erste Editor für Webseiten war), die Sprache HTML, das Protokoll HTTP und die URL. 
Am 6. August 1991 ging die erste Website des World Wide Web online.
1993 wurde der erste grafische Webbrowser entwickelt: Mosaic.

## Jetzt kommt Farbe ins Spiel 

Ein <span> ist eigentlich nichts. Gar nichts. Ein Style wird definiert dazu..
span{
color: red;
background-color: black; }

Dafür in Head habe ich <link href="styles.css" rel="stylesheet"/>
Es gibt für rel noch viele weitere Werte…rel="shortcut icon"zeigt auf ein Bild im ICO-Format, das in der Adresszeile und bei Bookmarks angezeigt wird
Das <body>-Tag umfasst den gesamten Seiteninhalt, 
**Der id-Selektor**  mit ex #zweiter-absatz { color: red;}
**Der Klassen-Selektor**  .hobby {color: blue; }
**Wenn zwei Regeln die gleiche Priorität haben und die gleiche Eigenschaft definieren, dann gewinnt immer die Regel, die im Stylesheet weiter unten steht.**
das RGB Modell 
**RGB steht für „Red, Green, Blue“ und ist das verbreitetste Modell, Farben für den Computer anzugeben. **
Jede der Komponenten Rot, Grün und Blau wird als zweistellige, hexadezimale Zahl angegeben, also im Zahlensystem auf der Basis 16. 
color: #A300A3; Rotwert Grünwert Blauwert
Je höher der Wert einer Farbkomponente, desto intensiver ist diese Komponente in der Farbe vertreten. Sind die drei Werte gleich, handelt es sich um einen Grauton, von #000000 = Schwarz bis #FFFFFF = Weiß. Für die Erklärung, warum das so funktioniert, sind wir hier im falschen Buch. Es handelt sich um additive Farbmischung.
Gelb ist etwas tricky, gebe ich zu. **Gelb ist #ffff00**
die Funktionsnotation rgb() ex .blue {color: rgb(0, 0, 255);}
Das **HSL-Modell**, nach Hue (Farbton), Saturation (Sättigung) und Luminosity (Leuchtkraft).
mit **rgba()** noch eine weitere Funktion, bei der neben den RGB-Werten noch ein vierter Wert übergeben wird, der sogenannte Alpha-Wert. 
Alpha darf zwischen 0 und 1 liegen und gibt die Undurchsichtigkeit des Elements an. Ein Wert von 1 bedeutet, dass das Element komplett undurchsichtig ist
**opacity** 
Es gibt aber einen ganz wichtigen Unterschied zwischen opacity und rgba(): opacity gilt für Vordergrund und Hintergrund des Elements, es wird also alles transparent. Verwendet man dagegen rgba() für background-color, dann bleibt die Vordergrundfarbe zu 100 % undurchsichtig. 
Um den Hintergrund eines Elements vollständig durch- sichtig zu machen, kann man eine beliebige Farbe mit Alphawert 0 angeben: background-color: rgba(123, 204, 17, 0).Einfacherund leserlicher ist es aber, den speziellen Wert transpa- rent zu benutzen: background-color: transparent
background-image: url(images/bild.png);
background-repeat. Neben dem Defaultwert repeat gibt es noch no-repeat, um das Hintergrund- bild genau einmal anzuzeigen, und repeat-x bzw. repeat-y, um das Bild nur horizontal oder nur vertikal zu wiederholen.
background-position 
background-position
kann auch mit nur einem Wert angegeben werden. Dieser Wert wird dann für die horizontale und die vertikale Position verwendet.Schlüsselwörter left, center und right bzw. top, cen- ter und bottom. left. Wenn du eine Prozentangabe für background-position benutzt, zum Beispiel 10 %, bedeutet das auch nicht, dass das Bild bei der 10 %-Marke des Elements anfängt.
background-attachment legt fest, woran das Hintergrundbild befestigt wird: an der HTML- Seite oder am Browserfenster. Aus der Beschreibung ist vielleicht nicht offensichtlich, was der Unterschied ist, aber am Beispiel wird es klar. Der Defaultwert für background-attachment ist scroll, alles, was wir bisher gemacht haben, hatte diesen Wert
Es gibt noch die CSS-Eigenschaft background, die alle Hintergrundeinstellungen gleichzeitig setzt.
#image {background: #000000 url(bild.jpg) no-repeat scroll center top;}
Pseudoklassen
Bei den Links a, a:visited {color: blue}
:hover selektiert Elemente, über denen gerade der Mauszeiger schwebt 
 
4 - Kaskaden 
Cascading bedeutet, dass ein Element sein Aussehen vom umgebenden Element „erbt“.

Nicht alle Eigenschaften kaskadieren. Die background- Eigenschaften werden zum Beispiel nicht vererbt, jedes Ele- ment hat einen durchsichtigen Hintergrund, außer wenn am Element selbst etwas anderes deklariert wird.
font-size
absoluten und relativen Größenangaben.
In absoluten Größen gibt es zwei verbreitete Einheiten: px und pt. Pixel (px) sind die natürliche Einheit des Computers, ein Pixel ist genau ein leuchtender Punkt auf dem Bild- schirm. Points (pt) sind eher eine Leihgabe aus der traditionellen Welt des Drucks. So richtig mit toten Bäumen. Unheimlich, oder? Ein Point ist heute festgelegt als 1/72 inch,
Diese Definition von Points bedeutet, dass es keine Umrechnung zwischen pt und px gibt. Wie viele Pixel einem Point entsprechen, hängt von Größe und Auflö- sung des Bildschirms ab.Es gibt sogar noch mehr Einheiten für absolute Schriftgrößen, CSS erkennt auch Inch (in), Zentimeter (cm) und Millimeter (mm) sowie Picas (pc) – ein Pica entspricht 12 pt. 
Prozentangaben, Die andere verbreitete Einheit heißt em und tut das Gleiche, wird aber als Multiplikator angegeben, also zum Beispiel font-size: 1.2em;
Die Grundeinstellung für die Basisschriftgröße ist in allen verbrei- teten Browsern 16 px. Ein beliebter Trick ist deshalb, am Anfang desStylesheetseinbody {font-size: 62.5%;}zu setzen. Damit wird es bei Standardeinstellungen einfacher, zu rechnen, denn 62.5 % von 16 px sind 10 px. Du willst eine 20px- Schrift? Kein Problem, 2em. Von 16px ausgehend auf 20px? Keine Ahnung, ich hol den Taschenrechner. Und trotzdem funktio- niert alles auch bei abweichender Grundeinstellung.
font-style: italic; font-style ist eine Eigenschaft, die man sich sehr einfach merken kann, es gibt nämlich, realistisch betrachtet, nur zwei Werte: normal und italic.
Elemente, die direkt in einem anderen Element enthalten sind, nennt man Kinder (children) des Elements. Alle Elemente, die in einem anderen Element enthalten sind, egal, wie tief verschach- telt, nennt man die Nachfahren (descendants) des Elements.
<em> ist ein Tag, das den enthalte- nen Text besonders hervorhebt. Im Gegensatz zu <span> hat es also eine semantische Bedeutung.
font-family: "Klingon New", "Comic Sans", Arial, sans-serif; Bei Schriftarten, deren Namen Leerzeichen enthält, müssen immer Anführungszeichen gesetzt werden.
i cursive sind Schriften, die einer Handschrift ähnlich sehen (cursive hat nichts mit dem Deutschen kursiv zu tun, das heißt, wie du weißt, italic).
i fantasy umfasst Schriften, die dekorativ sind, aber Buchstaben enthal- ten, also zum Beispiel nicht WinDings, das nur Symbole enthält.
i monospace bezeichnet Schriftarten, in denen alle Zeichen die gleiche Breite haben.
i sans-serif ist eine Schriftart ohne Serifen. i serif ist, wenig überraschend, eine Schriftart mit Serifen.
Die @font- face-Regeln. @font-face lädt eine Schriftart von einer URL und gibt ihr einen Namen, der anschließend in einer font-family-Eigenschaft benutzt werden kann.
 @font-face{font-family: "Meine Beispielschrift"; src:url('examplefont.eot');} p{ font-family: "Meine Beispielschrift", "Times New Roman", serif;}
Um wirklich sicherzugehen, dass überall die richtige Schriftart auftaucht, müssen also mindestens drei Formate zur Verfügung stehen, zum Beispiel WOFF, EOT und OTF
text-transform: uppercase stellt den gesamten Text des Elements nur in Großbuchstaben dar, text-transform: lowercase tut dasselbe mit Kleinbuchstaben, und text-transform: capitalize macht den ersten Buchstaben jedes Wortes zum Großbuchstaben. text-transform: none schaltet den ganzen Spaß ab.
text-decoration: underline; / text-decoration: overline; / text-decoration: line-through;
text-indent setzt die Einrückung für die erste Zeile in jedem Absatz (oder auch in <div>
text-align setzt den Text in einem Absatz (auch hier wieder in einem Blockele- ment) linksbündig (text-align: left), rechtsbündig (text-align: right), zentriert (text-align: center) oder im Blocksatz (text- align: justify).


Ordnung in die Plattensammlung
Für einfache Aufzählungen, wie die Liste deiner Platten- sammlung, gibt es zwei Arten, die sich eignen: <ul> und <ol> für unordered List bzw. ordered List (nichtnummerierte und nummerierte Liste). 
<ul>, <ol> und <li>
type bestimmt, in welcher Form Listenelemente nummeriert werden. Neben der Standardaufzählung mit Zahlen (type="decimal") gibt es noch Kleinbuchstaben (lower-alpha), Großbuchstaben (upper-alpha), und römische Zahlen in Klein- und Großbuchstaben (lower-roman und upper-roman). Ex  <ol type="lower-roman" start="9">
list-style-type wird auf die <li>s angewendet
Für unnummerierte Listen gibt es darüber hinaus noch die Werte circle, disc und square, die je ein entsprechendes Symbol auswählen. Und dann gibt es noch ein paar weitere Zählweisen für nummerierte Listen, zum Beispiel decimal-leading-zero, das bei einstelligen Zahlen eine 0 voranstellt, oder lower-greek für griechische Buchstaben.
Die Eigenschaft list-style- image akzeptiert eine URL, unter der ein Bild zu finden ist, das dann als Aufzählungs- zeichen verwendet wird.
<dl>, <dt> und <dd> die Definition List , <dfn>
Verschachtelte Listen
<style> 
ol ol>li { list-style-type: lower-alpha;}
ul > li {list-style-type: circle;}
Deshalb ändern wir nur den Style von <li> innerhalb von <ol> innerhalb von <ol>. Achte auch auf den Kind-Selektor bei ol ol > li: Würden wir stattdessen ol ol li schreiben, würde der Stil auch für die Elemente der unnummerierten Liste gelten, was wir nicht wollen
<table>, <tbody>, <tr>, <td>
Tabellen sind zeilenorientiert, das heißt, der <tbody> hat als Kinder eine oder mehrere – meis- tens mehrere – Tabellenzeilen <tr> (table row). Jede Zeile enthält wiederum eine oder mehrere Tabellenzellen <td> (table data).
<table>
      <tbody>
		<tr>
			<td>Queen</td>
			<td>Queen</td>
			<td>1973</td>
			<td>10</td>
			<td style="text-align: right">8</td>
		</tr>
      </tbody>
</table>

￼

Würden <col> und <colgroup> funktionieren, wie angepriesen, würde das vieles einfacher machen. Vielleicht eines Tages, man kann ja zumindest träumen ...
border-collapse

Check auf dem Buch für mehr tabelleKunst!


		<tbody>
			<tr>
				<td rowspan="2">...</td>
				<td colspan="2">...</td>
				<td colspan="2">...</td>
			</tr>
			<tr>
				<td rowspan="2">...</td>
				<td colspan="2">...</td>
				<td>...</td>
			</tr>
			<tr>
				<td>...</td>
				<td rowspan="2">...</td>
				<td colspan="2">...</td>
			</tr>
			<tr>
				<td>...</td>
				<td>...</td>
				<td rowspan="2">...</td>
				<td>...</td>
			</tr>
			<tr>
				<td>...</td>
				<td>...</td>
				<td>...</td>
				<td>...</td>
			</tr>
		</tbody>
	</table>
  </body>


SECHS 
Daten zum Server zu schicken, ist fast genauso wichtig, wie Daten vom Server zu bekommen, und dafür gibt es das <form>-Tag
<form> 
<form action="forms/hallowelt.php" method="get" accept-charset="utf-8">

In method steht, wie die Daten an den Server geschickt werden sollen ( du verwendest absolute URLs: http://localhost:8080/ forms/hallowelt.php
Hint. Geh ins terminal und tipp cd .. folder .. dann start PHP server : php -S localhost:8080
Wir haben die Input Tag <input type="text"> 
<form action="forms/hallowelt.php" method="get"> <input type="text" name="name">*2 </form>
 <button>Sag mal hallo!</button>
Wenn du nichts anderes angibst, dann schickt <button> das umgebende Formular ab. Du kannst aber auch mit <button type="reset"> einen Knopf anbieten, der das Formular kom- plett leert oder mit type="button" einen Button ohne eige- nes Verhalten, dem du dann mit JavaScript eine neue Aufgabe gibst.
Der placeholder-Wert wird im Eingabefeld in Grau angezeigt. Er verschwindet aber, sobald man etwas anderes eintippt, und wird auch nicht an den Server übermittelt. value. das Attribut maxlength. verschleierte Eingabe ->  <input type="password”>.
sollte für Passwörter immer HTTPS benutzt werden. HTTPS verschlüsselt die Übertragung, type="password" verschleiert nur die Eingabe.
Dass Parameter an die URL des get-Requests ange- hängt werden, hat einen sehr nützlichen Effekt: Alle get-Anfragen lassen sich als Lesezeichen speichern. Öffnest du das Lesezeichen später, werden dieselben Parameter wieder mitgeschickt, und du bekommst das aktuelle Ergebnis dazu. Das geht mit post nicht.
Genau dafür sind get-Requests da, um Seiten zu holen.  der Zweck von post ist, Daten an den Server zu schicken, die der dann speichern soll.
POST oder GET? Wenn ich den Request wiederholen kann, ohne dass ungewollte Nebenwirkun- gen eintreten, dann ist get richtig, ansonsten post. Wenn du bei Google 50-mal nach „Schrödinger rockt“ suchst, macht das nichts. Wenn du 50 Facebook-Profile anlegst, dann ist das schon eher ungewollt, 50-mal dieselbe Pizzabestellung abzuschicken, ganz schlecht. Wenn der Server dir 50-mal sagt, dass du ein toller Webentwickler bist, dann schadet das nichts. Also ist get hier in Ordnung.
Für Radiobuttons ist es auch echt nützlich, ein <label> zu haben ,.
  [Einfache Aufgabe]
Du kannst jetzt Radiobuttons fürs Geschlecht in die Seite von vorhin einfügen. Damit beim Server alles richtig ankommt, sollten sie den Namen geschlecht und die Werte m und w haben.
[Notiz]
Für Radiobuttons ist es auch echt nützlich, ein <label> zu haben. Die kleinen Dinger sind sonst auf einem Handydisplay sehr schwer zu treffen.
So sieht es aus mit Radiobuttons.
<label for="geschlecht_m">Männlein</label>
<input type="radio" name="geschlecht" value="m" id="geschlecht_m"> <label for="geschlecht_w">Weiblein</label>
<input type="radio" name="geschlecht" value="w" id="geschlecht_w">
Füge im Radioknopf für männlich das Attribut checked="checked" oder einfach nur checked ein. Damit ist dieser Wert ausgewählt, wenn die Seite geladen wird.
<input type="checkbox">
ls Nächstes die Select-Box, manchmal auch Dropdown-Box genannt, <select> und <option>
Ex <option value="intelligent" selected>intelligent</option>
 <select name="zusatz[]">
<optgroup label="The Good">
            <option value="intelligent">intelligent</option>
            <option value="gutaussehend">gutaussehend</option>
 </optgroup>

Optionen lassen sich mit dem <optgroup>- Tag gruppieren. Die Überschriften für jede Gruppe stehen im label-Attribut.
<datalist> gibt eine Liste von Einträgen an, die dem Benutzer vorgeschlagen werden, wenn er in ein Texteingabefeld tippt. Damit ist es so eine Art halbe Select-Box: Es werden mögliche Werte vorgeschlagen, aber der Benutzer kann auch eigene Eingaben machen.
Diese schicken Rahmen um die Radiobuttons sind übrigens <fieldset>s, ihr einziger Zweck ist es, Eingabefelder optisch zu gruppieren. Der in den Rahmen integrierte Titel steht, in ein <fieldset> verschachtelt, in einem <legend>-Tag. Vor allem für Radiobuttons und Checkbo- xen sind <fieldset>s sehr nützlich, denn man kann so darstellen, welche von ihnen zusammengehören.
versteckte Felder :  <input type="hidden">
Für mehrzeilige Eingaben gibt es das <textarea>-Tag
HTML5 bringt einen ganzen Schwung neuer Eingabefelder mit, die uns Webentwick- lern einen ganz fiesen Teil unserer Arbeit abnehmen sollen: die Eingabevalidierung. Auch Firefox und Chrome kannst du zwingen, Formulare mit ungültigen Daten trotzdem abzuschicken. Setz dazu einfach am <form>-Tag das Boolesche Attribut novalidate. Andersrum gibt es für Safari kein benimmdichanständig- Attribut.
CSS für Forms
:required und :optional beziehen sich offensichtlich auf das required-Attribut an Eingabefeldern. Ist es gesetzt, gilt die Style-Regel input:required, ansonsten input:optional. Mehr gibt es dazu auch nicht zu sagen.	
Alle Eingabe- felder sind erst mal aktiv. Eigentlich offensichtlich, man kann sie ja benutzen. Wenn du ein Eingabefeld inaktiv schalten möchtest, machst du das mit dem Attribut disabled bzw. disabled="disabled".
Die Pseudoklasse :focus bekommt das Element, mit dem der Benutzer gerade interagiert – in Entwicklersprech: das gerade den Fokus hat.Das, mit dem der Benutzer grade arbeitet, soll einen blauen Rahmen bekommen. input:focus{border: 2px solid #BBBBFF;}
Es gibt auch einen schicken, einfachen Trick, wie du zum Beispiel email-Felder anders aussehen lassen kannst als normale text-Felder: mit Attribut-Selektoren. Damit kannst du Elemente selek- tieren, die ein bestimmtes Attribut haben oder bei denen das Attribut einen bestimmten Wert hat. Attribut-Selektoren werden immer in eckigen Klammern geschrieben und funktionieren für alle Tags, nicht nur für Eingabefelder.
input[pattern] {color: green;}
input[type=text] {color: blue;}
Zusammen mit Attribut-Selektoren ist manchmal der Univer- sal-Selektor * nützlich. Der findet alle Elemente im ganzen Dokument. Dann kannst du zum Beispiel alle Elemente fin- den, die eine id haben: *[id]{...}. Es gibt, zugegeben, nützlichere Anwendungen, aber die Theorie ist klar.
File Upload. <input type="file">
Und das Allerschlimmste ist: Du kommst da mit CSS nicht dran. Dieser hässliche Knopf bleibt dir immer erhalten. Es gibt mit CSS keine Möglichkeit, Upload-Elemente zu stylen, deswegen greifen die meisten Seiten zu einem Trick: Sie legen einen hübscheren Knopf über den „Durchsuchen“-Knopf des Elements, aber sorgen dafür, dass du durch diesen Knopf auf das Original klicken kannst. Man braucht dafür ein wenig CSS-Zauberei. Upload- Elemente lassen sich auch nicht mit JavaScript kontrollieren.
Ein <input type="file" name="name"> genügt. Die einzigen Einschränkungen sind folgende:
i Das Formular muss mit method="post" geschickt werden, ein get-Request kann keine Dateien transportieren. Da der Server aber meistens die Datei speichern soll, passt das schon.
i Am Formular muss das Attribut enctype="multipart/form-data" gesetzt werden. Dieses Attribut steuert, wie Formulardaten im post-Request ver- packt werden, und wenn Dateien im Spiel sind, muss es dieser Wert sein. Ansons- ten gibt es keinen Grund, das Attribut zu setzen. Das Formular wird mit der post-Methode an die relative URL upload.php verschickt, dabei den enctype nicht vergessen.
<form method="post" action="upload.php" enctype="multipart/form-data">Datei: <input name="datei" type="file"></form>

SIEBEN 
Von Rändern und Schuhkartons
Die Grundlagen für alles –Block- und Inline-Elemente
Als Inline­ Elemente bezeichnet man HTML-Elemente, die mitten im Text vorkommen können
Als Blockelemente werden HTML-Elemente bezeichnet, die nicht innerhalb des Textes vorkommen, aber Text umfassen können. Blockelemente dulden von Natur aus nichts anderes neben sich: Solange man es nicht umstellt, steht das vorherige Element über einem Blockelement, das folgende darunter. Außerdem sind Blockelemente immer recht- eckig, das wird gleich wichtig.
<a>, <span> und <em> sind ganz klassische Inline-Elemente, sie tauchen mitten im Text auf, fügen Informati- onen über Aussehen oder Funktion hinzu, aber sie unterbrechen den Text nicht.
Dagegen sind <p> und <table> Blockelemente: Sie erzwingen einen Zeilen- umbruch vor und hinter sich und sind grundsätzlich rechteckig. Das sieht man zwar bei Absätzen nicht auf den ersten Blick, aber spätestens, wenn man eine Hin- tergrundfarbe zuweist, wird es offensichtlich.
Inline- Elemente dürfen nur Text und weitere Inline-Elemente enthalten, niemals Blockelemente. Blockelemente dürfen immer Inline-Elemente enthalten, manche auch weitere Blockelemente.Es geht jetzt also um Boxen – um stapelbare Boxen
das <div>-Tag. Es ist für Blockelemente im Wesentlichen das, was das <span>-Tag für Inline-Elemente ist. Es hat keine eigene Bedeutung, stellt keine Ansprüche daran, was drin ist, es ist einfach ein generischer Container, 
￼
Diese Box, mit sämtlichen Bereichen, die du dort siehst, wird vom Browser für jedes Blockelement erzeugt.


￼

width und height beziehen sich auf den Platz, der dem Inhalt einer Box zur Verfügung steht. Sie enthalten weder margin noch padding.
Die Annahme, width und height würden die Größe des Rahmens oder gar der ganzen Box setzen, ist eine der häufigsten Frustquellen für neue Webentwickler, denn dann passt nichts zusammen.
Als Nächstes kommt dann der Rahmen. Dazu weißt du ja schon alles Wichtige. Der Rahmen liegt zwischen Padding und Margin, nicht in einem der beiden Bereiche. Er braucht auch seinen eigenen Platz.
Der Platz, der von einem Element mit allen Paddings, Borders und Margins eingenommen wird, heißt die Margin­Box des Elements.
Ist keine Größe angegeben, wird ein Blockelement gerade so groß, dass sein Inhalt komplett hineinpasst.
Prozentangaben bei Blockelementen beziehen sich immer auf das umgebende Element, das heißt auf den <body>, wenn es kein anderes umgebendes Blockelement gibt. width: 50% bedeutet also halb so breit wie das Elternelement.
Auch relative Angaben für width und height gelten nur für den Inhaltsbereich. Insbesondere heißt das: Wenn zwei Elemente width: 50%; haben und außerdem margin, padding oder border, dann passen diese Elemente nicht nebeneinander in ihr Elternelement!!
Auch Prozentangaben für padding und für margin beziehen sich auf die Größe des umgebenden Elements, nicht des Ele- ments selbst. Das ist auch gut so, denn so weißt du, dass alles nebeneinanderpasst, wenn du in Summe auf 100% kommst.
Ist für das Elternelement keine Größe gesetzt, dann kommt es zu der Situation, dass das Elternelement die Größe seiner Kinder kennen muss, um die eigene Größe zu berechnen, die Kindele- mente aber die Größe des Elternelements kennen müssen, um die Prozentangabe aufzulösen. Wie der Browser damit umgeht, ist nicht definiert, aber es funktioniert nicht.
em im Box-Model - ems sind und bleiben eine Einheit für Schriftgrößen, und auch wenn man sie als Größen- angabe für Boxen benutzt, haben sie einen Bezug zur Schriftgröße. Ein Element mit height: 3em; ist so hoch wie drei ZeilenDas heißt aber nicht, dass auch drei Zeilen Text reinpassen. 

Ohne CSS - Zwischen den <div>s gibt es keinen Abstand.
i Wenn der Text zu lang ist, geht er einfach über den Rand.
Füge auf der Beispielseite für alle <div>s diese CSS-Eigenschaften hinzu:
overflow: hidden; margin-bottom: 5px;
„Prozentangaben funktionieren nur zuverlässig, wenn für das umgebende Element eine Größe gesetzt ist.“
Das umgebende Element ist  ... Body!

Das ist schon mal sehr richtig gedacht, Body hat wirklich keine festgelegte Höhe, deswegen wird deine Style-Regel für vier ignoriert. Und warum es so hoch wird, wie es jetzt ist, das merkst du ...
„Ist keine Größe angegeben, wird das Element gerade so groß, dass sein Inhalt komplett hineinpasst.“
￼

wenn zwei Margins zusammentref- fen, sagen wir margin-bottom eines Elements und margin- top des nächsten darunterliegenden Elements, dann werden sie nicht zusammenaddiert. Es wird nur die größere Margin angewendet!

margin: auto; ist fast wie Magie. Wie man ein Blockelement in einem anderen zentriert, ist nämlich nicht sofort offensichtlich. 
Deshalb finden die meisten Webentwickler nach ein bis zwei Jahren ihrer Karriere heraus, dass margin:auto; den verfügbaren Platz zwischenlinker / rechterbzw. oberer/unterer Margin aufteilt, also zentriert. Die Eigenschaft text-align funktioniert nur für Text und Inline- Elemente, die ja wie Text sind

die CSS-Eigenschaft overflow. 
Die Standardeinstellung für overflow ist visible,
Abhilfe schafft der Wert scroll, der am linken und unteren Rand des Elements einen Scrollbalken hinzu- fügt. Damit fließt längerer Text nicht über den Rand, aber er bleibt erreichbar, man kann scrollen.overflow: auto zeigt Scrollbalken genau dann an, wenn sie benötigt werden, sonst nicht
Mit position: 
 schaltest du das automatische Layout des Browsers für dieses Element komplett ab, er verlässt sich dann ganz auf deine Angaben, wo es hin soll
￼
[Achtung] 
Wenn für position kein Wert gesetzt wird, dann haben die vier Ortsangaben keine Wirkung. 
top und left beziehen sich aber nicht auf den, sondern auf die Margin-Box; an der Position, die du festlegst, kommen zuerst mal Margin, Border, Padding und dann der Inhalt.
Position
Was passiert?
Absolute
Mit position: absolute schaltest du das automatische Layout des Browsers für dieses Element komplett ab, er verlässt sich dann ganz auf deine Angaben, wo es hin soll.
static
static ist der Standardwert für position. In diesem Modus werden Angaben für top und left, right und bottom ignoriert, das Element wird genau dort platziert, wo der Browser es für richtig hält.
[Begriffsdefinition]
Elemente, deren position­Eigenschaft nicht static ist, nennt man positionierte Elemente.
relative
Relative Positionierung unterscheidet sich von absoluter Positionierung dadurch, dass der Layoutalgorithmus des Browsers nicht abgeschaltet wird. Der Browser berech­ net das Layout, aber anschließend wird das Element noch verschoben. Die Positionsangaben beziehen sich nicht auf das umgebende Element, sondern auf die Position, in der das Element eigentlich wäre. Alle anderen Elemente werden so darge­ stellt, als wäre dieses Element noch an seinem ursprünglichen Ort.
fixed
Mit position: fixed wird das Element an der angegebenen Position befestigt.der Unterschied ist, woran genau das Element befestigt wird. Absolute und re­ lative Positionierung beziehen sich auf etwas im Dokument, position: fixed setzt die Position relativ zum Viewport – also mal wieder dem Browserfenster.
Das heißt, dass sich ein solches Element ...beim Scrollen nicht mit bewegt! Egal, wie du hoch­ und runterscrollst, ein Element mit posi- tion: fixed bleibt genauda,woduesabgestellthast.

Elemente im Fluss – float und clear.
 das Element mit float: left; an den linken Rand sei- nes umgebenden Elements rutscht und alles, was nicht selbst floatet, rechts um dieses Element herumfließt.
Ex. 
blockquote.pull { float: left;
border-bottom: 3px solid darkblue; border-top: 3px solid darkblue; padding: 10px 20px;
font-variant: small-caps;
width: 240px; }

Dass <img>-Elemente eine intrinsische Breite haben, bedeutet, dass ihre Breite durch das angezeigte Bild festgelegt wird. Wenn du nichts anderes angibst, dann ist das Element so breit wie das Bild selbst. Die meisten anderen Elemente, auch <blockquote>, haben keine intrinsische Breite. Wenn du die width- Eigenschaft nicht setzt, dann werden sie immer breiter, bis sie ihren gesamten Inhalt anzeigen können oder bis sie an den Rand des umgebenden Elements stoßen; erst dann gibt es einen Zeilenumbruch.
Mit clear: left; stellt man sicher, dass links neben dem Element kein gefloateter Inhalt steht, clear: right; funktioniert natürlich ebenso, und clear: both; positioniert das Element unterhalb von allen gefloateten Nachbarn.

Und so sieht der Stylesheet am Ende aus:
Margin und Padding des Bodys werden zurückge- setzt, damit wir bis an den Rand kommen.
body{ padding: 0; margin: 0; }
Semantik statt <div> 
Die Idee, Informationen im Web automatisch auszuwerten, heißt Seman- tic Web. Stell dir vor, in ein paar Jahren kannst du deinem Computer sagen, du wüss- test gerne, wo du alte Pink-Floyd-Platten kaufen kannst, und er findet das für dich. Dafür müssen Informationen so gekennzeichnet werden, dass der Computer weiß, wel- che Bedeutung sie haben
  <footer> enthält Informationen zum Inhalt der Seite, die schon genannten Copyright-Informationen, den Autor, einen Link zum Impressum und so weiter.
Im <header> stehen einführende Informationen zum Sei- teninhalt: eine kurze Beschreibung, was auf dieser Seite zu finden ist, ein Seitenlogo ...
Ein einzelner Eintrag in einem Blog oder einem Onlinemagazin kann mit <article> ausgezeichnet werden. Artikel können eigene <footer> und <header> haben. Und auch darin verschachtelte <article>, zum Beispiel für Kommentare zu einem Blogeintrag.
Ein Artikel kann wiederum in <section>s unterteil werden. Sektionen sind Bereiche des Artikels, die eigenständig genug sind, dass sie eine eigene Überschrift haben können. Logischer- weise können sie also auch wieder einen <header> und auch einen <footer> haben.
In einem <aside>-Tag steht Inhalt, der zwar Bezug zur Seite (oder zum Artikel oder zur Sektion) hat, der aber entfernt werden könnte, ohne dass dem Hauptinhalt etwas fehlt.

Mit display: block; kannst du den Browser zwingen, ein Element, egal welcher Art, als Blockelement zu behandeln. Und was mit display: inline; passiert, kannst du dir wahrscheinlich denken. 
Sehr viele Webseiten haben eine solche Navigationsleiste links.
Diese beiden Eigenschaf- ten sorgen dafür, dass jeder Navigationseintrag eine
  klickbare Box wird. Der Rest bewirkt nur ein schöneres Aussehen.
display: block;
width: 100%;
Du kannst auch mit display: none; ein Element komplett von der Seite ent- fernen – es kommt zwar im Quelltext vor, aber es wird auf der Seite nicht dargestellt,

Und die Reihenfolge der Überlappung.. Mit der Eigenschaft z-index kannst du (mit Einschränkungen) festlegen, welches Element weiter oben liegt: Der höhere Wert gewinnt und liegt oben.z-index hat nur auf positionierte Elemente eine Auswirkung, also auf solche, die nicht position: statichaben.

iframe
Weil es noch eine ganz spezielle Art Kiste gibt, die ich dir zeigen möchte. Eine Kiste, anders als alle anderen. Eine Kiste, die keine HTML-Elemente enthält, sondern eine andere Webseite anzeigt. Ein Fenster in eine andere Welt: den <iframe>!
Ein <iframe> lädt eine HTML-Seite, deren URL du im src-Attribut angibst, und zeigt sie an.


ACHT 
Erste website. Die Enten 
Das Wichtigste für die Listeneinträge ist, dass list-style-type auf none gesetzt wird.
In der Navigation sollen keine Aufzählungszeichen zu sehen sein.
Und zum Schluss die Links in jedem Eintrag: Die meisten Eigenschaften ändern nur die Textdarstellung, aber wichtig ist display: block, denn dadurch wird die gesamte „Linkkiste“ klickbar, nicht nur der Text
#nav a, #nav a:visited, #nav a:hover, #nav  a:focus {
 display: block; height: 2em; text-decoration: none;  color: black; text-align: right; font-size: 1.6em;  padding: 2px 10px 0 0;
font-variant: small-caps; font-weight: bold;}

Im Beispiel-Stylesheet ist dir bestimmt aufgefallen, dass fast alle Regeln einen Nach- kommen-Selektor benutzen und nur innerhalb eines Bereichs – Kopf, Fuß, Navigation oder Inhalt – gelten. Nur grundlegende Einstellungen wie Hintergrundfarbe und Schriftart werden in global gültigen Regeln definiert. Das ist eine verbreitete Methode, Stylesheets zu organisieren, und hat mehrere Vorteile:

Ein <li> mit einem Klassennamen kann überall in der Seite vorkommen, änderst du eine Style- Eigenschaft, kann diese Änderung auch anderswo sichtbar sein. Mit auf einen Bereich beschränkten Regeln wie #nav li bist du davor geschützt.
Du kommst mit weniger Klassennamen aus. 
Deine Stylesheets werden übersichtlicher

Noch übersichtlicher kannst du deine Stylesheets übrigens mit Imports gestalten:
@import url("nav.css")importiert

Bilder mit einer Creative-Commons-Lizenz sind sehr nützlich, wenn du noch keine eigenen Bilder hast, aber sehen willst, wie die Seite später mal aussehen wird. Beachte: Sobald du die Seite an jemanden weiter- gibst, müssen Urheber und Lizenz genannt werden.

Für die Galerie
#inhalt.galerie div{  border: 1px solid white; width: 19%; min-width: 200px; height: 30em; margin: 1em 0 0 0.5%; float: left; text-align: center; padding: 0; color: white;}
Setze für Bilder in der Galerie die Style-Eigenschaften max-width: 100%undmax-height: 66%. !!! damit passen sie sich an!

#inhalt.galerie div .title,#inhalt.galerie div small { display: block;  }  Die beiden Elemente werden als Block gerendert, damit erledigt sich der Zeilenumbruch von selbst.

Eine Lightbox (JS)
Es gibt viele kostenlose Lightbox-Skripte, die du benut- zen kannst. Ich benutze hier Lokesh Dhakars Lightbox2 (http://lokeshdhakar.com/projects/lightbox2/), weil es extra-einfach zu benutzen ist.
 jQuery ist eine beliebte JavaScript-Bibliothek für alles Mögliche und eine Voraussetzung für Lightbox2. Du kannst jQuery unter http://jquery.com/ herunterladen, aber ich hab es auch schon für dich zu den Beispielen gepackt.
<script src="js/jquery-1.7.2.min.js"></script> 
<script src="js/lightbox.js"></script>
Das rel-Attribut gibt an, in welcher Beziehung zu dieser Datei die verlinkte Datei steht. Hier wird es aber benutzt, um dem Lightbox-Skript mitzuteilen, wo es etwas zu tun hat.Wenn die Seite vollständig geladen ist, findet das Lightbox-Skript alle Links mit rel="lightbox". An all denen macht es dann ein Stück JavaScript fest, das aktiv wird, wenn jemand darauf klickt und das verlinkte Bild in der großen Box anzeigt.

NEUN
abgerundete Ecken.
die neue CSS3-Eigenschaftsfamilie border-radius nimmt uns dieses Problem jetzt ab. Ein einzelner Wert, wie oben gesehen, wird auf alle vier Ecken angewandt. So weit, so gut, das war bei margin und padding auch so. Aber danach wird es merkwürdig. Gibt man zwei Werte an, gilt der erste für die Ecken links oben und rechts unten, der zweite für die beiden anderen. Und bei drei Werten wird es dann richtig komisch, 

border-image.  Rahmenbilder für Bilderrahmen
eine Kurzschreibweise 
border-image: url(rahmen.png) 20 50 repeat stretch;

Licht und Schatten und Glühen
die CSS3-Eigenschaft für Textschatten: text-shadow
einen zusätzlichen Parameter angeben, der vorgibt, wie unscharf der Schatten ist. .. 
Ex mit drei Schatten - text-shadow: 5px 5px 40px yellow; 10px 10px 30px orange,
20px 20px 20px red
Mehrere Schatten funktionieren nur so. Die text-shadow-Eigenschaft darf nur einmal vorkommen und hat dann mehrere Werte

Oder auch box-shadow: 10px 10px 5px #AAAACC;  — Das Schlüsselwort inset, ganz am Ende der Deklaration angegeben, sorgt dafür, dass der Schatten nicht außerhalb der Box steht, sondern innerhalb – anders als beim Text ist da ja Platz.
Außerdem, und dann reicht es auch mit Schatten, kann man für box-shadow die Ausbreitung (spread) angeben, eine weitere Größenangabe zwischen Unschärfe und Farbe. Der Schatten breitet sich dadurch in alle Richtungen weiter aus.

Animationen funktionieren seit Neuestem auch mit reinem CSS, 
Ein Einzelbild aus einer Animation heißt ein Frame. Die Animationstechnik, die wir in CSS benutzen können, ist die Keyframe- Animation.
Die neue @-Regel @keyframes beginnt eine Animationsdefinition. Browser, die @keyframes nicht kennen, ignorieren den gesamten Block. Für Chrome und Safari muss hier das reichlich hässliche @-webkit-keyframes stehen – und das vollkommen grundlos, alles andere bleibt gleich.Als Nächstes bekommt die Animation einen Namen. 
@keyframes colors { from {background-color: yellow;} 33% {background-color: red;} 66% {background-color: blue;}
           to{ background-color: yellow;}
Der Keyframe-Selektor gibt an, an welche Stelle der Animation dieser Keyframe gehört. from (oder 0 %) ist der erste Frame der Animation, to (oder 100 %) der letzte. Die Prozentangaben dazwischen kommen an die passende Stelle. Es gibt keine Angabe, wie lang die Animation insgesamt laufen soll, das kommt erst später.
In einem Keyframe können die meisten CSS-Eigenschaften stehen, die in normalen CSS-Regeln auch vorkommen können, alle Eigenschaften, deren Wert sich interpolieren lässt, um genau zu sein. Dazu gehören die offensichtlichen Dinge wie Größe, Position und Farbe, aber auch margin, padding, border- radius und viele andere. Nicht animieren lassen sich zum Beispiel background-image oder border- style: Den Wert zwischen solid und dashed kann der Browser nicht berechnen; diese Eigenschaften wechseln plötzlich, wenn ihr Keyframe an die Reihe kommt. Um Pac-Man über den Bildschirm rennen zu lassen, würdest du einfach die Eigenschaften left und/oder top animieren, aber dass er dabei auch noch kraftvoll zubeißt, wird mit CSS schwierig.
Damit ist die Animation definiert, aber es bewegt sich noch nichts, es wird schließlich nirgends angegeben, welche Elemente animiert werden sollen. Aber dafür brauchen wir keine komplexe, neue Syntax mehr, du musst nur drei neue CSS-Eigenschaften lernen:
#move_me {
animation-name: colors;*1
animation-duration: 10s;*2 animation-iteration-count: infinite;*3 -webkit-animation-name: colors;*4 -webkit-animation-duration: 10s;*4 -webkit-animation-iteration-count: infinite;*4
}

Example
In Style:

div {
    margin: 20px;
    width: 100px; 
    height: 100px;    
//    background: #f00;
    -webkit-animation: spin 4s  linear;
}

@-webkit-keyframes spin {
    0%  {-webkit-transform: rotate(-90deg);}
    100% {-webkit-transform: rotate(0deg);}   
}

In Body:
// what I put in the div will rotate
<div><img src="pinky.png"></div>

To move need position :relative;
And then 
from {top: 0px;}
    to {top: 200px;}

Das ist auch schön
div:hover {
   animation-play-state: paused;
    -webkit-animation-play-state: paused;
    }
____________________

Und Transitions
Normalerweise ändert sich der Zustand einer CSS-Eigenschaft in dem Augenblick, in dem sie geändert wird, zum Beispiel durch die :hover-Pseudoklasse oder später durch JavaScript. Mit Transitions kannst du diese Änderung über einen längeren Zeitraum ausdehnen, es lassen sich Regeln erstellen wie „wenn der Mauszeiger über das Element fährt, dann soll die Farbe langsam von Blau nach Rot wechseln“ . For instance
#hoverme {
background-color: red; color: blue; transition-properties: background-color, color; transition-duration: 5s;
...
}
#hoverme:hover {
background-color: blue; color: red;}

Das Beispiel „Farbe ändern, wenn der Mauszeiger über dem Element schwebt“ lässt sich zwar auch mit Keyframes umsetzen, dann hört aber die Animation einfach auf, wenn der Mauszeiger sich wegbewegt. Mit Transitions kehrt die Farbe langsam wieder zum Ursprungszustand zurück.

TEXT

 Genau darum geht es bei Transformationen, den klassischen geometrischen Operationen, die du auch in GIMP, Photoshop oder jeder anderen Bildbearbeitungssoftware auf Bilder anwenden kannst:
Verschieben, Skalieren, Rotieren und Scheren.
transform: rotate(45deg) translate(100px, 100px) scale(2);
Bei mehreren Transformationen ist die Reihenfolge extrem wichtig. 
Auch der Ursprungspunkt der Transformationen lässt sich verschieben. Falls sich mal etwas nicht um den Mittelpunkt drehen soll, kriegst du so auch das ganz einfach hin. Du musst nur die Eigenschaft transform-origin setzen,
Für den mathematisch begabten Webentwickler lassen sich auch alle Transformationen als eine 3x2-Matrix mit der Eigenschaft matrix(a, b, c, d, e, f)anwenden

Scroll Beispiel
@keyframes scroll { from {top: 0;} to {top: -2330px;}}

#film {
position: relative; animation-name: scroll; animation-duration: 45s; animation-iteration-count: 1; animation-timing-function: linear; animation-fill-mode: forwards;}
Noch eine nützliche Kleinigkeit: Wenn
Die Timing-Funktion linear lässt die Animation mit konstanter Geschwindigkeit laufen, anstatt sie am Anfang zu beschleunigen und am Ende zu verlangsamen.
[Achtung/ Vorsicht]
Denke daran, sowohl die @keyframes- Regel als auch die Animationseigenschaften mit dem Präfix -webkit- zu wiederholen.
animation-fill-mode: forwards gesetzt ist, dann bleibt die Animation im Endzustand stehen, anstatt in den Anfangszustand zurückzuspringen.
Und noch transform: rotateX für 3D perspective
#viewport {
width: 640px; height: 480px;
transform: rotateX(15deg); -webkit-transform: rotateX(15deg); overflow: hidden;


ZEHN 
 JavaScript ist eine vollwertige Programmiersprache, und bevor Schrödinger damit loslegen kann, muss er einige Grundlagen lernen. Aber keine Angst, das klingt viel schlimmer, als es ist.
JavaScript war fast von Anfang an ein Bestandteil des World Wide Web, genauer gesagt seit dem Netscape Navigator 2.0, erschienen 1995. Microsoft zog schon 1996 in Internet Explorer 3 mit seiner eigenen Variante, genannt JScript, nach. 
Schon Ende 1996 hat Netscape seine Version von JavaScript bei der Normungsorganisation Ecma International eingereicht, um einen Industriestandard daraus zu machen. Die erste Version dieses Stan- dards wurde Mitte 1997 verabschiedet unter dem Namen ECMAScript.Die Bezeichnung ECMAScript ist deshalb auch kaum gebräuchlich, im Alltag spricht man immer nur von JavaScript.
Interpretiert heißt, der Programmcode wird genau in dem Moment vom Computer analysiert und in Instruktionen übersetzt, wenn er auch ausgeführt wird. Das unterscheidet JavaScript von kom- pilierten Sprachen wie C++: Diese werden vom Compiler in ein maschinenlesbares Programm übersetzt, das dann vom Benutzer nur noch ausgeführt wird.
Der größte Lebensraum von JavaScript ist nach wie vor der Webbrowser, aber es kommt nicht nur dort vor. Schon ganz am Anfang haben es sowohl Netscape als auch Microsoft in ihren jeweiligen Webservern erlaubt, JavaScript auch auf der Serverseite auszuführen – eine Technik, die damals nicht übermäßig populär war und sich nicht wirklich durchsetzen konnte. Seit 2009 gibt es aber mit node.js ein neues Projekt, JavaScript auch außerhalb des Webbrowsers zu etablieren; und die- ses Mal kann es dort Fuß fassen, node.js erfreut sich wachsender Beliebtheit.
<script> kann sowohl im <head> als auch im <body> der Seite stehen. Experten empfeh- len, wenn möglich JavaScript am Ende des <body> zu laden, denn so werden sichtbare Elemente zuerst geladen, und der Betrachter bekommt schneller etwas zu sehen.
<noscript> ist, wenn du JavaScript einbindest, fast so wichtig wie <script>, obwohl es im besten Fall nichts tut und auch nicht zu sehen ist. Der Inhalt von <noscript>
Browser entweder abgeschaltet ist oder der Browser zu alt ist, um JavaScript zu kennen. Letzteres kommt heute so gut wie nicht mehr vor, Ersteres dafür umso öfter. Es ist immer eine gute Idee, einen Hinweis im <noscript> mit in die Seite zu packen.

Das ist ein Funktionsaufruf.  alert("Hallo Welt!”); oder document.write ..
Der Punkt in document.write bedeutet streng genommen, dass die Methode write des Objekts document aufgerufen wird. Du kannst es für den Augenblick wie eine einfache Funktion betrachten, die eben einen Punkt im Namen hat.

JavaScript kennt, im Gegensatz zu anderen Sprachen, keine Konstanten, also Werte, die unveränderlich sind, nachdem sie einmal festgelegt wurden. Man kann aber zumindest klarmachen, dass eine Variable nicht verändert werden sollte, indem man den Namen NUR IN GROSSBUCHSTABEN schreibt, dann weiß jeder JavaScript-Programmierer, dass er nicht daran rumpfuschen soll.

Zahlen in fast allen Programmiersprachen haben zwei blöde Angewohnheiten:
 -Es gibt einen Unterschied zwischen ganzen Zahlen
(den sogenannten Integer-Werten) und Kommazahlen (den Float-Werten).
- Zahlen können nicht unbegrenzt groß werden.
muss man sich in JavaScript keine Gedanken machen, ob man mit Zahlen mit oder ohne Kommastellen rechnet, es gibt nur den Datentyp Number, und da passt alles rein. Der Nachteil ist aber, dass alle Zahlen in JavaScript als „Double precision floating point values“ (Fließkommawerte mit doppelter Genauigkeit) nach IEEE 754 behandelt werden.
Das IEEE (Institute of Electrical and Electronics Engineering, häufig ausgesprochen als Ei-Triple-ie) ist eine internationale Vereinigung von Ingenieuren der Elektrotechnik, Informatik und Ähnlichem. Vieles, mit dem man als Programmierer im Alltag arbeitet, ist vom IEEE standardisiert worden, aber wenige Standards sind namentlich so bekannt wie IEEE 754.

 Für die Ausgabe in einem angenehmeren Format hat JavaScript ein sehr nützliches Werkzeug: toFixed(), eine Funktion, die eine Zahl mit der vorgegebenen Anzahl an Nachkommastellen ausgibt. Ex toFixed(2)
Es gibt drei spezielle Zahlenwerte, die keine echten Zahlen sind. infinity und -infinity sind das Ergebnis von Rechenoperationen, deren Ergebnis zu groß oder zu klein ist. Ab welcher Größe genau das passiert, unterscheidet sich je nach Browser, aber Division durch 0 ergibt immer infinity. Der dritte Wert, NaN steht für „Not a Number“ und ist das Ergebnis von undefinierten Operationen wie der Wurzel aus –1: Math.sqrt(-1).
 Funktion und Eventhandlern
function zaehleSchuhe(){ … };
Das ist der mysteriöse Eventhandler. So mysteriös ist er aber gar nicht, onclick bedeutet schlicht, dass der JavaScript-Code aus dem Attributwert ausgeführt wird, sobald dieses Element angeklickt wird. Hier wird die Funktion zaehleSchuhe aufgerufen.
Füge vor dem Wort Schuhe ein <span>-Tag mit id="ausgabe" ein.
Ersetze dann die letzte Zeile der Funktion zaehleSchuhe()durch diese: document.getElementById("ausgabe").innerHTML=schuhe;
 getElementById()
Es handelt sich um eine weitere Methode des document-Objekts, und sie findet in der Seite das Element, dessen id-Attribut dem übergebenen Parameter entspricht
Wenn du getElementById() mit einer ID aufrufst, die es im Dokument nicht gibt, dann erhältst du einen sogenannten null-Wert. null-Wert bedeutet, dass es das gesuchte Objekt nicht gibt. Und wenn du versuchst, Methoden daran aufzurufen, endet das mit einem Fehler.
Damit ist das Zielelement gefunden, jetzt muss nur noch der Wert reingeschrieben werden. Das passiert mit der zweiten Neuerung, innerHTML. Der Aufruf von getElementById() gibt ein neues Objekt zurück, das zu dem gesuchten HTML-Tag gehört. Dieses Objekt hat selbst wieder Methoden, die wir aufrufen können, und es hat die Variable innerHTML. Mit der kannst du alles tun, was du mit deinen eigenen Variablen auch tun kannst: ihren Wert auslesen und ihr einen neuen Wert zuweisen. Wenn du innerHTML einen Wert zuweist, dann schlägt diese Änderung sofort in die angezeigte Seite durch, der neue Wert erscheint als Inhalt des Elements.
Die Zuweisung an innerHTML überschreibt den vorherigen Inhalt des Elements. Überhaupt ist innerHTML eher die Holzhammermethode, um den Seiteninhalt zu manipulieren. Wie das auch weniger grobmoto- risch geht, zeige ich dir im Kapitel zur DOM-Manipulation.

Ex         function zaehleSchuhe() {
            var schuhe = paare * 2;
            /*document.getElementByID findet das HTML-Element mit der angegebenen ID.
            Die Eigenschaft innerHTML enthält den Inhalt des Elements, durch sie kannst du auch einen neuen Inhalt setzen*/
            document.getElementById("ausgabe").innerHTML = schuhe;
        }
<button type="button" onclick="zaehleSchuhe();">Klick mich!</button>

Ja, das ist richtig. Nach einem Element zu suchen, das es nicht gibt, ist erlaubt. Erst wenn du damit arbeiten willst, gibt es Probleme. Das ist genau wie im richtigen Leben. Wenn du in deiner ganzen Wohnung dein Handy suchst, das einfach nicht da ist, dann ist das noch kein Fehler, du findest es halt nicht, telefon = null sozusagen. Wenn du jetzt aber versuchst, mit dem Telefon, das du gerade gar nicht gefunden hast, jemanden anzurufen ... dann ist ganz definitiv was faul.

Immer, wenn in JavaScript etwas in Anführungszeichen steht, handelt es sich um einen String. Zum Beispiel "ausgabe" in document.getElementById("ausgabe") ist ein String.

Die Methode charAt()
 "ok".charAt(0); // = "o"
"ok".charAt(1); // = "k"
Möchte man andersherum wissen, an welcher Stelle im String ein bestimmtes Zeichen vor- kommt, helfen dabei die Funktion indexOf() und lastIndexOf(). Beide neh- men als ersten Parameter einen String und suchen dann, wo dieser String in „ihrem“ String vorkommt. Sie geben den Index zurück, an dem sie etwas gefunden haben. Dabei fängt indexOf() vorne im String an zu suchen, lastIndexOf() sucht von hinten.

Ex mit buttons
function zaehleSchuhe() {
 var regalboeden = document.getElementById("boeden").value;
regalboeden = parseInt(regalboeden);
document.getElementById("ausgabe").innerHTML = schuhe;
In body..
Regalböden: <input type="text" id="boeden" value="8"/><br/>

es müssen nur alle Eingabewerte explizit in Zahlen umgewandelt werden. Dazu hat JavaScript die Funktionen parseInt() und parseFloat(), die aus einem String entweder eine Ganzzahl oder einen Float-Wert erzeugen.


Es ist vollkommen okay, einer Variablen, die zuvor einen String enthielt, später eine Zahl zuzuweisen oder umge- kehrt oder ein beliebiges anderes Objekt. In manchen anderen Programmiersprachen funktioniert das nicht, dort kann eine Variable immer nur denselben Typ von Werten enthalten, und der muss in der Deklaration fest- gelegt sein. Diese Sprachen heißen statisch typisiert, JavaScript ist dynamisch typisiert.
Du kannst mit der Eigenschaft innerHTML auch neuen Text an den vorhan- denen anhängen, indem du die Eigenschaft zuerst ausliest, mit dem neuen Text konkatenierst und das Ergebnis wieder zuweist. Außerdem kann der String HTML-Tags enthalten, deswegen heißt es innerHTML.

liste.innerHTML = liste.innerHTML + "<li>" + neu + "</li>" 
Und
liste.innerHTML += "<li>" + neu + "</li>";

Die Funktion substring()
"Beispiel".substring(0, 3) = „Bei“ und "Beispiel".substring(5) = „iel“.

. eigentlich eval() 
function rechne(){
var aufgabe = document.getElementById("rechnung").value;
var plusPosition = aufgabe.indexOf("+");
var summand1 = parseInt(aufgabe.substring(0, plusPosition));
var summand2 = parseInt(aufgabe.substring(plusPosition + 1)); document.getElementById("ergebnis").innerHTML = summand1 + summand2;}

if (meinLevel > monsterLevel){ greifAn();
} 

> größer als
>= größer oder gleich
== gleich
<= kleiner oder gleich
< kleiner
!= ungleich
=== gleich ohne Typkonvertierung !== ungleich ohne Typkonvertierung

if (meinLevel + 3 < monsterLevel){ rennWeg();
} else if (meinLevel – 5 <= monsterLevel) { greifAn();
} else {
      sucheNeuesMonster();
}

Das doppelte Ampersand && ist eine Und-Verknüpfung zwischen zwei Bedingungen. Die gesamte Bedingung ist nur dann true, wenn die Bedingung links vom && und die Bedingung rechts vom && beide true sind.
if (meinLevel + 3 < monsterLevel && *1 monsterName.toLowerCase().indexOf("katze")
Mit zwei Stringfunktionen ist leicht zu finden, ob man einer Katze gegenübersteht: Wenn die Zeichenkette katze im Namen des Monsters vorkommt, dann ist das Ergebnis von indexOf() 0 oder größer. Die toLowerCase()- Funktion setzt monsterName komplett in Kleinbuchstaben um, bevor indexOf() angewendet wird. Das findet dann sowohl die „Große Katze“ als auch die „Wildkatze“

function pruefeVornamen(){
/*pruefe, ob ein Name eingegeben wurde und ob der Name nicht Klausie ist - ich weiß nicht warum, aber der Kunde hat ein Problem mit dem Namen*/
var vorname = document.getElementById("vorname").value;*1
if (vorname == ""){
schreibeFehler("Bitte geben Sie einen Vornamen an");}
       }

die Oder-Verknüpfung ||, die eine Bedingung dann wahr macht, wenn die linke Teilbedingung wahr ist oder die rechte Teilbedingung wahr ist oder beide wahr sind. Strg + Alt + <

Zum Beispiel an eine Funktion, die zu einer zweistelligen Zahl die Quersumme berechnet, die Summe aller Ziffern:
 function quersumme(zahl){
zahl = zahl.toString();
var ergebnis = parseInt(zahl.charAt(0)) + parseInt(zahl.charAt(1)); return ergebnis;
          }

Variablen, die innerhalb einer Funktion definiert werden, sind auch nur innerhalb der Funktion sichtbar. Nicht nur das, die gelten auch nur für diesen Aufruf der Funktion. Beim nächsten Aufruf ist die Variable wieder komplett neu.
Der Bereich, in dem eine Variable sichtbar ist, heißt der Scope der Variablen. In JavaScript gibt es nur zwei Scopes: Globale Variablen sind überall sichtbar, das betrifft alle Variablen, die außerhalb von Funktionen deklariert werden. Variablen, die innerhalb einer Funktion dekla- riert werden, sind nur innerhalb der Funktion sichtbar und heißen lokale Variablen.

Pruefen:
function quersumme(zahl){ 
if (!zahl) return NaN;   ///Hier wird zuallererst geprüft, ob über- haupt ein Parameter übergeben wurde,

Arrays
Arrays zu verschachteln: Die inneren Arrays stellen jeweils ein Koordinatenpaar dar, das äußere Array ist eine Liste dieser Koordinatenpaare. Arrays in Arrays werden auch als mehrdimensionale Arrays bezeichnet, weil genau das ein häufiger Fall ist, bei dem sie eingesetzt werden: um mehrdimensionale Strukturen abzubilden. Denk zum Beispiel an ein Schachbrett mit seinen 8 x 8 Feldern. Ein äußeres Array enthält die Reihen, jede Reihe ist wiederum ein Array und enthält die Felder. Und schon kannst du mit schachbrett[0][0] deinen Turm finden.

var array = [3, 5, 1, 7, 9]; document.write(array[2]);  array[2] = 7; document.write(array[2]);
Die Eigenschaft length kennst du schon von Strings, und sie hat bei Arrays die gleiche Bedeutung:
Wie viele Elemente enthält das Array? Oder besser gesagt, wie viele Elemente sind
es bis zum letzten Element des Arrays, das nicht undefined ist? Dieser Unter- schied ist wichtig, denn undefined Werte, die vor dem letzten definierten Element stehen, werden mitgezählt.
var array = [0, 1, 2]; 
document.write(array.length); array[10] = 10; 
document.write(array.length). ///Insgesamt enthält das Array nun elf Elemente, von denen sieben undefined sind. Da aber danach noch ein definiertes Element kommt, werden sie mitgezählt, die Ausgabe ist 11.
Die meisten Methoden eines Array-Objekts fügen entweder Elemente hinzu oder entfernen sie. push() und pop() fügen ein Element am Ende hinzu und entfernen es wieder. unshift() und shift() tun dasselbe am Anfang und verschieben dabei alle weiteren Elemente um eine Position.
Die beiden Methoden zum Entfernen von Elementen, pop() und shift(), geben auch das entfernte Element zurück. Außerdem interessant sind noch die Methoden reverse(), die ein Array umdreht, und concat(), die ein neues Array erzeugt, indem sie zwei Arrays zusammenfügt.

for (var i = 1; i < 10*3; i++){ document.write(i);
}
__________________
ein Detail von JavaScript, das viele nicht kennen. Wenn eine Funktion mehr Parameter erhält, als sie erwartet, dann stehen diese im arguments-Objekt. Sind keine Parameter deklariert, dann landen alle übergebe- nen Parameter in arguments. So muss für den Aufruf der Funktion nicht jedes Mal ein Array erzeugt werden, man übergibt einfach so viele Zahlen, wie man möchte!
function durchschnitt(){
if (arguments && arguments.length > 0){…
Man kann auf den Inhalt von arguments zwar mit dem Index in eckigen Klammern zugreifen wie bei einem Array, aber argu- ments ist kein echtes Array. Es kennt die eckigen Klammern und die Eigenschaft length, aber keine der Array-Funktionen.
Genau wie Arrays sollte man arguments nur dann benutzen, wenn alle Werte den gleichen Typ und die gleiche Bedeutung haben

Manchmal geht alles schief – Fehler

Fehler werden geworfen, nicht zurück- gegeben. Dadurch ist klar, dass die Funktion auf eine andere Art verlassen wird, als bei einem regulären Ergebnis. Ein Ergebnis über- gibt sie dir in die Hand, einen Fehler wirft sie dir vor die Füße.
Einen Fehler kannst du in JavaScript mit der throw-Anweisung werfen: throw "Die Zahl muss zweistellig sein";. Dieser Fehler ist an der Oberfläche zunächst nicht sichtbar, aber du findest ihn in den Entwicklerwerkzeugen deines Browsers, unter „Konsole“ oder „Fehlerkonsole“.Fehler, die mit throw geworfen werden, werden auch als Ausnahmefehler oder Exceptions bezeichnet.
Ex ohne Prüfungen und Fehler
function quersumme(zahl){
      zahl = zahl.toString();
	var ergebnis = parseInt(zahl.charAt(0)) + parseInt(zahl.charAt(1));
      return ergebnis;
}
Du siehst natürlich sofort, was schiefgehen kann. Ruft jemand die Funktion mit einer Zahl mit mehr als zwei Stellen, dann wird eine falsche Quersumme berechnet und angezeigt. 

Benutze die throw-Anweisung, um einen Fehler zu werfen, wenn die übergebene Zahl nicht zweistellig ist.

if (zahl.length != 2) throw "Nur zweistellige Zahlen erlaubt";

Fehler, die mit throw geworfen werden, werden auch als Ausnahmefehler oder Exceptions bezeichnet.
Das sehe ich nur in der Console.. der User sieht es nicht!

Davon hast du zuerst einfach nur, dass du deine Programmierfehler leichter findest. Du siehst eine Fehlermeldung in der Konsole statt eines falschen Ergebnisses. Wird der Fehler nur in der Konsole angezeigt, spricht man von einem unbehandelten Fehler.

Füge ein Eingabefeld und einen Knopf hinzu. Auf Knopfdruck soll eine neue Funktion berechne den Wert des Feldes auslesen, die Funktion quersumme damit rufen und das Ergebnis ausgeben.

function berechne(){
var zahl = document.getElementById("zahl").value; 
document.getElementById("ergebnis").innerHTML = quersumme(zahl); —> (Die Berechnung findet in der unveränderten Funktion quersumme statt.)
}
window.addEventListener("load", function(){
      document.getElementById("berechne").addEventListener("click", berechne);
});

Ändere jetzt die berechne-Funktion so, dass eventuelle Fehler behandelt und dem Benutzer angezeigt werden.
Das Schlüsselwort try leitet einen Codeblock ein, in dem Fehler auftreten könnten, die behandelt werden sollen.
Mit catch wird der Fehler gefangen. Falls im try-Block ein Fehler auftrat, und nur dann, wird der catch-Block ausgeführt.
In Klammern wird ein Variablen- name angegeben, unter dem die Fehlermeldung innerhalb des catch-Blocks verfügbar ist.
function berechne(){
      var zahl = document.getElementById("zahl").value;
      try {
            document.getElementById("ergebnis").innerHTML = quersumme(zahl);
      } catch (error){
            document.getElementById("ergebnis").innerHTML = "Fehler: " + error; }}


Wird ein Fehler nicht in der Funktion behandelt, in der er auftritt, dann wird er zur aufrufenden Funktion weitergeworfen. Gibt es auch dort keine Fehlerbehandlung, dann wird er wieder weitergeworfen. Und so weiter, bis es einen catch-Block gibt oder der Fehler in der obersten JavaScript-Funktion ankommt und von dort an den Browser weitergeworfen wird. Der schreibt dann den Fehler in die Konsole.


Wenn es sich um reine Programmierfehler handelt, dann sollst du nicht den geworfenen Fehler behandeln, sondern den Programmierfehler beheben.
  Wenn ein Fehler beim Arbeiten mit Benutzereingaben auftritt, dann solltest du ihn immer behandeln, und zwar so, dass der Benutzer auch sehen kann, was passiert ist. Im Beispiel solltest du nicht ausgeben „Fehler! Kaputt!“, sondern „Es sind nur zweistellige Zahlen erlaubt“.
für andere typische Fälle – Fehler beim Lesen von Dateien, Netzwerkfehler ... – gibt es in JavaScript eine andere Arbeitsweise, 

Anstatt Fehler zu werfen, wird an dem Objekt, das die Arbeit für dich erledigt, ein Eventhandler für den Fehlerfall registriert.
                einObjekt.addEventListener("error", behandleFehler);

Funktionen
function eineFunktion(parameter1, parameter2) {...} 
var meineReferenz = eineFunktion;
—! Wir können die Funktion einer Variablen zuweisen, das ist in JavaScript nichts Besonderes. Wichtig ist aber, dass die Klammern nach dem Funktionsnamen fehlen: Schreibt man die Klammern dazu, wird die Funktion aufgerufen und ihr Ergebnis der Variablen zugewiesen. Ohne die Klammern wird die Funktion selbst der Variablen zugewiesen.
meineReferenz(1, 1);
—! Nachdem meineReferenz jetzt eine Funktion referenziert, sollte sie auch aufrufbar sein. es, meineReferenz lässt sich nach der Zuweisung aufrufen, gerade so, als sei mit function meineReferenz eine Funktion diesen Namens deklariert worden.

du kannst noch etwas anderes mit Funktionen machen, und das ist a) interessant und b) ein sehr mächtiges Werkzeug in JavaScript. Du kannst sie als Parameter übergeben. Genau wie der Code oben funktioniert auch dieser:

function eineFunktion(parameter1, parameter2) {...} 
ganzAndereFunktion(eineFunktion);   **Auch hier ist wieder wichtig, die Klammern wegzulassen.

EX
die Array-Funktion sort(). Ein Array zu sortieren, klingt erst mal ganz einfach, das kleins- te Element soll an den Anfang, das größte ans Ende. Aber was ist das kleinste und was das größte? Bei Zahlen ist es noch eindeutig, bei Strings schon weniger – 
Es wäre doch viel praktischer, wenn man der sort()-Funktion mitgeben könnte, wie genau zwei Ele- mente zu vergleichen sind — so! 

function vergleicheNachLaenge(string1, string2)
{ return string1.length - string2.length;} 
//Die Subtraktion ist die kürzeste Methode, diese Sortierfunktion richtig zu implementieren. Die muss nämlich eine negative Zahl zurückgeben, wenn der erste Wert kleiner ist als der zweite, eine positive Zahl, wenn der erste Wert größer ist, und 0, wenn beide Werte gleich sind.
//sort() vergleicht paarweise, bis am Ende alles richtig geordnet ist.
array.sort(vergleicheNachLaenge);
//Der sort()-Methode wird eine Funktionsreferenz übergeben. Einmal mehr: Beachte das totale Fehlen von Klammern.

Callbacks .. 

Wenn du eine Funktion als Parameter übergibst, die nur genau an der Stelle genau einmal gebraucht wird, dann musst du ihr nicht mal einen Namen geben, du kannst sie als anonyme Funktion direkt in den Aufruf schreiben. Das sieht dann so aus:

array.sort(function(zahl1, zahl2){return zahl1 – zahl2;});

___________
Schreibe eine Vergleichsfunktion, durch die sort() Zahlen korrekt nach Größe vergleicht und nicht mehr alphabetisch.
Das ist mit dem Beispiel oben so gut wie identisch ist. Da wurden auch zwei Zahlen verglichen.
function vergleicheZahlen (zahl1, zahl2){
                                    return zahl1 – zahl2;}
Schreibe eine Vergleichsfunktion, um ein Array von Arrays von Zahlen zu sortieren. Dabei soll das Array mit der kleineren ersten Zahl als kleiner angesehen werden. Ist die erste Zahl beider Arrays gleich, sind auch die beiden Arrays für diese Funktion gleich.
function vergleicheArrays(array1, array2){ return array1[0] - array2[0];}

Schreibe eine Funktion, die ein Array von Strings als Parameter erhält. Sie soll alle diese Strings, durch Kommas getrennt, zu einem String zusammensetzen und diesen zurückgeben.Die Variable, in der das Ergebnis gesammelt werden soll, muss schon einen String enthalten, damit weitere dazu konkateniert werden können.
Die Schleife ist der totale Standard, um über ein Array zu iterieren.
function verbindeStrings(strings)
{var ergebnis = "";
for (var i = 0; i < strings.length; i++){
if (i){ergebnis += ",";}          /// if(i) ist die Kurzschreibweise für if(i != 0) //s wird also vor jedem String außer dem ersten ein Komma geschrieben.
ergebnis += strings[i]; }
return ergebnis;}

PS hier die Methode join()die Arbeit abnehmen könnte.

Schreibe eine Funktion, die als Parameter ein Array und eine Funktion nimmt. Die Funktion soll ein neues Array zurückgeben mit allen Werten aus dem Parameter-Array, für das die übergebene Funktion einen Truthy-Wert zurückgibt. Schreibe zwei Beispielfilter für diese Funktion, und teste sie. 1) Aus einem Array von Zahlen sollen nur die geraden Zahlen zurückgegeben werden. 2) Aus einem Array von Strings sollen alle die zurückgegeben werden, die mit einem Vokal anfangen.

function filter(array, filterfunktion){   //die Funktion filter() mit zwei Parametern, einem Array und einer Funktion
var ergebnis = [];  //In diesem Array werden alle Werte gesammelt, die die Filterfunktion für gut befindet.
for (var i = 0; i < array.length; i++){   //Eine Schleife über das übergebene Array ist wirklich nichts Aufregendes mehr.
if (filterfunktion(array[I])){ //Die übergebene Funktion kann mit dem Namen des Parameters aufgerufen werden
ergebnis.push(array[i])     //push() fügt das neue Element am Ende an
} }return ergebnis;}

function filterNurGerade(zahl){
	return zahl %2 == 0;   //Auf gerade Zahlen prüft man mit dem Modulo-Operator
}

function filterVokale(wort){
var ersterBuchstabe = wort.charAt(0).toLowerCase();
return ersterBuchstabe == "a" || ersterBuchstabe == "e" || ersterBuchstabe == "i" || ersterBuchstabe == "o" || ersterBuchstabe == "u";        //fünf Möglichkeiten, fünf Bedingungen mit Oder verknüpft
}

ZWÖLF 

Eventhandler. 

Der allergrößte Teil der Benutzer- interaktion in JavaScript funktioniert mit Eventhandlern.

Nach dem gleichen Prinzip funktionieren auch alle anderen Eventhandler: Man gibt für einen Auslöser an, welche Funktion ausgelöst werden soll, wenn er eintritt.
Eventhandler werden auch als Eventlistener bezeichnet.

Das war früher IE8.. mit onclick .. aber Handler kannst du registrieren, ohne sie im HTML angeben zu müssen.
<div id="klick-mich" onclick="wechsleStyle()">...</div>.  //onclick ist Der Auslöser: Wenn dieses Element angeklickt wird, soll etwas passieren. // "wechsleStyle() ist das Ausgelöste: Diese Funktion wird aufgerufen, wenn der Auslöser eintritt.

<script> function wechsleStyle(){
document.getElementById("klick-mich").classList.toggle("geklickt”);} </script>

Mit jedem Klick wird die Style-Klasse klick-mich dem Element entweder hinzugefügt oder wegge- nommen. Schon hast du deine eigene Checkbox; die CSS-Regel für #klick-mich muss nur definieren, wie der geklickte Zustand aussehen soll.
Die Eigenschaft classList des Elements ist ein weiterer, praktischer Vorgriff auf die DOM-Manipulation im nächsten Kapitel. Die Methode toggle fügt eine Style Klasse hinzu, wenn das Element sie och nicht hat, oder entfernt sie, wenn es schon hat. Methoden add und remove noch unterstützt wer- sind wohl selbsterklärend. die CSS-Regel für #klick-mich muss nur definieren, wie der geklickte Zustand aussehen soll.

Es gibt eine ganze Reihe von Events, für die Eventhandler registriert werden können. Mausevents, Tastaturevents, Events für Formulare und mehr, aber alle funktionieren gleich. 

Handler kannst du registrieren, ohne sie im HTML angeben zu müssen!
Besser ist denn
/* Jetzt modern und hip, Handler registrieren direkt im JavaScript */ 
document.getElementById("klick-mich").addEventListener("click", wechsleStyle); 

wechsleStyle  soll aufgerufen werden, wenn ein Element angeklickt wird.
addEventListener ist eine weitere Funktion, die an allen Objekten, die ein HTML-Element repräsentieren, von JavaScript bereitgestellt wird. Der Eventtyp, auf den reagiert werden soll, wird als erster Parameter und als String angegeben. Und Eine Referenz zu der Funktion, die aufgerufen werden soll. Einmal mehr: keine Klammern, hier wird die Funktion selbst als Parameter übergeben. Das click-Event funktioniert in allen Browsern.

<script>
      document.getElementById("ein-element").addEventListener("click", tuWas);
      document.getElementById("anderes-element").addEventListener("click",
      tuWasAnderes);
    </script> 

So registrierte Eventhandler lassen sich mit der removeEventListener()-Methode des Element-Objekts auch wieder entfernen, man muss als Parameter nur eine Referenz auf dieselbe Funktion übergeben.

Ein <script>-Tag ganz am Ende einzufügen,.. ?? es geht anders . Das load-Event wird ausgelöst, wenn die Seite und alle damit verbundenen Skripte und Stylesheets vollständig geladen wurden. Das ist genau die richtige Stelle, um alle anderen Eventhandler zu registrieren.

Das window-Objekt ist die JavaScript-Referenz auf das Browserfenster und ist global überall verfügbar, ähnlich wie document. Und es reagiert auf das load-Event.
window.addEventListener("load", setup); 
Wenn load ausgelöst wird, kannst du dich darauf verlassen, dass die Seite komplett geladen ist, und kannst ohne weitere Prüfungen deine „echten“ Listener registrieren.

(Internet Explorer 8 :(

Jetzt passe die abflug-Funktion so an, dass nur noch mit gedrückter Strg-Taste abgehoben werden kann

Event-Objekt!
Nach neueren Standards soll statt dieser Eigenschaften eigentlich die Funktion getModifierState verwendet werden, 
Add..:
function abflug(event){.  // parameter in the function !! 
if (event.ctrlKey){.  // diese if is true when ctrl key is pressed
alert("Konstruktion nicht abgeschlossen"); //Aber auch mit gedrückter Strg-Taste ist das Raumschiff noch nicht fertig. ;)
} else { alert("Falscher Startcode! Das Sicherheitsteam ist auf dem Weg!"); } // Nur wenn die Strg- Taste gedrückt ist, lässt sich das Raumschiff noch starten.

Mehr von der Maus
es gibt nicht nur eins, sondern gleich drei Events, die damit umgehen können: mouseover, mousemove und mouseout. Das mouseover-Event wird genau einmal gefeuert, wenn der Mauszeiger in den Bereich des Elements eintritt, das mouseout-Event ebenso, wenn der Zeiger das Element wieder verlässt. Solange sich der Zeiger innerhalb des Elements befindet, wird für jede Bewegung ein mousemove-Event gefeuert.mouseover und mouseout haben in JavaScript die gleiche Funktion wie die :hover-Pseudoklasse in CSS
Die Information, dass sich der Mauszeiger bewegt hat, ist schon toll, aber noch besser wäre es, zu wissen, wo er jetzt ist. Das steckt im Eventobjekt der jeweiligen Ereignisse gleich zweimal drin: in den Eigenschaften clientX und clientY relativ zur linken, oberen Ecke der Webseite und in screenX und screenY relativ zur Ecke des Bildschirms.
Es gibt für die feinere Kontrolle auch noch mousedown und mouseup, zwei Events die in dem Moment gefeuert werden, in dem eine Maustaste her- untergedrückt (mousedown) oder wieder losgelassen wird (mouseup). Beide zusam- men ergeben einen Klick!!
click wird nur durch die linke Maustaste ausgelöst, mousedown und mouseup auch durch die rechte, mittlere und zumindest theoretisch jede weitere Maustaste. 
Welche Taste gedrückt wurde, steht in der buttons-Eigenschaft des Events: 1 für die linke Maustaste, 2 für die rechte und 4 für die mittlere.In buttons kann aber auch eine 3 stehen, wenn die linke und rechte Taste gleichzeitig gedrückt wur- den. Oder eine 7 für alle drei Tasten. Die Codes der einzelnen Tasten werden aufaddiert.
Zuletzt gibt es noch die Möglichkeit, auf Doppelklicks zu reagieren. Du musst dazu nicht selbst zählen, wie oft geklickt wurde, das dblclick-Event übernimmt das für dich.
Das steckt in allen MouseEvents drin 
screenX 
die X-Position des Mauszeigers in Bildschirmkoordinaten 
screenY 
die Y-Position des Mauszeigers in Bildschirmkoordinaten 
clientX 
die X-Position des Mauszeigers in Viewport-Koordinaten 
clientY 
die Y-Position des Mauszeigers in Viewport-Koordinaten 
ctrlKey 
Ist die Strg-Taste gedrückt? 
shiftKey 
Ist die Shift-Taste gedrückt? 
altKey 
Ist die Alt-Taste gedrückt? 
metaKey 
Ist die Meta-Taste gedrückt? Das ist dieses Ding, das nur Apples kennen. 
buttons 
Welche Maustaste(n) ist/sind gedrückt? 
Und metaKey == command key
buttons Welche Maustaste(n) ist/sind gedrückt?

event.target ..
einen Eventhandler für mehrere Elemente zu verwenden.  Die Eigenschaft dazu heißt event.target.
das Ziel des Events, also das Element, mit dem der Benutzer interagiert hat, um das Event auszulösen. 

Event Bubbling 
(„aufsteigende Events“ auf Deutsch.)

Notfallkonsole der USS Schrödinger:
HTML.. <div id="antrieb" class="system">
			<h2>Antrieb</h2>
			<a id="waehle-antrieb">Abschalten!</a>
		</div>

________
function hoverHervorheben(event){} 
function hoverBeenden(event){} 
function setup(){
//An jedem Abschalten-Link wird ein Listener für mouseover und mouseenter registriert.
var seiten = ["antrieb", "holodeck", "schilde", "transporter"];for (var i = 0; i < seiten.length; i++){
document.getElementById("waehle-" + seiten[i]). addEventListener("mouseover", hoverHervorheben);
document.getElementById("waehle-" + seiten [i]). addEventListener("mouseout", hoverBeenden);
} }
window.addEventListener("load", setup); 

eine neue Eigenschaft, nämlich parentElement. Da steckt bei jedem Objekt, das ein HTML-Element repräsentiert,
für die Abschalten-Links also genau das <div> für die Statusanzeige..

function hoverHervorheben(event){
      event.target.parentElement.classList.add("hover"); /// this will add hover to the parent element of the target..!
}
function hoverBeenden(event){
      event.target.parentElement.classList.remove("hover");
}

_______ wenn der Mauszeiger über eines der <div>s fährt, soll die Zahl darin ums eins erhöht werden.

var mouseoverZaehler = 0;
function zaehle(event){
mouseoverZaehler++;
target.innerHTML = mouseoverZaehler;}. ////Beim mouseover wird der Zähler um eins erhöht.
}
__ und noch… 
<button type="button" id="antrieb">Antriebssystem</button>
<span id="antrieb-status">OFFLINE</span>
function energieUmschalten(event){
var statusanzeige = document.getElementById(event.target.id + "-status");
if (statusanzeige.innerHTML.indexOf("OFFLINE") > -1){
statusanzeige.innerHTML = "ONLINE";} else {
statusanzeige.innerHTML = "OFFLINE";

The indexOf() method returns the position of the first occurrence of a specified value in a string.
This method returns -1 if the value to search for never occurs.
Syntax : string.indexOf(searchvalue, start)
Der Rest ist ein einfaches if ... else ...: Wenn im Status OFFLINE steht, wird auf ONLINE geschaltet, ansonsten auf OFFLINE. So geschickt kann man die IDs der Elemente ausnutzen. Die Statusanzeige hat jeweils die gleiche ID wie ihr Knopf, mit einem angehängten -status. Eine Stringkonkatenation gibt uns die ID der Anzeige, und mit getElementById haben wir das richtige Element.

was passiert, wenn im <div> mit click-Handler ein <span> mit click-Handler liegt und darin wieder ein <a> mit click-Handler? Welcher Handler wird dann aufgerufen? Es werden alle Handler aufgerufen, und zwar in aufsteigender Reihenfolge. Es sei denn .. das Event-Objekt hat eine Methode mit dem klang- vollen Namen stopPropagation()

Auch wenn die Events aufsteigen, ändert sich das target nicht, es bleibt immer das innerste Ele- ment, das angeklickt wurde.

Wenn du zum Beispiel auf einen Link klickst, dann will der Browser diesem Link folgen und eine neue Seite anzeigen. Oder du drückst die rechte Maustaste, dann will der Browser unbedingt ein Kontextmenü öffnen. 
Und genau deswegen gibt es eine weitere Methode preventDefault(), die dieses Standardverhalten verhindert. 

Tastatur
keydown, keyup und keypress und verhalten sich genauso wie mousedown, mouseup und click. 
Alle Tastaturevents werden an dem Element ausgelöst, das im Augenblick den Fokus hat. Für viele Elemente ist es deshalb nicht möglich, diese Events zu verarbeiten, weil reine Darstellungselemente (<div>, <span>, <table> ...) nicht den Fokus haben können. Tastaturevents werden deshalb hauptsächlich an Formelementen oder an window verarbeitet.
Wenn du aber wissen möchtest, welche Taste überhaupt gedrückt wurde, dann .. keyCode
Wenn JavaScript schon heute überall funktionieren soll, dann musst du wohl oder übel die Uralteigenschaft keyCode benutzen.
der numerische Wert des Zeichens, normalerweise der ASCII-Code. Für eine Tabelle von Zeichencodes kannst du in den Anhang schauen. Für den Moment reichen aber die Pfeiltasten mit diesen Codes:
inks hoch rechts runter
37 38 39 40

function steuern(event){
if (event.keyCode == 37){alert("Links abbiegen");
} else if (event.keyCode == 38){ alert("Vorwärts!");
} else ... }

Ein keypress-Event wird nur für druckbare Zeichen ausgelöst. Für die Pfeiltasten, Funktionstasten, Shift, Strg und so weiter gibt es nur keydown und keyup
function abflug(event){
      if (event.ctrlKey){
window.addEventListener("keyup", steuern);
Neben dem Keycode kennen Tastaturevents auch noch dieselben Modifier, die dir schon von den Mausevents her bekannt sind: ctrlKey, altKey und shiftKey.

es gibt noch eine ganze Reihe weiterer Events,
resize wird gefeuert, wenn das Browserfenster vergrö- ßert oder verkleinert wird
Die neue Größe ist aus dem Event nicht erkennbar, kann aber in den Eigenschaften window.innerHeight und window.innerWidth gefunden werden
scroll wird ausgelöst, wenn im Browserfenster gescrollt wird,
wie weit insgesamt nach unten bzw. rechts gescrollt wurde, steht in window.pageXOffset und window.pageYOffset.

Die Methode window.setTimeout ruft eine übergebene Funktion nach der übergebenen Zeit auf. So lassen sich in JavaScript zeitgesteuerte Abläufe umsetzen.

window.setTimeout(eineFunktion, 5000);  // Die Zeitangabe erfolgt immer in Millisekunden.
 ___________
Schreibe eine Seite, die die Koordinaten des Mauszeigers sowie den Keycode der zuletzt betätigten Taste anzeigt

function bewegt(event){
document.getElementById("screenX").innerHTML = event.screenX; document.getElementById("screenY").innerHTML = event.screenY; document.getElementById("clientX").innerHTML = event.clientX; 
document.getElementById("clientY").innerHTML = event.clientY;
}
function taste(event){
document.getElementById("taste").innerHTML = event.keyCode; }

function setup(){ window.addEventListener("mousemove", bewegt); window.addEventListener("keyup", taste);}

window.addEventListener("load", setup);


DREIZEHN

Document Object Model. Das DOM ist die Repräsentation eines HTML-Dokuments für JavaScript und andere Programmiersprachen. Es erlaubt dir, den gesamten Inhalt des Dokuments durch entsprechende Objekte zu lesen und zu manipulieren.
In einem Modell werden also Dinge, die außerhalb der Programmiersprache existieren, als Objekte dar- gestellt. Konkret kann das zum Beispiel heißen, dass die gesamte Welt eines Computerspiels ein Modell ist, und dein Charakter ist ein Objekt darin, die Monster sind Objekte, deine Waffen sind Objekte,

Das DOM der Seite ist durch die globale Variable document zugänglich. Immer, wenn du ein Objekt mit document.getElementByID holst, arbeitest du mit dem DOM, immer wenn du an einem solchen Objekt innerHTML änderst oder eine Style-Klasse hinzufügst, hast du also das DOM manipuliert. 
Das DOM, auf das wir in JavaScript Zugriff haben, und die HTML-Struktur selbst sind also nicht identisch, aber zwischen den beiden werden alle Informationen in beide Richtungen ausgetauscht: Alles, was im HTML-Code steht, ist durch das DOM zugänglich, und alle Änderungen am DOM werden sofort ins HTML übernommen und damit für den Leser sichtbar. Wow!

Das document-Objekt ist, man konnte es dem Namen nach schon erraten, der Einstiegspunkt, von dem aus alle DOM-Operationen zugänglich sind. document.getElementById() ist eine der grundlegenden DOM-Methoden, um Elemente zu finden. Und wenn du die innerHTML-Eigenschaft setzt, manipulierst du den Inhalt eines Elements im DOM.
Im Wesentlichen ist das DOM ein großer Baum, in dem Sinne, in dem Informatiker das Wort verwenden: Es gibt eine Wurzel, das <html>- Element, und jedes Element kann Kinder haben. Das klingt genau wie die Grundlagen von HTML, es gibt <html> als oberstes Tag, und jedes Tag kann weitere Tags als Kinder enthalten.

Es gibt auch noch document.getElementsByTagName und document.getElementsByClassName. Beide finden nicht nur ein Element, sondern alle passenden Elemente, es kann ja durchaus mehrere geben. 
 ... damit geht dann so was:
document.getElementById("to-do-liste").getElementsByTagName("li”);
// Finde zuerst das Element mit der ID to-do-liste and suche als Nächstes alle Nachkommen von to-do-liste vom Typ <li>.
getElementsByTagName und getElementsByClassName geben beide eine NodeList zurück. 
NodeLists kennen die eckigen Klammern und die length-Eigenschaft, haben aber keine der Array-Methoden
ine NodeList plötzlich zwischen deinen Fingern ändern kann. Das liegt daran, dass sie live aus dem DOM geupdated wird: entfernst du einen Node aus dem Dokument, verschwindet sie auch aus sämtlichen NodeLists, die sie vorher enthalten haben!

<h1>Aufgaben für den Zauberlehrling</h1>
<ul id="aufgaben">
      <li class="offen">Zauberbücher lesen</li>
      <li class="offen">Tabellenzauber üben</li>
      <li class="offen">Des Meisters Schuhe putzen</li>
      <li class="offen">Wasser schleppen</li>
      <li class="offen">Den Boden wischen</li>
      <li class="offen">Kaffee kochen</li>
</ul>
<button type="button" id="erledigen">Erledigt</button>

Füge unter der Liste einen Erledigt-Knopf hinzu. Wenn dieser Knopf gedrückt wird, dann soll der oberste noch offene Punkt auf der Liste als erledigt markiert werden, indem die entsprechende Klasse zugewiesen wird.


function setup(){
      document.getElementById("erledigen").addEventListener("click", erledigeErsteOffeneAufgabe);
}
function erledigeErsteOffeneAufgabe(){
var offene = document.getElementById("aufgaben"). getElementsByClassName("offen");
if (offene.length > 0){offene[0].className = "erledigt";
}}
window.addEventListener("load", setup);

Die Style-Klassen eines Elements stehen in der Eigenschaft className
Aber weil live aus dem DOM geupdated wird .. Du erinnerst dich, dass ein Element beliebig viele Style-Klassen haben kann? Wenn es zum Beispiel noch eine Klasse wichtig gäbe, dann würdest du sie mit dem Code oben gnaden- los überschreiben und aus offen wichtig würde nur erledigt
benutzen wir lieber was anders

var el = offene[0]; 
el.classList.remove("offen");
el.classList.add("erledigt");

die Eigenschaft classList, die hat einige extrapraktische Methoden, um dir das zu ersparen: add fügt eine Klasse hinzu, ohne die anderen Klassen zu überschreiben.
remove entfernt genau eine Klasse.
contains prüft, ob das Element eine bestimmte Klasse hat.
toggle schaltet eine Klasse um: Ist sie da, wird sie entfernt, fehlt sie, wird sie gesetzt.
var el.  … Das Element, das bearbeitet werden soll, muss jetzt einer Variablen zugewiesen werden, sonst würde wieder das Problem mit dem Live-Update auftreten

Refactoring
Schreibe eine neue Funktion, die ein Element der To-do-Liste als Parameter annimmt und genau dieses Element als erledigt markiert. Diese Art Umbau heißt unter Programmierern Refactoring. Es geht dabei darum, Code einfacher, lesbarer und leichter erweiterbar zu machen.

function erledigeErsteOffeneAufgabe(){
var offene = document.getElementById("aufgaben").getElementsByClassName("offen"); if (offene.length > 0){
erledigeAufgabe(offene[0]); } //Anstatt direkt den Style zu setzen, wird jetzt eine Funktion gerufen! 
}
function erledigeAufgabe(aufgabe){
if (!aufgabe) throw "Parameter aufgabe wird benötigt";
    aufgabe.className = "erledigt";
}

<ul id="aufgaben">
<li class="offen">Zauberbücher lesen <a>Erledigt</a></li> ...
function setup(){
      ...
      var links = document.getElementById("aufgaben").getElementsByTagName("a");
      for (var i = 0; i < links.length; i++){
links[i].addEventListener("click", erledigeAufgabeDirekt); }
}
function erledigeAufgabeDirekt(event){
erledigeAufgabe(event.target.parentElement);
        event.preventDefault();

… Gerade vorhin habe ich behauptet, es gäbe eine elegantere Lösung für die Schleife, die die NodeList abarbeitet. 
while (offene.length > 0){ 
offene[0].className = "erledigt";
}
Eine while-Schleife, wie gezeigt, heißt kopfgesteuert, weil oben in der Schleife geprüft wird, ob die Bedingung wahr ist. Es gibt mit do ... while ... auch eine fußgesteuerte Schleife, die das erst am Ende prüft. Deswegen wird der Rumpf von do ... while ... mindestens einmal ausgeführt, bevor zum ersten Mal geprüft wird, aber ansonsten sind beide Varianten gleich. Ein weiterer Unterschied zum if- Statement ist, dass es bei while kein else gibt. Wenn die Bedingung falsy ist, passiert gar nichts.
es gibt auch Probleme, die mit while ganz einfach zu lösen sind, mit for aber nicht. Das ist vor allem dann der Fall, wenn am Anfang noch nicht klar ist, wie viele Wiederholungen nötig sind.

Mit getElementsByTagName und getElementsByClass kannst du zum Beispiel nicht alle Kinder eines Elements finden oder ein Geschwisterelement. Aber auch dafür gibt es selbstverständlich Möglichkeiten.

Ganz allgemein spricht man von einem Node: Alle Elements sind auch Nodes. 
Texte, Kommentare und sogar Attribute sind ebenfalls Nodes, aber eben keine Elements.

Dafür hat jeder Node die Eigenschaft nodeType. In der steht zunächst mal eine Zahl drin, aber if (nodeType == 1) lässt sich nur ganz schlecht lesen. Deshalb gibt es in einem Node Konstanten für die verschiedenen Typen, denn mit if (nodeType == Node.ELEMENT_NODE) sieht man auf Anhieb, was gemeint ist.

￼

Außerdem gibt es an jedem Node noch die Eigenschaften nodeName und nodeValue

Bei Element-Nodes steht der nodeName immer komplett in Großbuchstaben und ohne < und >, es steht also DIV oder SPAN drin.
Dazu hat jeder Node Eigen- schaften, um von einem Node zum nächsten zu navigieren
previousSibling firstChild lastChild nextSibling

So wird ein Element leergeräumt
while(element.firstChild){element.removeChild(element.firstChild);}

Immer wieder das erste Kind zu entfernen, funktioniert deshalb, weil es sofort aus der Liste verschwindet und das nächste Element das neue erste wird. Auch die Kinder eines Elements werden nämlich live upgedated.

Ein Element, das mit removeChild entfernt wurde, ist nicht mehr mit dem Dokument verbunden. Es hat keinen parentNode und auch keine Geschwister mehr. Wenn es Nachkommen hatte, dann sind die aus dem Dokument auch verschwunden, bleiben aber am Element-Objekt erhalten
Das Gegenstück zu removeChild heißt appendChild

Füge der Aufgabenliste einen Knopf hinzu, der die Reihenfolge umkehrt.
Das Element, dessen Kinder umgedreht werden sollen, wird in eine Variable gespeichert.
In diesem Array werden die Elemente zwischengespeichert.

function umdrehen(){
var liste = document.getElementById("aufgaben"); var kinder = [];
while(liste.firstChild){
kinder.push(liste.removeChild(liste.firstChild); }
while (kinder.length){ liste.appendChild(kinder.pop());}}

Weil removeChild das entfernte Element zurückgibt, sparen wir hier die Variable; der Rückgabewert wird sofort mit push ans Ende des Arrays gehängt. Nachdem die Liste leer ist, werden die Elemente wieder eingefügt. Mit pop kommt das letzte Element des Arrays als erstes zurück, so wird die Reihenfolge der Elemente umgekehrt. Und da pop das Element auch wirklich entfernt, kann diese Schleife so lange laufen, bis das Array leer ist.

Die Methode insertBefore wird genau wie appendChild am neuen Elternelement gerufen, nimmt aber zwei Parameter: zuerst das neue Element und dann das Element, vor dem es eingefügt werden soll.

parent.insertBefore(newChild, parent.firstChild);

Um ein neues Element zu erzeugen, rufst du document.createElement mit dem Tag-Namen als Parameter. 
Der Rückgabewert ist ein Element wie jedes andere und kann mit appendChild ins Dokument eingeklinkt werden. 

Füge ein Eingabefeld
function hinzufuegen(){
var neuerText = document.getElementById("neue-aufgabe").value; if (neuerText.length > 0){
var neuesElement = document.createElement("li");
var neueTextNode = document.createTextNode(neuerText);
neuesElement.appendChild(neueTextNode);neuesElement.classList.add("offen");
document.getElementById("aufgaben").appendChild(neuesElement);   //Und dann das neue Element der Liste hinzufügen. 
document.getElementById("neue-aufgabe").value = "";  //Ganz zum Schluss wird noch aufgeräumt

Attribute und Styles
Es gibt die Methode getAttribute, die als Parameter einen Attributnamen erwartet und den Wert dieses Attributs zurückgibt. Und es gibt die Methode setAttribute, der du einen Attributnamen und einen Wert übergibst und die das Attribut dann setzt.
element.setAttribute("id", "neue-id");
           element.getAttribute("id");

kannst du auch schreiben element.id = ..., das funktioniert zumindest für die häufigen Attribute wie id, name und so weiter.
Für das class-Attribut gibt es hier eine gemeine Ausnahme. Wenn du die Methode setAttribute benutzt, dann ist setAttribute("class", ...)richtig.Als Eigenschaft heißt es aber nicht element.class, sondern, wie am Anfang des Kapitels gesehen, element.className.

CSS Objekt - Zugriff auf Style-Eigenschaften 
Überall, wo in CSS ein Bindestrich vorkommt, wird der im style-Objekt durch CamelCase ersetzt. Aus back- ground-color wird backgroundColor, aus font-size wird fontSize und so weiter und so fort.

window.addEventListener("load", setup); 

function setup(){var lis = document.getElementsByTagName("li");
for (var i = 0; i < lis.length; i++){
lis[i].addEventListener("click", verschiebeAufgabe);}}

function verschiebeAufgabe(event){
var li = event.target;    //// Im Klick-Handler musst du zuerst wissen, welches Element angeklickt wurde.
if (li.parentNode.id == "to-do"){
document.getElementById("done").appendChild(li); } else {
document.getElementById("to-do").appendChild(li);}}

Anhand der ID des Elternelements kannst du herausfinden, in welcher Liste das angeklickte Element gerade steht ...
und es dann der anderen Liste hinzufügen. Es mit removeElement zu entfernen, ist nicht nötig, das passiert von selbst, wenn du es anderswo hinzufügst

Die Eigenschaft textContent enthält den gesamten in einem Element enthaltenen Text, inklusive der Nach- kommen, aber ohne die störenden Tags. Genau das, was du brauchst, um alphabethisch zu sortieren.

function sortiereListe(liste){
      var items = [];
while (liste.firstChild){
var el = liste.removeChild(liste.firstChild); 
if (el.nodeType == Node.ELEMENT_NODE){
items.push(el); }. //  Es werden alle Kinder aus der Liste entfernt, aber nur die Elemente werden ins Array übernommen
      }
while (items.length){
einsortieren(items.shift(), liste);  // Jedes Element wird dann in die Liste einsortiert
}}
function einsortieren(item, liste){
var text = item.textContent;
var current = liste.firstChild;
while (current && (current.nodeType != Node.ELEMENT_NODE || current.textContent < text)){
current = current.nextSibling; }
liste.insertBefore(item, current); } 

VIERZEHN 
Objektorientierung 
Ein Objekt ist eine Datenstruktur, die zusammengehörige Informationen (Eigenschaften) enthält und Operationen (Methoden) anbietet, die mit diesen Informationen arbeiten

Objekte wissen also Dinge in ihren Eigenschaften und können Dinge durch ihre Methoden.
Ist das so richtig?

String-Objekte wissen was: Sie wissen, welchen Text sie enthalten und wie lang der ist. Und sie können was: Sie können einen Teil des Strings extrahieren, sie können einen anderen String suchen und noch so einiges mehr.

 In einem rein objektorientierten Programm gibt es keine Variablen oder Funktionen, die nicht zu einem Objekt gehören.

das wichtigste Argument für objektorientierte Programmierung ist, dass sie unserer Wahrnehmung der Welt am nächsten kommt. 

Wenn du dir eine Katze anschaust, dann siehst du sie nicht als Sammlung von unabhängigen Variablen – katzeRasse, katzeGewicht, katzeName – und Funktionen – katzeKratzeMöbel(), katzeSchnurre(). Du siehst sie als eine Einheit, die die Eigen- schaften Rasse, Name und Gewicht besitzt und die Aktionen kratzeMöbel() und schnurre() ausführen kann.

Noch deutlicher wird dies, wenn Vererbung hinzukommt. Mit Vererbung werden Zusammen- hänge ausgedrückt wie „diese Katze ist vom Typ Katze, jede Katze ist auch ein Säugetier, jedes Säugetier ist auch ein Tier, jedes Tier ist auch ein Lebewesen“. Du wirst sehen, dass Vererbung ein sehr mächtiges Werkzeug ist.

Wie erzeuge ich ein Objekt in weniger als 5 Sekunden.
var meinErstesObjekt = {};
Es hat keine Eigenschaften und keine Methoden. Es hat aber zumindest einen Typ: jedes Objekt, das so erzeugt wird, ist vom Typ Object.

var schroedingersKatze = {};
schroedingersKatze.name = "Kleiner Stinker";
schroedingersKatze.rasse = "Straßenmischung";
schroedingersKatze.gewichtInKG = 4.5;
schroedingersKatze.mutter = {};  //Ein Objekt kann als Eigenschaften weitere Objekte enthalten.
schroedingersKatze.mutter.name = "Mietzhilde von Katzenstein";
schroedingersKatze.lebendig = null;

Oder auch 
schroedingersKatze.liebstes Fressen = "Käse";X FALSCH
schroedingersKatze["liebstes Fressen"] = "Käse";
document.write(schroedingersKatze["liebstes Fressen"]);

Mit eckigen Klammern kann der Name der Eigenschaft in einer Variablen stehen.
var eigenschaft = "gewichtInKG";
objekt[eigenschaft] = 4.8; jetzt wird der Inhalt der Variablen eigenschaft als Name benutzt und korrekt ein Wert der Eigenschaft gewicht zugewiesen.

???

Es war doch von Anfang an klar, dass zwischen den geschweiften Klammern früher oder später etwas stehen würde. Genau das passiert jetzt, zwischen den Klammern stehen die Initialwerte der Eigenschaften.
Das verwendete Format heißt JSON, für JavaScript Object Notation
var schroedingersKatze = {
name:"Kleiner Stinker",besitzer:"Schroedinger", alter: 4,
        gewicht: 4.5,
rasse:"Straßenmischung", impfungen: ["Tollwut", "Masern"], farbe: {
      grundfarbe: "orange",
	streifen: "schwarz”}

Objekt Methoden

Es ist nicht unbedingt notwendig, dass ein Objekt Methoden und Eigenschaften hat. Ein Objekt, das nur Eigenschaften hat (oder nur Methoden, aber dieser Fall ist seltener), ist trotzdem ein vollwertiges Objekt.

var schroedingersKatze = {
name: "Kleiner Stinker"; aergereSchroedinger: function(){*1
            for (var i = 0; i < 100; i++){
                  alert("Miau!"); 
}}}

Hier wird die Methode erschaffen und der Eigenschaft aergereSchroedinger zugewiesen. Sie kann anschließend als schroedingersKatze. aergereSchroedinger() aufgerufen werden. Und dann wird Schrödinger sich ärgern.

Noch viel toller wäre es natürlich, wenn die Methode auch etwas mit den Eigenschaften ihres Objekts anfangen könnte. Aber da gibt es noch ein kleines Hindernis.
Das wird nicht funktionieren..
var schroedingersKatze = {
      name: "Kleiner Stinker",
      begruesse: function(){
            alert("Miau, ich bin " +name);
      }
}
schroedingersKatze.begruesse();

Ergebnis : “Miao ich bin ___” Katze bleibt anonym!
es fehlt noch : Das Schlüsselwort this und Function Binding!
Das Schlüsselwort this und Function Binding
 Um auf die Eigenschaften eines Objekts zuzugreifen, musst du das Objekt ja benennen. Aber beim Namen nennen darfst du es nicht. Ich helf dir raus aus dem Dilemma: Das umgebende Objekt darfst du immer this nennen.
this ist eine Variable, die überall verfügbar ist und immer auf das lokale Objekt verweist,
So richtig
var schroedingersKatze = {
      name: "Kleiner Stinker",
      begruesse: function(){
Jetzt muss der Variablenname nicht mehr bekannt sein, durch this bekommen wir immer das richtige Objekt. Und zwar auch dann noch, wenn es mehrere Katzen gibt.
alert("Miau, ich bin " + this.name); }
}
Beim Aufruf von Eventhand- lern, auch wenn diese zu einer Funktion gehören, enthält this nämlich immer das window-Objekt. Frag mich nicht, warum, es ist einfach so. Um dieses Problem zu umgehen, bieten moderne Browser die bind- Funktion an: Mit der kannst du selbst festlegen, was für einen Methodenaufruf in this drinstecken soll.
Wuerde so aussehen
feld.addEventListener("blur", schroedingersKatze.update.bind(schroedingersKatze);
Als Parameter erwartet bind das Objekt, das in der ursprünglichen Funktion als this verfügbar sein soll.

Maps — >  assoziative Arrays
ein assoziatives Array kann auch beliebige andere Objekte als sogenannte Schlüssel verwenden.
Ex.    geburtstage["Freundin"] = "17.4."; // Freundin ist der Key 

JavaScript hat keinen eigenen Datentyp für Maps, denn Objekte können schon alles, was du brauchst.

Erstelle eine neue Seite mit einem Eingabefeld „Name“ und einem Eingabefeld „Geburtstag“.


______________


Setze die folgenden Dinge mit JavaScript in eine Vererbungsbeziehung: Kaffee, Lebensmittel, Speise, Sandwich, Getränk, Kuchen
Alle genannten Dinge sind Lebensmittel, also steht Lebensmittel an der Spitze der Kette. Da Lebensmittel selbst von nichts erbt und auch keine Methoden implementiert, muss der Prototyp nicht angegeben werden, er ist dann einfach leer.
function Lebensmittel(){...}
function Speise(){...}
Speise.prototype = new Lebensmittel(); 
function Getraenk(){...}
Getraenk.prototype = new Lebensmittel(); 
function Kaffee(){...}
Kaffee.prototype = new Getraenk(); 
function Sandwich(){...} 
Sandwich.prototype = new Speise(); 
function Kuchen(){...} 
Kuchen.prototype = new Speise();
Kaffee ist ein Getraenk. Speise und Getraenk erben direkt von Lebensmittel. Sandwich und Kuchen sind beides Speisen.

FÜNFZEHN 
Am Anfang war der Cookie.
Vor gar nicht so langer Zeit waren Cookies die einzige Möglichkeit, Daten auf der Clientseite, also auf dem Computer des Benutzers, zu speichern. 
sie erfüllen auch heute noch wichtige Aufgaben. Der eigentliche Zweck von Cookies ist es, kleine Datenmengen zwischen Browser und Server auszutauschen. Cookies werden mit jedem HTTP-Request an den Server geschickt. Im Detail funktioniert das so: 
Der Server schickt mit seiner Antwort auf einen Request die Aufforderung, einen Cookie zu speichern. 
Der Browser denkt sich: „Na gut, tut ja nicht weh“, und speichert den Cookie.
Von da an schickt der Browser bei jedem neuen Request diesen Cookie mit. Der Server braucht ihn vielleicht gar nicht immer, aber das kann der Browser ja nicht wissen: Er schickt alles mit, was von diesem Server stammt.
Meistens wird ein Cookie gesetzt, weil der Server einen Set-Cookie-HTTP-Header geschickt hat. Bei jedem Request werden alle Cookies, die der Server sehen darf, im Header Cookie mitgeschickt.
HTTP eigentlich ein zustandsloses Protokoll ist, also jeder Request so ausgeführt wird, als sei es der erste an den Server. Session-Cookies werden benutzt, um das zu umgehen.
Webseiten können Cookies nur für ihre eigene Domäne setzen, egal, ob per JavaScript oder HTTP-Header: Die Seite www.schroedingersseite.de kann in das Domain-Attribut nur www.schroedingersseite. de schreiben, alles andere wird vom Browser abgewiesen. Und nur Cookies mit diesem Domain-Attribut werden bei jedem Request an www.schroedingersseite.de geschickt. Das Path-Attribut schränkt weiter ein, an welche Seiten auf dem Server der Cookie gesendet wird: Es muss zum URL-Pfad passen, damit der Cookie mitgeschickt wird. Cookies können für alle Subdomains einer Domäne gelten.
Und es gibt noch weitere Einschränkungen, was mit einem Cookie passieren darf. Ist das Attribut Secure gesetzt, dann wird er nur bei verschlüsselten Verbindungen (HTTPS) weitergegeben, mit dem Attribut HttpOnly kann ein Cookie von JavaScript nicht gelesen werden. Das ist für uns zwar blöd, da aber Cookie-Diebstahl häufig durch bösartiges JavaScript erfolgt, ist dieses Attribut sehr wichtig. 
Auch JavaScript darf nur Cookies der eigenen Domäne sehen, aber bei überraschend vielen Webseiten kann man durch sogenannte Skript-Injection ein bösartiges JavaScript einschmuggeln, das vom Browser so behandelt wird, als käme es von der Domäne dieser Seite. Dieses Skript kann alle Cookies von der Domäne lesen, die nicht als HttpOnly markiert sind. 
Als Letztes haben Cookies noch ein Verfallsdatum: Ist das Datum im Expires-Attribut erreicht, wird der Cookie gelöscht. Max-Age hat die gleiche Funktion, aber anstelle eines Datums wird die Zeit, für die der Cookie frisch bleibt, in Sekunden angegeben.
[Achtung] Außerdem hat jeder einzelne Cookie ein Größenlimit von ca. 4 kB.
Die WebKit-Browser lassen bei Seiten, die über das File-Protokoll geladen wurden, keine Cookies zu. Benutze für die Übungen in diesem Abschnitt bitte Firefox oder Internet Explorer.
Wie man von JavaScript aus mit Cookies arbeitet, ist capenga.[Notiz] Capenga (gesprochen ka-pen-ga) ist ein Wort aus dem Brasilianischen und bezeichnet etwas, das zwar funktioniert, aber nicht besonders gut oder auf eine sehr hässliche Art. 
Grundsätzlich gibt es eine Eigenschaft, document.cookie, die für alle Welt wie ein String aussieht. In diese Eigenschaft kannst du einen Cookie schreiben, aber du musst ihn schon selbst richtig formatieren: Der Name des Cookies, gefolgt von einem Gleichheitszeichen, gefolgt vom Wert. 
document.cookie = "meinCookie=meinWert";  .// Ein Gleichheitszeichen. Achte darauf, dass es keine Leerzeichen zwischen Namen, Gleichheitszeichen und Wert geben darf.
function setzeCookieAusFormular(){
var name = document.getElementById("name").value; 
var wert = document.getElementById("wert").value; 
var name = nameFeld.value;
var wert = wertFeld.value;
setzeCookie(name, wert);
nameFeld.value = "";
wertFeld.value = "";
zeigeCookies();
}
function pruefeCookieName(name){
//Schade, dass wir noch keine regulären Ausdrücke können. Naja, es geht auch so.
      if (name.indexOf(",") > -1 || name.indexOf(";") > -1 || name.indexOf(" ") >
      -1 || name.indexOf("=") > -1){
            alert("Ungültiger Name");
            return false;
      }
return true;

function pruefeCookieWert(wert){
if (wert.indexOf(",") > -1 || wert.indexOf(";") > -1 || wert.indexOf(" ") > -1){
            alert("Ungültiger Wert");
            return false;
      }
return true; }

function setzeCookie(name, wert){
/*Wenn Name und Wert gültig sind, schreibe den Cookie*/ if (pruefeCookieName(name) && pruefeCookieWert(wert))*2{
document.cookie = name + "=" + wert; }
}
function zeigeCookies(){
leereAusgabe();

var cookies = document.cookie.split(";");
      var ausgabe = document.getElementById("ausgabe");
      for (var i = 0; i < cookies.length; i++){
            var li = document.createElement("li");
            li.appendChild(document.createTextNode(cookies[i]));
            ausgabe.appendChild(li);
} }

function init(){
      document.getElementById("speichern").addEventListener("click",
      setzeCookieAusFormular);
      zeigeCookies();
}
window.addEventListener("load", init);

mein Problem mit document.cookie.
 in Wirklichkeit macht es im Hintergrund nur Blödsinn und fügt alle Cookies zu einem String zusammen. 
es gibt fertige Bibliotheken dafür, zum Beispiel jquery-cookie
So muss das Verfallsdatum angegeben werden, und zwar genau so,
document.cookie="meinCookie=meinWert; expires=Tue, 24 Dec 2013 23:59:00 UTC
Aber wenn du glaubst, das könntest du mit JavaScript auch wieder auslesen, dann hab ich schlechte Neuigkeiten für dich.

die weiteren Attribute stehen in document.cookie einfach nicht drin, an die kommst du von JavaScript aus nie wieder dran. Um prüfen zu können, ob dein Cookie mit allen Attributen korrekt ist, musst du die entsprechende Funktion deines Browsers verwenden.

Es gibt nämlich seit HTML5 eine viel bessere Lösung für das Speichern von Daten am Client. Je nachdem, wem man zuhört, heißt sie Local Storage, HTML5 Storage oder, so heißt der entsprechende Standard, Web Storage

localStorage.setItem("Zucker", "2kg"); 
localStorage["Eier"] = 12;
alert("Kaufe Eier: " + localStorage.getItem("Eier"); alert("Kaufe Zucker: " + localStorage["Zucker"]; //

Für Name-Wert-Paare gibt es auch eine andere Art des Zugriffs, die du schon kennst: mit eckigen Klammern. Du kannst Web Storage genau wie ein x-beliebiges Objekt behandeln und so lesen und schreiben. localStorage["Zucker"]
Lesen geht auch durch die getItem-Methode, die als Parameter nur den Namen des Eintrags erwartet. localStorage.getItem("Eier")
Für Bonuspunkte prüft deine Anwendung als Erstes, ob Web Storage über- haupt zur Verfügung steht. if (window.localStorage) {...}

aber es gibt auch das sehr komfortable Modernizr- Skript (http://modernizr.com/),
Auch wenn du etwas anderes ins Web Storage reinsteckst, gespeichert werden immer Strings. Wenn du eine Zahl haben möchtest, dann musst du selbst wieder mit parseInt() konvertieren.
length hält keine Geheimnisse mehr, genau wie bei Arrays steht drin, wie viele Einträge es gibt.
for (var i = 0; i < localStorage.length; i++){ var name = localStorage.key(i);
var wert = localeStorage[name];}
Die key-Methode gibt den Key des n-ten Key-Value-Paares zurück.


Mit JSON.stringify wird aus jedem beliebigen Objekt ein String, mit JSON.parse macht man aus dem String wieder ein Objekt.

var einArray = [1, 2, 3, 4, 5]; 
localStorage["meinArray"] = JSON.stringify(einArray); 
einArray = JSON.parse(localStorage["meinArray"]);*

Alle Einträge im Web Storage werden in UTF-16-Kodierung gespeichert, das heißt, es sind 2 Byte pro Zeichen. Es stehen je nach Browser also 5 oder 10 MB zur Verfügung.

Alle aktuellen Browserversionen löschen die Web-Storage-Daten, wenn der Benutzer alle Cookies löscht. Das ist ungünstig, vor allem dann, wenn wichtige Daten nur dort gespeichert waren.
Ein weiterer, wichtiger Grund, seine Steuererklärung oder Ähnliches nicht im Web Sto- rage abzulegen ist, dass die Daten dort nicht verschlüsselt werden. 
Web Storage stellt hier die große Ausnahme dar: Jede Änderung der Daten führt dazu, dass in allen anderen Tabs, die auf dasselbe Web Storage zugreifen und die also von derselben Domäne geladen wurden, ein storage-Event geworfen wird. 
Das ist die erste zuverlässige Methode, zwischen mehreren Tabs zu kommunizieren

window.addEventListener("storage", function(event){
alert("Eintrag "+ event.key+ " geändert von " + event.oldValue + " in " + event.newValue);
});

Als letzten interessanten Punkt gibt es neben localStorage noch einen weiteren Speicherbereich im Web Storage. Dieser Bereich heißt sessionStorage, hat die gleichen Einschränkungen wie localStorage und wird auch auf die gleiche Weise benutzt.
Der Unterschied ist, dass sessionStorage noch eingeschränkter ist. Erstens wird es nicht zwischen mehreren Tabs geteilt, sondern jeder Tab hat seine eigene Instanz, zweitens wird es bei Beenden des Browsers geleert
Mit der Spezifikation IndexedDB gibt es auch die Möglich- keit, im Browser eine echte Datenbank zu benutzen
JavaScript kann heute das ganze Dateisystem des Clientrechners lesen.
jetzt gibt es die File-API. JavaScript-Anwendungen können damit lesend auf das Dateisystem zugreifen.. Nicht schreiben..
Der Benutzer muss Dateien, die JavaScript lesen darf, aktiv auswählen, zum Beispiel in einem Eingabefeld vom Typ file.
File-Objekt
Ein Eingabefeld vom Typ file ist eine Möglichkeit, wie du Dateien zur Bearbeitung in JavaScript auswählen kannst. Das multiple-Attribut legt fest, dass mehrere Dateien gleichzeitig gewählt werden können.
<input name="dateien" id="dateien" type="file" multiple/>

Die spezielle files-Eigen- schaft des Dateieingabefeldes gibt dir Zugriff auf die ausgewählten Dateien. Es steckt ein Objekt vom Typ FileList drin, aber was sich verhält wie ein Array, wird auch behandelt wie ein Array.
  
function waehleDateien(event){
var dateien = event.target.files;
for (var i = 0; i < dateien.length; i++){
            schreibeDateiInfo(dateien[i]);
}

tr.appendChild(erzeugeSpalte(datei.name)); tr.appendChild(erzeugeSpalte(datei.type)); tr.appendChild(erzeugeSpalte(datei.lastModifiedDate. toLocaleDateString())); 
tr.appendChild(erzeugeSpalte(datei.size));



Der Mime-Type ist eine Beschreibung, welche Art von Inhalt eine Datei enthält, ähnlich der Dateiendung. Ein Mime-Type besteht aus zwei Angaben, dem Type und dem Subtype, getrennt durch einen /. Der Typ gibt allge- mein die Art des Inhalts an, zum Beispiel text, image, audio oder video. Der Sub- type definiert näher, in welchem Format die Daten vorliegen. Beim Typ Text gibt es unter ande- rem text/plain für einfa- che Textdateien und text/
html für die Dateien, mit denen du dich seit einigen hun- dert Seiten beschäftigst. Bei Bil- dern gibt es image/jpeg, image/png und viele mehr, bei Audiodateien zum Beispiel audio/mp3 und so weiter. Möchte man von „irgendeiner Art Bild“ sprechen, wird das als image/* dargestellt. Dateien, die zu einer bestimmten Anwen- dung gehören, werden meistens als Subtype von applica- tion einsortiert, so wie application/msword für Microsoft-Word-Dateien. Dateien mit unbekanntem Typ werden meistens als appli- cation/octet-stream erkannt, das klingt genauer als ahnung/keine, bedeutet aber das Gleiche.
Eine ausführliche Liste findest du hier: http://www.iana.org/ assignments/media-types
Um den Dateiinhalt zu lesen, gibt es einen weiteren Objekttyp, den File- Reader. Der kann nicht nur Dateien lesen, der kann Dateien auf verschiedene Arten lesen: als Text, als Binärdatei oder als Data-URL.
Data-URLs sind ein kleines, aber nützliches Fea- ture von HTML5. Es handelt sich um URLs mit dem data:-Protokoll, die nicht angeben, wo eine Ressource gespeichert ist, sondern die Ressource direkt enthalten. Dazu wird der Dateiinhalt in Base64 kodiert, eine Kodierung, die Binärdaten in eine Reihe von druckbaren Zeichen umsetzt.
Das L von URL ist dann natürlich falsch. Es ist kein Locator mehr, der sagt, wo die Ressource zu finden ist, sondern die Ressource ist direkt enthalten
Das Problem ist, dass es schon mal etwas länger dauern kann, Dateien zu lesen. JavaScript kann aber nicht mehrere Dinge gleich- zeitig tun. Würde man also warten, bis die Datei vollständig gelesen ist, dann ginge in der Zwischenzeit nichts anderes.
Genauer ausgedrückt: JavaScript ist von Grund auf single-threaded. In einem Programm können niemals zwei Dinge gleichzeitig passieren. Egal, was das Pro- gramm tut, es arbeiten niemals mehrere Teile parallel.

Um das zu vermeiden, sind alle Operationen des FileReaders asynchron: Die Methode kehrt sofort und ohne Ergebnis zurück. Im Hintergrund liest der Browser die gewünschte Datei, und zwar außerhalb von JavaScript, so dass der Rest der Seite nicht blockiert wird. Wenn er fertig ist, schickt er ein Event, das du, wie gewohnt, behandeln kannst.

Ein neuer FileReader wird einfach so erzeugt, er muss noch nicht wissen, welche Datei er später mal lesen soll.
Das wichtigste Event ist load, es wird gefeuert, wenn die Datei vollständig geladen ist.
 
var leser = new FileReader(); 
leser.addEventListener("load", function(event){
var inhalt = event.target.result;});
leser.readAsDataURL(datei);

Um eine Datei als Text zu lesen, rufst du die Methode readAsText auf, ansonsten bleibt alles gleich. Binärdaten kannst du mit readAsBinaryString oder readAsArrayBuffer lesen, aber der Umgang mit Binärdaten ist ein fortgeschrittenes Thema und wird in diesem Buch nicht behandelt. Du sollst nur wissen, dass es möglich ist und du mit JavaScript selbst aufwendige Anwendungen, wie zum Beispiel Videoschnitt, ausführen kannst.

loadstart |  Dieses Event wird gefeuert, wenn das Laden beginnt.
progress | Während des Ladens tritt immer wieder die- ses Event auf und berichtet den Fortschritt.
abort | Wird das Laden mit der abort-Methode abgebrochen, kommt dieses Event.
load  | Das kennst du schon, wird gefeuert, wenn alles geladen ist.
error  | Falls mal ein Fehler auftritt, kommt dieses Event.
loadend | Ein zusammengefasstes Alles-vorbei-Event. Kommt sowohl nach load als auch nach error.

 Das switch-Statement
switch ist im Grunde genommen eine spezielle Art von if-else, bei dem alle Entscheidungen vom Wert derselben Variablen abhängen, hier zum Beispiel vom Namen des Fehlers. Für die verschiedenen Werte gibst du dann jeweils einen case-Block an, dessen Inhalt dann ausgeführt werden soll. Außerdem kannst du einen default-Block angeben, dessen Inhalt ausgeführt wird, wenn kein case passt.
 
switch (event.target.error.name){
case "NotFoundError": meldung = "Datei nicht gefunden."; break;
case "EncodingError": meldung = "Datei ist zu lang, um sie als Data-URL zu lesen."; break;
default: meldung = "Keine Ahnung, was kaputt ist";
So reagierst du auf einen Wert. Wenn in event.target.error.name der Wert "NotFoundError" steht, dann wird der Code nach dem Doppelpunkt ausgeführt.
 
Wenn du mit readAsText lädst, kannst du als zweiten Para- meter ein Encoding angeben, zum Beispiel „UTF-8“. Dann klappt’s auch mit den Umlauten.

Und um die einzelnen Zeilen zu bekommen, kannst du auf dem eingelesenen String split("\n") aufrufen: "\n" stellt einen Zeilenumbruch dar, und split macht damit aus dem String ein Array von Strings, bei jedem Zeilen- umbruch fängt ein neuer String an. Und jetzt lass dich von mir nicht stören, ich finde deine selbst gewählte Aufgabe ziemlich cool.

leser.readAsText(event.target.files[0], "UTF-8");
var zeilen = event.target.result.split("\n");

Leider haben wir keinen Platz, um ausführlich über die Drag-&-Drop-API von HTML5 zu sprechen. Mit allen Events und Sonderfällen ist die etwas unübersichtlich und auch nur begrenzt schön. Eine besonders tolle Sache damit wollte ich dir aber dennoch nicht vorenthalten: die Dateiauswahl per Drag & Drop.

Drag & Drop nur funktioniert, wenn das dragover-Event abgebrochen wird. Tust du das nicht, dann wird auch kein drop-Event gefeuert. Und wo wir schon davon sprechen:

SECHZEHN 

<video src="stapeln2013/videos/flaschenstapeln.mp4" controls></video>
<audio src="essprichtderboss.ogg" controls></audio>
Das Boolesche Attribut controls (in der Langschreib- weise controls="controls") gibt an, dass der Browser die üblichen Bedienelemente für einen Mediaplayer anzeigen soll: Play-/Pause-Knöpfe, Lautstärkeregler, Fortschrittsleiste. Fehlt das Attribut, gibt es auch keine Bedienelemente, <video> zeigt nur sein Bild, <audio> wird komplett unsichtbar.

Auch falls keine Bedienelemente dazu angezeigt werden, sind die Audio- und Video-Tags nicht sinn- los: Man kann das Abspielen auch per JavaScript kontrollieren, 
￼

Ein Codec ist, in diesem Kontext, ein Programm das Audio- und Videodaten in ein bestimmtes Dateiformat codiert und sie zum Abspielen wieder decodiert. Um zum Beispiel MP3- Dateien abspielen zu können, benötigt dein Computer ein MP3-Codec, 

Chrome und Firefox (und Opera) verwenden das offene und kostenlos nutzbare WebM, Safari und Internet Explorer benutzen MP4
Selbst dieser positive Ausgang heißt für uns Webentwickler leider, dass wir immer zwei Dateien bereitstellen müssen, zum Beispiel: .webm und .mp3 für Audio und .webm und .mp4 für Video.
DukannstmehrereURLsangeben.DerBrowserliest sie der Reihe nach ein und verwendet die erste, deren Mime-Type er darstellen kann. Den Mime-Type zu jeder URL musst du angeben.
 
<video controls>
<source src="stapeln2013/videos/flaschenstapeln.webm" type="video/webm"/>
<source src="stapeln2013/videos/flaschenstapeln.mp4" type="video/mp4"/> 
Dein Browser unterstützt das &lt;video&gt;-Tag nicht. Du kannst aber das Video vom Flaschenstapeln <a href="stapeln2013/videos/flaschenstapeln.mp4"> herunterladen</a>
            </video>

 bei <audio> is gleich
<audio> und <video> unterstützen noch genau ein weiteres Tag:
Das <track>-Tag dient dazu, Untertitel einzubinden oder auch andere Texte, die zu bestimmten Zeiten im Video erscheinen sollen

https://www.html5rocks.com/en/tutorials/track/basics/


MIME TYPES
WebM Audio (.webm) / audio/webm
MPEG-4 (.mp3) //  audio/mpeg
WebM Video (.webm) // video/webm 
MPEG-4 (.mp4) // video/mp4 

Warum haben MPEG-4-Audiodateien die Dateiendung .mp3? Weil das Audiocodec formal richtig „MPEG-1/ MPEG-2 Audio Layer III“ heißt, die drei kommt von Layer III. MP4-Dateien bekommen ihren Namen dagegen von der vier in „MPEG-4 Part 14“. Hurra, Verwirrung!

￼
￼


Mit eigene knöpfe 
function init(){
      var knopfPlay = document.getElementById("play-knopf");
      var knopfPause = document.getElementById("pause-knopf");
      var radio = document.getElementById("mein-radio");
      knopfPlay.addEventListener("click", function(){
radio.play();*1 });
knopfPause.addEventListener("click", function(){ radio.pause();*2
}); }
window.addEventListener("load", init);

￼

Es gibt noch viele weitere Eigenschaften…
Ein Frame ist, im Kontext von Audio- und Videodaten, nicht leicht in Worte zu fassen. Du weißt, dass dein Fernseher 24 Bil- der pro Sekunde anzeigt, damit du ein bewegtes Bild wahr- nimmst? Wenn du einen Frame als ein solches Einzelbild ver- stehst, dann ist das nicht zu 100 % richtig, aber nahe dran.

Was machst du also, wenn unter- wegs etwas schiefgeht?
Wie du es von einem gut erzogenen JavaScript-
Objekt erwartest, teilt dir ein MediaElement
durch Events mit, wenn etwas schiefgeht. Wenn die Ver-
bindung zum Server komplett abbricht oder wenn ein Video
nicht decodiert werden kann, wird ein error-Event gefeuert.
Nach einem error wird die Situation nicht mehr von alleine besser;
du kannst versuchen, die Ressource neu zu laden, aber auch das hat keine Erfolgsgarantie. Der häufigere Fall, dass der Browser keine Daten hat, um den nächsten Frame darzustellen, wird durch das Event waiting signalisiert. Sind wieder Daten verfügbar, wird ein canplay-Event gefeuert. Noch schöner ist das canplaythrough-Event, es sagt aus, dass nicht nur weitere Daten verfügbar sind, sondern dass das Abspielen wahrscheinlich auch ohne weitere Unterbre- chungen bis zum Ende läuft.
 Mit HTML5 ist <embed> ganz offiziell das Tag, um Plug-ins einzubinden
Java ist ein weiteres verbreitetes Plug-in, es bet- tet einen bestimmten Typ Java-Anwendungen, sogenannte Applets, im Browser ein

s gibt zum Beispiel die WebAudio-API, die zwar schwieriger zu benutzen ist, die aber eine feine Kontrolle über abgespielte Audioressourcen ermöglicht: mehrere Sounds gleich- zeitig abspielen, mehrere Kanäle abmischen, Filter anwenden und mehr. Damit kannst du ein komplettes Mischpult in JavaScript reali- sieren oder die API für Profisound in Browserspielen benutzen
auch Aufnehmen aus dem Browser wird möglich, die Methode navigator.getUserMedia öffnet den Weg zu Kamera und Mikrofon – 
http://labs.dinahmoe.com/rickastley

zeichnen auf dem <canvas>!
Die Attribute height und width sind bei <canvas> notwendig, Größenangaben im Stylesheet funktionieren nicht
<canvas height="200" width="500">
Dein Browser unterstützt &lt;canvas&gt; nicht, 
bitte besorg dir endlich einen neuen. //Wie bei <audio> und <video> wird der Inhalt von <canvas> nur angezeigt, wenn der Browser das Tag noch nicht kennt.
      </canvas>
die Größe eines <canvas> nicht per CSS zu setzen ist.

function zeichne(){
var canvas = document.getElementById("grafik"); 
var context = canvas.getContext("2d");

Das <canvas>-Element selbst hilft dir noch nicht weiter. Um zeichnen zu können, brauchst du den Grafikkontext. Den bekommst du durch die Methode getContext mit dem Parameter "2d".
 
Es gibt außer "2d" nur einen weiteren standardisierten Wert für diesen Parameter: "webgl". Der WebGL- Kontext bringt 3D-Grafik mit Hardwarebeschleunigung
in den Browser – 3D-Spiele in JavaScript, selbst das geht. 3D-Grafik geht aber ein wenig über den Umfang dieses Buches hinaus.

￼

context.lineStyle = "#000000"; 
context.lineWidth = 1; 
context.fillStyle = "#FFD700"; 
context.fillRect(0, 0, 30, 60); 
context.strokeRect(0, 0, 30, 60);

Transformationen – die Leinwand drehen und strecken

Der Rotationswinkel wird nicht wie bei CSS in Grad angegeben, sondern im Bogenmaß. Das ist das, bei dem alles in Vielfachen von Pi angegeben wird. Eine ganze Drehung sind 2 Pi, eine halbe Drehung Pi, 90° im Uhrzeigersinn 1/2 Pi, 90° gegen den Uhrzeigersinn 3/2 Pi. Und weil du Pi nicht jedes Mal selbst hinschreiben möchtest, gibt es in JavaScript dafür die Konstante Math.PI.
Diese drei Operationen verrücken das Koordinaten- system, drehen es oder stauchen bzw. strecken es. Ja, das Koordinatensystem, nicht die Figuren!

￼


SIEBZEHN 
AJAX (Asynchronous JavaScript and XML) Asynchron, weil die Webseite weiter benutzt wer- den kann, während im Hintergrund Daten geladen werden. JavaScript, weil ... ich denke, der Teil ist klar. Und XML, weil das zu Anfang das bevorzugte Datenformat war.
XML ist eine Markup-Sprache, sehr ähnlich wie HTML. In XML gibt es keine vorgegebe- ne Menge an Tags, man kann vollkommen beliebige Tag-Namen benutzen. Es ist ein verbreitetes Format für strukturierte Daten, weil es sowohl für Menschen als auch für Computer gut lesbar ist. das x in Ajax wird allgemein bei allen asynchronen Serverzugriffen benutzt, auch wenn kein XML vorkommt. Welche Art von Daten der Server liefert, ist vollkommen beliebig. Das häu- figste Format neben XML ist JSON, da es sich sehr einfach wieder in ein JavaScript-Objekt umwandeln lässt. Arbeiten mit XML ist etwas umständlicher

Mit AJAX wird das traditionelle Request-Response-Modell aufgebrochen, zumindest aus Sicht des Benutzers. Endlich kann jeder mit dem Server reden, ohne die ganze Seite abschicken zu müssen. Möglich macht’s der XMLHttpRequest
 
1. ein Request-Objekt erzeugen
var ajaxRequest = new XMLHttpRequest();

2. Eventlistener registrieren
ajaxRequest.addEventListener("load", ajaxGeladen);
ajaxRequest.addEventListener("error", ajaxFehler);
Wie es schon immer ging mit den Eventlistenern: zuerst der Name des Events, dann die Methode. load wird aufgerufen, wenn der Request erfolgreich war, ...
   ￼

3. mit einem Methodenaufruf den Request abschicken,
mit zwei Methodenaufrufen diesmal
Die open-Methode legt fest, was per Ajax aufgerufen werden soll.
ajaxRequest.open("get", "/ajaxURL"); 
ajaxRequest.send();

Die URL, gegen die der Request ausgeführt werden soll. Sie kann zwar relativ oder absolut sein, aber muss erst mal immer zu dem Server gehen, von dem dein JavaScript geladen wurde. Das liegt an der Same Origin Policy, die ich dir gleich auch noch erkläre.

 function ajaxGeladen(event){
                  var ergebnis = JSON.parse(event.target.responseText);
}

Jetzt werden deine Eventhandler aufgerufen, hoffentlich der load-Handler, und du bekommst dein Ergebnis: Es steht in der responseText-Eigenschaft des Requests. Reinen Text kannst du sofort weiterverwenden, JSON musst du vorher noch selbst parsen.
aus JSON werden sofort JavaScript- Objekte mit Eigenschaften, das ist viel einfacher. Und deswegen ist JSON heute verbreiteter.

ACHTZEHN 
Responsive Design, übersetzt so etwas wie reagierendes oder reaktionsfähiges Design, ist ein Paradigma des Webdesigns, bei dem sich die Seite an die Größe der Anzeige anpasst. Man hat weiterhin nur eine HTML-Datei 
Also, ganz am Anfang, als das mobile Web noch neu war,Damals gab es die Markup-Sprache WML (Wireless Markup Language) und das dazugehörige Protokoll WAP (Wireless Application Protocol),

Media Queries sind kein Hexenwerk, es handelt sich um eine Sammlung spezieller Anweisungen, die CSS-Regeln auf bestimmten Geräten aktivieren oder deaktivieren

Du musst an dieser Stelle vier Begriffe auseinanderhalten. Media Type ist eines der Schlüsselwörter, die ein Ausgabegerät beschreiben, zum Beispiel screen. Media Queries sind die CSS3-Erweiterung zu Media Types: Eine Media Query kann nur aus einem Media Type bestehen, aber sie kann auch Media Features enthalten, die ich dir gleich zeigen werde. Eine Media-Regel (oder @media-Regel) ist ein CSS-Konstrukt, das „normale“ CSS-Regeln mit einem Media Type oder einer Media Query versieht, für die sie gelten sollen.

<link rel="stylesheet" media="print" href="druck.css"/>
Im media-Attribut gibst du, Wunder über Wunder, eine Media Query an, die eben auch nur aus einem Media Type bestehen kann. Dieser Stylesheet kommt nur zum Einsatz, wenn die Seite gedruckt wird. Ansonsten wird er nicht einmal geladen.

So wird eine Media Query im Stylesheet angegeben: über das Schlüsselwort @media, gefolgt von der Query. Die Media Query und ihr Block bilden die Media-Regel. Innerhalb des Blocks stehen wieder vollständige CSS-Regeln
@media print {
      img {
            display: none;  
}
@media screen {… }. 


Diese Regel kommt nur beim Print zum Zug. Die Eigenschaft display: none wird zu den oben definierten allgemeinen Eigenschaften für //<img> //hinzugefügt und überschreibt die display-Eigenschaft  

Bilder beim Drucken auszublenden, ist eine häufige Anwendung für print

die Reihenfolge ist entscheidend! DieRegeldisplay: noneist nicht spezifischer, weil sie in einem @media-Block steht, sie überschreibt display:block nur deshalb, weil sie im Stylesheet weiter unten steht.

￼
Du kannst mehrere Bedingungen mit and verknüpfen,
Ex @media screen and (max-width: 850px)

ex 
@media screen and (max-width: 850px){ 
#inhalt {
float: none;
width: 100%;}
(Die beiden <div>s sollen untereinanderstehen, also ist Schluss mit float. Und die ganze Anzeige füllen, sollen sie auch noch)

Ex of navigation with Media Query
 @media screen and (max-width: 688px){
            #navigation {
height: auto;*1 }
#navigation li{ float: none;*2
width: 100%;*3
border-width: 0;*4 }
}


Für die Druck-Styles ist es aber außerdem wichtig, zu überlegen, welche Elemente du weglassen kannst, denn gedruckt wird normalerweise für den Hauptinhalt

Füge im Stylesheet noch einen Druckbereich hinzu, der #navigation und #sidebar komplett verschwinden lässt. Erinnere dich dafür an die display-Eigenschaft.
@media print {
#navigation, #sidebar {
                   display: none;
             } }
Die beiden unerwünschten Bereiche werden komplett ausgeblendet. Erinnere dich, display: nonelässt ein Element komplett verschwin- den und reserviert auch keinen Platz dafür.
      
Responsive Bildern
So einfach ist es, eine Eigenschaft und fertig. Das Hintergrundbild wird auf die kleinstmögliche Größe skaliert, die das Element komplett abdeckt.
body {
background-image: url(hintergrund.png); background-size: cover;
}

Ein anderer Wert, background- size: contain,skaliertdasBild so, dass es in eine Richtung genau bis an die Ränder reicht und in die andere Richtung Platz bleibt.

Responsive Design, also hast du in deinem Stylesheet schon Media Queries für verschiedene Größen. Erzeuge für jede Größe, bei der sich das Seitenlayout ändert, ein passendes Bild. Wenn deine Media Queries zum Beispiel lauten @media screen and (max-device-width: 850px) und @media screen and (max-device-width: 688px), so wie auf der Sta- pelfix-Seite, dann brauchst du drei Bilder: eins in voller Größe, eins in der Größe, wie es für 850 Pixel Bildschirmbreite gebraucht wird, und eins für 688 Pixel Bildschirmbreite. Was dazwischenliegt, kann der Browser dann skalieren.
Wenn du Hintergrundbilder austauschst, solltest du deine Media Queries immer mit *-device-width schreiben, nicht mit *-width. Benutzt du zum Beispiel max-width und dein Leser vergrößert oder verkleinert sein Browserfenster, dann kann es sein, dass plötzlich Bilder nachgeladen werden müssen. Dass sich die Bildschirmbreite ändert, passiert dagegen eher selten.
Was mit den anderen Bildern?
Genius!
img {
width: inherit; max-width: 100%;
        }
Kein Bild darf größer werden als sein Elternelement. Durch die Eigenschaft max-width wird das Bild nur verkleinert, wenn nötig. Steht mehr Platz zur Verfügung, wird es nicht automatisch vergrößert. Der Browser sorgt dafür, dass das Bild proportional verkleinert wird,

Achtung
Damit dieser CSS-Trick funktioniert, dürfen die Attribute width und height des <img>-Tags nicht gesetzt sein.

Mit Javascript gehts anders.. Mit DOM-Methoden werden alle Bilder gefunden und ihr src-Attribut verändert, um das Bild in der richtigen Größe zu laden.Für die richtige Größe gibt es eine Handvoll von JavaScript-Eigenschaften, die du brauchst. Das sind zum einen window.innerWidth und window.innerHeight, die die Größe des Anzeigebereichs (in Pixeln) enthalten. Sie entsprechen *-width bzw. *-height in einer Media Query
screen.width und screen.height funktionieren nicht zuverlässig, wenn mehrere Bildschirme angeschlossen sind. Greif lieber auf die window-Eigenschaften zurück.

Das Offensichtlichste an jedem Tablet und Handy ist wohl, dass weder Maus noch Tastatur dran sind.Touchscreen. Dazu zunächst eine gute Nachricht: Du musst dafür kein spezielles JavaScript schreiben, wenn du nicht möchtest. Das Fingergetatsche wird auch in Mausevents übersetzt.
Aber vielleicht möchtest du ja, dass deine Website so funktioniert, wie eine echte App. 
(Pinch-to-Zoom), das geht mit Mausevents nicht. Wenn du das unterstützen möchtest, dann ist Touch angesagt.

￼
gibt es jetzt ein oder mehrere Touch-Objekte in der Eigenschaft touches des Events.

￼

￼

Die Methode, um deine aktuelle Position zu finden, hat einen wenig überraschenden Namen: getCurrentPosition. 

Telefonieren: Du kannst zwar aus Sicherheitsgründen keine Anrufe annehmen, aber einen Anruf auszulösen, ist so einfach, dass es nicht mal JavaScript braucht. Das tel-Protokoll macht's möglich: <a href="tel:0228-1">Ruf mich an!</a>.
NEUNZEHN 

Mach dir eine Homepage, die richtig cool aussieht. Schreib ein Memory-Spiel in JavaScript.
Ein Framework ist nicht nur in CSS, sondern in der Softwareentwick- lung allgemein ein wiederverwendbarer Rahmen für deine Arbeit.
Ein Framework stellt den großen Rahmen zur Verfügung, in den du deine Arbeit einbettest. Bei anderen Bibliotheken – ich zeige dir gleich einige in JavaScript – baust du den großen Rahmen, und du rufst die Bibliotheken auf, um bestimmte Aufgaben zu erledigen.
Ex http://www.yaml.de/docs/index.html
YAML steht für Yet Another Multicolumn Layout.

 JavaScript-Bibliotheken und neue APIs
Mein persönlicher Favorit unter diesen allgemeinen Bibliotheken ist jQuery, die eierlegende Wollmilchsau einer Bibliothek. Von DOM-Manipulation über Event Handling bis Ajax ist zu jedem Thema was drin.

Wenn du eine vollkommen andere Art sehen möchtest, mit JavaScript zu arbeiten, dann gibt es auch da viele Ansätze. Gerade im Moment ist angular.js (http://angularjs.org/) ein solcher, der sehr beliebt ist.

Mit node.js (http://nodejs.org/) kannst du dein JavaScript-Wissen auch auf dem Server gebrauchen. 

Blog
Wordpress (http://wordpress.org/, PHP) ist eines der bekanntesten, aber auch Drupal (https://drupal.org/, PHP) 
 Forum! phpBB (https://www.phpbb.com/, PHP) ist sehr verbreitet, MyBB (http://www.mybb.com/, PHP)
Ein Wiki löst das sofort. MediaWiki (http://www.mediawiki.org/, PHP) ist hier weit vorne,

Detecting keystrokes >https://quirksmode.org/js/keys.html

Validierung für eine Zeichenkette / String.
Ex in formular
<input type="text" name="artikelnummer" pattern="STAKIS4711”>
Pattern is for instance. Has to begin with STA - next three letters are this this or KIS.. then 4 digits. All others will not be accepted
OR
<input type="text" name="artikelnummer" pattern="STA.......">
 etc
It can become this..
<input type="text" name="artikelnummer" pattern="STA(KIS|FAS|ROL|SON)\d{4}">

Ex in Javascript
Die Stringmethode test ist eine Funktion, die mit regulären Ausdrücken arbeitet. Sie prüft, ob der String oder ein Teil des Strings zur Regex passt, und gibt entsprechend true oder false zurück. This is an Objekt vom Typ RegExp.

"STAROL0190".test(/STA(KIS|FAS|ROL|SON)\d{4}/); // Ein regulärer Ausdruck wird in JavaScript zwischen Slashes / angegeben

Die Stringmethode test ist eine Funktion, die mit regulären Ausdrücken arbeitet. Sie prüft, ob der String oder ein Teil des Strings zur Regex passt, und gibt entsprechend true oder false zurück.

Die test-Methode verhält sich etwas anders als die Formularprüfung mit dem pattern-Attribut. Dort ist ein Wert nur gültig, wenn der gesamte String passt. test gibt aber auch dann true zurück, wenn ein Teilstring passt. Damit sich auch test so verhält wie pattern bei Formularen, musst du den regulären Ausdruck um zwei Zeichen erweitern: ^ passt auf den Anfang des Strings, $ auf das Ende. Insgesamt kannst du also /^STA(KIS|FAS|ROL|SON)\d{4}$/ schreiben, und schon prüft test, ob der ganze String passt.

Reguläre Ausdrücke in JavaScript können aber noch etwas, dass sie in der Formvalidierung nicht konnten: Du kannst hinter dem zweiten Slash noch ein oder mehrere Flags angeben, das sind Schalter, die das Verhalten des Ausdrucks beeinflussen. Mit Flags kann dein Ausdruck zum Beispiel so aussehen: /STA(KIS|FAS|ROL|SON)\d{4}/gi. Das sind auch die beiden wichtigs- ten Flags, die ich dir unbedingt zeigen wollte. i steht für case-insensitive, bedeutet also, dass Groß- und Kleinschreibung ignoriert wird. Ohne das i-Flag passt ein A im Ausdruck auch nur auf A im String, mit i passt es auf A und a. Das g bedeutet global und führt dazu, dass nicht nach dem ersten Treffer mit der Suche aufgehört wird, sondern alle passenden Teilstrings gefunden werden.

Reguläre Ausdrücke in JavaScript können aber noch etwas, dass sie in der Formvalidierung nicht konnten: Du kannst hinter dem zweiten Slash noch ein oder mehrere Flags angeben

var ausdruck = /STA(KIS|FAS|ROL|SON)\d{4}/g;
text.test(ausdruck);
text.test(ausdruck);

iMit search findest du nicht nur heraus, ob ein Teilstring zu deinem Ausdruck passt, sondern auch den Index, an dem er anfängt.
iiDie split-Methode macht aus einem String ein Array von Strings, indem sie an allen Stellen, die zum regulären Ausdruck passen, einen neuen String anfängt. Klingt komp- liziert, ist aber ganz einfach: "Dies ist ein Test".split(/\s/) ergibt das Array ["Dies", "ist", "ein", "Test"], weil der String an allen Whitespaces in Teilstrings zerlegt wird.

replace findet nicht nur alle Stellen, die zu deinem regulären Ausdruck passen, sondern ersetzt sie mit einem anderen String.

IDEA.
Japanese Kanji memory game mit small circles in browser not cards

More idea.. a series of games with Kanjis in the browser
