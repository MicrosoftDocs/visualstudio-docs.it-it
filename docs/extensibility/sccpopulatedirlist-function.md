---
title: Funzione SccPopulateDirList | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5315f3156f71310c92069ec3743232e98818b9a5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sccpopulatedirlist-function"></a>SccPopulateDirList (funzione)
Questa funzione determina quali directory e, facoltativamente, i file vengono archiviati nel controllo del codice sorgente, viene visualizzato un elenco di directory da esaminare.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
SCCRTN SccPopulateDirList(  
   LPVOID        pContext,  
   LONG          nDirs,  
   LPCSTR*       lpDirPaths,  
   POPDIRLISTFUNCpfnPopulate,  
   LPVOID        pvCallerData,  
   LONG          fOptions  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pContext  
 [in] Il puntatore di contesto plug-in controllo di origine.  
  
 nDirs  
 [in] Numero di percorsi di directory nel `lpDirPaths` matrice.  
  
 lpDirPaths  
 [in] Matrice di percorsi di directory da esaminare.  
  
 pfnPopulate  
 [in] Funzione di callback da chiamare per ogni nome del file nel percorso di directory e (facoltativamente) `lpDirPaths` (vedere [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) per informazioni dettagliate).  
  
 pvCallerData  
 [in] Valore che deve essere passato alla funzione di callback subisce modifiche.  
  
 fOptions  
 [in] Una combinazione di valori che controllano la modalità di elaborazione le directory (vedere la sezione "PopulateDirList flags" [flag di bit utilizzati dai comandi specifici](../extensibility/bitflags-used-by-specific-commands.md) per i valori possibili).  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|L'operazione è stata completata.|  
|SCC_E_UNKNOWNERROR|Si è verificato un errore.|  
  
## <a name="remarks"></a>Note  
 Solo le directory e, facoltativamente, i nomi di file che vengono effettivamente nel repository del controllo del codice sorgente vengono passati alla funzione di callback.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API plug-in controllo di origine](../extensibility/source-control-plug-in-api-functions.md)   
 [Flag di bit utilizzati dai comandi specifici](../extensibility/bitflags-used-by-specific-commands.md)   
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)   
 [Codici di errore](../extensibility/error-codes.md)