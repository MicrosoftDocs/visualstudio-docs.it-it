---
title: Codice sorgente di L2DBForm.xaml | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 624e96d4-6d27-4195-8ac2-2f3835f6c57e
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b815904a7ac2b8a050cd4b907698c43a91d929dc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="l2dbformxaml-source-code"></a>Codice sorgente di L2DBForm.xaml
Questo argomento contiene e descrive il file di origine XAML per [Esempio di data binding WPF tramite LINQ to XML](../designers/wpf-data-binding-using-linq-to-xml-example.md), L2DBForm.xaml.  
  
## <a name="overall-ui-structure"></a>Struttura complessiva dell'interfaccia utente  
 Come è tipico per i progetti WPF, questo file contiene un elemento padre, ovvero un elemento XML <xref:System.Windows.Window> associato alla classe derivata `L2XDBFrom` nello spazio dei nomi `LinqToXmlDataBinding` .  
  
 L'area client è contenuta all'interno di un oggetto <xref:System.Windows.Controls.StackPanel> per cui viene specificato uno sfondo azzurro. Il pannello contiene quattro sezioni dell'interfaccia utente <xref:System.Windows.Controls.DockPanel> separate da barre <xref:System.Windows.Controls.Separator> . Lo scopo di queste sezioni è descritto nella sezione **Note** dell'argomento precedente, [.](../designers/walkthrough-linqtoxmldatabinding-example.md)  
  
 Ogni sezione contiene un'etichetta che la identifica. Nelle prime due sezioni questa etichetta viene ruotata di 90 gradi tramite l'uso di un oggetto <xref:System.Windows.FrameworkElement.LayoutTransform%2A>. Il resto della sezione contiene gli elementi dell'interfaccia utente appropriati per lo scopo: blocchi di testo, caselle di testo, pulsanti e così via. A volte viene usato un elemento figlio <xref:System.Windows.Controls.StackPanel> per allineare questi controlli figlio.  
  
## <a name="window-resource-section"></a>Sezione delle risorse della finestra  
 Il tag di apertura di `<Window.Resources>` alla riga 9 indica l'inizio della sezione relativa alle risorse della finestra, che termina con il tag di chiusura alla riga 35.  
  
 Il tag `<ObjectDataProvider>` , che si estende dalla riga 11 alla riga 25, dichiara un oggetto <xref:System.Windows.Data.ObjectDataProvider>, denominato `LoadedBooks`, che usa <xref:System.Xml.Linq.XElement> come origine. <xref:System.Xml.Linq.XElement> viene inizializzato tramite l'analisi di un documento XML incorporato (elemento `CDATA` ). Si noti che lo spazio vuoto viene conservato quando si dichiara il documento XML incorporato e anche quando lo si analizza, in quanto il controllo <xref:System.Windows.Controls.TextBlock> , usato per visualizzare l'XML non elaborato, non include funzionalità speciali di formattazione XML.  
  
 Infine, viene definito un oggetto <xref:System.Windows.DataTemplate> denominato `BookTemplate` dalla riga 28 alla riga 34. Questo modello verrà usato per visualizzare le voci nella sezione dell'interfaccia utente **Book List** . Vengono usate l'associazione dati e le proprietà dinamiche di LINQ to XML per recuperare l'ID e il nome libro tramite le seguenti assegnazioni:  
  
```  
Text="{Binding Path=Attribute[id].Value}"Text="{Binding Path=Value}"  
```  
  
## <a name="data-binding-code"></a>Codice di associazione dati  
 Oltre che nell'elemento <xref:System.Windows.DataTemplate> , l'associazione dati viene usata in diverse altre sezioni del file.  
  
 Nel tag di apertura di `<StackPanel>` , alla riga 38, la proprietà <xref:System.Windows.FrameworkElement.DataContext%2A> di questo pannello è impostata sul provider di dati `LoadedBooks` .  
  
```  
DataContext="{Binding Source={StaticResource LoadedBooks}}  
```  
  
 In questo modo l'oggetto <xref:System.Windows.Controls.TextBlock> denominato `tbRawXml` , alla riga 46, è in grado di visualizzare l'XML non elaborato tramite l'associazione alla proprietà `Xml` di questo provider di dati:  
  
```  
Text="{Binding Path=Xml}"   
```  
  
 L'oggetto <xref:System.Windows.Controls.ListBox> nella sezione dell'interfaccia utente **Book List** , dalla riga 58 alla riga 62, imposta il modello per i relativi elementi visualizzati sull'oggetto `BookTemplate` definito nella sezione delle risorse della finestra:  
  
