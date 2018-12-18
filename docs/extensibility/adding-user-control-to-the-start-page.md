---
title: Aggiunta di controllo utente alla pagina iniziale | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- start page dll
- custom start page
- start page assembly
ms.assetid: 5b7997db-af6f-4fa9-a128-bceb42bddaf1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2bec2b4ab834eb55bd34a80f9e6a30931e3cd325
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="adding-user-control-to-the-start-page"></a>Aggiunta di controllo utente alla pagina iniziale
Questa procedura dettagliata viene illustrato come aggiungere un riferimento DLL a una pagina iniziale personalizzata. L'esempio aggiunge un controllo utente alla soluzione, compila il controllo utente e quindi si fa riferimento l'assembly compilato dal file con estensione XAML pagina iniziale. Una nuova scheda ospita il controllo utente, che funziona come un Web browser di base.  
  
 È possibile utilizzare lo stesso processo per aggiungere un assembly che può essere chiamato da un file con estensione XAML.  
  
## <a name="adding-a-wpf-user-control-to-the-solution"></a>Aggiunta di un controllo utente WPF alla soluzione  
 Aggiungere innanzitutto un controllo utente Windows Presentation Foundation (WPF) per la soluzione di pagina iniziale.  
  
1.  Creare una pagina iniziale utilizzando creata in [la creazione di una pagina iniziale personalizzata](../extensibility/creating-a-custom-start-page.md).  
  
2.  In **Esplora**destro la soluzione, fare clic su **Aggiungi**, quindi fare clic su **nuovo progetto**.  
  
3.  Nel riquadro sinistro della finestra di **nuovo progetto** finestra di dialogo espandere il il **Visual Basic** o **Visual c#** nodo e fare clic su **Windows**. Nel riquadro centrale, selezionare **libreria di controlli utente WPF**.  
  
4.  Denominare il controllo `WebUserControl` e quindi fare clic su **OK**.  
  
## <a name="implementing-the-user-control"></a>Implementazione del controllo utente  
 Per implementare un controllo utente WPF, compilare l'interfaccia utente (UI) in XAML e quindi scrivere gli eventi code-behind in c# o un altro linguaggio .NET.  
  
#### <a name="to-write-the-xaml-for-the-user-control"></a>Per scrivere il codice XAML per il controllo utente  
  
1.  Aprire il file XAML per il controllo utente. Nel \<griglia > elemento, aggiungere le seguenti definizioni di riga al controllo.  
  
    ```vb  
    <Grid.RowDefinitions>  
        <RowDefinition Height="Auto"/>  
        <RowDefinition Height="*" />  
    </Grid.RowDefinitions>  
  
    ```  
  
2.  Nella finestra principale `Grid` elemento, aggiungere il seguente nuovo `Grid` elemento che contiene una casella di testo per digitare gli indirizzi Web e un pulsante per impostare il nuovo indirizzo.  
  
    ```xml  
    <Grid Grid.Row="0">  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition Width="*" />  
            <ColumnDefinition Width="Auto" />  
        </Grid.ColumnDefinitions>  
        <TextBox x:Name="UserSource" Grid.Column="0" />  
        <Button Grid.Column="1" x:Name="SetButton" Content="Set Address" Click="SetButton_Click" />  
    </Grid>  
    ```  
  
3.  Aggiungere il seguente frame di primo livello `Grid` elemento subito dopo il `Grid` elemento che contiene il pulsante e casella di testo.  
  
    ```vb  
    <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />  
    ```  
  
4.  Nell'esempio seguente viene illustrato il codice XAML completo per il controllo utente.  
  
    ```xml  
    <UserControl x:Class="WebUserControl.UserControl1"  
                 xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
                 xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
                 xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"   
                 xmlns:d="http://schemas.microsoft.com/expression/blend/2008"   
                 mc:Ignorable="d"   
                 d:DesignHeight="300" d:DesignWidth="300">  
        <Grid>  
            <Grid.RowDefinitions>  
                <RowDefinition Height="Auto"/>  
                <RowDefinition Height="*" />  
            </Grid.RowDefinitions>  
            <Grid Grid.Row="0">  
                <Grid.ColumnDefinitions>  
                    <ColumnDefinition Width="*" />  
                    <ColumnDefinition Width="Auto" />  
                </Grid.ColumnDefinitions>  
                <TextBox x:Name="UserSource" Grid.Column="0" />  
                <Button Grid.Column="1" x:Name="SetButton" Content="Set Address" Click="SetButton_Click" />  
            </Grid>  
            <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />  
        </Grid>  
    </UserControl>  
  
    ```  
  
#### <a name="to-write-the-code-behind-events-for-the-user-control"></a>Per scrivere gli eventi di code-behind per il controllo utente  
  
