---
title: OPTNAMECHANGEPFN | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: OPTNAMECHANGEPFN
helpviewer_keywords: OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2d067d5dd150dd026a2bd29a8933e8d9f72222b0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
Si tratta di una funzione di callback specificata in una chiamata al [SccSetOption](../extensibility/sccsetoption-function.md) (tramite opzione `SCC_OPT_NAMECHANGEPFN`) e viene utilizzato per comunicare nome modifiche per il controllo del codice sorgente plug-in dell'IDE di.  
  
## <a name="signature"></a>Signature  
  
```cpp  
typedef void (*OPTNAMECHANGEPFN)(  
   LPVOID pvCallerData,  
   LPCSTR pszOldName,  
   LPCSTR pszNewName  
);  
```  
  
## <a name="parameters"></a>Parametri  
 pvCallerData  
 [in] Il valore di utente specificato in una chiamata precedente al [SccSetOption](../extensibility/sccsetoption-function.md) (utilizzando l'opzione `SCC_OPT_USERDATA`).  
  
 pszOldName  
 [in] Il nome originale del file.  
  
 pszNewName  
 [in] Il nome del file è stato rinominato.  
  
## <a name="return-value"></a>Valore restituito  
 Nessuno.  
  
## <a name="remarks"></a>Note  
 Se un file viene rinominato durante un'operazione di controllo del codice sorgente, il plug-in controllo del codice sorgente può inviare una notifica di modifica del nome tramite questo callback IDE.  
  
 Se l'IDE non supporta questo callback, non chiamerà il [SccSetOption](../extensibility/sccsetoption-function.md) specificarlo. Se il plug-in non supporta questo callback, verrà restituito `SCC_E_OPNOTSUPPORTED` dal `SccSetOption` funziona quando l'IDE tenta di impostare il callback.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni di callback implementate dall'IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)