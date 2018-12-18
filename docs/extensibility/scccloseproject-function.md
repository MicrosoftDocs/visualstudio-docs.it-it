---
title: Funzione SccCloseProject | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccCloseProject
helpviewer_keywords: SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 70b0e693f4223c9fe004170a0ed1b4b70c6de442
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
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