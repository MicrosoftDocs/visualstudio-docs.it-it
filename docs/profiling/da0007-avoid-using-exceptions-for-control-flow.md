---
title: 'DA0007: Evitare di usare eccezioni per il flusso di controllo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAExceptionsThrown
- vs.performance.7
- vs.performance.rules.DA0007
- vs.performance.DA0007
ms.assetid: ee8ba8b5-2313-46c9-b129-3f3a2a232898
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7ae7b890e12d56e61571ecbf72dc1b0cd39567a4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53898203"
---
# <a name="da0007-avoid-using-exceptions-for-control-flow"></a>DA0007: Evitare di usare eccezioni per il flusso di controllo

|||  
|-|-|  
|ID regola|DA0007|  
|Category|Uso di .NET Framework|  
|Metodi di profilatura|Tutti|  
|Messaggio|Rilevato un elevato numero costante di eccezioni. Provare a ridurre l'utilizzo di eccezioni nella logica di programma.|  
|Tipo messaggio|Avviso|  

 Quando si esegue la profilatura tramite i metodi di campionamento, memoria .NET o conflitto di risorse, è necessario raccogliere almeno 25 campioni per attivare questa regola.  

## <a name="cause"></a>Causa  
 Nei dati di profilatura è stato chiamato un numero elevato di gestori di eccezioni di .NET Framework. Considerare la possibilità di usare un'altra logica di flusso di controllo per ridurre il numero di eccezioni generate.  

## <a name="rule-description"></a>Descrizione della regola  
 Sebbene l'uso di gestori di eccezioni per rilevare gli errori e di altri eventi che compromettono l'esecuzione del programma sia una procedura consigliata, l'uso di un gestore di eccezioni come parte della normale logica di esecuzione del programma può essere costoso e deve essere evitato. Nella maggior parte dei casi, le eccezioni devono essere usate solo in circostanze eccezionali e impreviste. Le eccezioni non devono essere usate per restituire valori come parte del flusso di programma normale. In molti casi per evitare la generazione di eccezioni è possibile convalidare i valori e usare logica condizionale per arrestare l'esecuzione delle istruzioni che provocano il problema.  

 Per altre informazioni, vedere la sezione [Exception Management](http://go.microsoft.com/fwlink/?LinkID=177825) (Gestione delle eccezioni) in **Chapter 5 - Improving Managed Code Performance** (Capitolo 5 - Miglioramento delle prestazioni del codice gestito) nel volume **Improving .NET Application Performance and Scalability** (Miglioramento delle prestazioni e della scalabilità delle applicazioni .NET) della libreria **Microsoft Patterns and Practices** in MSDN.  

## <a name="how-to-investigate-a-warning"></a>Come esaminare un avviso  
 Fare doppio clic sul messaggio nella finestra Elenco errori per passare alla visualizzazione Contrassegni. Trovare la colonna che contiene le misurazioni **Eccezioni CLR .NET(@ProcessInstance)\\Eccezioni / sec**. Determinare se sono presenti fasi specifiche di esecuzione del programma in cui la gestione delle eccezioni risulta più frequente rispetto alle altre fasi. Usando un profilo di campionamento, provare a identificare le istruzioni throw e i blocchi try/catch che generano eccezioni frequenti. Se necessario, aggiungere logica ai blocchi catch per individuare le eccezioni che vengono gestite più spesso. Dove possibile, sostituire le istruzioni throw o i blocchi catch eseguiti frequentemente con una logica di controllo di flusso o un codice di convalida a bassa complessità.  

 Ad esempio, se si rileva che l'applicazione sta gestendo eccezioni DivideByZeroException frequenti, per migliorare le prestazioni dell'applicazione è possibile aggiungere logica al programma per verificare la presenza di denominatori con valori zero.