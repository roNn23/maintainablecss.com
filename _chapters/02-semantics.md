---
layout: chapter
title: Semantik
section: Hintergrund
permalink: /kapitel/semantik/
description: Etwas danach benennen, was es ist, anstatt wie es aussieht oder sich verhält sind die Grundzüge um gut strukturiertes und damit wartbares CSS zu schreiben.
---

**Zusammenfassung:** Benenne etwas auf der Basis was es *ist*, nicht wie es *aussieht* oder *sich verhält*.

## Die ausführliche Erklärung

Semantisches HTML dreht sich nicht nur um die Elemente die wir benutzen &mdash; es ist ziemlich offensichtlich, dass man ein `<a>` für einen Link, ein `<table>` for tabellarische Daten und ein `<p>` für Paragraphen verwendet.

Wesentlich wichtiger ist es, CSS-Klassenbezeichnungen (genauso wie IDs) in den richtigen Zusammenhang zu setzen um damit weitere Informationen über ein Element bereitzustellen. 

Es ist leider einfacher irgendeinen unbedachten Namen zu wählen, als einen korrekten bezeichnenden Namen. Aber die Benamung ist letztendlich sehr wichtig.

> &ldquo;There are only two hard things in Computer Science: cache invalidation and naming things.&rdquo;
<br>&mdash; <cite>Phil Karlton</cite>

Das liegt daran, dass Menschen gut in menschlicher Kommunikation sind und schlecht im Verstehen von abgekürzten, bedeutungsschwachen Abstraktionen.

## Gute und schlechte Beispiele von CSS-Klassennamen

Versuche den Unterschied zwischen nicht-semantischen und semantischen Klassennamen zu erkennen.

	<!-- Schlecht -->
	<div class="red pull-left"></div>
	<div class="grid row"></div>
	<div class="col-xs-4"></div>

Es ist nicht erkenntlich *was* das angegebene HTML repräsentiert. Du hast vielleicht eine *Idee* wie diese Elemente *aussehen könnten* (auf kleinen oder großen Bildschirmen), aber das ist auch schon alles.

	<!-- Gut -->
	<div class="header"></div>
	<div class="basket"></div>
	<div class="product"></div>
	<div class="searchResults"></div>

Bei dem Beispiel weiß man genau womit man es zu tun hat. Man erkennt den Zweck den das HTML repräsentiert. Dafür weiß man nicht wie die Elemente am Schluß aussehen&mdash;dafür ist das CSS verantwortlich. Semantische Klassennamen bedeuten etwas für HTML *und* CSS (und JS).

Also, **warum** sonst sollten wir semantische Klassennamen benutzen?

## Weil es einfacher zu verstehen ist

Ob du dir das HTML oder das CSS anschaust, du weißt welchen Teil du beeinflusst. Mit visuellen Klassennamen muss man einem Element mehrere verschiedene Klassen zuweisen, wodurch man nur ein vages Verständnis über den Zweck dieser Klassen bekommt. Das ist schwer zu warten.

## Weil wir Websites mit Hilfe von Responsive Webdesign entwickeln

Styles ändern sich oft durch verschiedene Viewport-Größen. Zum Beispiel möchte man Elemente auf großen Bildschirmen floaten, auf kleinen Bildschirmen dagegen nicht. Wenn man nun eine Klasse `clearfix` auf dem Element hat, diese aber auf kleinen Bildschirmen gar nicht zur Anwendung kommt, so hat man an der Stelle einen irreführenden Code.

Wenn du dagegen semantische Klassennamen benutzt, kannst du diese mittels unterschiedlichen Media-Queries einfacher pflegen.

## Weil semantische Klassennamen einfacher zu finden sind

Wenn ein Element Klassen trägt die das Aussehen beschreiben, wie beispielsweise `.red`, `clearfix` and `.pull-left`, dann werden diese Klassen überall im Code verwendet. Wenn man nun allerdings auf die Jagd nach einem bestimmten HTML-Element geht, wird einem der Klassenname nicht helfen, weil dieser ja sehr oft verwendet wurde.

