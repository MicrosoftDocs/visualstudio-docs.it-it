---
title: 'DA0502: Consumo massimo CPU del processo sottoposto a profilatura | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.rules.DA0502
- vs.performance.DA0502
- vs.performance.502
ms.assetid: 1ee53df5-b0dc-4265-9d4f-527830d08725
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: cb9e860afcd88b50b324f1d2b62c6d95a55c270f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="da0502-maximum-cpu-consumption-by-the-process-being-profiled"></a>DA0502: Consumo massimo CPU del processo sottoposto a profilatura
|||  
|-|-|  
|ID regola|DA0502|  
|Category|Monitoraggio risorse|  
|Metodo di profilatura|Tutti|  
|Messaggio|Regola a solo scopo informativo. Il contatore di tempo processore Process()\\% misura il consumo di CPU del processo sottoposto a profilatura. Il valore restituito corrisponde al valore massimo osservato per tutti gli intervalli di misurazione.|  
|Tipo regola|Informativo|  
  
 Quando si esegue la profilatura tramite i metodi di campionamento, memoria .NET o conflitto di risorse, è necessario raccogliere almeno 10 campioni per attivare questa regola.  
  
## <a name="rule-description"></a>Descrizione della regola  
 In questo messaggio viene indicata la percentuale massima di tempo impiegato da un processore per l'esecuzione di istruzioni dall'applicazione. Il valore indicato è il valore massimo segnalato fra tutti gli intervalli di misurazione nei quali il processo sottoposto a profilatura era attivo. In un computer con più processori la percentuale può essere maggiore del 100%.  
  
## <a name="how-to-use-the-rule-data"></a>Come usare i dati della regola  
 Usare il valore della regola per confrontare le prestazioni di versioni o build diverse del programma o per ottenere informazioni sulle prestazioni dell'applicazione in scenari di profilatura diversi.