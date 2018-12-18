---
title: Immagine di servizio e catalogo | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 34990c37-ae98-4140-9b1e-a91c192220d9
caps.latest.revision: "37"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 6f5d31e28c47dbcd4f17f7f1e1bc0ac6a8755d5b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="image-service-and-catalog"></a>Catalogo e servizio immagini
Questa Guida di riferimento contiene informazioni e procedure consigliate per adottare il servizio immagini di Visual Studio e il catalogo di immagini introdotta in Visual Studio 2015.  
  
 Il servizio immagini introdotto in Visual Studio 2015 consente agli sviluppatori di ottenere le immagini migliori per il dispositivo e il tema scelto dell'utente per visualizzare l'immagine, inclusi i temi corretto per il contesto in cui vengono visualizzati. Adottare il servizio immagini consente di eliminare i punti non indifferente correlati alla manutenzione di asset, ridimensionamento HDPI e temi.  
  
|||  
|-|-|  
|**Problemi relativi a oggi**|**Soluzioni**|  
|La sfumatura di colore di sfondo|Sfumatura alfa incorporato|  
|Immagini dei temi (alcune)|Metadati del tema|  
|La modalità contrasto elevato|Risorse alternative di contrasto elevato|  
|È necessario più risorse per le diverse modalità di DPI|Risorse selezionabile con fallback basato su vettore|  
|Immagini duplicate|Un identificatore per il concetto di immagine|  
  
 Adottare perché il servizio immagini?  
  
-   Ottenere sempre l'ultima immagine "pixel perfetto" da Visual Studio  
  
-   È possibile inviare e utilizzare le proprie immagini  
  
-   Non è necessario testare le immagini out quando Windows aggiunge di nuovo di ridimensionamento DPI  
  
-   Indirizzo ostacoli dell'architettura precedente nelle implementazioni di  
  
 Visual Studio shell barra degli strumenti prima e dopo aver utilizzato il servizio immagini:  
  
 ![Servizio immagini prima e dopo](../extensibility/media/image-service-before-and-after.png "servizio immagini prima e dopo")  
  
## <a name="how-it-works"></a>Come funziona  
 Il servizio immagini può fornire un'immagine bitmap adatta per un framework dell'interfaccia utente supportato:  
  
-   WPF: BitmapSource  
  
-   Windows Form: System.Drawing.Bitmap  
  
-   Win32: HBITMAP  
  
 Diagramma di flusso del servizio di immagine  
  
 ![Immagine di diagramma di flusso del servizio](../extensibility/media/image-service-flow-diagram.png "immagine diagramma di flusso del servizio")  
  
 **Moniker di immagini**  
  
 Un moniker immagine (o un moniker per breve) è una coppia GUID/ID che identifica in modo univoco un asset di immagine o risorsa di elenco di immagine nella raccolta immagini.  
  
 **Moniker noti**  
  
 Il set di moniker di immagini contenute nel catalogo di immagini Visual Studio e pubblicamente che può essere utilizzato da qualsiasi componente di Visual Studio o estensione.  
  
 **File manifesto immagine**  
  
 File di immagine manifesto (.imagemanifest) sono file XML che definiscono un set di risorse di immagini, il moniker che rappresentano tali risorse e l'immagine reale o le immagini per rappresentare ogni asset. Manifesti dell'immagine è possibile definire immagini autonome o elenchi di immagini per il supporto dell'interfaccia utente legacy. Inoltre, esistono attributi che è possibile impostare nell'asset o delle singole immagini dietro ogni asset cambiare la data e la modalità di visualizzazione di tali risorse.  
  
 **Schema del manifesto di immagini**  
  
 Un manifesto di completare l'immagine è simile al seguente:  
  
```xml  
<ImageManifest>  
      <!-- zero or one Symbols elements -->  
      <Symbols>  
        <!-- zero or more Import, Guid, ID, or String elements -->  
      </Symbols>  
      <!-- zero or one Images elements -->  
      <Images>  
        <!-- zero or more Image elements -->  
      </Images>  
      <!-- zero or one ImageLists elements -->  
      <ImageLists>  
        <!-- zero or more ImageList elements -->  
      </ImageLists>  
</ImageManifest>  
```  
  
 **Simboli**  
  
 Come favorire un leggibilità e la manutenzione, il manifesto di immagini è possibile usare i simboli per i valori di attributo. I simboli sono definiti come segue:  
  
```xml  
<Symbols>  
      <Import Manifest="manifest" />  
      <Guid Name="ShellCommandGuid" Value="8ee4f65d-bab4-4cde-b8e7-ac412abbda8a" />  
      <ID Name="cmdidSaveAll" Value="1000" />  
      <String Name="AssemblyName" Value="Microsoft.VisualStudio.Shell.UI.Internal" />  
</Symbols>  
```  
  
|||  
|-|-|  
|**Sottoelemento**|**Definizione**|  
|Import|Importa i simboli del file manifesto specificato per l'utilizzo nel manifesto corrente|  
|GUID|Il simbolo rappresenta un GUID e deve corrispondere a GUID formattazione|  
|Id|Il simbolo rappresenta un ID e deve essere un numero intero non negativo|  
|Stringa|Il simbolo rappresenta un valore stringa arbitrario|  
  
 I simboli sono maiuscole / minuscole e di cui viene fatto riferimento utilizzando la sintassi $(symbol-name):  
  
```xml  
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >  
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />  
</Image>  
```  
  
 Alcuni simboli sono predefiniti per tutti i manifesti. Possono essere usati nell'attributo dell'Uri di \<origine > o \<importazione > elemento ai percorsi di riferimento sul computer locale.  
  
|||  
|-|-|  
|**Simbolo**|**Descrizione**|  
|CommonProgramFiles|Il valore della variabile di ambiente % CommonProgramFiles %|  
|LocalAppData|Il valore della variabile di ambiente % LocalAppData %|  
|ManifestFolder|La cartella contenente il file manifesto|  
|Documenti|Il percorso completo della cartella documenti dell'utente corrente|  
|ProgramFiles|Il valore della variabile di ambiente % ProgramFiles %|  
|System|Nella cartella Windows\System32|  
|WinDir|Il valore della variabile di ambiente % WinDir %|  
  
 **Immagine**  
  
 Il \<immagine > elemento definisce un'immagine che è possibile fare riferimento da un moniker. Il GUID e l'ID nel loro insieme costituiscono il moniker dell'immagine. Il moniker per l'immagine deve essere univoco tra la libreria di immagini intero. Se più di un'immagine è un moniker specificato, il primo durante la compilazione della libreria è quello che viene mantenuto.  
  
 Deve contenere almeno un'origine. Indipendente dalla dimensione origini fornirà i migliori risultati in una vasta gamma di dimensioni, ma non sono necessarie. Se il servizio è richiesto per un'immagine di dimensioni non è stata definita il \<immagine > elemento ed è presente alcuna origine indipendente dalla dimensione, il servizio scegliere la migliore fonte di dimensioni specifiche e applicarvi la scalabilità per la dimensione richiesta.  
  
```xml  
<Image Guid="guid" ID="int" AllowColorInversion="true/false">  
      <Source ... />  
      <!-- optional additional Source elements -->  
</Image>  
```  
  
|||  
|-|-|  
|**Attributo**|**Definizione**|  
|GUID|[Obbligatorio] La parte GUID del moniker di immagini|  
|Id|[Obbligatorio] La porzione dell'ID del moniker immagine|  
|AllowColorInversion|[Facoltativo, valore predefinito true] Indica se l'immagine può avere i colori invertiti a livello di codice quando viene utilizzata su uno sfondo scuro.|  
  
 **Origine**  
  
 Il \<origine > elemento definisce una risorsa di origine immagine singola (XAML e PNG).  
  
```xml  
<Source Uri="uri" Background="background">  
      <!-- optional NativeResource element -->  
 </Source>  
```  
  
