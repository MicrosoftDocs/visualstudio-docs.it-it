---
title: Aggiunta di comandi di Visual Studio a una pagina iniziale | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: efb332de822bd86cc95c4786dbca3472fd0984cc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="adding-visual-studio-commands-to-a-start-page"></a>Aggiunta di comandi di Visual Studio a una pagina iniziale
Quando si crea una pagina iniziale personalizzata, è possibile aggiungervi comandi di Visual Studio. Questo documento vengono illustrate le diverse modalità di associazione di comandi di Visual Studio a oggetti XAML in una pagina di avvio.  
  
 Per ulteriori informazioni sui comandi in XAML, vedere [panoramica dei comandi](/dotnet/framework/wpf/advanced/commanding-overview)  
  
## <a name="adding-commands-from-the-command-well"></a>Aggiunta di comandi anche dal comando  
 La pagina iniziale creato in [la creazione di una pagina iniziale personalizzata](../extensibility/creating-a-custom-start-page.md) aggiunto il <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName> e <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> spazi dei nomi, come indicato di seguito.  
  
```  
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
```  
  
 Aggiungere un altro spazio dei nomi per Microsoft.VisualStudio.Shell dall'assembly Microsoft.VisualStudio.Shell.Immutable.11.0.dll. (Potrebbe essere necessario aggiungere un riferimento all'assembly nel progetto)  
  
```xml  
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"  
```  
  
 È possibile utilizzare il `vscom:` alias per associare i comandi di Visual Studio a XAML controlli nella pagina impostando la <xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A> proprietà del controllo da `vscom:VSCommands.ExecuteCommand`. È quindi possibile impostare il <xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A> proprietà sul nome del comando da eseguire, come illustrato nell'esempio seguente.  
  
```xml  
<Button Name="btnNewProj" Content="New Project"   
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
    CommandParameter="File.NewProject" >  
</Button>  
```  
  
> [!NOTE]
>  Il `x:` alias, che fa riferimento allo schema XAML, è necessario all'inizio di tutti i comandi.  
  
 È possibile impostare il valore di `Command` proprietà per tutti i comandi che è possibile accedere dal **comando** finestra. Per un elenco di comandi disponibili, vedere [alias di comandi di Visual Studio](../ide/reference/visual-studio-command-aliases.md).  
  
 Se il comando per aggiungere richiede un parametro aggiuntivo, è possibile aggiungere il valore di `CommandParameter` proprietà. Parametri separati da comandi tramite spazi, come illustrato nell'esempio seguente.  
  
```xml  
<Button Content="Web Search"   
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
        CommandParameter="View.WebBrowser www.bing.com" />  
```  
  
### <a name="calling-extensions-from-the-command-well"></a>La chiamata di estensioni dal comando anche  
 È possibile chiamare i comandi da pacchetti VSPackage registrati con la stessa sintassi utilizzata per chiamare altri comandi di Visual Studio. Se, ad esempio, un VSPackage installato aggiunge un **Home Page** comando per il **vista** menu, è possibile chiamare tale comando impostando `CommandParameter` a `View.HomePage`.  
  
> [!NOTE]
>  Se si chiama un comando che è associato a un pacchetto VSPackage, è necessario caricare il pacchetto quando viene richiamato il comando.  
  
## <a name="adding-commands-from-assemblies"></a>Aggiunta di comandi dagli assembly  
 Per chiamare un comando da un assembly o accedere al codice in un VSPackage che non è associato a un comando di menu, è necessario creare un alias per l'assembly e quindi chiamare l'alias.  
  
#### <a name="to-call-a-command-from-an-assembly"></a>Per chiamare un comando da un assembly  
  
1.  Nella soluzione, aggiungere un riferimento all'assembly.  
  
2.  Nella parte superiore del file StartPage, aggiungere una direttiva dello spazio dei nomi per l'assembly, come illustrato nell'esempio seguente.  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3.  Richiamare il comando impostando il `Command` proprietà di un oggetto XAML, come illustrato nell'esempio seguente.  
  
     XAML  
  
    ```  
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>  
    ```  
  
> [!NOTE]
>  È necessario copiare l'assembly e quindi incollarlo in... \\ *Cartella di installazione di visual Studio*\common7\ide\privateassemblies\. per assicurarsi che sia stata caricata prima che venga chiamato.  
  
## <a name="adding-commands-with-the-dte-object"></a>Aggiunta di comandi con l'oggetto DTE  
 È possibile accedere all'oggetto DTE da una pagina iniziale nel markup e nel codice.  
  
 Nel codice, è possibile accedervi tramite la [estensione di Markup Binding](/dotnet/framework/wpf/advanced/binding-markup-extension) sintassi per chiamare il <xref:EnvDTE.DTE> oggetto. È possibile utilizzare questo approccio per associare le proprietà semplici, ad esempio quelli che restituiscono raccolte, ma non è possibile associare ai metodi o servizi. Nell'esempio seguente un <xref:System.Windows.Controls.TextBlock> controllo associato al <xref:EnvDTE._DTE.Name%2A> proprietà e un <xref:System.Windows.Controls.ListBox> controllo che enumera il <xref:EnvDTE.Window.Caption%2A> le proprietà della raccolta restituita dal <xref:EnvDTE._DTE.Windows%2A> proprietà.  
  
```xml  
<TextBlock Text="{Binding Path=DTE.Name}" FontSize="12" HorizontalAlignment="Center"/>  
<ListBox ItemsSource="{Binding Path=DTE.Windows}">  
    <ListBox.ItemTemplate>  
        <DataTemplate>  
            <TextBlock Text="{Binding Path=Caption}"/>  
        </DataTemplate>  
    </ListBox.ItemTemplate>  
</ListBox  
```  
  
 Per un esempio, vedere [procedura dettagliata: salvataggio delle impostazioni utente in una pagina iniziale](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiunta di un controllo utente nella pagina iniziale](../extensibility/adding-user-control-to-the-start-page.md)