1.  Nella finestra di progettazione XAML, fare doppio clic su di **Set Address** pulsante aggiunto al controllo.  
  
     Il file UserControl1.cs verrà aperto nell'editor di codice.  
  
2.  Compilare il gestore dell'evento SetButton_Click come indicato di seguito.  
  
    ```csharp  
    private void SetButton_Click(object sender, RoutedEventArgs e)  
    {  
        try  
        {  
            this.WebFrame.Source = new Uri(this.UserSource.Text, UriKind.Absolute);  
        }  
        catch (Exception error)  
        {  
            MessageBox.Show(error.Message);  
        }  
    }  
    ```  
  
     Questo codice imposta l'indirizzo Web che viene digitato nella casella di testo come destinazione per il Web browser. Se l'indirizzo non è valido, il codice genera un errore.  
  
3.  Inoltre, è necessario gestire l'evento WebFrame_Navigated:  
  
    ```csharp  
    private void WebFrame_Navigated(object sender, EventArgs e)  
    { }  
    ```  
  
4.  Compilare la soluzione.  
  
## <a name="adding-the-user-control-to-the-start-page"></a>Aggiunta del controllo utente alla pagina iniziale  
 Per rendere disponibili per il progetto di pagina iniziale, questo controllo nel file di progetto di pagina iniziale, aggiungere un riferimento alla nuova libreria di controllo. È quindi possibile aggiungere il controllo al markup XAML di pagine iniziali.  
  
1.  In **Esplora**, nel progetto di pagina iniziale, fare doppio clic su **riferimenti** e quindi fare clic su **Aggiungi riferimento**.  
  
2.  Nel **progetti** , selezionare **WebUserControl** e quindi fare clic su **OK**.  
  
3.  Scegliere **Compila soluzione** dal menu **Compila**.  
  
     Compilare la soluzione rende il controllo utente disponibili in IntelliSense per gli altri file della soluzione.  
  
 Per aggiungere il controllo al markup XAML di pagine iniziali, aggiungere un riferimento all'assembly dello spazio dei nomi, quindi inserire il controllo nella pagina.  
  
#### <a name="to-add-the-control-to-the-markup"></a>Per aggiungere il controllo al markup  
  
1.  In **Esplora**, aprire il file con estensione XAML della pagina iniziale.  
  
2.  Nel **XAML** riquadro, aggiungere la seguente dichiarazione dello spazio dei nomi di primo livello <xref:System.Windows.Controls.Grid> elemento.  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3.  Nel **XAML** riquadro, scorrere verso il \<griglia > sezione.  
  
     La sezione contiene un <xref:System.Windows.Controls.TabControl> elemento in un <xref:System.Windows.Controls.Grid> elemento.  
  
4.  Aggiungere un \<TabControl > elemento contenente un \<TabItem > che contiene un riferimento al controllo utente.  
  
    ```xml  
  
    <TabItem Header="Web" Height="Auto">  
        <vsc:UserControl1 />  
    </TabItem>  
  
    ```  
  
 È ora possibile testare il controllo.  
  
## <a name="testing-a-manually-created-custom-start-page"></a>Test di una pagina di avvio personalizzati creati manualmente  
  
1.  Copiare il file XAML e qualsiasi file di testo o markup supporto file, al **%USERPROFILE%\My Documents\Visual Studio 2015\StartPages\\**  cartella.  
  
2.  Se la pagina iniziale fa riferimento a tutti i controlli o i tipi negli assembly che non sono installati da Visual Studio, copiare gli assembly e quindi incollarli in * cartella di installazione Visual Studio ***\Common7\IDE\PrivateAssemblies.\\** .  
  
3.  Al prompt dei comandi di Visual Studio digitare **devenv /rootsuffix Exp** per aprire un'istanza sperimentale di Visual Studio.  
  
4.  Nell'istanza sperimentale, passare al **Strumenti / opzioni / ambiente / avvio** pagina e selezionare il file XAML dal **Personalizza pagina iniziale** elenco a discesa.  
  
5.  Scegliere **Pagina iniziale** dal menu **Visualizza**.  
  
     La pagina iniziale personalizzata deve essere visualizzata. Se si desidera modificare i file, è necessario chiudere l'istanza sperimentale, apportare le modifiche, copiare e incollare i file modificati e quindi aprire nuovamente l'istanza sperimentale per visualizzare le modifiche.  
  
## <a name="see-also"></a>Vedere anche  
 [Controlli contenitore WPF](http://msdn.microsoft.com/en-us/a0177167-d7db-4205-9607-8ae316952566)   
 [Procedura dettagliata: Aggiunta di codice XAML personalizzato nella pagina iniziale](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)