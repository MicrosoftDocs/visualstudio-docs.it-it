---
title: Implementazione e la registrazione di un fornitore di porta | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1c05dc0bd15dc5c1959024327396d848cd0b1112
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-and-registering-a-port-supplier"></a>Implementazione e la registrazione di un fornitore di porta
Il ruolo di un fornitore di porta è per tenere traccia e specificare porte, che a sua volta la gestione dei processi. Al momento che è necessario creare una porta, il fornitore della porta viene creata un'istanza con CoCreate GUID del fornitore porta (gestore di sessione di debug [SDM] utilizzerà il fornitore della porta selezionato dall'utente o il fornitore della porta specificato dal sistema del progetto). Verrà quindi chiamato il SDM [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) per vedere se è possono aggiungere le porte. Se è possibile aggiungere una porta, una nuova porta è richiesta chiamando [Aggiungi porta](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) e passando un [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) che descrive la porta. `AddPort`Restituisce una nuova porta rappresentata da un [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interfaccia.  
  
## <a name="discussion"></a>Discussione  
 Viene creata una porta da un fornitore di porta, che a sua volta associato a un server macchina o di debug. Un server può enumerare i suoi fornitori porta tramite il[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) (metodo) e un fornitore di porta può enumerare le porte tramite il [EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) metodo.  
  
 Oltre la normale registrazione COM, un fornitore di porta deve registrarsi con Visual Studio inserendo il CLSID e il nome nei percorsi del Registro di sistema. Chiamare una funzione helper Debugging SDK `SetMetric` gestisce questo compito: viene chiamato una volta per ogni elemento deve essere registrato, in questo modo:  
  
```cpp  
SetMetric(metrictypePortSupplier,  
          <GUID of your port supplier>,  
          metricCLSID,  
          <CLSID of your port supplier>,  
          false,  
          NULL)  
SetMetric(metrictypePortSupplier,  
          <GUID of your port supplier>,  
          metricName,  
          <name of your port supplier>,  
          false,  
          NULL);  
```  
  
 Un fornitore di porta Annulla registrazione chiamando `RemoveMetric` (un'altra funzione di supporto Debugging SDK) una volta per ogni elemento che è stato registrato, in questo modo:  
  
```cpp  
RemoveMetric(metrictypePortSupplier,  
             <GUID of your port supplier>,  
             metricCLSID,  
             NULL);  
RemoveMetric(metrictypePortSupplier,  
             <GUID of your port supplier>,  
             metricName,  
             NULL);  
```  
  
> [!NOTE]
>  Il [SDK helper per il debug](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` e `RemoveMetric` sono funzioni statiche definite in dbgmetric.h e compilati in ad2de.lib. Il `metrictypePortSupplier`, `metricCLSID`, e `metricName` helper sono definiti anche nel dbgmetric.h.  
  
 Un fornitore di porta può fornire il nome e GUID tramite i metodi [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) e [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md), rispettivamente.  
  
## <a name="see-also"></a>Vedere anche  
 [Implementazione di un fornitore di porta](../../extensibility/debugger/implementing-a-port-supplier.md)   
 [Helper SDK per il debug](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Fornitori di porte](../../extensibility/debugger/port-suppliers.md)