---
title: Funzione JsAddRef | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsAddRef
helpviewer_keywords:
- JsAddRef function
ms.assetid: a7f3ed49-6a86-489a-abdf-c99428e79cae
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8e55ab6643dd949b8b41962161f76648dba926e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jsaddref-function"></a>Funzione JsAddRef
Aggiunge un riferimento a un oggetto raccolto dal Garbage Collector.  
  
## <a name="syntax"></a>Sintassi  
  
```  
STDAPI_(JsErrorCode) JsAddRef(  
   _In_ JsRef ref,  
   _Out_opt_ unsigned int *count  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ref`  
 Oggetto a cui aggiungere un riferimento.  
  
 `count`  
 Il nuovo conteggio dei riferimenti dell'oggetto (può passare il valore null).  
  
## <a name="return-value"></a>Valore restituito  
 Codice `JsNoError` se l'operazione ha avuto esito positivo; in caso contrario, un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questa operazione deve essere chiamata solo sul gestore `JsRef` che non sarà archiviato in un punto nello stack. Chiamando `JsAddRef` si garantisce che l'oggetto a cui `JsRef` si riferisce non sarà liberato finché non verrà chiamato `JsRelease`.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jsrt.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti (Runtime JavaScript)](../chakra-hosting/reference-javascript-runtime.md)