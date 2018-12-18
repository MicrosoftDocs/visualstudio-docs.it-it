---
title: Funzione SccPopulateList | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccPopulateList
helpviewer_keywords:
- SccPopulateList function
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 26e7bbb4a99c3cd649eedb7638feb5b6170b3b59
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sccpopulatelist-function"></a>SccPopulateList (funzione)
Questa funzione aggiorna un elenco di file per un comando di controllo di origine specifica e fornisce lo stato del controllo di origine in tutti i file specificati.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
SCCRTN SccPopulateList (  
   LPVOID          pvContext,  
   enum SCCCOMMAND nCommand,  
   LONG            nFiles,  
   LPCSTR*         lpFileNames,  
   POPLISTFUNC     pfnPopulate,  
   LPVOID          pvCallerData,  
   LPLONG          lpStatus,  
   LONG            fOptions  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pvContext  
 [in] La struttura di contesto plug-in controllo di origine.  
  
 Ncomando  
 [in] Il comando di controllo di origine che verrà applicato a tutti i file di `lpFileNames` matrice (vedere [codice comando](../extensibility/command-code-enumerator.md) per un elenco di possibili comandi).  
  
 nFiles  
 [in] Numero di file di `lpFileNames` matrice.  
  
 lpFileNames  
 [in] Matrice di nomi di file noto all'IDE.  
  
 pfnPopulate  
 [in] La funzione di callback da chiamare per aggiungere e rimuovere i file di IDE (vedere [POPLISTFUNC](../extensibility/poplistfunc.md) per informazioni dettagliate).  
  
 pvCallerData  
 [in] Valore che deve essere passato alla funzione di callback subisce modifiche.  
  
 lpStatus  
 [in, out] Una matrice per il plug-in per restituire il flag di stato per ogni file di controllo del codice sorgente.  
  
 fOptions  
 [in] Flag di comando (vedere la sezione "flag PopulateList" [flag di bit utilizzati dai comandi specifici](../extensibility/bitflags-used-by-specific-commands.md) per informazioni dettagliate).  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Operazione completata.|  
|SCC_E_NONSPECIFICERROR|Errore non specifico.|  
  
## <a name="remarks"></a>Note  
 Questa funzione esamina l'elenco di file per lo stato corrente. Usa il `pfnPopulate` funzione di callback per notificare al chiamante quando un file non corrispondono ai criteri per il `nCommand`. Ad esempio, se il comando è `SCC_COMMAND_CHECKIN` e non è estratto un file nell'elenco, quindi il callback viene utilizzato per informare il chiamante. In alcuni casi, il plug-in controllo del codice sorgente potrebbero essere presenti altri file che potrebbero far parte del comando e aggiungerli. In questo modo, ad esempio, un utente di Visual Basic per estrarre un file con estensione bmp che viene usato per il proprio progetto ma non viene visualizzato nel file di progetto Visual Basic. Un utente sceglie il **ottenere** comando nell'IDE. L'IDE verrà visualizzato un elenco di tutti i file che ritiene che l'utente può ottenere, ma prima che l'elenco viene visualizzato, il `SccPopulateList` funzione viene chiamata per verificare che l'elenco deve essere visualizzato è aggiornato.  
  
## <a name="example"></a>Esempio  
 L'IDE compila un elenco di file che ritiene che l'utente può ottenere. Prima di visualizzare l'elenco, viene chiamato il `SccPopulateList` di funzione, consentendo il plug-in controllo del codice sorgente per aggiungere ed eliminare file nell'elenco. Il plug-in modifica l'elenco, chiamando la funzione di callback specificato (vedere [POPLISTFUNC](../extensibility/poplistfunc.md) per altri dettagli).  
  
 Il plug-in continua a chiamare il `pfnPopulate` funzione, che aggiunge ed elimina i file, fino a quando non è terminato e lo restituisce il `SccPopulateList` (funzione). L'IDE è quindi possibile visualizzare il relativo elenco. Il `lpStatus` matrice rappresenta tutti i file nell'elenco originale passato dall'IDE. I plug-in riempimenti nello stato di tutti questi file oltre a rendere utilizzano la funzione di callback.  
  
> [!NOTE]
>  Un plug-in controllo del codice sorgente ha sempre la possibilità di limitino a restituire immediatamente da questa funzione, senza modificare l'elenco. Se un plug-in implementa questa funzione, è possibile che questo impostando il `SCC_CAP_POPULATELIST` funzionalità flag di bit nella prima chiamata al [SccInitialize](../extensibility/sccinitialize-function.md). Per impostazione predefinita, il plug-in necessario presupporre sempre che tutti gli elementi passati sono file. Tuttavia, se l'IDE imposta il `SCC_PL_DIR` flag nel `fOptions` parametro, tutti gli elementi passati devono essere considerati una directory. Il plug-in necessario aggiungere tutti i file che appartengono nelle directory. L'IDE non passeranno mai in una combinazione di file e directory.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API plug-in controllo di origine](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)   
 [Flag di bit utilizzati dai comandi specifici](../extensibility/bitflags-used-by-specific-commands.md)   
 [Codice di comando](../extensibility/command-code-enumerator.md)