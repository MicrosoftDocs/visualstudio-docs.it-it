---
title: Indirizzamento DPI Problemi2 | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 6218e01d061bbf65e0cae051050076e4b8267a2f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="addressing-dpi-issues"></a>Risolvere i problemi DPI
Un numero crescente di dispositivi è distribuiti con schermate "ad alta risoluzione". Queste schermate vengono visualizzate in genere sono più di 200 pixel per pollice (PPID). Utilizzo di un'applicazione in questi computer richiederà il contenuto per la scalabilità verticale per soddisfare le esigenze di visualizzazione del contenuto a una distanza di visualizzazione normale per il dispositivo. A partire da 2014, la destinazione principale per gli schermi ad alta densità è mobile computing dispositivi (telefoni, Tablet e portatili conchiglia).  
  
 Windows 8.1 e versioni successive sono disponibili molte funzionalità per abilitare questi computer per lavorare con gli ambienti in cui la macchina è associata a entrambi ad alta densità e densità standard consente di visualizzare contemporaneamente e Visualizza.  
  
-   Windows consente a ridimensiona il contenuto al dispositivo utilizzando il "accertarsi testo e altri elementi maggiori o minori" impostazione (disponibile a partire da Windows XP).  
  
-   Windows 8.1 e versioni successive verranno automaticamente scalati contenuto per la maggior parte delle applicazioni siano coerenti quando spostato da una visualizzazione delle diverse densità di pixel. Quando lo schermo primario è ad alta densità (200% scaling) e la visualizzazione secondaria è densità standard (100%), Windows verrà ridurre automaticamente il contenuto della finestra dell'applicazione sulla visualizzazione secondaria (1 pixel visualizzato per ogni 4 pixel eseguito il rendering tramite il applicazione).  
  
