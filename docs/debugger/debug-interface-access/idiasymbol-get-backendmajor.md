---
description: Recupera il numero di versione principale del back-end del compilatore.
title: IDiaSymbol::get_backEndMajor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_backEndMajor method
ms.assetid: 900a05dd-c29b-44ad-b46b-f43bda819a66
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1ead97e4fd347829f202dc60d136178414f25d5a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156489"
---
# <a name="idiasymbolget_backendmajor"></a>IDiaSymbol::get_backEndMajor
Recupera il numero di versione principale del back-end del compilatore.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_backEndMajor ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Restituisce il numero di versione principale del back-end. Vedere la sezione Osservazioni.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` o codice di errore.

> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Commenti
 Un compilatore è in genere costituito da due elementi primari: il front-end (il parser), che gestisce l'analisi del codice sorgente in un form intermedio e un back-end (Generatore di codice), che converte il modulo intermedio in assembly. Non è insolito che il front-end disponga di una versione diversa da quella del back-end.

 Un numero di versione front-end o back-end è costituito da tre parti: \<major> . \<minor> . \<build> , dove \<major> è il numero di versione principale, \<minor> è il numero di versione secondario e \<build> è il numero di Build. Ad esempio, 13.10.3077.

## <a name="requirements"></a>Requisiti

|Requisito|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2. h|
|Version:|DIA SDK v7.0|

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
