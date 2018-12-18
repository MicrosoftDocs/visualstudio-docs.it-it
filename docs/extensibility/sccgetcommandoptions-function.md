---
title: Funzione SccGetCommandOptions | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccGetCommandOptions
helpviewer_keywords:
- SccGetCommandOptions function
ms.assetid: bbe4aa4e-b4b0-403e-b7a0-5dd6eb24e5a9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 60245b7fab3c2a0b313ccbe1d7393b0783962a37
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sccgetcommandoptions-function"></a>SccGetCommandOptions (funzione)
Questa funzione è richiesto all'utente per le opzioni avanzate per un determinato comando.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
SCCRTN SccGetCommandOptions(  
   LPVOID pvContext,  
   HWND hWnd,  
   enum SCCCOMMAND iCommand,  
   LPCMDOPTS* ppvOptions  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pvContext  
 [in] La struttura di contesto plug-in controllo di origine.  
  
 hWnd  
 [in] Un handle di finestra dell'IDE che il plug-in controllo del codice sorgente è possibile utilizzare come un elemento padre per eventuali finestre di dialogo che fornisce.  
  
 iCommand  
 [in] Il comando per il quale vengono richieste le opzioni avanzate (vedere [codice comando](../extensibility/command-code-enumerator.md) per i valori possibili).  
  
 ppvOptions  
 [in] La struttura di opzione (può anche essere `NULL`).  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Operazione completata.|  
|SCC_I_ADV_SUPPORT|Il plug-in controllo del codice sorgente supporta opzioni avanzate per il comando.|  
|SCC_I_OPERATIONCANCELED|L'utente ha annullato l'origine plug-in controllo **opzioni** la finestra di dialogo.|  
|SCC_E_OPTNOTSUPPORTED|Il plug-in controllo del codice sorgente non supporta questa operazione.|  
|SCC_E_ISCHECKEDOUT|Impossibile eseguire questa operazione in un file che è attualmente estratto.|  
|SCC_E_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete. È consigliabile un nuovo tentativo.|  
|SCC_E_NONSPECIFICERROR|Errore non specifico.|  
  
## <a name="remarks"></a>Note  
 Questa funzione viene chiamata l'IDE per la prima volta con `ppvOptions` = `NULL` per determinare se il plug-in controllo del codice sorgente supporta la funzionalità delle opzioni avanzate per il comando specificato. Se il plug-in supporta la funzionalità per il comando, l'IDE di questa funzione viene chiamata nuovamente quando l'utente richiede le opzioni avanzate (in genere implementato come un **avanzate** pulsante in una finestra di dialogo) e fornisce un puntatore non NULL per `ppvOptions` che punta a un `NULL` puntatore. Il plug-in Opzioni avanzate, specificate dall'utente in una struttura private archivia e restituisce un puntatore alla struttura in `ppvOptions`. Questa struttura viene quindi passata a tutte le altre funzioni API plug-in controllo di origine che occorre conoscere, tra cui le chiamate successive al `SccGetCommandOptions` (funzione).  
  
 Un esempio può aiutare a chiarire la situazione.  
  
 Un utente sceglie il **ottenere** comando e l'IDE visualizza un **ottenere** la finestra di dialogo. Nell'IDE viene chiamato il `SccGetCommandOptions` funzione `iCommand` impostato su `SCC_COMMAND_GET` e `ppvOptions` impostato su `NULL`. Ciò viene interpretato dal plug-in come la domanda di controllo del codice sorgente, "Sono le opzioni avanzate per questo comando?" Se il plug-in restituisce `SCC_I_ADV_SUPPORT`, l'IDE visualizza un **avanzate** pulsante relativo **ottenere** la finestra di dialogo.  
  
 La prima volta che l'utente fa clic il **avanzate** pulsante, l'IDE chiama nuovamente il `SccGetCommandOptions` funzione, questa volta con un non -`NULL``ppvOptions` che punta a un `NULL` puntatore. I plug-in consente di visualizzare il proprio **opzioni Leggi** nella finestra di dialogo richiede l'immissione di informazioni, viene inserita nella propria struttura e restituisce un puntatore alla struttura in `ppvOptions`.  
  
 Se l'utente fa clic **avanzate** nuovamente nella stessa finestra di dialogo, l'IDE chiama il `SccGetCommandOptions` funzione nuovamente senza modificare `ppvOptions`, in modo che la struttura viene passata per il plug-in. In questo modo il plug-in reinizializzare la finestra di dialogo per i valori che l'utente è stato impostato in precedenza. Il plug-in modifica la struttura sul posto prima della restituzione.  
  
 Infine, quando l'utente fa clic **OK** dell'IDE **ottenere** della finestra di dialogo nell'IDE viene chiamato il [SccGet](../extensibility/sccget-function.md), passando la struttura restituita in `ppvOptions` che contiene il Opzioni avanzate.  
  
> [!NOTE]
>  Il comando `SCC_COMMAND_OPTIONS` viene utilizzato quando l'IDE visualizza un **opzioni** la finestra di dialogo che consente all'utente di imposta le preferenze che controllano il funzionamento dell'integrazione. Se il plug-in controllo del codice sorgente deve fornire una finestra di dialogo Preferenze, può visualizzare da un **avanzate** pulsante nella finestra di dialogo Preferenze dell'IDE. Il plug-in è responsabile unicamente della Guida e il mantenimento di queste informazioni. l'IDE non utilizzarlo o modificarlo.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API plug-in controllo di origine](../extensibility/source-control-plug-in-api-functions.md)   
 [Codice di comando](../extensibility/command-code-enumerator.md)