-   Windows utilizzerà il diritto di scalabilità per la densità di pixel e la visualizzazione di distanza per la visualizzazione (Windows 7 e versioni successive, configurabile dall'OEM).  
  
-   Windows può applicare la scalabilità automatica del contenuto di 250% su nuovi dispositivi che superano 280 PPID (a partire da Windows 8.1 S14).  
  
 Windows ha una soluzione per gestire la scalabilità verticale dell'interfaccia utente per sfruttare i vantaggi dei conteggi maggiore pixel. Un'applicazione consente di partecipare a questo sistema dichiarando stesso "sistema compatibilità DPI avanzata". Le applicazioni che si esegue questa operazione vengono ridimensionate dal sistema. Ciò può comportare un'esperienza utente "fuzzy" in cui è in modo uniforme estesa pixel dell'intera applicazione. Ad esempio:  
  
 ![DPI problemi Fuzzy](../extensibility/media/dpi-issues-fuzzy.png "DPI problemi Fuzzy")  
  
 Visual Studio consente di partecipare a da scalabilità compatibile con DPI e pertanto non viene "virtualizzata."  
  
 Windows (e Visual Studio) sfruttare diverse tecnologie dell'interfaccia utente, che sono diversi modi per gestire con dal sistema di fattori di scala. Ad esempio:  
  
-   WPF consente di misurare i controlli in modo indipendente dalla periferica (unità, non pixel). UI WPF viene ridimensionato automaticamente per la risoluzione corrente.  
  
-   Tutte le dimensioni di testo indipendentemente dal framework dell'interfaccia utente sono espresse in punti e pertanto vengono gestite dal sistema come indipendente dal DPI. Il testo Win32, Windows Form e WPF già la scalabilità verticale in modo corretto quando viene disegnata sullo schermo.  
  
-   Finestre di dialogo di Win32/Windows Form e Windows sono i mezzi per l'abilitazione di layout che viene ridimensionato con testo, ad esempio, tramite griglia, il flusso e pannelli di layout di tabella. Che permettono di evitare percorsi hardcoded pixel che non vengono scalati quando vengono aumentate le dimensioni del carattere.  
  
-   Icone fornite dal sistema o risorse in base alle metriche di sistema (ad esempio, SM_CXICON e SM_CXSMICON) sono già la scalabilità verticale.  
  
## <a name="older-win32-gdi-gdi-and-winforms-based-ui"></a>Win32 precedente (GDI, GDI+) e dell'interfaccia utente basata su Windows Form  
 Mentre WPF è ancora elevata compatibile con DPI, gran parte del codice basato su Win32/GDI non è stato scritto originariamente con il riconoscimento DPI presente. Windows ha fornito le API di ridimensionamento DPI. Correzioni dei problemi di Win32 devono essere considerati in modo uniforme per il prodotto. Visual Studio ha fornito un supporto di libreria di classi per evitare la duplicazione di funzionalità e verificare la coerenza tra il prodotto.  
  
## <a name="high-resolution-images"></a>Immagini ad alta risoluzione  
 In questa sezione è principalmente per gli sviluppatori di estendere Visual Studio 2013. Per Visual Studio 2015, utilizzare il servizio di immagine che viene compilato in Visual Studio. È inoltre possibile che si desidera supporto/destinazione molte versioni di Visual Studio e pertanto tramite il servizio immagini in 2015 non è un'opzione poiché non esiste nelle versioni precedenti. In questa sezione sarà anche per l'utente.  
  
## <a name="scaling-up-images-that-are-too-small"></a>L'aumento di immagini che sono troppo piccole  
 Le immagini che sono troppo ridotte possono essere "scalabilità" e sottoposto a rendering GDI e WPF tramite alcuni metodi comuni. Classi di helper DPI gestite sono disponibili per interni ed esterni integratori di Visual Studio all'indirizzo imagestrips, icone, bitmap e imagelists la scalabilità. Basate su Win32 nativo C / C++ helper sono disponibili per la scalabilità di ICONA, HBITMAP, HIMAGELIST e VsUI::GdiplusImage. Ridimensionamento di una bitmap in genere richiede solo una modifica di una riga dopo l'inclusione di un riferimento alla libreria di supporto. Ad esempio:  
  
```cpp  
(Unmanaged)  VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
```  
  
```csharp  
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);  
```  
  
 Scala il controllo imagelist varia a seconda se è stato completato in fase di caricamento, il componente imagelist o viene aggiunto in fase di esecuzione. Se in fase di caricamento è completo, chiamare LogicalToDeviceUnits() con il componente imagelist come una bitmap. Quando il codice deve caricare una bitmap singoli prima il componente imagelist di composizione, assicurarsi di ridimensionare le dimensioni dell'immagine di imagelist:  
  
```csharp  
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);  
```  
  
 Nel codice nativo, le dimensioni possono essere ridimensionate quando si crea il componente imagelist come indicato di seguito:  
  
```cpp  
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);  
```  
  
 Funzioni della libreria consentono di specificare l'algoritmo di ridimensionamento. Quando le immagini di scalabilità per essere inserito in imagelists, assicurarsi di specificare il colore di sfondo utilizzato per la trasparenza oppure utilizzare NearestNeighbor scalabilità (che altrimenti si verificherà distorsioni 125% e % 150).  
  
 Consultare la <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> documentazione su MSDN.  
  
 Nella tabella seguente mostra esempi di come le immagini devono essere scalate DPI corrispondente fattori di scala. Le immagini in verde indicano la procedura consigliata, a partire da Visual Studio 2013 (100-200% ridimensionamento DPI):  
  
 ![Problemi DPI-ridimensionamento](../extensibility/media/dpi-issues-scaling.png "problemi DPI-ridimensionamento")  
  
## <a name="layout-issues"></a>Problemi di layout  
 È possibile evitare problemi di layout comuni principalmente, mantenendo i punti nell'interfaccia utente ridimensionata e rispetto a un altro invece di percorsi assoluti (in particolare, in unità di pixel). Ad esempio:  
  
-   Posizioni di layout, testo necessario modificare l'account per le immagini con scalabilità verticale.  
  
-   Colonne nelle griglie devono avere larghezza regolata per il testo con scalabilità verticale.  
  
-   Dimensioni a livello di codice o spazio tra gli elementi sarà necessario per la scalabilità verticale. Le dimensioni che si basano solo le dimensioni del testo sono in genere un problema, perché i tipi di carattere vengono ridimensionati automaticamente.  
  
 Sono disponibili in funzioni di supporto di <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> classe per consentire la scalabilità sull'asse X e Y:  
  
-   LogicalToDeviceUnitsX/LogicalToDeviceUnitsY (funzioni consentono la scalabilità in X o asse Y)  
  
-   spazio int = DpiHelper.LogicalToDeviceUnitsX (10).  
  
-   altezza int = VsUI::DpiHelper::LogicalToDeviceUnitsY(5);  
  
 Esistono overload LogicalToDeviceUnits per consentire la scalabilità di oggetti, ad esempio Rect, punto e dimensioni.  
  
## <a name="using-the-dpihelper-libraryclass-to-scale-images-and-layout"></a>Utilizzo della libreria/classe DPIHelper per ridimensionare le immagini e il layout  
 La libreria di supporto di Visual Studio DPI è disponibile nei moduli nativi e gestiti e può essere utilizzata all'esterno di shell di Visual Studio da altre applicazioni.  
  
 Per utilizzare la libreria, passare al [esempi di estendibilità di Visual Studio VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) e clonare il codice di esempio elevata DPI_Images_Icons  
  
 Nel file di origine, includere VsUIDpiHelper.h e chiamare le funzioni statiche della classe VsUI::DpiHelper:  
  
```cpp  
#include "VsUIDpiHelper.h"  
  
int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);  
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
  
```  
  
> [!NOTE]
>  Non utilizzare le funzioni di supporto in variabili statiche a livello di modulo o a livello di classe. La libreria Usa anche elementi statici per la sincronizzazione dei thread e che possono verificarsi problemi di ordine-inizializzazione. Convertire tali elementi statici in variabili di membro non statiche oppure eseguire il wrapping in una funzione (in modo da ottenere costruite al primo accesso).  
  
 Per utilizzare le funzioni di supporto DPI da codice gestito che viene eseguita all'interno dell'ambiente Visual Studio:  
  
-   Il progetto utilizzato deve fare riferimento la versione più recente di MPF Shell. Ad esempio:  
  
    ```csharp  
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />  
    ```  
  
-   Verificare che il progetto contiene riferimenti a **Forms**, **PresentationCore**, e **PresentationUI**.  
  
-   Nel codice, utilizzare il **Microsoft.VisualStudio.PlatformUI** dello spazio dei nomi e chiamare funzioni statiche della classe DpiHelper. Per i tipi supportati (punti, dimensioni, rettangoli e così via), vengono fornite funzioni di estensione che restituiscono nuove ridimensionato oggetti. Ad esempio:  
  
    ```csharp  
    using Microsoft.VisualStudio.PlatformUI;  
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);  
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();  
    DpiHelper.LogicalToDeviceUnits(ref bitmap);  
  
    ```  
  
## <a name="dealing-with-wpf-image-fuzziness-in-zoomable-ui"></a>Gestione di tolleranza immagine WPF nell'interfaccia utente sul quale  
 In WPF, le bitmap vengono ridimensionate automaticamente da WPF per il livello di zoom DPI corrente mediante un algoritmo di alta qualità bicubica (impostazione predefinita), che funziona bene per immagini o schermate di grandi dimensioni, ma non è appropriata per le icone di voce di menu perché introduce confusa percepito .  
  
 Indicazioni:  
  
-   Per il logo banner e immagine grafica, il valore predefinito <xref:System.Windows.Media.BitmapScalingMode> può essere utilizzato in modalità di ridimensionamento.  
  
-   Per le voci di menu e le immagini visualizzato, il <xref:System.Windows.Media.BitmapScalingMode> deve essere utilizzato quando non causa di altri elementi di una distorsione eliminare confusa (in 200% e % 300).  
  
-   Per i livelli di zoom di grandi dimensioni non multipli di 100% (ad esempio, 250% o % 350), ridimensionamento di immagini visualizzato con Bicubica risultati nell'interfaccia utente fuzzy, sbiadito consentendo di riprodurre. Di ottenere risultati migliori prima scala un'immagine con NearestNeighbor al multiplo più grande del 100% (ad esempio, % 200 o 300%) e scalabilità con Bicubica da qui. Vedere caso speciale: prescaling immagini WPF per valori DPI elevato livelli per ulteriori informazioni.  
  
 La classe DpiHelper nello spazio dei nomi Microsoft.VisualStudio.PlatformUI fornisce un membro <xref:System.Windows.Media.BitmapScalingMode> che può essere utilizzato per l'associazione. Consentirà la shell di Visual Studio controllare la modalità ridimensionamento delle bitmap interno del prodotto in modo uniforme, in base al fattore di ridimensionamento DPI.  
  
 Per utilizzarlo in XAML, aggiungere:  
  
```xaml  
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
  
<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />  
  
```  
  
 La shell di Visual Studio già imposta questa proprietà in finestre di dialogo e finestre di primo livello. Interfaccia utente basato su WPF in esecuzione in Visual Studio verrà già ereditare. Se non si propaga l'impostazione per le parti dell'interfaccia utente specifici, è possibile impostare per l'elemento radice dell'interfaccia utente XAML/WPF. Posizioni in cui ciò si verifica includono i popup, per gli elementi con gli elementi padre Win32 e finestre di progettazione eseguiti da elaborare, come ad esempio Blend.  
  
 Un'interfaccia utente possono essere ridimensionati in modo indipendente dal livello di zoom DPI di sistema set, ad esempio l'editor di testo di Visual Studio e finestre di progettazione basate su WPF (Desktop WPF e Windows Store). In questi casi, DpiHelper.BitmapScalingMode non deve essere utilizzato. Per risolvere il problema nell'editor, il team IDE creato una proprietà personalizzata denominata RenderOptions.BitmapScalingMode. Impostare il valore della proprietà da riprodurre o NearestNeighbor a seconda del livello di zoom combinato del sistema e l'interfaccia utente.  
  
## <a name="special-case-prescaling-wpf-images-for-large-dpi-levels"></a>Caso speciale: prescaling immagini WPF per i livelli di grandi dimensioni DPI  
 Per i livelli di zoom molto elevato che non sono multipli di 100% (ad esempio, 250% 350% e così via), ridimensionamento di immagini visualizzato con risultati bicubica nell'interfaccia utente fuzzy, sbiadito consentendo di riprodurre. L'impressione di queste immagini con testo chiaro è quasi simile a quella di un effetto ottico. Le immagini vengono visualizzate a essere più vicina all'occhio e la messa a fuoco in relazione al testo. Il risultato della scalabilità queste dimensioni ingrandite può migliorare tramite l'adattamento con NearestNeighbor al multiplo più grande del 100% (ad esempio, % 200 o 300%) e scalabilità con Bicubica al resto (un ulteriore % 50).  
  
 Ecco un esempio delle differenze nei risultati, in cui la prima immagine viene ridimensionata con l'algoritmo di ridimensionamento doppia migliorato -> 100%, 200% -> 250%, e la seconda solo con Bicubica 100% -> % 250.  
  
 ![DPI problemi doppia esempio scalabilità](../extensibility/media/dpi-issues-double-scaling-example.png "DPI problemi esempio scalabilità Double")  
  
 Per abilitare l'interfaccia utente per utilizzare questa scalabilità doppia, markup XAML per la visualizzazione di ogni elemento immagine dovrà essere modificato. Nell'esempio seguente viene illustrato come utilizzare doppia scalabilità in WPF in Visual Studio usando la libreria DpiHelper e Shell.12/14.  
  
 Passaggio 1: Prescale l'immagine da % 200, 300% e così via utilizzando NearestNeighbor.  
  
 Prescale l'immagine utilizzando un convertitore di applicare un'associazione, o con un'estensione di markup XAML. Ad esempio:  
  
```xaml  
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />  
  
<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
  
<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />  
  
```  
  
 Se l'immagine sarà inoltre necessario applicare un tema (più, se non tutti, dovrebbe essere), il codice è possibile usare un convertitore di tipo diverso che esegue prima dei temi dell'immagine e quindi pre-scaling. Il markup può essere <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter> o <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter>, a seconda l'output di conversione desiderato.  
  
```xaml  
<vsui:DpiPrescaleThemedImageSourceConverter x:Key="DpiPrescaleThemedImageSourceConverter" />  
  
<Image Width="16" Height="16">  
  <Image.Source>  
    <MultiBinding Converter="{StaticResource DpiPrescaleThemedImageSourceConverter}">  
      <Binding Path="Icon" />  
      <Binding Path="(vsui:ImageThemingUtilities.ImageBackgroundColor)"    
               RelativeSource="{RelativeSource Self}" />  
      <Binding Source="{x:Static vsui:Boxes.BooleanTrue}" />  
    </MultiBinding>  
  </Image.Source>  
</Image>  
```  
  
 Passaggio 2: Verificare che le dimensioni finali sono corrette per la risoluzione corrente.  
  
 Poiché WPF verrà ridimensionato l'interfaccia utente per il DPI corrente utilizzando la proprietà BitmapScalingMode impostata su UIElement, un controllo immagine usando un'immagine prescaled come origine avrà un aspetto due o tre volte maggiore rispetto al necessario. Di seguito sono un paio di modi per contrastare questo effetto:  
  
-   Se si conosce la dimensione dell'immagine originale al 100%, è possibile specificare le dimensioni esatte del controllo immagine. Queste dimensioni riflette che la dimensione dell'interfaccia utente prima del ridimensionamento viene applicata.  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
    ```  
  
-   Se le dimensioni dell'immagine originale non sono noto, è possibile utilizzare un LayoutTransform scalare verso il basso l'oggetto immagine finale. Ad esempio:  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" >  
        <Image.LayoutTransform>  
         <ScaleTransform  
             ScaleX="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}"  
             ScaleY="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}" />  
        </Image.LayoutTransform>  
    </Image>  
    ```  
  
## <a name="enabling-hdpi-support-to-the-weboc"></a>Abilitazione del supporto HDPI per il WebOC  
 Per impostazione predefinita, i controlli di WebOC (ad esempio, il controllo WebBrowser in WPF, o l'interfaccia IWebBrowser2) non consentono il supporto e il rilevamento di HDPI. Il risultato sarà un controllo incorporato con il contenuto visualizzato è troppo piccolo su uno schermo ad alta risoluzione. Di seguito viene descritto come abilitare il supporto a DPI elevato in un'istanza di WebOC web specifico.  
  
 Implementare l'interfaccia IDocHostUIHandler (vedere l'articolo MSDN sul [IDocHostUIHandler](http://msdn.microsoft.com/library/aa753260.aspx) interface):  
  
```idl  
[ComImport, InterfaceType(ComInterfaceType.InterfaceIsIUnknown),  
 Guid("BD3F23C0-D43E-11CF-893B-00AA00BDCE1A")]  
public interface IDocHostUIHandler  
{  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int ShowContextMenu(  
        [In, MarshalAs(UnmanagedType.U4)] int dwID,  
        [In] POINT pt,  
        [In, MarshalAs(UnmanagedType.Interface)] object pcmdtReserved,  
        [In, MarshalAs(UnmanagedType.IDispatch)] object pdispReserved);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetHostInfo([In, Out] DOCHOSTUIINFO info);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int ShowUI(  
        [In, MarshalAs(UnmanagedType.I4)] int dwID,  
        [In, MarshalAs(UnmanagedType.Interface)] object activeObject,  
        [In, MarshalAs(UnmanagedType.Interface)] object commandTarget,  
        [In, MarshalAs(UnmanagedType.Interface)] object frame,  
        [In, MarshalAs(UnmanagedType.Interface)] object doc);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int HideUI();  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int UpdateUI();  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int EnableModeless([In, MarshalAs(UnmanagedType.Bool)] bool fEnable);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int OnDocWindowActivate([In, MarshalAs(UnmanagedType.Bool)] bool fActivate);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int OnFrameWindowActivate([In, MarshalAs(UnmanagedType.Bool)] bool fActivate);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int ResizeBorder(  
        [In] COMRECT rect,  
        [In, MarshalAs(UnmanagedType.Interface)] object doc,  
        bool fFrameWindow);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int TranslateAccelerator(  
        [In] ref MSG msg,  
        [In] ref Guid group,  
        [In, MarshalAs(UnmanagedType.I4)] int nCmdID);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetOptionKeyPath(  
        [Out, MarshalAs(UnmanagedType.LPArray)] string[] pbstrKey,  
        [In, MarshalAs(UnmanagedType.U4)] int dw);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetDropTarget(  
        [In, MarshalAs(UnmanagedType.Interface)] IOleDropTarget pDropTarget,  
        [MarshalAs(UnmanagedType.Interface)] out IOleDropTarget ppDropTarget);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetExternal([MarshalAs(UnmanagedType.IDispatch)] out object ppDispatch);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int TranslateUrl(  
        [In, MarshalAs(UnmanagedType.U4)] int dwTranslate,  
        [In, MarshalAs(UnmanagedType.LPWStr)] string strURLIn,  
        [MarshalAs(UnmanagedType.LPWStr)] out string pstrURLOut);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int FilterDataObject(  
        IDataObject pDO,  
        out IDataObject ppDORet);  
    }   
```  
  
 Facoltativamente, implementare l'interfaccia ICustomDoc (vedere l'articolo MSDN sul [ICustomDoc](http://msdn.microsoft.com/library/aa753272.aspx) interface):  
  
```idl  
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),  
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]  
public interface ICustomDoc  
{  
    void SetUIHandler(IDocHostUIHandler pUIHandler);  
}   
```  
  
 Associare la classe che implementa IDocHostUIHandler con il documento del WebOC. Se è implementato l'interfaccia ICustomDoc sopra riportata, come proprietà del documento del WebOC è valido, eseguirne il cast a un ICustomDoc e chiamare il metodo SetUIHandler, passando la classe che implementa IDocHostUIHandler.  
  
```csharp  
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface  
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;  
customDoc.SetUIHandler(this);  
  
```  
  
 Se si non implementa l'interfaccia ICustomDoc, quindi come proprietà del documento del WebOC è valido, è necessario eseguirne il cast a un oggetto IOleObject e chiamare il metodo SetClientSite, passando la classe che implementa IDocHostUIHandler. Imposta il flag DOCHOSTUIFLAG_DPI_AWARE il DOCHOSTUIINFO passato alla chiamata al metodo GetHostInfo:  
  
```csharp  
public int GetHostInfo(DOCHOSTUIINFO info)  
{  
    // This is what the default site provides.  
    info.dwFlags = (DOCHOSTUIFLAG)0x5a74012;  
    // Add the DPI flag to the defaults  
    info.dwFlags |=.DOCHOSTUIFLAG.DOCHOSTUIFLAG_DPI_AWARE;  
    return S_OK;  
}  
```  
  
 Deve trattarsi di tutto ciò che è necessario ottenere il controllo WebOC supporti HPDI.  
  
## <a name="tips"></a>Suggerimenti  
  
1.  Se la proprietà di documento nel controllo WebOC cambia, potrebbe essere necessario riassociare il documento con la classe IDocHostUIHandler.  
  
2.  Se la soluzione non funziona, sussiste un problema noto con il WebOC non prelievo per il flag DPI le modifiche. Il modo più affidabile di questa correzione è per attivare o disattivare lo zoom ottico di Web oC, due chiamate di significato con due valori diversi per la percentuale di zoom. Inoltre, se questa soluzione è necessaria, potrebbe essere necessario eseguirla in ogni chiamata di passare.  
  
    ```csharp  
    // browser2 is a SHDocVw.IWebBrowser2 in this case  
    // EX: Call the Exec twice with DPI%-1 and then DPI% as the zoomPercent values  
    IOleCommandTarget cmdTarget = browser2.Document as IOleCommandTarget;  
    if (cmdTarget != null)  
    {  
        object commandInput = zoomPercent;  
        cmdTarget.Exec(IntPtr.Zero,  
                       OLECMDID_OPTICAL_ZOOM,  
                       OLECMDEXECOPT_DONTPROMPTUSER,  
                       ref commandInput,  
                       ref commandOutput);  
    }  
    ```