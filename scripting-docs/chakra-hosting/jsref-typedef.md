---
title: Typedef JsRef | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 6aafc39f-6b9c-457f-8bf0-48831bffe9b8
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d9d4c478a45f53e83dfa59fdde21cfa4c988c92e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jsref-typedef"></a>Typedef JsRef
Un riferimento a un oggetto di proprietà del Garbage Collector di Chakra.  
  
## <a name="syntax"></a>Sintassi  
  
```  
typedef void *JsRef;  
```  
  
## <a name="remarks"></a>Note  
 Nel runtime di Chakra vengono rilevati automaticamente i riferimenti a JsRef finché sono memorizzati nelle variabili locali o nei parametri, cioè nello stack. Per archiviare un JsRef in una posizione diversa rispetto allo stack è necessario chiamare JsRef e JsRelease per gestire la durata dell'oggetto. In caso contrario il Garbage Collector potrebbe cancellare l'oggetto dalla memoria mentre è ancora in uso.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jsrt.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti (Runtime JavaScript)](../chakra-hosting/reference-javascript-runtime.md)