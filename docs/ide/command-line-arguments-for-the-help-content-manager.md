---
title: Argomenti della riga di comando per Gestione contenuto della Guida | Microsoft Docs
ms.custom: 
ms.date: 11/01/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-help-viewer
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3aa9890a-1147-42ba-adea-17935d184038
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b7eaa5214a87c2931a260f1c5adb6bac56dfa288
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="command-line-arguments-for-the-help-content-manager"></a>Argomenti della riga di comando per la Gestione contenuto della Guida
È possibile specificare come distribuire e gestire il contenuto della Guida locale usando gli argomenti della riga di comando per Gestione contenuto della Guida (HlpCtntMgr.exe). È necessario eseguire gli script per questo strumento da riga di comando con le autorizzazioni di amministratore e non è possibile eseguire questi script come servizio. Usando questo strumento è possibile eseguire le seguenti attività:  
  
-   Aggiungere o aggiornare il contenuto della Guida locale da un disco o dal cloud.  
  
-   Rimuovere il contenuto della Guida locale.  
  
-   Spostare l'archivio del contenuto della Guida locale.  
  
-   Aggiungere, aggiornare, rimuovere o spostare automaticamente il contenuto della Guida locale.  
  
Sintassi:  
  
```  
HlpCtntmgr.exe /operation Value /catalogname CatalogName /locale Locale /sourceuri InstallationPoint  
```  
  
Ad esempio:  
  
```  
hlpctntmgr.exe /operation install /catalogname VisualStudio15 /locale en-us /sourceuri d:\productDocumentation\HelpContentSetup.msha  
```  
  
## <a name="switches-and-arguments"></a>Opzioni e argomenti  
La tabella seguente definisce le opzioni e gli argomenti che è possibile usare per lo strumento da riga di comando per Gestione contenuto della Guida:  
  
