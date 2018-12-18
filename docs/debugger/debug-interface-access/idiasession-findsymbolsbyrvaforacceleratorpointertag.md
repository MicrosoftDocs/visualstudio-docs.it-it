---
title: IDiaSession::findSymbolsByRVAForAcceleratorPointerTag | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: a073cc45-0c7b-417e-b5fc-a3b08beccdbc
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2156aeec1f8e1b6b2f3670111946acf3e69392e9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idiasessionfindsymbolsbyrvaforacceleratorpointertag"></a>IDiaSession::findSymbolsByRVAForAcceleratorPointerTag
Dato un valore di tag corrispondente, questo metodo restituisce un'enumerazione di simboli contenuti in una funzione di stub di tasti di scelta rapida padre specificato da un indirizzo virtuale relativo specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT findSymbolsByRVAForAcceleratorPointerTag (   
   IDiaSymbol*           parent,  
   DWORD                 tagValue,  
   DWORD                 rva,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `parent`  
 [in] Un `IDiaSymbol` che corrisponde alla funzione stub tasti di scelta rapida per eseguire la ricerca.  
  
 `tagValue`  
 [in] Il valore del tag puntatore.  
  
 `rva`  
 [in] L'indirizzo virtuale relativo.  
  
 `ppResult`  
 [out] Un puntatore a un `IDiaEnumSymbols` puntatore a interfaccia che viene inizializzato con il risultato.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Chiamare questo metodo solo in un `IDiaSymbol` interfaccia che corrisponde a una funzione di stub di tasti di scelta rapida.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)