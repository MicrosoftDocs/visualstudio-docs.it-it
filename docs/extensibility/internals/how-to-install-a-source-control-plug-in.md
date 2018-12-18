---
title: 'Procedura: installare un plug-in controllo del codice sorgente | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- installation [Visual Studio SDK], source control plug-ins
- source control plug-ins, installing
ms.assetid: 9e2e01d9-7beb-42b2-99b2-86995578afda
caps.latest.revision: "32"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: dab9270b55f5980d36256db78db89b5e4ac186f0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-install-a-source-control-plug-in"></a>Procedura: installare un plug-in controllo del codice sorgente
Creazione di plug-in un controllo origine prevede tre passaggi:  
  
1.  Creare una DLL con le funzioni definite nella sezione di riferimento dell'API di plug-in controllo di origine di questa documentazione.  
  
2.  Implementare le funzioni definite dall'API di plug-in controllo di origine. Quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] chiamate, rendere le interfacce e le finestre di dialogo disponibili dal plug-in.  
  
3.  Registrare la DLL immettendo le voci del Registro di sistema appropriati.  
  
## <a name="integration-with-visual-studio"></a>Integrazione con Visual Studio  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]supporta origine plug-in del controllo che è conforme all'API plug-in controllo di origine.  
  
### <a name="registering-the-source-control-plug-in"></a>Il controllo del codice sorgente plug-in registrazione  
 Prima di un ambiente di sviluppo integrato (IDE) in esecuzione possibile chiamare il controllo del codice sorgente, è necessario trovare l'origine del plug-in DLL che esporta le API di controllo.  
  
##### <a name="to-register-the-source-control-plug-in-dll"></a>Per registrare il controllo origine DLL plug-in  
  
1.  Aggiungere due voci nella chiave HKEY_LOCAL_MACHINE nella sottochiave SOFTWARE che specifica la sottochiave nome società aggiungendo la sottochiave nome prodotto. Il modello è HKEY_LOCAL_MACHINE\SOFTWARE\\*[nome società]*\\*[nome prodotto]*\\*[entry]* = valore. Le due voci vengono sempre chiamate SCCServerName e SCCServerPath. Ognuno è una stringa normale.  
  
     Ad esempio, se il nome della società è Microsoft e il controllo del codice sorgente denominato SourceSafe, tale percorso del Registro di sistema è HKEY_LOCAL_MACHINE\Software\Microsoft\SourceSafe. Questa sottochiave, la prima voce, SCCServerName, è una stringa leggibile dall'utente denominazione del prodotto. La seconda voce, SCCServerPath, è il percorso completo all'origine del controllo DLL plug-in cui deve connettersi l'IDE. Nelle sezioni che seguono vengono fornite le voci del Registro di sistema di esempio:  
  
    |Voce del Registro di sistema di esempio|Valore di esempio|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerName|Microsoft Visual SourceSafe|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerPath|c:\vss\win32\ssscc.dll|  
  
    > [!NOTE]
    >  Il SCCServerPath è il percorso completo per il plug-in SourceSafe. Il plug-in controllo del codice sorgente utilizzerà i nomi di società e prodotti diversi ma gli stessi percorsi di voce del Registro di sistema.  
  
2.  Le seguenti voci del Registro di sistema facoltativo utilizzabile per modificare il comportamento di controllo del codice sorgente plug-in. Queste voci andare nella sottochiave stessa come SccServerName e SccServerPath.  
  
    -   La voce HideInVisualStudioregistry può essere utilizzata se non si desidera l'origine-plug-in controllo da visualizzare nell'elenco di selezione plug-in di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Questa voce avrà effetto anche sul passaggio automatico per il plug-in controllo del codice sorgente. Un possibile utilizzo di questa voce è se si fornisce un pacchetto di controllo di origine che sostituisce il plug-in controllo del codice sorgente, ma si desidera rendono più semplice per l'utente eseguire la migrazione da tramite il controllo del codice sorgente del plug-in di package del controllo del codice sorgente. Quando viene installato il package del controllo del codice sorgente, imposta questa voce del Registro di sistema, che nasconde il plug-in.  
  
         HideInVisualStudio è un valore DWORD e viene impostato su 1 per nascondere il plug-in o 0 per mostrare il plug-in. Se non viene visualizzata la voce del Registro di sistema, il comportamento predefinito è mostrare il plug-in.  
  
    -   La voce del Registro di sistema DisableSccManager consente di disabilitare o nascondere il **avviare \<Server di controllo di origine >** opzione di menu che viene in genere visualizzata nel **File**  ->   **Controllo del codice sorgente** sottomenu. Selezionare questo menu opzione chiamate di [SccRunScc](../../extensibility/sccrunscc-function.md) (funzione). Il plug-in controllo del codice sorgente potrebbe non supportare un programma esterno e pertanto si consiglia di disabilitare o nascondere anche le **avviare** opzione di menu.  
  
         DisableSccManager è un valore DWORD è impostato su 0 per abilitare il **avviare \<Server di controllo di origine >** opzione di menu, impostare su 1 per disabilitare l'opzione di menu e impostato su 2 per nascondere l'opzione di menu. Se questa voce del Registro di sistema non è visualizzato, il comportamento predefinito è mostrare l'opzione di menu.  
  
    |Voce del Registro di sistema di esempio|Valore di esempio|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\HideInVisualStudio|1|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\DisableSccManager|1|  
  
