---
title: Funzione SccCheckin | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccCheckin
helpviewer_keywords:
- SccCheckin function
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bf8c8d23a89e55b272657dde0c2374c78e63bfaf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="scccheckin-function"></a>SccCheckin (funzione)
Questa funzione controlla in precedenza i file estratti al sistema di controllo di origine, le modifiche e la creazione di una nuova versione. Questa funzione viene chiamata con un conteggio e una matrice di nomi dei file da archiviare.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
SCCRTN SccCheckin (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPSTR*    lpFileNames,  
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
 [in] Numero di file selezionati da archiviare.  
  
 lpFileNames  
 [in] Matrice di nomi di percorso locale completo dei file da archiviare.  
  
 lpComment  
 [in] Commento da applicare a ognuno dei file selezionati da archiviare. Si tratta di `NULL` se il plug-in controllo del codice sorgente è una richiesta di un commento.  
  
 fOptions  
 [in] Flag di comando, i valori validi sono 0 o `SCC_KEEP_CHECKEDOUT`.  
  
 pvOptions  
 [in] Opzioni specifiche plug-in controllo del codice sorgente.  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|I file è stato correttamente archiviato.|  
|SCC_E_FILENOTCONTROLLED|Il file selezionato non è incluso nel controllo del codice sorgente.|  
|SCC_E_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete. È consigliabile un nuovo tentativo.|  
|SCC_E_NONSPECIFICERROR|Errore non specifico. File non è stato archiviato.|  
|SCC_E_NOTCHECKEDOUT|L'utente non ha estratto il file, in modo non è possibile verificare.|  
|SCC_E_CHECKINCONFLICT|Archiviazione non può essere eseguita perché:<br /><br /> -Un altro utente ha archiviato anticipo e `bAutoReconcile` è false.<br /><br /> oppure<br /><br /> -Il merge automatico non può essere eseguito (ad esempio, quando i file sono binari).|  
|SCC_E_VERIFYMERGE|File è stato unito automaticamente, ma non è stato archiviato attesa di verifica dell'utente.|  
|SCC_E_FIXMERGE|File è stato unito automaticamente, ma non è stato archiviato a causa di un conflitto di tipo merge che deve essere risolti manualmente.|  
|SCC_E_NOTAUTHORIZED|L'utente non è possibile eseguire questa operazione.|  
|SCC_I_OPERATIONCANCELED|Operazione annullata prima del completamento.|  
|SCC_I_RELOADFILE|Un progetto o il file deve essere ricaricato.|  
|SCC_E_FILENOTEXIST|File locale non è stato trovato.|  
  
## <a name="remarks"></a>Note  
 Il commento si applica a tutti i file da archiviare. L'argomento commento può essere un `null` stringa, nel qual caso il plug-in controllo del codice sorgente può richiedere all'utente una stringa di commento per ogni file.  
  
 Il `fOptions` argomento può essere assegnato il valore di `SCC_KEEP_CHECKEDOUT` flag che indica l'intenzione dell'utente per archiviare il file ed estrarlo di nuovo.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)