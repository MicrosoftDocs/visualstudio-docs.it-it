---
title: Analizzare l'utilizzo della memoria in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 01/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: aac1c901f98d63b8cf77b41a165548cccede4f21
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2018
---
# <a name="analyze-memory-usage"></a>Analizzare l'uso della memoria
Usare lo strumento di diagnostica **Utilizzo memoria** integrato nel debugger per rilevare perdite di memoria e usi inefficienti della memoria. Lo strumento Utilizzo memoria consente di eseguire uno o più *snapshot* dell'heap di memoria gestito e nativo. È possibile raccogliere snapshot di app.NET, native o in modalità mista (.NET e native).  
  
-   È possibile analizzare un singolo snapshot per ottenere informazioni sull'impatto relativo dei tipi di oggetto sull'uso della memoria e per trovare nell'app il codice che usa la memoria in modo non efficiente.  
  
-   È anche possibile confrontare (diff) due snapshot di un'app per trovare le aree del codice che provocano l'incremento dell'uso della memoria nel tempo.  

Per istruzioni dettagliate, vedere l'esercitazione sull'[analisi dell'uso della memoria](../profiling/memory-usage.md). Per analizzare l'uso della memoria senza collegare il debugger, vedere [Utilizzo della memoria senza il debugger](memory-usage-without-debugging2.md).
  
## <a name="blogs-and-videos"></a>Blog e video  

|         |         |
|---------|---------|
|  ![icona della telecamera](../install/media/video-icon.png "Guardare un video")  |    [Guardare un video](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Profiling-with-Diagnostics-Tools-in-Visual-Studio-2017-daHnzMD6D_9211787171) sull'uso degli strumenti di diagnostica che illustra come analizzare l'uso della memoria e della CPU in Visual Studio 2017. |

 [Analizzare CPU e memoria in fase di debug](https://blogs.msdn.microsoft.com/visualstudio/2016/02/15/analyze-cpu-memory-while-debugging/)  
  
 [Blog su Visual C++: profilatura della memoria in Visual C++ 2015](https://blogs.msdn.microsoft.com/vcblog/2015/10/21/memory-profiling-in-visual-c-2015/)  

## <a name="see-also"></a>Vedere anche
 [Profilatura in Visual Studio](../profiling/index.md)  
 [Tour delle funzionalità di profilatura](../profiling/profiling-feature-tour.md)