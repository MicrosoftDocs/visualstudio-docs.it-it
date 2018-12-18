---
title: 'Procedura dettagliata: Salvataggio delle impostazioni utente in una pagina di avvio | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8ea4d4a07ed9f61f20ca2b3f79b99d3a2ebfa0b3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-saving-user-settings-on-a-start-page"></a>Procedura dettagliata: Salvataggio delle impostazioni utente in una pagina iniziale
È possibile mantenere le impostazioni utente per la pagina iniziale. Seguendo questa procedura dettagliata, è possibile creare un controllo per salvare un'impostazione nel Registro di sistema quando l'utente fa clic su un pulsante e recupera quindi che l'impostazione di ogni volta che viene caricata la pagina iniziale. Poiché il modello di progetto di pagina iniziale include un controllo utente personalizzabile e il valore predefinito, avviare XAML della pagina chiama tale controllo, non è necessario modificare la pagina iniziale se stesso.  
  
 L'archivio di impostazioni che viene creata un'istanza di questa procedura dettagliata è un'istanza di <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore> interfaccia che legge e scrive il percorso del Registro di sistema seguente quando viene chiamato: HKCU\Software\Microsoft\VisualStudio\14.0\\  *CollectionName*  
  
 Quando è in esecuzione nell'istanza sperimentale di Visual Studio, l'archivio impostazioni letture e scritture HKCU\Software\Microsoft\VisualStudio\14.0Exp\\*CollectionName.*  
  
 Per ulteriori informazioni su come rendere persistenti le impostazioni, vedere [opzioni e impostazioni utente di estensione](../extensibility/extending-user-settings-and-options.md).  
  
## <a name="prerequisites"></a>Prerequisiti  
  
> [!NOTE]
>  Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per ulteriori informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
>   
>  È possibile scaricare il modello di progetto di pagina iniziale utilizzando **Extension Manager**.  
  
## <a name="setting-up-the-project"></a>Impostazione del progetto  
  
#### <a name="to-configure-the-project-for-this-walkthrough"></a>Per configurare il progetto per questa procedura dettagliata  
  
1.  Creare un progetto di pagina iniziale come descritto in [la creazione di una pagina iniziale personalizzata](creating-a-custom-start-page.md). Denominare il progetto **SaveMySettings**.  
  
2.  In **Esplora**, aggiungere i seguenti riferimenti di assembly al progetto StartPageControl:  
  
    -   EnvDTE  
  
    -   EnvDTE80  
  
    -   Interop  
  
    -   Microsoft.VisualStudio.Shell.Interop.11.0  
  
3.  Aprire MyControl.xaml.  
  
4.  Dal riquadro XAML, di primo livello <xref:System.Windows.Controls.UserControl> definizione dell'elemento, aggiungere la seguente dichiarazione di evento dopo le dichiarazioni dello spazio dei nomi.  
  
    ```  
    Loaded="OnLoaded"  
    ```  
  
5.  Nel riquadro di progettazione, fare clic sull'area principale del controllo e quindi premere CANC.  
  
     Questa operazione rimuove il <xref:System.Windows.Controls.Border> elemento e tutti gli elementi e lascia solo il primo livello <xref:System.Windows.Controls.Grid> elemento.  
  
6.  Dal **della casella degli strumenti**, trascinare un <xref:System.Windows.Controls.StackPanel> controllo alla griglia.  
  
7.  Trascinare ora un <xref:System.Windows.Controls.TextBlock>, <xref:System.Windows.Controls.TextBox>e un pulsante per la <xref:System.Windows.Controls.StackPanel>.  
  
8.  Aggiungere un **X:Name** attributo per il <xref:System.Windows.Controls.TextBox>e un `Click` evento per il <xref:System.Windows.Controls.Button>, come illustrato nell'esempio seguente.  
  
    ```xml  
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">  
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>  
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />  
        <Button Click="Button_Click" Width="100">Save My Setting</Button>  
    </StackPanel>  
    ```  
  
## <a name="implementing-the-user-control"></a>Implementazione del controllo utente  
  
#### <a name="to-implement-the-user-control"></a>Per implementare il controllo utente  
  
1.  Nel riquadro di XAML, fare doppio clic su di `Click` attributo del <xref:System.Windows.Controls.Button> elemento e quindi fare clic su **passa al gestore eventi**.  
  
     Questo consente di aprire MyControl.xaml.cs e crea un gestore di stub per il `Button_Click` evento.  
  
