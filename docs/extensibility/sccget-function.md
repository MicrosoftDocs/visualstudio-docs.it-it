---
title: Funzione SccGet | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccGet
helpviewer_keywords: SccGet function
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 73f5c55b39d855eb084206ef27e2254d50377b86
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="sccget-function"></a>SccGet (funzione)
Questa funzione recupera una copia di uno o più file per la visualizzazione e la compilazione, ma non per la modifica. Nella maggior parte dei sistemi, i file vengono contrassegnati come di sola lettura.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
SCCRTN SccGet(  
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
 [in] La struttura di contesto del plug-in controllo del codice sorgente.  
  
 hWnd  
 [in] Un handle di finestra dell'IDE che il plug-in controllo del codice sorgente è possibile utilizzare come un elemento padre per eventuali finestre di dialogo che fornisce.  
  
 nFiles  
 [in] Numero di file specificato per il `lpFileNames` matrice.  
  
 lpFileNames  
 [in] Matrice di nomi completi di file da recuperare.  
  
 fOptions  
 [in] Flag di comando (`SCC_GET_ALL`, `SCC_GET_RECURSIVE`).  
  
 pvOptions  
 [in] Opzioni specifiche plug-in controllo di origine.  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Esito positivo dell'operazione get.|  
|SCC_E_FILENOTCONTROLLED|Il file non è incluso nel controllo del codice sorgente.|  
|SCC_E_OPNOTSUPPORTED|Il controllo del codice sorgente non supporta questa operazione.|  
|SCC_E_FILEISCHECKEDOUT|Impossibile ottenere il file che l'utente ha estratto.|  
|SCC_E_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete. È consigliabile un nuovo tentativo.|  
|SCC_E_NOSPECIFIEDVERSION|Versione non valida o data/ora specificati.|  
|SCC_E_NONSPECIFICERROR|Errore non specifico. file non è stato sincronizzato.|  
|SCC_I_OPERATIONCANCELED|Operazione annullata prima del completamento.|  
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|  
  
## <a name="remarks"></a>Note  
 Questa funzione viene chiamata con un conteggio e una matrice di nomi dei file da recuperare. Se l'IDE passa il flag `SCC_GET_ALL`, ciò significa che gli elementi in `lpFileNames` non sono file, ma le directory e che devono essere recuperati tutti i file di controllo del codice sorgente nella directory specificata.  
  
 Il `SCC_GET_ALL` flag può essere combinato con il `SCC_GET_RECURSIVE` flag per recuperare tutti i file nella directory specificata e tutte le sottodirectory anche.  
  
> [!NOTE]
>  `SCC_GET_RECURSIVE`non deve mai essere passato senza `SCC_GET_ALL`. Si noti inoltre che se le directory C:\A e C:\A\B sono entrambi passato in una ricorsiva ottengono, C:\A\B e tutte le relative sottodirectory verranno effettivamente recuperate due volte. È responsabilità dell'IDE, e non il controllo origine del plug-in, per assicurarsi che restino duplicati, ad esempio questo dalla matrice.  
  
 Infine, anche se un controllo origine plug-in specificato il `SCC_CAP_GET_NOUI` flag durante l'inizializzazione, che indica che non dispone di un'interfaccia utente per un comando Get, questa funzione può ancora essere chiamata dall'IDE per recuperare i file. Il flag indica semplicemente che l'IDE non è presente una voce di menu Get e che il plug-in non è previsto fornire qualsiasi interfaccia utente.  
  
## <a name="renaming-and-sccget"></a>La ridenominazione e SccGet  
 Situazione: un utente estrae un file, ad esempio, txt e modifica. Prima txt può essere archiviata, un secondo utente rinomina txt in b.txt nel database del controllo origine, estrae b.txt, effettua alcune modifiche al file e archivia il file. Il primo utente richiede le modifiche apportate dall'utente secondo pertanto il primo utente rinomina la versione locale di un file txt in b.txt e non un'operazione get sul file. Tuttavia, la cache locale che tiene traccia dei numeri di versione ancora ritiene che la prima versione di a. txt è archiviata in locale e quindi controllo del codice sorgente non è possibile risolvere le differenze.  
  
 Esistono due modi per risolvere questa situazione in cui la cache locale delle versioni di controllo di origine diventa sincronizzata con il database del controllo del codice sorgente:  
  
1.  Non consentire la ridenominazione di un file nel database di origine di controllo che è attualmente estratto.  
  
2.  Eseguire l'equivalente di "eliminazione precedente" seguita da "Aggiungi nuovo". L'algoritmo seguente è un modo per eseguire questa operazione.  
  
    1.  Chiamare il [SccQueryChanges](../extensibility/sccquerychanges-function.md) funzione per apprendere la ridenominazione di txt in b.txt nel database del controllo del codice sorgente.  
  
    2.  Rinominare il txt locale in b.txt.  
  
    3.  Chiamare il `SccGet` per txt e b.txt (funzione).  
  
    4.  Perché non esiste nel database del controllo origine txt, viene eliminata la cache della versione locale delle informazioni sulla versione txt mancante.  
  
    5.  Il file b.txt estratto viene unito con il contenuto del file locale b.txt.  
  
    6.  Il file aggiornato b.txt può ora essere archiviato.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API plug-in controllo di origine](../extensibility/source-control-plug-in-api-functions.md)   
 [Flag di bit usati da comandi specifici](../extensibility/bitflags-used-by-specific-commands.md)