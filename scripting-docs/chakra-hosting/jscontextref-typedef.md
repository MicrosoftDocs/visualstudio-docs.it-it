---
title: Typedef JsContextRef | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 8586bfcc-bb24-430d-a6f2-1a3b3e34ec2e
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ec1300717b59c3b901665b39ca0102988e83e853
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jscontextref-typedef"></a>Typedef JsContextRef
Riferimento a un contesto di script.  
  
## <a name="syntax"></a>Sintassi  
  
```  
typedef JsRef JsContextRef;  
```  
  
## <a name="remarks"></a>Note  
 Ogni contesto di script contiene un oggetto globale specifico, diverso dall'oggetto globale negli altri contesti di script.  
  
 Molti Chakra che ospitano le API richiedono un contesto script "attivo", che può essere impostato con `JsSetCurrentContext`. I Chakra che ospitano le API che richiedono l'impostazione di un contesto corrente lo indicheranno in modo esplicito nella relativa documentazione.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jsrt.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti (Runtime JavaScript)](../chakra-hosting/reference-javascript-runtime.md)