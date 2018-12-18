---
title: Risoluzione dei problemi relativi agli strumenti per le prestazioni | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b61cdf7-75b7-4abd-aff2-7bd997717626
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 748f642e4bd150c8ec5819057b4ee3f7768893f0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="troubleshooting-performance-tools-issues"></a>Risoluzione dei problemi relativi agli strumenti per le prestazioni
Quando si usano gli strumenti di profilatura, potrebbe verificarsi uno dei seguenti problemi:  
  
-   [Non vengono raccolti dati dagli strumenti di profilatura](#NoDataCollected)  
  
-   [Nei report e nelle visualizzazioni delle prestazioni vengono visualizzati numeri invece dei nomi di funzione](#NoSymbols)  
  
##  <a name="NoDataCollected"></a> Non vengono raccolti dati dagli strumenti di profilatura  
 Dopo aver eseguito la profilatura di un'applicazione, non viene creato alcun file di dati di profilatura (con estensione vsp) e viene visualizzato il seguente avviso nella finestra di output o nella finestra di comando:  
  
 PRF0025: Dati non raccolti.  
  
 Le cause del problema possono essere diverse:  
  
-   Un processo di cui è stata eseguita la profilatura tramite il campionamento o il metodo di memoria .NET avvia un processo figlio che diventa il processo che esegue le operazioni dell'applicazione. Alcune applicazioni, ad esempio, leggono la riga di comando per determinare se sono state avviate come un'applicazione Windows o come un'applicazione della riga di comando. Se è stata richiesta un'applicazione Windows, il processo originale avvia un nuovo processo configurato come un'applicazione Windows e quindi termina il processo originale. Poiché gli strumenti di profilatura non raccolgono automaticamente i dati per i processi figlio, non viene raccolto alcun dato.  
  
     Per raccogliere i dati di profilatura in questa situazione, collegare il profiler al processo figlio invece di avviare l'applicazione con il profiler. Per altre informazioni, vedere [Procedura: Connettere e disconnettere gli strumenti per le prestazioni ai processi in esecuzione](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md) e [Attach (VSPerfCmd)](../profiling/attach.md)  
  
##  <a name="NoSymbols"></a> Nei report e nelle visualizzazioni delle prestazioni vengono visualizzati numeri invece dei nomi di funzione  
 Dopo aver eseguito la profilatura di un'applicazione, nei report e nelle visualizzazioni vengono visualizzati numeri anziché i nomi di funzione.  
  
 Questo problema è causato dal fatto che il motore di analisi degli strumenti di profilatura non riesce a trovare i file PDB che contengono le informazioni sui simboli usate per eseguire il mapping delle informazioni sul codice sorgente, come nomi di funzione e numeri di riga, al file compilato. Per impostazione predefinita, il compilatore crea il file PDB quando viene compilato il file dell'applicazione. Un riferimento alla directory locale del file PDB viene archiviato nell'applicazione compilata. Il motore di analisi esegue una ricerca nella directory specificata dal riferimento per il file PDB e quindi nella directory che contiene i file dell'applicazione. Se il file PDB non viene trovato, il motore di analisi usa gli offset di funzione anziché i nomi di funzione.  
  
 È possibile risolvere il problema in due modi:  
  
-   Individuare i file PDB e posizionarli nella stessa directory dei file dell'applicazione.  
  
-   Incorporare le informazioni sui simboli nel file di dati di profilatura (con estensione VSP). Per altre informazioni, vedere [Salvataggio delle informazioni sui simboli con i file di dati di prestazioni](../profiling/saving-symbol-information-with-performance-data-files.md).  
  
> [!NOTE]
>  Il motore di analisi richiede che il file PDB sia della stessa versione del file dell'applicazione compilata. Non è possibile usare un file PDB di una compilazione precedente o successiva del file dell'applicazione.