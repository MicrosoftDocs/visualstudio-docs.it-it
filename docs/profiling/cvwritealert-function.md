---
title: Funzione CvWriteAlert | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvWriteAlertVA
- cvmarkers/CvWriteAlertVW
- cvmarkers/CvWriteAlertA
- cvmarkers/CvWriteAlertW
helpviewer_keywords:
- CvWriteAlertVW method
- CvWriteAlertA method
- CvWriteAlertVA method
- CvWriteAlertW method
ms.assetid: 937aa9d6-278a-4df3-bef7-151441df16d5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b7cc2316168d14c6c996c4d55065771c85ffdfc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62989779"
---
# <a name="cvwritealert-function"></a>Funzione CvWriteAlert
Scrive un avviso nel file di traccia del visualizzatore di concorrenza.

## <a name="syntax"></a>Sintassi

```C
HRESULT CvWriteAlertW(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ PCWSTR pMessage,
    ...
    );

HRESULT CvWriteAlertA(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ PCSTR pMessage,
    ...
    );

HRESULT CvWriteAlertVW(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ PCWSTR pMessage,
    _In_ va_list argList);

HRESULT CvWriteAlertVA(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ PCSTR pMessage,
    _In_ va_list argList);
```

#### <a name="parameters"></a>Parametri
 `argList` Elenco di argomenti.

 `pMarkerSeries` Contesto della serie di marcatori valido. Non può essere NULL.

 `pMessage` Stringa di formato del messaggio. Non può essere NULL.

## <a name="return-value"></a>Valore restituito
 S_OK quando il messaggio è stato scritto correttamente. Codice dell'errore nel caso in cui si siano verificati errori. Usare le macro SUCCEEDED/FAILED per controllare la condizione di errore.

## <a name="requirements"></a>Requisiti
 **Intestazione:** *cvmarkers.h*

 **Unicode:** CvWriteAlertW, CvWriteAlertVW

 **ANSI:** CvWriteAlertA, CvWriteAlertVA

## <a name="see-also"></a>Vedere anche
- [Riferimento alla libreria C++](../profiling/cpp-library-reference.md)