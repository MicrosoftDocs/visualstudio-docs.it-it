---
title: 'Area test 3: Check Out-Annulla estrazione | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, checkout
- source control plug-ins, undo checkout
- source control [Visual Studio SDK], checking out
- source control [Visual Studio SDK], undo checkout
ms.assetid: ce00c5a5-d472-4f45-8776-d77a1fbe9d37
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8835f1f8c312b3aba72353625a1d97b514dc21b8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="test-area-3-check-outundo-checkout"></a>Area test 3: Estrarre / Annulla estrazione
Questa area di plug-in test di controllo del codice sorgente include gli elementi di modifica e di ripristino dall'archivio delle versioni tramite il **Estrai** e **Annulla estrazione** comandi.  
  
 **Check-Out**: i segni di un elemento nell'archivio delle versioni come estratti, modifica la copia locale di lettura/scrittura.  
  
 **Annullare l'estrazione**: contrassegna un elemento nell'archivio delle versioni, come archiviazione, viene ripristinata la copia locale allo stato di check-out (a seconda delle opzioni).  
  
## <a name="command-menu-access"></a>Accedere al Menu comando  
 Nell'esempio [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vengono utilizzati percorsi menu dell'ambiente di sviluppo integrato nei test case.  
  
##### <a name="check-out"></a>Vedere:  
  
-   **File**, **controllo del codice sorgente**, **estrarre**.  
  
-   **File**, **estrarre**.  
  
-   Menu di scelta rapida, **estrarre**.  
  
-   Annullamento dell'estrazione: **File**, **controllo del codice sorgente**, **Annulla estrazione**.  
  
## <a name="common-expected-behavior"></a>Comportamento previsto comune  
  
-   Dopo l'operazione di estrazione, il file di destinazione e/o le cartelle sono contrassegnate come estratto dall'archivio delle versioni.  
  
-   L'archivio versione gli attributi utente corretto l'estrazione.  
  
