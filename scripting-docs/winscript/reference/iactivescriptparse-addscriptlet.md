---
title: IActiveScriptParse::AddScriptlet | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptParse.AddScriptlet
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptParse_AddScriptlet
ms.assetid: 824929f4-4dd3-473a-92d9-0b96acea2f14
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e854ac71dc36263d805160f9336e049856076ce5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparseaddscriptlet"></a>IActiveScriptParse::AddScriptlet
Aggiunge codice scriptlet allo script. Questo metodo viene utilizzato negli ambienti in cui lo stato persistente dello script è collegato con il documento di host e l'host è responsabile per il ripristino di script, anziché tramite un `IPersist*` interfaccia. Gli esempi primari sono linguaggi di scripting HTML che consentono gli scriptlet di codice incorporato nel documento HTML da collegare agli eventi intrinseci (ad esempio, ONCLICK="button1.text='Exit'").  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT AddScriptlet(  
    LPCOLESTR pstrDefaultName,       // address of default name of scriptlet  
    LPCOLESTR pstrCode,              // address of scriptlet text  
    LPCOLESTR pstrItemName,          // address of item name  
    LPCOLESTR pstrSubItemName,       // address of subitem name  
    LPCOLESTR pstrEventName,         // address of event name  
    LPCOLESTR pstrDelimiter,         // address of end-of-scriptlet delimiter  
    DWORD_PTR dwSourceContextCookie, // application-defined value for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // scriptlet flags  
    BSTR *pbstrName,                 // address of actual name of scriptlet  
    EXCEPINFO *pexcepinfo            // address of exception information  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pstrDefaultName`  
 [in] Indirizzo di un nome predefinito per associare lo scriptlet. Se lo scriptlet non contiene informazioni sulla denominazione (come nell'esempio ONCLICK precedente), questo nome verrà utilizzato per identificare lo scriptlet. Se questo parametro è `NULL`, il motore di script produce un nome univoco, se necessario.  
  
 `pstrCode`  
 [in] Indirizzo del testo scriptlet da aggiungere. L'interpretazione di questa stringa varia a seconda del linguaggio di script.  
  
 `pstrItemName`  
 [in] Indirizzo di un buffer che contiene il nome dell'elemento associato a questo scriptlet. Questo parametro, oltre a `pstrSubItemName`, identifica l'oggetto per cui lo scriptlet è un gestore eventi.  
  
 `pstrSubItemName`  
 [in] Indirizzo di un buffer che contiene il nome di un `subobject` dell'elemento di nome con cui è associato questo scriptlet; questo nome deve essere trovato nelle informazioni sul tipo di elemento denominato. Questo parametro è NULL, se lo scriptlet deve essere associato all'elemento denominato anziché un `subitem`. Questo parametro, oltre a `pstrItemName`, identifica l'oggetto specifico per il quale lo scriptlet è un gestore eventi.  
  
 `pstrEventName`  
 [in] Indirizzo di un buffer che contiene il nome dell'evento per il quale lo scriptlet è un gestore eventi.  
  
 `pstrDelimiter`  
 [in] Indirizzo del delimitatore di fine-scriptlet. Quando il `pstrCode` parametro viene analizzato da un flusso di testo, l'host Usa in genere un delimitatore, ad esempio due virgolette singole ("), per individuare la fine dello scriptlet. Questo parametro specifica il delimitatore che l'host utilizzato, consentendo il motore di script fornire alcuni condizionale primitivi pre-elaborazione (ad esempio, sostituendo una virgoletta singola ['] con due virgolette singole per l'utilizzo come un delimitatore). Esattamente come (e se) di scripting rende motore uso di queste informazioni dipende dal motore di script. Impostare questo parametro su NULL se l'host non ha utilizzato un delimitatore per contrassegnare la fine dello scriptlet.  
  
 `dwSourceContextCookie`  
 [in] Valore definito dall'applicazione che viene utilizzato a scopo di debug.  
  
 `ulStartingLineNumber`  
 [in] Valore in base zero che specifica la riga in cui l'analisi in modo che inizi.  
  
 `dwFlags`  
 [in] Flag associati lo scriptlet. Può essere una combinazione dei valori seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|SCRIPTTEXT_ISVISIBLE|Indica che il testo dello script deve essere visibile (e, pertanto, può essere chiamato dal nome) come un metodo globale nello spazio dei nomi dello script.|  
|SCRIPTTEXT_ISPERSISTENT|Indica che il codice aggiunto durante la chiamata deve essere salvato se il motore di script viene salvato (ad esempio, tramite una chiamata a `IPersist*::Save`), o se il motore di script viene reimpostato tramite una transizione allo stato inizializzato. Per ulteriori informazioni su questo stato, vedere gli stati di motore di Script.|  
  
 `pbstrName` ,  
 [out] Nome utilizzato per identificare lo scriptlet effettivo. Questa operazione deve essere in ordine di preferenza: il testo di scriptlet specificato in modo esplicito un nome, il nome predefinito fornito `pstrDefaultName`, o un nome univoco sintetizzato dal motore di scripting.  
  
 `pexcepinfo` ,  
 [out] Indirizzo di una struttura contenente informazioni sull'eccezione. Questa struttura deve essere compilata se viene restituito DISP_E_EXCEPTION.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Operazione completata.|  
|`DISP_E_EXCEPTION`|Un'eccezione durante l'analisi dello scriptlet. Il `pexcepinfo` parametro contiene informazioni sull'eccezione.|  
|`E_INVALIDARG`|Un argomento non valido.|  
|`E_NOTIMPL`|Questo metodo non è supportato. il motore di script non supporta l'aggiunta di scriptlet sink di evento.|  
|`E_POINTER`|È stato specificato un puntatore non valido.|  
|`E_UNEXPECTED`|La chiamata non era previsto (ad esempio, il motore di script non è ancora caricato o inizializzato) e pertanto non è riuscita.|  
|`OLESCRIPT_E_INVALIDNAME`|Il nome predefinito fornito non è valido in questo linguaggio di scripting.|  
|`OLESCRIPT_E_SYNTAX`|Si è verificato un errore di sintassi non specificato nello scriptlet.|  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)