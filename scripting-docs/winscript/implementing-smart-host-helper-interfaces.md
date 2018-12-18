---
title: Implementazione delle interfacce helper Smart Host | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Smart Host Helper Interfaces, implementing
ms.assetid: b9c44246-4d4d-469e-91be-00c8f5796fa5
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba571f6ad66855c44902e06467889e2cae5b4555
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="implementing-smart-host-helper-interfaces"></a>Implementazione delle interfacce helper Smart Host
L'[interfaccia IDebugDocumentHelper](../winscript/reference/idebugdocumenthelper-interface.md) semplifica notevolmente l'attività di creazione di uno smart host per il debug attivo, poiché offre le implementazioni per molte delle interfacce necessarie per l'hosting smart.  
  
 Per essere uno smart host che usa `IDebugDocumentHelper`, un'applicazione host deve eseguire solo tre operazioni:  
  
1.  Eseguire `CoCreate` sulla gestione del debug dei processi e usare l'[interfaccia IProcessDebugManager](../winscript/reference/iprocessdebugmanager-interface.md) per aggiungere l'applicazione all'elenco delle applicazioni di cui può essere eseguito il debug.  
  
2.  Creare un helper di documenti di debug per ogni oggetto di script tramite il metodo [IProcessDebugManager::CreateDebugDocumentHelper](../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md). Verificare che nome del documento, documento padre, testo e blocchi di script siano definiti.  
  
3.  Implementare l'[interfaccia IActiveScriptSiteDebug](../winscript/reference/iactivescriptsitedebug-interface.md) sull'oggetto che implementa l'interfaccia [IActiveScriptSite](../winscript/reference/iactivescriptsite.md), necessaria per lo script attivo. Il metodo non comune sull'interfaccia `IActiveScriptSiteDebug` delega semplicemente all'helper.  
  
 Facoltativamente, è possibile implementare l'host dell'[interfaccia IDebugDocumentHost](../winscript/reference/idebugdocumenthost-interface.md) se è necessario un controllo maggiore su colore sintassi, creazione di contesto per il documento e altre funzionalità estese.  
  
 Il principale limite dell'helper smart host è che può gestire solo documenti il cui contenuto viene modificato o ristretto dopo che sono stati aggiunti (benché sia possibile espandere i documenti). Per molti smart host, tuttavia, la relativa funzionalità offerta corrisponde esattamente a quanto necessario.  
  
 Nelle sezioni seguenti viene descritto più in dettaglio ogni singolo passaggio.  
  
## <a name="create-an-application-object"></a>Creare un oggetto applicazione  
 Prima di poter usare l'helper smart host, è necessario creare un oggetto [Interfaccia IDebugApplication](../winscript/reference/idebugapplication-interface.md) per rappresentare l'applicazione nel debugger.  
  
#### <a name="to-create-an-application-object"></a>Per creare un oggetto applicazione  
  
1.  Creare un'istanza di gestione del debug dei processi tramite `CoCreateInstance`.  
  
2.  Chiamare [IProcessDebugManager::CreateApplication](../winscript/reference/iprocessdebugmanager-createapplication.md).  
  
3.  Impostare il nome dell'applicazione tramite [IDebugApplication::SetName](../winscript/reference/idebugapplication-setname.md).  
  
4.  Aggiungere l'oggetto applicazione per l'elenco delle applicazioni di cui può essere eseguito il debug tramite [IProcessDebugManager::AddApplication](../winscript/reference/iprocessdebugmanager-addapplication.md).  
  
     Il codice riportato di seguito descrive il processo, ma non include il controllo degli errori o altre tecniche di programmazione affidabile.  
  
    ```  
    CoCreateInstance(CLSID_ProcessDebugManager, NULL,  
          CLSCTX_INPROC_SERVER | CLSCTX_INPROC_HANDLER  
          | CLSCTX_LOCAL_SERVER,  
    IID_IProcessDebugManager, (void **)&g_ppdm);  
    g_ppdm->CreateApplication(&g_pda);  
    g_pda->SetName(L"My cool application");  
    g_ppdm->AddApplication(g_pda, &g_dwAppCookie);  
    ```  
  
## <a name="using-idebugdocumenthelper"></a>Uso di IDebugDocumentHelper  
  
#### <a name="to-use-the-helper-minimal-sequence-of-steps"></a>Per usare l'helper (sequenza minima di passaggi)  
  
1.  Per ogni documento host, creare un supporto tramite [IProcessDebugManager::CreateDebugDocumentHelper](../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md).  
  