Auf der anderen Seite, wird man das entsprechende HTML mit semantischen Klassen wesentlich schneller finden. Wenn du also typischerweise eine Suche basierend auf einem HTML-Tag beginnst (was durch Inspizieren in den Webdevelopertools oft vorkommt), wird du die entsprechenden CSS-Selektoren schneller auf Grundlage des semantischen Klassennamens finden.

## Weil du keine unerwartete Regression willst

Angenommen du bearbeitest diese nicht-semantischen Klassen, welche auf vielen Elementen hinterlegt sind. Fühlst du dich dabei gut? Oder ist es eher so, dass du ein unschönes Gefühl in der Magengegend hast, weil du nicht weißt ob die Änderung auch an einer anderen Stelle wirkt?

Durch semantische Klassennamen kannst du dir absolut sicher sein, nur an der Stelle eine Änderung einzubauen, an der du auch tatsächlich arbeitest. Dies wird durch die einmalige Verwendung dieser Klassen erreicht. Dadurch wird die Wartung an CSS wesentlich einfacher, sicherer und damit auch schneller.

## Weil du keine Angst haben solltest Code zu ändern

Wie im vorherigen Punkt bzgl. der Regression erwähnt, fühlst du dich oft nicht wohl beim Ändern von Code, da dadurch oft Probleme an anderen Stellen auftreten als an denen du aktuell arbeitest. Dadurch kann es passieren, dass du manchen Code am liebsten gar nicht anfassen magst. Deswegen wird oft redundanter Code erstellt, welche die Wartung noch schwieriger macht. Ein Teufelskreis.

## Weil es dir hilft automatische Tests durchzuführen

Automatische Funktionstests funktionieren auf der Grundlage, dass man bestimmte Elemente im Quellcode sucht, mit diesen interagiert (Text eintragen, Buttons drücken oder Links klicken) und anschließend das Ergebnis überprüft.

Hat man nun viele visuelle Klassennamen im HTML, ist es sehr schwierig das entsprechende Element zu treffen und mit diesem zu interagieren.

## Aus allgemeinen Gründen der Wartbarkeit

Wenn du etwas danach benennst, was es tatsächlich ist, brauchst du das HTML nie wieder anfassen. Zum Beispiel bleibt eine Überschrift immer eine Überschrift, egal wie sie *aussieht*.

Die Optik kann sich ändern, aber dann brauchst du nur das CSS anzupassen. Das ist auch bekannt als *Loose Coupling* und verbessert die Wartbarkeit deines Codes.

## Weil Hilfsklassen stören, wenn man debuggen möchte

Wenn du ein Element debuggen möchtest, stört es, wenn zu viele CSS-Selektoren auf dem Element wirken.

## Weil es vom Standard empfohlen wird

Die HTML5-Spezifikation erklärt zum Gebrauch der Klassenattribute (3.2.3.7):

> "[...] authors are encouraged to use values that describe the nature of the content, rather than values that describe the desired presentation of the content."

## Weil es die Performance steigert

Das ist nur ein *kleiner* Vorteil, aber wenn man nur eine Klasse pro Element vergibt, resultiert das in einem kleineren HTML. Mit visuellen Klassen wird das Markup mit unnötigen Bytes vergrößert.

## Weil es die Reuse-Regel beachtet

Wenn du keine semantischen Klassennamen benutzt, brichst du die Reuse-Regel. Dazu kommen wir gleich im nächsten Kapitel.

## Schlussgedanken zur Semantik

Semantische Klassennamen sind der Grundstein von *MaintainableCSS*. Ohne diesen macht alles andere wenig Sinn. Also denke immer daran die Element danach zu benennen, was sind sind, nicht wie sie aussehen. Alles andere kommt dann von ganz allein.
