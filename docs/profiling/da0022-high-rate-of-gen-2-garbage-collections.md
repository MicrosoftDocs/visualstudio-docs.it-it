---
title: 'DA0022: Frequenza elevata di Garbage Collection di generazione 2 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0022
- vs.performance.rules.DA0022
- vs.performance.22
ms.assetid: f871a547-0e6f-4b11-b2d7-174d30fc2ed8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9cd868c55e62f673e8818126f791c889380548e9
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="da0022-high-rate-of-gen-2-garbage-collections"></a>DA0022: Frequenza elevata di Garbage Collection di generazione 2
|||  
|-|-|  
|ID regola|DA0022|  
|Category|Uso di .NET Framework|  
|Metodo di profilatura|Tutti|  
|Messaggio|È stata rilevata una frequenza elevata di Garbage Collection di generazione 2. In genere, ciò avviene se la maggior parte delle strutture dati del programma sono allocate e rese persistenti per molto tempo per progettazione. Tuttavia, se tale comportamento è imprevisto, l'applicazione potrebbe bloccare gli oggetti. Per altri dettagli, è possibile raccogliere dati sull'allocazione di memoria .NET e informazioni sulla durata degli oggetti per comprendere il criterio di allocazione della memoria usata dall'applicazione.|  
|Tipo regola|Avviso|  
  
 Quando si esegue la profilatura tramite i metodi di campionamento, memoria .NET o conflitto di risorse, è necessario raccogliere almeno 10 campioni per attivare questa regola.  
  
## <a name="cause"></a>Causa  
 I dati relativi alle prestazioni di sistema raccolti durante la profilatura indicano che una percentuale significativa della memoria per oggetti .NET Framework è stata recuperata nell'operazione di Garbage Collection di generazione 2 rispetto alle operazioni di Garbage Collection di generazione 0 e 1.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Common Language Runtime (CLR) di Microsoft .NET offre un meccanismo di gestione automatica della memoria che usa un Garbage Collector per recuperare memoria da oggetti che non vengono più usati dall'applicazione. Il Garbage Collector è orientato alla generazione, basandosi sull'ipotesi che molte allocazioni sono di breve durata. Le variabili locali, ad esempio, dovrebbero essere di breve durata. Gli oggetti appena creati vengono avviati in generazione 0 (gen 0), quindi avanzano a generazione 1 se vengono conservati dopo l'esecuzione di un'operazione di Garbage Collection e infine passano a generazione 2 se sono ancora usati dall'applicazione.  
  
 Gli oggetti in generazione 0 vengono raccolti frequentemente e in genere in modo molto efficace. Gli oggetti in generazione 1 vengono raccolti meno frequentemente e in modo meno efficace. Infine, gli oggetti di lunga durata in generazione 2 dovrebbero essere raccolti con una frequenza ancora inferiore. La raccolta in generazione 2, che è l'esecuzione di un'operazione di Garbage Collection completa, è anche l'operazione più costosa.  
  
 Questa regola viene attivata quando si verificano proporzionalmente troppe operazioni di Garbage Collection di generazione 2. Le applicazioni .NET Framework ben progettate avranno un numero di operazioni di Garbage Collection di generazione 1 cinque volte maggiore rispetto alle raccolte di generazione 2. Un fattore 10x è probabilmente ideale.  
  
## <a name="how-to-investigate-a-warning"></a>Come esaminare un avviso  
 Fare doppio clic sul messaggio nella finestra Elenco errori per passare alla [visualizzazione Contrassegni](../profiling/marks-view.md) dei dati di profilatura. Individuare le colonne **Memoria CLR .NET\\Raccolte di generazione 0** e **Memoria CLR .NET\\Raccolte di generazione 1**. Determinare se sono presenti fasi specifiche di esecuzione del programma in cui l'operazione di Garbage Collection si verifica più frequentemente. Confrontare questi valori con la colonna **% Time in GC** (% tempo in GC) per verificare se il modello di allocazioni della memoria gestita sta provocando un eccessivo sovraccarico della gestione della memoria.  
  
 Una percentuale elevata di Garbage Collection di generazione di 2 non è sempre un problema. Potrebbe essere stato definito in fase di progettazione. È possibile che questa regola venga attivata da un'applicazione che alloca strutture dei dati di grandi dimensioni che devono rimanere attive per i lunghi periodi durante l'esecuzione. Se nell'applicazione si verifica un utilizzo elevato di memoria, è possibile che venga imposta l'esecuzione di operazioni di Garbage Collection frequenti. Se le operazioni di Garbage Collection di generazione 0 e generazione 1 meno costose possono recuperare solo una piccola quantità memoria gestita, verranno pianificate operazioni più frequenti di Garbage Collection di generazione 2.  
  
 Nella visualizzazione Contrassegni sono presenti altre colonne Memoria CLR .NET che possono facilitare l'identificazione dei problemi di Garbage Collection. La colonna **% Time in GC** (% tempo in GC) consente di ottenere informazioni sull'incidenza dell'attuale sovraccarico di gestione della memoria. Se l'applicazione usa in genere un numero limitato di oggetti grandi ma persistenti, le raccolte frequenti di generazione 2 non dovranno usare quantità eccessive di tempo di CPU. Se nell'applicazione si verifica un utilizzo elevato di memoria perché è richiesta una maggiore quantità di memoria fisica (RAM), è possibile che vengano attivate anche regole correlate per la valutazione dei valori della colonna **Memoria\Pagine/sec**.  
  
 Per comprendere il modello di utilizzo della memoria gestita dell'applicazione, eseguire di nuovo la profilatura con un profilo di allocazione della memoria .NET e selezionare l'opzione di profilatura Durata oggetti.  
  
 Per informazioni su come migliorare le prestazioni di Garbage Collection, vedere [Garbage Collector Basics and Performance Hints](http://go.microsoft.com/fwlink/?LinkId=148226) (Nozioni fondamentali su Garbage Collection e suggerimenti sulle prestazioni) sul sito Web Microsoft. Per informazioni sul sovraccarico della procedura di Garbage Collection automatica, vedere [Large Object Heap Uncovered](http://go.microsoft.com/fwlink/?LinkId=177836) (Heap di oggetti grandi).