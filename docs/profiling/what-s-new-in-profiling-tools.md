---
title: Novità per la profilatura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling
- what's new
ms.assetid: d4736cc8-8961-4089-be9e-d5190ce8353c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ec85de208c7761b69a73cc17a72bdb4a59fe6bb4
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="whats-new-in-profiling-tools-in-includevsdev15miscincludesvsdev15mdmd"></a>Novità negli strumenti di profilatura di [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]
Gli strumenti di diagnostica includono nuove visualizzazioni che consentono di identificare i problemi da risolvere nell'app. Gli strumenti di diagnostica ora includono il supporto per le app ASP.NET.

Per altre informazioni, vedere le [Note sulla versione per [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes#debuggingdiag).

È stata aggiunta agli strumenti una scheda **Riepilogo**, che consente di concentrarsi sulle aree principali per l'analisi delle prestazioni. Questa scheda mostra il numero di eventi si sono verificati, consente di creare snapshot dell'heap e consente di abilitare rapidamente la raccolta dei dati di utilizzo della CPU. Questa visualizzazione mostra eventuali eventi di [Application Insights](https://azure.microsoft.com/en-us/documentation/articles/app-insights-visual-studio/) o di [Analisi interfaccia utente](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes#UIAnalysis). Inoltre, per Visual Studio Enterprise, questa visualizzazione mostra anche gli eventi di IntelliTrace.

![Strumenti di diagnostica Scheda Riepilogo](../profiling/media/DiagToolsSummaryTab-2.png "DiagToolsSummaryTab")

Lo strumento Utilizzo CPU dispone di [nuove visualizzazioni](../profiling/Beginners-Guide-to-Performance-Profiling.md) che aiutano a identificare le funzioni che possono causare problemi di prestazioni. La nuova visualizzazione **Chiamante/chiamato** consente di analizzare i costi delle chiamate di funzione effettuate da e verso una funzione selezionata.

![Strumenti di diagnostica Visualizzazione Chiamante Chiamato](../profiling/media/DiagToolsCallerCallee.png "DiagToolsCallerCallee")
  
## <a name="see-also"></a>Vedere anche  
 [Profilatura in Visual Studio](../profiling/index.md)  
 [Tour delle funzionalità di profilatura](../profiling/profiling-feature-tour.md)