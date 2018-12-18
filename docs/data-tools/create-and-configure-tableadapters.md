---
title: Creare e configurare gli oggetti TableAdapter | Documenti Microsoft
ms.custom: 
ms.date: 09/01/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- table adapters, creating
- creating TableAdapters
- data [Visual Studio], creating data components
- data [Visual Studio], TableAdapters
- data [Visual Studio], creating table adapters
ms.assetid: 08630d69-0d6c-4e8f-b42d-2922f45f8415
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 3c9b501b78a82a94b81b2a29c86fd07a7a0d7f98
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="create-and-configure-tableadapters"></a>Creare e configurare gli oggetti TableAdapter
Gli oggetti TableAdapter forniscono la comunicazione tra l'applicazione e un database. Connessione al database, eseguire query o stored procedure e restituiscono i dati di tabella o di riempimento esistente <xref:System.Data.DataTable> con i dati restituiti. Gli oggetti TableAdapter anche inviare i dati aggiornati dall'applicazione al database.  
  
Gli oggetti TableAdapter vengono creati automaticamente quando si esegue una delle azioni seguenti:  
  
-   Eseguire il [configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png) e selezionare il **Database** o **servizio Web** tipo di origine dati.  
  
-   Trascinare gli oggetti di database **Esplora Server** nel **Progettazione Dataset**.  
  
È anche possibile creare un nuovo TableAdapter e configurarlo con un'origine dati mediante il trascinamento di un oggetto TableAdapter dalla casella degli strumenti a un'area vuota nel **Progettazione Dataset** area.  
  
Per un'introduzione agli oggetti TableAdapter, vedere [riempire i set di dati utilizzando gli oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="use-the-tableadapter-configuration-wizard"></a>Utilizzare la configurazione guidata TableAdapter  
Eseguire il **configurazione guidata TableAdapter** per creare o modificare oggetti TableAdapter e le tabelle dati associate. È possibile configurare un oggetto TableAdapter esistente facendo clic su di esso nel **Progettazione Dataset**.  
  
![Configurazione guidata adattatore tabella raddata](../data-tools/media/raddata-table-adapter-configuration-wizard.png "raddata configurazione guidata adattatore di tabella")  
  
