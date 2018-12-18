---
title: Visualizzazione Chiamante/chiamato | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.callercallee
helpviewer_keywords:
- profiling tools, reports, Caller/Callee view
- profiling tools, Caller/Callee view
- performance reports, Caller/Callee view
- Caller/Callee view
ms.assetid: d3511bcf-cce0-4cbe-aecb-b94c7c80ad1b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 34920cfd91c236df4fc88d671d3cac48ebf02252
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="callercallee-view"></a>visualizzazione Chiamante/Chiamato
La visualizzazione Chiamante/chiamato consente di visualizzare informazioni di profilatura per una funzione selezionata e le relative funzioni padre e figlio. La visualizzazione Chiamante/chiamato contiene tre griglie:  
  
 Nella griglia centrale **Funzione corrente** visualizza le informazioni di profilatura per la funzione selezionata. I valori includono tutte le chiamate alla funzione che sono state raccolte nell'esecuzione della profilatura.  
  
 La griglia superiore contiene **Funzioni che hanno chiamato la funzione corrente**, che visualizza il numero di valori della funzione selezionata (corrente) generati da chiamate da parte della funzione chiamante (padre).  
  
 Nella griglia inferiore **Funzioni che sono state chiamate dalla funzione corrente** visualizza informazioni di profilatura per le funzioni chiamate (figlio) della funzione selezionata quando la funzione figlio è stata chiamata dalla funzione corrente.  
  
 Le colonne disponibili nella visualizzazione Chiamante/chiamato dipendono dal metodo di profilatura (campionamento o strumentazione) usato per raccogliere i dati e dal fatto che i dati della memoria .NET siano stati raccolti o meno durante l'esecuzione della profilatura.  
  
 È possibile selezionare un'altra funzione come funzione corrente nella parte centrale della visualizzazione report facendo doppio clic su una delle funzioni elencate nelle altre due parti della visualizzazione. La visualizzazione report viene automaticamente aggiornata in base alle modifiche.  
  
 Per ordinare i dati è possibile fare clic sui nomi delle colonne. È possibile aggiungere altre colonne alla visualizzazione Chiamante/chiamato. Per altre informazioni, vedere [Procedura: Personalizzare colonne della visualizzazione report](../profiling/how-to-customize-report-view-columns.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione Chiamante/chiamato: dati di campionamento](../profiling/caller-callee-view-sampling-data.md)   
 [Visualizzazione Chiamante/chiamato: dati di strumentazione](../profiling/caller-callee-view-instrumentation-data.md)   
 [Visualizzazione Chiamante/chiamato: dati di strumentazione di memoria .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Visualizzazione Chiamante/chiamato: dati di campionamento di memoria .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Visualizzazione Chiamante/chiamato: dati sui conflitti](../profiling/caller-callee-view-contention-data.md)