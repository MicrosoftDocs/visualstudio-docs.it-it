---
title: Funzione SccBeginBatch | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5350484294d02356301839e38b97bea1d40ec27c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sccbeginbatch-function"></a>SccBeginBatch (funzione)
Questa funzione viene avviata una sequenza di batch di operazioni di controllo codice sorgente. Il [SccEndBatch](../extensibility/sccendbatch-function.md) verrà chiamata per terminare il batch. Questi batch non possono essere annidati.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
SCCRTN SccBeginBatch(void);  
```  
  
#### <a name="parameters"></a>Parametri  
 Nessuno.  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Batch di operazioni è iniziata correttamente.|  
|SCC_E_UNKNOWNERROR|Errore non specifico.|  
  
## <a name="remarks"></a>Note  
 Batch di controllo di origine utilizzati per eseguire le stesse operazioni in più progetti o più contesti. Batch consente di eliminare le finestre di dialogo progetto ridondanti dall'esperienza utente durante un'operazione batch. Il `SccBeginBatch` funzione e [SccEndBatch](../extensibility/sccendbatch-function.md) vengono utilizzati come una coppia di funzione per indicare l'inizio e fine di un'operazione. Non possono essere annidate. `SccBeginBatch` imposta un flag che indica che un'operazione batch è in corso.  
  
 Durante un'operazione batch è attiva, il plug-in controllo del codice sorgente deve presentare al massimo una finestra di dialogo per qualsiasi domanda all'utente, applicare la risposta da questa finestra di dialogo tutte le operazioni successive.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API plug-in controllo di origine](../extensibility/source-control-plug-in-api-functions.md)   
 [SccEndBatch](../extensibility/sccendbatch-function.md)