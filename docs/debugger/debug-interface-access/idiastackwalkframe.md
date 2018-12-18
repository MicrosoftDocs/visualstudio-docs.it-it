---
title: IDiaStackWalkFrame | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaStackWalkFrame interface
ms.assetid: 42d82845-d6f6-4846-9ecd-9dd169216077
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: eb683afe63880af9d1a666436739140519f7339b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idiastackwalkframe"></a>IDiaStackWalkFrame
Gestisce il contesto di stack tra le chiamate del [idiaframedata:: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md) metodo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDiaStackWalkFrame : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDiaStackWalkFrame`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDiaStackWalkFrame::get_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-get-registervalue.md)|Recupera il valore di un registro.|  
|[IDiaStackWalkFrame::put_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-put-registervalue.md)|Imposta il valore di un registro.|  
|[IDiaStackWalkFrame::readMemory](../../debugger/debug-interface-access/idiastackwalkframe-readmemory.md)|Legge dall'immagine della memoria.|  
|[IDiaStackWalkFrame::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddress.md)|Cerca il frame dello stack specificato per l'indirizzo restituito della funzione più vicino.|  
|[IDiaStackWalkFrame::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddressstart.md)|Cerca il frame dello stack specificato per un indirizzo del mittente in o in prossimità dell'indirizzo specificato.|  
  
## <a name="remarks"></a>Note  
 Questa interfaccia viene utilizzata durante l'esecuzione del programma per leggere e scrivere i registri, nonché accedere alla memoria e trovare indirizzi restituiti.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 L'applicazione client implementa questa interfaccia e passa un'istanza dell'interfaccia per il [idiaframedata:: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md) metodo. La stessa istanza di questa interfaccia è utilizzata più volte per mantenere lo stato dei registri durante ogni chiamata del `execute` metodo. Il `execute` metodo utilizza anche questa interfaccia per determinare l'indirizzo del mittente.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Dia2.h  
  
 Libreria: diaguids.lib  
  
 DLL: MSDIA80  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)