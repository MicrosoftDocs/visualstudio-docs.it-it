---
title: Funzione SccEndBatch | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ec549b5bb0a6c48946edf59f0ab1423cea0ac704
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sccendbatch-function"></a>SccEndBatch (funzione)
Questa funzione termina un batch di operazioni di controllo codice sorgente. Questi batch non possono essere annidati.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
SCCRTN SccEndBatch(void);  
```  
  
#### <a name="parameters"></a>Parametri  
 Nessuno.  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Batch di operazioni conclusi correttamente.|  
|SCC_E_UNKNOWNERROR|Errore non specifico.|  
  
## <a name="remarks"></a>Note  
 Batch di controllo di origine utilizzati per eseguire le stesse operazioni di controllo di origine in più progetti o più contesti. Batch consente di eliminare le finestre di dialogo ridondanti dall'esperienza utente durante un'operazione batch. Il [SccBeginBatch](../extensibility/sccbeginbatch-function.md) e `SccEndBatch` funzione vengono utilizzate in coppia per indicare l'inizio e fine di un'operazione. Non possono essere annidate.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API plug-in controllo di origine](../extensibility/source-control-plug-in-api-functions.md)   
 [SccBeginBatch](../extensibility/sccbeginbatch-function.md)