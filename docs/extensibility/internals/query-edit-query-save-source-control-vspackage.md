---
title: Eseguire una query modifica Query Salva (origine controllo VSPackage) | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- QEQS events
- Query Edit Query Save events
- source control packages, Query Edit Query Save events
ms.assetid: c360d2ad-fe42-4d65-899d-d1588cc8a322
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e3428e51dda2f8cc8410b6ac67f5779f7c2300ed
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="query-edit-query-save-source-control-vspackage"></a>Query modifica Query Salva (origine controllo VSPackage)
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Editor è possono trasmettere gli eventi di Query modifica Query salvare (QEQS). [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Origine controllo Stub implementa il servizio QEQS, in modo che sia il destinatario di eventi QEQS. Questi eventi vengono quindi delegati per il controllo del codice sorgente attualmente attive VSPackage. Il controllo del codice sorgente active pacchetto VSPackage implementa il <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> e i relativi metodi. I metodi del `IVsQueryEditQuerySave2` interfaccia vengono in genere chiamato immediatamente prima che il documento viene modificato per la prima volta e immediatamente prima del salvataggio di un documento.  
  
## <a name="queryeditquerysave-events"></a>Eventi QueryEditQuerySave  
 Il controllo del codice sorgente VSPackage deve gestire gli eventi QEQS implementando il `IVsQueryEditQuerySave2` interfaccia e i metodi necessari. Di seguito è fornita una breve descrizione dei due metodi che il pacchetto VSPackage deve implementare almeno. L'implementazione effettiva deve essere in base alla logica di controllo del modello di origine.  
  
### <a name="queryeditfiles-method"></a>Metodo QueryEditFiles  
 Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> viene chiamato quando qualsiasi progetto o l'editor tenta di modificare un file. In teoria, questo metodo viene chiamato *prima* il file viene modificato e quando viene salvato un file. Quando viene richiamato, il `IVsQueryEditQuerySave2::QueryEditFiles` metodo controlla se i file specificati sono al controllo del codice sorgente, devono essere estratti e che possa essere ricaricati. Se circostanze impediscono che i file sia modificabile, il `IVsQueryEditQuerySave2::QueryEditFiles` metodo indica al programma chiamante per annullare la modifica. È anche possibile che al chiamante di specificare una modalità di chiamata. In modalità "automatica", questo metodo accetta azione solo se ciò non causa qualsiasi interfaccia utente da visualizzare. Se dell'interfaccia utente è inevitabile, è necessario che venga restituito un flag per indicare il problema.  
  
 Il metodo si comporta in modo transazionale. ovvero, se la modifica viene annullata in un singolo file, la modifica è stata annullata per tutti i file. Viceversa, se è consentita la modifica, è consentito per tutti i file. Se questo metodo consente la modifica di una volta per un determinato set di file, è necessario consentire sempre la modifica per le chiamate successive per lo stesso set di file. Consenti modifica ciclo continua fino a quando i file vengono chiusi, salvati e ricaricati; fino a quando non modificare i relativi attributi (proprietà); o fino a quando non viene modificato il package del controllo del codice sorgente. Nell'implementazione dei casi il `IVsQueryEditQuerySave2::QueryEditFiles` metodo includono più file, file speciali, annullare dall'utente e le modifiche in memoria.  
  
### <a name="querysavefiles-method"></a>Metodo QuerySaveFiles  
 Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> viene chiamato quando è necessario salvare un set di file di qualsiasi progetto o un editor. Quando viene richiamato, il `IVsQueryEditQuerySave2::QuerySaveFiles` metodo controlla se i file specificati sono di sola lettura e che sono sotto controllo del codice sorgente. Se i file devono essere estratto, la chiamata viene delegata al pacchetto di controllo di origine. Se circostanze impedire che i file vengono salvate le `IVsQueryEditQuerySave2::QuerySaveFiles` metodo deve indicare all'editor per annullare il salvataggio. Come con la `IVsQueryEditQuerySave2::QueryEditFiles` (metodo), è possibile che al chiamante di specificare una modalità di chiamata. In modalità "automatica", questo metodo accetta azione solo se ciò non causa qualsiasi interfaccia utente da visualizzare. Se dell'interfaccia utente è inevitabile, è necessario che venga restituito un flag per indicare il problema.  
  
 Questo metodo deve comportarsi in modo transazionale. ovvero, se il salvataggio viene annullato in un singolo file, il salvataggio è stato annullato per tutti i file. Viceversa, se è consentito il salvataggio, deve essere abilitato per tutti i file. Come con la `IVsQueryEditQuerySave2::QueryEditFiles` metodo, di casi da considerare quando si implementa il `IVsQueryEditQuerySave2::QuerySaveFiles` metodo includono più file, file speciali, annullare dall'utente e le modifiche in memoria.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>