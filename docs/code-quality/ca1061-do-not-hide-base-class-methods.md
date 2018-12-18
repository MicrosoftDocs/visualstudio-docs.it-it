---
title: 'CA1061: Non nascondere i metodi della classe base | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1061
- DoNotHideBaseClassMethods
helpviewer_keywords:
- DoNotHideBaseClassMethods
- CA1061
ms.assetid: 0bda9dc8-87b4-4038-ab9d-563298387466
caps.latest.revision: "9"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d7eb4db46697e7f4cbb54d9ee11e4289b5a2ba2c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1061-do-not-hide-base-class-methods"></a>CA1061: Non nascondere i metodi di una classe base
|||  
|-|-|  
|TypeName|DoNotHideBaseClassMethods|  
|CheckId|CA1061|  
|Category|Microsoft. Design|  
|Modifica importante|Interruzione|  
  
## <a name="cause"></a>Causa  
 Un tipo derivato dichiara un metodo con lo stesso nome e con lo stesso numero di parametri come uno dei relativi metodi base; uno o più dei parametri è un tipo di base del parametro corrispondente nel metodo di base; e i parametri rimanenti sono tipi che corrispondono ai parametri corrispondenti nel metodo di base.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Un metodo in un tipo di base è nascosto da un metodo denominato in modo identico in un tipo derivato, quando la firma di parametro del metodo derivato differisce solo per i tipi che presentano una derivazione più debole rispetto ai tipi corrispondenti nella firma del parametro del metodo di base.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, rimuovere o rinominare il metodo o modificare la firma di parametro in modo che il metodo non nasconde il metodo di base.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato un metodo che viola la regola.  
  
 [!code-csharp[FxCop.Design.HideBaseMethod#1](../code-quality/codesnippet/CSharp/ca1061-do-not-hide-base-class-methods_1.cs)]