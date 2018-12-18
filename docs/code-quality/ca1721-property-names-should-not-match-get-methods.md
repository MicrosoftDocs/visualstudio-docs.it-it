---
title: "CA1721: I nomi di proprietà non devono corrispondere ai metodi get | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
helpviewer_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: eb0a1b45276e6563ab645100377dec25a9060e06
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1721-property-names-should-not-match-get-methods"></a>CA1721: I nomi delle proprietà non devono corrispondere ai metodi get
|||  
|-|-|  
|TypeName|PropertyNamesShouldNotMatchGetMethods|  
|CheckId|CA1721|  
|Category|Microsoft. naming|  
|Modifica importante|Interruzione|  
  
## <a name="cause"></a>Causa  
 Il nome di un membro pubblico o protetto inizia con 'Get' e in caso contrario corrisponda al nome di una proprietà di tipo pubblico o protetto. Ad esempio, un tipo che contiene un metodo denominato "GetColor" e una proprietà denominata 'Color' viola questa regola.  
  
## <a name="rule-description"></a>Descrizione della regola  
 I metodi get e le proprietà devono avere nomi che consente di distinguere chiaramente le relative funzioni.  
  
 Convenzioni di denominazione forniscono un aspetto comune per librerie destinate a common language runtime. In questo modo si riduce il tempo necessario per l'apprendimento di una nuova libreria software e aumenta la confidenza di clienti che la libreria è stata sviluppata da un utente che ha esperienza nello sviluppo di codice gestito.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Modificare il nome in modo che il nome di un metodo che è preceduto da 'Get' non corrisponde.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
> [!NOTE]
>  Questo avviso può essere esclusa se il metodo Get è determinato implementando l'interfaccia IExtenderProvider.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente contiene un metodo e proprietà che violano questa regola.  
  
 [!code-csharp[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/CSharp/ca1721-property-names-should-not-match-get-methods_1.cs)]
 [!code-vb[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/VisualBasic/ca1721-property-names-should-not-match-get-methods_1.vb)]  
  
## <a name="related-rules"></a>Regole correlate  
 [CA1024: Usare proprietà dove appropriato](../code-quality/ca1024-use-properties-where-appropriate.md)