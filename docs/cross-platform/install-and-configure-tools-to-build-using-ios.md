---
title: Installare e configurare gli strumenti per la compilazione con iOS | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-mobile
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: d0c311c9-9eb9-42c5-ba07-25604362cd28
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: d015b927f8ba0fa62244a6cd09ff19efcb46451d
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="install-and-configure-tools-to-build-using-ios"></a>Install and Configure Tools to Build using iOS
È possibile usare Visual C++ per lo sviluppo di app per dispositivi mobili multipiattaforma per modificare, eseguire il debug e distribuire codice iOS al simulatore iOS o a un dispositivo iOS. Tuttavia, a causa di restrizioni di licenza, il codice deve essere compilato ed eseguito in modalità remota su Mac. Per compilare ed eseguire le app iOS usando Visual Studio, è necessario installare e configurare l'agente remoto [vcremote](http://go.microsoft.com/fwlink/p/?LinkId=534988), sul Mac. L'agente remoto gestisce le richieste di compilazione da parte di Visual Studio ed esegue l'app su un dispositivo iOS connesso a Mac o nel simulatore iOS su Mac.  
  
> [!NOTE]
>  Per informazioni sull'uso dei servizi di Mac ospitati nel cloud anziché su Mac, vedere [Build and Simulate iOS in the Cloud](https://taco.visualstudio.com/en-us/docs/build_ios_cloud/). Le istruzioni riguardano la compilazione con Visual Studio Tools per Apache Cordova. Per usare le istruzioni per compilare con Visual C++ per lo sviluppo di app per dispositivi mobili multipiattaforma, sostituire l'agente vcremote per vs-mda-remote.  
  
 Dopo aver installato gli strumenti per la compilazione con iOS, consultare questo argomento per informazioni su come configurare e aggiornare rapidamente l'agente remoto per lo sviluppo di iOS in Visual Studio e sul Mac.  
  
 [Prerequisiti](#Prerequisites)  
  
 [Installare l'agente remoto per iOS](#Install)  
  
 [Avviare l'agente remoto](#Start)  
  
 [Configurare l'agente remoto in Visual Studio](#ConfigureVS)  
  
 [Generate a new security PIN](#GeneratePIN)  
  
 [Generare un nuovo certificato del server](#GenerateCert)  
  
 [Configure the remote agent on the Mac](#ConfigureMac)  
  
##  <a name="Prerequisites"></a> Prerequisiti  
 Per installare e usare l'agente remoto per sviluppare il codice per iOS, è necessario prima di tutto avere questi prerequisiti:  
  
-   Un computer Mac OS X Mavericks o versione successiva  
  
-   Un [ID Apple](https://appleid.apple.com/)  
  
-   Un account attivo del [programma per sviluppatori iOS](https://developer.apple.com/programs/ios/) di Apple  
  
-   [Xcode 6](https://developer.apple.com/xcode/downloads/)  
  
     Xcode 6 può essere scaricato dall'App Store.  
  
-   Strumenti della riga di comando Xcode  
  
     Per installare gli strumenti della riga di comando Xcode aprire l'app Terminal nel Mac e immettere il comando seguente:  
  
     `xcode-select --install`  
  
-   Un'identità di firma iOS configurata in Xcode  
  
     Per informazioni dettagliate su come ottenere un'identità di firma iOS, vedere l'articolo relativo alla [gestione di identità e di certificati di firma](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingCertificates/MaintainingCertificates.html) in iOS Developer Library. Per visualizzare o impostare l'identità di firma in Xcode, aprire il menu **Xcode** e scegliere **Preferences**. Selezionare **Accounts** e scegliere il proprio ID Apple, quindi scegliere il pulsante **View Details** .  
  
-   Se si usa un dispositivo iOS per lo sviluppo, un profilo di provisioning configurato in Xcode per il dispositivo  
  
     Per informazioni dettagliate sulla creazione di profili di provisioning, vedere l'articolo relativo alla [creazione di profili di provisioning con Member Center](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingProfiles/MaintainingProfiles.html#//apple_ref/doc/uid/TP40012582-CH30-SW24) in iOS Developer Library.  
  
-   [Node.js](http://nodejs.org/)  
  
-   Una versione aggiornata di npm  
  
     La versione di npm fornita con Node.js potrebbe non essere abbastanza recente per installare vcremote. Per aggiornare npm, aprire l'app Terminal nel Mac e immettere il comando seguente:  
  
     `sudo npm install -g npm@latest`  
  
##  <a name="Install"></a> Installare l'agente remoto per iOS  
 Quando si installa Visual C++ per lo sviluppo di app per dispositivi mobili multipiattaforma, Visual Studio può comunicare con [vcremote](http://go.microsoft.com/fwlink/p/?LinkId=534988), un agente remoto in esecuzione nel proprio Mac per trasferire i file, compilare ed eseguire l'app iOS e inviare comandi di debug.  
  
 Prima di installare l'agente remoto, verificare di avere soddisfatto i [Prerequisiti](#Prerequisites) e installato [Visual C++ per lo sviluppo di app per dispositivi mobili multipiattaforma](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md#InstallTheTools).  
  
###  <a name="DownloadInstall"></a> Per scaricare e installare l'agente remoto  
  
-   Dall'app Terminal nel Mac, immettere:  
  
     `sudo npm install -g --unsafe-perm vcremote`  
  
     L'opzione di installazione globale (**-g**) è consigliata ma non richiesta.  
  
     Durante l'installazione, l'agente vcremote viene installato e nel Mac viene attivata la modalità sviluppatore. Vengono anche installati[Homebrew](http://brew.sh/) e due pacchetti npm, vcremote-lib e vcremote-utils.  
  
    > [!NOTE]
    >  Per installare Homebrew, è necessario l'accesso a sudo (amministratore). Se occorre installare vcremote senza sudo, è possibile installare Homebrew manualmente in un percorso usr/local e aggiungere la relativa cartella bin al percorso. Per altre informazioni, vedere la [documentazione di Homebrew](https://github.com/Homebrew/homebrew/wiki/Installation). Per abilitare manualmente la modalità sviluppatore, immettere questo comando nell'app Terminal: `DevToolsSecurity -enable`  
  
 Se il computer è stato aggiornato a una nuova versione di Visual Studio, è necessario aggiornare anche la versione corrente dell'agente remoto. Per aggiornare l'agente remoto, ripetere i passaggi per scaricare e installare l'agente remoto.  
  
##  <a name="Start"></a> Avviare l'agente remoto  
 Per compilare ed eseguire il codice iOS l'agente remoto deve essere in esecuzione per Visual Studio. Visual Studio deve essere associato all'agente remoto prima che possa comunicare. Per impostazione predefinita, l'agente remoto viene eseguito in modalità di connessione protetta, che richiede un PIN per l'associazione con Visual Studio.  
  
###  <a name="RemoteAgentStartServer"></a> Per avviare l'agente remoto  
  
-   Dall'app Terminal nel Mac, immettere:  
  
     `vcremote`  
  
     L'agente remoto verrà avviato con una directory di compilazione predefinita ~/vcremote. Per le opzioni di configurazione aggiuntive, vedere [Configure the remote agent on the Mac](#ConfigureMac).  
  
 La prima volta che si avvia l'agente, e ogni volta che si crea un nuovo certificato client, verranno fornite le informazioni necessarie per configurarlo in Visual Studio, inclusi il nome host, la porte e il PIN.  
  
 ![Uso di vcremote per la generazione di un PIN sicuro](../cross-platform/media/cppmdd_vcremote_generateclientcert.png "CPPMDD_vcremote_generateClientCert")  
  
 Per configurare l'agente remoto in Visual Studio usando il nome host, effettuare il ping del Mac da Windows con il nome host per verificare che sia raggiungibile. In caso contrario, potrebbe essere necessario usare l'indirizzo IP.  
  
 Il PIN generato può essere usato una sola volta ed è valido per un periodo limitato. Se non si associa Visual Studio all'agente remoto prima della scadenza dell'intervallo, sarà necessario generare un nuovo PIN. Per altre informazioni, vedere [Generate a new security PIN](#GeneratePIN).  
  
 È possibile usare l'agente remoto in modalità non protetta. In modalità non protetta, l'agente remoto può essere associato a Visual Studio senza un PIN.  
  
#### <a name="to-disable-secured-connection-mode"></a>Per disabilitare la modalità di connessione protetta  
  
-   Per disabilitare la modalità di connessione protetta in vcremote, immettere questo comando nell'app Terminal su Mac:  
  
     `vcremote --secure false`  
  
#### <a name="to-enable-secured-connection-mode"></a>Per abilitare la modalità di connessione protetta  
  
-   Per abilitare la modalità di connessione protetta, immettere questo comando:  
  
     `vcremote --secure true`  
  
 Dopo aver avviato l'agente remoto, è possibile usarlo da Visual Studio fino a quando non lo si arresta.  
  
#### <a name="to-stop-the-remote-agent"></a>Per arrestare l'agente remoto  
  
-   Nella finestra Terminal in cui è in esecuzione vcremote, immettere `Control+C`.  
  
##  <a name="ConfigureVS"></a> Configurare l'agente remoto in Visual Studio  
 Per connettere l'agente remoto da Visual Studio, è necessario specificare la configurazione remota nelle opzioni di Visual Studio.  
  
#### <a name="to-configure-the-remote-agent-from-visual-studio"></a>Per configurare l'agente remoto da Visual Studio  
  
1.  Se l'agente remoto non è già in esecuzione nel Mac, seguire la procedura indicata in [Avviare l'agente remoto](#Start). Per poter associare, connettere e compilare correttamente il progetto, l'agente vcremote deve essere in esecuzione sul Mac.  
  
2.  Nel Mac, ottenere il nome host o l'indirizzo IP del Mac.  
  
     È possibile ottenere l'indirizzo IP usando il comando **ifconfig** in una finestra Terminal. Usare l'indirizzo inet elencato all'interno dell'interfaccia di rete attiva.  
  
3.  Nella barra dei menu di Visual Studio scegliere **Strumenti**, **Opzioni**.  
  
4.  Nella finestra di dialogo **Opzioni** espandere **Multipiattaforma**, **C++**, **iOS**.  
  
5.  Nei campi **Nome host** , e **Porta** immettere i valori specificati dall'agente remoto quando è stato avviato. Il nome host può essere il nome DNS o l'indirizzo IP del Mac. Il numero di porta predefinito è 3030.  
  
    > [!NOTE]
    >  Se non è possibile effettuare il ping del Mac con il nome host, potrebbe essere necessario usare l'indirizzo IP.  
  
6.  Se si usa l'agente remoto nella modalità di connessione protetta predefinita, selezionare la casella di controllo **Proteggi** , quindi immettere il valore PIN specificato dall'agente in remoto nel campo **Pin** . Se si usa l'agente remoto in modalità di connessione non protetta, deselezionare la casella di controllo **Proteggi** e lasciare il campo **Pin** .  
  
7.  Scegliere **Associa** per abilitare l'associazione.  
  
     ![Configurazione della connessione vcremote per compilazioni iOS](../cross-platform/media/cppmdd_options_ios.PNG "CPPMDD_Options_iOS")  
  
     L'associazione viene mantenuta finché non si modifica il nome host o la porta. Se si modifica il nome host o la porta nella finestra di dialogo **Opzioni** , per annullare la modifica, scegliere il pulsante **Ripristina** per ripristinare l'associazione precedente.  
  
     Se l'associazione non riesce, verificare che l'agente remoto sia in esecuzione eseguendo i passaggi in [Start the remote agent](#Start). Se è trascorsa un'eccessiva quantità di tempo dalla generazione del PIN dell'agente remoto, seguire i passaggi in [Generate a new security PIN](#GeneratePIN) sul Mac e riprovare. Se si usa il nome host del Mac, provare a usare l'indirizzo IP del campo **Nome host** .  
  
8.  Aggiornare il nome della cartella nel campo **Radice remota** per specificare la cartella usata dall'agente remoto nella directory home (~) su Mac. Per impostazione predefinita, l'agente remoto usa /Users/`username`/vcremote come radice remota.  
  
9. Scegliere **OK** per salvare le impostazioni di connessione di associazione remota.  
  
 Visual Studio usa le stesse informazioni per connettersi all'agente remoto su Mac ad ogni uso. Non è necessario associare nuovamente Visual Studio all'agente remoto a meno che non si generi un nuovo certificato di sicurezza su Mac oppure il relativo nome host o l'indirizzo IP subiscano delle modifiche.  
  
##  <a name="GeneratePIN"></a> Generate a new security PIN  
 Quando si avvia l'agente remoto per la prima volta, il PIN generato è valido per un intervallo di tempo limitato (per impostazione predefinita, 10 minuti). Se non si associa Visual Studio all'agente remoto prima della scadenza dell'intervallo, sarà necessario generare un nuovo PIN.  
  
#### <a name="to-generate-a-new-pin"></a>Per generare un nuovo PIN  
  
1.  Arrestare l'agente oppure aprire una seconda finestra dell'app Terminal nel Mac e usarla per immettere il comando.  
  
2.  Immettere questo comando nell’app Terminal:  
  
     `vcremote generateClientCert`  
  
     L'agente remoto genera un nuovo PIN temporaneo. Per associare Visual Studio usando il nuovo PIN, ripetere i passaggi in [Configurare l'agente remoto in Visual Studio](#ConfigureVS).  
  
##  <a name="GenerateCert"></a> Generare un nuovo certificato del server  
 Per motivi di sicurezza, i certificati del server che associano Visual Studio all'agente remoto sono collegati all'indirizzo IP o al nome host del Mac. Se questi valori vengono modificati, sarà necessario generare un nuovo certificato del server e quindi riconfigurare Visual Studio con i nuovi valori.  
  
#### <a name="to-generate-a-new-server-certificate"></a>Per generare un nuovo certificato del server  
  
1.  Arrestare l'agente remoto vcremote.  
  
2.  Immettere questo comando nell’app Terminal:  
  
     `vcremote resetServerCert`  
  
3.  Quando viene richiesta la conferma, immettere `Y`.  
  
4.  Immettere questo comando nell’app Terminal:  
  
     `vcremote generateClientCert`  
  
     Viene generato un nuovo PIN temporaneo.  
  
5.  Per associare Visual Studio usando il nuovo PIN, ripetere i passaggi in [Configurare l'agente remoto in Visual Studio](#ConfigureVS).  
  
##  <a name="ConfigureMac"></a> Configure the remote agent on the Mac  
 È possibile configurare l'agente remoto usando diverse opzioni della riga di comando. Ad esempio, è possibile specificare la porta per l'ascolto delle richieste di compilazione e specificare il numero massimo di build da gestire nel file system. Per impostazione predefinita, il limite è di 10 build. L'agente remoto rimuove le build eccedenti il numero massimo all'arresto.  
  
#### <a name="to-configure-the-remote-agent"></a>Per configurare l'agente remoto  
  
-   Per vedere un elenco completo dei comandi dell'agente remoto, nell'app Terminal immettere:  
  
     `vcremote --help`  
  
-   Per disabilitare la modalità protetta e abilitare connessioni semplici basate su HTTP, immettere:  
  
     `vcremote --secure false`  
  
     Se si usa questa opzione, deselezionare la casella di controllo **Proteggi** e lasciare vuoto il campo **Pin** quando si configura l'agente in Visual Studio.  
  
-   Per specificare un percorso per i file dell'agente remoto, immettere:  
  
     `vcremote --serverDir directory_path`  
  
     dove *directory_path* è il percorso nel Mac in cui inserire file di log, build e certificati del server. Per impostazione predefinita, questo percorso è /Users/*nome utente*/vcremote. In questa posizione, le build vengono organizzate per numero.  
  
-   Per usare un processo in background per acquisire `stdout` e `stderr` in un file denominato server.log, immettere:  
  
     `vcremote > server.log 2>&1 &`  
  
     Il file server.log può essere d'aiuto nella risoluzione dei problemi di compilazione.  
  
-   Per eseguire l'agente usando un file di configurazione al posto dei parametri della riga di comando, immettere:  
  
     `vcremote --config config_file_path`  
  
     dove *config_file_path* è il percorso di un file di configurazione in formato JSON. Le opzioni di avvio e i relativi valori non devono includere trattini.  
  
## <a name="see-also"></a>Vedere anche  
 [Install Visual C++ for Cross-Platform Mobile Development](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)