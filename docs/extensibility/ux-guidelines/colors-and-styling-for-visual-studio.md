---
title: I colori e stili per Visual Studio | Documenti Microsoft
ms.custom: 
ms.date: 07/31/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 40e795238e46885707cfd6eff715a27a5f53f85c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="colors-and-styling-for-visual-studio"></a>I colori e stili per Visual Studio
## <a name="using-color-in-visual-studio"></a>Utilizzo di colore in Visual Studio  
In Visual Studio, colore viene utilizzato principalmente come strumento di comunicazione, non solo come effetto. Utilizza colore minima e riservarlo in situazioni in cui si desidera:  
  
-   Comunicare significato o associazione (ad esempio, i modificatori di piattaforma o linguaggio)  
  
-   Attirare l'attenzione (ad esempio, che indica una modifica di stato)  
  
-   Migliorare la leggibilità e specificare i punti di riferimento per lo spostamento dell'interfaccia utente  
  
-   Aumento delle opportunità  
  
Sono disponibili diverse opzioni per l'assegnazione di colori per gli elementi dell'interfaccia utente in Visual Studio. In alcuni casi può essere difficile per individuare quale opzione, è opportuno per utilizzare, o come usarlo in modo corretto. In questo argomento consentono di:  
  
1.  Comprendere i diversi servizi e sistemi utilizzati per definire i colori in Visual Studio.  
  
2.  Selezionare l'opzione corretto per un determinato elemento.  
  
3.  Utilizzare correttamente l'opzione scelto.  
  
> **Nota:** mai impostare come hardcoded esadecimale, RGB o colori di sistema per gli elementi dell'interfaccia utente. Utilizzo dei servizi consente una flessibilità tonalità di ottimizzazione. Inoltre, senza il servizio, non sarà in grado di sfruttare i vantaggi delle funzionalità di commutazione tema [il servizio VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).
  
### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Metodi per l'assegnazione di colori per gli elementi dell'interfaccia di Visual Studio  
Scegliere il metodo più adattato per gli elementi dell'interfaccia utente.  
  
| L'interfaccia utente | Metodo | Cosa sono? |  
| --- | --- | --- |  
| Non è stato incorporato o finestre di dialogo autonomo. | **Colori di sistema** | I nomi di sistema che consentono il sistema operativo definire il colore e l'aspetto degli elementi dell'interfaccia utente, quali controlli di finestra di dialogo comune. |
| Si dispone di un'interfaccia utente personalizzata che si desidera siano coerenti con l'ambiente di Visual Studio globale e si dispongono di elementi dell'interfaccia utente che corrispondono alla categoria e un significato semantico dei token condiviso. | **Colori condivisi comuni** | I nomi di token di colore predefiniti per specifici elementi dell'interfaccia utente esistente |
| Si dispone di un singole funzionalità o un gruppo di funzionalità e non è un colore non condiviso per gli elementi simili. | **Colori personalizzati** | Nomi di token di colore che sono specifici di un'area e non devono essere condivisa con altri dell'interfaccia utente |
| Si desidera consentire all'utente finale di personalizzare l'interfaccia utente o il contenuto (ad esempio, per gli editor di testo o le finestre di progettazione specifiche). | **Personalizzazione dell'utente finale**<br /><br />**(Strumenti &gt; finestra di dialogo Opzioni)** | Le impostazioni definite nella pagina di "Tipi di carattere e colori" il **strumenti &gt; opzioni** finestra di dialogo o una pagina specializzata specifica di una funzionalità dell'interfaccia utente. |
  
### <a name="visual-studio-themes"></a>Temi di Visual Studio  
Visual Studio dispone di tre temi di colore diverso: chiaro, scuro e blu. Verifica inoltre rileva la modalità contrasto elevato, ovvero una combinazione di colori di sistema progettata per l'accessibilità.  
  
Gli utenti viene richiesto di selezionare un tema durante il primo utilizzo di Visual Studio e sono in grado di scorrere i temi in un secondo momento, passare a **strumenti &gt; opzioni &gt; ambiente &gt; generale** e scegliendo un nuovo tema dal il menu a discesa "colori".  
  
Gli utenti possono inoltre utilizzare Pannello di controllo per alternare i relativi sistemi interi tema a contrasto elevato. Se un utente seleziona un tema a contrasto elevato, quindi il selettore del tema colori di Visual Studio non influenza più colori in Visual Studio, anche se tutte le modifiche al tema vengono salvate per quando l'utente esce dalla modalità a contrasto elevato. Per ulteriori informazioni sulla modalità a contrasto elevato, vedere [colori a contrasto elevato scelta](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors).
  
