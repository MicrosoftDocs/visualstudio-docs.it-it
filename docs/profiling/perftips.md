---
title: PerfTips | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 509d2d4f-48a5-4cdf-acad-6f7b75421303
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 81e5f0696db8f8e29204f9fbed49cc347a4afb74
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="perftips"></a>PerfTips
Il debugger di Visual Studio *PerfTips* e il debugger integrato **Strumenti di diagnostica** consentono di monitorare e analizzare le prestazioni dell'app durante il debug.  
  
 Anche se gli strumenti di diagnostica integrati debugger sono un ottimo modo per acquisire consapevolezza dei problemi di prestazioni durante lo sviluppo, il debugger può avere un impatto significativo sulle prestazioni dell'applicazione. Per raccogliere dati più accurati sulle prestazioni, è consigliabile usare gli strumenti di diagnostica di Visual Studio che vengono eseguiti all'esterno del debugger troppo come un'ulteriore indicazione le indagini sulle prestazioni. Vedere [Esecuzione degli strumenti di profilatura con o senza il debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md).  
  
## <a name="perftips"></a>PerfTips  
 Quando il debugger interrompe l'esecuzione in un punto di interruzione o un'operazione passo a passo, il tempo trascorso tra l'interruzione e il precedente punto di interruzione viene visualizzato come un suggerimento nella finestra dell'editor. Per altre informazioni, vedere [PerfTips, informazioni immediate sulle prestazioni durante il debug in Visual Studio](http://blogs.msdn.com/b/visualstudioalm/archive/2014/08/18/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio.aspx).  
  
 ![PerfTip](../profiling/media/dbgdiag_perf_perftip.png "DBGDIAG_PERF_PerfTip")  
  
## <a name="diagnostics-tools-window"></a>Finestra Strumenti di diagnostica  
 I punti di interruzione e i dati di intervallo associati vengono registrati nella finestra Strumenti di diagnostica  
  
 Il grafico seguente mostra la finestra Strumenti di diagnostica in Visual Studio 2015 Update 1:  
  
 ![DiagnosticTools&#45;Update1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-Update1")  
  
-   La sequenza temporale **Eventi di interruzione** contrassegnano i punti di interruzione che vengono eseguiti nella sessione di debug. Fare clic su un evento per selezionare l’elenco dei dettagli **Debugger** .  
  
-   Il grafico **Utilizzo CPU** mostra la modifica di uso della CPU tra tutti i core di processori nella sessione di debug.  
  
-   L’elenco **Eventi** del riquadro dettagli **Debugger** include gli elementi per ogni evento di interruzione.  
  
-   La colonna **Durata** di un evento di interruzione visualizza il tempo trascorso tra l'evento e il punto di interruzione precedente.  
  
## <a name="turn-perftips-on-or-off"></a>Attivare o disattivare PerfTips  
 Per abilitare o disabilitare PerfTips:  
  
1.  Scegliere **Opzioni** dal menu **Debug**.  
  
2.  Selezionare o deselezionare **Mostra il PerfTip relativo al tempo trascorso durante il debug**.  
  
## <a name="turn-the-diagnostic-tools-window-on-or-off"></a>Attivare o disattivare la finestra Strumenti di diagnostica  
 Per attivare o disattivare la finestra Strumenti di diagnostica:  
  
1.  Scegliere **Opzioni** dal menu **Debug**.  
  
2.  Selezionare o deselezionare **Abilita Strumenti di diagnostica durante il debug**.

## <a name="see-also"></a>Vedere anche
 [Profilatura in Visual Studio](../profiling/index.md)  
 [Tour delle funzionalità di profilatura](../profiling/profiling-feature-tour.md)
