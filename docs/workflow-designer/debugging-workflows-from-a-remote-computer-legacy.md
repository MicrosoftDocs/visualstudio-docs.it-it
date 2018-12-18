---
title: Debug dei flussi di lavoro da un Computer remoto (Legacy) | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- workflows, debugging remotely
- debugging workflows, remotely
- remote debugging, workflows
- debugging, remote
ms.assetid: 44eaec8f-9959-4ae7-a374-670946f933c1
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: b4b9207702e6b4c3b93838eccfe1da15c42b5baa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-workflows-from-a-remote-computer-legacy"></a>Esecuzione del debug dei flussi di lavoro da computer remoto (legacy)
In questo argomento viene descritto come eseguire il debug di applicazioni [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] legacy remote che sono compilate con la [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] legacy. Usare la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] legacy quando l'applicazione deve fare riferimento a [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Quando si installa [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)], una delle opzioni di installazione del componente consiste nell'installare il [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] del Debugger per [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]. In questo modo vengono installati i componenti di debug remoto. Questi componenti di debug remoto devono essere installati nel computer nel quale si desidera eseguire il debug del flusso di lavoro remoto.  
  
 Inoltre, l'assembly contenente la definizione del flusso di lavoro del flusso di lavoro legacy per il quale si sta eseguendo il debug in un computer remoto deve essere installato nella Global Assembly Cache (GAC) del computer locale dal quale si sta eseguendo il debug. Ad esempio, se un flusso di lavoro legacy è in esecuzione nel computer remoto A e si sta eseguendo il debug da un computer locale B, la definizione del flusso di lavoro deve essere presente nella GAC del computer B. Ciò consente alla finestra di progettazione di deserializzare e visualizzare sul computer B il markup del flusso di lavoro in esecuzione in modalità remota nel computer A. Per ulteriori informazioni sulla Global Assembly Cache, visitare il sito MSDN Library.  
  
 Il debug remoto di [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] funziona nello stesso modo del debug remoto per altri componenti [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Per ulteriori informazioni, vedere [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] debug remoto in MSDN Library.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug dei flussi di lavoro legacy](../workflow-designer/debugging-legacy-workflows.md)