```  
ItemTemplate ="{StaticResource BookTemplate}"   
```  
  
 Quindi, dalla riga 59 alla riga 62, i valori effettivi dei libri vengono associati a questa casella di riepilogo:  
  
```  
<ListBox.ItemsSource>  
    <Binding Path="Elements[{http://www.mybooks.com}book]"/>  
</ListBox.ItemsSource>  
```  
  
 La terza sezione dell'interfaccia utente, **Edit Selected Book**, associa l'oggetto <xref:System.Windows.FrameworkElement.DataContext%2A> dell'oggetto <xref:System.Windows.Controls.StackPanel> padre all'elemento attualmente selezionato della sezione dell'interfaccia utente **Book List** (riga 82):  
  
```  
DataContext="{Binding ElementName=lbBooks, Path=SelectedItem}"  
```  
  
 Usa quindi l'associazione dati bidirezionale, in modo che i valori correnti degli elementi libro vengano visualizzati e aggiornati dalle due caselle di testo di questo pannello. L'associazione dati a proprietà dinamiche è simile a quella usata nel modello di dati `BookTemplate` :  
  
```  
Text="{Binding Path=Attribute[id].Value}"...Text="{Binding Path=Value}"  
```  
  
 L'ultima sezione dell'interfaccia utente, **Add New Book**, non usa l'associazione dati nel codice XAML, ma tale codice è invece disponibile nel codice di gestione degli eventi nel file L2DBForm.xaml.cs.  
  
## <a name="example"></a>Esempio  
  
### <a name="description"></a>Descrizione  
  
> [!NOTE]
>  Si consiglia di copiare il codice seguente in un editor di codice, ad esempio l'editor di codice sorgente C# in Visual Studio, in modo che sia più facile tenere traccia dei numeri di riga.  
  
### <a name="code"></a>Codice  
  
