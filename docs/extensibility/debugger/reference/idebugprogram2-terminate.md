---
title: IDebugProgram2::Terminate | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgram2::Terminate
helpviewer_keywords: IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fea9b99fc597a75e93392b14fe40a1be87072602
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
Termina il programma.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Terminate(   
   void   
);  
```  
  
```csharp  
int Terminate();  
```  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Se possibile, verrà terminato e scaricato dal processo; il programma in caso contrario, il motore di debug (DE) eseguirà le operazioni di pulitura necessarie.  
  
 Questo metodo o [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) metodo viene chiamato dall'IDE, in genere in risposta all'utente di interrompere il debug tutti. L'implementazione di questo metodo deve, in teoria, terminare il programma all'interno del processo. In caso contrario, la Germania deve impedire che il programma in esecuzione altri in questo processo ed eseguire operazioni di pulitura necessarie. Se il `IDebugProcess2::Terminate` metodo è stato chiamato dall'IDE, l'intero processo verrà terminato un po' dopo il `IDebugProgram2::Terminate` metodo viene chiamato.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Terminare](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)