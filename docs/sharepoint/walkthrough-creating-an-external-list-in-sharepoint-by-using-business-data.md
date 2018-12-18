---
title: 'Procedura dettagliata: Creazione di un elenco esterno in SharePoint utilizzando i dati di Business | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], business data in a Web Part
- BDC [SharePoint development in Visual Studio], external list
- Business Data Connectivity service [SharePoint development in Visual Studio], business data in a SharePoint list
- BDC [SharePoint development in Visual Studio], business data in a SharePoint list
- BDC [SharePoint development in Visual Studio], business data in a Web Part
- BDC [SharePoint development in Visual Studio], entity backed list
- Business Data Connectivity service [SharePoint development in Visual Studio], entity backed list
- Business Data Connectivity service [SharePoint development in Visual Studio], external list
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 09606f3ca61abd747451f92d4ecf8ee43010e669
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data"></a>Procedura dettagliata: creazione di un elenco esterno in SharePoint tramite il servizio di integrazione applicativa dei dati

Il servizio di integrazione applicativa dei dati (BDC) consente di visualizzare i dati aziendali da applicazioni server back-end, servizi Web e database SharePoint.

Questa procedura dettagliata viene illustrato come creare un modello per il servizio di integrazione applicativa dei dati che restituisce informazioni sui contatti in un database di esempio. Si creerà quindi un elenco esterno in SharePoint utilizzando il modello corrente.

In questa procedura dettagliata vengono illustrate le attività seguenti:

- Creazione di un progetto.
- Aggiunta di un'entità al modello.
- Aggiunta di un metodo finder.
- Aggiunta di un metodo finder specifico.
- Test del progetto.

## <a name="prerequisites"></a>Prerequisiti

Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:

- Le edizioni supportate di Windows e SharePoint. Per ulteriori informazioni, vedere [requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).

