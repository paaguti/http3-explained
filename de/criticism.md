#Kritik

## UDP wird nie funktionieren

Viele Unternehmen, Betreiber und Organisationen blockieren oder begrenzen den UDP
Verkehr außerhalb des Ports 53 (der für DNS verwendet wird), da dieser in letzter Zeit meist
für Angriffe missbraucht wurde. Insbesondere einige der bestehenden UDP-Protokolle und
populären Server-Implementierungen für diese sind für Amplifikationsangriffe anfällig, 
mit denen ein Angreifer eine hohe Menge an Verkehr erzeugen kann, um
unschuldige Opfer anzugreifen.

QUIC verfügt über eine eingebaute Abschwächung gegen Amplifikationsangriffe. Es schreibt vor, dass das
erste Paket mindestens 1200 Bytes groß sein muss. Zusätzlich gibt es eine Einschränkung im Protokoll
die bewirkt, dass ein Server nicht mehr als die dreifache Größe der
Anfrage als Antwort senden darf, ohne ein Paket vom Client als Antwort zu erhalten.

## UDP ist langsam im Kernel

Dies scheint derzeit die Wahrheit zu sein. Wir können natürlich nicht vorhersagen, wie 
sich das entwickeln wird und wie viel davon einfach das Ergebnis davon ist, dass 
Übertragungsleistung bei UDP seit vielen Jahren nicht mehr im Fokus der Entwickler stand.

Für die meisten Clients ist diese "Lahmheit" wahrscheinlich nicht einmal spürbar.

## QUIC braucht zu viel CPU

Ähnlich wie bei der Bermerkung "UDP ist langsam", liegt dies teilweise daran, 
dass die Nutzung von TCP und TLS eine längere Zeit hatte, um zu reifen, sich zu verbessern und
Hardware-Unterstützung zu bekommen.

Es gibt Gründe zu erwarten, dass sich dies im Laufe der Zeit verbessern wird, und [wir sehen bereits
einige Verbesserungen in diesem Bereich](https://www.fastly.com/blog/measuring-quic-vs-tcp-computational-efficiency).
Die Frage ist, wie sehr diese zusätzliche CPU-Belastung den Bereitstellern schaden wird.

## Das ist nur Google

Nein, ist es nicht. Google brachte die ursprüngliche Spezifikation in die IETF ein, nachdem es bewiesen hatte,
dass der Einsatz dieser Art von Protokoll über UDP tatsächlich funktioniert und gut performt.

Seitdem haben Personen aus einer großen Anzahl von Unternehmen und Organisationen
in der Hersteller-neutralen Organisation IETF daran gearbeitet, ein Standard
Transportprotokoll daraus zu machen. An dieser Arbeit haben sich natürlich auch Mitarbeiter von Google
beteiligt, aber auch Mitarbeiter einer großen Anzahl anderer Unternehmen, die daran interessiert sind, 
den Zustand der Transportprotokolle im Internet zu fördern, darunter Mozilla, Fastly, Cloudflare, Akamai, Microsoft,
Facebook und Apple.

## Das ist eine zu geringe Verbesserung

Das ist nicht wirklich eine Kritik, sondern eine Meinung. Vielleicht ist es das, und vielleicht ist es
eine zu geringe Verbesserung so kurz nach der Auslieferung von HTTP/2.

HTTP/3 wird wahrscheinlich in verlustbehafteten Netzen viel besser funktionieren. Es
bietet schnellere Handshakes, sodass es die gefühlte und tatsächliche Latenzzeit verbessert.
Aber ist das genug an Vorteilen, um Leute zu motivieren, HTTP/3 Unterstützung auf ihren Servern 
und für ihre Dienste einzusetzen? Die Zeit und zukünftige Leistungsmessungen werden es sicherlich zeigen!
