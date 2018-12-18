---
title: 'Procedura: implementare la gestione di annullamento | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - undo management
ms.assetid: 1942245d-7a1d-4a11-b5e7-a3fe29f11c0b
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: cf57b24d81e193294f5ab90f71af07b229ec5839
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-undo-management"></a>Procedura: implementare la gestione di annullamento
L'interfaccia principale utilizzata per la gestione di annullamento è <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>, che è implementata dall'ambiente. Per supportare la gestione di annullamento, implementare l'unità di annullamento separato (vale a dire <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>, che può contenere più i singoli passaggi.  
  
 Modalità di implementazione di gestione di annullamento varia a seconda se l'editor supporta più viste o meno. Nelle sezioni seguenti vengono descritti in dettaglio le procedure per ogni implementazione.  
  
## <a name="cases-where-an-editor-supports-a-single-view"></a>Casi in cui un editor supporta una visualizzazione  
 In questo scenario, l'editor non supporta più viste. È presente solo un editor e un documento e supportano l'annullamento. Utilizzare la procedura seguente per implementare la gestione di annullamento.  
  
#### <a name="to-support-undo-management-for-a-single-view-editor"></a>Per supportare la gestione di rollback per un editor di sola visualizzazione  
  
1.  Chiamare `QueryInterface` sul `IServiceProvider` interfaccia la cornice della finestra per `IOleUndoManager`, dall'oggetto documento vista per accedere al gestore di annullamento (`IID_IOLEUndoManager`).  
  
2.  Quando una vista è collocata in una cornice di finestra, ottiene un puntatore a sito, che è possibile utilizzare per chiamare `QueryInterface` per `IServiceProvider`.  
  
## <a name="cases-where-an-editor-supports-multiple-views"></a>Casi in cui un editor supporta più viste  
 Se si dispone di separazione di documento e la visualizzazione, è in genere un annullamento manager associato al documento stesso. Tutte le unità di annullamento vengono inserite nella gestione di un annullamento associato all'oggetto dati di documento.  
  
 Anziché l'esecuzione di query visualizzazione per il gestore di annullamento, che ne esista uno per ogni visualizzazione, i dati del documento object chiama <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> per creare un'istanza di gestione degli annullamenti, specificando un identificatore di classe di CLSID_OLEUndoManager. L'identificatore di classe è definita nel file OCUNDOID.h.  
  
 Quando si utilizza <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> per creare la propria istanza di gestione di annullamento, usare la procedura seguente per associare il gestore di annullamento nell'ambiente.  
  
#### <a name="to-hook-your-undo-manager-into-the-environment"></a>Per associare il gestore di annullamento nell'ambiente  
  
1.  Chiamare `QueryInterface` sull'oggetto restituito da <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> per `IID_IOleUndoManager`. Archiviare il puntatore a <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>.  
  
2.  Chiamare `QueryInterface` su `IOleUndoManager` per `IID_IOleCommandTarget`. Archiviare il puntatore a <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
3.  Inoltro del <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> e <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> chiama archiviato `IOleCommandTarget` interfaccia per i seguenti comandi StandardCommandSet97:  
  
    -   cmdidUndo  
  
    -   cmdidMultiLevelUndo  
  
    -   cmdidRedo  
  
    -   cmdidMultiLevelRedo  
  
    -   cmdidMultiLevelUndoList  
  
    -   cmdidMultiLevelRedoList  
  
4.  Chiamare `QueryInterface` su `IOleUndoManager` per `IID_IVsChangeTrackingUndoManager`. Archiviare il puntatore a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>.  
  
     Utilizzare il puntatore a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> per chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.MarkCleanState%2A>, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.AdviseTrackingClient%2A>e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.UnadviseTrackingClient%2A> metodi.  
  
5.  Chiamare `QueryInterface` su `IOleUndoManager` per `IID_IVsLinkCapableUndoManager`.  
  
6.  Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkCapableUndoManager.AdviseLinkedUndoClient%2A> con il documento, che deve inoltre implementare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoClient> interfaccia. Quando la chiusura del documento, chiamare `IVsLinkCapableUndoManager::UnadviseLinkedUndoClient`.  
  
7.  Quando la chiusura del documento, chiamare `QueryInterface` in per la gestione degli annullamenti `IID_IVsLifetimeControlledObject`.  
  
8.  Chiamare il metodo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject.SeverReferencesToOwner%2A>.  
  
9. Quando vengono apportate modifiche al documento, chiamare <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> del gestore con un `OleUndoUnit` classe. Il <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> metodo mantiene un riferimento all'oggetto, generalmente rilascio subito dopo il <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>.  
  
 La `OleUndoManager` classe rappresenta un'istanza di stack singola operazione di annullamento. Pertanto, è disponibile un oggetto di gestione di annullamento per ogni entità di dati viene tenuta traccia per l'annullamento o ripetizione.  
  
> [!NOTE]
>  Mentre l'oggetto di gestione di annullamento è ampiamente utilizzato da editor di testo, è un componente generale che non dispone di alcun supporto specifico per l'editor di testo. Se si desidera supportare l'annullamento a più livello o ripristino, è possibile utilizzare questo oggetto a tale scopo.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject>   
 [Procedura: cancellare lo Stack di annullamento](../extensibility/how-to-clear-the-undo-stack.md)