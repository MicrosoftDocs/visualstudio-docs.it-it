---
title: 'Procedura: Creare un report calltrace degli strumenti di profilatura | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance tools, viewing ETW data
- ETW [Visual Studio ALM], viewing data
ms.assetid: 7640520a-7d3c-456c-b184-872a5d2f82f3
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 21eb9883e445e799487a358e4e343754afd3ec2a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-profiling-tools-call-trace-report"></a>Procedura: Creare un rapporto calltrace degli strumenti di profilatura
Il *report calltrace* per gli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] elenca le informazioni di intervallo per ogni punto di ingresso e di uscita delle funzioni dell'applicazione e ogni chiamata ad altre funzioni da parte di una determinata funzione. I report calltrace sono disponibili per i dati di profilatura solo se sono stati raccolti con il metodo di strumentazione.  
  
> [!NOTE]
>  Non è possibile visualizzare i report calltrace in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. È necessario usare lo strumento da riga di comando **VSPerfReport** per generare un file con valori delimitati da virgole (file con estensione csv) o un file XML. Per altre informazioni su questo strumento, vedere [VSPerfReport](../profiling/vsperfreport.md).  
  
### <a name="to-create-a-call-trace-report"></a>Per creare un report calltrace  
  
1.  Aprire una finestra del **prompt dei comandi**.  
  
2.  Al prompt dei comandi digitare il seguente comando:  
  
     *ToolsPath* **VSPerfReport** *VSPFile*  **/CallTrace [/Xml]**  
  
    |||  
    |-|-|  
    |*ToolsPath*|Percorso degli strumenti da riga di comando degli strumenti di profilatura. Per altre informazioni, vedere [Specifica del percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|  
    |*VSPFile*|File (con estensione vsp o vsps) dei dati di profilatura. Sono accettati percorsi completi e parziali.|  
    |Xml|Genera un report in formato XML.|  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Raccogliere dati ETW (Event Tracing for Windows)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)   
 [API degli strumenti di profilatura](../profiling/profiling-tools-apis.md)