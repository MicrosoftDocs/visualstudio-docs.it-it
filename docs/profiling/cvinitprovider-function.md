---
title: Funzione CvInitProvider | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: cvmarkers/CvInitProvider
helpviewer_keywords: CvInitProvider method
ms.assetid: ba1863ad-e35f-4d34-a2f2-5e68957d1915
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 15abebb58382674bc7943d7949dfddbc62524c91
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="cvinitprovider-function"></a>Funzione CvInitProvider
Inizializza il provider di marcatori. Deve essere chiamata prima di qualsiasi altra funzione SDK del visualizzatore di concorrenza.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT CvInitProvider(  
   _In_ const GUID* pGuid,  
   _Out_ PCV_PROVIDER* ppProvider  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pGuid`  
 GUID del provider. Non può essere NULL.  
  
 `ppProvider`  
 Indirizzo di una variabile di output in cui verrà archiviato il contesto del provider. Non può essere NULL.  
  
## <a name="return-value"></a>Valore restituito  
 S_OK quando il provider è stato inizializzato correttamente oppure codice dell'errore nel caso in cui si siano verificati errori. Usare le macro SUCCEEDED/FAILED per controllare la condizione di errore.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** cvmarkers.h  
  
## <a name="see-also"></a>Vedere anche  
 [C++ Library Reference](../profiling/cpp-library-reference.md) (Riferimento alla libreria C++)