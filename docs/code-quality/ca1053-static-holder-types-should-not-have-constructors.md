---
title: 'CA1053: I tipi statici non devono avere costruttori | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- StaticHolderTypesShouldNotHaveConstructors
- CA1053
helpviewer_keywords:
- CA1053
- StaticHolderTypesShouldNotHaveConstructors
ms.assetid: 10302b9a-fa5e-4935-a06a-513d9600f613
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d482c715e3f93df5fb26f0c88c6b0665b3dee506
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1053-static-holder-types-should-not-have-constructors"></a>CA1053: I tipi che contengono membri statici non devono avere costruttori
|||  
|-|-|  
|TypeName|StaticHolderTypesShouldNotHaveConstructors|  
|CheckId|CA1053|  
|Category|Microsoft. Design|  
|Modifica importante|Interruzione|  
  
## <a name="cause"></a>Causa  
 Un tipo pubblico o annidato dichiara solo membri statici e presenta un costruttore predefinito pubblico o protetto.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Il costruttore non è necessario perché la chiamata a membri statici non richiede un'istanza del tipo. Inoltre, perché il tipo non dispone di membri non statici, creazione di un'istanza non fornisce accesso a uno dei membri del tipo.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, rimuovere il costruttore predefinito o renderlo privato.  
  
> [!NOTE]
>  Se il tipo non definisce alcun costruttore, alcuni compilatori di creano automaticamente un costruttore predefinito pubblico. In questo caso con il tipo, aggiungere un costruttore privato predefinito per eliminare la violazione.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola. La presenza del costruttore suggerisce che il tipo non è un tipo statico.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato un tipo che viola questa regola. Si noti che nel codice sorgente è presente alcun costruttore predefinito. Quando questo codice viene compilato in un assembly, il compilatore c# viene inserito un costruttore predefinito, che verrà violano questa regola. Per risolvere il problema, dichiarare un costruttore privato.  
  
 [!code-csharp[FxCop.Design.StaticTypes#1](../code-quality/codesnippet/CSharp/ca1053-static-holder-types-should-not-have-constructors_1.cs)]