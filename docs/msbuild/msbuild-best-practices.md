---
title: Procedure consigliate per MSBuild | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- best practices, MSBuild
- MSBuild, best practices
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a2572e300c666462c5f514452a40f810a349040f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="msbuild-best-practices"></a>Procedure consigliate di MSBuild
Per la scrittura degli script di MSBuild è consigliabile seguire le indicazioni riportate di seguito:  
  
-   I valori di proprietà predefiniti vengono gestiti meglio con l'attributo `Condition` e non dichiarando una proprietà il cui valore predefinito può essere sottoposto a override nella riga di comando. Ad esempio, usare  
  
     `<MyProperty Condition="'$(MyProperty)' == ''">`  
  
     `MyDefaultValue`  
  
     `</MyProperty>`  
  
-   Evitare i caratteri jolly quando si selezionano elementi. Al contrario, specificare i file in modo esplicito. Ciò semplifica l'individuazione degli errori che possono verificarsi quando si aggiungono o si eliminano file.  
  
## <a name="see-also"></a>Vedere anche  
 [Advanced Concepts](../msbuild/msbuild-advanced-concepts.md) (Concetti avanzati)
