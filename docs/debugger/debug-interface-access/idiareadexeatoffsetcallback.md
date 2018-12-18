---
title: IDiaReadExeAtOffsetCallback | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtOffsetCallback interface
ms.assetid: 3c961641-3ce3-4bc3-bd6e-a802fa3bec49
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b60730a81ecc2948c51020fb7d7b4df766b93579
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="idiareadexeatoffsetcallback"></a>IDiaReadExeAtOffsetCallback
Consente a un'applicazione client fornire i byte di un file eseguibile come specificato dalla posizione del file.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDiaReadExeAtOffsetCallback : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDiaReadExeAtOffsetCallback`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDiaReadExeAtOffsetCallback::ReadExecutableAt](../../debugger/debug-interface-access/idiareadexeatoffsetcallback-readexecutableat.md)|Legge il numero specificato di byte a partire dall'offset specificato da un file eseguibile.|  
  
## <a name="remarks"></a>Note  
 L'applicazione client implementa questa interfaccia per fornire i byte del file eseguibile con un offset assoluto nel file dell'eseguibile. Per utilizzare un indirizzo virtuale relativo, implementare il [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) interfaccia.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Questo metodo viene implementato dall'applicazione client e passato al [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metodo come metodo alternativo per la lettura del file.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Dia2.h  
  
 Libreria: diaguids.lib  
  
 DLL: MSDIA80  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)