|||  
|-|-|  
|**Attributo**|**Definizione**|  
|URI|[Obbligatorio] URI che definisce dove è possibile caricare l'immagine da. Può essere uno dei valori seguenti:<br /><br /> -A [URI di tipo Pack](http://msdn.microsoft.com/en-US/library/aa970069\(v=vs.100\).aspx) utilizzando l'applicazione: / / / autorità<br />-Un riferimento a una risorsa componente assoluto<br />-Un percorso di un file contenente una risorsa nativa|  
|Sfondo|[Facoltativo] Indica l'oggetto tipo di sfondo che dell'origine deve essere utilizzata.<br /><br /> Può essere uno dei valori seguenti:<br /><br /> *Illuminazione:* l'origine può essere utilizzata su uno sfondo.<br /><br /> *Scuro:*l'origine può essere utilizzata su uno sfondo scuro.<br /><br /> *Contrasto elevato:* l'origine può essere utilizzata su qualsiasi sfondo in modalità a contrasto elevato.<br /><br /> *HighContrastLight:* l'origine può essere utilizzata su uno sfondo di colore in modalità a contrasto elevato.<br /><br /> *HighContrastDark:* l'origine può essere utilizzata su uno sfondo scuro in modalità a contrasto elevato.<br /><br /> Se l'attributo Background viene omesso, l'origine è utilizzabile in qualsiasi dello sfondo.<br /><br /> Se lo sfondo è *luce*, *scuro*, *HighContrastLight*, o *HighContrastDark*, i colori dell'origine non vengono mai invertiti. Se viene omesso o è impostato su sfondo *contrasto elevato*, l'inversione dei colori dell'origine viene controllata l'immagine **AllowColorInversion** attributo.|  
|||  
  
 Oggetto \<origine > elemento può avere uno e uno solo dei sottoelementi facoltativi seguenti:  
  
||||  
|-|-|-|  
|**Elemento**|**Attributi (tutti necessari)**|**Definizione**|  
|\<Dimensioni >|Valore|L'origine verrà utilizzata per le immagini della dimensione specificata (in unità dispositivo). L'immagine sarà quadrato.|  
|\<SizeRange >|MinSize, MaxSize|L'origine verrà utilizzata per le immagini da MinSize MaxSize (in unità dispositivo), inclusi. L'immagine sarà quadrato.|  
|\<Dimensioni >|Larghezza, altezza|L'origine verrà utilizzata per le immagini di una determinata larghezza e altezza (in unità dispositivo).|  
|\<DimensionRange >|MinWidth, MinHeight,<br /><br /> MaxWidth, MaxHeight|L'origine verrà utilizzata per le immagini dalla larghezza/altezza minima di larghezza/altezza massima (in unità dispositivo), inclusi.|  
  
 Oggetto \<origine > elemento può avere anche un parametro facoltativo \<NativeResource > sottoelemento che definisce un \<origine > che viene caricato da un assembly nativo piuttosto che da un assembly gestito.  
  
```xml  
<NativeResource Type="type" ID="int" />  
```  
  
|||  
|-|-|  
|**Attributo**|**Definizione**|  
|Tipo|[Obbligatorio] Il tipo di risorsa nativa, XAML o PNG|  
|Id|[Obbligatorio] Il quoziente di ID di risorsa nativa|  
  
 **ImageList**  
  
 Il \<ImageList > elemento definisce una raccolta di immagini che possono essere restituite in un singolo elenco. L'elenco viene compilato su richiesta, in base alle esigenze.  
  
```xml  
<ImageList>  
      <ContainedImage Guid="guid" ID="int" External="true/false" />  
      <!-- optional additional ContainedImage elements -->  
 </ImageList>  
```  
  
|||  
|-|-|  
|**Attributo**|**Definizione**|  
|GUID|[Obbligatorio] La parte GUID del moniker di immagini|  
|Id|[Obbligatorio] La porzione dell'ID del moniker immagine|  
|Altre informazioni|[Impostazione predefinita è false, facoltativo] Indica se il moniker dell'immagine fa riferimento a un'immagine nel manifesto corrente.|  
  
 Il moniker per l'immagine contenuta non è necessario fare riferimento a un'immagine definita nel manifesto corrente. Se l'immagine del contenuto non viene trovato nella raccolta immagini, un'immagine segnaposto vuoto verrà utilizzata al suo posto.  
  
## <a name="using-the-image-service"></a>Tramite il servizio immagini  
  
### <a name="first-steps-managed"></a>Primi passi (gestite)  
 Per utilizzare il servizio immagini, è necessario aggiungere riferimenti ad alcuni o tutti gli assembly seguenti al progetto:  
  
-   **Microsoft.VisualStudio.ImageCatalog.dll**  
  
    -   Obbligatorio se si utilizza il catalogo di immagine incorporata KnownMonikers  
  
-   **Microsoft.VisualStudio.Imaging.dll**  
  
    -   Obbligatorio se si usa **CrispImage** e **ImageThemingUtilities** nella UI di WPF  
  
-   **Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll**  
  
    -   Obbligatorio se si usa il **ImageMoniker** e **ImageAttributes** tipi  
  
    -   **EmbedInteropTypes** deve essere impostato su true  
  
-   **Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime**  
  
    -   Obbligatorio se si usa il **IVsImageService2** tipo  
  
    -   **EmbedInteropTypes** deve essere impostato su true  
  
-   **Microsoft.VisualStudio.Utilities.dll**  
  
    -   Obbligatorio se si usa il **BrushToColorConverter** per il ImageThemingUtilities. **ImageBackgroundColor** nell'interfaccia utente WPF  
  
-   **Microsoft.VisualStudio.Shell. \<VSVersion >,0**  
  
    -   Obbligatorio se si usa il **IVsUIObject** tipo  
  
-   **Microsoft.VisualStudio.Shell.Interop.10.0.dll**  
  
    -   Obbligatorio se si usa gli helper di interfaccia utente relativa a Windows Form  
  
    -   **EmbedInteropTypes** deve essere impostato su true  
  
### <a name="first-steps-native"></a>Primi passi (nativo)  
 Per utilizzare il servizio immagini, è necessario includere alcune o tutte le intestazioni seguenti al progetto:  
  
-   **KnownImageIds.h**  
  
    -   Obbligatorio se si utilizza il catalogo di immagine incorporata **KnownMonikers**, ma non è possibile utilizzare il **ImageMoniker** tipo, ad esempio quando la restituzione di valori da **IVsHierarchy GetGuidProperty**o **GetProperty** chiamate.  
  
-   **KnownMonikers.h**  
  
    -   Obbligatorio se si utilizza il catalogo di immagine incorporata **KnownMonikers**.  
  
-   **ImageParameters140.h**  
  
    -   Obbligatorio se si usa il **ImageMoniker** e **ImageAttributes** tipi.  
  
-   **VSShell140.h**  
  
    -   Obbligatorio se si usa il **IVsImageService2** tipo.  
  
-   **ImageThemingUtilities.h**  
  
    -   Obbligatorio se non è possibile lasciare che il servizio immagini gestisca i temi si.  
  
    -   Non utilizzare questa intestazione se il servizio immagini in grado di gestire i temi di immagine.  
  
-   **VSUIDPIHelper.h**  
  
    -   Obbligatorio se si usa gli helper DPI per ottenere il valore del DPI corrente.  
  
## <a name="how-do-i-write-new-wpf-ui"></a>La modalità di scrittura di nuovi UI WPF  
  
