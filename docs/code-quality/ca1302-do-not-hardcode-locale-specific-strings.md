---
title: 'CA1302: Non impostare come hardcoded le stringhe delle impostazioni locali'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
helpviewer_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
ms.assetid: 05ed134a-837d-43d7-bf97-906edeac44ce
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0de562f8f7af4e76b31bc49c33742009db485415
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1302-do-not-hardcode-locale-specific-strings"></a>CA1302: Non impostare come hardcoded le stringhe delle impostazioni locali
|||
|-|-|
|TypeName|DoNotHardcodeLocaleSpecificStrings|
|CheckId|CA1302|
|Category|Microsoft.Globalization|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un metodo utilizza un valore letterale stringa che rappresenta una parte del percorso di determinate cartelle di sistema.

## <a name="rule-description"></a>Descrizione della regola
 Il <xref:System.Environment.SpecialFolder?displayProperty=fullName> enumerazione contiene membri che fanno riferimento a cartelle speciali di sistema. I percorsi di queste cartelle possono presentare valori diversi in sistemi operativi diversi, l'utente può modificare alcune delle posizioni e i percorsi sono localizzati. Un esempio di una cartella speciale è la cartella di sistema, ovvero "C:\WINDOWS\system32" in [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)] ma "C:\WINNT\system32" in [!INCLUDE[win2kfamily](../code-quality/includes/win2kfamily_md.md)]. Il <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName> il metodo restituisce i percorsi in cui sono associati le <xref:System.Environment.SpecialFolder> enumerazione. I percorsi in cui vengono restituiti da <xref:System.Environment.GetFolderPath%2A> sono localizzati e appropriati per il computer in uso.

 Questa regola suddivide in token i percorsi delle cartelle che vengono recuperati utilizzando il <xref:System.Environment.GetFolderPath%2A> metodo in livelli di directory separati. Ogni valore letterale stringa viene confrontato con i token. Se viene trovata una corrispondenza, si presuppone che il metodo è la creazione di una stringa che rappresenta il percorso di sistema che è associato al token. Portabilità e la possibilità di localizzazione, utilizzare il <xref:System.Environment.GetFolderPath%2A> metodo per recuperare i percorsi delle cartelle di sistema speciali anziché valori letterali stringa.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, recuperare il percorso utilizzando il <xref:System.Environment.GetFolderPath%2A> metodo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È consigliabile escludere un avviso da questa regola se il valore letterale stringa non viene utilizzata per fare riferimento a uno dei percorsi di sistema che è associato il <xref:System.Environment.SpecialFolder> enumerazione.

## <a name="example"></a>Esempio
 Nell'esempio seguente crea il percorso della cartella dati applicazioni comuni che genera tre avvisi da questa regola. Successivamente, l'esempio recupera il percorso utilizzando il <xref:System.Environment.GetFolderPath%2A> metodo.

 [!code-csharp[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/CSharp/ca1302-do-not-hardcode-locale-specific-strings_1.cs)]
 [!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/VisualBasic/ca1302-do-not-hardcode-locale-specific-strings_1.vb)]

## <a name="related-rules"></a>Regole correlate
 [CA1303: Non passare valori letterali come parametri localizzati](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)