---
title: Idiaenumsegments | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::get_Count method
ms.assetid: c62a0fda-17b8-4cf6-b321-6014ce581096
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eac1b6d88917ca94db82a3e4e8c20c4be3060560
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62833197"
---
# <a name="idiaenumsegmentsgetcount"></a>IDiaEnumSegments::get_Count
Recupera il numero di segmenti.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_Count ( 
   LONG* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 pRetVal
- [out, retval] Restituisce il numero di segmenti.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)
- [IDiaEnumSegments::Item](../../debugger/debug-interface-access/idiaenumsegments-item.md)