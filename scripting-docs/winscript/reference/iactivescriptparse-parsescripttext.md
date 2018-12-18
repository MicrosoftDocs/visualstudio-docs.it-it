---
title: IActiveScriptParse::ParseScriptText | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParse.ParseScriptText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParse_ParseScriptText
ms.assetid: 2d237d6c-cc65-415b-8808-72791304a136
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 70d17807b47468f2238c0254cc39b339df616411
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparseparsescripttext"></a>IActiveScriptParse::ParseScriptText
Analizza lo scriptlet codice specifico, aggiungendo le dichiarazioni nello spazio dei nomi e la valutazione di codice nel modo appropriato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT ParseScriptText(  
    LPCOLESTR pstrCode,              // address of scriptlet text  
    LPCOLESTR pstrItemName,          // address of item name  
    IUnknown *punkContext,           // address of debugging context  
    LPCOLESTR pstrDelimiter,         // address of end-of-scriptlet delimiter  
    DWORD_PTR dwSourceContextCookie, // cookie for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // scriptlet flags  
    VARIANT *pvarResult,             // address of buffer for results  
    EXCEPINFO *pexcepinfo            // address of buffer for error data  
);  
```  
  
#### <a name="parameters"></a>Parametri  
  
|||  
|-|-|  
|`pstrCode`|[in] Indirizzo del testo scriptlet da valutare. L'interpretazione di questa stringa varia a seconda del linguaggio di script.|  
|`pstrItemName`|[in] Indirizzo del nome dell'elemento che fornisce il contesto in cui lo scriptlet è da valutare. Se questo parametro è NULL, il codice viene valutato nel contesto globale del motore di script.|  
|`punkContext`|[in] Indirizzo dell'oggetto di contesto. Questo oggetto è riservato per l'utilizzo in un ambiente di debug, in questo contesto può essere fornito dal debugger per rappresentare un contesto di runtime attivo. Se questo parametro è NULL, il motore utilizza `pstrItemName` per identificare il contesto.|  
|`pstrDelimiter`|[in] Indirizzo del delimitatore di fine-scriptlet. Quando `pstrCode` viene analizzata da un flusso di testo, l'host in genere viene utilizzato un delimitatore, ad esempio due virgolette singole ("), per individuare la fine dello scriptlet. Questo parametro specifica il delimitatore che l'host utilizzato, consentendo il motore di script fornire alcuni condizionale primitivi pre-elaborazione (ad esempio, sostituendo una virgoletta singola ['] con due virgolette singole per l'utilizzo come un delimitatore). Esattamente come (e se) di scripting rende motore uso di queste informazioni dipende dal motore di script. Impostare questo parametro su `NULL` se l'host non ha utilizzato un delimitatore per contrassegnare la fine dello scriptlet.|  
|`dwSourceContextCookie`|[in] Cookie utilizzato per scopi di debug.|  
|`ulStartingLineNumber`|[in] Valore in base zero che specifica la riga in cui l'analisi in modo che inizi.|  
|`dwFlags`|[in] Flag associati lo scriptlet. Può essere una combinazione dei valori seguenti:|  
  
|Valore|Significato|  
|-----------|-------------|  
|SCRIPTTEXT_ISEXPRESSION|Se la distinzione tra un'espressione di calcolo e di un'istruzione è importante, ma sintatticamente ambiguo nel linguaggio di script, questo flag specifica che lo scriptlet deve essere interpretato come un'espressione, anziché come un'istruzione o un elenco di istruzioni. Per impostazione predefinita, le istruzioni si presuppone che, a meno che la scelta corretta può essere determinata dalla sintassi del testo scriptlet.|  
|SCRIPTTEXT_ISPERSISTENT|Indica che il codice aggiunto durante la chiamata deve essere salvato se il motore di script viene salvato (ad esempio, tramite una chiamata a `IPersist*::Save`), o se il motore di script viene reimpostato tramite una transizione allo stato inizializzato.|  
|SCRIPTTEXT_ISVISIBLE|Indica che il testo dello script deve essere visibile (e, pertanto, può essere chiamato dal nome) come un metodo globale nello spazio dei nomi dello script.|  
  
|||  
|-|-|  
|`pvarResult`|[out] Indirizzo di un buffer che riceve i risultati dell'elaborazione scriptlet, o `NULL` se il chiamante prevede che nessun risultato (ovvero, il valore SCRIPTTEXT_ISEXPRESSION non è impostato).|  
|`pexcepinfo`|[out] Indirizzo di una struttura che riceve le informazioni sull'eccezione. Questa struttura viene compilata se `IActiveScriptParse::ParseScriptText` restituisce DISP_E_EXCEPTION.|  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Operazione completata.|  
|`DISP_E_EXCEPTION`|Un'eccezione durante l'elaborazione dello scriptlet. Il `pexcepinfo` parametro contiene informazioni sull'eccezione.|  
|`E_INVALIDARG`|Un argomento non valido.|  
|`E_POINTER`|È stato specificato un puntatore non valido.|  
|`E_NOTIMPL`|Questo metodo non è supportato. Il motore di script non supporta la valutazione in fase di esecuzione di istruzioni o espressioni.|  
|`E_UNEXPECTED`|La chiamata non era previsto (ad esempio, il motore di script è in stato non inizializzato o chiuso, oppure è stato impostato il flag SCRIPTTEXT_ISEXPRESSION e il motore di script si trova nello stato inizializzato).|  
|`OLESCRIPT_E_SYNTAX`|Si è verificato un errore di sintassi non specificato nello scriptlet.|  
  
## <a name="remarks"></a>Note  
 Se il motore di script è in stato inizializzato, nessun codice verrà effettivamente valutato durante questa chiamata; piuttosto, tale codice è in coda ed eseguito quando il motore di script viene eseguita la transizione in (o tramite) avviato. Poiché l'esecuzione non è consentita nello stato non inizializzato, è un errore di chiamare questo metodo con il flag SCRIPTTEXT_ISEXPRESSION quando è nello stato non inizializzato.  
  
 Lo scriptlet può essere un'espressione, un elenco di istruzioni o qualsiasi elemento consentito per il linguaggio di scripting. Ad esempio, questo metodo viene utilizzato nella valutazione del codice HTML \<SCRIPT > tag, che consente di istruzioni da eseguire quando viene creata la pagina HTML, anziché doverli solo allo stato di script.  
  
 Il codice passato a questo metodo deve essere una parte valida e completa di codice. Ad esempio, in VBScript non è consentito chiamare questo metodo una volta con Sub Function e quindi una seconda volta con `End Sub`. Il parser non deve attendere la seconda chiamata a completare la subroutine, ma è invece necessario generare un errore di analisi perché una dichiarazione di una subroutine è stata avviata ma non completata.  
  
 Per ulteriori informazioni sugli stati di script, vedere la sezione di stati di motore di Script di [motori di Script Windows](../../winscript/windows-script-engines.md).  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)