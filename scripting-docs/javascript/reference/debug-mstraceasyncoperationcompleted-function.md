---
title: Funzione debug. mstraceasyncoperationcompleted | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 9b628b71-61f1-478a-857f-5e1f607db56c
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 41370257042a2de50d21eba51c299198a6bfb72a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="debugmstraceasyncoperationcompleted-function"></a>Funzione Debug.msTraceAsyncOperationCompleted
Indica il completamento di un'operazione asincrona.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Debug.msTraceAsyncOperationCompleted(asyncOperationId, status)  
```  
  
#### <a name="parameters"></a>Parametri  
 `asyncOperationId`  
 Obbligatorio. ID associato a un'operazione asincrona.  
  
 `status`  
 Facoltativo. Stato dell'operazione asincrona. Se omesso, viene utilizzato `Debug.MS_ASYNC_OP_STATUS_SUCCESS`.  
  
## <a name="remarks"></a>Note  
 Chiamare questa funzione quando l'operazione asincrona viene completata.  
  
 `asyncOperationId` deve corrispondere all'ID dell'operazione precedentemente restituito da `Debug.msTraceAsyncOperationStarting`.  
  
 I valori possibili per `status` includono:  
  
-   `Debug.MS_ASYNC_OP_STATUS_SUCCESS`  
  
-   `Debug.MS_ASYNC_OP_STATUS_CANCELED`  
  
-   `Debug.MS_ASYNC_OP_STATUS_ERROR`  
  
> [!NOTE]
>  Alcuni strumenti di debug non visualizzano le informazioni inviate al debugger.  
  
## <a name="example"></a>Esempio  
 Il codice riportato di seguito fornisce un esempio di traccia di una chiamata asincrona per un'app di [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
```JavaScript  
function asyncWrapperFunction() {  
    var opID = Debug.msTraceAsyncOperationStarting('async trace');  
    doSomethingAsync().then(function (result) {  
        Debug.msTraceAsyncOperationCompleted(opID, Debug.MS_ASYNC_OP_STATUS_SUCCESS);  
        Debug.msTraceAsyncCallbackStarting(opID);  
        // Process result of async operation.  
    }, function (error) {  
        Debug.msTraceAsyncOperationCompleted(opID, Debug.MS_ASYNC_OP_STATUS_ERROR);  
        Debug.msTraceAsyncCallbackStarting(opID);  
    });  
  
    Debug.msTraceAsyncCallbackCompleted();  
}  
  
function doSomethingAsync() {  
    return WinJS.Promise.as(true);  
}  
  
asyncWrapperFunction();  
```  
  
## <a name="requirements"></a>Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]