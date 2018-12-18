---
title: Interfaccia IProvideExpressionContexts | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IProvideExpressionContexts interface
ms.assetid: e4c70f2c-7d86-4fdc-a1cb-f5a0bb8ed037
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 402b439da6f1fa369accacb27f987ac77119e343
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iprovideexpressioncontexts-interface"></a>Interfaccia IProvideExpressionContexts
Consente di enumerare i contesti di espressione noti per un determinato componente. Motori di script è in genere implementano questa interfaccia.  
  
 Il gestore di debug del processo utilizza questa interfaccia per trovare tutti i contesti di espressione globale associati a un determinato thread.  
  
> [!NOTE]
>  Questa interfaccia viene chiamata dall'interno il thread di interesse. È responsabilità dell'implementatore per identificare il thread corrente e restituisce un enumeratore appropriato.  
  
## <a name="methods"></a>Metodi  
 Oltre ai metodi ereditati da `IUnknown`, `IProvideExpressionContexts` interfaccia espone i metodi seguenti.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IProvideExpressionContexts::EnumExpressionContexts](../../winscript/reference/iprovideexpressioncontexts-enumexpressioncontexts.md)|Restituisce un enumeratore dei contesti di espressione noto da questo componente.|