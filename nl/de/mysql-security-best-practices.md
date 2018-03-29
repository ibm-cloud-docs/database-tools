---
copyright:
  years: 2014, 2018
lastupdated: "2018-01-26"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# MySQL - Best Practices für die Sicherheit

Zahlreiche Benutzer von {{site.data.keyword.BluSoftlayer_full}} verwenden {{site.data.keyword.mysql}} als Datenbanklösung. Da Datenbanken verschiedene wichtige und teilweise auch sensible Informationen enthalten, müssen Sie sicherstellen, dass die {{site.data.keyword.mysql}}-Datenbanken gesichert werden, um Ihre Daten zu schützen. Sicherheitsverfahren für {{site.data.keyword.mysql}} hängen von individuellen Bedürfnissen und Geschäftsanforderungen ab; es gibt jedoch einige Best Practices, die als erste Schritte beachtet werden sollten. Stellen Sie daher sicher, dass Sie sich an die nachfolgenden Tipps halten, damit Sie Ihre {{site.data.keyword.mysql}}-Datenbank schon frühzeitig sichern können.

* Legen Sie das Rootkennwort für {{site.data.keyword.mysql}} fest.
* Löschen Sie das Testkonto und die Datenbank, die während der Erstinstallation von {{site.data.keyword.mysql}} erstellt wurden.
* Stellen Sie sicher, dass jedes einzelne {{site.data.keyword.mysql}}-Kontokennwort festgelegt wurde.
* Erteilen Sie je nach Bedarf entsprechende Berechtigungen. Vermeiden Sie es, unnötig globale Berechtigungen zu gewähren.
* Verwenden Sie keine Platzhalter als Wert für den Hostnamen, der Konten zugeordnet ist.
* Überprüfen Sie in regelmäßigen Abständen die {{site.data.keyword.mysql}}-Benutzer und -Datenbanken für ein Konto, um sicherzustellen, dass Berechtigungen weiterhin korrekt zugewiesen sind.
* Verwenden Sie keine Kennwörter in der Befehlszeile mit dem Befehl `shell>mysql -u root - password=somepassword mysql`.

**Hinweis:** Verwenden Sie den folgenden Befehl, um zuzulassen, dass Benutzer mit Befehlszeilenzugriff das Kennwort mit dem Befehl `shell>ps` extrahieren können. Verwenden Sie den Befehl `shell>mysql -u root -p mysql`, um stattdessen zur Eingabe des Kennworts aufzufordern. So werden Kennwörter geschützt.

## Zusätzliche Ressourcen

Es gibt verschiedene Ressourcen mit näheren Einzelheiten darüber, wie Sie die {{site.data.keyword.mysql}}-Datenbank schützen können. Machen Sie sich zuerst mit den {{site.data.keyword.mysql}}-Sicherheitsrichtlinien vertraut, die auf der Version von {{site.data.keyword.mysql}} basieren, die sich auf Ihrer Einheit befindet:

* [{{site.data.keyword.mysql}} Version 5.7 ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://dev.mysql.com/doc/refman/5.7/en/security.html){: new_window}

Es gibt verschiedene zusätzliche Ressourcen, die nicht durch {{site.data.keyword.mysql}} verwaltet werden, die hilfreich sein könnten. Sie können nach diesen Ressourcen suchen, indem Sie in einer beliebigen Suchengine nach '{{site.data.keyword.mysql}} Security' suchen. Da Ressourcen anderer Anbieter nicht von den Machern von {{site.data.keyword.mysql}} gewartet werden, bedienen Sie sich dieser Verfahren mit Vorsicht. Wie bei allen Ressourcen sollten Sie vertrauenswürdige Sites verwenden und, wann immer möglich, offizielle Dokumentationen und Support-Sites nutzen.
