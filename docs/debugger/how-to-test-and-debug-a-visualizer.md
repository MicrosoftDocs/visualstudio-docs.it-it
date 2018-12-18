---
title: 'Procedura: testare ed eseguire il Debug di un visualizzatore | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- visualizers, testing
- visualizers, debugging
- debugging [Visual Studio], visualizers
ms.assetid: 5cc12ce8-c819-48e4-b487-98d403001b28
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 860d6bd5f89ff85f3abf75f1beceb62b6b860d54
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-test-and-debug-a-visualizer"></a>Procedura: testare un visualizzatore ed eseguirne il debug
Dopo avere scritto un visualizzatore, è necessario testarlo ed eseguirne il debug.  
  
 Una possibile soluzione per testare un visualizzatore consiste nell'installarlo in Visual Studio e nel chiamarlo da un finestra del debugger. (Vedere [procedura: installare un visualizzatore](../debugger/how-to-install-a-visualizer.md).) Se si sceglie questa soluzione, sarà necessario utilizzare una seconda istanza di Visual Studio per la connessione e il debug del visualizzatore, che verrà eseguito nella prima istanza del debugger.  
  
 Una soluzione più semplice per il debug di un visualizzatore consiste nell'eseguire il visualizzatore da un driver di test. L'API del Visualizzatore semplificano la creazione di un driver di questo tipo, che viene chiamato il *host di sviluppo del visualizzatore*.  
  
### <a name="to-create-a-visualizer-development-host"></a>Per creare un host di sviluppo del visualizzatore  
  
1.  Nella classe del lato debugger includere un metodo statico che consenta di creare un oggetto <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerDevelopmentHost> e di chiamare il relativo metodo di visualizzazione:  
  
    ```  
    public static void TestShowVisualizer(object objectToVisualize)  
    {  
       VisualizerDevelopmentHost myHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));  
       myHost.ShowVisualizer();  
    }  
    ```  
  
     Come parametri per la costruzione dell'host vengono utilizzati l'oggetto dati che verrà mostrato nel visualizzatore (`objectToVisualize`) e il tipo della classe del lato debugger.  
  
2.  Aggiungere l'istruzione riportata di seguito per chiamare `TestShowVisualizer`. Se il visualizzatore è stato creato in una libreria di classi, sarà necessario creare un eseguibile per chiamare la libreria di classi e inserire questa istruzione nell'eseguibile:  
  
    ```  
    DebuggerSide.TestShowVisualizer(myString);  
    ```  
  
     Per un esempio più esaustivo, vedere [procedura dettagliata: scrittura di un visualizzatore in c#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Scrittura di un visualizzatore in c#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)   
 [Procedura: installare un visualizzatore](../debugger/how-to-install-a-visualizer.md)   
 [Creazione di visualizzatori personalizzati](../debugger/create-custom-visualizers-of-data.md)