2.  Chiamare [IDebugDocumentHelper::Init](../winscript/reference/idebugdocumenthelper-init.md) sull'helper, specificando nome e attributi del documento e così via.  
  
3.  Chiamare [IDebugDocumentHelper::Attach](../winscript/reference/idebugdocumenthelper-attach.md) con l'helper padre per il documento (o NULL se il documento è la radice) per definire la posizione del documento nell'albero e renderlo visibile al debugger.  
  
4.  Chiamare [IDebugDocumentHelper::AddDBCSText](../winscript/reference/idebugdocumenthelper-adddbcstext.md) o [IDebugDocumentHelper::AddUnicodeText](../winscript/reference/idebugdocumenthelper-addunicodetext.md) per definire il testo del documento. È possibile chiamarli più volte se il documento è stato scaricato in modo incrementale, come nel caso di un browser.  
  
5.  Chiamare [IDebugDocumentHelper::DefineScriptBlock](../winscript/reference/idebugdocumenthelper-definescriptblock.md) per definire gli intervalli per ogni blocco di script e i motori di script associati.  
  
## <a name="implementing-iactivescriptsitedebug"></a>Implementazione di IActiveScriptSiteDebug  
 Per implementare [IActiveScriptSiteDebug::GetDocumentContextFromPosition](../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md), ottenere l'helper corrispondente al sito specificato e quindi l'offset del documento iniziale per il contesto di origine specificato, come indicato di seguito:  
  
```  
pddh->GetScriptBlockInfo(dwSourceContext, NULL, &ulStartPos, NULL);  
```  
  
 Usare quindi l'helper per creare un nuovo contesto di documento per l'offset del carattere specificato:  
  
```  
pddh->CreateDebugDocumentContext(ulStartPos + uCharacterOffset, cChars, &pddcNew);  
```  
  
 Per implementare [IActiveScriptSiteDebug::GetRootApplicationNode](../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md) è sufficiente chiamare `IDebugApplication::GetRootNode` (ereditata da [IRemoteDebugApplication::GetRootNode](../winscript/reference/iremotedebugapplication-getrootnode.md)).  
  
 Per implementare [IDebugDocumentHelper::GetDebugApplicationNode](../winscript/reference/idebugdocumenthelper-getdebugapplicationnode.md) restituire semplicemente l'elemento `IDebugApplication` creato inizialmente tramite la gestione del debug dei processi.  
  
## <a name="the-optional-idebugdocumenthost-interface"></a>Interfaccia IDebugDocumentHost facoltativa  
 L'host può offrire un'implementazione dell'[interfaccia IDebugDocumentHost](../winscript/reference/idebugdocumenthost-interface.md) usando [IDebugDocumentHelper::SetDebugDocumentHost](../winscript/reference/idebugdocumenthelper-setdebugdocumenthost.md) per assegnarle un controllo maggiore sull'helper. Ecco alcune delle operazioni che l'interfaccia dell'host consente di eseguire:  
  
-   Aggiungere testo tramite [IDebugDocumentHelper::AddDeferredText](../winscript/reference/idebugdocumenthelper-adddeferredtext.md) in modo che l'host non debba specificare immediatamente i caratteri effettivi. Se i caratteri sono veramente necessari, l'helper chiamerà [IDebugDocumentHost::GetDeferredText](../winscript/reference/idebugdocumenthost-getdeferredtext.md) nell'host.  
  
-   Eseguire l'override dei colori della sintassi predefiniti specificati dall'helper. L'helper chiama [IDebugDocumentHost::GetScriptTextAttributes](../winscript/reference/idebugdocumenthost-getscripttextattributes.md) per determinare la colorazione di un intervallo di caratteri, ritornando alla sua implementazione predefinita se l'host restituisce `E_NOTIMPL`.  
  
-   Offrire un controllo sconosciuto per contesti di documento creati dall'helper implementando [IDebugDocumentHost::OnCreateDocumentContext](../winscript/reference/idebugdocumenthost-oncreatedocumentcontext.md). In questo modo l'host ignora la funzionalità dell'implementazione del contesto di documento predefinito.  
  
-   Specificare un nome percorso nel file system per il documento. Alcune interfacce di debug utente usano questa funzione per consentire all'utente di modificare e salvare le modifiche apportate al documento. [IDebugDocumentHost::NotifyChanged](../winscript/reference/idebugdocumenthost-notifychanged.md) viene chiamato per inviare una notifica all'host dopo che il documento è stato salvato.  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica del debug di script ActiveX](../winscript/active-script-debugging-overview.md)