### <a name="the-vscolor-service"></a>Il servizio VSColor  
Visual Studio fornisce un servizio di colore di ambiente, noto come il servizio VSColor, che consente di associare i valori di colore degli elementi dell'interfaccia utente a una voce denominata contenente i valori di colore per ogni tema di Visual Studio. In questo modo si garantisce che i colori verranno modificate automaticamente per riflettere la corrente selezionate dall'utente del sistema o del tema modalità contrasto elevato. Utilizzo del servizio indica che l'implementazione di tutte le modifiche relative al tema di colore è gestito in un'unica posizione, e se si usano i colori condivisi comuni dal servizio, l'interfaccia utente verrà applicata automaticamente nuovi temi nelle versioni future di Visual Studio.  
  
### <a name="implementation"></a>Implementazione  
Il codice sorgente di Visual Studio include diversi file di definizione del pacchetto che contengono elenchi di nomi di token e i valori rispettivi per ogni tema. Il servizio di colore legge il VSColors definiti in questi file di definizione del pacchetto. Questi colori sono a cui fa riferimento nel markup XAML o nel codice e quindi caricati tramite il `IVsUIShell5.GetThemedColor` metodo o un mapping DynamicResource.  
  
### <a name="system-colors"></a>Colori di sistema  
Controlli comuni di fare riferimento i colori di sistema per impostazione predefinita. Se si desidera che l'interfaccia utente di utilizzare i colori di sistema, ad esempio quando si crea una finestra di dialogo incorporata o autonomo, è necessario eseguire alcuna operazione.  
  
### <a name="common-shared-colors-in-the-vscolor-service"></a>Colori condivisi comuni nel servizio VSColor  
Gli elementi di interfaccia devono riflettere l'ambiente di Visual Studio complessiva. Riutilizzando i colori condivisi comuni che sono appropriati per il componente dell'interfaccia utente per la creazione, verificare che l'interfaccia è coerenza con le altre interfacce di Visual Studio, e che i colori verranno aggiornati automaticamente quando i temi vengono aggiunti o aggiornati.  
  
Prima di usare colori condivisi comuni, assicurarsi di aver compreso come utilizzarle in modo corretto. Utilizzo non corretto di colori condivisi comuni potrebbe comportare un'esperienza incoerente, frustrante o confusione per gli utenti.  
  
### <a name="user-customizable-colors"></a>Colori personalizzabili  
Vedere: [esposizione di colori per gli utenti finali](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)  
  
In alcuni casi, è possibile consentire all'utente finale di personalizzare l'interfaccia utente, ad esempio, quando si crea un editor di codice o l'area di progettazione. Componenti dell'interfaccia utente personalizzabili si trovano nel **tipi di carattere e colori** sezione del **strumenti &gt; opzioni** finestra di dialogo, in cui gli utenti possono scegliere di modificare il colore primo piano, colore di sfondo o entrambi.  
  
