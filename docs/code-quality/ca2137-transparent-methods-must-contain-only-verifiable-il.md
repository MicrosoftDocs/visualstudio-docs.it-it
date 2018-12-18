---
title: 'CA2137: I metodi Transparent devono contenere solo IL verificabile'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2137
ms.assetid: cbaeb0e1-56b6-43b4-812a-596b2859c329
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 647240903ab2ada2e8fb319dca967a346a84b4cb
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca2137-transparent-methods-must-contain-only-verifiable-il"></a>CA2137: I metodi Transparent devono contenere solo IL verificabile
|||
|-|-|
|TypeName|TransparentMethodsMustBeVerifiable|
|CheckId|CA2137|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un metodo contiene codice non verificabile o restituisce un tipo tramite riferimento.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola viene attivata sui tentativi tramite codice trasparente per la sicurezza per eseguire MSIL (Microsoft Intermediate Language) non verificabile. Tuttavia, la regola non contiene un verificatore di IL completo, ma usa invece regole euristiche per intercettare la maggior parte delle violazioni di verifica MSIL.

 Per essere certi che il codice contiene solo MSIL verificabile, eseguire [Peverify.exe (strumento PEVerify)](/dotnet/framework/tools/peverify-exe-peverify-tool) nell'assembly. Eseguire PEVerify con il **/ trasparente** opzione che limita l'output solo non verificabili metodi trasparenti di cui verrebbe generato un errore. Se il / opzione trasparente non è utilizzata, PEVerify verifica inoltre i metodi critici che possono contenere codice non verificabile.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, contrassegnare il metodo con il <xref:System.Security.SecurityCriticalAttribute> o <xref:System.Security.SecuritySafeCriticalAttribute> attributo o rimuovere il codice non verificabile.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Il metodo in questo esempio Usa codice non verificabile e deve essere contrassegnato con il <xref:System.Security.SecurityCriticalAttribute> o <xref:System.Security.SecuritySafeCriticalAttribute> attributo.

 [!code-csharp[FxCop.Security.CA2137.TransparentMethodsMustBeVerifiable#1](../code-quality/codesnippet/CSharp/ca2137-transparent-methods-must-contain-only-verifiable-il_1.cs)]