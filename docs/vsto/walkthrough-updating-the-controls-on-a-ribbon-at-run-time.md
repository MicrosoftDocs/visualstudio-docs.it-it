---
title: 'Procedura dettagliata: Aggiornamento dei controlli in una barra multifunzione in fase di esecuzione | Documenti Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], controls
- updating Ribbon controls
- Ribbon [Office development in Visual Studio], dynamic menu
- dynamic menus [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], updating
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 39952d1059833c92d3d5e8c277faac1b47c6e80b
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-updating-the-controls-on-a-ribbon-at-run-time"></a>Procedura dettagliata: aggiornamento dei controlli di una barra multifunzione in fase di esecuzione
  Questa procedura dettagliata illustra come usare il modello a oggetti della barra multifunzione per aggiornare i controlli di una barra multifunzione dopo che la barra multifunzione è stata caricata nell'applicazione Office.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 L'esempio effettua il pull dei dati del database di esempio Northwind per popolare una casella combinata e un menu in Microsoft Office Outlook. Gli elementi selezionati in questi controlli automaticamente popolano i campi, ad esempio **a** e **soggetto** in un messaggio di posta elettronica.  
  
 Questa procedura dettagliata illustra le attività seguenti:  
  
-   Creazione di un nuovo progetto di componente aggiuntivo VSTO per Outlook.  
  
-   Progettazione di un gruppo personalizzato della barra multifunzione.  
  
-   Aggiunta del gruppo personalizzato a una scheda predefinita.  
  
-   Aggiornamento dei controlli della barra multifunzione in fase di esecuzione.  
  
> [!NOTE]  
>  I nomi o i percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Outlook  
  
## <a name="creating-a-new-outlook-vsto-add-in-project"></a>Creazione di un nuovo progetto di componente aggiuntivo VSTO di Outlook  
 Prima di tutto, creare un progetto di componente aggiuntivo VSTO di Outlook.  
  
#### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>Per creare un nuovo progetto di componente aggiuntivo VSTO di Outlook  
  
1.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], creare un progetto di componente aggiuntivo VSTO di Outlook con il nome **Ribbon_Update_At_Runtime**.  
  
2.  Nella finestra di dialogo **Nuovo progetto** selezionare **Crea directory per soluzione**.  
  
