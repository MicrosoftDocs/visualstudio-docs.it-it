---
title: 'DA0018: Applicazione a 32 bit in esecuzione al limite di memoria gestito dal processo | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.18
- vs.performance.DA0018
- vs.performance.rules.DA0018
ms.assetid: 98eb2d96-f92f-42f9-915c-e5ac2330ffbf
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: ba328ae4b54728422e032741e20543b99f49d5ae
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="da0018-32-bit-application-running-at-process-managed-memory-limits"></a>DA0018: Applicazione a 32 bit in esecuzione al limite di memoria gestito dal processo
|||  
|-|-|  
|ID regola|DA0018|  
|Category|Uso degli strumenti di profilatura|  
|Metodo di profilatura|Campionamento|  
|Messaggio|Le allocazioni di memoria gestita hanno quasi raggiunto il limite predefinito per un processo a 32 bit. L'applicazione potrebbe essere associata alla memoria.|  
|Tipo regola|Avviso|  
  
 Quando si esegue la profilatura tramite i metodi di campionamento, memoria .NET o conflitto di risorse, è necessario raccogliere almeno 10 campioni per attivare questa regola.  
  
## <a name="cause"></a>Causa  
 I dati di sistema raccolti durante l'esecuzione della profilatura indicano che gli heap di memoria di .NET Framework hanno quasi raggiunto la dimensione massima consentita per gli heap gestiti in un processo a 32 bit. Questa dimensione massima è un valore predefinito. Il valore è basato sulla quantità totale dello spazio degli indirizzi del processo che può essere allocata per i byte privati. Il valore indicato è il massimo valore degli heap osservato durante l'attività del processo profilato. È consigliabile eseguire di nuovo la profilatura usando il metodo di profilatura della memoria di .NET e ottimizzare l'utilizzo delle risorse gestite dall'applicazione.  
  
 Quando la dimensione degli heap gestiti si avvicina al limite predefinito, potrebbe essere necessario richiamare più frequentemente il processo di Garbage Collection automatico. In questo modo viene aumentato il sovraccarico di gestione della memoria.  
  
 La regola viene attivata solo per applicazioni a 32 bit in esecuzione su computer a 32 bit.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Common Language Runtime (CLR) di Microsoft .NET offre un meccanismo di gestione automatica della memoria che usa un Garbage Collector per recuperare memoria da oggetti che non vengono più usati dall'applicazione. Il Garbage Collector è orientato alla generazione, basandosi sull'ipotesi che molte allocazioni sono di breve durata. Le variabili locali, ad esempio, dovrebbero essere di breve durata. Gli oggetti appena creati vengono avviati in generazione 0 (gen 0), quindi avanzano a generazione 1 se vengono conservati dopo l'esecuzione di un'operazione di Garbage Collection e infine passano a generazione 2 se sono ancora usati dall'applicazione.  
  
 Gli oggetti gestiti maggiori di 85 KB vengono allocati nell'heap oggetti grandi, dove sono soggetti a Garbage Collection e a compressione meno frequenti rispetto agli oggetti più piccoli. Gli oggetti grandi vengono gestiti separatamente perché si presuppone che siano più persistenti e perché la combinazione di oggetti grandi e persistenti con oggetti più piccoli allocati frequentemente potrebbe produrre una frammentazione indesiderata dell'heap.  
  
 Quando la dimensione totale degli heap gestiti si avvicina al limite predefinito, il sovraccarico di gestione della memoria aumenta di solito a un punto tale che potrebbe iniziare ad avere un impatto sulla capacità di risposta e sulla scalabilità dell'applicazione.  
  
## <a name="how-to-investigate-a-warning"></a>Come esaminare un avviso  
 Fare doppio clic sul messaggio nella finestra Elenco errori per passare alla visualizzazione [Contrassegni](../profiling/marks-view.md). Individuare le colonne **Memoria CLR .NET\\Byte in tutti gli heap** e **Totale byte di cui è stato eseguito il commit**. Determinare se sono presenti fasi specifiche di esecuzione del programma in cui l'allocazione di memoria gestita è maggiore rispetto ad altre fasi. Confrontare i valori della colonna **Byte in tutti gli heap** con la frequenza di Garbage Collection indicata nelle colonne **Memoria CLR .NET\\Raccolte di generazione 0**, **Memoria CLR .NET\\Raccolte di generazione 1** e **Memoria CLR .NET\\Raccolte di generazione 2** per determinare se il modello di allocazioni di memoria gestita incide sulla frequenza di Garbage Collection.  
  
 In un'applicazione .NET Framework, Common Language Runtime limita la dimensione totale degli heap gestiti a un valore leggermente inferiore a metà della dimensione massima della parte di area privata di uno spazio degli indirizzi del processo. Per i processi a 32 bit in esecuzione su un computer a 32 bit, il limite superiore della parte privata dello spazio degli indirizzi del processo è di 2 GB. Quando la dimensione totale degli heap gestiti si avvicina al limite predefinito, il sovraccarico di gestione della memoria può aumentare e le prestazioni dell'applicazione possono diminuire.  
  
 Se l'eccessivo sovraccarico della memoria gestita costituisce un problema, considerare una delle opzioni seguenti:  
  
-   ottimizzazione dell'uso delle risorse di memoria gestita da parte dell'applicazione  
  
     oppure  
  
-   esecuzione di procedure per limitare i vincoli architettonici alla dimensione massima della memoria virtuale per un processo a 32 bit  
  
 Per ottimizzare l'uso delle risorse di memoria gestita da parte dell'applicazione, raccogliere i dati di allocazione della memoria gestita con un'esecuzione della profilatura dell'allocazione di memoria di .NET. Rivedere i report delle [Visualizzazioni dei dati di memoria .NET](../profiling/dotnet-memory-data-views.md) per comprendere il modello di allocazione di memoria dell'applicazione.  
  
 Usare la [Visualizzazione Durata oggetti](../profiling/object-lifetime-view.md) per determinare quali oggetti dati del programma vengono mantenuti nella generazione e verranno quindi recuperati.  
  
 Usare la [Visualizzazione Allocazioni](../profiling/dotnet-memory-allocations-view.md) per determinare il percorso di esecuzione che ha comportato queste allocazioni.  
  
 Per altre informazioni su come migliorare le prestazioni di Garbage Collection, vedere l'articolo tecnico di .NET Framework, [Garbage Collector Basics and Performance Hints](http://go.microsoft.com/fwlink/?LinkId=177946) (Nozioni fondamentali su Garbage Collector e suggerimenti sulle prestazioni) sul sito Web MSDN.  
  
 Per limitare i vincoli della memoria virtuale sull'architettura alla dimensione della parte privata di uno spazio degli indirizzi del processo, provare a eseguire questo processo a 32 bit su un computer a 64 bit.  Un processo a 32 bit su un computer a 64 bit può acquisire fino a 4 GB di memoria virtuale privata.  
  
 Un processo a 64 bit eseguito su un computer a 64 bit può acquisire fino a 8 TB di memoria virtuale. È consigliabile compilare di nuovo l'applicazione in modo che venga eseguita come un'applicazione a 64 bit nativa. Questa regola è solo a scopo informativo e potrebbe non richiedere azione correttiva.