- Accesso al database di esempio AdventureWorks. Per ulteriori informazioni su come installare il database AdventureWorks, vedere [database di esempio di SQL Server](http://go.microsoft.com/fwlink/?LinkID=117483).

## <a name="creating-a-project-that-contains-a-bdc-model"></a>Creazione di un progetto contenente un modello BDC

1. Nella barra dei menu in Visual Studio, scegliere **File**, **New**, **progetto**.

     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

2. In presenza di **Visual c#** o **Visual Basic**, espandere il **SharePoint** nodo, quindi scegliere il **2010** elemento.

3. Nel **modelli** riquadro scegliere **progetto SharePoint 2010**, denominare il progetto **AdventureWorksTest**, quindi scegliere il **OK** pulsante .

     Il **Personalizzazione guidata SharePoint** viene visualizzato. In questa procedura guidata, è possibile specificare il sito che si utilizzerà per eseguire il debug del progetto e impostare il livello di attendibilità della soluzione.

4. Scegliere il **Distribuisci come soluzione farm** pulsante di opzione per impostare il livello di attendibilità.

5. Scegliere il **fine** pulsante per accettare il sito di SharePoint locale predefinito.

6. In **Esplora**, scegliere il nodo di progetto SharePoint.

7. Nella barra dei menu, scegliere **progetto**, **Aggiungi nuovo elemento**.

     Viene aperta la finestra di dialogo **Aggiungi nuovo elemento**.

8. Nel **modelli** riquadro scegliere **(solo soluzione Farm) modello di integrazione applicativa dei dati aziendali**, denominare il progetto **AdventureWorksContacts**, quindi scegliere il **Aggiungi** pulsante.

## <a name="adding-data-access-classes-to-the-project"></a>Classi di accesso dati aggiunta al progetto

1. Nella barra dei menu, scegliere **strumenti**, **Connetti al Database**.

     Il **Aggiungi connessione** verrà visualizzata la finestra di dialogo.

2. Aggiungere una connessione al database di esempio AdventureWorks di SQL Server.

     Per ulteriori informazioni, vedere [Aggiungi/Modifica connessione (Microsoft SQL Server)](http://msdn.microsoft.com/fa400910-26c3-4df7-b9d1-115e688b4ea3).

3. Scegliere il nodo di progetto in **Esplora soluzioni**.

4. Nella barra dei menu, scegliere **progetto**, **Aggiungi nuovo elemento**.

5. Nel **modelli installati** riquadro, scegliere il **dati** nodo.

6. Nel **modelli** riquadro scegliere **classi LINQ to SQL**.

7. Nel **nome** specificare **AdventureWorks**, quindi scegliere il **Aggiungi** pulsante.

     Verrà aggiunto al progetto un file con estensione dbml e verrà aperto Object Relational Designer (O/R Designer).

8. Nella barra dei menu, scegliere **vista**, **Esplora Server**.

9. In **Esplora Server**, espandere il nodo che rappresenta il database di esempio AdventureWorks e quindi espandere il **tabelle** nodo.

10. Aggiungere il **Contact (Person)** tabella in Progettazione relazionale oggetti.

     Viene creata una classe di entità, che verrà visualizzata nell'area di progettazione. La classe di entità dispone di proprietà che eseguono il mapping alle colonne della tabella Contact (Person).

## <a name="removing-the-default-entity-from-the-bdc-model"></a>Rimozione dell'entità predefinita dal modello di integrazione applicativa dei dati

Il **modello di integrazione applicativa dei dati di Business** progetto aggiunge un'entità predefinita denominata Entity1 al modello. Rimuovere questa entità. In un secondo momento, si aggiungerà una nuova entità. A partire da un modello vuoto riduce il numero di passaggi necessari per completare la procedura dettagliata.

1. In **Esplora**, espandere il **BdcModel1** nodo e quindi aprire il file Bdcmodel1.

2. Consente di aprire il file del modello di integrazione applicativa dei dati di Business nella finestra di progettazione di integrazione applicativa dei dati.

3. Nella finestra di progettazione, aprire il menu di scelta rapida per **Entity1**, quindi scegliere **eliminare**.

4. In **Esplora**, aprire il menu di scelta rapida per Entity1. vb (in Visual Basic) o Entity1.cs (in c#) e quindi scegliere **eliminare**.

5. Aprire il menu di scelta rapida per Entity1Service. vb (in Visual Basic) o per Entity1Service.cs (in c#) e quindi scegliere **eliminare**.

## <a name="adding-an-entity-to-the-model"></a>Aggiunta di un'entità al modello

Aggiungere un'entità al modello. È possibile aggiungere entità da Visual Studio **della casella degli strumenti** nella finestra di progettazione di integrazione applicativa dei dati.

1. Sulla barra dei menu scegliere **Visualizza**, **Casella degli strumenti**.

2. Nel **BusinessDataConnectivity** scheda della finestra di **della casella degli strumenti**, aggiungere un **entità** nella finestra di progettazione di integrazione applicativa dei dati.

     La nuova entità viene visualizzata nella finestra di progettazione. Visual Studio aggiunge un file denominato EntityService. vb (in Visual Basic) o EntityService.cs (in c#) al progetto.

3. Nella barra dei menu, scegliere **vista**, **proprietà**, **finestra**.

4. Nel **proprietà** finestra, impostare il **nome** valore della proprietà da **contatto**.

5. Nella finestra di progettazione, aprire il menu di scelta rapida per l'entità, scegliere **Aggiungi**, quindi scegliere **identificatore**.

     Verrà visualizzato un nuovo identificatore nell'entità.

6. Nel **proprietà** finestra, modificare il nome dell'identificatore di **ContactID**.

7. Nel **nome del tipo** scegliere **System. Int32**.

## <a name="adding-a-specific-finder-method"></a>Aggiunta di un metodo Finder specifico

Per abilitare il servizio di integrazione applicativa dei dati visualizzare un contatto specifico, è necessario aggiungere un metodo Finder specifico. Il servizio di integrazione applicativa dei dati chiama il metodo Finder specifico quando un utente seleziona un elemento in un elenco e quindi sceglie il **Visualizza elemento** pulsante della barra multifunzione.

Aggiungere un metodo Finder specifico all'entità Contact utilizzando il **Dettagli metodo di integrazione applicativa dei dati** finestra. Per restituire un'entità specifica, aggiungere codice al metodo.

1. Nella finestra di progettazione di integrazione applicativa dei dati, scegliere il **contatto** entità.

2. Nella barra dei menu, scegliere **vista**, **altre finestre**, **Dettagli metodo di integrazione applicativa dei dati**.

     Verrà visualizzata la finestra Dettagli metodo di integrazione applicativa dei dati.

3. Nel **aggiungere un metodo** scegliere **Crea metodo Finder specifico**.

     Visual Studio aggiunge i seguenti elementi al modello. Questi elementi vengono visualizzati nel **Dettagli metodo di integrazione applicativa dei dati** finestra.

    - Un metodo denominato ReadItem.

    - Un parametro di input per il metodo.

    - Un parametro restituito del metodo.

    - Un descrittore di tipo per ogni parametro.

    - Un'istanza del metodo per il metodo.

4. Nel **Dettagli metodo di integrazione applicativa dei dati** finestra, aprire l'elenco visualizzato per il **contatto** descrittore di tipo e quindi scegliere **modifica**.

     Il **Esplora integrazione applicativa dei dati** apre e offre una visualizzazione gerarchica del modello.

5. Nel **proprietà** finestra, aprire l'elenco accanto al **TypeName** proprietà, scegliere il **progetto corrente** scheda e quindi scegliere il **contatto**proprietà.

6. Nel **Esplora integrazione applicativa dei dati**, aprire il menu di scelta rapida del **contatto**, quindi scegliere **Aggiungi descrittore tipo**.

     Un nuovo descrittore di tipo denominato **TypeDescriptor1** è presente il **Esplora integrazione applicativa dei dati**.

7. Nel **proprietà** finestra, impostare il **nome** valore della proprietà da **ContactID**.

8. Aprire l'elenco accanto al **TypeName** proprietà, quindi scegliere **Int32**.

9. Aprire l'elenco accanto al **identificatore** proprietà, quindi scegliere **ContactID**.

10. Ripetere il passaggio 6 per creare un descrittore di tipo per ognuno dei seguenti campi.

    |nome|Nome tipo|
    |----------|---------------|
    |FirstName|System.String|
    |LastName|System.String|
    |Telefono|System.String|
    |emailAddress|System.String|
    |EmailPromotion|System.Int32|
    |NameStyle|System.Boolean|
    |PasswordHash|System.String|
    |PasswordSalt|System.String|

11. Nella finestra di progettazione di integrazione applicativa dei dati sul **contatto** entità, aprire il **ReadItem** metodo.

     Il file di codice del servizio di Contact verrà aperto nell'Editor di codice.

12. Nel `ContactService` classe, sostituire il `ReadItem` (metodo) con il codice seguente. Mediante il codice vengono effettuate le seguenti attività:

    - Recupera un record dalla tabella Contact del database AdventureWorks.

    - Restituisce un'entità Contact al servizio di integrazione applicativa dei dati.

    > [!NOTE]
    > Sostituire il valore di `ServerName` campo con il nome del server.

     [!code-csharp[SP_BDC#3](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#3)]

## <a name="adding-a-finder-method"></a>Aggiunta di un metodo Finder

Per abilitare il servizio di integrazione applicativa dei dati visualizzare un elenco di contatti, è necessario aggiungere un metodo Finder. Aggiungere un metodo Finder all'entità Contact tramite il **Dettagli metodo di integrazione applicativa dei dati** finestra. Per restituire una raccolta di entità per il servizio di integrazione applicativa dei dati, aggiungere codice al metodo.

1. Nella finestra di progettazione di integrazione applicativa dei dati, scegliere il **contatto** entità.

2. Nel **Dettagli metodo di integrazione applicativa dei dati** Comprimi finestra il **ReadItem** nodo.

3. Nel **aggiungere un metodo** elenco sotto il **ReadList** (metodo), scegliere **Crea metodo Finder**.

     Visual Studio aggiunge un metodo, un parametro restituito e un descrittore di tipo.

4. Nella finestra di progettazione di integrazione applicativa dei dati sul **contatto** entità, aprire il **ReadList** metodo.

     Il file di codice per il servizio di Contact verrà aperto nell'editor di codice.

5. Nel `ContactService` classe, sostituire il `ReadList` (metodo) con il codice seguente. Mediante il codice vengono effettuate le seguenti attività:

    - Recupera i dati dalla tabella Contacts del database AdventureWorks.

    - Restituisce un elenco di entità di contatto per il servizio di integrazione applicativa dei dati.

    > [!NOTE]
    > Sostituire il valore di `ServerName` campo con il nome del server.

     [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]

## <a name="testing-the-project"></a>Test del progetto

Quando si esegue il progetto, viene aperto il sito di SharePoint e Visual Studio viene aggiunto il modello per il servizio di integrazione applicativa dei dati aziendali. Creare un elenco esterno in SharePoint che fa riferimento all'entità di contatto. Nell'elenco sono presenti i dati per i contatti nel database AdventureWorks.

> [!NOTE]
> Potrebbe essere necessario modificare le impostazioni di sicurezza in SharePoint prima di poter eseguire il debug della soluzione. Per ulteriori informazioni, vedere [progettazione di un modello di connettività dei dati di Business](../sharepoint/designing-a-business-data-connectivity-model.md).

1. Premere **F5**.

     Apre il sito di SharePoint.

2. Nel **Azioni sito** menu, scegliere il **altre opzioni** comando.

3. Nel **crea** pagina, scegliere il **elenco esterno** , modello e quindi scegliere il **crea** pulsante.

4. Nome elenco personalizzato **contatti**.

5. Scegliere il pulsante Sfoglia accanto al **tipo di contenuto esterno** campo.

6. Nel **Selezione tipo di contenuto esterno** finestra di dialogo scegliere la **AdventureWorksContacts.BdcModel1.Contact** elemento e quindi scegliere il **crea** pulsante.

     In SharePoint viene creato un elenco esterno con i contatti del database di esempio AdventureWorks.

7. Per testare il metodo Finder specifico, scegliere un contatto nell'elenco.

8. Sulla barra multifunzione, scegliere il **elementi** scheda e quindi scegliere il **Visualizza elemento** comando.

     I dettagli del contatto selezionato verranno visualizzati in un form.

## <a name="next-steps"></a>Passaggi successivi

Per informazioni sulla progettazione di modelli per il servizio di integrazione applicativa dei dati in SharePoint, vedere gli argomenti seguenti:

- [Procedura: aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md).
- [Procedura: aggiungere un metodo Updater](../sharepoint/how-to-add-an-updater-method.md).
- [Procedura: aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md).

## <a name="see-also"></a>Vedere anche

[Progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md)  
[Creazione di un modello di integrazione applicativa dei dati](../sharepoint/creating-a-business-data-connectivity-model.md)  
[Panoramica degli strumenti di progettazione del modello di integrazione applicativa dei dati](../sharepoint/bdc-model-design-tools-overview.md)  
[Integrazione di dati business in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
