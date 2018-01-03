---
copyright:
  years: 1994, 2017
lastupdated: "2017-11-15"
---
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Riak-Netz konfigurieren

## Übersicht

Wenn Sie Riak auf einem für {{site.data.keyword.Bluemix}} optimierten Server installieren, wird Riak an die [private IP-Netzadresse ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://www.softlayer.com/about/datacenters/rack-architecture){: new_window} gebunden. Durch diese Bindung werden die Sicherheitsrisiken in Bezug auf eine offene und durch die Bereitstellung öffentlich zugängliche Riak-Instanz minimiert. Die IP-Adresse, die an Riak gebunden ist, kann jederzeit geändert werden. **Hinweis:** Riak sollte nicht ohne zusätzliche Sicherheitsmaßnahmen (z. B. Firewalls und iptables) an allgemein zugänglichen Schnittstellen bereitgestellt werden, um den externen Zugriff auf die Instanz zu begrenzen.
{:shortdesc}

Führen Sie die folgenden Schritte durch, um das Riak-Netz zum Binden an eine neue Schnittstelle zu konfigurieren.

## Riak an eine neue Schnittstelle binden

1. Wechseln Sie zum Abschnitt `riak_core` der Datei `/etc/riak/app.config` in der Installation.
2. Aktualisieren Sie das Attribut `http{}` im Abschnitt `riak_core` mit der neuen IP-Adresse, an die Riak gebunden ist.<br/>`{http, [ {"127.0.0.1", 8098 } ] },`
3. Suchen Sie nach der Datei `/etc/vm.args` in der Installation.
4. Bearbeiten Sie das Attribut `-name` in der Datei `/etc/vm.args` so, dass es die neue IP-Adresse widerspiegelt:<br/>`-name riak@127.0.0.1`
5. Starten Sie Riak erneut, um die Änderungen für die Bindung abzuschließen.

## Nächste Schritte

Die an der Bindung vorgenommenen Änderungen wirken sich auf alle vorherigen Bindungen zu Schnittstellen aus, die der Riak-Instanz zugeordnet sind. Nach dem Neustart wird die gebundene IP-Adresse aktualisiert und funktioniert ordnungsgemäß. Wenn Sie die Riak-Instanz erneut starten und dies nicht zu einer erfolgreichen Bindung führt, wenden Sie sich an den [Support](/general/support.html).