|Opzione|Obbligatorio?|Argomenti|  
|------------|---------------|---------------|  
|/operation|Yes|-   **Install**: aggiunge i libri dell'origine dell'installazione specificata all'archivio del contenuto locale.<br />     Questa opzione richiede l'argomento /booklist, l'argomento /sourceURI o entrambi. Se non si specifica l'argomento /sourceURI, come origine dell'installazione viene usato l'URI predefinito di Visual Studio. Se non si specifica l'argomento /booklist, vengono installati tutti i libri in /sourceUri.<br />-   **Uninstall**: rimuove dall'archivio del contenuto locale i libri specificati.<br />     Questa opzione richiede l'argomento /booklist o l'argomento /sourceURI.  Se si specifica l'argomento /sourceURI, vengono rimossi tutti i libri e l'argomento /booklist viene ignorato.<br />-   **Move**: sposta l'archivio locale nel percorso specificato. Il percorso dell'archivio locale predefinito viene impostato come directory in %ProgramData%<br />     Questa opzione richiede gli argomenti /locationPath e /catalogName. Nel registro eventi vengono registrati messaggi di errore se si specifica un percorso non valido o se lo spazio libero sull'unità non è sufficiente per il contenuto.<br />-   **Refresh**: aggiorna gli argomenti modificati dopo l'installazione o aggiornati più di recente.<br />     Questa opzione richiede l'argomento /sourceURI.|  
|/catalogName|Yes|Specifica il nome del catalogo del contenuto.|  
|/locale|No|Specifica le impostazioni locali del prodotto usate per visualizzare e gestire il contenuto per l'istanza corrente del visualizzatore della Guida. Ad esempio, è possibile specificare `EN-US` per Inglese (Stati Uniti).<br /><br /> Se non si specificano le impostazioni locali, vengono usate quelle del sistema operativo. Se tali impostazioni locali non possono essere determinate, viene usato `EN-US`.<br /><br /> Se si specificano impostazioni locali non valide, nel log eventi viene registrato un messaggio di errore.|  
|/e|No|Eleva Gestione contenuto della Guida ai privilegi amministrativi se l'utente corrente dispone di credenziali amministrative.|  
|/sourceURI|No|Specifica l'URL da cui viene installato il contenuto l'installazione (API del servizio) o il percorso del file di installazione del contenuto (msha). L'URL può fare riferimento al gruppo di prodotti (nodo di primo livello) o ai libri del prodotto (nodo di livello foglia) in un endpoint di stile di Visual Studio 2010. Non è necessario includere una barra (/) alla fine dell'URL. Se si include una barra finale, verrà gestita in modo appropriato.<br /><br /> Nel log eventi viene registrato un messaggio di errore se il file specificato non viene trovato, non è valido o non è accessibile oppure se una connessione a Internet non è disponibile o viene interrotta durante la gestione del contenuto.|  
|/vendor|No|Specifica il fornitore del contenuto del prodotto che verrà rimosso (ad esempio, `Microsoft`). L'argomento predefinito per questa opzione è Microsoft.|  
|/productName|No|Specifica il nome del prodotto per i libri che verranno rimossi. Il nome del prodotto viene identificato nel file helpcontentsetup.msha o books.html fornito con il contenuto. È possibile rimuovere libri da un solo prodotto alla volta. Per rimuovere documenti da più libri, è necessario eseguire più installazioni.|  
|/booklist|No|Specifica i nomi dei libri da gestire, separati da spazi. I valori devono corrispondere ai nomi dei libri elencati nei supporti di installazione.<br /><br /> Se non si specifica questo argomento, vengono installati tutti i libri consigliati per il prodotto specificato in /sourceURI.<br /><br /> Se il nome di un libro contiene uno o più spazi, racchiuderlo tra virgolette doppie (") in modo che l'elenco venga delimitato in modo corretto.<br /><br /> Vengono registrati messaggi di errore se si specifica un'opzione /sourceURI non valida o non raggiungibile.|  
|/skuId|No|Specifica il codice di riferimento del prodotto (SKU) dall'origine dell'installazione e filtra i libri identificati dall'opzione /SourceURI.|  
|/membership|No|-   **Minimum**: installa un set minimo del contenuto della Guida in base allo SKU specificato usando l'opzione /skuId. Il mapping tra lo SKU e il set del contenuto viene esposto nell'API del servizio.<br />-   **Recommended**: installa un set di libri consigliati per lo SKU specificato usando l'argomento /skuId. L'origine dell'installazione è l'API del servizio o il file MSHA.<br />-   **Full**: installa l'intero set di libri per lo SKU specificato usando l'argomento /skuId. L'origine dell'installazione è l'API del servizio o il file MSHA.|  
|/locationpath|No|Specifica la cartella predefinita per il contenuto della Guida locale. Questa opzione deve essere usata solo per installare o rimuovere il contenuto. Se si specifica questa opzione, è necessario specificare anche l'opzione /silent.|  
|/silent|No|Installa o rimuove il contenuto della Guida senza chiedere conferma all'utente o visualizzare l'interfaccia utente, nemmeno l'icona nell'area di notifica dello stato. L'output viene registrato in un file nella directory %Temp%. **Importante:**  per installare automaticamente il contenuto, è necessario usare file con firma digitale con estensione cab, anziché file con estensione mshc.|  
|/launchingApp|No|Definisce il contesto dell'applicazione e del catalogo quando viene avviato il visualizzatore della Guida senza l'applicazione padre. Gli argomenti per questa opzione sono *CompanyName*, *ProductName* e *VersionNumber* (ad esempio `/launchingApp Microsoft,VisualStudio,15.0`).<br /><br /> Questa opzione è necessaria per l'installazione del contenuto con il parametro /silent.|  
|/wait *secondi*|No|Sospende le operazioni di installazione, disinstallazione e aggiornamento. Se un'operazione è già in corso per il catalogo, il processo attenderà il numero specificato di secondi per continuare. Usare 0 per restare in attesa in modo indefinito.|  
|/?|No|Elenca le opzioni e le relative descrizioni per lo strumento da riga di comando per Gestione contenuto della Guida.|  
  
### <a name="exit-codes"></a>Codici di uscita  
Quando si esegue lo strumento da riga di comando per Gestione contenuto della Guida in modalità automatica, restituisce i seguenti codici di uscita:  
  
```
Success = 0,  
  
FailureToElevate = 100  
InvalidCmdArgs = 101,  
FailOnFetchingOnlineContent = 110,  
FailOnFetchingContentFromDisk = 120,  
FailOnFetchingInstalledBooks = 130,  
NoBooksToUninstall = 200,  
NoBooksToInstall = 300,  
FailOnUninstall = 400,  
FailOnInstall = 500,  
FailOnMove = 600,  
FailOnUpdate = 700,  
FailOnRefresh = 800,  
Cancelled = 900,  
Others = 999,  
ContentManagementDisabled = 1200,  
OnlineHelpPreferenceDisabled = 1201  
UpdateAlreadyRunning = 1300 - (Signals that the update didn't run because another was in progress.)
```  
  
## <a name="see-also"></a>Vedere anche  
[Guida dell'amministratore di Help Viewer](../ide/help-viewer-administrator-guide.md)  
[Ovverride di Gestione contenuto della Guida](../ide/help-content-manager-overrides.md)  
[Microsoft Help Viewer](../ide/microsoft-help-viewer.md)