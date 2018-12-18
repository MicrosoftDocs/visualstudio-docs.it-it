---
title: 'CA1050: Dichiarare i tipi negli spazi dei nomi | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1050
- DeclareTypesInNamespaces
helpviewer_keywords:
- DeclareTypesInNamespaces
- CA1050
ms.assetid: 1002748d-ac8d-404f-85dd-7a12d1ad3e05
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 297491e6f3bdaef2b0d460bfe37716f6cae0dbd3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1050-declare-types-in-namespaces"></a>CA1050: Dichiarare i tipi negli spazi dei nomi
|||  
|-|-|  
|TypeName|DeclareTypesInNamespaces|  
|CheckId|CA1050|  
|Category|Microsoft. Design|  
|Modifica importante|Interruzione|  
  
## <a name="cause"></a>Causa  
 Un tipo pubblico o protetto è definito all'esterno dell'ambito di uno spazio dei nomi denominato.  
  
## <a name="rule-description"></a>Descrizione della regola  
 I tipi vengono dichiarati negli spazi dei nomi per evitare conflitti di nome e un modo per organizzare i tipi correlati in una gerarchia di oggetti. I tipi che sono di fuori di qualsiasi spazio dei nomi sono in uno spazio dei nomi globale che non può fare riferimento nel codice.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, inserire il tipo in uno spazio dei nomi.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Anche se non mai necessario escludere un avviso da questa regola, è consigliabile eseguire questa operazione se l'assembly non verrà mai utilizzato insieme ad altri assembly.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente mostra una raccolta che dispone di un tipo dichiarato in modo errato di fuori di uno spazio dei nomi e un tipo che ha lo stesso nome dichiarato in uno spazio dei nomi.  
  
 [!code-csharp[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_1.cs)]
 [!code-vb[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_1.vb)]  
  
## <a name="example"></a>Esempio  
 La seguente applicazione utilizza la libreria che è stata definita in precedenza. Si noti che il tipo dichiarato all'esterno di uno spazio dei nomi viene creato quando il nome `Test` non è qualificato da uno spazio dei nomi. Si noti inoltre che per accedere il `Test` digitare `Goodspace`, il nome dello spazio dei nomi è obbligatorio.  
  
 [!code-csharp[FxCop.Design.TestTypesLive#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_2.cs)]
 [!code-vb[FxCop.Design.TestTypesLive#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_2.vb)]