2.  Aggiungere il seguente `using` istruzioni all'inizio del file.  
  
     [!code-csharp[StartPageDTE#11](../extensibility/codesnippet/CSharp/walkthrough-saving-user-settings-on-a-start-page_1.cs)]  
  
3.  Aggiungere una privata `SettingsStore` proprietà, come illustrato nell'esempio seguente.  
  
    ```csharp  
    private IVsWritableSettingsStore _settingsStore = null;  
    private IVsWritableSettingsStore SettingsStore  
    {  
        get  
        {  
            if (_settingsStore == null)  
            {  
                // Get a reference to the DTE from the DataContext.   
                var typeDescriptor = DataContext as ICustomTypeDescriptor;  
                var propertyCollection = typeDescriptor.GetProperties();  
                var dte = propertyCollection.Find("DTE", false).GetValue(  
                    DataContext) as DTE2;  
  
                // Get the settings manager from the DTE.   
                var serviceProvider = new ServiceProvider(  
                    (Microsoft.VisualStudio.OLE.Interop.IServiceProvider)dte);  
                var settingsManager = serviceProvider.GetService(  
                    typeof(SVsSettingsManager)) as IVsSettingsManager;  
  
                // Write the user settings to _settingsStore.  
                settingsManager.GetWritableSettingsStore(  
                    (uint)__VsSettingsScope.SettingsScope_UserSettings,  
                    out _settingsStore);  
            }  
            return _settingsStore;  
        }  
    }  
    ```  
  
     Questa proprietà ottiene innanzitutto un riferimento al <xref:EnvDTE80.DTE2> interfaccia, che contiene il modello oggetto di automazione, a partire dal <xref:System.Windows.FrameworkElement.DataContext%2A> del controllo utente e quindi utilizza l'oggetto DTE per ottenere un'istanza del <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> interfaccia. Tale istanza viene quindi utilizzata per restituire le impostazioni utente correnti.  
  
4.  Compilare il `Button_Click` evento come indicato di seguito.  
  
    ```csharp  
    private void Button_Click(object sender, RoutedEventArgs e)  
    {  
        int exists = 0;  
        SettingsStore.CollectionExists("MySettings", out exists);  
        if (exists != 1)  
        {  
            SettingsStore.CreateCollection("MySettings");  
        }  
        SettingsStore.SetString("MySettings", "MySetting", txtblk.Text);  
    }  
    ```  
  
     Scrive il contenuto della casella di testo a un campo "MySetting" in una raccolta di "MySettings" nel Registro di sistema. Se la raccolta non esiste, viene creato.  
  
5.  Aggiungere il seguente gestore per il `OnLoaded` evento del controllo utente.  
  
    ```csharp  
    private void OnLoaded(Object sender, RoutedEventArgs e)  
    {  
        string value;  
        SettingsStore.GetStringOrDefault(  
            "MySettings", "MySetting", "", out value);  
        txtblk.Text = value;  
    }  
    ```  
  
     Questo imposta il testo della casella di testo per il valore corrente di "MySetting".  
  
6.  Compilare il controllo utente.  
  
7.  In **Esplora**, aprire vsixmanifest.  
  
8.  Nell'editor del manifesto, impostare **Product Name** a **Salva pagina di avvio impostazioni personali**.  
  
     Questo imposta il nome della pagina iniziale come verrà visualizzato nel **Personalizza pagina iniziale** nell'elenco di **opzioni** la finestra di dialogo.  
  
9. Compilare StartPage.  
  
## <a name="testing-the-control"></a>Test del controllo  
  
#### <a name="to-test-the-user-control"></a>Per testare il controllo utente  
  
1.  Premere F5.  
  
     Apre l'istanza sperimentale di Visual Studio.  
  
2.  Nell'istanza sperimentale, nel **strumenti** menu, fare clic su **opzioni**.  
  
3.  Nel **ambiente** nodo, fare clic su **avvio**, quindi il **Personalizza pagina iniziale** elenco, selezionare **[installato estensione] Salva My impostazioni pagina iniziale** .  
  
     Fare clic su **OK**.  
  
4.  Chiudere la pagina iniziale se è aperto, quindi scegliere il **vista** menu, fare clic su **pagina iniziale**.  
  
5.  Nella pagina iniziale, fare clic su di **MyControl** scheda.  
  
6.  Nella casella di testo, digitare **Cat**, quindi fare clic su **Salva My impostazione**.  
  
7.  Chiudere la pagina iniziale, quindi aprirlo nuovamente.  
  
     La parola "Cat" deve essere visualizzato nella casella di testo.  
  
8.  Sostituire la parola "Cat" con la parola "Dog". Non fare clic sul pulsante.  
  
9. Chiudere la pagina iniziale, quindi aprirlo nuovamente.  
  
     La parola "Dog" deve essere visualizzata nella casella di testo, anche se l'impostazione non è stato salvato. Ciò accade perché Visual Studio consente di mantenere le finestre degli strumenti in memoria, anche qualora siano chiusi, fino alla chiusura di Visual Studio.  
  
10. Chiudere l'istanza sperimentale di Visual Studio.  
  
11. Premere F5 per aprire nuovamente l'istanza sperimentale.  
  
12. La parola "Cat" deve essere visualizzato nella casella di testo.  
  
## <a name="next-steps"></a>Passaggi successivi  
 È possibile modificare il controllo utente per salvare e recuperare un numero qualsiasi di impostazioni personalizzate utilizzando valori diversi dai gestori eventi diversi per ottenere e impostare il `SettingsStore` proprietà. Come utilizzare un altro `propertyName` parametro per ogni chiamata a <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A>, i valori non comporta la sovrascrittura tra loro nel Registro di sistema.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:EnvDTE80.DTE2?displayProperty=fullName>     
 [Aggiunta di comandi di Visual Studio in una pagina iniziale](../extensibility/adding-visual-studio-commands-to-a-start-page.md)