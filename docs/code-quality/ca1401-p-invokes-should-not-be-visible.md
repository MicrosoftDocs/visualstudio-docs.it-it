---
title: 'CA1401: P-richiama non devono essere visibile | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PInvokesShouldNotBeVisible
- CA1401
helpviewer_keywords:
- CA1401
- PInvokesShouldNotBeVisible
ms.assetid: 0f4d96c1-f9de-414e-b223-4dc7f691bee3
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: cbb2a08e5a346aff8d03f76a7fc0579ce9928952
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1401-pinvokes-should-not-be-visible"></a>CA1401: I P/Invoke non devono essere visibili
|||  
|-|-|  
|TypeName|PInvokesShouldNotBeVisible|  
|CheckId|CA1401|  
|Category|Microsoft.Interoperability|  
|Modifica importante|Interruzione|  
  
## <a name="cause"></a>Causa  
 Un metodo pubblico o protetto in un tipo pubblico presenta il <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> attributo (implementato anche dal `Declare` parola chiave in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).  
  
## <a name="rule-description"></a>Descrizione della regola  
 I metodi contrassegnati con il <xref:System.Runtime.InteropServices.DllImportAttribute> attributo (o i metodi definiti mediante il `Declare` parola chiave in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) utilizzare servizi di Platform Invoke per accedere a codice non gestito. Questi metodi non devono essere esposti. Per mantenere questi metodi privati o interni, assicurarsi che la raccolta non può essere utilizzata per violare la sicurezza consentendo ai chiamanti di accedere ad API non gestite che non può chiamare in caso contrario.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, modificare il livello di accesso del metodo.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene dichiarato un metodo che viola questa regola.  
  
 [!code-vb[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/VisualBasic/ca1401-p-invokes-should-not-be-visible_1.vb)]
 [!code-csharp[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/CSharp/ca1401-p-invokes-should-not-be-visible_1.cs)]