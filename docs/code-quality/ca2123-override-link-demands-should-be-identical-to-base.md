---
title: 'CA2123: Le richieste di collegamento di Override devono essere identiche a base | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2123
- OverrideLinkDemandsShouldBeIdenticalToBase
helpviewer_keywords:
- OverrideLinkDemandsShouldBeIdenticalToBase
- CA2123
ms.assetid: 4538ecd5-fc6f-4480-ab00-90b2ce4730db
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3181e791d95f0268fd60654e8ceedb8fa394f7a0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca2123-override-link-demands-should-be-identical-to-base"></a>CA2123: Le richieste di collegamento negli verrine devono essere identiche a quelle nei metodi di base
|||  
|-|-|  
|TypeName|OverrideLinkDemandsShouldBeIdenticalToBase|  
|CheckId|CA2123|  
|Category|Microsoft.Security|  
|Modifica importante|Interruzione|  
  
## <a name="cause"></a>Causa  
 Un metodo pubblico o protetto in un tipo pubblico esegue l'override di un metodo o implementa un'interfaccia e non avere le stesse [le richieste di collegamento](/dotnet/framework/misc/link-demands) dell'interfaccia o un metodo virtuale.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Questa regola associa un metodo al relativo metodo di base che può essere un'interfaccia o un metodo virtuale in un altro tipo, quindi confronta le richieste di collegamento in ognuno. Se il metodo o il metodo di base dispone di una richiesta di collegamento e l'altro non lo fa, viene segnalata una violazione.  
  
 Se questa regola viene violata, un chiamante malintenzionato può ignorare la richiesta di collegamento chiamando semplicemente il metodo non sicuro.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, applicare la stessa richiesta di collegamento per il metodo di eseguire l'override o l'implementazione. In caso contrario, contrassegnare il metodo con una richiesta completa o rimuovere completamente l'attributo.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente mostra alcune violazioni di questa regola.  
  
 [!code-csharp[FxCop.Security.OverridesAndSecurity#1](../code-quality/codesnippet/CSharp/ca2123-override-link-demands-should-be-identical-to-base_1.cs)]  
  
## <a name="see-also"></a>Vedere anche  
 [Linee guida di codice sicuro](/dotnet/standard/security/secure-coding-guidelines)   
 [Richieste di collegamento](/dotnet/framework/misc/link-demands)