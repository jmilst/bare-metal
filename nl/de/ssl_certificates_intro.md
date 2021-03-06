---

copyright:
  years: 2017, 2019
lastupdated: "2018-04-02"

keywords: ssl certificate, sercure sockets layer

subcollection: bare-metal

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# SSL-Zertifikate
{: #bm-ssl-certificates}

Secure Sockets Layer (SSL) ist eine Technologie, mit der der Datenverkehr zwischen der Clientanwendung und der Serveranwendung, die am Datenaustausch teilnehmen, verschlüsselt wird. Diese Verschlüsselung wird über ein System mit öffentlichem Schlüssel und privatem Schlüssel unter Verwendung eines SSL-Zertifikats durchgeführt.
{:shortdesc}

Das SSL-Zertifikat enthält Folgendes: den öffentlichen Schlüssel des Servers; den Zeitraum, für den das Zertifikat gültig ist; einen Hostnamen, für den das Zertifikat gültig ist; eine Signatur von der Zertifizierungsstelle, die das Zertifikat ausgegeben hat. Mit diesen Informationen und einigen Protokollinformationen, die zu Beginn der Sitzung ausgetauscht werden, kann der Client einigermaßen sicher sein, dass der Server tatsächlich der Server ist, mit dem kommuniziert werden soll.

Weitere Informationen zu SSL-Zertifikaten finden Sie unter [Einführung in SSL-Zertifikate](/docs/infrastructure/ssl-certificates?topic=ssl-certificates-getting-started-tutorial).
