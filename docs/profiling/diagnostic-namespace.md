---
title: Spazio dei nomi diagnostic | Microsoft Docs
description: Usare lo spazio dei nomi di diagnostica per creare marcatori del Visualizzatore di concorrenza. Lo spazio dei nomi di diagnostica è un membro dello spazio dei nomi Concurrency.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic
helpviewer_keywords:
- Concurrency, diagnostic namespace
ms.assetid: ad786b19-7c4c-46ee-bfb6-c4752b373a09
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 22224e375c1d1f463f1c07d41ca5a03efa5cabdb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923737"
---
# <a name="diagnostic-namespace"></a>Spazio dei nomi diagnostic
Lo spazio dei nomi `diagnostics` offre funzionalità per l'emissione di marcatori del visualizzatore di concorrenza.

## <a name="syntax"></a>Sintassi

```cpp
namespace diagnostic;
```

## <a name="members"></a>Members

### <a name="classes"></a>Classi

|Nome|Descrizione|
|----------|-----------------|
|[Classe marker_series](../profiling/marker-series-class.md)|Rappresenta un canale seriale di eventi generati da un singolo provider.|
|[Classe span](../profiling/span-class.md)|Definisce una fase dell'applicazione.|

### <a name="enumerations"></a>Enumerazioni

|Nome|Descrizione|
|----------|-----------------|
|[Enumerazione marker_importance](../profiling/marker-importance-enumeration.md)|Rappresenta il livello di importanza di un marcatore del visualizzatore di concorrenza.|

## <a name="requirements"></a>Requisiti
 **Intestazione:** *cvmarkersobj.h*

 **Spazio dei nomi:** Concorrenza

## <a name="see-also"></a>Vedi anche
- [Spazio dei nomi Concurrency (Visualizzatore di concorrenza)](../profiling/concurrency-namespace-concurrency-visualizer.md)