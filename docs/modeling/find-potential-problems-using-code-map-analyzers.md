---
title: Trovare problemi potenziali usando gli analizzatore delle mappe codice
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.progression.codemapanalyzers
helpviewer_keywords:
- code analysis, dependency graphs
- dependency graphs, analyzing code
- graph documents, analyzing
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: a282c192b06f878279f567673469d223a71b8d89
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="find-potential-problems-using-code-map-analyzers"></a>Trovare problemi potenziali usando gli analizzatori di mappe codice
Eseguire gli analizzatori sulle mappe codice per identificare il codice che potrebbe essere eccessivamente complesso o che potrebbe richiedere un miglioramento. È possibile, ad esempio, usare gli analizzatori seguenti:

|**Per trovare codice con**|**Esaminare queste aree per vedere se**|
|-------------------------------|--------------------------------------------|
|Cicli o dipendenze circolari|È possibile semplificarli e stabilire se è possibile interrompere questi cicli.|
|Troppe dipendenze|Sono in esecuzione troppe funzioni o per determinare l'impatto della modifica di queste aree. Una mappa del codice corretto mostra un numero minimo di dipendenze. Per rendere il codice più facile da gestire, modificare, testare e riutilizzare, stabilire se effettuare il refactoring di queste aree in modo che siano definite più chiaramente o se è possibile unire codice che esegue funzioni simili.|
|Nessuna dipendenza|Sono necessarie o se è necessario rimuovere questo codice.|

## <a name="analyze-code-maps"></a>Analizzare mappe del codice

1.  Sulla barra degli strumenti della mappa scegliere **Layout**, **Analizzatori**e quindi l'analizzatore da eseguire:

    |**Analizzatore**|**Per identificare i nodi che**|
    |------------------|--------------------------------|
    |**Analizzatore Riferimenti circolari**|Hanno dipendenze circolari tra loro. **Nota:** dipendenze circolari che si trovano i **Generics** gruppo non vengono visualizzate sulla mappa quando si espande il gruppo.|
    |**Analizzatore Trova hub**|Rientrano nel primo 25% dei nodi con connessione elevata<br /><br /> **Per nascondere tutti gli altri nodi nella mappa**<br /><br /> -Aprire il menu di scelta rapida per la mappa, scegliere **avanzate**, **selezionare**, **Nascondi non selezionati**.<br />     La mappa consente di nascondere i nodi non selezionati e l'analizzatore identifica nuovi nodi come hub.|
    |**Analizzatore Nodi senza riferimenti**|Non contengono riferimenti da altri nodi. **Attenzione:** verificare ognuno di questi casi prima supponendo che il codice non viene utilizzato. Non è possibile trovare alcune dipendenze, ad esempio le dipendenze XAML e di runtime, in modo statico nel codice.|

 Gli analizzatori di mappe codice continueranno l'esecuzione una volta applicati. Se si modifica la mappa, eventuali analizzatori applicati automaticamente rielaboreranno la mappa aggiornata. Per interrompere l'esecuzione di un analizzatore, sulla barra degli strumenti mappa scegliere **Layout**, **Analizzatori**. Disattivare l'analizzatore selezionato.

> [!TIP]
> Se si ha una mappa di dimensioni molto grandi, l'esecuzione di un analizzatore potrebbe provocare un'eccezione per memoria insufficiente. In questo caso, modificare la mappa per ridurne l'ambito o generarne una di dimensioni più piccole e quindi eseguire l'analizzatore.

## <a name="see-also"></a>Vedere anche

- [Eseguire il mapping delle dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md)
- [Usare le mappe del codice per eseguire il debug delle applicazioni](../modeling/use-code-maps-to-debug-your-applications.md)
- [Mappare i metodi sullo stack di chiamate durante il debug](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
