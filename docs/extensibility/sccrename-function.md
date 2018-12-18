---
title: Funzione SccRename | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccRename
helpviewer_keywords:
- SccRename function
ms.assetid: b467ade6-a1db-4c0b-b60f-7850ec4f79eb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c24d84ff659d287f3b32be2b5585ded16b148395
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sccrename-function"></a>SccRename (funzione)
Questa funzione Rinomina un file nel sistema di controllo di origine.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
SCCRTN SccRename(  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPCSTR lpFileName,  
   LPCSTR lpNewName  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pvContext  
 [in] La struttura di contesto plug-in controllo di origine.  
  
 hWnd  
 [in] Un handle di finestra dell'IDE che il plug-in controllo del codice sorgente è possibile utilizzare come un elemento padre per eventuali finestre di dialogo che fornisce.  
  
 lpFileName  
 [in] Il nome file completo del file da rinominare.  
  
 lpNewName  
 [in] Il nuovo nome completo. Se il percorso della directory è diverso, quindi il file è stato spostato da una sottodirectory a un altro.  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|L'operazione di ridenominazione è stata completata.|  
|SCC_E_PROJNOTOPEN|Il progetto non è aperto in controllo del codice sorgente.|  
|SCC_E_FILENOTCONTROLLED|Il file non è incluso nel controllo del codice sorgente.|  
|SCC_E_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete.|  
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato per completare l'operazione.|  
|SCC_E_COULDNOTCREATEPROJECT|Il progetto non può essere creato come parte del processo di ridenominazione.|  
|SCC_E_OPNOTPERFORMED|Non è stata eseguita l'operazione.|  
|SCC_E_NONSPECIFICERROR|Si è verificato un errore non specificato o generale.|  
  
## <a name="remarks"></a>Note  
 Questa funzione può essere utilizzata per rinominare un file o lo spostamento da una posizione a un'altra nel sistema di controllo di origine. Il plug-in controllo del codice sorgente non tentare di accedere al file su disco. È responsabilità dell'IDE per rinominare il file locale.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)