![Strumenti &gt; finestra di dialogo Opzioni](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301 a_ToolsOptionsDialog")<br />Strumenti &gt; finestra di dialogo Opzioni
  
##  <a name="BKMK_TheVSColorService"></a>Il servizio VSColor  
Visual Studio fornisce un servizio di colore di ambiente, denominato anche il servizio VSColor o il colore della shell. Questo servizio consente di associare i valori di colore degli elementi dell'interfaccia utente a un set contenente i colori per ogni tema di colori nome-valore. Il servizio VSColor deve essere utilizzato per tutti gli elementi dell'interfaccia utente, in modo che i colori automaticamente modificati per riflettere il tema selezionato dall'utente corrente, in modo che l'interfaccia utente associato al servizio colori ambiente integrerà con nuovi temi nelle future versioni di Visual Studio.  
  
### <a name="how-the-service-works"></a>Funzionamento del servizio  
Il servizio colori ambiente legge che vscolors definito nel pkgdef per il componente dell'interfaccia utente. Questi VSColors viene quindi fatto riferimento nel markup XAML o nel codice e vengono caricati tramite il `IVsUIShell5.GetThemedColor` o `DynamicResource` mapping.  
  
![Architettura del servizio colori ambiente](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302 a_EnvironmentColorServiceArchitecture")<br />Architettura del servizio colori ambiente
  
### <a name="accessing-the-service"></a>L'accesso al servizio
Esistono diversi modi per utilizza il servizio VSColor, a seconda di quale tipo di colore i token di accesso e il tipo di codice si dispone.  

#### <a name="predefined-environment-colors"></a>Colori di ambiente predefinite  
  
##### <a name="from-native-code"></a>Dal codice nativo  
La shell fornisce un servizio che fornisce l'accesso per il `COLORREF` dei colori. L'interfaccia del servizio/è:  
  
```  
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)  
```  
  
Nel file VSShell80.idl, l'enumerazione `__VSSYSCOLOREX` con un colore di shell costanti. Per utilizzarlo, passato come il valore di indice uno dei valori di `enum __VSSYSCOLOREX` documentate in MSDN o un indice regolare numero di sistema Windows API, `GetSysColor`, accetta. Questa operazione consente di ottenere il valore RGB del colore che deve essere utilizzato nel secondo parametro.  
  
Se l'archiviazione di una penna o un pennello con un nuovo colore, è necessario `AdviseBroadcastMessages` (di fuori della shell di Visual Studio) e attendere `WM_SYSCOLORCHANGE` e `WM_THEMECHANGED` i messaggi.  
  
  
Per accedere al servizio di colore in codice nativo, si verrà effettuata una chiamata che è analogo al seguente: 

```
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);    
```  

> **Nota:** il `COLORREF` valori restituiti da `GetVSSysColorEx()` contengono solo R, G, componenti B di un colore del tema. Se una voce di tema usa la trasparenza, il valore del canale alfa viene eliminato prima della restituzione. Pertanto, se il colore di ambiente di interesse deve essere utilizzata in una posizione in cui il canale di trasparenza è importante, è necessario utilizzare `IVsUIShell5.GetThemedColor` anziché `IVsUIShell2::GetVSSysColorEx`, come descritto più avanti in questo argomento.  
  
##### <a name="from-managed-code"></a>Dal codice gestito  
Accedere al servizio VSColor attraverso il codice nativo è piuttosto semplice. Se si lavora tramite codice gestito, tuttavia, determinare la modalità di utilizzo del servizio può essere complessa. Tenendo presente, di seguito è un frammento di codice c# che illustra questo processo:  
  
```  
private void VSColorPaint(object sender, System.Windows.Forms.PaintEventArgs e)  
{  
    //getIVSUIShell2  
    IVsUIShell2 uiShell2 = Package.GetService(typeof(SVsUIShell)) as IVsUIShell2;  
    Debug.Assert (uiShell2 != null, "failed to get IVsUIShell2");  
  
    if (uiShell2 != null)  
    {  
        //get the COLORREF structure  
        uint win32Color;  
        uiShell.GetVSSysColorEx(VSSYSCOLOREX.VSCOLOR_SMARTTAG_HOVER_FILL, out win32Color);  
  
        //translate it to a managed Color structure  
        Color myColor = ColorTranslator.FromWin32((int)win32Color);  
        //use it  
        e.Graphics.FillRectangle(new SolidBrush(myColor), 0, 0, 100, 100);  
    }  
}  
```  
  
Se si lavora in Visual Basic, utilizzare:  
  
```  
Dim myColor As Color = ColorTranslator.FromWin32((Integer)win32Color)  
```  
  
##### <a name="from-wpf-ui"></a>Nell'interfaccia utente WPF  
È possibile associare ai colori di Visual Studio tramite valori esportati all'applicazione `ResourceDictionary`. Di seguito è riportato un esempio di utilizzo delle risorse della tabella di colore, così come l'associazione ai dati di tipo di carattere ambiente in XAML.  
  
```  
<Style TargetType="{x:Type Button}">  
    <Setter Property="TextBlock.FontFamily"  
            Value="{DynamicResource VsFont.EnvironmentFontFamily}" />  
    <Setter Property="TextBlock.FontSize"  
            Value="{DynamicResource VsFont.EnvironmentFontSize}" />  
    <Setter Property="Background"  
            Value="{DynamicResource VsBrush.EnvironmentBackgroundGradient}" />  
</Style>  
```  
  
#### <a name="helper-classes-and-methods-for-managed-code"></a>Classi di supporto e i metodi per il codice gestito  
Per il codice gestito, libreria Managed Package Framework della shell (`Microsoft.VisualStudio.Shell.12.0.dll`) contiene un paio di classi helper agevolare l'utilizzo di temi colori.  
  
I metodi di supporto nel `Microsoft.VisualStudio.Shell.VsColors` classe MPF includono `GetThemedGDIColor()` e `GetThemedWPFColor()`. Tali metodi helper restituisce il valore di colore di una voce di tema come `System.Drawing.Color` o `System.Windows.Media.Color`, da usare in Windows Form o UI di WPF.  
  
```  
IVsUIShell5 shell5;  
Button button = new Button();  
button.BackColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemBrushKey);  
button.ForeColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemTextBrushKey);  
  
/// <summary>  
/// Gets a System.Drawing.Color value from the current theme for the given color key.  
/// </summary>  
/// <param name="vsUIShell">The IVsUIShell5 service, used to get the color's value.</param>  
/// <param name="themeResourceKey">The key to find the color for.</param>  
/// <returns>The current theme's value of the named color.</returns>  
public static System.Drawing.Color GetThemedGDIColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)  
{  
   Validate.IsNotNull(vsUIShell, "vsUIShell");  
   Validate.IsNotNull(themeResourceKey, "themeResourceKey");  
  
   byte[] colorComponents = GetThemedColorRgba(vsUIShell, themeResourceKey);  
  
   // Note: The Win32 color we get back from IVsUIShell5.GetThemedColor is ABGR  
   return System.Drawing.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]);  
}  
  
private static byte[] GetThemedColorRgba(IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)  
{  
   Guid category = themeResourceKey.Category;  
   __THEMEDCOLORTYPE colorType = __THEMEDCOLORTYPE.TCT_Foreground  
   if (themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundColor || themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundBrush)  
   {  
      colorType = __THEMEDCOLORTYPE.TCT_Background;  
   }  
  
   // This call will throw an exception if the color is not found  
   uint rgbaColor = vsUIShell.GetThemedColor(ref category, themeResourceKey.Name, (uint)colorType);  
   return BitConverter.GetBytes(rgbaColor);  
}  
public static System.Windows.Media.Color GetThemedWPFColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)  
{  
   Validate.IsNotNull(vsUIShell, "vsUIShell");  
   Validate.IsNotNull(themeResourceKey, "themeResourceKey");  
  
   byte[] colorComponents = GetThemedColorComponents(vsUIShell, themeResourceKey);  
  
    return System.Windows.Media.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]);  
}    
```  
  
La classe inoltre utilizzabile per ottenere gli identificatori VSCOLOR per una chiave di risorsa colore specifico di WPF, o viceversa.  
  
```  
public static string GetColorBaseKey(int vsSysColor);  
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);  
```  
  
I metodi di `VsColors` classe di eseguire query sul servizio VSColor per restituire il valore di colore ogni volta che vengono richiamati. Per ottenere un valore di colore come `System.Drawing.Color`, alternativa con prestazioni migliori, è possibile usare invece i metodi del `Microsoft.VisualStudio.PlatformUI.VSThemeColor` (classe), che memorizza nella cache i valori di colore ottenuti dal servizio VSColor. La classe internamente sottoscrive gli eventi di messaggi trasmessi shell e ignora il valore memorizzato nella cache quando si verifica un evento di modifica del tema. Inoltre, la classe fornisce un. Evento NET adatti per sottoscrivere modifiche al tema. Utilizzare il `ThemeChanged` evento da aggiungere un nuovo gestore e utilizzare il `GetThemedColor()` per ottenere colore i valori per il `ThemeResourceKeys` di interesse. Un codice di esempio potrebbe essere simile al seguente:  
  
```  
public MyWindowPanel()  
{  
    InitializeComponent();  
  
    // Subscribe to theme changes events so we can refresh the colors  
    VSColorTheme.ThemeChanged += VSColorTheme_ThemeChanged;  
  
    RefreshColors();  
}  
  
private void VSColorTheme_ThemeChanged(ThemeChangedEventArgs e)  
{  
    RefreshColors();  
  
    // Also post a message to all the children so they can apply the current theme appropriately  
    foreach (System.Windows.Forms.Control child in this.Controls)  
    {  
        NativeMethods.SendMessage(child.Handle, e.Message, IntPtr.Zero, IntPtr.Zero);  
    }  
}  
  
private void RefreshColors()  
{  
    this.BackColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowBackgroundColorKey);  
    this.ForeColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowTextColorKey);  
}  
  
protected override void Dispose(bool disposing)  
{  
    if (disposing)  
    {  
        VSColorTheme.ThemeChanged -= this.VSColorTheme_ThemeChanged;  
        base.Dispose(disposing);}  
}  
```  
  
##  <a name="BKMK_ChoosingHighContrastColors"></a>Scelta di colori a contrasto elevato  
  
### <a name="overview"></a>Panoramica  
Windows Usa diversi temi a livello di sistema di contrasto elevato che aumentare il contrasto di colore del testo, sfondi e immagini, visualizzando gli elementi più distinta sullo schermo. Per motivi di accessibilità, è importante che gli elementi dell'interfaccia di Visual Studio rispondono correttamente quando gli utenti passano a un tema a contrasto elevato.  
  
Solo un numero limitato di colori di sistema può essere utilizzato per i temi di contrasto elevato. Quando si sceglie il sistema di nomi di colore, tenere presenti i suggerimenti seguenti:  
  
1.  **Scegliere i colori di sistema che hanno lo stesso significato semantico** come l'elemento che è colorazione. Ad esempio, se si sceglie un colori a contrasto elevato per il testo all'interno di una finestra, utilizzare WindowText e non ControlText.  
  
2.  **Scegliere le coppie di primo piano/sfondo** insieme o non sarà certi che il colore scelto funzionerà in tutti i temi di contrasto elevato.  
  
3.  **Determinare quali parti dell'interfaccia utente sono quelli più importanti e assicurarsi che le aree di contenuto verranno evidenziati.** Si perderà numerosi dettagli che normalmente verrebbero distinguere i lievi differenze in tonalità di colore, pertanto l'utilizzo di colori del bordo sicuro è comune per definire le aree di contenuto, poiché non esistono alcun varianti di colore per diverse aree di contenuto.  
  
### <a name="system-color-set"></a>Set di colori di sistema  
La tabella in [Blog del Team WPF: riferimento SystemColors](http://blogs.msdn.com/b/wpf/archive/2010/11/30/systemcolors-reference.aspx) indica il set completo di nomi di colori di sistema e le corrispondenti tonalità visualizzate in ogni tema.  
  
Quando l'applicazione di questo set di colori per l'interfaccia utente, limitato *è previsto che si perderanno dettagli presenti nei temi "normali"*. Di seguito è riportato un esempio dell'interfaccia utente con colori grigio minimi che consentono di distinguere le aree all'interno di una finestra degli strumenti. Quando viene utilizzata con la stessa finestra visualizzata in modalità a contrasto elevato, è possibile visualizzare tutti gli sfondi vengono la stessa tonalità che i bordi di tali aree sono indicati con bordo solo:  
  
![Esempio di come dettagli vengono perse in contrasto elevato](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303 a_PropertiesWindow")<br />Esempio di come dettagli vengono perse in contrasto elevato
  
#### <a name="choosing-text-colors-in-an-editor"></a>Scelta di colori del testo in un editor  
Testo colorato viene utilizzato in un editor o in un'area di progettazione per indicare un significato, ad esempio consentire l'identificazione immediata dei gruppi di elementi simili. Un tema a contrasto elevato, tuttavia, non è la possibilità di distinguere tra più di tre colori del testo. WindowText, GrayText e HotTrackText sono i colori soli disponibili nelle aree WindowBackground. Poiché non è possibile utilizzare più di tre colori, scegliere con attenzione le differenze più importanti che si desidera visualizzare in modalità a contrasto elevato.  
  
Tonalità per ognuno dei nomi di token è consentiti in una superficie dell'editor, come appaiono in ogni tema a contrasto elevato:  
  
![Confronto di editor a contrasto elevato](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303 b_HCEditorComparison")<br />Confronto di editor a contrasto elevato
  
Esempi dell'area di editor del tema blu:  
  
![Editor con tema blu](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303 c_EditorBlue")<br />Editor con tema blu
  
![Editor con tema a contrasto elevato #1](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303 d_EditorHC1")<br />Editor con tema a contrasto elevato #1
  
### <a name="usage-patterns"></a>Modelli di utilizzo
Molti elementi dell'interfaccia utente comuni sono già definiti colori a contrasto elevato. È possibile fare riferimento questi modelli di utilizzo quando si sceglie un sistema di nomi di colori in modo che gli elementi dell'interfaccia utente sono coerenti con i componenti simili.  
  
| Colore di sistema | Utilizzo |
| --- | --- |
| ActiveCaption | -Active IDE e icone di finestra rafted pulsante al passaggio del mouse e premere<br />-Sfondo della barra del titolo per IDE e rafted windows<br />-Sfondo della barra di stato predefinito |
| ActiveCaptionText | -Active IDE e rafted windows per il colore della barra del titolo (testo e icone)<br />-In background e il bordo dei pulsanti finestra attiva nel passaggio del mouse e premere |
| Control | -Casella combinata elenco a discesa e ricerca controllare l'impostazione predefinita e in background, incluso il pulsante di menu a discesa disabilitato<br />-Lo sfondo di pulsante di ancoraggio destinazione<br />-Sfondo della barra dei comandi<br />-Sfondo della finestra strumento |
| ControlDark | -Sfondo IDE<br />-Menu e comandi il separatore barra<br />: Bordo barra dei comandi<br />-Shadows menu<br />-Strumento bordo predefinito e al passaggio del mouse sulla scheda della finestra e il separatore<br />-Documento e lo sfondo di pulsante di overflow<br />-Bordo glifo di ancoraggio destinazione |
| ControlDarkDark |Finestra della scheda di documento con stato non attivo e selezionato |
| ControlLight |-Bordo sottoscheda Nascondi automaticamente<br />-Bordo dell'elenco combinata casella e l'elenco a discesa<br />-Ancorare bordo e uno sfondo di destinazione |
| ControlLightLight | -Bordo provvisorio selezionata, con stato attivo |
| ControlText | -Icona di elenco combinata casella e l'elenco a discesa<br />-Testo scheda della finestra deselezionato strumento |
| GrayText |-Casella combinata e l'elenco a discesa disabilitato bordo, elenco a discesa glifo, testo e testo voce di menu<br />-Testo del menu disabilitato<br />-Testo dell'intestazione 'opzioni di ricerca' ricerca controllo<br />-Separatore di sezione ricerca controllo |
| Evidenziazione | -Tutti al passaggio del mouse e gli sfondi premuti e i bordi, ad eccezione di combinata casella pulsante a discesa sfondo e del documento e di overflow bordo del pulsante<br />-Sfondi elemento |
| HighlightText | -Tutti al passaggio del mouse e premuti primi piani (testo e icone)<br />-Strumento mirati documento e finestra Scheda finestra controllo in primo piano<br />-Bordo barra del titolo della finestra di strumento con lo stato attivo<br />-In primo piano con lo stato attivo, selezionato scheda provvisoria<br />-Bordo del pulsante documento e di overflow al passaggio del mouse e premere<br />-Bordo dell'icona selezionato|
| HotTrack | -Barra scorrimento sfondo thumb e bordo premere<br />-Barra di scorrimento icona freccia in premere |
| InactiveCaption | -IDE inattivo e icone di finestra rafted pulsante al passaggio del mouse<br />-Sfondo della barra del titolo per IDE e rafted windows<br />-Sfondo del controllo ricerca disabilitato |
| InactiveCaptionText | -IDE inattivi e in primo piano sulla barra del titolo windows rafted (testo e icone)<br />-Sfondo pulsanti inattiva e il bordo al passaggio del mouse<br />-Bordi e sfondo pulsante della finestra dello strumento con stato non attivo<br />-Primo piano di controllo di ricerca disabilitato |
| Menu | Elenco a discesa dello sfondo del menu<br />-Segno di spunta selezionata e disabilitata sfondo |
| MenuText | -Bordo del menu elenco a discesa<br />-I segni di spunta<br />-Icone menu<br />-Testo del menu elenco a discesa<br />-Bordo dell'icona selezionato |  
| Barra di scorrimento | -Scorri barra e barra background freccia, tutti gli stati di scorrimento |
| Window | Nascondi automaticamente in background di scheda<br />-Menu barra e sfondo scaffale dei comandi<br />-Bordo del documento, per le schede provvisorie sia aperte e sfondo della scheda della finestra documento selezionato o con stato non attivo<br />-Sfondo della barra del titolo finestra strumento con stato non attivo<br />-Strumento scheda sfondo della finestra, sia selezionati e deselezionati |
| WindowFrame | -Bordo IDE |
| WindowText | -In primo piano della scheda Nascondi automaticamente<br />-In primo piano della scheda di finestra strumento selezionato<br />Scheda della finestra di documento con stato non attivo e in primo piano selezionato o con stato non attivo scheda provvisoria<br />-Ad albero in primo piano predefinito di visualizzazione e al passaggio del mouse sull'icona non selezionato<br />-Bordo sottoscheda selezionato finestra<br />-Barra di scorrimento sfondo thumb, bordo e del glifo |
  
##  <a name="BKMK_ExposingColorsForEndUsers"></a>Esposizione di colori per gli utenti finali  
  
### <a name="overview"></a>Panoramica  
Talvolta si desidera consentire all'utente finale di personalizzare l'interfaccia utente, ad esempio, quando si crea un editor di codice o l'area di progettazione. È il modo più comune per eseguire questa operazione utilizzando il **strumenti &gt; opzioni** finestra di dialogo. A meno che non si dispone di elevata specializzati dell'interfaccia utente che richiede controlli speciali, il modo più semplice per presentare la personalizzazione è tramite il **tipi di carattere e colori** pagina all'interno di **ambiente** sezione della finestra di dialogo. Per ogni elemento che espone per la personalizzazione, l'utente può scegliere di modificare il colore primo piano, colore di sfondo o entrambi.

### <a name="building-a-vspackage-for-your-customizable-colors"></a>La creazione di un pacchetto VSPackage per i colori personalizzabili  
Un pacchetto VSPackage può controllare i tipi di carattere e colori tramite categorie personalizzate e visualizzare gli elementi nella pagina delle proprietà dei tipi di carattere e colori. Quando si utilizza questo meccanismo, i pacchetti VSPackage devono implementare il [IVsFontAndColorDefaultsProvider](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.aspx) interfaccia e le relative interfacce associate.  
  
In sostanza, questo meccanismo può essere utilizzato per modificare tutti gli elementi di visualizzazione esistente e le categorie che li contengono. Tuttavia, e non deve essere utilizzato per modificare la categoria Editor di testo o i relativi elementi visualizzati. Per ulteriori informazioni sulla categoria di Editor di testo, vedere [tipo di carattere e colore Panoramica](../font-and-color-overview.md).  
  
Per implementare le categorie personalizzate o visualizzare gli elementi, un pacchetto VSPackage deve:  
  
-   **Creare o identificare categorie nel Registro di sistema.** Implementazione dell'IDE del **tipi di carattere e colori** pagina delle proprietà utilizza queste informazioni per eseguire correttamente le query per il servizio supporta una determinata categoria.  
  
-   **Creare o identificare i gruppi nel Registro di sistema (facoltativo).** Potrebbe essere utile definire un gruppo che rappresenta l'unione di due o più categorie. Se viene definito un gruppo, l'IDE automaticamente unisce le sottocategorie e distribuisce gli elementi di visualizzazione all'interno del gruppo.  
  
-   **Implementazione del supporto IDE.**  
  
-   **Gestire le modifiche di carattere e colori.**  
  
#### <a name="to-create-or-identify-categories"></a>Per creare o identificare categorie  
Creare un tipo speciale di voce del Registro di sistema categoria `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<Category\>]` dove `<Category>` è il nome non localizzato della categoria.
  
Popolare il Registro di sistema con due valori:  

| nome | Tipo | Dati | Descrizione |
| --- | --- | --- | --- |
| Category | REG_SZ | GUID | Creato da un GUID per identificare la categoria |
| Pacchetto | REG_SZ | GUID | Il GUID del servizio che supporta la categoria di VSPackage |
  
 Il servizio specificato nel Registro di sistema deve fornire un'implementazione di [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) per la categoria corrispondente.  
  
#### <a name="to-create-or-identify-groups"></a>Per creare o identificare i gruppi  
Creare un tipo speciale di voce del Registro di sistema categoria `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<group\>]` dove `<group>` è il nome non localizzato del gruppo.  
  
Popolare il Registro di sistema con due valori:

| nome | Tipo | Dati | Descrizione |
|--- | --- | --- | --- |
| Category | REG_SZ | GUID | Creato da un GUID per identificare la categoria |
| Pacchetto | REG_SZ | GUID | Il GUID del servizio che supporta la categoria di VSPackage |
  
Il servizio specificato nel Registro di sistema deve fornire un'implementazione di `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` per il gruppo corrispondente.

![Implementazione dell'interfaccia IVsFontAndColorGroup](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304 a_FontAndColorGroup")<br />Implementazione di`IVsFontAndColorGroup`
  
### <a name="to-implement-ide-support"></a>Per implementare il supporto IDE  
Implementare [GetObject](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject.aspx), che restituisce un [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) interfaccia o un `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` all'IDE per ciascuna categoria di interfaccia o un gruppo GUID specificato.  
  
Per ogni categoria supporta un pacchetto VSPackage implementa un'istanza separata del [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) interfaccia.  
  
I metodi implementati tramite [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) deve fornire l'IDE con:  
  
-   Elenchi di elementi visualizzati nella categoria  
  
-   Nomi localizzabili per gli elementi di visualizzazione  
  
-   Visualizzare le informazioni per ogni membro della categoria  
  
 > **Nota:** ogni categoria deve contenere almeno un elemento di visualizzazione.
  
L'IDE Usa il `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` interfaccia per definire un'unione di diverse categorie.

L'implementazione fornisce l'IDE con:

-   Un elenco di categorie che costituiscono un gruppo specifico  
  
-   Accesso alle istanze del [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) ogni categoria all'interno del gruppo di supporto  
  
-   Nomi dei gruppi localizzabile  
  
#### <a name="updating-the-ide"></a>L'aggiornamento dell'IDE  
L'IDE memorizza nella cache di informazioni sulle impostazioni di carattere e colori. Dopo qualsiasi modifica della configurazione di IDE carattere e colori, garantendo che la cache viene aggiornata di conseguenza, è consigliabile.  
  
Aggiornamento della cache viene eseguita tramite il [IvsFontAndColorCacheManager](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) l'interfaccia e può essere eseguita a livello globale o solo in elementi.  
  
### <a name="handling-font-and-color-changes"></a>Gestione delle modifiche di carattere e colori  
Per supportare correttamente la colorazione di testo che visualizza un VSPackage, il servizio di colorazione supporta il pacchetto VSPackage deve rispondere alle modifiche apportate tramite la pagina delle proprietà di tipi di carattere e colori avviata dall'utente.  
  
A tale scopo, un pacchetto VSPackage deve:  
  
-   **gestire gli eventi generati IDE** implementando il [IVsFontAndColorEvents](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.aspx) interfaccia. L'IDE chiama il metodo appropriato dopo le modifiche apportate dall'utente della pagina tipi di carattere e colori. Ad esempio, chiama il [OnFontChanged](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged.aspx) metodo se si seleziona un nuovo tipo di carattere.  
  
 **OR**  
  
-   **eseguire il polling dell'IDE per le modifiche**. Questo può avvenire tramite implementato dal sistema [IVsFontAndColorStorage](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) interfaccia. Sebbene principalmente per il supporto di persistenza, il [GetItem](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem.aspx) metodo possibile ottenere informazioni di carattere e colori per gli elementi di visualizzazione. Per ulteriori informazioni sulle impostazioni di carattere e colori, vedere l'articolo MSDN [accesso archiviati tipo di carattere e le impostazioni dei colori](../accessing-stored-font-and-color-settings.md).  
  
> **Nota:** per assicurarsi che il polling risultati siano corretti, usare il [IVsFontAndColorCacheManager](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) interfaccia per determinare se sono necessari un scaricamento della cache e l'aggiornamento prima di chiamare i metodi di recupero del [ IVsFontAndColorStorage](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) interfaccia.
  
#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>Registrazione del carattere e colore categoria senza implementare interfacce  
Esempio di codice riportato di seguito viene illustrato come registrare il tipo di carattere personalizzato e il colore di categoria senza l'implementazione di interfacce:  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]  
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"  
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"  
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"  
  
    "NameID"=dword:00000064  
```  

In questo esempio di codice:   
-   `"NameID"`= l'ID di risorsa del nome della categoria localizzata nel pacchetto
-   `"ToolWindowPackage"`= GUID del pacchetto
-   `"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"`è solo un esempio e il valore effettivo può essere un nuovo GUID fornito dall'implementatore.  
  
### <a name="set-the-font-and-color-property-category-guid"></a>Impostare il tipo di carattere e colore proprietà GUID di categoria  
Esempio di codice seguente viene illustrata l'impostazione di GUID di categoria.  
  
```  
// m_pView is your IVsTextView  
IVsTextEditorPropertyCategoryContainer spPropCatContainer =  
(IVsTextEditorPropertyCategoryContainer)m_pView;  
if (spPropCatContainer != null)  
{  
IVsTextEditorPropertyContainer spPropContainer;  
Guid GUID_EditPropCategory_View_MasterSettings =  
new Guid("{D1756E7C-B7FD-49a8-B48E-87B14A55655A}");  
hr = spPropCatContainer.GetPropertyCategory(  
ref GUID_EditPropCategory_View_MasterSettings,  
out spPropContainer);  
if(hr == 0)  
{  
hr =  
spPropContainer.SetProperty(  
VSEDITPROPID.VSEDITPROPID_ViewGeneral_FontCategory,  
catGUID);  
hr =  
spPropContainer.SetProperty(  
VSEDITPROPID.VSEDITPROPID_ViewGeneral_ColorCategory,  
catGUID);  
}  
}  
```  
