---
title: IDiaSymbol::get_undecoratedNameEx | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_undecoratedNameEx method
ms.assetid: 579aed0b-c57d-41a1-a94a-3bf665fd4a9d
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 82d0b25b2306cc957015ec4c205a22cd44660357
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolgetundecoratednameex"></a>IDiaSymbol::get_undecoratedNameEx
Recupera o parte di un nome non decorato di C++ decorati nome (collegamento).  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_undecoratedNameEx(   
   DWORD undecorateOptions,  
   BSTR* pRetval  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `undecoratedOptions`  
 [in] Specifica una combinazione di flag che controllano ciò che viene restituito. Vedere la sezione Osservazioni per i valori specifici e le operazioni eseguite.  
  
 `pRetVal`  
 [out] Restituisce che il nome non decorato di C++ nome decorato.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
> [!NOTE]
>  Valore restituito di `S_FALSE` significa che la proprietà non è disponibile per il simbolo.  
  
## <a name="remarks"></a>Note  
 Il `undecorateOptions` può essere una combinazione dei flag seguenti.  
  
> [!NOTE]
>  I nomi di flag non sono definiti in DIA SDK, pertanto è necessario aggiungere le dichiarazioni per codice oppure utilizzare i valori non elaborati.  
  
|Flag|Valore|Descrizione|  
|----------|-----------|-----------------|  
|UNDNAME_COMPLETE|0x0000|Consente di undecoration completo.|  
|UNDNAME_NO_LEADING_UNDERSCORES|0x0001|Rimuove i caratteri di sottolineatura di iniziali da parole chiave estese Microsoft.|  
|UNDNAME_NO_MS_KEYWORDS|0x0002|Disabilita l'espansione delle parole chiave estese Microsoft.|  
|UNDNAME_NO_FUNCTION_RETURNS|0x0004|Disabilita l'espansione di un tipo restituito per la dichiarazione primario.|  
|UNDNAME_NO_ALLOCATION_MODEL|0x0008|Disabilita l'espansione del modello di dichiarazione.|  
|UNDNAME_NO_ALLOCATION_LANGUAGE|0x0010|Disabilita l'espansione dell'identificatore di lingua di dichiarazione.|  
|UNDNAME_RESERVED1|0x0020|RISERVATO.|  
|UNDNAME_RESERVED2|0x0040|RISERVATO.|  
|UNDNAME_NO_THISTYPE|0x0060|Disabilita tutti i modificatori nel `this` tipo.|  
|UNDNAME_NO_ACCESS_SPECIFIERS|0x0080|Disabilita l'espansione di identificatori di accesso per i membri.|  
|UNDNAME_NO_THROW_SIGNATURES|0x0100|Disabilita l'espansione di "throw-firme" per le funzioni e i puntatori a funzioni.|  
|UNDNAME_NO_MEMBER_TYPE|0x0200|Disabilita l'espansione di `static` o `virtual` membri.|  
|UNDNAME_NO_RETURN_UDT_MODEL|0x0400|Disabilita l'espansione del modello di Microsoft per tipo definito dall'utente restituisce.|  
|UNDNAME_32_BIT_DECODE|0x0800|Undecorates nomi decorati a 32 bit.|  
|UNDNAME_NAME_ONLY|0x1000|Ottiene solo il nome per la dichiarazione primario. Restituisce semplicemente [ambito::] nome.  Consente di espandere i parametri di modello.|  
|UNDNAME_TYPE_ONLY|0x2000|Input è solo un tipo di codifica. compone un dichiaratore astratto.|  
|UNDNAME_HAVE_PARAMETERS|0x4000|Sono disponibili i parametri di modello reali.|  
|UNDNAME_NO_ECSU|0x8000|Elimina enum, classe o struct/unione.|  
|UNDNAME_NO_IDENT_CHAR_CHECK|0x10000.|Elimina controllo per i caratteri di identificatore valido.|  
|UNDNAME_NO_PTR64|0x20000|Non include ptr64 nell'output.|  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)