---
title: IActiveScriptParseProcedureOld::ParseProcedureText | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParseProcedureOld.ParseProcedureText
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptParseProcedureOld::ParseProcedureText
ms.assetid: 21a21313-35ce-432d-b9a6-7999065f19ac
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cab546deb390535fa8ff71e116a0ad42d33cc104
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparseprocedureoldparseproceduretext"></a>IActiveScriptParseProcedureOld::ParseProcedureText
Analizza la routine di codice specificato e aggiunge una routine anonima per lo spazio dei nomi.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT ParseProcedureText(  
   LPCOLESTR    pstrCode,  
   LPCOLESTR    pstrFormalParams,  
   LPCOLESTR    pstrItemName,  
   IUnknown*    punkContext,  
   LPCOLESTR    pstrDelimiter,  
   DWORD_PTR    dwSourceContextCookie,  
   ULONG        ulStartingLineNumber,  
   DWORD        dwFlags,  
   IDispatch**  ppdisp  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pstrCode`  
 [in] Il testo della stored procedure da valutare. L'interpretazione di questa stringa varia a seconda del linguaggio di script.  
  
 `pstrFormalParams`  
 [in] Nomi di parametri formali per la procedura. I nomi di parametro devono essere separati da delimitatori appropriati per il motore di script. I nomi non devono essere racchiusi tra parentesi.  
  
 `pstrItemName`  
 [in] Il nome dell'elemento denominata che fornisce il contesto in cui la procedura è da valutare. Se questo parametro è `NULL`, il codice viene valutato nel contesto globale del motore di script.  
  
 `punkContext`  
 [in] L'oggetto di contesto. Questo oggetto è riservato per l'utilizzo in un ambiente di debug, in questo contesto può essere fornito dal debugger per rappresentare un contesto di runtime attivo. Se questo parametro è `NULL`, il motore utilizza `pstrItemName` per identificare il contesto.  
  
 `pstrDelimiter`  
 [in] Il delimitatore di fine di procedura. Quando `pstrCode` viene analizzata da un flusso di testo, l'host in genere viene utilizzato un delimitatore, ad esempio due virgolette singole ("), per rilevare la fine della routine. Questo parametro specifica il delimitatore che l'host utilizzato, consentendo di fornire alcuni condizionale, il motore di script di pre-elaborazione primitivi (ad esempio, la sostituzione di una virgoletta singola ['] con due virgolette singole per l'utilizzo come un delimitatore). Esattamente come (e se) utilizzati dal motore scripting questa informazioni dipendono dal motore di script. Impostare questo parametro su `NULL` se l'host non ha utilizzato un delimitatore per contrassegnare la fine della procedura.  
  
 `dwSourceContextCookie`  
 [in] Valore definito dall'applicazione che viene utilizzato a scopo di debug.  
  
 `ulStartingLineNumber`  
 [in] Valore in base zero che specifica la riga in cui verrà avviata l'analisi.  
  
 `dwFlags`  
 [in] Flag associati con la procedura. Può essere una combinazione di questi valori.  
  
|Costante|Valore|Significato|  
|--------------|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|0x00000020|Indica che il codice in `pstrCode` è un'espressione che rappresenta il valore restituito della procedura.|  
|SCRIPTPROC_IMPLICIT_THIS|0x00000100|Indica che il `this` puntatore è incluso nell'ambito della procedura.|  
|SCRIPTPROC_IMPLICIT_PARENTS|0x00000200|Indica che ai padri di `this` puntatore sono inclusi nell'ambito della procedura.|  
  
 `ppdisp`  
 [out] Restituisce un wrapper di distribuzione in cui il metodo predefinito è la procedura analizzata da questo metodo.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_INVALIDARG`|Un argomento non valido.|  
|`E_POINTER`|È stato specificato un puntatore non valido.|  
|`E_NOTIMPL`|Questo metodo non è supportato. Il motore di script non supporta l'aggiunta in fase di esecuzione delle procedure per lo spazio dei nomi.|  
|`E_UNEXPECTED`|La chiamata non era previsto (ad esempio, il motore di script è in stato non inizializzato o chiuso).|  
|`OLESCRIPT_E_SYNTAX`|Si è verificato un errore di sintassi non specificato nella procedura.|  
|`S_FALSE`|Il motore di script non supporta un oggetto di distribuzione. il `ppdisp`parametro è impostato su `NULL`.|  
  
## <a name="remarks"></a>Note  
 Nessun codice di script viene valutato durante la chiamata; invece, la procedura viene compilata in un metodo su `ppdisp` in cui può essere chiamato dallo script in un secondo momento.  
  
 Questa interfaccia è deprecata a favore del `IActiveScriptParseProcedure` interfaccia. Il `IActiveScriptParseProcedure::ParseProcedureText` metodo è simile a questo metodo, ma consente di specificare il nome di procedura. In tutti i casi, `IActiveScriptParseProcedure::ParseProcedureText` deve essere utilizzato.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptParseProcedureOld](../../winscript/reference/iactivescriptparseprocedureold-interface.md)   
 [IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)