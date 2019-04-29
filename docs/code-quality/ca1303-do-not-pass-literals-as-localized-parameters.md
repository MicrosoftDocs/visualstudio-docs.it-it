---
title: 'CA1303: Non passare valori letterali come parametri localizzati'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- Do not pass literals as localized parameters
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
helpviewer_keywords:
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 5bdae3d0ee17624a2b168e5ce944ba10ab37fc8a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62797461"
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303: Non passare valori letterali come parametri localizzati

|||
|-|-|
|TypeName|DoNotPassLiteralsAsLocalizedParameters|
|CheckId|CA1303|
|Category|Microsoft.Globalization|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un metodo passa una stringa letterale come parametro a un costruttore o un metodo nella libreria di classi .NET Framework e tale stringa deve essere localizzabile.

 Questo avviso viene generato quando una valore letterale stringa viene passata come valore per un parametro o una proprietà e uno o più delle seguenti condizioni sono true:

- Il <xref:System.ComponentModel.LocalizableAttribute> attributi del parametro o della proprietà sono impostato su true.

- Il nome di parametro o una proprietà contiene "Text", "Messaggio" o "Caption".

- Il nome del parametro di stringa che viene passato a un metodo Console. Write o console. WriteLine è "value" o "format".

## <a name="rule-description"></a>Descrizione della regola
 Valori letterali stringa incorporati nel codice sorgente sono difficili da localizzare.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, sostituire il valore letterale stringa con una stringa recuperata tramite un'istanza di <xref:System.Resources.ResourceManager> classe.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 È possibile eliminare un avviso da questa regola se la libreria di codice non verrà localizzata, o se la stringa non viene esposto all'utente finale o a uno sviluppatore che usa la libreria di codice.

 Gli utenti possono eliminare le segnalazioni con i metodi che non deve essere passato stringhe localizzate rinominando il parametro o una proprietà denominata o contrassegnando tali elementi come condizionale.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un metodo che genera un'eccezione se uno dei due argomenti sono comprese nell'intervallo. Per il primo argomento, il costruttore di eccezione viene passato una stringa letterale che viola questa regola. Per il secondo argomento, il costruttore correttamente viene passato una stringa recuperata tramite una <xref:System.Resources.ResourceManager>.

 [!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CPP/ca1303-do-not-pass-literals-as-localized-parameters_1.cpp)]
 [!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/VisualBasic/ca1303-do-not-pass-literals-as-localized-parameters_1.vb)]
 [!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CSharp/ca1303-do-not-pass-literals-as-localized-parameters_1.cs)]

## <a name="see-also"></a>Vedere anche
 [Risorse nelle applicazioni desktop](/dotnet/framework/resources/index)