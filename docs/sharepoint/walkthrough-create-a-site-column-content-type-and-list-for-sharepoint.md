---
title: 'Procedura dettagliata: Creazione di una colonna del sito, tipo di contenuto e l''elenco per SharePoint | Documenti Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.ListDesigner.GeneralMessageHelp
- Microsoft.VisualStudio.SharePoint.Designers.ListDesigner.ViewModels.ListViewModel.SortingAndGrouping
- VS.SharePointTools.ListDesigner.SortingGrouping
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, list definitions
- SharePoint development in Visual Studio, list instances
- SharePoint development in Visual Studio, fields
- SharePoint development in Visual Studio, content types
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 4db9ed078131e7152f3987c80f4e6181f888e540
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-create-a-site-column-content-type-and-list-for-sharepoint"></a>Procedura dettagliata: creare una colonna del sito, un tipo di contenuto e un elenco per SharePoint
  Le procedure seguenti viene illustrato come creare colonne del sito di SharePoint personalizzate, o *campi*, nonché un tipo di contenuto che utilizza le colonne del sito. Viene inoltre illustrato come creare un elenco che viene utilizzato il nuovo tipo di contenuto.  
  
 In questa procedura dettagliata sono incluse le attività seguenti:  
  
-   [Creazione di colonne del sito personalizzato](#BKMK_CreatingCustSiteCols).  
  
-   [Creazione di un tipo di contenuto personalizzato](#BKMK_CreateCustContType).  
  
-   [Creazione di un elenco](#BKMK_CreateList).  
  
-   [Creazione di un elenco](#BKMK_CreateList).  
  
-   [Test dell'applicazione](#BKMK_TestApp).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   Le edizioni supportate di Windows e SharePoint. Per ulteriori informazioni, vedere [requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
##  <a name="BKMK_CreatingCustSiteCols"></a>Creazione di colonne del sito personalizzato  
 Questo esempio crea un elenco per la gestione dei pazienti in un ospedale. In primo luogo, è necessario creare un progetto SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e aggiungervi le colonne del sito, come indicato di seguito.  
  
#### <a name="to-create-the-project"></a>Per creare il progetto  
  
1.  Nel [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **File** menu, scegliere **New**, **progetto**.  
  
2.  Nel **nuovo progetto** in presenza di una finestra di dialogo **Visual c#** o **Visual Basic**, espandere il **SharePoint** nodo, quindi scegliere **2010**.  
  
3.  Nel **modelli** riquadro scegliere **progetto SharePoint 2010**, modificare il nome del progetto per **Clinic**, quindi scegliere il **OK** pulsante.  
  
     Il modello di progetto SharePoint 2010 è un progetto vuoto che viene utilizzato in questo esempio per contenere le colonne del sito e altri elementi di progetto che vengono aggiunti in seguito.  
  
4.  Nel **specificare il livello di sito e di sicurezza per il debug** pagina, immettere l'URL del sito di SharePoint locale a cui si desidera aggiungere il nuovo elemento di campo personalizzato oppure utilizzare il percorso predefinito (`http://<`*NomeSistema* `>/)`.  
  
5.  Nel **qual è il livello di attendibilità per la soluzione SharePoint?** sezione, utilizzare il valore predefinito **Distribuisci come soluzione creata mediante sandbox**.  
  
     Per ulteriori informazioni su creata mediante sandbox e soluzioni farm, vedere [considerazioni sulle soluzioni create mediante sandbox](../sharepoint/sandboxed-solution-considerations.md).  
  
6.  Scegliere il **fine** pulsante. Il progetto dovrebbe ora essere elencato **Esplora**.  
  
#### <a name="to-add-site-columns"></a>Per aggiungere le colonne del sito  
  
1.  Aggiungere una nuova colonna del sito. A tale scopo, in **Esplora**, aprire il menu di scelta rapida per **Clinic**, quindi scegliere **Aggiungi**, **nuovo elemento**.  
  
2.  Nel **Aggiungi nuovo elemento** finestra di dialogo scegliere **colonna del sito**, modificare il nome in **Nome paziente**, quindi scegliere il **Aggiungi** pulsante.  
  
3.  Nel file Elements.xml della colonna del sito, lasciare il **tipo** impostando come **testo**e modificare il **gruppo** impostando su **colonne del sito Clinic**. Al termine, i file Elements.xml della colonna del sito dovrebbe essere analogo al seguente.  
  
    ```  
    <Field  
         ID="{f9ba60d1-5631-41fb-b016-a38cf48eef63}"  
         Name="Clinic - Patient Name"  
         DisplayName="Patient Name"  
         Type="Text"  
         Required="FALSE"  
         Group="Clinic Site Columns">  
    </Field>  
    ```  
  
4.  Utilizzando la stessa procedura, aggiungere altre due colonne del sito al progetto: **ID paziente** (tipo = "Integer") e **Nome medico** (tipo = "Text"). Impostare il valore di gruppo **colonne del sito Clinic**.  
  
##  <a name="BKMK_CreateCustContType"></a>Creazione di un tipo di contenuto personalizzato  
 Successivamente, creare un tipo di contenuto, in base al tipo di contenuto di contatti, che include le colonne del sito creato nella procedura precedente. È possibile basare un tipo di contenuto su un tipo di contenuto esistente, per risparmiare tempo perché il tipo di contenuto base fornisce diverse colonne del sito da utilizzare nel nuovo tipo di contenuto.  
  
#### <a name="to-create-a-custom-content-type"></a>Per creare un tipo di contenuto personalizzato  
  
1.  Aggiungere un tipo di contenuto al progetto. A tale scopo, in **Esplora**, scegliere il nodo del progetto  
  
2.  Nella barra dei menu, scegliere **progetto**, **Aggiungi nuovo elemento**.  
  
3.  In presenza di **Visual c#** o **Visual Basic**, espandere il **SharePoint** nodo, quindi scegliere il **2010** nodo.  
  
4.  Nel **modelli** riquadro, scegliere il **tipo di contenuto** modello, modificare il nome in **Info paziente**e quindi scegliere il **Aggiungi** pulsante.  
  
     Il **Personalizzazione guidata SharePoint** apre.  
  
5.  Nel **quale tipo di contenuto di base deve ereditare questo tipo di contenuto da** scegliere **contatto** come tipo di contenuto su cui basare il nuovo tipo di contenuto e quindi scegliere il **fine**pulsante.  
  
     Questa operazione consente di accedere ad altre colonne sito potenzialmente utile nel tipo di contenuto contatto, oltre alle colonne del sito definito in precedenza.  
  
6.  Dopo il tipo di contenuto finestra di progettazione viene visualizzata, nel **colonne** scheda, aggiungere tre siti le colonne definite in precedenza: **Nome paziente**, **ID paziente**e **Nome medico**. Per aggiungere tali colonne, scegliere la prima casella di riepilogo nell'elenco di colonne del sito in **nome visualizzato**, quindi scegliere ogni colonna del sito nell'elenco uno alla volta.  
  
    > [!TIP]  
    >  Per scegliere le colonne del sito più rapidamente, filtrare l'elenco immettendo le prime lettere del nome della colonna.  
  
7.  Oltre alle tre colonne sito personalizzato, aggiungere il **commenti** colonna del sito dall'elenco delle colonne del sito.  
  
8.  Selezionare il **obbligatorio** casella di controllo per il **Nome paziente** e **ID paziente** colonne del sito in modo da renderle campi obbligatori.  
  
9. Nel **Content Type** scheda, assicurarsi che il nome del tipo di contenuto sia **Info paziente**e quindi modificare la descrizione in **scheda informazioni sui pazienti**.  
  
10. Modifica **nome gruppo** a **tipi di contenuto Clinic**e lasciare le altre impostazioni in base ai valori predefiniti.  
  
11. Nella barra dei menu, scegliere **File**, **Salva tutto**, quindi chiudere la finestra di progettazione del tipo di contenuto.  
  
##  <a name="BKMK_CreateList"></a>Creazione di un elenco  
 A questo punto, creare un elenco che utilizza le nuove colonne di tipo e il sito del contenuto.  
  
#### <a name="to-create-a-list"></a>Per creare un elenco  
  
1.  Aggiungere un elenco al progetto. A tale scopo, in **Esplora**, scegliere il nodo del progetto.  
  
2.  Nella barra dei menu, scegliere **progetto**, **Aggiungi nuovo elemento**.  
  
3.  In presenza di **Visual c#** o **Visual Basic**, espandere il **SharePoint** nodo, quindi scegliere il **2010** nodo.  
  
4.  Nel **modelli** riquadro, scegliere il **elenco** modello, modificare il nome in **pazienti**e quindi scegliere il **Aggiungi** pulsante.  
  
5.  Lasciare il **personalizzare l'elenco in base a** impostando come **predefinito (vuoto)**, quindi scegliere il **fine** pulsante.  
  
6.  Nella finestra di progettazione di elenco, scegliere il **tipi di contenuto** pulsante per visualizzare il **impostazioni del tipo di contenuto** la finestra di dialogo.  
  
7.  Scegliere la nuova riga, scegliere il **Info paziente** il contenuto di tipo nell'elenco dei tipi di contenuto e quindi scegliere il **OK** pulsante.  
  
     Questa operazione aggiunge tutte le colonne del sito dal **Info paziente** tipo nell'elenco di contenuto.  
  
8.  Eliminare tutte le colonne del sito nell'elenco, ad eccezione dei seguenti:  
  
    -   ID del paziente  
  
    -   Nome del paziente  
  
    -   Telefono dell'abitazione  
  
    -   Posta elettronica  
  
    -   Nome medico  
  
    -   Commenti  
  
9. In **nome visualizzato colonna**, scegliere una riga vuota, aggiungere una colonna di elenco personalizzato e denominarlo **ospedale**. Lasciare il tipo di dati come **una riga di testo**.  
  
     La colonna di elenco personalizzato si applica solo a questo elenco. Quando si aggiunge una colonna di elenco personalizzato per un elenco, un nuovo tipo di contenuto, incluse tutte le colonne aggiunte nell'elenco, viene creato e impostato come elenco predefinito.  
  
    > [!TIP]  
    >  Se si sceglie una colonna dall'elenco di colonne del sito, viene utilizzata una colonna di sito esistente. Tuttavia, se si immette un valore di nome di colonna senza scegliere tutte le colonne nell'elenco, viene creata una colonna di elenco personalizzato, anche se una colonna con lo stesso nome esiste già nell'elenco.  
  
     Facoltativamente, anziché impostare il tipo di dati della colonna di elenco personalizzato per **una riga di testo**, invece, è possibile impostare il tipo di dati per la colonna di ricerca e i relativi valori verrebbero recuperati da una tabella o un altro elenco. Per informazioni sulle colonne di ricerca, vedere [relazioni di elenco in SharePoint 2010](http://go.microsoft.com/fwlink/?LinkId=224994) e [ricerche e le relazioni di elenco](http://go.microsoft.com/fwlink/?LinkID=224995).  
  
10. Accanto al **ID paziente** e **Nome paziente** caselle, selezionare il **necessari** casella di controllo.  
  
11. Nel **viste** scheda, scegliere una riga vuota per creare una vista. Immettere **i dettagli sui pazienti**.  
  
     Nel **viste** scheda, è possibile specificare le colonne che si desidera visualizzare nell'elenco di SharePoint.  
  
12. Scegliere la nuova **dettagli paziente** di riga e quindi scegliere il **imposta come predefinito** pulsante.  
  
     La nuova vista è ora la visualizzazione predefinita per l'elenco.  
  
13. Aggiungere le colonne seguenti per il **colonne selezionate** elenco nell'ordine seguente:  
  
    -   ID del paziente  
  
    -   Nome del paziente  
  
    -   Telefono dell'abitazione  
  
    -   Posta elettronica  
  
    -   Nome medico  
  
    -   Ospedale  
  
    -   Commenti  
  
14. Nel **proprietà** scegliere il **ordinamento e raggruppamento** , proprietà e quindi scegliere il pulsante con i puntini di sospensione ![icona puntini di sospensione](../sharepoint/media/ellipsisicon.gif "i puntini di sospensione icona")per visualizzare il **ordinamento e raggruppamento** la finestra di dialogo.  
  
15. Nel **nome di colonna** scegliere **Nome paziente**, assicurarsi che il **ordinamento** colonna è impostata su **crescente**e quindi scegliere il  **OK** pulsante.  
  
##  <a name="BKMK_TestApp"></a>Test dell'applicazione  
 Ora che le colonne del sito personalizzati, tipo di contenuto ed elenco sono pronti, distribuirle in SharePoint ed eseguire l'applicazione per eseguire il test.  
  
#### <a name="to-test-the-application"></a>Per eseguire il test dell'applicazione  
  
1.  Nella barra dei menu scegliere **File**, **Salva tutto**.  
  
2.  Premere F5 per eseguire l'applicazione.  
  
     L'applicazione viene compilata e quindi le funzionalità sono distribuite in SharePoint e attivate.  
  
3.  Sulla barra di navigazione rapida, scegliere il **pazienti** link per visualizzare il **pazienti** elenco.  
  
     I nomi delle colonne nell'elenco devono corrispondere a quelli che è stato immesso il **viste** scheda [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
4.  Scegliere il **Aggiungi nuovo elemento** collegamento per creare una scheda informazioni sui pazienti.  
  
5.  Immettere le informazioni nei campi e quindi scegliere il **salvare** pulsante.  
  
     Il nuovo record venga visualizzato nell'elenco.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di colonne del sito, tipi di contenuto ed elenchi per SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md)   
 [Sviluppo di soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Procedura: creare un tipo di campo personalizzato](http://go.microsoft.com/fwlink/?LinkId=192079)   
 [Tipi di contenuto](http://go.microsoft.com/fwlink/?LinkId=192080)   
 [Colonne](http://go.microsoft.com/fwlink/?LinkId=192081)  
  
  