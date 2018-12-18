---
title: POPDIRLISTFUNC | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: POPLISTFUNC
helpviewer_keywords: POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8503afb26ec8dc244db39dff5bddcc6d3b733896
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
Si tratta di una funzione di callback specificata per il [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) funzione per aggiornare un insieme di directory e, facoltativamente, i nomi di file per scoprire che si trovano sotto controllo del codice sorgente.  
  
 Il `POPDIRLISTFUNC` callback deve essere chiamato solo per le directory e i nomi di file (nell'elenco specificato per il `SccPopulateDirList` funzione) che vengono effettivamente nel controllo del codice sorgente.  
  
## <a name="signature"></a>Signature  
  
```cpp  
typedef BOOL (*POPDIRLISTFUNC)(  
   LPVOID pvCallerData,  
   BOOL bFolder,  
   LPCSTR lpDirectoryOrFileName  
);  
```  
  
## <a name="parameters"></a>Parametri  
 pvCallerData  
 [in] Il valore di utente fornito [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md).  
  
 bOpzioni cartella  
 [in] `TRUE` se il nome in `lpDirectoryOrFileName` è una directory; in caso contrario il nome è un nome file.  
  
 lpDirectoryOrFileName  
 [in] Percorso locale completo per un nome di directory o un file incluso nel controllo del codice sorgente.  
  
## <a name="return-value"></a>Valore restituito  
 Nell'IDE viene restituito un codice di errore appropriato:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Continuare l'elaborazione.|  
|SCC_I_OPERATIONCANCELED|Arrestare l'elaborazione.|  
|SCC_E_xxx|Qualsiasi errore di controllo di origine appropriato deve arrestare l'elaborazione.|  
  
## <a name="remarks"></a>Note  
 Se il `fOptions` parametro del `SccPopulateDirList` funzione contiene il `SCC_PDL_INCLUDEFILES` flag, quindi l'elenco conterrà probabilmente i nomi di file, nonché i nomi di directory.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni di callback implementate dall'IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)   
 [Codici di errore](../extensibility/error-codes.md)