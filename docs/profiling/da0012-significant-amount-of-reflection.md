---
title: DA0012-quantità significativa di Reflection | Microsoft Docs
description: Le chiamate ai metodi System.Reflection, ad esempio InvokeMember e GetMember, o ai metodi Type, ad esempio MemberInvoke, costituiscono una percentuale significativa dei dati di profilatura.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAReflection
- vs.performance.12
- vs.performance.rules.DA0012
- vs.performance.DA0011
ms.assetid: c92a1d76-21fa-426e-8b1b-a3c08e9bcbca
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 733f9d6c38b93005c0344de2f3d5b1d43093c12e
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2021
ms.locfileid: "102469961"
---
# <a name="da0012-significant-amount-of-reflection"></a>DA0012: Utilizzo elevato della reflection

|Elemento|valore|
|-|-|
|ID regola|DA0012|
|Category|Uso di .NET Framework|
|Metodi di profilatura|campionamento|
|Message|È possibile che si stia usando la reflection in modo eccessivo. L'operazione è dispendiosa.|
|Tipo regola|Avviso|

## <a name="cause"></a>Causa
 Le chiamate ai metodi System.Reflection, ad esempio InvokeMember e GetMember, o ai metodi Type, ad esempio MemberInvoke, costituiscono una percentuale significativa dei dati di profilatura. Ove possibile considerare la possibilità di sostituire questi metodi con associazione anticipata ai metodi di assembly dipendenti.

## <a name="rule-description"></a>Descrizione della regola
 La reflection è una funzionalità flessibile di .NET Framework che può essere usata per eseguire l'associazione tardiva dell'applicazione a un assembly di runtime dipendente oppure per creare ed eseguire dinamicamente nuovi tipi durante il runtime. Tuttavia, queste tecniche possono ridurre le prestazioni se vengono usate frequentemente o chiamate in cicli ridotti.

 Per altre informazioni, vedere la sezione [Reflection and Late Binding](/previous-versions/msp-n-p/ff647790(v=pandp.10)#reflection-and-late-binding) (Reflection e associazione tardiva) in Chapter 5 - Improving Managed Code Performance (Capitolo 5 - Miglioramento delle prestazioni del codice gestito) nel volume Improving .NET Application Performance and Scalability (Miglioramento delle prestazioni e della scalabilità delle applicazioni .NET) della libreria Microsoft Patterns and Practices in MSDN.

## <a name="how-to-investigate-a-warning"></a>Come esaminare un avviso
 Fare doppio clic sul messaggio nella finestra Elenco errori per passare alla [visualizzazione Dettagli funzione](../profiling/function-details-view.md) dei dati di profilatura. Esaminare le funzioni chiamanti del metodo System.Type o System.Reflection per trovare le sezioni del programma che fanno maggior uso delle API Reflection di .NET. Evitare di usare metodi che restituiscono metadati. Quando le prestazioni dell'applicazione sono di importanza fondamentale potrebbe essere necessario evitare l'uso dell'associazione tardiva e la creazione dinamica di tipi durante il runtime.
