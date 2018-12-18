---
title: Funzione debug. mstraceasynccallbackstarting | Documenti Microsoft
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
ms.assetid: 0e2ca7c4-103c-44f2-b76c-102fb1e42543
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 49203cdf16e7cbd74493c882d9cf17b7629da79a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="debugmstraceasynccallbackstarting-function"></a>Funzione Debug.msTraceAsyncCallbackStarting
Associa lo stack di callback a un'operazione asincrona specificata in precedenza.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Debug.msTraceAsyncCallbackStarting(asyncOperationId)  
```  
  
#### <a name="parameters"></a>Parametri  
 `asyncOperationId`  
 Obbligatorio. ID associato all'operazione asincrona.  
  
## <a name="remarks"></a>Note  
 Chiamare questa funzione nella funzione di callback per l'operazione asincrona dopo la chiamata a `Debug.msTraceAsyncOperationCompleted`.  
  
> [!NOTE]
>  Alcuni strumenti di debug non visualizzano le informazioni inviate al debugger.  
  
 `asyncOperationId` deve corrispondere al nome dell'operazione precedentemente restituito da `Debug.msTraceAsyncOperationStarting`.  
  
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