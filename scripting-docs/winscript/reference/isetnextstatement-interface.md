---
title: Interfaccia ISetNextStatement | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: b570c2e0-a173-4f14-97d8-f39465753115
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bdd71a427a8ef2c57684eef75a044d0cedf42415
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="isetnextstatement-interface"></a>Interfaccia ISetNextStatement
Questa interfaccia è implementata da un interprete per consentire la gestione processo di Debug per aggiornare l'istruzione corrente. Viene implementato da un oggetto stack frame e PDM ottiene questa interfaccia tramite QueryInterface.  
  
 interfaccia fornisce i metodi che consentono di impostare il punto di esecuzione, che determina l'istruzione successiva da eseguire.  
  
 Oltre ai metodi ereditati da `IUnknown`, `ISetNextStatement` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[ISetNextStatement::CanSetNextStatement](../../winscript/reference/isetnextstatement-cansetnextstatement.md)|Determina se il punto di esecuzione è possibile impostare nel percorso specificato.|  
|[ISetNextStatement::SetNextStatement](../../winscript/reference/isetnextstatement-setnextstatement.md)|Imposta il punto di esecuzione nella posizione specificata.|