---
title: 'Area test 6: Eliminare | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], deleting items
- source control plug-ins, deleting items
ms.assetid: 6f2e872c-5ba2-4303-9f50-a90cef9a6225
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 97fc6ab9746e7ef2188c78dc77ec357f7d415a42
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="test-area-6-delete"></a>Test Area 6: eliminare
Questa area di plug-in test di controllo del codice sorgente vengono illustrate le azioni di eliminazione.  
  
 Controllo del codice sorgente risponde per eliminare le azioni in **Esplora**.  
  
 Ecco un elenco di elementi che possono essere eliminate:  
  
-   File  
  
-   Cartelle  
  
-   Progetto  
  
 A seconda del tipo di progetto, potrebbe essere possibile **rimuovere** il progetto (lascia i file su disco) o **eliminare** il progetto (rimuove i file su disco). Entrambe le azioni rimuove il progetto o un elemento da **Esplora**.  
  
## <a name="expected-behavior"></a>Comportamento previsto  
 Il comportamento previsto per i test case nell'area di prova delete è:  
  
-   Elemento eliminato non è più visibile all'interno di **Esplora**.  
  
-   L'elemento padre del progetto eliminato o dell'elemento è stato estratto in base alle esigenze (possibilmente con un prompt dei comandi.)  
  
-   Dopo avere eliminato un timeout o elemento aggiunto, non appare nella **archiviazioni in sospeso** finestra.  
  
-   L'elemento è ancora presente all'interno dell'archivio del controllo origine, anche dopo l'eliminazione e deve essere eliminato manualmente.  
  
|Operazione|Passi di test|Per verificare i risultati previsti|  
|------------|----------------|--------------------------------|  
|Eliminare un progetto client|1.  Creare un progetto client.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Rimuovere l'intero progetto dalla soluzione|Comportamento previsto comune.|  
|Eliminare un file vuoto|1.  Creare un progetto client.<br />2.  Aggiungere un file di zero byte per il progetto.<br />3.  Aggiungere la soluzione al controllo del codice sorgente.<br />4.  Selezionare il file, eliminarlo.|Comportamento previsto comune.|  
|Eliminare una cartella con un file|1.  Creare la soluzione singolo progetto.<br />2.  Aggiungere una cartella.<br />3.  Aggiungere un file nella cartella.<br />4.  Aggiungere la soluzione al controllo del codice sorgente.<br />5.  Estrarre il progetto per evitare richieste.<br />6.  Eliminare la cartella.|Comportamento previsto comune.|  
|Eliminare un progetto Web di File System|1.  Creare un progetto Web di File System (utilizzare il pulsante Sfoglia per specificare un percorso UNC).<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Rimuovere l'intero progetto dalla soluzione.<br />4.  Ripetere i passaggi da 1 a 3 per un progetto Web locale (esercita percorsi diversi nel codice ma ha la stessa interfaccia esterna e il comportamento).|Comportamento previsto comune.|  
|Eliminare un file da un progetto Web di File System|1.  Creare un progetto di File System. Web.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Eliminare un file dal progetto.<br />4.  Ripetere i passaggi da 1 a 3 per un progetto Web locale (esercita percorsi diversi nel codice ma ha la stessa interfaccia esterna e il comportamento).|Comportamento previsto comune.|  
  
## <a name="see-also"></a>Vedere anche  
 [Guida per il test dei plug-in del controllo del codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)