---
title: 'CA1059: I membri non devono esporre tipi concreti specifici | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1059
- MembersShouldNotExposeCertainConcreteTypes
helpviewer_keywords:
- MembersShouldNotExposeCertainConcreteTypes
- CA1059
ms.assetid: 59f61f52-8d6c-49cb-aefb-191910523a3c
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: eae9070d76312fa4840f2cf8724a74a2cde4f7b2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1059-members-should-not-expose-certain-concrete-types"></a>CA1059: I membri non devono esporre tipi concreti specifici
|||  
|-|-|  
|TypeName|MembersShouldNotExposeCertainConcreteTypes|  
|CheckId|CA1059|  
|Category|Microsoft. Design|  
|Modifica importante|Interruzione|  
  
## <a name="cause"></a>Causa  
 Un membro visibile esternamente è un tipo concreto specifico o espone tipi concreti specifici tramite uno dei relativi parametri o valore restituito. Attualmente, questa regola segnala l'esposizione dei tipi concreti seguenti:  
  
-   Un tipo derivato da <xref:System.Xml.XmlNode?displayProperty=fullName>.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Un tipo concreto è un tipo con implementazione completa, pertanto è possibile crearne un'istanza. Per consentire un utilizzo esteso del membro, sostituire il tipo concreto con l'interfaccia suggerita. In questo modo il membro accettare qualsiasi tipo che implementa l'interfaccia o essere utilizzate dove è previsto un tipo che implementa l'interfaccia.  
  
 Nella tabella seguente sono elencati i tipi concreti di destinazione e le relative sostituzioni consigliate.  
  
|Tipo concreto|Sostituzione|  
|-------------------|-----------------|  
|<xref:System.Xml.XPath.XPathDocument>|<xref:System.Xml.XPath.IXPathNavigable?displayProperty=fullName>.<br /><br /> Tramite l'interfaccia separa il membro da un'implementazione specifica di un'origine dati XML.|  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, modificare il tipo concreto per l'interfaccia suggerita.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 È possibile eliminare un messaggio da questa regola se è necessaria la funzionalità specifica fornita dal tipo concreto.  
  
## <a name="related-rules"></a>Regole correlate  
 [CA1011: Considerare il passaggio di tipi di base come parametri](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)