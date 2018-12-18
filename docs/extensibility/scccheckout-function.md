---
title: Funzione SccCheckout | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccCheckout
helpviewer_keywords: SccCheckout function
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: af8aac642ecd21f8f4709874e4e3e6ff0b3e58b5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="scccheckout-function"></a>SccCheckout (funzione)
Dato un elenco di nomi completi dei file, questa funzione li estrae nell'unità locale. Il commento si applica a tutti i file estratti. L'argomento commento può essere un `null` stringa.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
SCCRTN SccCheckout (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LPCSTR    lpComment,  
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
 [in] Numero di file selezionati per l'estrazione.  
  
 lpFileNames  
 [in] Matrice di nomi di percorso locale completo dei file da estrarre.  
  
 lpComment  
 [in] Commento da applicare a ogni file selezionato venga estratto.  
  
 fOptions  
 [in] Flag di comando (vedere [flag di bit utilizzati dai comandi specifici](../extensibility/bitflags-used-by-specific-commands.md)).  
  
 pvOptions  
 [in] Opzioni specifiche plug-in controllo di origine.  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Estrazione completata.|  
|SCC_E_FILENOTCONTROLLED|Il file selezionato non è incluso nel controllo del codice sorgente.|  
|SCC_E_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete. È consigliabile un nuovo tentativo.|  
|SCC_E_NOTAUTHORIZED|L'utente non è possibile eseguire questa operazione.|  
|SCC_E_NONSPECIFICERROR|Errore non specifico. Il file non estratto.|  
|SCC_E_ALREADYCHECKEDOUT|L'utente ha già estratto il file.|  
|SCC_E_FILEISLOCKED|Il file è bloccato, che la creazione di nuove versioni.|  
|SCC_E_FILEOUTEXCLUSIVE|Un altro utente ha eseguito un'estrazione esclusiva su questo file.|  
|SCC_I_OPERATIONCANCELED|L'operazione è stata annullata prima del completamento.|  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API plug-in controllo di origine](../extensibility/source-control-plug-in-api-functions.md)   
 [Flag di bit usati da comandi specifici](../extensibility/bitflags-used-by-specific-commands.md)