---
title: 'CA2212: Non contrassegnare componenti serviti con WebMethod'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
helpviewer_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
ms.assetid: 774bc55d-e588-48ee-8f38-c228580feca2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9ee4371f44a8a8c2acd0b20f48fcc89a1242b4df
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212: Non contrassegnare componenti serviti con WebMethod
|||
|-|-|
|TypeName|DoNotMarkServicedComponentsWithWebMethod|
|CheckId|CA2212|
|Category|Microsoft.Usage|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un metodo in un tipo che eredita da <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> è contrassegnato con <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Descrizione della regola
 <xref:System.Web.Services.WebMethodAttribute> si applica ai metodi all'interno di un servizio Web XML creati tramite ASP.NET. rende il metodo chiamabile dai client Web remoti. Il metodo e la classe deve essere pubblico e in esecuzione in un'applicazione Web ASP.NET. <xref:System.EnterpriseServices.ServicedComponent> i tipi sono ospitati da applicazioni COM+ e possono usare servizi di COM+. <xref:System.Web.Services.WebMethodAttribute> non viene applicato al <xref:System.EnterpriseServices.ServicedComponent> tipi perché non sono progettati per gli stessi scenari. In particolare, l'aggiunta dell'attributo per il <xref:System.EnterpriseServices.ServicedComponent> metodo non rendere il metodo chiamabile dai client Web remoti. Poiché <xref:System.Web.Services.WebMethodAttribute> e <xref:System.EnterpriseServices.ServicedComponent> metodo presentano comportamenti in conflitto e i requisiti di contesto e flusso delle transazioni, il comportamento del metodo sarà corretto in determinati scenari.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rimuovere l'attributo dal <xref:System.EnterpriseServices.ServicedComponent> metodo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola. Non sono scenari in cui la combinazione di questi elementi è corretta.

## <a name="see-also"></a>Vedere anche
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>