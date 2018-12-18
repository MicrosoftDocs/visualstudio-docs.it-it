---
title: 'CA1064: Le eccezioni devono essere pubbliche | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1064
- ExceptionsShouldBePublic
helpviewer_keywords:
- ExceptionsShouldBePublic
- CA1064
ms.assetid: 83eb224c-2456-4368-acf4-3b3378e67759
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7779be831b32572addb6198b5a5be46616cdb1b4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1064-exceptions-should-be-public"></a>CA1064: Le eccezioni devono essere pubbliche
|||  
|-|-|  
|TypeName|ExceptionsShouldBePublic|  
|CheckId|CA1064|  
|Category|Microsoft. Design|  
|Modifica importante|Non importante|  
  
## <a name="cause"></a>Causa  
 Un'eccezione non pubblica deriva direttamente dalla <xref:System.Exception>, <xref:System.SystemException>, o <xref:System.ApplicationException>.  
  
## <a name="rule-description"></a>Descrizione della regola  
 È visibile nel relativo ambito interno solo un'eccezione interna. Se l'eccezione si verifica al di fuori dell'ambito interno, può essere rilevata solo tramite l'eccezione di base. Se l'eccezione interna è ereditata da <xref:System.Exception>, <xref:System.SystemException>, o <xref:System.ApplicationException>, il codice esterno non contiene informazioni sufficienti per sapere cosa fare con l'eccezione.  
  
 Tuttavia, se il codice dispone di un'eccezione pubblica in un secondo momento viene utilizzata come base per un'eccezione interna, è ragionevole supporre che il codice ulteriormente out sarà in grado di eseguire un'operazione intelligente con l'eccezione di base. Eccezione pubblica sarà disponibili più informazioni rispetto a quello fornito da T:System.Exception, T:System.SystemException o T:System.ApplicationException.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Rendere pubblico il tipo di eccezione o derivare l'eccezione interna da un'eccezione non pubblica <xref:System.Exception>, <xref:System.SystemException>, o <xref:System.ApplicationException>.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Esclusione di un messaggio da questa regola se si è certi in tutti i casi l'eccezione privata verrà rilevata nel relativo ambito interno.  
  
## <a name="example"></a>Esempio  
 Questa regola funziona sul primo metodo di esempio, FirstCustomException perché la classe di eccezione deriva direttamente da eccezione ed è interna. La regola non viene generato nella classe SecondCustomException perché anche se la classe deriva direttamente da Exception, la classe è dichiarata pubblica. La terza classe inoltre non venga attivato la regola perché non deriva direttamente da <xref:System.Exception?displayProperty=fullName>, <xref:System.SystemException?displayProperty=fullName>, o <xref:System.ApplicationException?displayProperty=fullName>.  
  
 [!code-csharp[FxCop.Design.ExceptionsShouldBePublic.CA1064#1](../code-quality/codesnippet/CSharp/ca1064-exceptions-should-be-public_1.cs)]