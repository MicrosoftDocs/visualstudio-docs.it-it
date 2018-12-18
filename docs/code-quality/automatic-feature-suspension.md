---
title: "Sospensione di funzionalità automatico | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
caps.latest.revision: "6"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-code-analysis
ms.workload: multiple
ms.openlocfilehash: 0bb8155f2ec1ed6815ac37f1124dfbf57cf838b2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="automatic-feature-suspension"></a>Sospensione di funzionalità automatico
Se la memoria di sistema disponibile è pari o inferiore a 200MB, Visual Studio visualizza il messaggio seguente nell'editor di codice.  
  
 ![Avviso di analisi della soluzione completa di sospensione](../code-quality/media/fsa_alert.png "FSA_Alert")  
  
 Quando Visual Studio rileva una condizione di memoria insufficiente, viene automaticamente sospeso alcune funzionalità avanzate che consenta di rimane stabile. Quando questo avanzate funzionalità sospensione avviso viene visualizzato, Visual Studio continueranno a funzionare come prima, ma le prestazioni risultano leggermente inferiori.  
  
 In una condizione di memoria insufficiente, si verifica quanto segue:  
  
-   Analisi della soluzione completa per Visual c# e Visual Basic sono disabilitata.  
  
-   [Operazione di Garbage Collection](/dotnet/standard/garbage-collection/index) modalità di bassa latenza (GC) per Visual c# e Visual Basic sono disabilitati.  
  
-   Vengono scaricate le cache di Visual Studio.  
  
## <a name="improve-visual-studio-performance"></a>Migliorare le prestazioni di Visual Studio  
 Per suggerimenti e consigli su come migliorare le prestazioni di Visual Studio quando si lavora con soluzioni di grandi dimensioni o condizioni di memoria insufficiente, vedere [considerazioni sulle prestazioni per soluzioni di grandi dimensioni](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).  
  
## <a name="full-solution-analysis-suspended"></a>Analisi della soluzione completa sospeso  
 Per impostazione predefinita, l'analisi della soluzione completa sono abilitato per Visual Basic e disabilitato per Visual c#. Tuttavia, in una condizione di memoria insufficiente, analisi della soluzione completa viene disabilitata automaticamente per Visual Basic e Visual c#, indipendentemente dalle impostazioni nella finestra di dialogo Opzioni. Tuttavia, è possibile abilitare nuovamente analisi della soluzione completa, scegliendo il **riabilitare** pulsante Info bar quando viene visualizzato, selezionando il **abilitare l'analisi della soluzione completa** casella di controllo nella finestra di dialogo Opzioni, o Riavviare Visual Studio. La finestra di dialogo Opzioni Mostra sempre soluzione completa corrente le impostazioni di analisi. Per ulteriori informazioni, vedere [procedura: abilitare e disabilitare analisi completa della soluzione](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).  
  
## <a name="gc-low-latency-disabled"></a>Garbage Collection a bassa latenza disabilitata  
 Per abilitare nuovamente la modalità di bassa latenza GC, riavviare Visual Studio.  Per impostazione predefinita, Visual Studio consente di modalità di bassa latenza di Garbage Collection ogni volta che si sta digitando per assicurarsi che il testo digitato non blocca le operazioni di Garbage Collection. Tuttavia, se una condizione di memoria insufficiente causa Visual Studio visualizzare l'avviso di sospensione automatica, modalità di bassa latenza di Garbage Collection è disabilitata per la sessione. Riavviare Visual Studio, il comportamento di catalogo globale predefinito verrà riattivata. Per ulteriori informazioni, vedere [GCLatencyMode enumerazione](http://msdn.microsoft.com/Library/057757a5-cd62-4d13-8a40-370eb7f47c87).  
  
## <a name="visual-studio-caches-flushed"></a>Cache di Visual Studio scaricate  
 Tutte le cache di Visual Studio vengono svuotate immediatamente, ma saranno necessario ripopolare se continuare la sessione corrente di sviluppo o riavviare Visual Studio. Le cache scaricate includono cache per le funzionalità seguenti.  
  
-   Trova tutti i riferimenti  
  
-   Passa a  
  
-   Aggiungi Using  
  
 Inoltre, vengono cancellati cache usati per le operazioni interne di Visual Studio.  
  
> [!NOTE]
>  L'avviso di sospensione funzionalità automatico si verifica solo una volta su base per ogni soluzione, non su una base per ogni sessione. Ciò significa che se si passa da Visual Basic, Visual c# (o viceversa) e un'altra condizione di memoria insufficiente, è possibile ottenere probabilmente un altro avviso di sospensione di funzionalità automatiche.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: abilitare e disabilitare l'analisi della soluzione completa](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)   
 [Principi fondamentali di Garbage Collection](/dotnet/standard/garbage-collection/fundamentals)   
 [Considerazioni sulle prestazioni per soluzioni di grandi dimensioni](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)