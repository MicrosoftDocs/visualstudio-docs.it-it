---
title: "CA2126: Le richieste di collegamento necessarie richieste di ereditarietà | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
helpviewer_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
ms.assetid: 07b604e5-5579-4df9-a578-dadd0d8370a7
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 20ce42e001bcb0fe60f563cb4cfbee913315df27
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca2126-type-link-demands-require-inheritance-demands"></a>CA2126: Per le richieste di collegamento dei tipi sono necessarie richieste di ereditarietà
|||  
|-|-|  
|TypeName|TypeLinkDemandsRequireInheritanceDemands|  
|CheckId|CA2126|  
|Category|Microsoft.Security|  
|Modifica importante|Interruzione|  
  
## <a name="cause"></a>Causa  
 Un tipo non sealed pubblico è protetto con una richiesta di collegamento, dispone di un metodo sottoponibile a override e il tipo né il metodo è protetto con una richiesta di ereditarietà.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Una richiesta di collegamento in un metodo o il tipo dichiarante il chiamante immediato del metodo deve avere l'autorizzazione specificata. Una richiesta di ereditarietà in un metodo richiede un metodo di overriding disporre dell'autorizzazione specificata. Una richiesta di ereditarietà in un tipo richiede una classe di derivazione disporre dell'autorizzazione specificata.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, proteggere il tipo o il metodo con una richiesta di ereditarietà per la stessa autorizzazione della richiesta di collegamento.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato un tipo che viola la regola.  
  
 [!code-cpp[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CPP/ca2126-type-link-demands-require-inheritance-demands_1.cpp)]
 [!code-vb[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/VisualBasic/ca2126-type-link-demands-require-inheritance-demands_1.vb)]
 [!code-csharp[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2126-type-link-demands-require-inheritance-demands_1.cs)]  
  
## <a name="related-rules"></a>Regole correlate  
 [CA2108: Controllare la sicurezza dichiarativa sui tipi di valori](../code-quality/ca2108-review-declarative-security-on-value-types.md)  
  
 [CA2112: I tipi protetti non devono esporre campi](../code-quality/ca2112-secured-types-should-not-expose-fields.md)  
  
 [CA2122: Non esporre in modo indiretto metodi con richieste di collegamento](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)  
  
 [CA2123: Le richieste di collegamento negli override devono essere identiche a quelle nei metodi di base](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Linee guida di codice sicuro](/dotnet/standard/security/secure-coding-guidelines)   
 [Richieste di collegamento](/dotnet/framework/misc/link-demands)   
