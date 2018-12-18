---
title: Funzione SccAdd | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccAdd
helpviewer_keywords: SccAdd function
ms.assetid: 545268f3-8e83-446a-a398-1a9db9e866e8
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 52137da9d14920a2fd5213f1110a74d895e51c7f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="sccadd-function"></a>SccAdd (funzione)
Questa funzione consente di aggiungere nuovi file per il controllo del codice sorgente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
SCCRTN SccAdd(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LPCSTR    lpComment,  
   LONG*     pfOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pvContext  
 [in] La struttura di contesto plug-in controllo di origine.  
  
 hWnd  
 [in] Un handle di finestra dell'IDE che il plug-in controllo del codice sorgente è possibile utilizzare come un elemento padre per eventuali finestre di dialogo che fornisce.  
  
 nFiles  
 [in] Numero di file selezionati da aggiungere al progetto corrente come specificato nella `lpFileNames` matrice.  
  
 lpFileNames  
 [in] Matrice di nomi completi di locali dei file da aggiungere.  
  
 lpComment  
 [in] Il commento da applicare a tutti i file da aggiungere.  
  
 pfOptions  
 [in] Matrice di flag dei comandi, fornite in un singolo file.  
  
 pvOptions  
 [in] Opzioni specifiche plug-in controllo di origine.  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|L'operazione di aggiunta è riuscita.|  
|SCC_E_FILEALREADYEXISTS|Il file selezionato è già in controllo del codice sorgente.|  
|SCC_E_TYPENOTSUPPORTED|Il tipo del file (ad esempio, binario) non è supportato dal sistema di controllo di origine.|  
|SCC_E_OPNOTSUPPORTED|Il controllo del codice sorgente non supporta questa operazione.|  
|SCC_E_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete. È consigliabile un nuovo tentativo.|  
|SCC_E_NOTAUTHORIZED|L'utente non è possibile eseguire questa operazione.|  
|SCC_E_NONSPECIFICERROR|Errore non specifico. aggiungere non eseguita.|  
|SCC_I_OPERATIONCANCELED|L'operazione è stata annullata prima del completamento.|  
|SCC_I_RELOADFILE|Un progetto o il file deve essere ricaricato.|  
|SCC_E_FILENOTEXIST|File locale non è stato trovato.|  
  
## <a name="remarks"></a>Note  
 Le normali attività `fOptions` vengono sostituiti seguito da una matrice, `pfOptions`, con uno `LONG` opzione specifica per ogni file. Questo avviene perché il tipo di file può variare da un file a un file.  
  
> [!NOTE]
>  Non è possibile specificare sia `SCC_FILETYPE_TEXT` e `SCC_FILETYPE_BINARY` opzioni per lo stesso file, ma è possibile specificare nessuno. L'impostazione non corrisponde all'impostazione `SCC_FILETYPE_AUTO`, nel qual caso il controllo origine plug-in rileva automaticamente il tipo di file.  
  
 Di seguito è riportato l'elenco di flag utilizzati nel `pfOptions` matrice:  
  
|Opzione|Valore|Significato|  
|------------|-----------|-------------|  
|SCC_FILETYPE_AUTO|0x00|Il plug-in controllo del codice sorgente deve rilevare il tipo di file.|  
|SCC_FILETYPE_TEXT|0x01|Indica un file di testo ASCII.|  
|SCC_FILETYPE_BINARY|0x02|Indica un tipo di file diversi dal testo ASCII.|  
|SCC_ADD_STORELATEST|0x04|Archivia solo la copia più recente del file, non delta.|  
|SCC_FILETYPE_TEXT_ANSI|0x08|Considera il file come testo ANSI.|  
|SCC_FILETYPE_UTF8|0x10|Considera il file come testo Unicode in formato UTF8.|  
|SCC_FILETYPE_UTF16LE|0x20|Considera il file come testo Unicode in formato UTF16 Little Endian formato.|  
|SCC_FILETYPE_UTF16BE|0x40|Considera formattare il file come testo Unicode in formato UTF16 Big Endian.|  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)