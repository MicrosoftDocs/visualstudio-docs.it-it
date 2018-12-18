---
title: IDiaStackWalkHelper | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaStackWalkHelper2 interface
ms.assetid: d66e5c84-565d-494e-8486-f91db9a34548
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 6cbd88bbe3e8a752721047ee80d847e72cf115b9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idiastackwalkhelper"></a>IDiaStackWalkHelper
Facilita la verifica dello stack utilizzando il file di database (con estensione pdb) di debug di programma.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
IDiaStackWalkHelper: IUnknown  
  
```  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine VTable  
 Nella tabella seguente sono illustrati i metodi di `IDiaStackWalkHelper`:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDiaStackWalkHelper::get_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-get-registervalue.md)|Recupera il valore di un registro.|  
|[IDiaStackWalkHelper::put_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-put-registervalue.md)|Imposta il valore di un registro.|  
|[IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)|Legge un blocco di dati dall'immagine del file eseguibile in memoria.|  
|[IDiaStackWalkHelper::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddress.md)|Cerca il frame dello stack specificato per l'indirizzo restituito della funzione più vicino.|  
|[IDiaStackWalkHelper::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddressstart.md)|Cerca stack frame specificato per un indirizzo del mittente in o in prossimità l'indirizzo specificato nello stack.|  
|[IDiaStackWalkHelper::frameForVA](../../debugger/debug-interface-access/idiastackwalkhelper-frameforva.md)|Recupera lo stack frame che contiene l'indirizzo virtuale specificato.|  
|[IDiaStackWalkHelper::symbolForVA](../../debugger/debug-interface-access/idiastackwalkhelper-symbolforva.md)|Recupera il simbolo che contiene l'indirizzo virtuale specificato. **Nota:** simbolo deve essere del tipo `SymTagFunctionType` (compreso il [SymTagEnum (enumerazione)](../../debugger/debug-interface-access/symtagenum.md) enumerazione).|  
|[IDiaStackWalkHelper::pdataForVA](../../debugger/debug-interface-access/idiastackwalkhelper-pdataforva.md)|Restituisce il blocco di dati PDATA associato all'indirizzo virtuale specificato.|  
|[IDiaStackWalkHelper::imageForVA](../../debugger/debug-interface-access/idiastackwalkhelper-imageforva.md)|Recupera l'indirizzo virtuale iniziale di un file eseguibile, un indirizzo virtuale in un punto nello spazio di memoria dell'eseguibile specificato.|  
  
## <a name="remarks"></a>Note  
 Questa interfaccia viene chiamata dal codice DIA per ottenere informazioni relative all'eseguibile per costruire un elenco di frame dello stack durante l'esecuzione del programma.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Un'applicazione client implementa questa interfaccia per supportare la verifica dello stack durante l'esecuzione del programma. Un'istanza di questa interfaccia viene passata per il [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) o [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) metodi.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Dia2.h  
  
 Libreria: diaguids.lib  
  
 DLL: MSDIA80  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [SymTagEnum (enumerazione)](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)   
 [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)