Se si trascina un nuovo TableAdapter dalla casella degli strumenti quando la **Progettazione Dataset** sia nello stato attivo, l'avvio della procedura guidata devono connettersi richiede di specificare quali dati di origine dell'oggetto TableAdapter. Nella pagina successiva, viene richiesto il tipo di comandi da usare per comunicare con il database, le istruzioni SQL o stored procedure. (Non non visibile se si sta configurando un TableAdapter che è già associato a un'origine dati.)  
  
-   È possibile creare una nuova stored procedure nel database sottostante, se si dispone delle autorizzazioni corrette per il database. Se non si dispone di queste autorizzazioni, questo aspetto non è un'opzione.  
  
-   È anche possibile scegliere di eseguire stored procedure esistenti per il **selezionare**, **inserire**, **aggiornamento**, e **eliminare** i comandi del TableAdapter. La stored procedure che viene assegnata al **aggiornamento** comando, ad esempio, viene eseguito quando il `TableAdapter.Update()` metodo viene chiamato.  
  
Mappare i parametri dalla stored procedure selezionata alle colonne corrispondenti nella tabella dati. Ad esempio, se la stored procedure accetta un parametro denominato `@CompanyName` che passa il `CompanyName` set di colonne nella tabella, il **colonna di origine** del `@CompanyName` parametro `CompanyName`.  
  
> [!NOTE]
>  La stored procedure assegnata al comando SELECT viene eseguita chiamando il metodo dell'oggetto TableAdapter indicato nel passaggio successivo della procedura guidata. Il metodo predefinito è `Fill`, pertanto il codice che in genere utilizzato per l'esecuzione della stored procedure SELECT è `TableAdapter.Fill(tableName)`. Se si modifica il nome predefinito da `Fill`, sostituire `Fill` con il nome assegnare e sostituire "TableAdapter" con il nome effettivo dell'oggetto TableAdapter (ad esempio, `CustomersTableAdapter`).  
  
-   Selezionando il **Crea metodi per inviare aggiornamenti direttamente al database** opzione equivale all'impostazione di `GenerateDBDirectMethods` proprietà su true. L'opzione è disponibile quando l'istruzione SQL originale non fornisce informazioni sufficienti o la query non è aggiornabile. Questa situazione può verificarsi, ad esempio, in **JOIN** query e le query che restituiscono un singolo valore (scalare).  
  
Il **opzioni avanzate** nella procedura guidata consentono di:  
- Genera istruzioni INSERT, UPDATE e DELETE in base all'istruzione SELECT su cui è definito il **genera istruzioni SQL** pagina
- Usa concorrenza ottimistica
- Specificare se aggiornare la tabella di dati dopo l'inserimento e vengono eseguite le istruzioni UPDATE  
  
## <a name="configure-a-tableadapters-fill-method"></a>Configurare il metodo di riempimento di un oggetto TableAdapter  
In alcuni casi è consigliabile modificare lo schema della tabella dell'oggetto TableAdapter. A tale scopo, si modifica primaria dell'oggetto TableAdapter `Fill` metodo. TableAdapter vengono creati con un database primario `Fill` metodo che definisce lo schema della tabella di dati associato. Il database primario `Fill` metodo si basa sulla query o stored procedure immessa durante la configurazione iniziale dell'oggetto TableAdapter. È il primo metodo (in primo piano) sotto la tabella di dati in Progettazione DataSet.  
  
![TableAdapter con più query](../data-tools/media/tableadapter.gif "TableAdapter")  
  
Tutte le modifiche apportate all'oggetto TableAdapter principale del `Fill` metodo vengono riflesse nello schema della tabella dati associata. Ad esempio, la rimozione di una colonna dalla query principale `Fill` metodo rimuove anche la colonna dalla tabella dati associata. Inoltre, rimuovere la colonna dalla principale `Fill` metodo rimuove la colonna da qualsiasi altra query per tale oggetto TableAdapter.  
  
È possibile utilizzare la configurazione guidata Query TableAdapter per creare e modificare query aggiuntive per l'oggetto TableAdapter. Queste query aggiuntive devono essere conformi allo schema della tabella, a meno che non restituiscono un valore scalare.  Ogni query aggiuntive ha un nome specificato.  
 
Nell'esempio seguente viene illustrato come chiamare un'altra query denominata `FillByCity`:  
 
`CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, "Seattle")`  
  
#### <a name="to-start-the-tableadapter-query-configuration-wizard-with-a-new-query"></a>Per avviare la configurazione guidata Query TableAdapter con una nuova query  
  
1.  Aprire il dataset nel **Progettazione Dataset**.  
  
2.  Se si sta creando una nuova query, trascinare un **Query** dell'oggetto dal **set di dati** scheda del **della casella degli strumenti** su un <xref:System.Data.DataTable>, oppure selezionare **Aggiungi Query**dal menu di scelta rapida dell'oggetto TableAdapter. È anche possibile trascinare un **Query** oggetto in un'area vuota del **Progettazione Dataset**, che consente di creare un oggetto TableAdapter non associato a un <xref:System.Data.DataTable>. Queste query possono restituire singoli valori (scalari) o eseguire UPDATE, INSERT o solo eliminare comandi sul database.  
  
3.  Nel **Seleziona connessione dati** a schermo intero, selezionare o creare la connessione che verrà utilizzata la query.  
  
    > [!NOTE]
    >  Questa schermata viene visualizzata solo quando la finestra di progettazione non è possibile determinare la connessione appropriata da utilizzare, o quando non vi sono connessioni disponibili.  
  
4.  Nel **scegliere un tipo di comando** selezionare uno dei seguenti metodi di recupero dei dati dal database:  
  
    -   **Utilizzare le istruzioni SQL** consente di digitare un'istruzione SQL per selezionare i dati dal database.  
  
    -   **Creare una nuova stored procedure** Abilita per la creazione guidata crei una nuova stored procedure (database) in base all'istruzione SELECT specificata.  
  
    -   **Usa stored procedure esistenti** consente di eseguire una stored procedure esistente quando si esegue la query.  
  
#### <a name="to-start-the-tableadapter-query-configuration-wizard-on-an-existing-query"></a>Per avviare la configurazione guidata Query TableAdapter con una query esistente  
  
-   Se si modifica una query TableAdapter esistente, fare doppio clic su query e quindi scegliere **configura** dal menu di scelta rapida.  
  
    > [!NOTE]
    >  Facendo clic sulla query principale di un oggetto TableAdapter consente di riconfigurare il TableAdapter e <xref:System.Data.DataTable> dello schema. Facendo clic su una query aggiuntiva in un oggetto TableAdapter, tuttavia, configura solo la query selezionata. Il **configurazione guidata TableAdapter** riconfigura la definizione di TableAdapter, durante la configurazione guidata Query TableAdapter riconfigura solo la query selezionata.  
  
#### <a name="to-add-a-global--query-to-a-tableadapter"></a>Per aggiungere una query globale a un oggetto TableAdapter  
  
-   *Query globali* query SQL che restituiscono un singolo valore (scalare) o nessun valore. Funzioni globali in genere, eseguono le operazioni di database, ad esempio inserimenti, aggiornamenti, Elimina. Sono inoltre di aggregare informazioni, ad esempio un numero di clienti in una tabella o il costo totale di tutti gli elementi in un ordine particolare.  
  
     Per aggiungere query globali trascinando un **Query** dell'oggetto dal **set di dati** scheda della finestra il **della casella degli strumenti** in un'area vuota del **Progettazione Dataset**.  
  
-   Specificare una query che esegue l'attività desiderata, ad esempio, `SELECT COUNT(*) AS CustomerCount FROM Customers`.  
  
    > [!NOTE]
    >  Trascinare un **Query** oggetto direttamente nel **Progettazione Dataset** crea un metodo che restituisce solo un valore scalare (singolo). Mentre la query o stored procedure selezionata potrebbe restituire più di un singolo valore, il metodo che viene creato dalla procedura guidata restituisce solo un singolo valore. Ad esempio, la query potrebbe restituire la prima colonna della prima riga dei dati restituiti.

## <a name="see-also"></a>Vedere anche
[Compilare i set di dati usando oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)