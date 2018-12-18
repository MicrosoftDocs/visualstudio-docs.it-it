---
title: Aggiornamento delle personalizzazioni della barra multifunzione nei progetti di Office migrati a .NET Framework 4 o .NET Framework 4.5 | Documenti Microsoft
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
helpviewer_keywords: Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 4d3c2e834b3a618bf033ef7f37ca8bbac7d0efcf
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Aggiornamento delle personalizzazioni della barra multifunzione nei progetti di Office di cui si esegue la migrazione a .NET Framework 4 o a .NET Framework 4.5
  Se il progetto contiene una personalizzazione della barra multifunzione che è stata creata utilizzando il **della barra multifunzione (finestra di progettazione visiva)** dell'elemento di progetto, è necessario apportare le modifiche seguenti al codice del progetto se il framework di destinazione viene modificato nel [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o in un secondo momento.  
  
-   Modificare il codice della barra multifunzione generato.  
  
-   Modificare qualsiasi codice che crea un'istanza dei controlli della barra multifunzione in fase di esecuzione, gestisce gli eventi della barra multifunzione o imposta la posizione di un componente della barra multifunzione a livello di programmazione.  
  
## <a name="updating-the-generated-ribbon-code"></a>Aggiornamento del codice della barra multifunzione generato  
 Se la versione di. il Framework di destinazione del progetto viene aggiornato a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive, è necessario modificare il codice generato per l'elemento barra multifunzione effettuando i passaggi seguenti. I file di codice che è necessario aggiornare dipendono dal linguaggio di programmazione e dalla modalità di creazione del progetto:  
  
-   Nei progetti Visual Basic o nei progetti Visual c# creati in uno [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] o [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] eseguire tutti i passaggi nel file code-behind della barra multifunzione (*YourRibbonItem*. Designer.cs o *YourRibbonItem*. Designer. vb). Per visualizzare il file code-behind nei progetti Visual Basic, scegliere il **Mostra tutti i file** pulsante **Esplora**.  
  
-   Nei progetti Visual c# creati in Visual Studio 2008 e successivamente aggiornato a [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], eseguire i primi due passaggi nel file di codice della barra multifunzione (*YourRibbonItem*. cs o *YourRibbonItem*VB), e eseguire i passaggi rimanenti nel file di codice della barra multifunzione.  
  
#### <a name="to-change-the-generated-ribbon-code"></a>Per modificare il codice della barra multifunzione generato  
  
1.  Modificare la dichiarazione della classe Ribbon in modo che derivi da <xref:Microsoft.Office.Tools.Ribbon.RibbonBase> anziché OfficeRibbon.  
  
2.  Modificare il costruttore della classe Ribbon come illustrato di seguito. Se è stato aggiunto codice al costruttore, non modificare il codice. Nei progetti Visual Basic modificare solo il costruttore senza parametri. Ignorare l'altro costruttore.  
  
     L'esempio di codice seguente illustra il costruttore predefinito di una classe Ribbon in un progetto destinato a .NET Framework 3.5  
  
    ```vb  
    Public Sub New()  
        MyBase.New()  
        InitializeComponent()  
    End Sub  
    ```  
  
    ```csharp  
    public Ribbon1()  
    {  
        InitializeComponent();  
    }  
    ```  
  
     L'esempio di codice seguente illustra il costruttore predefinito di una classe Ribbon in un progetto destinato a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive.  
  
    ```vb  
    Public Sub New()  
        MyBase.New(Globals.Factory.GetRibbonFactory())  
        InitializeComponent()  
    End Sub  
    ```  
  
    ```csharp  
    public Ribbon1()  
        : base(Globals.Factory.GetRibbonFactory())  
    {  
        InitializeComponent();  
    }  
    ```  
  
