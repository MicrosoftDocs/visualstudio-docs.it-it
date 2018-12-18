---
title: 'Area di test 1: Aggiungere a Apri dal controllo del codice sorgente | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], adding and opening solutions
- source control plug-ins, adding and opening solutions
ms.assetid: 5b3b5b08-5e9b-41be-ac72-c63957faed22
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1891e0242463f3673d22d22e0f9a2d000b01ae60
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="test-area-1-add-toopen-from-source-control"></a>Area di test 1: Aggiungere a / Apri dal controllo del codice sorgente
Questo controllo del codice sorgente plug-in di test viene illustrata l'area immissione soluzioni o progetti nel controllo del codice sorgente e vengono recuperati dal controllo del codice sorgente.  
  
## <a name="command-menu-access"></a>Accedere al Menu comando  
 Nell'esempio [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vengono utilizzati percorsi menu dell'ambiente di sviluppo integrato nei test case:  
  
-   Per [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]aprire dal controllo del codice sorgente: **File**, **aprire**, **progetto**/**soluzione**; cercare nel [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] percorso.  
  
-   Per altri origine plug-in del controllo, aprire dal controllo del codice sorgente: **File**, **controllo del codice sorgente**, **aprire dal controllo del codice sorgente**.  
  
-   Aggiungere al controllo del codice sorgente: **File**, **controllo del codice sorgente**, **Aggiungi soluzione al controllo codice sorgente**, **controllo del codice sorgente**, **Aggiungi Progetti al controllo del codice sorgente selezionati**.  
  
-   Menu di scelta rapida (progetto/soluzione), **Aggiungi soluzione al controllo del codice sorgente**.  
  
-   Aggiungi dal controllo del codice sorgente: **File**, **controllo del codice sorgente**, **Aggiungi progetto dal controllo del codice sorgente**.  
  
-   Per [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], aggiungere dall'origine controllo è disponibile anche in **File**, **Aggiungi**, **progetto esistente**; cercare nel [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] percorso.  
  
    > [!NOTE]
    >  In questo test, è possibile utilizzare un percorso di un file locale o un sito Web IIS locale (server web).  
  
## <a name="expected-behavior"></a>Comportamento previsto  
  
-   Per ogni tipo di progetto supportati, un utente deve essere in grado di "Aggiungere" e "Aperto" dal controllo del codice sorgente.  
  
-   Quando viene aggiunto un progetto al controllo del codice sorgente, un corrispondente \< *ProjectName*> viene creato e vspscc (file di progetto hint). Contiene informazioni di connessione e l'elenco di file esclusione. Non eliminare questo file perché contiene informazioni specifiche per il progetto.  
  
-   Quando una soluzione viene aggiunta al controllo del codice sorgente, un corrispondente \< *SolutionName*> viene creato il file. vssscc (triple S). Il file di testo contiene informazioni di connessione e un elenco di file di esclusione, simile al file di hint di progetto. Questo file è temporaneo ed esiste solo nel database del controllo del codice sorgente.  
  
-   Quando viene aperta una soluzione dal controllo del codice sorgente, un \< *SolutionName*> .vsscc (S double) i file che esiste solo nel database del controllo del codice sorgente viene creato in locale in un file temporaneo. Questo file contiene il percorso dalla cartella di connessione della soluzione per il file della soluzione. Questo file è temporaneo e la copia locale viene eliminata quando l'operazione "Apri dal controllo del codice sorgente" è stata completata.  
  
-   Dopo l'aggiunta di un progetto per il controllo del codice sorgente, è possibile eseguire le azioni di controllo di origine su di esso (estrazione, Get e così via).  
  
## <a name="test-cases"></a>Test case  
 Di seguito sono specifici test case per l'aggiunta a / Open dall'area di test di controllo del codice sorgente.  
  
### <a name="case-1a-add-solution-to-source-control"></a>Caso 1a: Aggiungi soluzione al controllo del codice sorgente  
 Questo test case è incentrata sull'aggiunta di soluzioni al controllo del codice sorgente.  
  
|Operazione|Passi di test|Per verificare i risultati previsti|  
|------------|----------------|--------------------------------|  
|Aggiungere una soluzione contenente un progetto di client di controllo del codice sorgente|1.  Creare un progetto client.<br />2.  Aggiungere la soluzione al controllo del codice sorgente (**File**, **controllo del codice sorgente**, **Aggiungi soluzione al controllo del codice sorgente**).|Soluzione/progetto è stato aggiunto al controllo del codice sorgente.|  
|Aggiungere una soluzione contenente un File System o un progetto Web IIS locale al controllo del codice sorgente|1.  Creare un File System o un progetto Web IIS locale (clic sul pulsante Sfoglia per puntare al percorso del progetto; il percorso determina il tipo di progetto Web viene creato).<br />2.  Aggiungere la soluzione al controllo del codice sorgente (**File**, **controllo del codice sorgente**, **Aggiungi soluzione al controllo del codice sorgente**).|Soluzione/progetto è stato aggiunto al controllo del codice sorgente.|  
|Aggiungere una soluzione contenente un progetto Web del sito remoto al controllo del codice sorgente|1.  Creare un progetto Web del sito remoto.<br />2.  Aggiungere la soluzione al controllo del codice sorgente (**File**, **controllo del codice sorgente**, **Aggiungi soluzione al controllo del codice sorgente**).<br />3.  Fare clic su **OK** nella finestra di dialogo Avviso di accesso di FrontPage.|Soluzione è stata aggiunta al controllo del codice sorgente.<br /><br /> Progetto di sito remoto non è incluso nel controllo del codice sorgente. (Progetti di sito remoto devono essere controllati da un server IIS).|  
|Aggiungere una singolo progetto soluzione al controllo di origine mediante **Aggiungi progetti selezionati a controllo del codice sorgente**.|1.  Creare una singolo progetto soluzione.<br />2.  Aggiungere solo soluzione al controllo del codice sorgente come selezione (**File**, **controllo del codice sorgente**, **Aggiungi progetti selezionati a controllo del codice sorgente**). Se questo passaggio ha esito positivo, andare al passaggio successivo.<br />3.  Aggiungi progetto al controllo del codice sorgente come selezione (**File**, **controllo del codice sorgente**, **Aggiungi progetti selezionati a controllo del codice sorgente**).<br />4.  Fare clic su **Sì** per aggiungere il progetto nello stesso percorso.<br />5.  Fare clic su **Estrai** in **Estrai per la modifica** la finestra di dialogo.|`Result from Step 2:`<br /><br /> Il progetto e tutti i file all'interno del progetto hanno un indicatore di controllo origine out e consente di visualizzare una descrizione comando "non in"controllo del codice sorgente.<br /><br /> `Result from Step 5:`<br /><br /> File di progetto e di soluzione sono nella stessa cartella nel controllo del codice sorgente.|  
|Annullare l'aggiunta di una soluzione a controllo del codice sorgente|1.  Creare una singolo progetto soluzione.<br />2.  Tentativo di aggiungere progetti e soluzioni al controllo del codice sorgente. Se questo passaggio ha esito positivo, andare al passaggio successivo.<br />3.  Annullare una volta nel controllo del codice sorgente.|`Result from Step 2:`<br /><br /> Il Set di progetto percorso origine controllo finestra di dialogo viene visualizzata una sola volta.<br /><br /> `Result from Step 3:`<br /><br /> Progetto aggiungere annullato, progetto/soluzione non è incluso nel controllo del codice sorgente e tutti aggiungere al menu di controllo origine ancora disponibili.|  
  
### <a name="case-1b-open-solution-from-source-control"></a>1b case. Apri soluzione dal controllo del codice sorgente  
 Questo test case è incentrata sull'apertura di soluzioni dal controllo del codice sorgente.  
  
|Operazione|Passi di test|Per verificare i risultati previsti|  
|------------|----------------|--------------------------------|  
|Aprire una soluzione contenente un progetto client dal controllo del codice sorgente|1.  Creare un progetto client.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Chiudere la soluzione.<br />4.  Aprire la soluzione dal controllo del codice sorgente in un nuovo percorso.|Soluzione/progetto aperto dal controllo del codice sorgente.|  
|Aprire una soluzione contenente un locale o un progetto Web di IIS dal controllo del codice sorgente|1.  Creare un progetto Web di IIS locale.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Chiudere la soluzione.<br />4.  Aprire la soluzione dal controllo del codice sorgente in un nuovo percorso.|Soluzione/progetto aperto dal controllo del codice sorgente.|  
|Aprire una soluzione contenente un progetto Web del sito remoto dal controllo del codice sorgente|1.  Creare un progetto Web del sito remoto.<br />2.  Aggiungere la soluzione al controllo del codice sorgente. Se questo passaggio ha esito positivo, andare al passaggio successivo.<br />3.  Chiudere la soluzione.<br />4.  Aprire la soluzione dal controllo del codice sorgente in un nuovo percorso.|`Result from Step 2:`<br /><br /> Web del sito remoto non è incluso nel controllo del codice sorgente.<br /><br /> `Result from Step 4:`<br /><br /> Soluzione aperta dal controllo del codice sorgente.<br /><br /> Progetto di sito remoto viene caricato, ma non è incluso nel controllo del codice sorgente.|  
  
### <a name="case-1c-add-solution-from-source-control"></a>Caso c 1: aggiungere una soluzione dal controllo del codice sorgente  
 Questo test case è incentrata sull'aggiunta di soluzioni dal controllo del codice sorgente.  
  
|Operazione|Passi di test|Per verificare i risultati previsti|  
|------------|----------------|--------------------------------|  
|Aggiungere alla soluzione vuota, ovvero una singolo progetto soluzione|1.  Creare una singolo progetto soluzione.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Chiudere la soluzione.<br />4.  Creare una seconda soluzione vuota.<br />5.  Aggiungere la soluzione in precedenza è controllata dal controllo del codice sorgente (**File**, **controllo del codice sorgente**, **Aggiungi progetto dal controllo del codice sorgente**).|Il progetto aggiunto viene visualizzato **Esplora** e viene archiviato.|  
|Aggiungere alla soluzione con singolo progetto, ovvero unico progetto|1.  Creare una soluzione con un singolo progetto.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Chiudere la soluzione.<br />4.  Creare una seconda soluzione vuota.<br />5.  Aggiungere la soluzione in precedenza è controllata dal controllo del codice sorgente (**File**, **controllo del codice sorgente**, **Aggiungi progetto dal controllo del codice sorgente**).|Il progetto aggiunto viene visualizzato **Esplora** e viene archiviato.|  
|Aggiungere alla soluzione-soluzione aggiunto al controllo del codice sorgente dalla selezione|1.  Creare una soluzione con un progetto.<br />2.  Aggiungere solo soluzione al controllo del codice sorgente come selezione. Se questo passaggio ha esito positivo, andare al passaggio successivo.<br />3.  Chiudere la soluzione.<br />4.  Creare una nuova soluzione.<br />5.  Aggiungere la soluzione in precedenza è controllata dal controllo del codice sorgente (**File**, **controllo del codice sorgente**, **Aggiungi progetto dal controllo del codice sorgente**).|`Result from Step 2:`<br /><br /> Progetto non è incluso nel controllo del codice sorgente.<br /><br /> `Result from Step 5:`<br /><br /> Se la prima soluzione conteneva degli elementi, non aggiungere dal controllo del codice sorgente, pertanto non verranno visualizzati.<br /><br /> Progetto dalla soluzione primo viene visualizzato come non disponibile.|  
  
## <a name="see-also"></a>Vedere anche  
 [Guida per il test dei plug-in del controllo del codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)