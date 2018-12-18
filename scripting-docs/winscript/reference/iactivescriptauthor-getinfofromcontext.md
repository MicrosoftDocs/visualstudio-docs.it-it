---
title: IActiveScriptAuthor::GetInfoFromContext | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptAuthor.GetInfoFromContext
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptAuthor::GetInfoFromContext
ms.assetid: 9891b095-6eb5-4473-87c0-c2e5cd2afc1a
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 27c13dbe51bb1150554275b5fbeacd00be2e445f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorgetinfofromcontext"></a>IActiveScriptAuthor::GetInfoFromContext
Restituisce tipo di informazioni e le posizioni di ancoraggio di un carattere specificato in un blocco di codice. Fornisce informazioni per il membro IntelliSense, gli elenchi globali e suggerimenti relativi ai parametri.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetInfoFromContext(  
   LPCOLESTR  pszCode,  
   ULONG      cchCode,  
   ULONG      ichCurrentPosition,  
   DWORD      dwListTypesRequested,  
   DWORD      *pdwListTypesProvided,  
   ULONG      *pichListAnchorPosition,  
   ULONG      *pichFuncAnchorPosition,  
   MEMBERID   *pmemid,  
   LONG       *piCurrentParameter,  
   IUnknown   **ppunk  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pszCode`  
 [in] L'indirizzo della stringa di blocco di codice usata per generare i risultati di informazioni.  
  
 `cchCode`  
 [in] La lunghezza del blocco di codice.  
  
 `ichCurrentPosition`  
 [in] Posizione del carattere relativo all'inizio del blocco.  
  
 `dwListTypesRequested`  
 [in] I tipi di elenco richiesti. Può essere una combinazione dei valori seguenti:  
  
|Costante|Valore|Descrizione|  
|--------------|-----------|-----------------|  
|SCRIPT_CMPL_NOLIST|0x0000|Nessun elenco.|  
|SCRIPT_CMPL_MEMBERLIST|0x0001|Elenco dei membri.|  
|SCRIPT_CMPL_ENUMLIST|0x0002|Elenco di enumerazione.|  
|SCRIPT_CMPL_PARAMLIST|0x0004|Chiamare l'elenco di parametri di metodo.|  
|SCRIPT_CMPL_GLOBALLIST|0x0008|Elenco globale.|  
  
 Il tipo SCRIPT_CMPL_GLOBALLIST viene trattato come un elemento di completamento predefinito che può essere combinato utilizzando l'operatore OR con altri elementi di completamento. Lo script di creazione prima motore tenta di popolare le informazioni sul tipo per altri elementi dell'elenco di completamento. Se il problema persiste, il motore viene popolato per SCRIPT_CMPL_GLOBALLIST.  
  
 `pdwListTypesProvided`  
 [out] Il tipo di elenco fornito.  
  
 `pichListAnchorPosition`  
 [out] Indice iniziale del contesto che contiene la posizione corrente. L'indice iniziale è relativo all'inizio del blocco.  
  
 Viene popolato solo quando `dwListTypesRequested` include SCRIPT_CMPL_MEMBERLIST, SCRIPT_CMPL_ENUMLIST o SCRIPT_CMPL_GLOBALLIST. Per altri tipi di elenco richiesto, il risultato è indefinito.  
  
 `pichFuncAnchorPosition`  
 [out] Indice iniziale della chiamata di funzione che contiene la posizione corrente. L'indice iniziale è relativo all'inizio del blocco.  
  
 Viene popolato solo quando il contesto che contiene la posizione corrente è una chiamata di funzione e quando `dwListTypesRequested` include SCRIPT_CMPL_PARAMLIST. In caso contrario, il risultato è indefinito.  
  
 `pmemid`  
 [out] MEMBERID della funzione, come definito da un tipo nel `IProvideMultipleClassInfo``ppunk` parametro out.  
  
 Viene popolato solo quando `dwListTypesRequested` include SCRIPT_CMPL_PARAMLIST.  
  
 `piCurrentParameter`  
 [out] L'indice del parametro che contiene la posizione corrente. Se la posizione corrente è sul nome della funzione, viene restituito -1.  
  
 Il `piCurrentParameter` valore viene popolato solo quando `dwListTypesRequested` include SCRIPT_CMPL_PARAMLIST.  
  
 `ppunk`  
 Le informazioni sul tipo, che viene forniti sotto forma di un `IProvideMultipleClassInfo` oggetto.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IProvideMultipleClassInfo](https://msdn.microsoft.com/library/microsoft.visualstudio.ole.interop.iprovidemultipleclassinfo.aspx)   
 [Interfaccia IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)