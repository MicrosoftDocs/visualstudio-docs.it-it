---
title: 'CA1028: L''archivio di Enum deve essere Int32 | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1028
- EnumStorageShouldBeInt32
helpviewer_keywords:
- EnumStorageShouldBeInt32
- CA1028
ms.assetid: 87160825-9f39-4142-8d7f-a31fe7ac7b84
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b09082cd78b3b78dda28201e85099e87f87d8ad4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1028-enum-storage-should-be-int32"></a>CA1028: L'archivio di enum deve essere Int32
|||  
|-|-|  
|TypeName|EnumStorageShouldBeInt32|  
|CheckId|CA1028|  
|Category|Microsoft. Design|  
|Modifica importante|Interruzione|  
  
## <a name="cause"></a>Causa  
 Il tipo sottostante di un'enumerazione pubblica non è <xref:System.Int32?displayProperty=fullName>.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Un'enumerazione è un tipo di valore che definisce un insieme di costanti denominate correlate. Per impostazione predefinita, il <xref:System.Int32?displayProperty=fullName> il tipo di dati viene utilizzato per archiviare il valore costante. Anche se è possibile modificare questo tipo sottostante, non è necessario o consigliato per la maggior parte degli scenari. Si noti che nessun miglioramento significativo delle prestazioni viene ottenuta con un tipo di dati che è minore di quelle <xref:System.Int32>. Se non è possibile utilizzare il tipo di dati predefinito, è necessario utilizzare uno del sistema CLS (Common Language)-conformi tipi integrali, <xref:System.Byte>, <xref:System.Int16>, <xref:System.Int32>, o <xref:System.Int64> per assicurarsi che tutti i valori dell'enumerazione possono essere rappresentati in Linguaggi di programmazione conformi a CLS.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, a meno che non sono presenti problemi di dimensioni o di compatibilità, utilizzare <xref:System.Int32>. Per le situazioni in cui <xref:System.Int32> non è sufficientemente grande per contenere i valori, utilizzare <xref:System.Int64>. Se la compatibilità con le versioni precedenti richiede un tipo di dati più piccolo, utilizzare <xref:System.Byte> o <xref:System.Int16>.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Escludere un avviso da questa regola solo se richiesto per problemi di compatibilità con le versioni precedenti. Nelle applicazioni, la mancata conformità con questa regola, in genere non causa problemi. Nelle raccolte in cui è richiesta l'interoperabilità di linguaggio, la mancata conformità con questa regola potrebbe influire negativamente sugli utenti.  
  
## <a name="example-of-a-violation"></a>Esempio di violazione  
  
### <a name="description"></a>Descrizione  
 L'esempio seguente mostra due enumerazioni che non utilizzano il tipo di dati sottostante consigliato.  
  
### <a name="code"></a>Codice  
 [!code-vb[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_1.vb)]
 [!code-csharp[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_1.cs)]  
  
## <a name="example-of-how-to-fix"></a>Esempio di come correzione  
  
### <a name="description"></a>Descrizione  
 Nell'esempio seguente consente di correggere la violazione precedente modificando il tipo di dati sottostante per <xref:System.Int32>.  
  
### <a name="code"></a>Codice  
 [!code-csharp[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_2.cs)]
 [!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_2.vb)]  
  
## <a name="related-rules"></a>Regole correlate  
 [CA1008: Gli enum devono avere valore zero](../code-quality/ca1008-enums-should-have-zero-value.md)  
  
 [CA1027: Contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
 [CA2217: Non contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
 [CA1700: Non denominare 'Reserved' i valori di enumerazione](../code-quality/ca1700-do-not-name-enum-values-reserved.md)  
  
 [CA1712: Non usare nomi di tipo come prefisso nei valori di enumerazione](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Byte?displayProperty=fullName>   
 <xref:System.Int16?displayProperty=fullName>   
 <xref:System.Int32?displayProperty=fullName>   
 <xref:System.Int64?displayProperty=fullName>