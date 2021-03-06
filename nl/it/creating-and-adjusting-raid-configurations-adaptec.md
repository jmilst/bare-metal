---

copyright:
  years: 2017, 2019
lastupdated: "2018-07-10"

keywords: raid, adaptec, ipmi, raid bios, raid array, RAID configuration

subcollection: bare-metal

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Creazione e regolazione delle configurazioni RAID Adaptec
{: #bm-create-raid-config}

Il BIOS RAID Adaptec ti consente di configurare e gestire la tua impostazione RAID. Usa questo BIOS se stai utilizzando la nostra opzione di [Nessun sistema operativo](/docs/bare-metal?topic=bare-metal-the-no-os-option) e vuoi impostare una specifica configurazione di unità.

## Accesso al dispositivo IPMI per interagire con il BIOS RAID
{: #bm-access-ipmi}

Indipendentemente dal fatto che la tua macchina abbia un controller Adaptec o un controller LSI, hai bisogno di accedere al server che utilizza IPMI per interagire con il BIOS RAID. Per interagire con IPMI, devi prima stabilire una connessione alla VPN {{site.data.keyword.cloud}} Adaptec.
1. Accedi alla VPI tramite [SSL](/docs/infrastructure/iaas-vpn?topic=VPN-setup-ssl-vpn-connections#setup-ssl-vpn-connections) o PPTP.
* Accedi all'Elenco dispositivi in [{{site.data.keyword.slportal}} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://cloud.ibm.com/){: new_window}. Fai riferimento a [Accedi all'elenco dispositivi](/docs/infrastructure/vsi?topic=virtual-servers-managing-virtual-servers).
* Fai clic sul dispositivo al quale vuoi accedere.
* Seleziona la scheda Remote Mgmt per trovare i dettagli di accesso IPMI del tuo server.
* Inserisci l'IP del tuo dispositivo IPMI nel browser ed esegui l'accesso.
* Per iniziare a interagire con la console remota, fai clic su **Remote Control > Console Redirection**.

## Creazione di array RAID
{: #bm-create-raid-array}

Durante il processo di avvio, premi **Ctrl+A** per accedere al BIOS RAID.

Per iniziare a configurare il tuo RAID, apri Logical Device Configuration (prima opzione). Questa opzione esegue la scansione della topologia delle tue unità e visualizza un menu in cui puoi gestire gli array, creare gli array e completare altre attività di amministrazione dell'unità.

Il seguente esempio mostra come creare un array. Ti viene presentato un elenco di unità disponibili da utilizzare nella creazione del tuo array RAID.

1. Per selezionare le unità, premi la barra spaziatrice per popolare la casella *Selected Drives*.
* Dopo che hai selezionato tutte le unità che desideri utilizzare nel tuo array, premi INVIO per andare al passo di configurazione del RAID.
* Scegli il tipo di RAID che vuoi utilizzare. Se hai bisogno di assistenza a determinare quale configurazione di RAID risponde meglio alle tue esigenze, consulta le [Domande frequenti da Adaptec ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](http://www.adaptec.com/en-us/_common/compatibility/_education/raid_level_compar_wp.htm){: new_window}.
* Fornisci un'etichetta di array durante la configurazione. È buona prassi includere il tipo di RAID nell'etichetta (ad esempio: RAID10-A).
* Premi **Invio** per andare alle restanti impostazioni. Usa i valori predefiniti.

Dopo che hai completato la configurazione, seleziona Done; il RAID viene creato. Puoi vedere il nuovo array selezionando 'Manage Arrays' dal menu principale. Per uscire dal programma di utilità di configurazione, premi il tasto ESC finché non ti verrà richiesto di uscire dal BIOS Adaptec.

## Rimozione di array RAID esistenti
{: #bm-remove-raid-array}

Se devi rimuovere un array esistente, vai a **Manage Arrays**, seleziona l'array da rimuovere, premi **Delete** e conferma.

## Configurazioni di esempio
{: #bm-example-config}

1. Su un server con un totale di sei unità, puoi configurare due SSD in un RAID 0 per il tuo sistema operativo e quattro unità aggiuntive in un RAID 10 per i tuoi dati effettivi. Utilizza questa configurazione per ricaricare rapidamente il sistema operativo del server senza ripristinare i tuoi dati di servizio o sito se si trova sull'array secondario.

* Su un server cPanel, hai /var e /home su array RAID SSD separati. Poiché le directory sono le due con l'I/O più intensivo su un server cPanel, puoi potenzialmente ridurre il tempo di risposta del sito con le seguenti impostazioni:
  * RAID0 (2 unità SATA) - /
  * RAID0 (2 unità SSD) - /var
  * RAID0 (2 unità SSD) - /home
  * RAID10 (4 unità SATA) - /backup

* Utilizza un singolo array RAID per configurare più partizioni logiche. Ad esempio, utilizza due unità da 4 TB configurate in un RAID 1. Puoi partizionare il RAID perché risponda alle tue esigenze. Vedi il seguente esempio:
  * Partizione primaria di 100 GB per il tuo sistema operativo
  * Seconda partizione di 500 GB per i tuoi dati
  * Terza partizione del restante spazio per i backup
