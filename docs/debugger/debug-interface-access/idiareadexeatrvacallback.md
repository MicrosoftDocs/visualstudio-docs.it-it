---
description: Consente a un'applicazione client di fornire byte di un file eseguibile come specificato da un indirizzo virtuale relativo.
title: IDiaReadExeAtRVACallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtRVACallback interface
ms.assetid: b2892513-3952-4f99-9b98-60cb9b1fdc91
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a8efb088012af4fbcba259182465d53ee7ce8eac
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148045"
---
# <a name="idiareadexeatrvacallback"></a>IDiaReadExeAtRVACallback
Consente a un'applicazione client di fornire byte di un file eseguibile come specificato da un indirizzo virtuale relativo.

## <a name="syntax"></a>Sintassi

```
IDiaReadExeAtRVACallback : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 La tabella seguente illustra i metodi di `IDiaReadExeAtRVACallback` .

|Metodo|Descrizione|
|------------|-----------------|
|[IDiaReadExeAtRVACallback::ReadExecutableAtRVA](../../debugger/debug-interface-access/idiareadexeatrvacallback-readexecutableatrva.md)|Legge il numero specificato di byte a partire dall'indirizzo RVA (relative Virtual Address) specificato dal file eseguibile.|

## <a name="remarks"></a>Commenti
 L'applicazione client implementa questa interfaccia per fornire i byte del file eseguibile usando un indirizzo virtuale relativo nel file dell'eseguibile. Per usare un offset assoluto dei file, implementare l'interfaccia [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) .

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questo metodo viene implementato dall'applicazione client e passato al metodo [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) come metodo alternativo per la lettura del file.

## <a name="requirements"></a>Requisiti
 Intestazione: dia2. h

 Libreria: diaguids. lib

 DLL: msdia80.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
