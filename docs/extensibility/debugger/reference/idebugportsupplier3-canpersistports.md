---
title: IDebugPortSupplier3::CanPersistPorts | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords: IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7cb364ca40c42a3f392a5944169b7dd97075ab9b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
Questo metodo determina se il fornitore della porta può rendere persistente porte (mediante la scrittura su disco) tra le chiamate del debugger.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT CanPersistPorts();  
```  
  
```csharp  
int CanPersistPorts();  
```  
  
#### <a name="parameters"></a>Parametri  
 Nessuno.  
  
## <a name="return-value"></a>Valore restituito  
 `S_OK`Se le porte possono essere reso persistente, o `S_FALSE` per indicare che le porte non possono essere persistente.  
  
## <a name="remarks"></a>Note  
 Se il fornitore della porta può rendere persistente porte, dovrebbe eseguire questa operazione quando viene eliminato e quindi ricaricarli quando ne viene creata un'istanza ancora una volta.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)