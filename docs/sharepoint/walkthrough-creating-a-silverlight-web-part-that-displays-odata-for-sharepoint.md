---
title: 'Procedura dettagliata: Creazione di una Web Part Silverlight che visualizza OData per SharePoint | Documenti Microsoft'
ms.custom: 
ms.date: 02/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.SPE.SilverlightWebPart
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 3c2c66490e0eb46508fce0f346fe44563548b407
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint"></a>Procedura dettagliata: creazione di una Web part Silverlight che visualizza il servizio OData per SharePoint
  SharePoint 2010 espone i dati elenco tramite OData. In SharePoint, il servizio OData è implementato dal servizio RESTful ListData.svc. Questa procedura dettagliata viene illustrato come creare una web part di SharePoint che ospita un'applicazione Silverlight. L'applicazione Silverlight consente di visualizzare informazioni relative all'elenco SharePoint annuncio utilizzando ListData.svc. Per ulteriori informazioni, vedere [interfaccia REST di SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=225999) e [Open Data Protocol](http://go.microsoft.com/fwlink/?LinkId=226000).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   Edizioni supportate di Microsoft Windows e SharePoint. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].  
  
##  <a name="creating-a-silverlight-application-and-silverlight-web-part"></a>Creazione di un'applicazione Silverlight e Web Part Silverlight  
 Innanzitutto, creare un'applicazione Silverlight in Visual Studio. L'applicazione Silverlight recupera i dati nell'elenco di annunci di SharePoint tramite il servizio ListData.svc.  
  
> [!NOTE]  
>  Nessuna versione di Silverlight precedenti alla 4.0 supportano le interfacce necessarie per fare riferimento a dati di elenchi SharePoint.  
  
#### <a name="to-create-a-silverlight-application-and-silverlight-web-part"></a>Per creare un'applicazione Silverlight e web part Silverlight  
  
1.  Nella barra dei menu, scegliere **File**, **New**, **progetto** per visualizzare il **nuovo progetto** la finestra di dialogo.  
  
2.  Espandere il **SharePoint** nodo sotto **Visual c#** o **Visual Basic**, quindi scegliere il **2010** nodo.  
  
3.  Nel riquadro dei modelli, scegliere il **Web Part Silverlight di SharePoint 2010** modello.  
  
4.  Nel **nome** immettere **SLWebPartTest** e quindi scegliere il **OK** pulsante.  
  
     Il **Personalizzazione guidata SharePoint** viene visualizzata la finestra di dialogo.  
  
5.  Nel **specificare il livello di sito e di sicurezza per il debug** pagina, immettere l'URL per il server di sito di SharePoint in cui si desidera eseguire il debug di definizione del sito o utilizzare il percorso predefinito (http://*nome sistema*/) .  
  