3.  Salvare il progetto nella directory del progetto predefinita.  
  
     Per altre informazioni, vedere [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
## <a name="designing-a-custom-ribbon-group"></a>Progettazione di un gruppo personalizzato della barra multifunzione  
 La barra multifunzione per questo esempio verrà visualizzata quando un utente compone un nuovo messaggio di posta. Per creare un gruppo personalizzato per la barra multifunzione, aggiungere prima un elemento barra multifunzione al progetto, quindi progettare il gruppo nella finestra di progettazione della barra multifunzione. Questo gruppo personalizzato consente di generare messaggi di posta elettronica da completare per i clienti usando nomi e cronologie di ordine di un database.  
  
#### <a name="to-design-a-custom-group"></a>Per progettare un gruppo personalizzato  
  
1.  Nel menu **Progetto** fare clic su **Aggiungi nuovo elemento**.  
  
2.  Nella finestra di dialogo **Aggiungi nuovo elemento** selezionare **Barra multifunzione (finestra di progettazione visiva)**.  
  
3.  Modificare il nome della nuova barra multifunzione per **CustomerRibbon**, quindi fare clic su **Aggiungi**.  
  
     Il **CustomerRibbon. cs** o **CustomerRibbon. vb** nella finestra di progettazione della barra multifunzione e visualizza una scheda predefinita e un gruppo di file.  
  
4.  Fare clic nella finestra di progettazione per selezionarlo.  
  
5.  Nel **proprietà** finestra, fare clic sulla freccia giù accanto al **RibbonType** , proprietà e quindi fare clic su **Compose**.  
  
     In tal modo, la barra multifunzione viene visualizzata quando l'utente compone un nuovo messaggio di posta in Outlook.  
  
6.  Nella finestra di progettazione della barra multifunzione, fare clic su **Group1** per selezionarlo.  
  
7.  Nel **proprietà** finestra impostare **etichetta** a **Customer Purchases**.  
  
8.  Dal **controlli della barra multifunzione di Office** scheda della finestra il **della casella degli strumenti**, trascinare un **ComboBox** sul **Customer Purchases** gruppo.  
  
9. Fare clic su **ComboBox1** per selezionarlo.  
  
10. Nel **proprietà** finestra impostare **etichetta** a **clienti**.  
  
11. Dal **controlli della barra multifunzione di Office** scheda della finestra il **della casella degli strumenti**, trascinare un **Menu** sul **Customer Purchases** gruppo.  
  
12. Nel **proprietà** finestra impostare **etichetta** a **prodotto acquistato**.  
  
13. Impostare **dinamica** a **true**.  
  
     In tal modo, è possibile aggiungere e rimuovere i controlli nel menu in fase di esecuzione dopo che la barra multifunzione è stata caricata nell'applicazione Office.  
  
## <a name="adding-the-custom-group-to-a-built-in-tab"></a>Aggiunta del gruppo personalizzato a una scheda predefinita  
 Una scheda incorporata rappresenta una scheda già presente sulla barra multifunzione di una finestra di esplorazione o di un controllo di Outlook. In questa procedura, si aggiunge il gruppo personalizzato a una scheda predefinita e quindi si specifica la posizione del gruppo personalizzato nella scheda.  
  
#### <a name="to-add-the-custom-group-to-a-built-in-tab"></a>Per aggiungere il gruppo personalizzato a una scheda predefinita  
  
1.  Fare clic su di **TabAddins (Built-)** tab per selezionarlo.  
  
2.  Nel **proprietà** finestra, espandere il **ControlId** proprietà e quindi impostare **OfficeId** a **TabNewMailMessage**.  
  
     Aggiunge il **Customer Purchases** gruppo il **messaggi** scheda della barra multifunzione che viene visualizzato in un nuovo messaggio di posta elettronica.  
  
3.  Fare clic su di **Customer Purchases** gruppo per selezionarlo.  
  
4.  Nel **proprietà** finestra, espandere il **posizione** proprietà, fare clic sulla freccia giù accanto al **PositionType** , proprietà e quindi fare clic su  **BeforeOfficeId**.  
  
5.  Impostare il **OfficeId** proprietà **GroupClipboard**.  
  
     Viene posizionato il **Customer Purchases** gruppo prima di **negli Appunti** gruppo del **messaggi** scheda.  
  
## <a name="creating-the-data-source"></a>Creazione dell'origine dati  
 Usare la finestra **Origini dati** per aggiungere un DataSet tipizzato al progetto.  
  
#### <a name="to-create-the-data-source"></a>Per creare l'origine dati  
  
1.  Scegliere **Aggiungi nuova origine dati** dal menu **Dati**.  
  
     Verrà avviata la **configurazione guidata origine dati**.  
  
2.  Selezionare **Database**, quindi fare clic su **Avanti**.  
  
3.  Selezionare **Dataset**, quindi fare clic su **Avanti**.  
  
4.  Selezionare una connessione dati al database di Microsoft SQL Server Compact 4.0 di esempio Northwind, o aggiungere una nuova connessione utilizzando il **nuova connessione** pulsante.  
  
5.  Dopo una connessione è stata selezionata o creata, fare clic su **Avanti**.  
  
6.  Fare clic su **Avanti** per salvare la stringa di connessione.  
  
7.  Nel **Seleziona oggetti di Database** espandere **tabelle**.  
  
8.  Selezionare la casella di controllo accanto a ciascuna delle seguenti tabelle:  
  
    1.  **Clienti**  
  
    2.  **Dettagli dell'ordine**  
  
    3.  **Ordini**  
  
    4.  **Prodotti**  
  
9. Scegliere **Fine**.  
  
## <a name="updating-controls-in-the-custom-group-at-run-time"></a>Aggiornamento dei controlli nel gruppo personalizzato in fase di esecuzione  
 Usare il modello a oggetti della barra multifunzione per effettuare le seguenti attività:  
  
-   Aggiungere nomi di clienti il **clienti** casella combinata.  
  
-   Aggiungere menu e controlli di pulsanti per la **prodotti acquistati** menu che rappresenta gli ordini di vendita e i prodotti venduti.  
  
-   Popolare a, oggetto e corpo campi dei nuovi messaggi di posta elettronica utilizzando dati di **clienti** casella combinata e **prodotti acquistati** menu.  
  
#### <a name="to-update-controls-in-the-custom-group-by-using-the-ribbon-object-model"></a>Per aggiornare i controlli nel gruppo personalizzato usando il modello a oggetti della barra multifunzione  
  
1.  Scegliere **Aggiungi riferimento** dal menu **Progetto**.  
  
2.  Nel **Aggiungi riferimento** la finestra di dialogo, fare clic sul **.NET** , selezionare il **LINQ** assembly e quindi fare clic su **OK**.  
  
     Questo assembly contiene le classi per l'uso di Language-Integrated Queries (LINQ). LINQ viene usato per popolare i controlli nel gruppo personalizzato con i dati del database Northwind.  
  
3.  In **Esplora**, fare clic su **CustomerRibbon. cs** o **CustomerRibbon. vb** per selezionarlo.  
  
4.  Nel **vista** menu, fare clic su **codice**.  
  
     Il file di codice della barra multifunzione viene aperto nell'editor di codice.  
  
5.  Aggiungere le seguenti istruzioni alla parte iniziale del file di codice della barra multifunzione. Queste istruzioni forniscono l'accesso agli spazi dei nomi LINQ e allo spazio dei nomi dell'assembly di interoperabilità primario (PIA) di Outlook.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#1](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#1)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#1](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#1)]  
  
6.  Aggiungere il codice seguente all'interno della classe CustomerRibbon. Il codice dichiara la tabella dati e gli adattatori di tabella che verranno usati per archiviare le informazioni delle tabelle Clienti, Ordini, Dettagli sugli ordini e Prodotti del database Northwind.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#2](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#2](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#2)]  
  
7.  Aggiungere il seguente blocco di codice alla classe `CustomerRibbon`. Questo codice aggiunge tre metodi di supporto che creano i controlli per la barra multifunzione in fase di esecuzione.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#3](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#3](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#3)]  
  
8.  Sostituire il metodo del gestore eventi `CustomerRibbon_Load` con il codice seguente. Questo codice usa una query LINQ per eseguire le attività seguenti:  
  
    -   Popolare il **clienti** casella combinata con l'ID e nome di 20 clienti del database Northwind.  
  
    -   Chiama il metodo di supporto `PopulateSalesOrderInfo`. Questo metodo aggiorna il **ProductsPurchased** menu con numeri di ordine di vendita relativi al cliente attualmente selezionato.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#4](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#4)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#4](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#4)]  
  
9. Aggiungere il codice seguente alla classe `CustomerRibbon`. Questo codice usa le query LINQ per eseguire le attività seguenti:  
  
    -   Aggiungere un sottomenu di **ProductsPurchased** menu per ogni ordine di vendita correlati al cliente selezionato.  
  
    -   Aggiungere pulsanti a ogni sottomenu per i prodotti relativi all'ordine di vendita.  
  
    -   Aggiungere gestori eventi a ogni pulsante.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#6](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#6)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#6](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#6)]  
  
10. In **Esplora**, fare doppio clic sul file di codice della barra multifunzione.  
  
     La finestra di progettazione della barra multifunzione viene aperta.  
  
11. Nella finestra di progettazione della barra multifunzione, fare doppio clic su di **clienti** casella combinata.  
  
     Nell'editor di codice viene aperto il file di codice della barra multifunzione e viene visualizzato il gestore eventi `ComboBox1_TextChanged`.  
  
12. Sostituire il gestore eventi `ComboBox1_TextChanged` con il codice seguente. Mediante il codice vengono effettuate le seguenti attività:  
  
    -   Chiama il metodo di supporto `PopulateSalesOrderInfo`. Questo metodo aggiorna il **prodotti acquistati** menu con gli ordini di vendita relativi al cliente selezionato.  
  
    -   Chiama il metodo di supporto `PopulateMailItem` e passa al testo corrente, ossia il nome del cliente selezionato. Questo metodo popola a, oggetto e corpo campi dei nuovi messaggi di posta elettronica.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#5](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#5)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#5](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#5)]  
  
13. Aggiungere il gestore dell'evento Click indicato di seguito alla classe `CustomerRibbon`. Questo codice aggiunge il nome dei prodotti selezionati per il campo del corpo di nuovi messaggi di posta elettronica.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#8](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#8)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#8](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#8)]  
  
14. Aggiungere il codice seguente alla classe `CustomerRibbon`. Mediante il codice vengono effettuate le seguenti attività:  
  
    -   Inserisce la riga a dei nuovi messaggi di posta elettronica usando l'indirizzo di posta elettronica del cliente attualmente selezionato.  
  
    -   Aggiunge il testo per i campi di tipo di oggetto e il corpo di nuovi messaggi di posta elettronica.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#7](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#7)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#7](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#7)]  
  
## <a name="testing-the-controls-in-the-custom-group"></a>Test dei controlli nel gruppo personalizzato  
 Quando si apre un nuovo modulo di posta elettronica in Outlook, un gruppo personalizzato denominato **Customer Purchases** è presente il **messaggi** scheda della barra multifunzione.  
  
 Per creare un messaggio di posta elettronica da completare per il cliente, selezionare un cliente e quindi selezionare i prodotti acquistati dal cliente. I controlli di **Customer Purchases** gruppo vengono aggiornati in fase di esecuzione con i dati dal database Northwind.  
  
#### <a name="to-test-the-controls-in-the-custom-group"></a>Per testare i controlli nel gruppo personalizzato  
  
1.  Premere F5 per eseguire il progetto.  
  
     Viene avviato Outlook.  
  
2.  In Outlook, nel **File** dal menu **New**, quindi fare clic su **messaggio di posta elettronica**.  
  
     Eseguire le azioni seguenti:  
  
    -   Viene visualizzata una nuova finestra di controllo del messaggio di posta.  
  
    -   Nel **messaggio** scheda della barra multifunzione, il **Customer Purchases** gruppo viene visualizzato prima il **Appunti** gruppo.  
  
    -   Il **clienti** casella combinata gruppo viene aggiornata con i nomi dei clienti nel database Northwind.  
  
3.  Nel **messaggio** scheda della barra multifunzione, nel **Customer Purchases** gruppo, selezionare un cliente dal **clienti** casella combinata.  
  
     Eseguire le azioni seguenti:  
  
    -   Il **prodotti acquistati** menu viene aggiornato per visualizzare ogni ordine di vendita per il cliente selezionato.  
  
    -   Ogni sottomenu dell'ordine di vendita viene aggiornato in modo da visualizzare i prodotti acquistati in quell'ordine.  
  
    -   Indirizzo di posta elettronica del cliente selezionato viene aggiunto al **a** riga di messaggio di posta elettronica, l'oggetto e corpo del messaggio di posta vengono popolati con testo.  
  
4.  Fare clic su di **Products Purchases** menu, selezionare un ordine di vendita e quindi fare clic su un prodotto dall'ordine di vendita.  
  
     Il nome di prodotto viene aggiunto al corpo del messaggio di posta.  
  
## <a name="next-steps"></a>Passaggi successivi  
 È possibile trovare ulteriori informazioni sulla personalizzazione dell'interfaccia utente di Office nei seguenti argomenti:  
  
-   Aggiunta di un'interfaccia utente basata sul contesto a una personalizzazione a livello di documento. Per altre informazioni, vedere [Actions Pane Overview](../vsto/actions-pane-overview.md).  
  
-   Estensione di un modulo standard o personalizzato di Microsoft Office Outlook. Per ulteriori informazioni, vedere [procedura dettagliata: progettazione di un'area del modulo di Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).  
  
-   Aggiungere un riquadro attività personalizzato a Outlook. Per ulteriori informazioni, vedere [riquadri attività personalizzati](../vsto/custom-task-panes.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Accessing the Ribbon at Run Time](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)   
 [Language-Integrated Query (LINQ)](/dotnet/csharp/linq/index)   
 [Procedura: iniziare a personalizzare la barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)   
 [Procedura dettagliata: Creazione di una scheda personalizzata utilizzando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Panoramica del modello a oggetti della barra multifunzione](../vsto/ribbon-object-model-overview.md)   
 [Personalizzazione di una barra multifunzione per Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Procedura: modificare la posizione di una scheda della barra multifunzione](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [Procedura: personalizzare una scheda incorporata](../vsto/how-to-customize-a-built-in-tab.md)   
 [Procedura: aggiungere controlli alla visualizzazione Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Procedura: esportare una barra multifunzione dalla finestra di progettazione della barra multifunzione alla barra multifunzione XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [Procedura: Visualizzare gli errori dell'interfaccia utente del componente aggiuntivo](../vsto/how-to-show-add-in-user-interface-errors.md)  
  
  