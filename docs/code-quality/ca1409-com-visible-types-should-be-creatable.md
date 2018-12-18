---
title: 'CA1409: I tipi visibili a COM devono essere creabili'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
helpviewer_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
ms.assetid: 9f59569b-de15-4a38-b7cb-cff152972243
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8b2a7157c405eba52a2a7dc5de3b290a7ff26dc4
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca1409-com-visible-types-should-be-creatable"></a>CA1409: I tipi visibili a COM devono essere creabili
|||
|-|-|
|TypeName|ComVisibleTypesShouldBeCreatable|
|CheckId|CA1409|
|Category|Microsoft.Interoperability|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un tipo di riferimento contrassegnato specificatamente come visibile al modello COM (Component Object) contiene un costruttore con parametri pubblico ma non contiene un costruttore pubblico predefinito (senza parametri).

## <a name="rule-description"></a>Descrizione della regola
 Un tipo senza un costruttore predefinito pubblico non può essere creato da client COM. Tuttavia, il tipo può comunque accedere ai client COM se è disponibile un altro mezzo per creare il tipo e lo passerà al client (ad esempio, tramite il valore restituito di una chiamata al metodo).

 La regola ignora i tipi che derivano da <xref:System.Delegate?displayProperty=fullName>.

 Per impostazione predefinita, sono visibili a COM seguente: assembly, i tipi pubblici, i membri di istanza pubblici nei tipi pubblici e tutti i membri dei tipi di valore pubblico.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, aggiungere un costruttore predefinito pubblico o rimuovere il <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> dal tipo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se sono disponibili altri modi per creare e passare l'oggetto per il client COM.

## <a name="related-rules"></a>Regole correlate
 [CA1017: Contrassegnare gli assembly con ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Vedere anche
 [Qualificazione di tipi .NET per l'interoperabilità](/dotnet/framework/interop/qualifying-net-types-for-interoperation) [interoperabilità con codice non gestito](/dotnet/framework/interop/index)