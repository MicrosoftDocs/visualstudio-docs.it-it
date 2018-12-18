---
title: 'CA1031: Non rilevare tipi di eccezione generali | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
helpviewer_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
ms.assetid: cbc283ae-2a46-4ec0-940e-85aa189b118f
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d1b11db50a4e6104c09a65ebe9e7616d223ef3ee
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031: Non rilevare tipi di eccezione generali
|||  
|-|-|  
|TypeName|DoNotCatchGeneralExceptionTypes|  
|CheckId|CA1031|  
|Category|Microsoft. Design|  
|Modifica importante|Non sostanziale|  
  
## <a name="cause"></a>Causa  
 Un'eccezione generale come <xref:System.Exception?displayProperty=fullName> o <xref:System.SystemException?displayProperty=fullName> viene rilevata in un `catch` istruzione o una clausola catch generale, ad esempio `catch()` viene utilizzato.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Le eccezioni generali non devono essere rilevate.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, rilevare un'eccezione più specifica o rigenerare l'eccezione generale come ultima istruzione nel `catch` blocco.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola. Il rilevamento di tipi di eccezione generali può nascondere i problemi in fase di esecuzione da parte dell'utente di libreria e può rendere più difficile il debug.  
  
> [!NOTE]
>  A partire dal [!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)], common language runtime (CLR) non recapita più eccezioni di stato danneggiato che si verificano nel sistema operativo e codice gestito, ad esempio le violazioni di accesso in [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)], devono essere gestiti da codice gestito. Se si desidera compilare un'applicazione nel [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] o versioni successive e mantenere la gestione delle eccezioni di stato danneggiato, è possibile applicare il <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> attributo al metodo che gestisce l'eccezione di stato danneggiato.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato un tipo che viola la regola e un tipo che implementa correttamente il `catch` blocco.  
  
 [!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CPP/ca1031-do-not-catch-general-exception-types_1.cpp)]
 [!code-vb[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/VisualBasic/ca1031-do-not-catch-general-exception-types_1.vb)]
 [!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CSharp/ca1031-do-not-catch-general-exception-types_1.cs)]  
  
## <a name="related-rules"></a>Regole correlate  
 [CA2200: Eseguire il rethrow per mantenere i dettagli dello stack](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)