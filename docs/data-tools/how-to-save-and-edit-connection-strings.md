---
title: 'Procedura: salvare e modificare stringhe di connessione | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f8ef3a2c-029c-423b-9d9e-a4f1add4f640
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: bb3ddcf8a4d1ac14b356bfabac2378ff345ef65b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-save-and-edit-connection-strings"></a>Procedura: salvare e modificare stringhe di connessione
Le stringhe di connessione nelle applicazioni di Visual Studio possono essere salvate nel file di configurazione dell'applicazione (detto anche le impostazioni dell'applicazione) o a livello di codice direttamente nell'applicazione. Il salvataggio delle stringhe di connessione nel file di configurazione dell'applicazione semplifica la gestione dell'applicazione. Se la stringa di connessione richiede modifiche, infatti, è possibile aggiornarla all'interno di tale file anziché modificarla nel codice sorgente e poi ricompilare l'applicazione.

L'archiviazione di informazioni riservate, ad esempio una password, nella stringa di connessione può avere implicazioni sulla sicurezza dell'applicazione. Le stringhe di connessione salvate nel file di configurazione dell'applicazione non vengono crittografate. Per tale motivo, chiunque può accedere al file e visualizzarne il contenuto. La sicurezza integrata di Windows consente di controllare l'accesso a un database in modo più sicuro.

Se non si sceglie di utilizzare la sicurezza integrata di Windows e il database in uso richiede l'immissione di un nome utente e di una password, è possibile ometterli nella stringa di connessione, ma sarà comunque necessario specificarli per eseguire la connessione al database. È ad esempio possibile creare una finestra di dialogo in cui vengono richieste tali informazioni e compilare la stringa di connessione dinamicamente in fase di esecuzione. Anche in questo caso possono presentarsi problemi di sicurezza se le informazioni vengono intercettate nel percorso verso il database. Per altre informazioni, vedere [Protezione delle informazioni di connessione](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="to-save-a-connection-string-from-within-the-data-source-configuration-wizard"></a>Per salvare una stringa di connessione dall'interno la configurazione guidata origine dati
Nel **configurazione guidata origine dati**, selezionare l'opzione per salvare la connessione alla salvare la stringa di connessione alla pagina File di configurazione dell'applicazione.

## <a name="to-save-a-connection-string-directly-into-application-settings"></a>Per salvare una stringa di connessione direttamente nelle impostazioni dell'applicazione
- In Esplora soluzioni fare doppio clic sull'icona di progetto (Visual Basic) o sull'icona delle proprietà (c#) per aprire la finestra di progettazione del progetto.
- Selezionare la scheda Impostazioni.
- Immettere un nome per la stringa di connessione. Fare riferimento a questo nome per l'accesso alla stringa di connessione nel codice.
- Impostare il tipo (stringa di connessione).
- Lasciare l'ambito impostato su applicazione.
- Digitare la stringa di connessione nel campo del valore o fare clic sul pulsante con puntini di sospensione (...) nel campo valore per aprire la finestra di dialogo proprietà di connessione per compilare la stringa di connessione.  

## <a name="editing-connection-strings-stored-in-application-settings"></a>La modifica di stringhe di connessione archiviate nelle impostazioni dell'applicazione
È possibile modificare le informazioni di connessione salvate nelle impostazioni dell'applicazione utilizzando la finestra di progettazione del progetto.  

### <a name="to-edit-a-connection-string-stored-in-application-settings"></a>Per modificare una stringa di connessione archiviata nelle impostazioni dell'applicazione
- In Esplora soluzioni fare doppio clic sull'icona di progetto (Visual Basic) o sull'icona delle proprietà (c#) per aprire la finestra di progettazione del progetto.
- Selezionare la scheda Impostazioni.
- Individuare la connessione a cui che si desidera modificare e selezionare il testo nel campo del valore.
- Modificare la stringa di connessione nel campo del valore o fare clic sul pulsante con puntini di sospensione (...) nel campo valore per modificare la connessione con la finestra di dialogo proprietà di connessione.  

## <a name="editing-connection-strings-for-datasets"></a>La modifica di stringhe di connessione per i set di dati
È possibile modificare le informazioni di connessione per ogni TableAdapter in un set di dati.  

### <a name="to-edit-a-connection-string-for-a-tableadapter-in-a-dataset"></a>Per modificare una stringa di connessione per un oggetto TableAdapter in un set di dati
- In Esplora soluzioni fare doppio clic sul set di dati (file con estensione XSD) contenente la connessione che si desidera modificare.
- Selezionare il TableAdapter o una query che contiene la connessione che si desidera modificare.
- Nella finestra Proprietà espandere il nodo della connessione.
- Per modificare rapidamente la stringa di connessione, è possibile modificare la proprietà ConnectionString, o fare clic sulla freccia giù sulla proprietà di connessione e scegliere Nuova connessione.

## <a name="security"></a>Sicurezza
L'archiviazione delle informazioni riservate, ad esempio la password, nella stringa di connessione può avere implicazioni sulla sicurezza dell'applicazione. La sicurezza integrata di Windows consente di controllare l'accesso a un database in modo più sicuro.
Per altre informazioni, vedere [Protezione delle informazioni di connessione](/dotnet/framework/data/adonet/protecting-connection-information).
  
## <a name="see-also"></a>Vedere anche
[Aggiunta di connessioni](../data-tools/add-new-connections.md)