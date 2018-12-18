---
title: Le funzioni API plug-in controllo dell'origine | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control plug-ins, functions
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: beaab13c76b3d50f97662e66c1f72dc83161e96d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="source-control-plug-in-api-functions"></a>Funzioni API plug-in controllo di origine
L'API di plug-in controllo di origine fornisce le funzioni seguenti, che devono essere implementate per il controllo del codice sorgente plug-in base a questa API. Le firme di ogni funzione e la semantica associata con il flag di bit e altri parametri sono descritti in dettaglio in questo riferimento.  
  
## <a name="initialization-and-housekeeping-functions"></a>Inizializzazione e funzioni di manutenzione  
  
|Funzione|Descrizione|  
|--------------|-----------------|  
|[SccCloseProject](../extensibility/scccloseproject-function.md)|Chiude un progetto.|  
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|Richiede all'utente per le opzioni avanzate per il comando specificato.|  
|[SccGetVersion](../extensibility/sccgetversion-function.md)|Restituisce la versione del controllo origine plug-in.|  
|[SccInitialize](../extensibility/sccinitialize-function.md)|Inizializza il plug-in controllo del codice sorgente. Viene chiamato una volta per ogni istanza del plug-in.|  
|[SccOpenProject](../extensibility/sccopenproject-function.md)|Apre un progetto.|  
|[SccSetOption](../extensibility/sccsetoption-function.md)|Una funzione generica utilizzata per impostare un'ampia gamma di opzioni. Ogni opzione inizia con `SCC_OPT_xxx` e presenta un proprio set di valori definiti.|  
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|Chiamato una volta quando un plug-in controllo del codice sorgente deve essere scollegato.|  
  
## <a name="core-source-control-functions"></a>Funzioni di controllo di origine di base  
  
|Funzione|Descrizione|  
|--------------|-----------------|  
|[SccAdd](../extensibility/sccadd-function.md)|Aggiunge una matrice di file specificati da nomi di percorso completo per il controllo del codice sorgente.|  
|[SccAddFromScc](../extensibility/sccaddfromscc-function.md)|Consente di individuare i file già presenti nel sistema di controllo di origine e inserire i file del progetto corrente.|  
|[SccCheckin](../extensibility/scccheckin-function.md)|Verifica in una matrice di file.|  
|[SccCheckout](../extensibility/scccheckout-function.md)|Consente di estrarre una matrice di file.|  
|[SccDiff](../extensibility/sccdiff-function.md)|Vengono illustrate le differenze tra i file dell'utente locale specificato da un nome di percorso completo e la versione di controllo del codice sorgente.|  
|[SccGet](../extensibility/sccget-function.md)|Recupera una copia di sola lettura di un set di file.|  
|[SccGetEvents](../extensibility/sccgetevents-function.md)|Controlla lo stato del file che il chiamante ha richiesto sulla (tramite `SccQueryInfo`).|  
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|Fa sì che il plug-in per richiedere all'utente per un percorso di progetto che è significativo per il plug-in controllo del codice sorgente.|  
|[SccHistory](../extensibility/scchistory-function.md)|Mostra la cronologia per una matrice di nomi di file locale completo.|  
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|Esamina l'elenco di file per il relativo stato corrente. Inoltre, viene utilizzato il `pfnPopulate` funzione per segnalare al chiamante quando un file non corrispondono ai criteri per il `nCommand`.|  
|[SccProperties](../extensibility/sccproperties-function.md)|Vengono illustrate le proprietà di un file completo.|  
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|Esamina un elenco di file completi per il relativo stato corrente.|  
|[SccRemove](../extensibility/sccremove-function.md)|Rimuove il controllo del codice sorgente, quindi la matrice di file completi.|  
|[SccRename](../extensibility/sccrename-function.md)|Rinomina il file specificato in un nuovo nome nel sistema di controllo di origine.|  
|[SccRunScc](../extensibility/sccrunscc-function.md)|Accede l'intera gamma di funzionalità del sistema di origine.|  
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|Annulla l'estrazione di una matrice di file.|  
  
## <a name="functions-that-support-additional-capability-version-12-of-the-source-control-plug-in-api"></a>Funzioni che supportano funzionalità aggiuntive (versione 1.2 dell'API plug-in controllo origine)  
 Questo gruppo di funzioni definisce le funzionalità aggiuntive incluse nella versione 1.2 dell'API plug-in controllo di origine. Forniscono l'accesso a funzionalità di controllo di origine e le funzionalità più avanzate.  
  
|Funzione|Descrizione|  
|--------------|-----------------|  
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|Avvia un'operazione batch.|  
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|Crea un sottoprogetto con il nome specificato in un progetto padre esistente.|  
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|Mostra le differenze tra la directory locale dell'utente specificato da un nome di percorso completo e la posizione del controllo del database di origine.|  
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|Esamina un elenco di directory completo per il relativo stato corrente.|  
|[SccEndBatch](../extensibility/sccendbatch-function.md)|Termina un'operazione batch.|  
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|Restituisce padre del percorso del progetto specificato (il progetto deve essere presente).|  
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|Controlla se sono consentite le estrazioni multiple in un file.|  
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|Controlla se il plug-in Crea MSSCCPRJ. File SCC.|  
  
## <a name="functions-that-support-advanced-capability-version-13-of-the-source-control-plug-in-api"></a>Funzioni che supportano funzionalità avanzate (versione 1.3 dell'API plug-in controllo origine)  
 Questo gruppo di funzioni definisce le funzionalità aggiuntive incluse nella versione 1.3 di API plug-in controllo di origine. Forniscono l'accesso a funzionalità di controllo di origine e le funzionalità più avanzate.  
  
|Funzione|Descrizione|  
|--------------|-----------------|  
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|Aggiunge un elenco di file dal controllo del codice sorgente al progetto corrente.|  
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|Recupera un elenco di file dal controllo del codice sorgente senza un'interfaccia utente.|  
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|Recupera un elenco di file nel controllo del codice sorgente che sono diversi dai file locali.|  
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|Recupera i flag che specificano funzionalità estese supportate per il plug-in controllo del codice sorgente.|  
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|Recupera le opzioni specifiche dell'utente.|  
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|Esamina un elenco di directory e file in un progetto o i progetti inclusi nel controllo del codice sorgente. Ogni nome di directory e file trovato viene passato a una funzione di callback.|  
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|Esamina modifiche apportate a un elenco di file di nome. Ogni nome di file viene passato a una funzione di callback con il relativo stato di modifica.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: scc.h  
  
 (Fornito nel SDK di ambiente comuni include cartelle, per impostazione predefinita *[unità]*8.0\EnvSDK\common\inc \Program Files\VSIP; fornire anche nella cartella VSIP con l'esempio MSSCCI, *[unità]*\Programmi. Files\VSIP 8.0\MSSCCI).  
  
## <a name="see-also"></a>Vedere anche  
 [Plug-in del controllo codice sorgente](../extensibility/source-control-plug-ins.md)   
 [Creazione di un plug-in del controllo del codice sorgente](../extensibility/internals/creating-a-source-control-plug-in.md)