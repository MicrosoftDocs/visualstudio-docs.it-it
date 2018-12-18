---
title: 'Area test 7: Condividere | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], sharing items
- source control plug-ins, sharing items
ms.assetid: 6ec4780a-bda4-4327-bb3e-c6c9e7eabf35
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fa74d6ff2291288a1ca0e7f17a2edb1e126f222b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="test-area-7-share"></a>Test Area 7: condivisione
Test responsabilità Condivisione elementi tra i percorsi tramite la **condivisione** comando.  
  
 Un'operazione hhare è la duplicazione apparente di file e cartella elementi tra due o più posizioni all'interno di una gerarchia di file di controllo di origine. La duplicazione non viene effettivamente eseguito sul server, ma l'utente, vedere il file stesso in due o più percorsi specificati. Ogni volta che vengono apportate modifiche a tutti gli elementi condivisi, le modifiche visualizzate in tutti gli altri percorsi condivisi.  
  
 Condivisione di cartelle funziona se si seleziona una cartella con almeno un file in essa contenuti nel controllo del codice sorgente. Il comando di condivisione è disabilitato nelle condizioni seguenti:  
  
-   Se la cartella selezionata è una cartella vuota.  
  
-   Se è presente una cartella reale, ma non contiene alcun file di controllo di origine.  
  
-   Se è presente una cartella virtuale, che i file nel controllo del codice sorgente siano in essa contenuti o meno.  
  
-   Se è presente un progetto Web del sito remoto.  
  
## <a name="command-menu-access"></a>Accedere al Menu comando  
 Nell'esempio [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vengono utilizzati percorsi menu dell'ambiente di sviluppo integrato nei test case.  
  
 Condivisione: **File**->**controllo del codice sorgente**->**condivisione**.  
  
## <a name="expected-behavior"></a>Comportamento previsto  
  
-   File condivisi viene visualizzato in una posizione condivisa.  
  
-   Visualizzazione origine controllo versione archivio cronologia mostra che i file vengono condivisi.  
  
-   Modifica di un file condiviso consente di modificare i percorsi del file.  
  
## <a name="test-cases"></a>Test case  
 Di seguito sono specifici test case per l'area di test di condivisione.  
  
|Operazione|Passi di test|Per verificare i risultati previsti|  
|------------|----------------|--------------------------------|  
|Condividere un file da un progetto caricato nel controllo del codice sorgente in un altro progetto caricato|1.  Creare un nuovo progetto.<br />2.  Aggiungere un secondo progetto alla soluzione.<br />3.  Creare un file nel progetto secondo con un nome che non è nel primo progetto.<br />4.  Aggiungere la soluzione al controllo del codice sorgente.<br />5.  Selezionare il primo progetto.<br />6.  Aprire **condivisione** la finestra di dialogo (**File** -> **controllo del codice sorgente** -> **condivisione**).<br />7.  Condividere il file dal progetto secondo al primo progetto.<br />8.  Accettare **Estrai** se richiesto.|Comportamento previsto comune.|  
|Condividere un file da un progetto a un altro|1.  Creare un nuovo progetto.<br />2.  Aggiungerlo al controllo del codice sorgente.<br />3.  Chiudere la soluzione.<br />4.  Creare un secondo progetto (nuova soluzione).<br />5.  Aggiungere la soluzione al controllo del codice sorgente.<br />6.  Selezionare il progetto.<br />7.  Aprire il **condivisione** la finestra di dialogo (**File** -> **controllo del codice sorgente** -> **condivisione**).<br />8.  Condividere un file dal progetto già aggiunto al progetto aperto.<br />9. Accettare **Estrai** se richiesto.|Comportamento previsto comune.|  
|Condividere un file non fa parte del progetto dal controllo del codice sorgente nel progetto attualmente caricato|1.  Creare un nuovo progetto.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Aggiungere un file al controllo del codice sorgente che non fa parte del progetto o soluzione.<br />4.  Selezionare il progetto e aprire il **condivisione** la finestra di dialogo (**File** -> **controllo del codice sorgente** -> **condivisione**).<br />5.  Selezionare un file all'interno di **condividere** la finestra di dialogo che non esiste all'interno del progetto corrente o della soluzione e condividerlo.<br />6.  Accettare **Estrai** se richiesto.|Archivio del controllo codice sorgente ha eseguito un'operazione Get, pertanto il file è ora nel percorso locale del progetto.|  
|Condivisione di file all'interno dello stesso progetto in una cartella diversa|1.  Selezionare **Estrai automaticamente** in **strumenti** -> **opzioni** -> **controllo del codice sorgente**.<br />2.  Creare un nuovo progetto e aggiungerlo al controllo del codice sorgente.<br />3.  Aggiungere una cartella per il progetto.<br />4.  Aggiungere un file nella cartella e archiviare la cartella.<br />5.  Selezionare la cartella.<br />6.  Aprire **condivisione** la finestra di dialogo (**File** -> **controllo del codice sorgente** -> **condivisione**).<br />7.  Condividere i file nella cartella selezionata.|Comportamento previsto comune.<br /><br /> Prima di poter essere utilizzato per condivisione, cartella deve essere selezionata con un file in essa contenuti.|  
|Condividere una cartella nel progetto caricato, ricorsivi|1.  Creare un nuovo progetto.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Selezionare il progetto.<br />4.  Aprire il **condivisione** la finestra di dialogo (**File** -> **controllo del codice sorgente** -> **condivisione**).<br />5.  Selezionare una cartella.<br />6.  Condividere la cartella in modo ricorsivo nel progetto.|Comportamento previsto comune.|  
|Condivisione di file diversi da un progetto a un altro|1.  Creare un nuovo progetto con diversi file in essa contenuti.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Chiudere la soluzione.<br />4.  Creare un nuovo progetto in una nuova soluzione.<br />5.  Aggiungere la soluzione al controllo del codice sorgente.<br />6.  Selezionare il progetto.<br />7.  Aprire il **condivisione** la finestra di dialogo (**File** -> **controllo del codice sorgente** -> **condivisione**).<br />8.  Condivisione di file diversi dal progetto creato in precedenza per il progetto aperto.|Comportamento previsto comune.|  
  
## <a name="see-also"></a>Vedere anche  
 [Guida per il test dei plug-in del controllo del codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)