1.  Inizio aggiungendo i riferimenti agli assembly necessari in questa prima la procedura di sezione per il progetto. Non è necessario aggiungere tutti gli elementi, aggiungere solo i riferimenti che necessari. (Nota: se si utilizza o si dispone dell'accesso a **colori** anziché **pennelli**, quindi è possibile passare il riferimento a **utilità**, poiché non è necessario il convertitore.)  
  
2.  Selezionare l'immagine desiderata e recuperare il moniker. Utilizzare un **KnownMoniker**, o utilizzare il proprio se si dispone delle proprie immagini personalizzate e il moniker.  
  
3.  Aggiungere **CrispImages** in XAML. (Vedere esempio seguente).  
  
4.  Impostare il **ImageThemingUtilities.ImageBackgroundColor** proprietà nella gerarchia dell'interfaccia utente. (Deve essere impostato in corrispondenza della posizione in cui il colore di sfondo è noto, non necessariamente nel **CrispImage**.) (Vedere esempio seguente).  
  
```xaml  
<Window  
  x:Class="WpfApplication.MainWindow"  
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
  xmlns:imaging="clr-namespace:Microsoft.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.Imaging"  
  xmlns:theming="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Imaging"  
  xmlns:utilities="clr-namespace:Microsoft.Internal.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.Imaging"  
  xmlns:catalog="clr-namespace:Microsoft.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.ImageCatalog"  
  Title="MainWindow" Height="350" Width="525" UseLayoutRounding="True">  
  <Window.Resources>  
    <utilities:BrushToColorConverter x:Key="BrushToColorConverter"/>  
  </Window.Resources>  
  <StackPanel Background="White" VerticalAlignment="Center"   
    theming:ImageThemingUtilities.ImageBackgroundColor="{Binding Background, RelativeSource={RelativeSource Self}, Converter={StaticResource BrushToColorConverter}}">  
    <imaging:CrispImage Width="16" Height="16" Moniker="{x:Static catalog:KnownMonikers.MoveUp}" />  
  </StackPanel>  
</Window>  
```  
  
 **Come posso aggiornare UI WPF esistenti?**  
  
 L'aggiornamento di UI WPF esistente è un processo relativamente semplice è costituito da tre passaggi di base:  
  
1.  Sostituisci tutto \<immagine > elementi nell'interfaccia utente con \<CrispImage > elementi  
  
2.  Modificare tutti gli attributi di origine per gli attributi di Moniker  
  
    -   Se l'immagine non modifica mai e si utilizza **KnownMonikers**, quindi associare in modo statico tale proprietà per il **KnownMoniker**. (Vedere l'esempio precedente).  
  
    -   Se l'immagine non modifica mai e si utilizza un'immagine personalizzata, quindi in modo statico associato al proprio moniker.  
  
    -   Se è possibile modificare l'immagine, è possibile associare l'attributo Moniker a una proprietà di codice che invia una notifica sulle modifiche di proprietà.  
  
3.  In un punto qualsiasi nella gerarchia dell'interfaccia utente, impostare **ImageThemingUtilities.ImageBackgroundColor** per rendere l'inversione di colore che funziona correttamente.  
  
    -   Potrebbe essere necessario l'utilizzo del **BrushToColorConverter** classe. (Vedere l'esempio precedente).  
  
## <a name="how-do-i-update-win32-ui"></a>Come aggiornare l'interfaccia utente di Win32?  
 Aggiungere quanto segue al codice ogni volta che è opportuno sostituire il caricamento di immagini non elaborato. Passare i valori per restituire gli HBITMAP e HICONs rispetto HIMAGELIST in base alle esigenze.  
  
 **Ottenere il servizio immagini**  
  
```cpp  
CComPtr<IVsImageService2> spImgSvc;  
CGlobalServiceProvider::HrQueryService(SID_SVsImageService, &spImgSvc);  
```  
  
 **L'immagine di richiesta**  
  
```cpp  
ImageAttributes attr = { 0 };  
attr.StructSize      = sizeof(attributes);  
attr.Format          = DF_Win32;  
// IT_Bitmap for HBITMAP, IT_Icon for HICON, IT_ImageList for HIMAGELIST  
attr.ImageType       = IT_Bitmap;  
attr.LogicalWidth    = 16;  
attr.LogicalHeight   = 16;  
attr.Dpi             = VsUI::DpiHelper::GetDeviceDpiX();  
attr.Background      = 0xFFFFFFFF;  
// Desired RGBA color, if you don't use this, don't set IAF_Background below  
attr.Flags           = IAF_RequiredFlags | IAF_Background;  
  
CComPtr<IVsUIObject> spImg;  
// Replace this KnownMoniker with your desired ImageMoniker  
spImgSvc->GetImage(KnownMonikers::Blank, attributes, &spImg);  
  
```  
  
## <a name="how-do-i-update-winforms-ui"></a>Come posso aggiornare WinForms UI?  
 Aggiungere quanto segue al codice ogni volta che è opportuno sostituire il caricamento di immagini non elaborato. Passare i valori per la restituzione di bitmap e icone in base alle esigenze.  
  
 **Istruzione using utili**  
  
```csharp  
using GelUtilities = Microsoft.Internal.VisualStudio.PlatformUI.Utilities;  
```  
  
 **Ottenere il servizio immagini**  
  
```csharp  
// This or your preferred way of querying for Visual Studio services  
IVsImageService2 imageService = (IVsImageService2)Package.GetGlobalService(typeof(SVsImageService));  
  
```  
  
 **Richiedono l'immagine**  
  
```csharp  
ImageAttributes attributes = new ImageAttributes  
{  
    StructSize    = Marshal.SizeOf(typeof(ImageAttributes)),  
    // IT_Bitmap for Bitmap, IT_Icon for Icon  
    ImageType     = (uint)_UIImageType.IT_Bitmap,  
    Format        = (uint)_UIDataFormat.DF_WinForms,  
    LogicalWidth  = 16,  
    LogicalHeight = 16,  
    // Desired RGBA color, if you don't use this, don't set IAF_Background below  
    Background    = 0xFFFFFFFF,  
    Flags = (uint)_ImageAttributesFlags.IAF_RequiredFlags | _ImageAttributesFlags.IAF_Background,  
};  
  
// Replace this KnownMoniker with your desired ImageMoniker  
IVsUIObject uIObj = imageService.GetImage(KnownMonikers.Blank, attributes);  
  
Bitmap bitmap = (Bitmap)GelUtilities.GetObjectData(uiObj); // Use this if you need a bitmap  
// Icon icon = (Icon)GelUtilities.GetObjectData(uiObj); // Use this if you need an icon  
  
```  
  
## <a name="how-do-i-use-image-monikers-in-a-new-tool-window"></a>Utilizzo di moniker di immagini in una nuova finestra degli strumenti  
 Il modello di progetto di pacchetto VSIX è stato aggiornato per Visual Studio 2015. Per creare una nuova finestra degli strumenti, fare clic sul progetto VSIX e selezionare "Aggiungi nuovo elemento..." (Ctrl + Maiusc + A). Nel nodo di estendibilità per il linguaggio del progetto, selezionare "Finestra degli strumenti personalizzata", assegnare un nome di finestra degli strumenti, quindi premere il pulsante "Aggiungi".  
  
 Questi sono i punti chiavi da usare moniker in una finestra degli strumenti. Seguire le istruzioni per ogni:  
  
1.  La scheda finestra degli strumenti quando le schede ottenere piccole sufficiente (utilizzato anche nelle finestre di Ctrl + Tab).  
  
     Aggiungere questa riga per il costruttore della classe che deriva dal **ToolWindowPane** tipo:  
  
    ```csharp  
    // Replace this KnownMoniker with your desired ImageMoniker  
    this.BitmapImageMoniker = KnownMonikers.Blank;  
    ```  
  
2.  Il comando per aprire la finestra degli strumenti.  
  
     Nel file vsct per il pacchetto, modificare il pulsante di comando della finestra dello strumento:  
  
    ```xml  
    <Button guid="guidPackageCmdSet" id="CommandId" priority="0x0100" type="Button">  
      <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>  
      <!-- Replace this KnownMoniker with your desired ImageMoniker -->  
      <Icon guid="ImageCatalogGuid" id="Blank" />  
      <!-- Add this -->  
      <CommandFlag>IconIsMoniker</CommandFlag>  
      <Strings>  
        <ButtonText>MyToolWindow</ButtonText>  
      </Strings>  
    </Button>  
    ```  
  
 **Utilizzo di moniker di immagini in una finestra dello strumento esistente**  
  
 L'aggiornamento di una finestra dello strumento esistente per l'utilizzo di moniker immagine è simile ai passaggi per la creazione di una nuova finestra degli strumenti.  
  
 Questi sono i punti chiavi da usare moniker in una finestra degli strumenti. Seguire le istruzioni per ogni:  
  
