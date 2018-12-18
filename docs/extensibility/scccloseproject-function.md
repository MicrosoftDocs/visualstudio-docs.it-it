---
title: Funzione SccCloseProject | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4f977c1241408f5e33d31a63262abb5ee24670e5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="scccloseproject-function"></a>SccCloseProject (funzione)
Questa funzione chiude un progetto, contrassegnare la fine di una determinata sessione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
SCCRTN SccCloseProject (  
   LPVOID pvContext  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pvContext  
 La struttura di contesto plug-in controllo di origine.  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Il progetto è stato chiuso.|  
|SCC_E_PROJNOTOPEN|Nessun progetto è aperto.|  
|SCC_E_NOTAUTHORIZED|L'utente non è possibile eseguire questa operazione.|  
|SCC_E_NONSPECIFICERROR|Errore non specifico.|  
  
## <a name="remarks"></a>Note  
 Il [SccOpenProject](../extensibility/sccopenproject-function.md) viene sempre chiamato prima che questa funzione. Una chiamata a questa funzione è quindi seguita da una chiamata al `SccOpenProject` funzione o [SccUninitialize](../extensibility/sccuninitialize-function.md), che termina la connessione per il controllo del codice sorgente completamente.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API plug-in controllo di origine](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)