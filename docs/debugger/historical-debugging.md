---
title: Il debug cronologico | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7cc5ddf2-2f7c-4f83-b7ca-58e92e9bfdd2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a75dfc04bd5ce3b1e61cc2c8e8fe293c13560cf9
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="historical-debugging"></a>Il debug cronologico
Il debug cronologico è una modalità di debug che dipende dalle informazioni raccolte da IntelliTrace. Consente di tornare indietro e avanti l'esecuzione dell'applicazione e controllare lo stato.  
  
 È possibile utilizzare IntelliTrace in Visual Studio Enterprise edition (ma non le edizioni Professional o Community).  
  
## <a name="why-use-historical-debugging"></a>Perché utilizzare il debug cronologico?  
 Impostazione di punti di interruzione per individuare i bug può essere una questione piuttosto hit-or-miss. È possibile impostare un punto di interruzione simile al punto nel codice in cui si ritiene che il bug sia quindi eseguire l'applicazione nel debugger e spero che il punto di interruzione ottiene accesso e il luogo in cui l'esecuzione si interrompe è in grado di rivelare l'origine del bug. In caso contrario, sarà necessario provare a impostare un punto di interruzione in un'altra posizione nel codice ed eseguire nuovamente il debugger, eseguire i passi del test più volte fino a individuare il problema.  
  
 ![l'impostazione di un punto di interruzione](../debugger/media/breakpointprocesa.png "BreakpointProcesa")  
  
 È possibile utilizzare IntelliTrace e il debug cronologico per spostarsi all'interno dell'applicazione e controllare lo stato (stack di chiamate e variabili locali) senza dover impostare punti di interruzione, riavviare il debug e ripetere i passi del test. Ciò consente di risparmiare molto tempo, soprattutto quando il bug si trova approfondita in uno scenario di test che richiede molto tempo per eseguire.  
  
## <a name="how-do-i-start-using-historical-debugging"></a>Come iniziare a utilizzare il debug cronologico?  
 IntelliTrace è attivato per impostazione predefinita. Sarà sufficiente è decidere quali eventi e chiamate di funzione sono di interesse, e se si desidera visualizzare gli snapshot dello stato dell'applicazione completo. Per ulteriori informazioni sulla definizione di ciò che si desidera cercare, vedere [funzionalità IntelliTrace](../debugger/intellitrace-features.md).  

 - Per visualizzare gli snapshot con il debug cronologico, vedere [visualizzare snapshot tramite IntelliTrace passaggio-back](../debugger/how-to-use-intellitrace-step-back.md)
 - Per informazioni su come controllare le variabili e spostarsi nel codice, vedere [controllare l'app con il debug cronologico](../debugger/historical-debugging-inspect-app.md)
 - Per ulteriori informazioni sul debug con eventi di IntelliTrace, vedere [procedura dettagliata: utilizzo di IntelliTrace](../debugger/walkthrough-using-intellitrace.md).