-   La data dell'estrazione e l'ora siano corrette (per le impostazioni dell'utente).  
  
## <a name="test-cases"></a>Test case  
 Di seguito sono specifici test case per l'area di test di estrazione/annullamento dell'estrazione.  
  
### <a name="case-3a-check-out"></a>Caso 3: Check-Out  
 Questa sezione vengono illustrati l'operazione del comando di estrazione.  
  
|Operazione|Passi di test|Per verificare i risultati previsti|  
|------------|----------------|--------------------------------|  
|Controllare Out esclusivo (COE) un progetto client|1.  Creare un progetto client.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Estrae l'intero progetto in modo esclusivo (**File**, **Estrai**).|Si verifica l'estrazione.|  
|Estrazione esclusiva (COE), un File System o un progetto Web IIS locale|1.  Impostare connessione Server Web a una condivisione nel File **strumenti**, **opzioni**, **progetti**, **impostazioni Web**.<br />2.  Creare un progetto Web.<br />3.  Aggiungere la soluzione al controllo del codice sorgente.<br />4.  Estrae l'intero progetto in modo esclusivo (**File**, **controllo del codice sorgente**, **Estrai**).|Si verifica l'estrazione.|  
|Estrarre gli elementi di soluzione in una soluzione (nuovo metodo per la gestione di altri file)|1.  Creare una soluzione vuota.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Estrarre la soluzione.<br />4.  Aggiungere più elementi di soluzione.<br />5.  Controllare tutti gli elementi appena aggiunto.<br />6.  Selezionare più elementi di soluzione.<br />7.  Estrarre gli elementi selezionati (Menu di scelta rapida, **Estrai**).|I file selezionati sono stati estratti.|  
|Estrai versione locale (se questa funzionalità supporta i plug-in sottoposta a test)|1.  L'utente 1: Creare un progetto client.<br />2.  L'utente 1: Aggiungere la soluzione al controllo del codice sorgente.<br />3.  L'utente 2: Aprire la soluzione dal controllo del codice sorgente in un altro percorso.<br />4.  L'utente 2: Estrazione di un file.<br />5.  L'utente 2: Modificare il file.<br />6.  L'utente 2: Archiviare il file.<br />7.  Utente 1: Controllare la versione locale del file (controllare il **Estrai versione locale** avanzate opzione **Estrai** la finestra di dialogo).|La versione locale del file è estratto.<br /><br /> Le modifiche apportate dall'utente 2 non vengono applicate ai file utente 1.|  
  
### <a name="case-3b-disconnected-check-out"></a>Caso 3b: disconnesso Check-out  
 Opera in modalità disconnessa consente agli utenti un livello di supporto del controllo di origine continua se non è collegato direttamente a un archivio delle versioni. Questa operazione viene eseguita localmente nella cache tutte le informazioni sui soluzione integrata e progetti.  
  
 Operazioni di estrazione esclusiva può verificarsi solo durante la connessione per l'archivio del controllo codice sorgente. Operazioni di estrazione condivisa può verificarsi in qualsiasi momento, se connesso o disconnesso. Pertanto, quando disconnesso dall'archivio delle versioni, solo il **controllare e condiviso** (CO) command è abilitato. Durante la disconnessione, **Annulla estrazione** è disabilitata perché la versione precedente non può essere recuperata per sostituire le modifiche apportate dall'utente.  
  
 Quando l'utente si riconnette alla versione archiviare, gli stati di completamento di tutte le soluzioni integrate e progetti sono stati sincronizzati. Si verificheranno gli aggiornamenti necessari per l'archivio di estrazioni in modo che l'utente ha eseguito. Una volta che si è verificato la sincronizzazione, l'utente è in grado di continuare a lavorare normalmente (connesso).  
  
#### <a name="expected-behavior"></a>Comportamento previsto  
  
-   Non è possibile utilizzare **Out esclusivamente** comando durante la disconnessione dall'archivio versione.  
  
-   Non è possibile utilizzare **Annulla estrazione** comando durante la disconnessione dall'archivio versione.  
  
-   **Condiviso Estrai** comando funziona.  
  
|Operazione|Passi di test|Per verificare i risultati previsti|  
|------------|----------------|--------------------------------|  
|Durante la disconnessione, estrarre un file, quindi connettersi per la sincronizzazione|1.  Disconnettere un progetto controllato utilizzando la finestra di dialogo Modifica controllo del codice sorgente (**File**, **controllo del codice sorgente**, **Modifica controllo del codice sorgente**l).<br />2.  Estrarre un file.<br />3.  Fare clic su Estrai (disconnesso) nella finestra di dialogo di avviso.<br />4.  Modificare il file.<br />5.  Connettersi utilizzando la finestra di dialogo Modifica controllo del codice sorgente.<br />6.  Ottenere la versione più recente del file modificato.|Comportamento previsto comune|  
  
### <a name="case-3c-query-editquery-save-qeqs"></a>Caso 3c: Query o modifica Query salvare (QEQS)  
 Gli elementi nel controllo del codice sorgente vengono tenuta traccia per le modifiche, le modifiche, e Salva per consentire agli utenti facilmente gestione i file. Quando viene modificato un elemento controllato archiviato "in", QEQS intercetta il tentativo di modifica e viene chiesto all'utente se desidera estrarre il file per modificarlo. A seconda **strumenti**, **opzioni** impostazioni, l'utente è obbligati a verificare estrarre il file per modificare o possono essere autorizzati a modificare una copia in memoria e check-out in un secondo momento. Se l'utente **strumenti**, **opzioni** non è impostata per visualizzare la finestra di dialogo Estrai e appena estrarlo, quindi effettua la modifica, il file estrae automaticamente, quando possibile.  
  
#### <a name="expected-behavior"></a>Comportamento previsto  
  
-   Dopo l'operazione di estrazione, il file di destinazione e/o le cartelle sono contrassegnate come estratto dall'archivio delle versioni.  
  
-   L'archivio versione attributi il check-out per l'utente corretto.  
  
-   La data e ora del check-out sono corretti (per le impostazioni dell'utente).  
  
-   La copia locale del file di destinazione o della cartella è scrivibile.  
  
|Operazione|Passi di test|Per verificare i risultati previsti|  
|------------|----------------|--------------------------------|  
|Modificare il file di testo che viene controllato|1.  Creare un nuovo progetto che contiene un file di testo.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Impostare **strumenti**, **opzioni**, **controllo del codice sorgente**, **consentire la modifica di sola lettura su disco dei file** a deselezionata.<br />4.  Impostare **strumenti**, **opzioni**, **controllo del codice sorgente**, **Richiedi estrazione** nel **archiviazione nel file sonomodificato** casella combinata.<br />5.  Impostare **strumenti**, **opzioni**, **controllo del codice sorgente**, **Richiedi estrazione** nel **quando archiviare i file vengono salvati** casella combinata.<br />6.  Aprire il file di testo nell'editor, tentare di digitare il nuovo testo nel file. Se questo passaggio ha esito positivo, andare al passaggio successivo.<br />7.  Fare clic su **Annulla** nel **Estrai per la modifica** la finestra di dialogo. Se questo passaggio ha esito positivo, andare al passaggio successivo.<br />8.  Impostare **strumenti**, **opzioni**, **controllo del codice sorgente**, **consentire la modifica di sola lettura su disco dei file** a selezionato.<br />9. Aprire il file di progetto nell'editor, tentare di digitare il nuovo testo nel file. Se questo passaggio ha esito positivo, andare al passaggio successivo.<br />10. Fare clic su **modifica** nel **Estrai per la modifica** la finestra di dialogo. Se questo passaggio ha esito positivo, andare al passaggio successivo.<br />11. Modificare il file di testo e si tenterà di salvarlo.|`Result of step 6:`<br /><br /> Controllare per viene visualizzata la finestra di dialogo di modifica.<br /><br /> `Result of step 7:`<br /><br /> Il file è stato modificato.<br /><br /> `Result of step 9:`<br /><br /> Controllare per viene visualizzata la finestra di dialogo di modifica.<br /><br /> `Result of step 10:`<br /><br /> È possibile modificare il file di progetto in memoria.<br /><br /> `Result of step 11:`<br /><br /> Salva il Check-out nella finestra di dialogo di salvataggio viene visualizzato.|  
|Modificare un file di soluzione che viene archiviato|Ripetere i passaggi, come descritto nella precedente di test, ma anziché modificare un file di testo, modificare soluzione modificando le proprietà di soluzione.|Stesso test precedente|  
|Modificare un file di progetto che viene controllato|Ripetere i passaggi, come descritto nella precedente di test, ma anziché modificare un file di testo, modificare progetto modificando le proprietà del progetto.|Uguale a test precedente.|  
  
### <a name="case-3d-silent-check-out"></a>Caso 3d: Estrazione automatica  
 Questo controllo include sottoarea scenari in cui il **Estrai** la finestra di dialogo non viene visualizzato per ogni utente **strumenti**, **opzioni**, **le impostazioni di controllo del codice sorgente** .  
  
#### <a name="expected-behavior"></a>Comportamento previsto  
  
-   Dopo l'operazione di estrazione, il file di destinazione e/o le cartelle sono contrassegnate come estratto dall'archivio delle versioni.  
  
-   L'archivio versione attributi il check-out per l'utente corretto.  
  
-   La data e ora del check-out è corretto (per le impostazioni dell'utente).  
  
-   La copia locale del file di destinazione o della cartella è scrivibile.  
  
|Operazione|Passi di test|Per verificare i risultati previsti|  
|------------|----------------|--------------------------------|  
|Estrazione invisibile all'utente per un file|1.  Impostare **strumenti**, **opzioni**, **controllo del codice sorgente** a **estragga i file automaticamente dal menu Modifica**.<br />2.  Creare un nuovo progetto con un file.<br />3.  Aggiungere la soluzione al controllo del codice sorgente.<br />4.  Estrarre il file.|File viene estratto automaticamente (senza interfaccia utente).|  
|Estrazione invisibile all'utente per un progetto|1.  Impostare **strumenti**, **opzioni**, **controllo del codice sorgente** a **estragga i file automaticamente dal menu Modifica**.<br />2.  Creare un nuovo progetto.<br />3.  Aggiungere la soluzione al controllo del codice sorgente.<br />4.  Estrarre il progetto.|File viene estratto automaticamente (senza interfaccia utente).|  
  
### <a name="case-3e-undo-check-out"></a>Caso 3e: Annulla estrazione  
 **Annulla estrazione** viene utilizzato per annullare un file estratto lo stato e di evitare la verifica delle modifiche apportate al file.  
  
#### <a name="expected-behavior"></a>Comportamento previsto  
  
-   Il valore predefinito si basa l'utente **Estrai versione locale** impostazione. Se l'utente ha scelto di Estrai versione locale, il valore predefinito per l'annullamento dell'estrazione è possibile annullare sempre la versione estratta.  
  
-   All'accettazione dell'annullamento, le icone in **Esplora** vengono aggiornate per i file e l'elemento viene rimosso dal **archiviazioni in sospeso** finestra.  
  
|Operazione|Passi di test|Per verificare i risultati previsti|  
|------------|----------------|--------------------------------|  
|Annullare l'estrazione di un singolo file che è stato estratto in modo esclusivo|1.  Creare un progetto client.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Estrae un file in modo esclusivo.<br />4.  Modificare il file.<br />5.  Annullare l'estrazione (**File**, **controllo del codice sorgente**, **Annulla estrazione**).|Comportamento previsto comune.|  
|Annullare l'estrazione di un singolo file che è stato estratto condiviso|1.  Creare un progetto client.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Estrarre un file condiviso.<br />4.  Modificare il file.<br />5.  Annullare l'estrazione (**File**, **controllo del codice sorgente**, **Annulla estrazione**).|Comportamento previsto comune.|  
|Annullare l'estrazione di un progetto dopo l'aggiunta di file al progetto|1.  Creare un nuovo progetto e aggiungerlo al controllo del codice sorgente.<br />2.  Estrarre il progetto.<br />3.  Aggiungere un file al progetto.<br />4.  Annullare l'estrazione del progetto.|Aggiunta di file viene rimosso dal progetto in Esplora soluzioni.<br /><br /> Progetto non è stato estratto.|  
|Annullare l'estrazione di un progetto dopo l'eliminazione di file dal progetto|1.  Creare un nuovo progetto e aggiungerlo al controllo del codice sorgente.<br />2.  Estrarre il progetto.<br />3.  Eliminare un file dal progetto.<br />4.  Annullare l'estrazione del progetto.|File eliminato viene visualizzato sotto il progetto in Esplora soluzioni.<br /><br /> Progetto non è stato estratto.|  
  
## <a name="see-also"></a>Vedere anche  
 [Guida per il test dei plug-in del controllo del codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)