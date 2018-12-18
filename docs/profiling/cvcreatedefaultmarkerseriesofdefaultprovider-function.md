---
title: Funzione CvCreateDefaultMarkerSeriesOfDefaultProvider | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvCreateDefaultMarkerSeriesOfDefaultProvider
helpviewer_keywords:
- CvCreateDefaultMarkerSeriesOfDefaultProvider method
ms.assetid: 24eb80f8-8fca-4c47-93b5-bb1eb8ffdffd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 418acf8e296446785fb0cda5d0a97f52754050e2
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="cvcreatedefaultmarkerseriesofdefaultprovider-function"></a>Funzione CvCreateDefaultMarkerSeriesOfDefaultProvider
Crea serie di marcatori predefinite di un provider predefinito.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT CvCreateDefaultMarkerSeriesOfDefaultProvider(  
   _Out_ PCV_PROVIDER* ppProvider,  
   _Out_ PCV_MARKERSERIES* ppMarkerSeries  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppProvider`  
 Indirizzo della variabile dell'oggetto provider. L'indirizzo non può essere NULL, la variabile può avere qualsiasi valore.  
  
 `ppMarkerSeries`  
 Indirizzo della variabile dell'oggetto serie marcatori. L'indirizzo non può essere NULL, la variabile può avere qualsiasi valore.  
  
## <a name="return-value"></a>Valore restituito  
 S_OK quando sia il provider che la serie di marcatori vengono creati correttamente oppure codice dell'errore nel caso in cui si siano verificati errori. Usare le macro SUCCEEDED/FAILED per controllare la condizione di errore.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** cvmarkers.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla libreria C++](../profiling/cpp-library-reference.md)