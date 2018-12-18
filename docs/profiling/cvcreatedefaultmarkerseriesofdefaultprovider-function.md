---
title: Funzione CvCreateDefaultMarkerSeriesOfDefaultProvider | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: cvmarkers/CvCreateDefaultMarkerSeriesOfDefaultProvider
helpviewer_keywords: CvCreateDefaultMarkerSeriesOfDefaultProvider method
ms.assetid: 24eb80f8-8fca-4c47-93b5-bb1eb8ffdffd
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3fae064fab478de88f6b5f66c41df7e4e57d4ead
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
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
 [C++ Library Reference](../profiling/cpp-library-reference.md) (Riferimento alla libreria C++)