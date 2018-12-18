---
title: Gerarchia dei tipi di simboli di classi | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: symbols [DIA SDK], class hierarchies
ms.assetid: 0ccd6990-4654-44cd-a6f3-bdd82fe90f6c
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d2cb2374a33677f961fa798332ac96b6d801990b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="class-hierarchy-of-symbol-types"></a>Gerarchia di classi dei tipi di simboli
Nella tabella seguente vengono descritti i tipi di simboli nella gerarchia delle classi.  
  
## <a name="symbol-types"></a>Tipi di simboli  
  
|Tipo di simbolo|Descrizione|  
|-----------------|-----------------|  
|[UDT](../../debugger/debug-interface-access/udt.md)|Simbolo utilizzato per rappresentare ogni classe, struttura e unione.|  
|[Enum (Debug Interface Access SDK)](../../debugger/debug-interface-access/enum-debug-interface-access-sdk.md)|Simbolo per i tipi enumerati.|  
|[PointerType](../../debugger/debug-interface-access/pointertype.md)|Simbolo per tipi puntatore.|  
|[ArrayType](../../debugger/debug-interface-access/arraytype.md)|Simbolo per i tipi di matrice.|  
|[BaseType](../../debugger/debug-interface-access/basetype.md)|Simbolo per tipi di base|  
|[Typedef (Debug Interface Access SDK)](../../debugger/debug-interface-access/typedef-debug-interface-access-sdk.md)|Simbolo che introduce nomi per gli altri tipi.|  
|[BaseClass](../../debugger/debug-interface-access/baseclass.md)|Simbolo utilizzato per ogni classe di base di un tipo definito dall'utente (UDT).|  
|[Friend (Debug Interface Access SDK)](../../debugger/debug-interface-access/friend-debug-interface-access-sdk.md)|Simbolo per classi di tipo friend e le funzioni friend.|  
|[FunctionType](../../debugger/debug-interface-access/functiontype.md)|Simbolo per ogni firma della funzione univoco.|  
|[FunctionArgType](../../debugger/debug-interface-access/functionargtype.md)|Simbolo per ogni parametro a una funzione.|  
|[VTableShape](../../debugger/debug-interface-access/vtableshape.md)|Simbolo per le dimensioni della tabella virtuale.|  
|[VTable](../../debugger/debug-interface-access/vtable.md)|Simbolo di una tabella virtuale.|  
|[CustomType](../../debugger/debug-interface-access/customtype.md)|Simbolo di tipo definito dal fornitore.|  
|[ManagedType](../../debugger/debug-interface-access/managedtype.md)|Simbolo di un tipo definito nei metadati.|  
|[Dimensione](../../debugger/debug-interface-access/dimension.md)|Simbolo per le dimensioni di matrice.|  
  
> [!NOTE]
>  Ogni simbolo può disporre di proprietà che contengono informazioni sui simboli, nonché a riferimenti ad altri simboli. Queste proprietà sono elencate negli argomenti di simbolo.  
  
## <a name="see-also"></a>Vedere anche  
 [CV_access_e (enumerazione)](../../debugger/debug-interface-access/cv-access-e.md)   
 [Gerarchia lessicale dei tipi di simboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [Simboli e relativi tag](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)