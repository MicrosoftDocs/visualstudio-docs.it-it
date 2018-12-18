---
title: Visualizzazione processi | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.externaltools.spyplus.processesview
helpviewer_keywords: Processes view
ms.assetid: e144e70e-eef2-45a7-a562-a177f177d9a1
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d2dc97cbe5c6bc178e4b14c89287a3f1c3794dca
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="processes-view"></a>Visualizzazione processi
La visualizzazione dei processi viene visualizzato un albero di tutti i processi attivi nel sistema. Vengono visualizzati il nome del modulo e l'ID processo. Se si desidera esaminare un particolare processo di sistema, che generalmente corrisponde a un programma in esecuzione, utilizzare la visualizzazione dei processi. I processi vengono identificati da nomi di modulo o vengono designati come "processi di sistema".  
  
 Microsoft Windows supporta più processi. Ogni processo può avere uno o più thread e ogni thread può avere uno o più finestre di primo livello. Ogni finestra di primo livello può disporre di una serie di windows. Un simbolo + indica che un livello è compresso. La visualizzazione compressa è costituita da una riga per ogni processo. Scegliere il simbolo + per espandere il livello.  
  
 Se si desidera esaminare un particolare processo di sistema, che generalmente corrisponde a un programma in esecuzione, utilizzare la visualizzazione dei processi. I processi vengono identificati da nomi di modulo o vengono designati come "processi di sistema". Per trovare un processo, comprimere la struttura ad albero e l'elenco di ricerca.  
  
## <a name="procedures"></a>Procedure  
  
#### <a name="to-open-the-processes-view"></a>Per aprire la visualizzazione dei processi  
  
1.  Dal **Spy** menu, scegliere **processi**.  
  
 ![Spy &#43; &#43; Visualizzazione processi](../debugger/media/spy--_processes.png "Spy + + _Processes")  
Visualizzazione processi di Spy++  
  
 La seguente figura mostra la visualizzazione dei processi con thread e processi nodi espansi.  
  
### <a name="in-this-section"></a>In questa sezione  
 [Ricerca di un processo nella visualizzazione processi](../debugger/how-to-search-for-a-process-in-processes-view.md)  
 Viene illustrato come trovare un processo specifico nella visualizzazione processi.  
  
 [Visualizzazione delle proprietà di processo](../debugger/how-to-display-process-properties.md)  
 Viene illustrato come visualizzare ulteriori informazioni su un messaggio.  
  
### <a name="related-sections"></a>Sezioni correlate  
 [Visualizzazioni di Spy++](../debugger/spy-increment-views.md)  
 Vengono illustrate le visualizzazioni ad albero Spy + + di windows, i messaggi, thread e processi.  
  
 [Uso di Spy++](../debugger/using-spy-increment.md)  
 Vengono presentati lo strumento Spy + + e come può essere usato.  
  
 [Finestra di dialogo Ricerca processi](../debugger/process-search-dialog-box.md)  
 Utilizzato per trovare il nodo per un determinato processo nella visualizzazione processi.  
  
 [Finestra di dialogo Proprietà processo](../debugger/process-properties-dialog-box.md)  
 Visualizza le proprietà di un processo selezionato nella visualizzazione processi.  
  
 [riferimenti per Spy++](../debugger/spy-increment-reference.md)  
 Include le sezioni che descrivono ogni Spy + + menu e finestra di dialogo.