---
title: 'CA2133: Delegati devono essere associati ai metodi con trasparenza consistente | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2133
ms.assetid: a09672e2-63cb-4abd-9e8f-dff515e101ce
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d5e5d391fc11fbefbe1f3cef6ee1512ab02d6b00
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca2133-delegates-must-bind-to-methods-with-consistent-transparency"></a>CA2133: Delegati devono essere associati ai metodi con trasparenza consistente
|||  
|-|-|  
|TypeName|DelegatesMustBindWithConsistentTransparency|  
|CheckId|CA2133|  
|Category|Microsoft.Security|  
|Modifica importante|Interruzione|  
  
> [!NOTE]
>  Questo avviso viene applicato solo al codice che esegue CoreCLR (la versione di CLR è specifico di applicazioni Silverlight Web).  
  
## <a name="cause"></a>Causa  
 Questo avviso è generato su un metodo che associa un delegato che è contrassegnato con il <xref:System.Security.SecurityCriticalAttribute> a un metodo trasparente o contrassegnato con il <xref:System.Security.SecuritySafeCriticalAttribute>. L'avviso genera anche un metodo che associa un delegato che è trasparente o critico per la sicurezza a un metodo critico.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Tipi delegati e i metodi che vengono associate devono avere trasparenza consistente. Delegati Transparent e SafeCritical possono solo eseguire il binding ad altri metodi transparent o SafeCritical. In modo analogo, delegati critici possono solo associare ai metodi critici. Queste regole di associazione assicurano che l'unico codice che è possibile richiamare un metodo tramite un delegato può inoltre aver richiamato lo stesso metodo direttamente. Ad esempio, le regole di associazione impediscono di chiamata di codice critical direttamente tramite un delegato trasparente codice trasparente.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questo avviso, modificare la trasparenza del delegato o del metodo che associa in modo che la trasparenza tra i due sono equivalenti.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
### <a name="code"></a>Codice  
 [!code-csharp[FxCop.Security.CA2133.DelegatesMustBindWithConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2133-delegates-must-bind-to-methods-with-consistent-transparency_1.cs)]