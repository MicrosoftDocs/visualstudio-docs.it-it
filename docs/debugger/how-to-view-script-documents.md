---
title: 'Procedura: visualizzare documenti Script | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords: Script Explorer
ms.assetid: 8b621e53-4508-4b4a-9995-70995b0b9ac8
caps.latest.revision: "22"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7daecd0974abd5be733e7cec3426045c1f859eb8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-view-script-documents"></a>Procedura: visualizzare documenti script
Nelle versioni precedenti di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i file script sul lato client generati da uno script sul lato server venivano visualizzati nella finestra Esplora script. La finestra Esplora script era spesso nascosta, per cui la disponibilità di script sul lato client non era sempre ovvia.  
  
 In [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] i file script sul lato client generati da uno script sul lato server vengono visualizzati in Esplora soluzioni, visualizzata per impostazione predefinita. La finestra Esplora script è stata eliminata.  
  
 I file script sul lato client sono visibili solo in modalità di debug o in modalità interruzione. Vengono visualizzati nel **documenti Script** nodo.  
  
 I file script sul lato server sono sempre visibili. Vengono visualizzati nel  **\<percorso sito Web >** nodo. Il nome del nodo è simile a questo esempio:`c:\...\Website2\`  
  
### <a name="to-view-a-server-side-script-document"></a>Per visualizzare un documento script sul lato server  
  
1.  In **Esplora**, aprire il  **\<percorso sito Web >** nodo.  
  
2.  Fare doppio clic sul file script che si desidera visualizzare.  
  
     Il file script sul lato server verrà aperto in una finestra di origine.  
  
### <a name="to-view-a-client-side-script-document"></a>Per visualizzare un documento script sul lato client  
  
1.  In **Esplora**, aprire il **documenti Script** nodo.  
  
2.  Fare doppio clic sul file script che si desidera visualizzare.  
  
     Il file script sul lato client verrà aperto in una finestra di origine.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione di dati nel debugger](../debugger/viewing-data-in-the-debugger.md)