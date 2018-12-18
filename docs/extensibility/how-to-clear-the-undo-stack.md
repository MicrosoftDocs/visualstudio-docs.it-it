---
title: 'Procedura: cancellare lo Stack di annullamento | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - clear undo stack
ms.assetid: 2200d2d4-7f58-401c-87fc-ddd32d368193
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b2519d529da13366c706e940b78f57a6ad903de7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-clear-the-undo-stack"></a>Procedura: cancellare lo Stack di annullamento
La procedura riportata di seguito viene illustrato come cancellare lo stack di annullamento.  
  
### <a name="to-clear-the-undo-stack"></a>Per cancellare lo stack di annullamento  
  
1.  Per cancellare l'utilizzo dello stack di annullamento di [IOleUndoManager::DiscardFrom](http://msdn.microsoft.com/library/windows/desktop/ms693799) metodo. Di seguito è riportato un esempio di questo oggetto:  
  
    ```  
    HRESULT CCmdWindow::ClearUndoStack()  
    {  
      HRESULT hr = S_OK;  
  
      if (m_pUndoMgr == NULL)  
        {  
        IfFailGo(m_pTextLines->GetUndoManager(&m_pUndoMgr));  
        ASSERT(m_pUndoMgr != NULL, "",;);  
        }  
  
      IfFailGo(m_pUndoMgr->DiscardFrom(NULL));  
  
    Error:  
      return hr;  
    }  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: implementare la gestione di annullamento](../extensibility/how-to-implement-undo-management.md)