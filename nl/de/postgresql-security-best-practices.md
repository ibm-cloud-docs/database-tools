---
copyright:
  years: 1994, 2017
lastupdated: "2017-11-13"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# PostgreSQL - Best Practices für die Sicherheit

## Übersicht

Zahlreiche Benutzer von {{site.data.keyword.BluSoftlayer_full}} verwenden {{site.data.keyword.mysql}} als Datenbanklösung. Da Datenbanken verschiedene wichtige und teilweise auch sensible Informationen enthalten, sollten Sie {{site.data.keyword.mysql}}-Datenbanken sichern, um Ihre Daten zu schützen. Sicherheitsverfahren für {{site.data.keyword.mysql}} hängen von zahlreichen individuellen Bedürfnissen und Geschäftsanforderungen ab. Es gibt jedoch einige Best Practices, die als erste Schritte beachtet werden sollten. Stellen Sie daher sicher, dass Sie sich an die nachfolgenden Tipps halten, damit Sie Ihre {{site.data.keyword.mysql}}-Datenbank schon frühzeitig sichern können.
{:shortdesc}

* Legen Sie das Rootkennwort für {{site.data.keyword.mysql}} fest.
* Löschen Sie das Testkonto und die Datenbank, die während der Erstinstallation von {{site.data.keyword.mysql}} erstellt wurden.
* Stellen Sie sicher, dass jedes einzelne {{site.data.keyword.mysql}}-Kontokennwort festgelegt wurde.
* Erteilen Sie je nach Bedarf entsprechende Berechtigungen. Vermeiden Sie es, unnötig globale Berechtigungen zu gewähren.
* Verwenden Sie keine [Platzhalter ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://en.wikipedia.org/wiki/Wildcard_character){: new_window} als Wert für den Hostnamen, der Konten zugeordnet ist.
* Überprüfen Sie in regelmäßigen Abständen die {{site.data.keyword.mysql}}-Benutzer und -Datenbanken für ein Konto, um sicherzustellen, dass Berechtigungen weiterhin korrekt zugewiesen sind.

## Zusätzliche Ressourcen

Es gibt verschiedene zusätzliche Ressourcen, die nicht durch {{site.data.keyword.mysql}} verwaltet werden, die hilfreich sein könnten. Sie können nach diesen Ressourcen suchen, indem Sie in einer beliebigen Suchengine nach '{{site.data.keyword.mysql}} Security' suchen. Da Ressourcen anderer Anbieter nicht von den Machern von {{site.data.keyword.mysql}} gewartet werden, bedienen Sie sich dieser Verfahren mit Vorsicht. Wie bei allen Ressourcen sollten Sie vertrauenswürdige Sites verwenden und, wann immer möglich, offizielle Dokumentationen und Support-Sites nutzen.
