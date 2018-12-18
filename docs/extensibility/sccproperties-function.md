---
title: Funzione SccProperties | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccProperties
helpviewer_keywords: SccProperties function
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: efaa2877743fcf69a61a79633108d203442489e0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="sccproperties-function"></a>SccProperties (funzione)
Questa funzione consente di visualizzare proprietà di controllo di origine per un file o progetto.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
SCCRTN SccProperties (  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPCSTR lpFileName  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pvContext  
 [in] La struttura di contesto plug-in controllo di origine.  
  
 hWnd  
 [in] Un handle di finestra dell'IDE che il plug-in controllo del codice sorgente è possibile utilizzare come un elemento padre per eventuali finestre di dialogo che fornisce.  
  
 lpFileName  
 [in] Il nome del percorso completo del file o progetto.  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Le proprietà sono state visualizzate correttamente.|  
|SCC_I_RELOADFILE|Sistema di controllo della versione ha modificato le proprietà di file, pertanto l'IDE di ricaricare il file.|  
|SCC_E_PROJNOTOPEN|Il progetto specificato non è stato aperto nel controllo del codice sorgente.|  
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a visualizzare le proprietà di questo file o progetto.|  
|SCC_E_FILENOTCONTROLLED|Il file specificato o il progetto non è in controllo del codice sorgente.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Si è verificato un errore sconosciuto o generale.|  
  
## <a name="remarks"></a>Note  
 Il plug-in controllo del codice sorgente consente di visualizzare le proprietà in una finestra di dialogo.  
  
 Le proprietà sono definite dal plug-in controllo del codice sorgente e potrebbero essere diversi da plug-in per plug-in. Se il plug-in consente all'utente di modificare le proprietà del controllo di un file di origine, deve restituire `SCC_I_RELOAD` per segnalare l'IDE che il file o il progetto deve essere ricaricato.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)