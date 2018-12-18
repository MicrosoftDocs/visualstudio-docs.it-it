---
title: Funzione SccUncheckout | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccUncheckout
helpviewer_keywords:
- SccUncheckout function
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c363da795e588963c234af05a856f3352a7b2815
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sccuncheckout-function"></a>SccUncheckout (funzione)
Questa funzione Annulla un'operazione di estrazione precedente, ripristinando in questo modo il contenuto del file selezionato o dei file allo stato precedente l'estrazione. Tutte le modifiche apportate al file dopo l'estrazione andranno perse.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
SCCRTN SccUncheckout (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pvContext  
 [in] La struttura di contesto plug-in controllo di origine.  
  
 hWnd  
 [in] Un handle di finestra dell'IDE che il plug-in controllo del codice sorgente è possibile utilizzare come un elemento padre per eventuali finestre di dialogo che fornisce.  
  
 nFiles  
 [in] Numero di file specificato per il `lpFileNames` matrice.  
  
 lpFileNames  
 [in] Matrice di nomi di percorso locale completo dei file per il quale annullare l'estrazione.  
  
 fOptions  
 [in] Flag di comando (non utilizzato).  
  
 pvOptions  
 [in] Opzioni specifiche plug-in controllo di origine.  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Annullamento dell'estrazione è stata completata.|  
|SCC_E_FILENOTCONTROLLED|Il file selezionato non è incluso nel controllo del codice sorgente.|  
|SCC_E_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete. È consigliabile un nuovo tentativo.|  
|SCC_E_NONSPECIFICERROR|Errore non specifico. Annulla estrazione non riuscita.|  
|SCC_E_NOTCHECKEDOUT|L'utente non dispone di file viene estratto.|  
|SCC_E_NOTAUTHORIZED|L'utente non è possibile eseguire questa operazione.|  
|SCC_E_PROJNOTOPEN|Il progetto non è stata aperta dal controllo del codice sorgente.|  
|SCC_I_OPERATIONCANCELED|L'operazione è stata annullata prima del completamento.|  
  
## <a name="remarks"></a>Note  
 Dopo questa operazione, il `SCC_STATUS_CHECKEDOUT` e `SCC_STATUS_MODIFIED` flag verranno cancellati per i file in cui è stato eseguito l'annullamento dell'estrazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)