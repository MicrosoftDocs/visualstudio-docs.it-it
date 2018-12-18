---
title: 'CA1303: Non passare valori letterali come localizzati parametri | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Do not pass literals as localized parameters
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
helpviewer_keywords:
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 361155e9d46e4f71ddc61775f56105cedb5d18b9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303: Non passare valori letterali come parametri localizzati
|||  
|-|-|  
|TypeName|DoNotPassLiteralsAsLocalizedParameters|  
|CheckId|CA1303|  
|Category|Microsoft.Globalization|  
|Modifica importante|Non importante|  
  
## <a name="cause"></a>Causa  
 Un metodo passa una stringa letterale come parametro a un costruttore o un metodo di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] libreria di classi e questa stringa deve essere localizzabile.  
  
 Questo avviso viene generato quando una valore letterale stringa viene passata come valore per un parametro o una proprietà e uno o più delle seguenti condizioni sono true:  
  
-   Il <xref:System.ComponentModel.LocalizableAttribute> attributo di parametro o la proprietà è impostata su true.  
  
-   Il nome di parametro o la proprietà contiene "Text", "Messaggio" o "Didascalia".  
  
-   Il nome del parametro di stringa che viene passato a un metodo Write o console. WriteLine è "value" o "format".  
  
## <a name="rule-description"></a>Descrizione della regola  
 Valori letterali stringa incorporati nel codice sorgente sono difficili da localizzare.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, sostituire il valore letterale stringa con una stringa recuperata tramite un'istanza di <xref:System.Resources.ResourceManager> classe.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 È possibile eliminare un avviso da questa regola se la libreria di codice non verrà localizzata o se la stringa non viene esposto all'utente finale o gli sviluppatori che utilizzano la libreria di codice.  
  
 Gli utenti possono eliminare le segnalazioni sui metodi non da passare stringhe localizzate rinominando il parametro o una proprietà denominata o contrassegnando questi elementi come condizionali.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato un metodo che genera un'eccezione se uno di due argomenti non è compreso nell'intervallo. Per il primo argomento, il costruttore di eccezione viene passato una valore letterale stringa, che violano questa regola. Per il secondo argomento, il costruttore è passato correttamente recuperata tramite una stringa di un <xref:System.Resources.ResourceManager>.  
  
 [!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CPP/ca1303-do-not-pass-literals-as-localized-parameters_1.cpp)]
 [!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/VisualBasic/ca1303-do-not-pass-literals-as-localized-parameters_1.vb)]
 [!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CSharp/ca1303-do-not-pass-literals-as-localized-parameters_1.cs)]  
  
## <a name="see-also"></a>Vedere anche  
 [Risorse nelle applicazioni desktop](/dotnet/framework/resources/index)