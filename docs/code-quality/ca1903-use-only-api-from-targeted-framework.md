---
title: 'CA1903: Utilizzare solo API .NET framework di destinazione | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UseOnlyAPIFromTargetedFramework
- CA1903
helpviewer_keywords:
- UseOnlyApiFromTargetedFramework
- CA1903
ms.assetid: efdb5cc7-bbd8-4fa7-9fff-02b91e59350e
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d20496fae54b0fdf2b0f0d17de0590c325bab0ee
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1903-use-only-api-from-targeted-framework"></a>CA1903: Utilizzare solo API della versione di .NET Framework di destinazione
|||  
|-|-|  
|TypeName|UseOnlyApiFromTargetedFramework|  
|CheckId|CA1903|  
|Category|Microsoft.Portability|  
|Modifica importante|Sostanziale - Quando viene generato con la firma di un membro visibile esternamente o un tipo.<br /><br /> Non sostanziale - Quando viene generato nel corpo di un metodo.|  
  
## <a name="cause"></a>Causa  
 Un tipo o membro utilizza un membro o un tipo che è stato introdotto in un service pack che non è stato incluso con framework di destinazione del progetto.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Tipi e i nuovi membri sono stati inclusi in .NET Framework 2.0 Service Pack 1 e 2, .NET Framework 3.0 Service Pack 1 e 2 e .NET Framework 3.5 Service Pack 1. I progetti destinati alle versioni principali di .NET Framework involontariamente possono richiedere dipendenze in queste nuove API. Per evitare questa dipendenza, questa regola viene attivata in caso di utilizzo di nuovi membri e tipi che non sono stati inclusi per impostazione predefinita con il framework di destinazione del progetto.  
  
 **Framework di destinazione e le dipendenze dei Service Pack**  
  
|||  
|-|-|  
|Quando il framework di destinazione è|Viene attivato in caso di utilizzo di membri introdotti in|  
|.NET Framework 2.0|.NET framework 2.0 SP1, .NET Framework 2.0 SP2|  
|.NET Framework 3.0|.NET framework 2.0 SP1, .NET Framework 2.0 SP2, .NET Framework 3.0 SP1, .NET Framework 3.0 SP2|  
|.NET Framework 3.5|.NET Framework 3.5 SP1|  
|.NET Framework 4|N/D|  
  
 Per modificare il framework di destinazione del progetto, vedere [come destinazione una versione di .NET Framework specifico](../ide/targeting-a-specific-dotnet-framework-version.md).  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per rimuovere la dipendenza del service pack, rimuovere tutti gli utilizzi del nuovo membro o tipo. Se si tratta di una dipendenza intenzionale, eliminare l'avviso o disattivare la regola.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola se non si tratta di una dipendenza intenzionale del service pack specificato. In questo caso, l'applicazione potrebbe non riuscire per l'esecuzione nei sistemi senza questo service pack installato. Eliminare l'avviso o disattivare questa regola se si tratta di una dipendenza intenzionale.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrata una classe che utilizza il tipo DateTimeOffset è disponibile solo in .NET 2.0 Service Pack 1. Questo esempio è necessario che .NET Framework 2.0 è stato selezionato nell'elenco a discesa Framework di destinazione nelle proprietà del progetto.  
  
 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_1.cs)]  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente consente di correggere la violazione descritta in precedenza sostituendo gli utilizzi del tipo DateTimeOffset con il tipo DateTime.  
  
 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_2.cs)]  
  
## <a name="see-also"></a>Vedere anche  
 [Avvisi di portabilità](../code-quality/portability-warnings.md)   
 [Sviluppo per una versione specifica di .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)