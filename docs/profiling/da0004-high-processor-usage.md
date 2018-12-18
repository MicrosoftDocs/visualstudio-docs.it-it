---
title: 'DA0004: Utilizzo elevato del processore | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAHighProcessorUsage
- vs.performance.rules.DA0004
- vs.performance.DA0004
- vs.performance.4
ms.assetid: 2c4fb569-929e-4f1d-8c50-b590ee371351
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dab522c19971e734e5a42f607d99f38f8e44930d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="da0004-high-processor-usage"></a>DA0004: Utilizzo elevato del processore
|||  
|-|-|  
|ID regola|DA0004|  
|Category|Uso degli strumenti di profilatura|  
|Metodi di profilatura|Strumentazione<br /><br /> Campionamento|  
|Messaggio|L'utilizzo del processore è costantemente superiore al 75%. Si consiglia di utilizzare la modalità di campionamento per le applicazioni basate sulla CPU.|  
|Tipo regola|Informazioni|  
  
 Quando si esegue la profilatura tramite i metodi di campionamento, memoria .NET o conflitto di risorse, è necessario raccogliere almeno 10 campioni per attivare questa regola.  
  
## <a name="cause"></a>Causa  
 L'utilizzo del processore (CPU) è significativamente elevato nei dati di profilatura raccolti usando il metodo di strumentazione. Si consiglia di usare il metodo di profilatura del campionamento per profilare applicazioni associate alla CPU.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Durante l'esecuzione della profilatura, il processore o i processori sono stati molto occupati in modo coerente. Un utilizzo della CPU elevato può indicare un'applicazione basata sulla CPU. In genere i profili instrumentati non rappresentano il modo più valido per esaminare gli scenari di utilizzo della CPU. Il campionamento di solito è più efficace quando si profilano applicazioni che per la maggior parte del tempo eseguono istruzioni sul processore.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Ad eccezione dei casi in cui è necessaria la temporizzazione della funzione o si è più interessati a comprendere l'input/output che i colli di bottiglia del processore, è consigliabile eseguire nuovamente la profilatura dell'applicazione usando il metodo di campionamento anziché il metodo di strumentazione.