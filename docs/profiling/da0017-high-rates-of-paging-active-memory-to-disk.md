---
title: 'DA0017: Frequenze elevate di paging di memoria attiva su disco | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.17
- vs.performance.rules.DA0017
- vs.performance.DA0017
ms.assetid: 01011eec-5930-43b3-980d-2cb01e2ca7f6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1e962cfe761af48f5c7aa02d1e476c33e1bf9f4a
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="da0017-high-rates-of-paging-active-memory-to-disk"></a>DA0017: Frequenze elevate di paging di memoria attiva su disco
|||  
|-|-|  
|ID regola|DA0017|  
|Category|Memoria e paging|  
|Metodo di profilatura|Tutti|  
|Messaggio|È stata rilevata una frequenza elevata di paging di memoria attiva su disco. L'applicazione potrebbe essere associata alla memoria.|  
|Tipo regola|Informazioni|  
  
 Quando si esegue la profilatura tramite i metodi di campionamento, memoria .NET o conflitto di risorse, è necessario raccogliere almeno 10 campioni per attivare questa regola.  
  
## <a name="cause"></a>Causa  
 I dati relativi alle prestazioni di sistema raccolti nell'esecuzione della profilatura indicano che si è verificata una frequenza elevata di paging di memoria attiva da e su disco durante la profilatura. Le frequenze di paging a questo livello hanno un impatto sulle prestazioni e sulla capacità di risposta dell'applicazione. È consigliabile ridurre le allocazioni di memoria rivedendo gli algoritmi. Potrebbe inoltre essere necessario esaminare i requisiti di memoria dell'applicazione.  
  
## <a name="rule-description"></a>Descrizione della regola  
  
> [!NOTE]
>  Questa regola informativa viene attivata quando i livelli di paging di memoria attiva raggiungono una quantità significativa. Quando si verifica un livello di paging estremamente elevato, viene attivata invece la regola di avviso [DA0014: Frequenze molto elevate di paging di memoria attiva su disco](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md).  
  
 Un'attività di paging su disco eccessiva può essere causata da memoria fisica insufficiente. Se le operazioni di paging usano in modo dominante il disco fisico su cui risiede il file di paging, possono rallentare le altre operazioni del disco orientate all'applicazione sullo stesso disco.  
  
 Le pagine vengono spesso lette dal disco o scritte nel disco mediante operazioni di paging in blocco. Ad esempio, il numero di output di pagine al secondo è spesso maggiore del numero di scritture di pagine al secondo. Ciò avviene perché il numero di pagine generate al secondo include anche le pagine di dati modificate dalla cache dei file di sistema. Tuttavia, non è sempre facile determinare quale processo è direttamente responsabile del paging o perché.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Fare doppio clic sul messaggio nella finestra Elenco errori per passare alla visualizzazione [Contrassegni](../profiling/marks-view.md). Individuare la colonna **Memoria\Pagine/sec**. Determinare se sono presenti fasi specifiche di esecuzione del programma in cui l'attività I/O di paging è più elevata rispetto ad altre fasi.  
  
 Se si raccolgono dati del profilo per un'applicazione ASP.NET in un scenario del test di carico, provare a eseguire nuovamente il test di carico su un computer configurato con memoria fisica (o RAM) aggiuntiva.  
  
 È consigliabile ridurre le allocazioni di memoria rivedendo gli algoritmi ed evitando API che usano molta memoria, ad esempio String.Concat e String.Substring.