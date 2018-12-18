---
title: 'Procedura: utilizzare Gestione fase di rollback collegata | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - linked undo management
ms.assetid: af5cc22a-c9cf-45b1-a894-1022d563f3ca
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7a025cdfc14eb39dad7ea2bc72a69f1f260fb583
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-linked-undo-management"></a>Procedura: utilizzare Gestione fase di rollback collegata
Fase di rollback collegata consente all'utente di annullare contemporaneamente le stesse modifiche in più file. Modifiche di testo simultanee in più file di programma, ad esempio un file di intestazione e un file di Visual C++, è ad esempio, una transazione di annullamento collegata. Funzionalità di annullamento collegato è incorporata l'implementazione dell'ambiente di gestione degli annullamenti, e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager> consente di modificare questa funzionalità. Fase di rollback collegata è implementata da un'unità di annullamento padre che è possibile collegare gli stack di annullamento separato in modo da essere considerato come una sola unità di annullamento. La procedura per l'utilizzo di fase di rollback collegata è descritta in dettaglio nella sezione seguente.  
  
### <a name="to-use-linked-undo"></a>Per utilizzare il comando Annulla collegato  
  
1.  Chiamare `QueryService` su `SVsLinkedUndoManager` per ottenere un puntatore a `IVsLinkedUndoTransactionManager`.  
  
2.  Creare l'unità di annullamento collegato padre iniziale chiamando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.OpenLinkedUndo%2A>. Questo imposta il punto di partenza per un set di stack di annullamento al fine di essere raggruppati in stack in fase di rollback collegata. Nel `OpenLinkedUndo` metodo sarà inoltre necessario specificare se si desidera che la fase di rollback collegata non strict o strict. Il comportamento di annullamento collegato non strict significa che alcuni dei documenti con elementi di pari livello fase di rollback collegata è possibile chiudere e lasciare l'altra collegato annullare nei rispettivi stack di elementi di pari livello. Comportamento di annullamento collegato rigido specifica che tutti gli stack di pari livello fase di rollback collegata può essere annullata insieme o non è affatto. Aggiungere successive collegata Annulla stack chiamando [IOleUndoManager::Add](http://msdn.microsoft.com/library/windows/desktop/ms680135) metodo.  
  
3.  Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.CloseLinkedUndo%2A> eseguire tutte le unità di annullamento collegati come uno.  
  
    > [!NOTE]
    >  Per implementare la gestione fase di rollback collegata in un editor, aggiungere Gestione di annullamento. Per ulteriori informazioni sull'implementazione della fase di rollback collegata management, vedere [procedura: implementare annullare gestione](../extensibility/how-to-implement-undo-management.md).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>   
 [IOleParentUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms682151)   
 [Interfaccia IOleUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms678476)   
 [Procedura: implementare la gestione di annullamento](../extensibility/how-to-implement-undo-management.md)