3.  Nel metodo `InitializeComponent` modificare il codice con il quale viene costruito un controllo barra multifunzione in modo che il codice usi invece uno dei metodi di supporto dell'oggetto <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory>.  
  
    > [!NOTE]  
    >  Nei progetti Visual C# è necessario espandere l'area denominata `Component Designer generated code` per visualizzare il metodo `InitializeComponent`.  
  
     Ad esempio, si supponga che il file contenga la riga di codice seguente con la quale viene creata un'istanza di un oggetto <xref:Microsoft.Office.Tools.Ribbon.RibbonButton> denominata `button1` in un progetto destinato a .NET Framework 3.5.  
  
    ```vb  
    Me.button1 = New Microsoft.Office.Tools.Ribbon.RibbonButton()  
    ```  
  
    ```csharp  
    this.button1 = new Microsoft.Office.Tools.Ribbon.RibbonButton();  
    ```  
  
     In un progetto destinato a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive, è necessario usare il codice seguente.  
  
    ```vb  
    Me.button1 = Me.Factory.CreateRibbonButton()  
    ```  
  
    ```csharp  
    this.button1 = this.Factory.CreateRibbonButton();  
    ```  
  
     Per un elenco completo dei metodi di supporto per i controlli della barra multifunzione, vedere [creazione di controlli della barra multifunzione](#ribboncontrols).  
  
4.  Nei progetti Visual C# modificare qualsiasi riga di codice nel metodo `InitializeComponent` che usa un delegato <xref:System.EventHandler%601> per usare invece un delegato specifico della barra multifunzione.  
  
     Ad esempio, si supponga che il file contenga la riga di codice seguente con la quale viene gestito l'evento <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> in un progetto destinato a .NET Framework 3.5.  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
     In un progetto destinato a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive, è necessario usare il codice seguente.  
  
<CodeContentPlaceHolder>9</CodeContentPlaceHolder>  
     Per un elenco completo dei delegati della barra multifunzione, vedere [gestione degli eventi della barra multifunzione](#ribbonevents).  
  
5.  Nei progetti Visual Basic trovare la classe `ThisRibbonCollection` alla fine del file. Modificare la dichiarazione di questa classe in modo che non erediti più da RibbonReadOnlyCollection.  
  
##  <a name="ribboncontrols"></a>Creazione di controlli della barra multifunzione  
 È necessario modificare il codice che crea dinamicamente un'istanza dei controlli barra multifunzione. Nei progetti destinati a .NET Framework 3.5 i controlli barra multifunzione sono classi per le quali è possibile creare un'istanza direttamente in alcuni scenari. Nei progetti destinati a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive, questi controlli sono interfacce di cui non è possibile creare istanze direttamente. È necessario creare i controlli con i metodi forniti dall'oggetto <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory>.  
  
 Sono disponibili due modi per accedere all'oggetto <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory>:  
  
-   Utilizzando la proprietà Factory della classe Ribbon. Usare questo approccio dal codice della classe Ribbon.  
  
-   Tramite il metodo Globals.Factory.GetRibbonFactory. Usare questo approccio dal codice all'esterno della classe Ribbon. Per ulteriori informazioni sulla classe Globals, vedere [accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
 L'esempio di codice seguente dimostra come creare <xref:Microsoft.Office.Tools.Ribbon.RibbonButton> in una classe Ribbon in un progetto destinato a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive.   
  
<CodeContentPlaceHolder>10</CodeContentPlaceHolder>  
<CodeContentPlaceHolder>11</CodeContentPlaceHolder>  
 La tabella seguente elenca i controlli creati a livello di codice e il metodo da usare per creare i controlli nei progetti destinati a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive.  
  
|CTRL|Metodo RibbonFactory da usare nei progetti [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] e versioni successive|  
|-------------|---------------------------------------------------------------------------------------------------------------|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonButton%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonButtonGroup%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonCheckBox%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonComboBox%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDialogLauncher%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>:|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDropDown%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDownItem>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDropDownItem%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonEditBox%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonGallery%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonGroup%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonLabel%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonManager>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonManager%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonMenu%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonSeparator%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonSplitButton%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonTab%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonToggleButton%2A>|  
  
##  <a name="ribbonevents"></a>Gestione di eventi della barra multifunzione  
 È necessario modificare il codice che gestisce gli eventi dei controlli barra multifunzione. Nei progetti destinati a .NET Framework 3.5 questi eventi sono gestiti dal delegato <xref:System.EventHandler%601> generico. Nei progetti destinati a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive, questi eventi sono ora gestiti da altri delegati.  
  
 La tabella seguente elenca gli eventi della barra multifunzione e i delegati associati nei progetti destinati a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive.  
  
|event|Delegato da usare in progetti di [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] e versioni successive|  
|-----------|---------------------------------------------------------------------------------------------------|  
|Evento <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage> in una classe Ribbon generata|<xref:Microsoft.Office.Tools.Ribbon.RibbonLoadImageEventHandler>|  
|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load>|<xref:Microsoft.Office.Tools.Ribbon.RibbonUIEventHandler>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.TextChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.ButtonClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.SelectionChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox.TextChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ButtonClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click>|<xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventHandler>|  
  
## <a name="setting-the-position-of-a-ribbon-component-programmatically"></a>Impostazione della posizione di un componente della barra multifunzione a livello di codice  
 È necessario modificare il codice che imposta la posizione di gruppi, schede o controlli barra multifunzione. Nei progetti destinati a .NET Framework 3.5, è possibile utilizzare i metodi AfterOfficeId e BeforeOfficeId della classe Microsoft.Office.Tools.Ribbon.RibbonPosition statica per assegnare la proprietà posizione di un gruppo, scheda o controllo. Nei progetti destinati a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive, è necessario accedere a questi metodi usando la proprietà <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.RibbonPosition%2A> fornita dall'oggetto <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory>.  
  
 Sono disponibili due modi per accedere all'oggetto <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory>:  
  
-   Utilizzando la proprietà Factory della classe Ribbon. Usare questo approccio dal codice della classe Ribbon.  
  
-   Tramite il metodo Globals.Factory.GetRibbonFactory. Usare questo approccio dal codice all'esterno della classe Ribbon. Per ulteriori informazioni sulla classe Globals, vedere [accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
 Esempio di codice riportato di seguito viene illustrato come impostare la proprietà di posizione di una scheda in una classe Ribbon in un progetto destinato a .NET Framework 3.5.  
  
```vb  
Me.tab1.Position = RibbonPosition.AfterOfficeId("TabHome")  
```  
  
```csharp  
this.tab1.Position = RibbonPosition.AfterOfficeId("TabHome");  
```  
  
 L'esempio di codice seguente illustra la stessa attività per un progetto destinato a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  
  
```vb  
Me.tab1.Position = Me.Factory.RibbonPosition.AfterOfficeId("TabHome")  
```  
  
```csharp  
this.tab1.Position = this.Factory.RibbonPosition.AfterOfficeId("TabHome");  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Migrating Office Solutions to the .NET Framework 4 or later](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)  
  
  