6.  Nel **qual è il livello di attendibilità per la soluzione SharePoint?** , scegliere il **Distribuisci come soluzione farm** pulsante di opzione.  
  
     Sebbene in questo esempio utilizza una soluzione farm, i progetti di Silverlight web part possono essere distribuiti come farm o soluzioni create mediante sandbox. Per ulteriori informazioni sulle soluzioni create mediante sandbox e soluzioni farm, vedere [considerazioni sulle soluzioni create mediante sandbox](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  Nel **come si desidera associare la Web Part Silverlight** sezione il **specificare le informazioni di configurazione Silverlight** pagina, scegliere il **creare un nuovo progetto Silverlight e associarlo con la web part** pulsante di opzione.  
  
8.  Modifica il **nome** a **SLApplication**, impostare **Language** al **Visual Basic** o **Visual c#**, e quindi impostare **versione Silverlight** a **Silverlight 4.0**.  
  
9. Scegliere il **fine** pulsante. I progetti vengono visualizzati **Esplora**.  
  
     La soluzione contiene due progetti: un'applicazione Silverlight e una web part Silverlight. L'applicazione Silverlight recupera e visualizza i dati elenco SharePoint e la web part Silverlight ospita l'applicazione Silverlight, che consente di visualizzarla in SharePoint.  
  
##  <a name="customizing-the-silverlight-application"></a>Personalizzazione dell'applicazione Silverlight  
 Aggiungere elementi di progettazione e codice per l'applicazione Silverlight.  
  
#### <a name="to-customize-the-silverlight-application"></a>Per personalizzare l'applicazione Silverlight  
  
1.  Aggiungere un riferimento all'assembly System, nell'applicazione Silverlight. Per ulteriori informazioni, vedere [procedura: aggiungere o rimuovere riferimenti utilizzando la finestra di dialogo Aggiungi riferimento](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
2.  In **Esplora**, aprire il menu di scelta rapida per **riferimenti**, quindi scegliere **Aggiungi riferimento al servizio**.  
  
    > [!NOTE]  
    >  Se si utilizza Visual Basic, è necessario scegliere il **Mostra tutti i file** in alto di **Esplora** per visualizzare il **riferimenti** nodo.  
  
3.  Nella casella dell'indirizzo del **Aggiungi riferimento al servizio** finestra di dialogo immettere l'URL del sito di SharePoint, ad esempio **http://MySPSite**, quindi scegliere il **passare** pulsante.  
  
     Quando Silverlight individua il servizio SharePoint OData ListData.svc, l'indirizzo viene sostituito con l'URL completo del servizio. In questo esempio http://myserver diventa http://myserver/_vti_bin/ListData.svc.  
  
4.  Scegliere il **OK** pulsante per aggiungere il riferimento al servizio al progetto e utilizzare il nome di servizio predefinito, ServiceReference1.  
  
5.  Nella barra dei menu scegliere **Compilazione**, **Compila soluzione**.  
  
6.  Aggiungere una nuova origine dati per il progetto in base al servizio di SharePoint. A tale scopo, nella barra dei menu, scegliere **vista**, **altre finestre**, **origini dati**.  
  
     Il **origini dati** finestra Mostra tutti i dati elenco SharePoint disponibili, ad esempio attività, annunci e calendario.  
  
7.  Aggiungere i dati dell'elenco di annunci all'applicazione Silverlight. È possibile trascinare "Annunci" il **origini dati** finestra nella finestra di progettazione di Silverlight.  
  
     Crea un controllo griglia associato all'elenco di annunci del sito di SharePoint.  
  
8.  Ridimensionare il controllo griglia per adattarlo alla pagina di Silverlight.  
  
9. Nel file di codice di MainPage. XAML (MainPage.xaml.cs per Visual c#) o. Xaml. vb per Visual Basic, aggiungere i seguenti riferimenti dello spazio dei nomi.  
  
    ```vb  
    ' Add the following three Imports statements.  
    Imports SLApplication.ServiceReference1  
    Imports System.Windows.Data  
    Imports System.Data.Services.Client  
    ```  
  
    ```csharp  
    // Add the following three using statements.  
    using SLApplication.ServiceReference1;  
    using System.Windows.Data;  
    using System.Data.Services.Client;  
    ```  
  
10. Aggiungere le seguenti dichiarazioni di variabili nella parte superiore della classe.  
  
    ```vb  
    Private context As TeamSiteDataContext  
    Private myCollectionViewSource As CollectionViewSource  
    Private announcements As New DataServiceCollection(Of AnnouncementsItem)()  
    ```  
  
    ```csharp  
    private TeamSiteDataContext context;  
    private CollectionViewSource myCollectionViewSource;  
    DataServiceCollection<AnnouncementsItem> announcements = new DataServiceCollection<AnnouncementsItem>();  
    ```  
   
11. Sostituire il `UserControl_Loaded` procedure con il codice seguente.  
  
    ```vb  
    Private Sub UserControl_Loaded_1(sender As Object, e As RoutedEventArgs)  
        ' The URL for the OData service.  
        ' Replace <server name> in the next line with the name of your SharePoint server.  
        context = New TeamSiteDataContext(New Uri("http://<server name>/_vti_bin/ListData.svc"))  
  
        ' Do not load your data at design time.  
        If Not System.ComponentModel.DesignerProperties.GetIsInDesignMode(Me) Then  
            'Load your data here and assign the results to the CollectionViewSource.  
            myCollectionViewSource =   DirectCast(Me.Resources("announcementsViewSource"), System.Windows.Data.CollectionViewSource)  
            announcements.LoadCompleted += New EventHandler(Of LoadCompletedEventArgs)(AddressOf announcements_LoadCompleted)  
            announcements.LoadAsync(context.Announcements)  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private void UserControl_Loaded_1(object sender, RoutedEventArgs e)  
    {  
        // The URL for the OData service.  
        // Replace <server name> in the next line with the name of your   
        // SharePoint server.  
        context = new TeamSiteDataContext(new Uri("http://ServerName>/_vti_bin/ListData.svc"));  
  
        // Do not load your data at design time.  
        if (!System.ComponentModel.DesignerProperties.GetIsInDesignMode(this))  
        {  
            //Load your data here and assign the results to the CollectionViewSource.  
            myCollectionViewSource = (System.Windows.Data.CollectionViewSource)this.Resources["announcementsViewSource"];  
            announcements.LoadCompleted += new EventHandler<LoadCompletedEventArgs>(announcements_LoadCompleted);  
            announcements.LoadAsync(context.Announcements);  
        }  
    }  
    ```  
     Assicurarsi di sostituire il *ServerName* segnaposto con il nome del server che è in esecuzione SharePoint.  
  
12. Aggiungere la seguente procedura di gestione degli errori.  
  
    ```vb  
    Private Sub announcements_LoadCompleted(sender As Object, e As LoadCompletedEventArgs)  
        ' Handle any errors.  
        If e.[Error] Is Nothing Then  
            myCollectionViewSource.Source = announcements  
        Else  
            MessageBox.Show(String.Format("ERROR: {0}", e.[Error].Message))  
        End If  
    End Sub  
  
    ```  
  
    ```csharp  
    void announcements_LoadCompleted(object sender, LoadCompletedEventArgs e)  
    {  
        // Handle any errors.  
        if (e.Error == null)  
        {  
            myCollectionViewSource.Source = announcements;  
        }  
        else  
        {  
            MessageBox.Show(string.Format("ERROR: {0}", e.Error.Message));  
        }  
    }  
    ```  
       
## <a name="modifying-the-silverlight-web-part"></a>Modifica la Web Part Silverlight  
 Modificare una proprietà il progetto di web part Silverlight per abilitare il debug di Silverlight.  
  
#### <a name="to-modify-the-silverlight-web-part"></a>Per modificare la web part Silverlight  
  
1.  Aprire il menu di scelta rapida per il progetto di web part Silverlight (**SLWebPartTest**), quindi scegliere **proprietà**.  
  
2.  Nel **proprietà** finestra, scegliere il **SharePoint** scheda.  
  
3.  Se non è già selezionata, selezionare il **bilita debug Silverlight (anziché il debug degli Script)** casella di controllo.  
  
4.  Salvare il progetto.  
  
##  <a name="testing-the-silverlight-web-part"></a>La Web Part Silverlight di test  
 Testare le web part Silverlight di nuovo in SharePoint per garantire che vengano visualizzati correttamente i dati elenco SharePoint.  
  
#### <a name="to-test-the-silverlight-web-part"></a>Per testare la web part Silverlight  
  
1.  Premere il tasto F5 per compilare ed eseguire la soluzione di SharePoint.  
  
2.  In SharePoint, nel **Azioni sito** menu, scegliere **nuova pagina**.  
  
3.  Nel **nuova pagina** finestra di dialogo immettere un titolo, ad esempio **SL Web Part Test**, quindi scegliere il **crea** pulsante.  
  
4.  Nella finestra di progettazione di pagina, nel **gli strumenti di modifica** scegliere **inserire**.  
  
5.  Nell'elenco di scheda, scegliere **Web Part**.  
  
6.  Nel **categorie** scegliere il **personalizzato** cartella.  
  
7.  Nel **Web part** elenco, scegliere la web part Silverlight e quindi scegliere il **Aggiungi** pulsante per aggiungere la web part nella finestra di progettazione.  
  
8.  Dopo tutte le aggiunte apportate alla pagina web che si desidera, scegliere il **pagina** scheda e quindi scegliere il **Salva e Chiudi** pulsante sulla barra degli strumenti.  
  
     La web part Silverlight deve ora visualizzare dati di annuncio del sito di SharePoint. Per impostazione predefinita, la pagina viene archiviata nell'elenco delle pagine del sito di SharePoint.  
  
    > [!NOTE]  
    >  Quando si accede ai dati in Silverlight tra domini, Silverlight protegge le vulnerabilità di sicurezza che possono essere utilizzate per sfruttare le applicazioni web. Se si verificano problemi quando si accede a dati remoti in Silverlight, vedere [effettua un servizio disponibile tra confini di domini](http://go.microsoft.com/fwlink/?LinkId=223276).  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di Web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Distribuzione, pubblicazione e aggiornamento dei pacchetti delle soluzioni SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)  
  
  
