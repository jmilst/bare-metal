---

copyright:
  years: 2017, 2019
lastupdated: "2018-06-03"

keywords: mount iso bare metal

subcollection: bare-metal

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}


# Montaggio di una ISO su un server bare metal
{: #bm-mount-iso}

## Panoramica

Anche se la maggior parte dei clienti {{site.data.keyword.cloud}} utilizza uno dei sistemi operativi standard forniti con i nostri server, puoi montare delle ISO (immagini disco) personalizzate sui server. Hai tre opzioni per montare le ISO personalizzate.

Affinché i metodi funzionino, devi connetterti alla rete privata tramite il servizio VPN SL, ad esempio [SoftLayer SSL VPN Portal - AMS01](https://vpn.ams01.softlayer.com/prx/000/http/localhost/login) o tramite un altro server connesso alla rete.

**Nota:** le immagini del disco hardware Lenovo di dimensioni superiori a 50 MB devono essere montate utilizzando la scheda dell'interfaccia della console IMM > media.

## Opzione 1 (preferita): utilizzo di IPMI (ISO su una condivisione CIFS)
{: #bm-mount-iso-opt-1}

Se già hai l'infrastruttura distribuita su {{site.data.keyword.cloud_notm}}, puoi configurare un server esistente per offrire una condivisione CIFS alla rete interna. Puoi quindi montare su un server bare metal qualsiasi ISO presente.

Questo è il metodo preferito per l'installazione di un sistema operativo personalizzato su un server bare metal perché viene installato sulla rete locale, che è molto veloce e può mantenere una ISO montata anche se ti disconnetti o vieni disconnesso dall'interfaccia di gestione.

Attieniti alla seguente procedura per installare un sistema operativo personalizzato da una condivisione CIFS:

1. Assicurati di aver messo la ISO nella condivisione CIFS.
* Accedi alla console di gestione IPMI puntando il tuo browser web all'IP specificato in cloud.ibm.com e in devices -> il tuo server (device details) -> Remote Mgmt. Vengono qui specificati anche il nome utente e la password.
* Punta il mouse su **Virtual Media** e fai clic su **CD-ROM image**
* Compila i dettagli appropriati e fai clic su **Save and Mount**.
* Non tutti gli utenti dispongono dell'autorizzazione a modificare il BIOS del server. Se necessario, puoi aprire un ticket al supporto richiedendo:
  * I privilegi di amministratore di un utente root su IPMI (per poter modificare la modalità Virtual Media Attach)
  * Modificare la sequenza di avvio in ‘IPMI Virtual Disk’ come prima opzione di avvio.
* Dopo aver apportato queste modifiche, torna alla console di gestione IPMI e vai a configuration -> Remote session e modifica la modalità di collegamento (attach) in: **attach**. In alcune console IPMI meno recenti, puoi tralasciare questa opzione.
* Riavvia il server ed esegui l'avvio dal supporto virtuale.


## Opzione 2: utilizzo di IPMIView (ISO su una condivisione CIFS)
{: #bm-mount-iso-opt-2}

Prerequisiti:<br/>
* Disponi di una ISO avviabile
* Un server CIFS Windows o un'archiviazione NAS per memorizzare l'ISO avviabile
* L'ISO è caricata sul File Storage (NAS) associato al server.
* IPMIView è installato o c'è un accesso alla console KVM
* Il file ISO è scaricabile utilizzando wget
* Disponi dell'accesso SSH con i privilegi per accedere ai pacchetti e installarli e per creare un montaggio


### Linux e Windows
Attieniti alla seguente procedura per montare una ISO con IPMIView.
1. Tramite un ticket di supporto, richiedi che il tuo server esegua l'avvio dal suo CD-ROM virtuale come primo dispositivo. Ogni dispositivo deve eseguire l'avvio dal suo CD-ROM virtuale associato. Puoi annullare la modifica apportata a questa impostazione dopo che hai installato il sistema operativo.
* Stabilisci una connessione VPN a [VPN](http://www.softlayer.com/VPN-Access). Se stai utilizzando Microsoft Internet Explorer, assicurati di includere .softlayer.com e .cloud.ibm.com nel tuo elenco di siti attendibili e di mantenere aggiornato il tuo JAVA.
* Copia il supporto ISO su NAS o sul server CIFS Windows.
  * Stabilisci una connessione al tuo jumpbox Linux utilizzando SSH.
  * Monta la condivisione NAS sul tuo jumpbox Linux:

        mkdir /mnt/nasmount
        mount -t cifs //NAS_SERVER_NAME_ORIP/SLN#####-2 -o username=SLN#####-2,
        password=NAS_STORAGE_PW,rw,nounix,iocharset=utf8,file_mode=0644,dir_mode=0755 /mnt/nasmount
  * Chiave di parametro del comando mount:
        NAS_SERVER_NAME_ORIP = il nome o l'IP dell'archiviazione NAS.
        /SLN#####-2 = il nome utente e il nome cartella per stabilire una connessione alla tua archiviazione NAS.
        NAS_STORAGE_PW = la password alla tua archiviazione NAS.
        /mnt/nasmount = la cartella per montare l'archiviazione NAS.
  * Modifica la directory alla tua nuova cartella di montaggio NAS.
        cd /mnt/nasmount
  * Scarica il file iso utilizzando wget.
        wget http://www.linktoyouriso.com/isofilename.iso
  Vedrai una conferma della corretta esecuzione del download.
* Scarica IPMIView qui:
      https://www.servethehome.com/download-supermicro-ipmiview-latest-version/
* Stabilisci una connessione al server sull'IP di gestione.<br>
      1. Stabilisci una connessione a `winadmin`.
      2. Apri IPMIView e vai a **File > New > System**.
      3. Utilizza l'indirizzo IP IPMI dall'oggetto hardware per completare i campi del nome server e dell'indirizzo IP.<br>
      4. Fai doppio clic sul sistema con lo stesso indirizzo IP sul lato sinistro e immetti ADMIN per Login ID e la password IPMI dall'oggetto hardware.
      5. Dopo esserti connesso, hai molte schede disponibili nella finestra. Puoi utilizzare **Text Console** o **KVM Console** per connetterti al server.

* Apri la scheda Virtual Media
* Completa i dettagli della connessione dell'immagine CD-ROM.
  *
    * Share host = l'indirizzo IP dell'archiviazione NAS. Puoi trovare questo valore eseguendo un ping del tuo nome server di archiviazione NAS. Ad esempio, `ping nas501.service.softlayer.com`
    * Share Name = il nome utente dell'archiviazione NAS
    * Path to image = il nome del file ISO, nel seguente formato:
          \nomeutenteNAS\nomeiso.iso (ossia \SLN123456\centos6.iso)
    * User = il nome utente dell'archiviazione NAS
    * Password = la password per l'archiviazione NAS
* Riavvia il server
* Apri la vista KVM Console
* Attieniti ai prompt di sistema per avviare la ISO avviabile (BOOTABLE ISO)
* Installa il sistema operativo
* Smonta il supporto virtuale
* Riavvia il server

## Opzione 3: montaggio di una ISO dal tuo computer locale
{: #bm-mount-iso-opt-3}

<a name="option3"></a>

Puoi montare una ISO dal tuo computer locale utilizzando Java iKVM Viewer (console). Ciò ti consentirà di montare una ISO mentre sei connesso alla console. La velocità alla quale avanza l'installazione può variare a seconda della velocità di caricamento e della latenza della tua connessione a Internet e delle prestazioni di java e del tuo computer.

Se non disponi dell'autorizzazione a modificare la BIOS su un server, apri un ticket al supporto richiedendo le seguenti modifiche:
* I privilegi di amministratore di un utente Root su IPMI (per poter modificare la modalità Virtual Media Attach)
* Modificare la sequenza di avvio in ‘IPMI Virtual Disk’ come prima opzione di avvio. (Poiché ISO non è ancora montata, il supporto deve modificare solo la priorità del dispositivo di avvio, per ora).


1. Accedi alla console di gestione IPMI puntando il tuo browser web all'IP specificato in cloud.ibm.com.
* Fai clic su Devices > il tuo server (device details) > Remote Mgmt. Specifica il nome utente e la password.
* Fai clic su Configuration > Remote session e modifica la modalità di collegamento (attach) in **attach**. In alcune console IPMI meno recenti, questa opzione non è disponibile e puoi pertanto tralasciare questo passo.
* Fai clic su System > System information per ritornare alla pagina System Information. Vedrai un'icona di finestra della console.
* Fai clic sull'icona della console per aprire la console. Accetta tutte le avvertenze di sicurezza.
* Quando la console è connessa, vedrai il prompt di accesso.
* Fai clic su Virtual Media > Virtual Storage
* Vai alla scheda **CDROM&ISO** e seleziona il file ISO (ISO File) in **Logical Drive Type**
* Fai clic su **Open Image** e seleziona l'ISO sul tuo computer locale
* Fai clic su **Plug in** per inserire l'ISO nell'unità CD-ROM virtuale.
* Fai clic su **OK**.
* Riavvia il server e utilizza l'opzione **boot from the virtual cd-rom drive**. Potresti aver bisogno di utilizzare la tastiera virtuale in iKVM Viewer per selezionare un dispositivo di avvio.

## Risoluzione dei problemi
{: #bm-mount-iso-troubleshooting}

* Non tutti gli utenti hanno l'accesso predefinito per montare il supporto virtuale. Se si verifica un errore di autorizzazione, contatta il supporto per un aggiornamento alle autorizzazioni utente IPMI root.
* Se una ISO è già montata, verrà visualizzato un messaggio di errore con il testo **There is a disk mounted**. Devi smontare il disco esistente oppure sostituirlo con la nuova ISO. Due ISO non possono essere montate contemporaneamente.
* Potresti dover contattare il supporto per modificare l'ordine di avvio nel BIOS.
* Quando monti una ISO, utilizza la [VPN SSL](http://vpn.softlayer.com) anziché la VPN PPTP.  Una volta stabilita una connessione alla rete VPN, puoi anche accedere all'IPMI di sistema tramite l'indirizzo IPMI (https://private-ip-IPMI-management).
* Quando immetti il percorso di una ISO, usa la sintassi di denominazione UNC (Universal Naming Convention) per il percorso, ad esempio:
  `\\<NAS username>\<isoname>.iso`
