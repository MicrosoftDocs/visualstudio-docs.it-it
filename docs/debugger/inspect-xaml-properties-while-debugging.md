---
title: "Analizzare le proprietà XAML durante il debug | Documenti Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 390edde4-7b8d-4c89-8d69-55106b7e6b11
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: 40ff41cc6728244d11e93541057af1cb525c7af3
ms.sourcegitcommit: 5d43e9590e2246084670b79269cc9d99124bb3df
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2018
---
# <a name="inspect-xaml-properties-while-debugging"></a>Analizzare le proprietà XAML durante il debug
È possibile ottenere una visualizzazione in tempo reale sul codice XAML in esecuzione con il **albero elementi visivi attivi** e **Esplora proprietà attive**. Questi strumenti offrono una visualizzazione albero degli elementi dell'interfaccia utente dell'applicazione XAML in esecuzione e mostrano le proprietà di runtime di qualsiasi elemento dell'interfaccia utente selezionato.  
  
 È possibile usare questi strumenti nelle configurazioni seguenti:  
  
|Tipo di app|Sistema operativo e strumenti|  
|-----------------|--------------------------------|  
|Applicazioni Windows Presentation Foundation (4.0 e versioni successive)|Windows 7 e versioni successive|  
|App di Windows universale|Windows 10 e versioni successive, con la [Windows 10 SDK](https://dev.windows.com/en-us/downloads/windows-10-sdk)|  
  
## <a name="looking-at-elements-in-the-live-visual-tree"></a>Visualizzazione degli elementi nella finestra Struttura ad albero visuale attiva  
 È possibile iniziare subito con un'applicazione WPF molto semplice con una visualizzazione elenco e un pulsante. Ogni volta che si fa clic sul pulsante, viene aggiunto un altro elemento all'elenco. Gli elementi pari sono di colore grigio e quelli dispari sono gialli.  
  
 Creare una nuova applicazione WPF in c# (File > Nuovo > progetto, quindi selezionare c# e trova applicazione WPF). Il nome **TestXAML**.  
  
 Modificare MainWindow.xaml come segue:  
  
```xaml  
<Window x:Class="TestXAML.MainWindow"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
    xmlns:local="clr-namespace:TestXAML"  
    mc:Ignorable="d"  
     Title="MainWindow" Height="350" Width="525">  
    <Grid>  
        <Button x:Name="button" Background="LightBlue" Content="Add Item" HorizontalAlignment="Left" Margin="216,206,0,0" VerticalAlignment="Top" Width="75" Click="button_Click"/>  
        <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="100" VerticalAlignment="Top" Width="100" Margin="205,80,0,0"/>  
    </Grid>  
</Window>  
```  
  
 Aggiungere il gestore del comando seguente al file MainWindow.xaml.cs:  
  
```csharp 
int count;

private void button_Click(object sender, RoutedEventArgs e)  
{  
    ListBoxItem item = new ListBoxItem();  
    item.Content = "Item" + ++count;  
    if (count % 2 == 0)  
    {  
        item.Background = Brushes.LightGray;  
    }  
    else  
    {  
        item.Background = Brushes.LightYellow;  
    }  
    listBox.Items.Add(item);  
}  
```  
  
 Compilare il progetto e avviare il debug. La build deve essere configurata per il debug, non per il rilascio. Per ulteriori informazioni sulle configurazioni della build, vedere [informazioni sulle configurazioni della Build](../ide/understanding-build-configurations.md).)  
  
 Quando la finestra viene visualizzata, fare clic su di **Aggiungi elemento** pulsante un paio di volte. Viene visualizzato un output simile al seguente:  
  
 ![Finestra principale dell'app](../debugger/media/livevisualtree-app.png "LiveVIsualTree-App")  
  
 Aprire quindi il **albero elementi visivi attivi** finestra (**Debug > Windows > albero elementi visivi attivi**, o si trova lungo il lato sinistro dell'IDE). Trascinare la posizione di ancoraggio in modo è possibile esaminare in questa finestra e **Live proprietà** finestra side-by. Nel **albero elementi visivi attivi** finestra, espandere il **ContentPresenter** nodo. Tale nodo dovrebbe contenere i nodi per il pulsante e la casella di riepilogo. Espandere la casella di riepilogo (e quindi la **ScrollContentPresenter** e **ItemsPresenter**) per individuare i relativi elementi. La finestra dovrebbe essere simile alla seguente:  
  
 ![La struttura ad albero visuale in tempo reale ListBoxItem](../debugger/media/livevisualtree-listboxitems.png "LiveVisualTree ListBoxItem")  
  
 Tornare alla finestra dell'applicazione e aggiungere altri elementi. Dovrebbero venire visualizzati altri elementi casella di riepilogo nel **albero elementi visivi attivi**.  
  
 Ora esaminiamo le proprietà di uno degli elementi casella di riepilogo. Selezionare il primo elemento della casella di riepilogo nel **albero elementi visivi attivi** e fare clic su di **Mostra proprietà** icona sulla barra degli strumenti. Il **Esplora proprietà attive** dovrebbe essere visualizzato. Si noti che il **contenuto** campo è "Item1" e **Background** campo **#FFFFFFE0** (giallo chiaro). Tornare al **albero elementi visivi attivi** e selezionare il secondo elemento casella di riepilogo. Il **Esplora proprietà attive** viene mostrato che il **contenuto** campo è "Item2" e il **sfondo** campo **#FFD3D3D3** (grigio chiaro ).  
  
 La struttura effettiva del codice XAML include numerosi elementi a cui probabilmente non si è direttamente interessati e se non si conosce bene il codice potrebbe essere difficoltà a esplorare l'albero per trovare ciò che sta cercando. Pertanto la **albero elementi visivi attivi** ha un paio di modi che consentono di utilizzare dell'interfaccia utente dell'applicazione che consentono di trovare l'elemento che si desidera esaminare.  
  
 **Abilita la selezione nell'applicazione in esecuzione**. È possibile abilitare questa modalità quando si seleziona il pulsante all'estrema sinistra nel **albero elementi visivi attivi** barra degli strumenti. Con questa modalità è attivata, è possibile selezionare un elemento dell'interfaccia utente dell'applicazione e **albero elementi visivi attivi** (e **visualizzatore delle proprietà attive**) si aggiorni automaticamente per mostrare il nodo nell'albero corrispondente a tale elemento, e le relative proprietà.  
  
 **Visualizza gli Adorner layout nell'applicazione in esecuzione**. È possibile abilitare questa modalità quando si seleziona il pulsante immediatamente a destra del pulsante di abilitazione della selezione. Quando **Visualizza gli Adorner layout** è abilitato, fa sì che la finestra dell'applicazione visualizzare linee orizzontali e verticali lungo i bordi dell'oggetto selezionato in modo da visualizzare vederne l'allineamento, nonché rettangoli che mostrano i margini. Ad esempio, attivare entrambe le opzioni **Abilita selezione** e **Visualizza gli Adorner layout** e selezionare il **Aggiungi elemento** blocco di testo nell'applicazione. Verrà visualizzato il nodo del blocco di testo nel **albero elementi visivi attivi** e proprietà del blocco di testo **visualizzatore delle proprietà attive**, nonché le linee orizzontali e verticali lungo i bordi del blocco di testo.  
  
 ![LivePropertyViewer in DisplayLayout](../debugger/media/livevisualtreelivepropertyviewer-displaylayout.png "LiveVisualTreeLivePropertyViewer DisplayLayout")  
  
 **Anteprima selezione**. È possibile abilitare questa modalità selezionando il terzo pulsante da sinistra sulla barra degli strumenti nella finestra Struttura ad albero visuale attiva. Questa modalità mostra il codice XAML in cui è stato dichiarato l'elemento, se si ha accesso al codice sorgente dell'applicazione. Selezionare **Abilita selezione** e **anteprima selezione**, e quindi selezionare il pulsante nell'applicazione di test. Il file MainWindow.xaml verrà aperto in Visual Studio e il cursore verrà posizionato sulla riga in cui è definito il pulsante.  
  
## <a name="using-xaml-tools-with-running-applications"></a>Uso di strumenti XAML con applicazioni in esecuzione  
 È possibile utilizzare questi strumenti XAML anche quando non si dispone del codice sorgente. Quando si collega a un'applicazione XAML in esecuzione, è possibile utilizzare il **albero elementi visivi attivi** sugli elementi dell'interfaccia utente di tale applicazione troppo. Di seguito è riportato un esempio, utilizzando la stessa applicazione di test WPF usata in precedenza.  
  
1.  Avviare il **TestXaml** applicazione nella configurazione di rilascio. Non è possibile collegare a un processo in esecuzione in un **Debug** configurazione.  
  
2.  Aprire una seconda istanza di Visual Studio e fare clic su **Debug > Connetti a processo**. Trovare **TestXaml.exe** nell'elenco dei processi disponibili, fare clic su **collegamento**.  
  
3.  Viene avviata l'esecuzione dell'applicazione.  
  
4.  Nella seconda istanza di Visual Studio, aprire il **albero elementi visivi attivi** (**Debug > Windows > albero elementi visivi attivi**). Verrà visualizzato il **TestXaml** elementi dell'interfaccia utente e si dovrebbe essere possibile modificarli come durante il debug dell'applicazione direttamente.