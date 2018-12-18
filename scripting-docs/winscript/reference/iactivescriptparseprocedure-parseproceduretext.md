---
title: IActiveScriptParseProcedure::ParseProcedureText | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParseProcedure.ParseProcedureText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParseProcedure_ParseProcedureText
ms.assetid: 345a74ae-b4e8-42b2-abd8-633a370e8e7f
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c2a877f6ebc692f9f54d69597e06db501f642802
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparseprocedureparseproceduretext"></a>IActiveScriptParseProcedure::ParseProcedureText
Analizza la routine di codice specificato e aggiunge la procedura per lo spazio dei nomi.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT ParseProcedureText(  
    LPCOLESTR pstrCode,              // address of procedure text  
    LPCOLESTR pstrFormalParams,      // address of formal parameter names  
    LPCOLESTR pstrProcedureName,     // address of procedure name  
    LPCOLESTR pstrItemName,          // address of item name  
    IUnknown *punkContext,           // address of debugging context  
    LPCOLESTR pstrDelimiter,         // address of end-of-procedure delimiter  
    DWORD_PTR dwSourceContextCookie, // application-defined value for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // procedure flags  
    IDispatch **ppdisp               // receives IDispatch pointer  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pstrCode`  
 [in] Indirizzo del testo routine da valutare. L'interpretazione di questa stringa varia a seconda del linguaggio di script.  
  
 `pstrFormalParams`  
 [in] Indirizzo di nomi di parametri formali per la procedura. I nomi di parametro devono essere separati da delimitatori appropriati per il motore di script. I nomi non devono essere racchiusi tra parentesi.  
  
 `pstrProcedureName`  
 [in] Indirizzo del nome della stored procedure deve essere analizzato.  
  
 `pstrItemName`  
 [in] Indirizzo del nome dell'elemento che fornisce il contesto in cui la procedura è da valutare. Se questo parametro è `NULL`, il codice viene valutato nel contesto globale del motore di script.  
  
 `punkContext`  
 [in] Indirizzo dell'oggetto di contesto. Questo oggetto è riservato per l'utilizzo in un ambiente di debug, in questo contesto può essere fornito dal debugger per rappresentare un contesto di runtime attivo. Se questo parametro è `NULL`, il motore utilizza `pstrItemName` per identificare il contesto.  
  
 `pstrDelimiter`  
 [in] Indirizzo del delimitatore finale di procedura. Quando `pstrCode` viene analizzata da un flusso di testo, l'host in genere viene utilizzato un delimitatore, ad esempio due virgolette singole ("), per rilevare la fine della routine. Questo parametro specifica il delimitatore che l'host utilizzato, consentendo il motore di script fornire alcuni condizionale primitivi pre-elaborazione (ad esempio, sostituendo una virgoletta singola ['] con due virgolette singole per l'utilizzo come un delimitatore). Esattamente come (e se) di scripting rende motore uso di queste informazioni dipende dal motore di script. Impostare questo parametro su `NULL` se l'host non ha utilizzato un delimitatore per contrassegnare la fine della procedura.  
  
 `dwSourceContextCookie`  
 [in] Valore definito dall'applicazione che viene utilizzato a scopo di debug.  
  
 `ulStartingLineNumber`  
 [in] Valore in base zero che specifica la riga in cui l'analisi in modo che inizi.  
  
 `dwFlags`  
 [in] Flag associati con la procedura. Può essere una combinazione dei valori seguenti:  
  
|Valore|Significato|  
|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|Indica che il codice in `pstrCode` è un'espressione che rappresenta il valore restituito della procedura. Per impostazione predefinita, il codice può contenere un'espressione, un elenco di istruzioni o qualsiasi elemento in caso contrario è consentito in una stored procedure per il linguaggio di scripting.|  
|SCRIPTPROC_IMPLICIT_THIS|Indica che il `this` puntatore è incluso nell'ambito della procedura.|  
|SCRIPTPROC_IMPLICIT_PARENTS|Indica che ai padri di `this` puntatore sono inclusi nell'ambito della procedura.|  
  
 `ppdisp`  
 [out] Indirizzo del puntatore per l'oggetto che contiene le proprietà e metodi globali lo script. Se il motore di script non supporta tale tipo di oggetto, `NULL` viene restituito.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Operazione completata.|  
|`E_INVALIDARG`|Un argomento non valido.|  
|`E_POINTER`|È stato specificato un puntatore non valido.|  
|`E_NOTIMPL`|Questo metodo non è supportato. Il motore di script non supporta l'aggiunta in fase di esecuzione delle procedure per lo spazio dei nomi.|  
|`E_UNEXPECTED`|La chiamata non era previsto (ad esempio, il motore di script è in stato non inizializzato o chiuso).|  
|`OLESCRIPT_E_SYNTAX`|Si è verificato un errore di sintassi non specificato nella procedura.|  
|`S_FALSE`|Il motore di script non supporta un oggetto di distribuzione. il `ppdisp` parametro è impostato su `NULL`.|  
  
## <a name="remarks"></a>Note  
 Nessun codice di script viene valutato durante la chiamata; invece, la procedura viene compilata allo stato di script in cui può essere chiamato dallo script in un secondo momento.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)