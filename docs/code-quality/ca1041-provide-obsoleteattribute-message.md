---
title: "CA1041: Fornire una proprietà ObsoleteAttribute. message | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1041
- ProvideObsoleteAttributeMessage
helpviewer_keywords:
- ProvideObsoleteAttributeMessage
- CA1041
ms.assetid: be5bee69-d2d2-44e1-be2e-3ea451969003
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a7536130842c78ca2c00bab1afc3caf842e02cba
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041: Fornire una proprietà ObsoleteAttribute.Message
|||  
|-|-|  
|TypeName|ProvideObsoleteAttributeMessage|  
|CheckId|CA1041|  
|Category|Microsoft. Design|  
|Modifica importante|Non sostanziale|  
  
## <a name="cause"></a>Causa  
 Un tipo o membro viene contrassegnato utilizzando un <xref:System.ObsoleteAttribute?displayProperty=fullName> attributo che non dispone di relativo <xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName> proprietà specificata.  
  
## <a name="rule-description"></a>Descrizione della regola  
 <xref:System.ObsoleteAttribute>viene utilizzato per contrassegnare i membri e tipi di libreria obsoleta. Consumer della libreria è consigliabile evitare l'utilizzo di qualsiasi tipo o membro che è contrassegnato come obsoleto. Infatti potrebbe non essere supportato e verrà rimossi dalle versioni successive della libreria. Quando un tipo o un membro contrassegnato utilizzando <xref:System.ObsoleteAttribute> viene compilato il <xref:System.ObsoleteAttribute.Message%2A> proprietà dell'attributo è visibile. In questo modo vengono fornite le informazioni utente sul tipo o sul membro obsoleto. Queste informazioni comprendono in genere il tempo di tipo obsoleto o membro sarà supportato per le finestre di progettazione di libreria e la sostituzione preferita da utilizzare.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, aggiungere il `message` parametro per il <xref:System.ObsoleteAttribute> costruttore.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola perché i <xref:System.ObsoleteAttribute.Message%2A> proprietà fornisce informazioni essenziali sul tipo o membro obsoleto.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato un membro obsoleto che ha dichiarato in modo corretto <xref:System.ObsoleteAttribute>.  
  
 [!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CPP/ca1041-provide-obsoleteattribute-message_1.cpp)]
 [!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CSharp/ca1041-provide-obsoleteattribute-message_1.cs)]
 [!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/VisualBasic/ca1041-provide-obsoleteattribute-message_1.vb)]  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.ObsoleteAttribute?displayProperty=fullName>