3.  Aggiungere la sottochiave SourceCodeControlProvider, sotto la chiave HKEY_LOCAL_MACHINE nella sottochiave del SOFTWARE.  
  
     In questa sottochiave viene impostata voce del Registro di sistema ProviderRegKey a una stringa che rappresenta la sottochiave che è stata inserita nel Registro di sistema nel passaggio 1. Il modello è HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey = SOFTWARE\\*[nome società]*\\*[nome prodotto]*.  
  
     Di seguito è l'esempio di contenuto di questa sottochiave.  
  
    |Voce del Registro di sistema|Valore di esempio|  
    |--------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey|SOFTWARE\Microsoft\SourceSafe|  
  
    > [!NOTE]
    >  Controllo del codice sorgente plug-in userà la stessa sottochiave e i nomi delle voci, ma il valore sarà diverso.  
  
4.  Creare una sottochiave denominata InstalledSCCProviders nella sottochiave SourceCodeControlProvider e quindi inserire una voce in tale sottochiave.  
  
     Il nome di questa voce è il nome leggibile dall'utente del provider (uguale al valore specificato per la voce SCCServerName) e il valore è, in questo caso, la sottochiave creata nel passaggio 1. Il modello è HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\\*[nome]* = SOFTWARE\\*[nome società]* \\ *[nome prodotto]*.  
  
     Ad esempio:  
  
    |Voce del Registro di sistema di esempio|Valore di esempio|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\Microsoft Visual SourceSafe|SOFTWARE\Microsoft\SourceSafe|  
  
    > [!NOTE]
    >  Possono essere presenti più origine plug-in del controllo registrato in questo modo. Si tratta come [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] trova installati tutti i plug-in basato su API plug-in controllo di origine.  
  
## <a name="how-an-ide-locates-the-dll"></a>Modalità di individuazione della DLL un IDE  
 Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE presenta due metodi per individuare l'origine controllano DLL plug-in:  
  
-   Trovare il controllo del codice sorgente predefinito plug-in e connettersi ad esso invisibile all'utente.  
  
-   Trova origine registrata tutti i plug-in del controllo, da cui l'utente sceglie una.  
  
 Per individuare la DLL nel primo caso, l'IDE di ricerca nella sottochiave HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider per la voce ProviderRegKey. Il valore di questa voce punta a un'altra sottochiave. L'IDE cerca una voce denominata SccServerPath nella sottochiave secondo nella chiave HKEY_LOCAL_MACHINE. Il valore di questa voce punta IDE alla DLL.  
  
> [!NOTE]
>  L'IDE non caricare le DLL da percorsi relativi (ad esempio,.\NewProvider.DLL). Specificare un percorso completo della DLL (ad esempio, c:\Providers\NewProvider.DLL). Ciò aumenta la protezione dell'IDE, impedendo che il caricamento delle DLL plug-in utenti non autorizzati o rappresentato.  
  
 Per individuare la DLL il secondo modo, l'IDE cerca nella sottochiave HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider\InstalledSCCProviders per tutte le voci*.* Ogni voce ha un nome e un valore. L'IDE visualizza un elenco di questi nomi per l'utente*.* Quando l'utente sceglie un nome, l'IDE rileva che il valore per il nome selezionato che punta a una sottochiave. L'IDE verrà cercata una voce denominata SccServerPath nella sottochiave nella chiave HKEY_LOCAL_MACHINE. Il valore della voce punta IDE alla DLL corretta.  
  
 Un plug-in controllo del codice sorgente deve supportare entrambi i metodi di individuazione della DLL e, di conseguenza, impostare ProviderRegKey, sovrascrivendo qualsiasi impostazione precedente. Ancora più importante, è necessario aggiungere stesso all'elenco di InstalledSccProviders l'utente può avere una scelta di quale plug-in controllo del codice sorgente per utilizzare.  
  
> [!NOTE]
>  Poiché viene utilizzata la chiave HKEY_LOCAL_MACHINE, controllo del codice sorgente di un solo plug-in può essere registrato come controllo di origine predefinito plug-in di un computer specifico (tuttavia, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] consente agli utenti di determinare quale controllo codice sorgente che desiderano utilizzare effettivamente per una particolare soluzione). Durante il processo di installazione, verificare se un plug-in controllo del codice sorgente è già impostata; In questo caso, chiedere all'utente di impostare il controllo del codice sorgente nuovo plug-in viene installato come il valore predefinito o meno. Durante la disinstallazione, non rimuovere altre sottochiavi del Registro di sistema che sono comuni a tutti origine plug-in del controllo in HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider; rimuovere la specifica sottochiave SCC.  
  
## <a name="how-the-ide-detects-version-1213-support"></a>Come l'IDE rileva versione 1.2 o 1.3 supporto  
 Come does [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rilevare la presenza di una funzionalità di versione 1.2 e 1.3 plug-in supporta API plug-in controllo di origine? Per dichiarare le funzionalità avanzate, il plug-in controllo del codice sorgente deve implementare la funzione corrispondente.  
  
 Prima di tutto, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] controlla il valore restituito dalla chiamata di [SccGetVersion](../../extensibility/sccgetversion-function.md). Deve essere maggiore o uguale a 1.2.  
  
 Successivamente, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] determina se la nuova funzionalità particolare è supportata esaminando il `lpSccCaps` argomento per il [SccInitialize](../../extensibility/sccinitialize-function.md).  
  
 Se entrambe queste condizioni vengono soddisfatte, le nuove funzioni supportate nelle versioni 1.2 e 1.3 possono essere chiamate.  
  
## <a name="see-also"></a>Vedere anche  
 [Introduzione](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)