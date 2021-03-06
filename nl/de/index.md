---



copyright:
  years: 2018, 2018
lastupdated: "2018-06-18"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Einführung in Bare Metal Servers
{: #getting-started}

{{site.data.keyword.baremetal_long}} sind physische Server für einzelne Tenants, die Ihnen Leistung und Kontrolle mit maschinennahem Zugriff auf Hardwareressourcen bereitstellen. Sie teilen den Server nicht mit "Noisy Neighbors" - er gehört vollständig Ihnen!
{: shortdesc}

Die Schritte in Tabelle 1 helfen Ihnen bei der schnellen Bereitstellung und Konfiguration Ihrer {{site.data.keyword.baremetal_short}}. 
<table>
   <CAPTION>Tabelle 1. Schritte für den Schnelleinstieg</CAPTION>
   <THEAD>
   <TR>
   <th>Aufgabe</th>
   <th>Details</th>
   </TR>
   </THEAD>
   <TBODY>
   <tr>
   <td>1. Lesen Sie Inhalte, die Ihnen bei der Implementierung helfen. </td>
   <td>IBM Cloud und Bare-Metal-Server sind neu für Sie? Die folgenden Sites stellen nützliche Informationen zur Verfügung, die Ihnen bei der Planung Ihrer Umgebung helfen.
   <li><a href="https://ibm.com/cloud-computing/">Was ist IBM Cloud?</a></li>
   <li><a href="https://ibm.com/cloud/get-started">Einführung in IBM Cloud</a></li>
   <li><a href="https://www.ibm.com/cloud/bare-metal-servers">Bare Metal Servers</a></li>
   </td>
 <tr>
   <td>2. Melden Sie sich bei IBM Cloud an. </td>
   <td><a href="https://console.bluemix.net/docs/admin/adminpublic.html#signing-up-for-ibm-cloud">IBM Cloud-Anmeldung</a> enthält die Schritte, die Sie ausführen müssen, um Ihr IBM Cloud-Konto einzurichten. </td>
 <tr>
   <td>3. Bestimmen Sie Ihre Workloadspezifikationen. </td>
   <td>Bestimmen Sie vor der Bereitstellung Ihres Servers, wie der Server verwendet wird und welche Servergröße Sie benötigen, um erfolgreich zu sein. Planen Sie beispielsweise, den Server für Entwicklung und Tests oder für die Produktion zu verwenden? Testen Sie die Benutzererfahrung, die Verarbeitung langer Algorithmen, die Sicherung und Wiederherstellung von Daten oder die Erhöhung der Latenz (Geschwindigkeit)?</td>  
 <tr>
   <td>4. Legen Sie die Größe fest und ermitteln Sie die Kosten Ihres Servers. </td>
   <td>Das <a href="https://www.ibm.com/cloud-computing/bluemix/bare-metal-search">Bare-Metal-Suchtool</a> hilft Ihnen bei der Festlegung der Größe und der Berechnung der Kosten Ihres Servers. </td>
 <tr>
   <td>5. Melden Sie sich bei Ihrem IBM Cloud-Konto an. </td>
   <td>Auf das Bestellformular für Bare Metal Servers können Sie über den IBM Cloud-Katalog oder das Kundenportal für IBM Cloud-Infrastruktur zugreifen. Sie benötigen eine <a href="https://console.bluemix.net/docs/customer-portal/getting-started.html#getting-started">IBMid und ein Kennwort</a>, um auf den Katalog und das Kundenportal für Infrastruktur zuzugreifen.
   <li><a href="https://console.bluemix.net/catalog/">IBM Cloud-Katalog</a></li>
   <li><a href="https://control.softlayer.com">Kundenportal für IBM Cloud-Infrastruktur</a></li>  
   </td>   
<tr>   
   <td>6. Stellen Sie Ihren Server bereit. </td>
   <td>Bei der Bereitstellung Ihres Servers haben Sie drei Optionen: gängig, angepasst und von SAP zertifiziert. Gängige Server sind vorkonfigurierte Server, die den Anforderungen der meisten Kunden entsprechen und bereits 30 bis 40 Minuten nach der Bereitstellung für die Konfiguration verfügbar sein können.  
   
     
<br>Angepasste Server sind Server, die Sie erstellen, indem Sie bestimmte Optionen für Rechenleistung, Konnektivität, Speicher und Netz auswählen, die Ihre Anforderungen erfüllen. Beachten Sie, dass die Bereitstellung angepasster Server länger dauert, nämlich in der Regel 2 bis 4 Stunden, und dass die Betriebskosten für diese Server höher sind. Sie haben auch die Möglichkeit, <a href="bm_provision_ssd.html">einen mit Intel Optane kompatiblen Bare-Metal-Server</a> oder einen Server mit einer <a href="bare-metal-provision-SGX.html">Intel SGX-Architektur bereitzustellen</a>.  
     
<br>Von SAP zertifizierte Server wurden speziell für die Unterstützung von SAP HANA- und SAP NetWeaver-Umgebungen zertifiziert.
Verwenden Sie die Links, um Bereitstellungsinformationen für den jeweiligen Servertyp aufzurufen. Beachten Sie, dass Sie bei von SAP zertifizierten Servern auswählen müssen, ob Sie eine SAP HANA- oder SAP NetWeaver-Umgebung bereitstellen.   
  <li><a href="baremetal-provision-popular.html">Schnell bereitgestellte Bare-Metal-Server</a></li>
  <li><a href="baremetal-provision.html">Angepasste Bare-Metal-Server</a></li>
  <li><a href="bare-metal-sap-applications.html">Von SAP zertifizierte IBM Cloud-Infrastruktur</a></li>
  </td>
 <tr>
   <td>7. Konfigurieren Sie Ihren Bare-Metal-Server. </td>
   <td>Ihr Server ist jetzt für die Konfiguration bereit. Weitere Informationen finden Sie in den Themen unter *Konfiguration*. </td>
   </td>
   </tr>
   </TBODY>
   </table>
