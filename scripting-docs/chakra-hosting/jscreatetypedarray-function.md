---
title: Funzione JsCreateTypedArray | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 937a2a91-6f5f-4aaa-a018-d3089702bf36
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1df33d0e1aadec9d7ed5aebf743e2c2f840e51fd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="jscreatetypedarray-function"></a>Funzione JsCreateTypedArray
Crea un oggetto matrice tipizzata JavaScript.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
STDAPI_(JsErrorCode) JsCreateTypedArray(  
   _In_ JsTypedArrayType arrayType,  
   _In_ JsValueRef baseArray,  
   _In_ unsigned int byteOffset,  
   _In_ unsigned int elementLength,  
   _Out_ JsValueRef *result  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `arrayType`  
 Tipo della matrice da creare.  
  
 `baseArray`  
 Matrice di base della nuova matrice. Usare `JS_INVALID_REFERENCE` se non esiste alcuna matrice di base.  
  
 `byteOffset`  
 Offset in byte a partire dall'inizio di `baseArray`  (`ArrayBuffer`) a cui deve fare riferimento la matrice tipizzata del risultato. Applicabile solo se `baseArray` è un oggetto `ArrayBuffer`; in caso contrario, deve essere 0.  
  
 `elementLength`  
 Numero di elementi nella matrice. Applicabile solo quando si crea una nuova matrice tipizzata senza `baseArray` (`baseArray` è `JS_INVALID_REFERENCE`) o quando `baseArray` è un oggetto `ArrayBuffer`; in caso contrario, deve essere 0.  
  
 `result`  
 Nuovo oggetto matrice tipizzata.  
  
## <a name="return-value"></a>Valore restituito  
 Codice `JsNoError` se l'operazione ha avuto esito positivo; in caso contrario, un codice di errore.  
  
## <a name="remarks"></a>Note  
 `baseArray` può essere un elemento `ArrayBuffer`, un'altra matrice tipizzata o un elemento `Array` JavaScript. La matrice tipizzata restituita userà `baseArray` se è un elemento `ArrayBuffer`; in caso contrario, creerà e userà una copia della matrice di origine sottostante.  
  
 Richiede un contesto di script attivo.  
  
 Questa API è supportata solo in modalità Edge.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jsrt.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti (Runtime JavaScript)](../chakra-hosting/reference-javascript-runtime.md)