```xml  
<Window x:Class="LinqToXmlDataBinding.L2XDBForm"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:system="clr-namespace:System;assembly=mscorlib"  
    xmlns:xlinq="clr-namespace:System.Xml.Linq;assembly=System.Xml.Linq"  
    xmlns:local="clr-namespace:LinqToXmlDataBinding"  
    Title="WPF Data Binding using LINQ-to-XML" Height="665" Width="500" ResizeMode="NoResize">  
  
    <Window.Resources>  
        <!-- Books provider and inline data -->  
        <ObjectDataProvider x:Key="LoadedBooks" ObjectType="{x:Type xlinq:XElement}" MethodName="Parse">  
            <ObjectDataProvider.MethodParameters>  
                <system:String xml:space="preserve">  
<![CDATA[  
<books xmlns="http://www.mybooks.com">  
  <book id="0">book zero</book>  
  <book id="1">book one</book>  
  <book id="2">book two</book>  
  <book id="3">book three</book>  
</books>  
]]>                  
                </system:String>  
                <xlinq:LoadOptions>PreserveWhitespace</xlinq:LoadOptions>  
            </ObjectDataProvider.MethodParameters>  
        </ObjectDataProvider>  
  
        <!-- Template for use in Books List listbox. -->  
        <DataTemplate x:Key="BookTemplate">  
            <StackPanel Orientation="Horizontal">  
                <TextBlock Margin="3" Text="{Binding Path=Attribute[id].Value}"/>  
                <TextBlock Margin="3" Text="-"/>  
                <TextBlock Margin="3" Text="{Binding Path=Value}"/>  
            </StackPanel>  
        </DataTemplate>  
    </Window.Resources>  
  
    <!-- Main visual content container -->  
    <StackPanel Background="lightblue" DataContext="{Binding Source={StaticResource LoadedBooks}}">  
        <!-- Raw XML display section -->  
        <DockPanel Margin="5">  
            <Label  Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" FontWeight="Bold">XML  
            <Label.LayoutTransform>  
                <RotateTransform Angle="90"/>  
            </Label.LayoutTransform>  
            </Label>  
            <TextBlock Name="tbRawXml" Height="200" Background="LightGray" Text="{Binding Path=Xml}" TextTrimming="CharacterEllipsis" />  
        </DockPanel>  
  
        <Separator Height="4" Margin="5" />  
  
        <!-- List box to display all books section -->  
        <DockPanel Margin="5">  
            <Label  Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" FontWeight="Bold">Book List  
                <Label.LayoutTransform>  
                    <RotateTransform Angle="90"/>  
                </Label.LayoutTransform>  
            </Label>  
            <ListBox Name="lbBooks" Height="200" Width="415" ItemTemplate ="{StaticResource BookTemplate}">  
                <ListBox.ItemsSource>  
                    <Binding Path="Elements[{http://www.mybooks.com}book]"/>  
                </ListBox.ItemsSource>  
            </ListBox>  
            <Button Margin="5" DockPanel.Dock="Right" Height="30" Width ="130" Content="Remove Selected Book" Click="OnRemoveBook">      
            <Button.LayoutTransform>  
                <RotateTransform Angle="90"/>  
            </Button.LayoutTransform>  
            </Button>  
        </DockPanel>  
  
        <Separator Height="4" Margin="5" />  
  
        <!-- Edit current selection section -->  
        <DockPanel Margin="5">  
            <TextBlock Margin="5" Height="30" Width="65" DockPanel.Dock="Right" Background="LightGray" TextWrapping="Wrap" TextAlignment="Center">  
                    Changes are live!  
                <TextBlock.LayoutTransform>  
                    <RotateTransform Angle="90"/>  
                </TextBlock.LayoutTransform>  
            </TextBlock>  
            <StackPanel>  
                <Label Width="450" Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" HorizontalAlignment="Left" FontWeight="Bold">Edit Selected Book</Label>      
                <StackPanel Margin="1" DataContext="{Binding ElementName=lbBooks, Path=SelectedItem}">  
                    <StackPanel Orientation="Horizontal">  
                        <Label Width="40">ID:</Label>  
                        <TextBox Name="editAttributeTextBox" Width="410" Text="{Binding Path=Attribute[id].Value}">  
                            <TextBox.ToolTip>  
                                <TextBlock FontWeight="Bold" TextAlignment="Center">  
                                    <Label>Edit the selected book ID and see it changed.</Label>  
                                </TextBlock>  
                            </TextBox.ToolTip>  
                        </TextBox>  
                    </StackPanel>  
                    <StackPanel Orientation="Horizontal">  
                        <Label Width="40">Value:</Label>  
                        <TextBox Name="editValueTextBox" Width="410" Text="{Binding Path=Value}" Height="25">  
                            <TextBox.ToolTip>  
                                <TextBlock FontWeight="Bold" TextAlignment="Center">  
                                    <Label>Edit the selected book Value and see it changed.</Label>  
                                </TextBlock>  
                            </TextBox.ToolTip>  
                        </TextBox>  
                    </StackPanel>  
                </StackPanel>  
            </StackPanel>  
        </DockPanel>  
  
        <Separator Height="4" Margin="5" />  
  
        <!-- Add new book section -->  
        <DockPanel Margin="5">  
            <Button Margin="5" Height="30" DockPanel.Dock="Right" Click ="OnAddBook">Add Book  
                <Button.LayoutTransform>  
                    <RotateTransform Angle="90"/>  
                </Button.LayoutTransform>  
            </Button>  
            <StackPanel>  
                <Label Width="450" Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" HorizontalAlignment="Left" FontWeight="Bold">Add New Book</Label>  
                <StackPanel Margin="1">  
                    <StackPanel Orientation="Horizontal">  
                        <Label Width="40">ID:</Label>  
                        <TextBox Name="tbAddID" Width="410">  
                            <TextBox.ToolTip>  
                                <TextBlock FontWeight="Bold" TextAlignment="Center">  
                                    <Label>Enter a book ID and Value pair, then click Add Book.</Label>  
                                </TextBlock>  
                            </TextBox.ToolTip>  
                        </TextBox>  
                    </StackPanel>  
                    <StackPanel Orientation="Horizontal">  
                        <Label Width="40">Value:</Label>  
                        <TextBox Name="tbAddValue" Width="410" Height="25">  
                            <TextBox.ToolTip>  
                                <TextBlock FontWeight="UltraBold" TextAlignment="Center">  
                                    <Label>Enter a book ID and Value pair, then click Add Book.</Label>  
                                </TextBlock>  
                            </TextBox.ToolTip>  
                        </TextBox>  
                    </StackPanel>  
                </StackPanel>  
            </StackPanel>  
        </DockPanel>  
    </StackPanel>  
</Window>  
  
```  
  
### <a name="comments"></a>Commenti  
 Per il codice sorgente C# relativo ai gestori eventi associati agli elementi dell'interfaccia utente WPF, vedere [Codice sorgente di L2DBForm.xaml.cs](../designers/l2dbform-xaml-cs-source-code.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Esempio LinqToXmlDataBinding](../designers/walkthrough-linqtoxmldatabinding-example.md)   
 [Codice sorgente di L2DBForm.xaml.cs](../designers/l2dbform-xaml-cs-source-code.md)