1.  La scheda finestra degli strumenti quando le schede ottenere piccole sufficiente (utilizzato anche nelle finestre di Ctrl + Tab).  
  
    1.  Rimuovere le righe seguenti (se presenti) nel costruttore per la classe che deriva dal **ToolWindowPane** tipo:  
  
        ```csharp  
        this.BitmapResourceID = <Value>;  
        this.BitmapIndex = <Value>;  
        ```  
  
    2.  Vedere il passaggio &#1; il "How Do I moniker di immagine di utilizzare in una nuova finestra degli strumenti?" sezione precedente.  
  
2.  Il comando per aprire la finestra degli strumenti.  
  
    -   Passaggio &#2;, vedere la "How Do I moniker di immagine di utilizzare in una nuova finestra degli strumenti?" sezione precedente.  
  
## <a name="how-do-i-use-image-monikers-in-a-vsct-file"></a>Utilizzo di moniker di immagini in un file vsct  
 Aggiornare il file con estensione vsct come indicato dalle righe di commento seguenti:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <!--  Include the definitions for images included in the VS image catalog -->  
  <Include href="KnownImageIds.vsct"/>  
  <Commands package="guidMyPackage">  
    <Buttons>  
      <Button guid="guidMyCommandSet" id="cmdidMyCommand" priority="0x0000" type="Button">  
        <!-- Add an Icon element, changing the attributes to match the image moniker you want to use.  
             In this case, we're using the Guid for the VS image catalog.  
             Change the id attribute to be the ID of the desired image moniker. -->  
        <Icon guid="ImageCatalogGuid" id="OpenFolder" />  
        <CommandFlag>DynamicVisibility</CommandFlag>  
        <CommandFlag>DefaultInvisible</CommandFlag>  
        <CommandFlag>DefaultDisabled</CommandFlag>  
        <CommandFlag>CommandWellOnly</CommandFlag>  
        <CommandFlag>IconAndText</CommandFlag>  
        <!-- Add the IconIsMoniker CommandFlag -->  
        <CommandFlag>IconIsMoniker</CommandFlag>  
        <Strings>  
          <ButtonText>Quick Fixes...</ButtonText>  
          <CommandName>Show Quick Fixes</CommandName>  
          <CanonicalName>ShowQuickFixes</CanonicalName>  
          <LocCanonicalName>ShowQuickFixes</LocCanonicalName>  
        </Strings>  
      </Button>  
    </Buttons>  
  </Commands>  
  <!-- It is recommended that you remove <Bitmap> elements that are no longer used in the vsct file -->  
  <Symbols>  
    <GuidSymbol name="guidMyPackage"    value="{1491e936-6ffe-474e-8371-30e5920d8fdd}" />  
    <GuidSymbol name="guidMyCommandSet" value="{10347de4-69a9-47f4-a950-d3301f6d2bc7}">  
      <IDSymbol name="cmdidMyCommand" value="0x9437" />  
    </GuidSymbol>  
  </Symbols>  
</CommandTable>  
```  
  
 **Cosa accade se il file con estensione vsct deve inoltre essere letto da versioni precedenti di Visual Studio?**  
  
 Le versioni precedenti di Visual Studio non è possibile riconoscere il **IconIsMoniker** flag di comando. È possibile utilizzare immagini dal servizio immagine su versioni di Visual Studio che lo supporta, ma continuano a utilizzare le immagini di vecchio stile nelle versioni precedenti di Visual Studio. A tale scopo, è necessario lasciare il file con estensione vsct invariato (e pertanto compatibili con versioni precedenti di Visual Studio) e creare un file CSV (valori delimitati da virgole) che esegue il mapping da coppie/ID GUID definite in un file con estensione vsct \<bitmap > elemento immagine coppie GUID/ID moniker.  
  
 Il formato del file CSV di mapping è:  
  
```  
Icon guid, Icon id, Moniker guid, Moniker id  
b714fcf7-855e-4e4c-802a-1fd87144ccad,1,fda30684-682d-421c-8be4-650a2967058e,100  
b714fcf7-855e-4e4c-802a-1fd87144ccad,2,fda30684-682d-421c-8be4-650a2967058e,200  
```  
  
 Il file CSV viene distribuito con il pacchetto e il relativo percorso è specificato dal **IconMappingFilename** proprietà del **ProvideMenuResource** attributo package:  
  
```csharp  
[ProvideMenuResource("MyPackage.ctmenu", 1, IconMappingFilename="IconMappings.csv")]  
```  
  
 Il **IconMappingFilename** un percorso relativo in modo implicito con radice in $ $PackageFolder (come nell'esempio precedente) o un percorso assoluto con radice in modo esplicito in una directory definita da una variabile di ambiente, ad esempio @"%UserProfile%\ dir1\dir2\MyMappingFile.csv".  
  
## <a name="how-do-i-port-a-project-system"></a>La modalità di porta di un sistema di progetto  
 **Come fornire ImageMonikers per un progetto**  
  
1.  Implementare **VSHPROPID_SupportsIconMonikers** il progetto **IVsHierarchy**e restituisce true.  
  
2.  Implementare uno **VSHPROPID_IconMonikerImageList** (se il progetto originale utilizzato **VSHPROPID_IconImgList**) o **VSHPROPID_IconMonikerGuid**,  **VSHPROPID_IconMonikerId**, **VSHPROPID_OpenFolderIconMonikerGuid**, **VSHPROPID_OpenFolderIconMonikerId** (se il progetto originale utilizzato  **VSHPROPID_IconHandle** e **VSHPROPID_OpenFolderIconHandle**).  
  
3.  Modificare l'implementazione del VSHPROPIDs originale per le icone per creare versioni "legacy" delle icone se ne fanno richiedono punti di estensione. **IVsImageService2** fornisce la funzionalità necessaria per ottenere le icone  
  
 **Requisiti aggiuntivi per VB / c# progetto caratteristiche**  
  
 Implementare solo **VSHPROPID_SupportsIconMonikers** se si rileva che il progetto è il **flavor più esterno**. In caso contrario, la versione più esterna effettiva potrebbe non supportare i moniker di immagini in realtà, e la versione di base potrebbe effettivamente "hide" immagini personalizzate.  
  
 **Utilizzo di moniker di immagini in CPS**  
  
 L'impostazione di immagini personalizzate in CPS (Common Project System) può essere eseguita manualmente o tramite un modello di elemento che viene fornito con il SDK di estendibilità del sistema di progetto.  
  
 **Utilizzare l'estensibilità del sistema di progetto SDK**  
  
 Seguire le istruzioni in [fornire icone personalizzate per il tipo del tipo di progetto/elemento](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/scenario/provide_custom_icons_for_the_project_or_item_type.md) per personalizzare le immagini di CPS. Ulteriori informazioni sull'istruzione CPS sono reperibile in [documentazione estendibilità di sistema progetto di Visual Studio](https://github.com/Microsoft/VSProjectSystem)  
  
 **Utilizzare manualmente ImageMonikers**  
  
1.  Implementare ed esportare il **IProjectTreeModifier** interfaccia nel sistema di progetto.  
  
2.  Determinare quale **KnownMoniker** o moniker dell'immagine personalizzata che si desidera utilizzare.  
  
3.  Nel **ApplyModifications** (metodo), eseguire le operazioni seguenti in un punto nel metodo prima di restituire il nuovo albero, simile all'esempio seguente:  
  
    ```csharp  
    // Replace this KnownMoniker with your desired ImageMoniker  
    tree = tree.SetIcon(KnownMonikers.Blank.ToProjectSystemType());  
    ```  
  
4.  Se si sta creando un nuovo albero, è possibile impostare le immagini personalizzate passando i moniker desiderati nel metodo NewTree simile per l'esempio seguente:  
  
    ```csharp  
    // Replace this KnownMoniker with your desired ImageMoniker  
    ProjectImageMoniker icon         = KnownMonikers.FolderClosed.ToProjectSystemType();  
    ProjectImageMoniker expandedIcon = KnownMonikers.FolderOpened.ToProjectSystemType();  
  
    return this.ProjectTreeFactory.Value.NewTree(/*caption*/<value>,  
                                                 /*filePath*/<value>,  
                                                 /*browseObjectProperties*/<value>,  
                                                 icon,  
                                                 expandedIcon);  
    ```  
  
## <a name="how-do-i-convert-from-a-real-image-strip-to-a-moniker-based-image-strip"></a>Come si converte da un elenco di immagini reali in un elenco di immagini basate su moniker?  
 **È necessario supportare HIMAGELISTs**  
  
 Se è presente un elenco di immagini già esistente per il codice che si desidera aggiornare per utilizzare il servizio immagini, ma sono limitati dalle API che richiedono di utilizzare elenchi di immagini, è comunque possibile ottenere i vantaggi del servizio di immagine. Per creare un elenco di immagini basate su moniker, seguire i passaggi seguenti per creare un manifesto da moniker esistente.  
  
1.  Eseguire il **ManifestFromResources** strumento, passando l'elenco di immagini. Verrà generato un manifesto per la striscia.  
  
    -   Consigliato: specificare un nome di non predefinito per il manifesto soddisfare il relativo utilizzo.  
  
2.  Se si utilizzano solo **KnownMonikers**, quindi eseguire le operazioni seguenti:  
  
    -   Sostituire il \<immagini > della sezione del manifesto con \<immagini / >.  
  
    -   Rimuovere tutti l'icona della regione ID (qualsiasi valore con \<imagestrip nome > _ # #).  
  
    -   Consigliato: rinominare il simbolo AssetsGuid e il simbolo striscia di immagine in base alle esigenze dell'utilizzo.  
  
    -   Sostituire ogni **ContainedImage**del GUID con $(ImageCatalogGuid), sostituire ogni **ContainedImage**dell'ID con $(\<moniker >) e aggiungere l'attributo "true" esterno = ogni **ContainedImage**  
  
        -   \<moniker > deve essere sostituito con il **KnownMoniker** che corrisponda all'immagine, ma con "KnownMonikers". rimosso dal nome.  
  
    -   Aggiungere < importazione Manifest="$(ManifestFolder)\\< relativo installare percorso dir\>\Microsoft.VisualStudio.ImageCatalog.imagemanifest" /\> all'inizio del \<simboli > sezione.  
  
        -   Il percorso relativo è il percorso di distribuzione definito nel programma di installazione di authoring per il manifesto.  
  
3.  Eseguire il **ManifestToCode** strumento per generare i wrapper in modo che il codice esistente con un moniker può utilizzare per eseguire query sul servizio di immagine per l'elenco immagini.  
  
    -   Consigliato: specificare i nomi non predefinito per il wrapper e spazi dei nomi in base all'utilizzo.  
  
4.  Eseguire tutte le aggiunge, il programma di installazione di creazione/distribuzione e altre modifiche al codice per funzionare con il servizio immagini e i nuovi file.  
  
 Incluse le immagini interne ed esterne per vedere cosa dovrebbe essere simile al manifesto di esempio:  
  
```xml  
<?xml version="1.0"?>  
<ImageManifest  
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
  xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">  
  
  <Symbols>  
    <!-- This needs to be the relative path from your manifest to the ImageCatalog's manifest  
         where $(ManifestFolder) is the deployed location of this manifest. -->  
    <Import Manifest="$(ManifestFolder)\<RelPath>\Microsoft.VisualStudio.ImageCatalog.imagemanifest" />  
  
    <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/ImageStrip" />  
    <Guid Name="ImageGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" />  
    <Guid Name="ImageStripGuid" Value="{9c84a570-d9a7-4052-a340-188fb276f973}" />  
    <ID Name="MyImage_0" Value="100" />  
    <ID Name="MyImage_1" Value="101" />  
    <ID Name="InternalList" Value="1001" />  
    <ID Name="ExternalList" Value="1002" />  
  </Symbols>  
  
  <Images>  
    <Image Guid="$(ImageGuid)" ID="$(MyImage_0)">  
      <Source Uri="$(Resources)/MyImage_0.png">  
        <Size Value="16" />  
      </Source>  
    </Image>  
    <Image Guid="$(ImageGuid)" ID="$(MyImage_1)">  
      <Source Uri="$(Resources)/MyImage_1.png">  
        <Size Value="16" />  
      </Source>  
    </Image>  
  </Images>  
  
  <ImageLists>  
    <ImageList Guid="$(ImageStripGuid)" ID="$(InternalList)">  
      <ContainedImage Guid="$(ImageGuid)" ID="$(MyImage_0)" />  
      <ContainedImage Guid="$(ImageGuid)" ID="$(MyImage_1)" />  
    </ImageList>  
    <ImageList Guid="$(ImageStripGuid)" ID="$(ExternalList)">  
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusError)" External="true" />  
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusWarning)" External="true" />  
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusInformation)" External="true" />  
    </ImageList>  
  </ImageLists>  
  
