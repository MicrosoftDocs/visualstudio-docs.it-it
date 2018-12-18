---
title: Creazione di file dei dati di profilatura portabili tramite la riga di comando | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2ceb63a7-b835-4988-b756-2afc3fcc4808
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 95302666d8bd5c5738f93a2fb0a8ec698c5bb7d9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="creating-portable-profiling-data-files-from-the-command-line"></a>Creazione di file dei dati di profilatura portabili tramite la riga di comando
Per semplificare la condivisione dei dati di profilatura è possibile usare lo strumento della riga di comando [VSPerfReport](../profiling/vsperfreport.md) per incorporare i simboli di un'esecuzione della profilatura nel file con estensione vsp.  
  
 È anche possibile creare un file di dati di profilatura preanalizzati (con estensione vsps), più piccolo e più facile da caricare nell'IDE.  
  
> [!NOTE]
>  Verificare che i file di simboli (con estensione pdb) siano disponibili per **VSPerfReport**. Per altre informazioni, vedere [Procedura: Specificare percorsi dei file di simboli tramite la riga di comando](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).  
>   
>  Per altre informazioni sul percorso di **VSReport**, vedere [Specifica del percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
>  Non è possibile filtrare i dati di profilatura di un file con estensione vsps.  
  
### <a name="to-embed-the-symbols-for-a-profiling-run-into-a-profiling-data-vsp-file"></a>Per incorporare i simboli per un'esecuzione della profilatura in un file di dati di profilatura (con estensione vsp)  
  
-   In una finestra del prompt dei comandi, digitare il comando seguente:  
  
     \<percorso>**VSPerfReport \<**file VSP> **/PackSymbols**  
  
     Per impostazione predefinita il file con estensione vsps è denominato con il nome base del file con estensione vsp. È possibile specificare un nome alternativo con l'opzione **Output**.  
  
### <a name="to-create-a-summary-profiling-data-file"></a>Per creare un file di riepilogo dati di profilatura  
  
-   In una finestra del prompt dei comandi, digitare il comando seguente:  
  
     \<percorso>**VSPerfReport \<**file VSP> **/SummaryFile** [**/Output:**\<nome file>]  
  
     Per impostazione predefinita il file con estensione vsps è denominato con il nome base del file con estensione vsp. È possibile specificare un nome alternativo con l'opzione **Output**.