</ImageManifest>  
```  
  
 **Non è necessario supportare HIMAGELISTs**  
  
1.  Determinare il set di **KnownMonikers** che corrispondono le immagini nell'elenco di immagini o creare il propria moniker per le immagini nell'elenco di immagini.  
  
2.  Aggiornare qualsiasi mapping usato per ottenere l'immagine in corrispondenza dell'indice richiesto nell'elenco di immagine invece di utilizzare il moniker.  
  
3.  Aggiornare il codice per utilizzare il servizio immagini per richiedere i moniker tramite il mapping di aggiornamento. (È possibile che l'aggiornamento a **CrispImages** per codice gestito, o che richiede gli HBITMAP o HICONs dal servizio di immagine e passarli intorno a codice nativo.)  
  
## <a name="testing-your-images"></a>Testare le immagini  
 È possibile utilizzare lo strumento Visualizzatore di libreria di immagini per testare i manifesti dell'immagine per verificare che tutto ciò che è stato creato correttamente. È possibile trovare lo strumento di [Visual Studio 2015 SDK](http://msdn.microsoft.com/library/bb166441.aspx). Documentazione relativa a questo e altri strumenti è reperibile [qui](http://aka.ms/VSImageThemeTools).  
  
## <a name="additional-resources"></a>Risorse aggiuntive  
  
### <a name="samples"></a>Esempi  
 Molti degli esempi di Visual Studio in GitHub sono stati aggiornati per mostrare come utilizzare il servizio immagini come parte di vari punti di estendibilità di Visual Studio.  
  
 Controllare [http://github.com/Microsoft/VSSDK-Extensibility-Samples](http://github.com/Microsoft/VSSDK-Extensibility-Samples) per gli esempi più recenti.  
  
### <a name="tooling"></a>Strumenti  
 È stato creato un set di strumenti di supporto per il servizio immagini per facilitare la creazione o l'aggiornamento dell'interfaccia utente che funziona con il servizio immagini. Per ulteriori informazioni su ogni strumento, consultare la documentazione fornita con gli strumenti. Gli strumenti sono inclusi come parte di [Visual Studio 2015 SDK.](http://msdn.microsoft.com/library/bb166441.aspx)  
  
 **ManifestFromResources**  
  
 Il manifesto dallo strumento di risorse accetta un elenco di risorse grafiche (PNG o XAML) e genera un file manifesto immagine per l'utilizzo di tali immagini con il servizio immagini.  
  
 **ManifestToCode**  
  
 Il manifesto per lo strumento di codice accetta un file manifesto dell'immagine e genera un wrapper file per fare riferimento a valori del manifesto in codice (C++, c# o Visual Basic) o file con estensione vsct.  
  
 **ImageLibraryViewer**  
  
 Lo strumento Visualizzatore di immagini libreria può caricare l'immagine manifesti e consente all'utente di modificarli in modo identico a Visual Studio per verificare che il manifesto è stato creato correttamente. L'utente può modificare in background, le dimensioni, impostazione DPI, contrasto elevato e altre impostazioni. Inoltre, Visualizza le informazioni di caricamento per trovare gli errori nei manifesti e visualizza le informazioni di origine per ogni immagine nel manifesto.  
  
## <a name="faq"></a>Domande frequenti  
  
-   Sono presenti dipendenze che è necessario includere durante il caricamento \<Include="Microsoft.VisualStudio.* di riferimento. Interop.14.0.DesignTime"/ >?  
  
    -   Impostare EmbedInteropTypes = "true" in tutte le DLL di interoperabilità.  
  
-   Come distribuire un manifesto di immagini con estensione?  
  
    -   Aggiungere il file .imagemanifest al progetto.  
  
    -   Impostare "Includi in VSIX" su True.  
  
-   Il sistema di progetto CPS durante l'aggiornamento. Cosa è successo a **ImageName** e **StockIconService**?  
  
    -   o che queste sono state rimosse quando l'istruzione CPS è stato aggiornato per utilizzare i moniker. Non è più necessario chiamare il **StockIconService**, è sufficiente passare l'oggetto desiderato **KnownMoniker** al metodo o proprietà utilizzando il **ToProjectSystemType()** il metodo di estensione in le utilità di CPS. È possibile trovare un mapping da **ImageName** a **KnownMonikers** di seguito:  
  
        |||  
        |-|-|  
        |**ImageName**|**KnownMoniker**|  
        |ImageName.OfflineWebApp|KnownImageIds.Web|  
        |ImageName.WebReferencesFolder|KnownImageIds.Web|  
        |ImageName.OpenReferenceFolder|KnownImageIds.FolderOpened|  
        |ImageName.ReferenceFolder|KnownImageIds.Reference|  
        |ImageName.Reference|KnownImageIds.Reference|  
        |ImageName.SdlWebReference|KnownImageIds.WebReferenceFolder|  
        |ImageName.DiscoWebReference|KnownImageIds.DynamicDiscoveryDocument|  
        |ImageName.Folder|KnownImageIds.FolderClosed|  
        |ImageName.OpenFolder|KnownImageIds.FolderOpened|  
        |ImageName.ExcludedFolder|KnownImageIds.HiddenFolderClosed|  
        |ImageName.OpenExcludedFolder|KnownImageIds.HiddenFolderOpened|  
        |ImageName.ExcludedFile|KnownImageIds.HiddenFile|  
        |ImageName.DependentFile|KnownImageIds.GenerateFile|  
        |ImageName.MissingFile|KnownImageIds.DocumentWarning|  
        |ImageName.WindowsForm|KnownImageIds.WindowsForm|  
        |ImageName.WindowsUserControl|KnownImageIds.UserControl|  
        |ImageName.WindowsComponent|KnownImageIds.ComponentFile|  
        |ImageName.XmlSchema|KnownImageIds.XMLSchema|  
        |ImageName.XmlFile|KnownImageIds.XMLFile|  
        |ImageName.WebForm|KnownImageIds.Web|  
        |ImageName.WebService|KnownImageIds.WebService|  
        |ImageName.WebUserControl|KnownImageIds.WebUserControl|  
        |ImageName.WebCustomUserControl|KnownImageIds.WebCustomControl|  
        |ImageName.AspPage|KnownImageIds.ASPFile|  
        |ImageName.GlobalApplicationClass|KnownImageIds.SettingsFile|  
        |ImageName.WebConfig|KnownImageIds.ConfigurationFile|  
        |ImageName.HtmlPage|KnownImageIds.HTMLFile|  
        |ImageName.StyleSheet|KnownImageIds.StyleSheet|  
        |ImageName.ScriptFile|KnownImageIds.JSScript|  
        |ImageName.TextFile|KnownImageIds.Document|  
        |ImageName.SettingsFile|KnownImageIds.Settings|  
        |ImageName.Resources|KnownImageIds.DocumentGroup|  
        |ImageName.Bitmap|KnownImageIds.Image|  
        |ImageName.Icon|KnownImageIds.IconFile|  
        |ImageName.Image|KnownImageIds.Image|  
        |ImageName.ImageMap|KnownImageIds.ImageMapFile|  
        |ImageName.XWorld|KnownImageIds.XWorldFile|  
        |ImageName.Audio|KnownImageIds.Sound|  
        |ImageName.Video|KnownImageIds.Media|  
        |ImageName.Cab|KnownImageIds.CABProject|  
        |ImageName.Jar|KnownImageIds.JARFile|  
        |ImageName.DataEnvironment|KnownImageIds.DataTable|  
        |ImageName.PreviewFile|KnownImageIds.Report|  
        |ImageName.DanglingReference|KnownImageIds.ReferenceWarning|  
        |ImageName.XsltFile|KnownImageIds.XSLTransform|  
        |ImageName.Cursor|KnownImageIds.CursorFile|  
        |ImageName.AppDesignerFolder|KnownImageIds.Property|  
        |ImageName.Data|KnownImageIds.Database|  
        |ImageName.Application|KnownImageIds.Application|  
        |ImageName.DataSet|KnownImageIds.DatabaseGroup|  
        |ImageName.Pfx|KnownImageIds.Certificate|  
        |ImageName.Snk|KnownImageIds.Rule|  
        |ImageName.VisualBasicProject|KnownImageIds.VBProjectNode|  
        |ImageName.CSharpProject|KnownImageIds.CSProjectNode|  
        |ImageName.Empty|KnownImageIds.Blank|  
        |ImageName.MissingFolder|KnownImageIds.FolderOffline|  
        |ImageName.SharedImportReference|KnownImageIds.SharedProject|  
        |ImageName.SharedProjectCs|KnownImageIds.CSSharedProject|  
        |ImageName.SharedProjectVc|KnownImageIds.CPPSharedProject|  
        |ImageName.SharedProjectJs|KnownImageIds.JSSharedProject|  
        |ImageName.CSharpCodeFile|KnownImageIds.CSFileNode|  
        |ImageName.VisualBasicCodeFile|KnownImageIds.VBFileNode|  
  
    -   Il provider dell'elenco di completamento durante l'aggiornamento. Cosa **KnownMonikers** corrisponde a quella vecchia **StandardGlyphGroup** e **StandardGlyph** valori?  
  
        ||||  
        |-|-|-|  
        |GlyphGroupClass|GlyphItemPublic|ClassPublic|  
        |GlyphGroupClass|GlyphItemInternal|ClassInternal|  
        |GlyphGroupClass|GlyphItemFriend|ClassInternal|  
        |GlyphGroupClass|GlyphItemProtected|ClassProtected|  
        |GlyphGroupClass|GlyphItemPrivate|ClassPrivate|  
        |GlyphGroupClass|GlyphItemShortcut|ClassShortcut|  
        |GlyphGroupConstant|GlyphItemPublic|ClassPublic|  
        |GlyphGroupConstant|GlyphItemInternal|ClassInternal|  
        |GlyphGroupConstant|GlyphItemFriend|ClassInternal|  
        |GlyphGroupConstant|GlyphItemProtected|ClassProtected|  
        |GlyphGroupConstant|GlyphItemPrivate|ClassPrivate|  
        |GlyphGroupConstant|GlyphItemShortcut|ClassShortcut|  
        |GlyphGroupDelegate|GlyphItemPublic|DelegatePublic|  
        |GlyphGroupDelegate|GlyphItemInternal|DelegateInternal|  
        |GlyphGroupDelegate|GlyphItemFriend|DelegateInternal|  
        |GlyphGroupDelegate|GlyphItemProtected|DelegateProtected|  
        |GlyphGroupDelegate|GlyphItemPrivate|DelegatePrivate|  
        |GlyphGroupDelegate|GlyphItemShortcut|DelegateShortcut|  
        |GlyphGroupEnum|GlyphItemPublic|EnumerationPublic|  
        |GlyphGroupEnum|GlyphItemInternal|EnumerationInternal|  
        |GlyphGroupEnum|GlyphItemFriend|EnumerationInternal|  
        |GlyphGroupEnum|GlyphItemProtected|EnumerationProtected|  
        |GlyphGroupEnum|GlyphItemPrivate|EnumerationPrivate|  
        |GlyphGroupEnum|GlyphItemShortcut|EnumerationShortcut|  
        |GlyphGroupEnumMember|GlyphItemPublic|EnumerationMemberPublic|  
        |GlyphGroupEnumMember|GlyphItemInternal|EnumerationMemberInternal|  
        |GlyphGroupEnumMember|GlyphItemFriend|EnumerationMemberInternal|  
        |GlyphGroupEnumMember|GlyphItemProtected|EnumerationMemberProtected|  
        |GlyphGroupEnumMember|GlyphItemPrivate|EnumerationMemberPrivate|  
        |GlyphGroupEnumMember|GlyphItemShortcut|EnumerationMemberShortcut|  
        |GlyphGroupEvent|GlyphItemPublic|EventPublic|  
        |GlyphGroupEvent|GlyphItemInternal|EventInternal|  
        |GlyphGroupEvent|GlyphItemFriend|EventInternal|  
        |GlyphGroupEvent|GlyphItemProtected|EventProtected|  
        |GlyphGroupEvent|GlyphItemPrivate|EventPrivate|  
        |GlyphGroupEvent|GlyphItemShortcut|EventShortcut|  
        |GlyphGroupException|GlyphItemPublic|ExceptionPublic|  
        |GlyphGroupException|GlyphItemInternal|ExceptionInternal|  
        |GlyphGroupException|GlyphItemFriend|ExceptionInternal|  
        |GlyphGroupException|GlyphItemProtected|ExceptionProtected|  
        |GlyphGroupException|GlyphItemPrivate|ExceptionPrivate|  
        |GlyphGroupException|GlyphItemShortcut|ExceptionShortcut|  
        |GlyphGroupField|GlyphItemPublic|FieldPublic|  
        |GlyphGroupField|GlyphItemInternal|FieldInternal|  
        |GlyphGroupField|GlyphItemFriend|FieldInternal|  
        |GlyphGroupField|GlyphItemProtected|FieldProtected|  
        |GlyphGroupField|GlyphItemPrivate|FieldPrivate|  
        |GlyphGroupField|GlyphItemShortcut|FieldShortcut|  
        |GlyphGroupInterface|GlyphItemPublic|InterfacePublic|  
        |GlyphGroupInterface|GlyphItemInternal|InterfaceInternal|  
        |GlyphGroupInterface|GlyphItemFriend|InterfaceInternal|  
        |GlyphGroupInterface|GlyphItemProtected|InterfaceProtected|  
        |GlyphGroupInterface|GlyphItemPrivate|InterfacePrivate|  
        |GlyphGroupInterface|GlyphItemShortcut|InterfaceShortcut|  
        |GlyphGroupMacro|GlyphItemPublic|MacroPublic|  
        |GlyphGroupMacro|GlyphItemInternal|MacroInternal|  
        |GlyphGroupMacro|GlyphItemFriend|MacroInternal|  
        |GlyphGroupMacro|GlyphItemProtected|MacroProtected|  
        |GlyphGroupMacro|GlyphItemPrivate|MacroPrivate|  
        |GlyphGroupMacro|GlyphItemShortcut|MacroShortcut|  
        |GlyphGroupMap|GlyphItemPublic|MapPublic|  
        |GlyphGroupMap|GlyphItemInternal|MapInternal|  
        |GlyphGroupMap|GlyphItemFriend|MapInternal|  
        |GlyphGroupMap|GlyphItemProtected|MapProtected|  
        |GlyphGroupMap|GlyphItemPrivate|MapPrivate|  
        |GlyphGroupMap|GlyphItemShortcut|MapShortcut|  
        |GlyphGroupMapItem|GlyphItemPublic|MapItemPublic|  
        |GlyphGroupMapItem|GlyphItemInternal|MapItemInternal|  
        |GlyphGroupMapItem|GlyphItemFriend|MapItemInternal|  
        |GlyphGroupMapItem|GlyphItemProtected|MapItemProtected|  
        |GlyphGroupMapItem|GlyphItemPrivate|MapItemPrivate|  
        |GlyphGroupMapItem|GlyphItemShortcut|MapItemShortcut|  
        |GlyphGroupMethod|GlyphItemPublic|MethodPublic|  
        |GlyphGroupMethod|GlyphItemInternal|MethodInternal|  
        |GlyphGroupMethod|GlyphItemFriend|MethodInternal|  
        |GlyphGroupMethod|GlyphItemProtected|MethodProtected|  
        |GlyphGroupMethod|GlyphItemPrivate|MethodPrivate|  
        |GlyphGroupMethod|GlyphItemShortcut|MethodShortcut|  
        |GlyphGroupOverload|GlyphItemPublic|MethodPublic|  
        |GlyphGroupOverload|GlyphItemInternal|MethodInternal|  
        |GlyphGroupOverload|GlyphItemFriend|MethodInternal|  
        |GlyphGroupOverload|GlyphItemProtected|MethodProtected|  
        |GlyphGroupOverload|GlyphItemPrivate|MethodPrivate|  
        |GlyphGroupOverload|GlyphItemShortcut|MethodShortcut|  
        |GlyphGroupModule|GlyphItemPublic|ModulePublic|  
        |GlyphGroupModule|GlyphItemInternal|ModuleInternal|  
        |GlyphGroupModule|GlyphItemFriend|ModuleInternal|  
        |GlyphGroupModule|GlyphItemProtected|ModuleProtected|  
        |GlyphGroupModule|GlyphItemPrivate|ModulePrivate|  
        |GlyphGroupModule|GlyphItemShortcut|ModuleShortcut|  
        |GlyphGroupNamespace|GlyphItemPublic|NamespacePublic|  
        |GlyphGroupNamespace|GlyphItemInternal|NamespaceInternal|  
        |GlyphGroupNamespace|GlyphItemFriend|NamespaceInternal|  
        |GlyphGroupNamespace|GlyphItemProtected|NamespaceProtected|  
        |GlyphGroupNamespace|GlyphItemPrivate|NamespacePrivate|  
        |GlyphGroupNamespace|GlyphItemShortcut|NamespaceShortcut|  
        |GlyphGroupOperator|GlyphItemPublic|OperatorPublic|  
        |GlyphGroupOperator|GlyphItemInternal|OperatorInternal|  
        |GlyphGroupOperator|GlyphItemFriend|OperatorInternal|  
        |GlyphGroupOperator|GlyphItemProtected|OperatorProtected|  
        |GlyphGroupOperator|GlyphItemPrivate|OperatorPrivate|  
        |GlyphGroupOperator|GlyphItemShortcut|OperatorShortcut|  
        |GlyphGroupProperty|GlyphItemPublic|PropertyPublic|  
        |GlyphGroupProperty|GlyphItemInternal|PropertyInternal|  
        |GlyphGroupProperty|GlyphItemFriend|PropertyInternal|  
        |GlyphGroupProperty|GlyphItemProtected|PropertyProtected|  
        |GlyphGroupProperty|GlyphItemPrivate|PropertyPrivate|  
        |GlyphGroupProperty|GlyphItemShortcut|PropertyShortcut|  
        |GlyphGroupStruct|GlyphItemPublic|StructurePublic|  
        |GlyphGroupStruct|GlyphItemInternal|StructureInternal|  
        |GlyphGroupStruct|GlyphItemFriend|StructureInternal|  
        |GlyphGroupStruct|GlyphItemProtected|StructureProtected|  
        |GlyphGroupStruct|GlyphItemPrivate|StructurePrivate|  
        |GlyphGroupStruct|GlyphItemShortcut|StructureShortcut|  
        |GlyphGroupTemplate|GlyphItemPublic|TemplatePublic|  
        |GlyphGroupTemplate|GlyphItemInternal|TemplateInternal|  
        |GlyphGroupTemplate|GlyphItemFriend|TemplateInternal|  
        |GlyphGroupTemplate|GlyphItemProtected|TemplateProtected|  
        |GlyphGroupTemplate|GlyphItemPrivate|TemplatePrivate|  
        |GlyphGroupTemplate|GlyphItemShortcut|TemplateShortcut|  
        |GlyphGroupTypedef|GlyphItemPublic|TypeDefinitionPublic|  
        |GlyphGroupTypedef|GlyphItemInternal|TypeDefinitionInternal|  
        |GlyphGroupTypedef|GlyphItemFriend|TypeDefinitionInternal|  
        |GlyphGroupTypedef|GlyphItemProtected|TypeDefinitionProtected|  
        |GlyphGroupTypedef|GlyphItemPrivate|TypeDefinitionPrivate|  
        |GlyphGroupTypedef|GlyphItemShortcut|TypeDefinitionShortcut|  
        |GlyphGroupType|GlyphItemPublic|TypePublic|  
        |GlyphGroupType|GlyphItemInternal|TypeInternal|  
        |GlyphGroupType|GlyphItemFriend|TypeInternal|  
        |GlyphGroupType|GlyphItemProtected|TypeProtected|  
        |GlyphGroupType|GlyphItemPrivate|TypePrivate|  
        |GlyphGroupType|GlyphItemShortcut|TypeShortcut|  
        |GlyphGroupUnion|GlyphItemPublic|UnionPublic|  
        |GlyphGroupUnion|GlyphItemInternal|UnionInternal|  
        |GlyphGroupUnion|GlyphItemFriend|UnionInternal|  
        |GlyphGroupUnion|GlyphItemProtected|UnionProtected|  
        |GlyphGroupUnion|GlyphItemPrivate|UnionPrivate|  
        |GlyphGroupUnion|GlyphItemShortcut|UnionShortcut|  
        |GlyphGroupVariable|GlyphItemPublic|FieldPublic|  
        |GlyphGroupVariable|GlyphItemInternal|FieldInternal|  
        |GlyphGroupVariable|GlyphItemFriend|FieldInternal|  
        |GlyphGroupVariable|GlyphItemProtected|FieldProtected|  
        |GlyphGroupVariable|GlyphItemPrivate|FieldPrivate|  
        |GlyphGroupVariable|GlyphItemShortcut|FieldShortcut|  
        |GlyphGroupValueType|GlyphItemPublic|ValueTypePublic|  
        |GlyphGroupValueType|GlyphItemInternal|ValueTypeInternal|  
        |GlyphGroupValueType|GlyphItemFriend|ValueTypeInternal|  
        |GlyphGroupValueType|GlyphItemProtected|ValueTypeProtected|  
        |GlyphGroupValueType|GlyphItemPrivate|ValueTypePrivate|  
        |GlyphGroupValueType|GlyphItemShortcut|ValueTypeShortcut|  
        |GlyphGroupIntrinsic|GlyphItemPublic|ObjectPublic|  
        |GlyphGroupIntrinsic|GlyphItemInternal|ObjectInternal|  
        |GlyphGroupIntrinsic|GlyphItemFriend|ObjectInternal|  
        |GlyphGroupIntrinsic|GlyphItemProtected|ObjectProtected|  
        |GlyphGroupIntrinsic|GlyphItemPrivate|ObjectPrivate|  
        |GlyphGroupIntrinsic|GlyphItemShortcut|ObjectShortcut|  
        |GlyphGroupJSharpMethod|GlyphItemPublic|MethodPublic|  
        |GlyphGroupJSharpMethod|GlyphItemInternal|MethodInternal|  
        |GlyphGroupJSharpMethod|GlyphItemFriend|MethodInternal|  
        |GlyphGroupJSharpMethod|GlyphItemProtected|MethodProtected|  
        |GlyphGroupJSharpMethod|GlyphItemPrivate|MethodPrivate|  
        |GlyphGroupJSharpMethod|GlyphItemShortcut|MethodShortcut|  
        |GlyphGroupJSharpField|GlyphItemPublic|FieldPublic|  
        |GlyphGroupJSharpField|GlyphItemInternal|FieldInternal|  
        |GlyphGroupJSharpField|GlyphItemFriend|FieldInternal|  
        |GlyphGroupJSharpField|GlyphItemProtected|FieldProtected|  
        |GlyphGroupJSharpField|GlyphItemPrivate|FieldPrivate|  
        |GlyphGroupJSharpField|GlyphItemShortcut|FieldShortcut|  
        |GlyphGroupJSharpClass|GlyphItemPublic|ClassPublic|  
        |GlyphGroupJSharpClass|GlyphItemInternal|ClassInternal|  
        |GlyphGroupJSharpClass|GlyphItemFriend|ClassInternal|  
        |GlyphGroupJSharpClass|GlyphItemProtected|ClassProtected|  
        |GlyphGroupJSharpClass|GlyphItemPrivate|ClassPrivate|  
        |GlyphGroupJSharpClass|GlyphItemShortcut|ClassShortcut|  
        |GlyphGroupJSharpNamespace|GlyphItemPublic|NamespacePublic|  
        |GlyphGroupJSharpNamespace|GlyphItemInternal|NamespaceInternal|  
        |GlyphGroupJSharpNamespace|GlyphItemFriend|NamespaceInternal|  
        |GlyphGroupJSharpNamespace|GlyphItemProtected|NamespaceProtected|  
        |GlyphGroupJSharpNamespace|GlyphItemPrivate|NamespacePrivate|  
        |GlyphGroupJSharpNamespace|GlyphItemShortcut|NamespaceShortcut|  
        |GlyphGroupJSharpInterface|GlyphItemPublic|InterfacePublic|  
        |GlyphGroupJSharpInterface|GlyphItemInternal|InterfaceInternal|  
        |GlyphGroupJSharpInterface|GlyphItemFriend|InterfaceInternal|  
        |GlyphGroupJSharpInterface|GlyphItemProtected|InterfaceProtected|  
        |GlyphGroupJSharpInterface|GlyphItemPrivate|InterfacePrivate|  
        |GlyphGroupJSharpInterface|GlyphItemShortcut|InterfaceShortcut|  
        |GlyphGroupError||StatusError|  
        |GlyphBscFile||ClassFile|  
        |GlyphAssembly||Riferimenti|  
        |GlyphLibrary||Libreria|  
        |GlyphVBProject||VBProjectNode|  
        |GlyphCoolProject||CSProjectNode|  
        |GlyphCppProject||CPPProjectNode|  
        |GlyphDialogId||Finestra di dialogo|  
        |GlyphOpenFolder||FolderOpened|  
        |GlyphClosedFolder||FolderClosed|  
        |GlyphArrow||GoToNext|  
        |GlyphCSharpFile||CSFileNode|  
        |GlyphCSharpExpansion||Frammento di codice|  
        |GlyphKeyword||IntellisenseKeyword|  
        |GlyphInformation||StatusInformation|  
        |GlyphReference||ClassMethodReference|  
        |GlyphRecursion||Ricorsione|  
        |GlyphXmlItem||Tag|  
        |GlyphJSharpProject||DocumentCollection|  
        |GlyphJSharpDocument||Document|  
        |GlyphForwardType||GoToNext|  
        |GlyphCallersGraph||Callto://|  
        |GlyphCallGraph||CallFrom|  
        |GlyphWarning||StatusWarning|  
        |GlyphMaybeReference||QuestionMark|  
        |GlyphMaybeCaller||Callto://|  
        |GlyphMaybeCall||CallFrom|  
        |GlyphExtensionMethod||ExtensionMethod|  
        |GlyphExtensionMethodInternal||ExtensionMethod|  
        |GlyphExtensionMethodFriend||ExtensionMethod|  
        |GlyphExtensionMethodProtected||ExtensionMethod|  
        |GlyphExtensionMethodPrivate||ExtensionMethod|  
        |GlyphExtensionMethodShortcut||ExtensionMethod|  
        |GlyphXmlAttribute||XmlAttribute|  
        |GlyphXmlChild||XmlElement|  
        |GlyphXmlDescendant||XmlDescendant|  
        |GlyphXmlNamespace||xmlNamespace|  
        |GlyphXmlAttributeQuestion||XmlAttributeLowConfidence|  
        |GlyphXmlAttributeCheck||XmlAttributeHighConfidence|  
        |GlyphXmlChildQuestion||XmlElementLowConfidence|  
        |GlyphXmlChildCheck||XmlElementHighConfidence|  
        |GlyphXmlDescendantQuestion||XmlDescendantLowConfidence|  
        |GlyphXmlDescendantCheck||XmlDescendantHighConfidence|  
        |GlyphCompletionWarning||IntellisenseWarning|