---
title: Tipi di carattere e la formattazione per Visual Studio | Documenti Microsoft
ms.custom: 
ms.date: 04/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fcd6b5edd5d0c6724ca7ed1e393e32d657a4a29b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="fonts-and-formatting-for-visual-studio"></a>Tipi di carattere e la formattazione per Visual Studio
##  <a name="BKMK_TheEnvironmentFont"></a>Il tipo di carattere ambiente  
 Tutti i tipi di carattere all'interno di Visual Studio deve essere esposto all'utente per la personalizzazione. Ciò avviene principalmente attraverso il **tipi di carattere e colori** nella pagina il **strumenti > Opzioni** finestra di dialogo. Le tre categorie principali di impostazioni dei caratteri sono:  
  
-   **Tipo di carattere ambiente** -il tipo di carattere primario per l'ambiente IDE (ambiente di sviluppo integrato), utilizzato per tutti gli elementi di interfaccia, incluse le finestre di dialogo, menu, finestre degli strumenti e finestre di documento. Per impostazione predefinita, il tipo di carattere ambiente è correlato a un tipo di carattere di sistema che viene visualizzato come 9 punti Segoe UI nelle versioni correnti di Windows. Utilizzo di un tipo di carattere per tutti gli elementi di interfaccia contribuisce a garantire un aspetto coerente del carattere dell'IDE.  
  
-   **Editor di testo** -pagina elementi che superficie di attacco nel codice e altri editor basati su testo può essere personalizzato nell'Editor di testo **strumenti > Opzioni**.  
  
-   **Raccolte specifiche** -finestre di progettazione che offrono personalizzazione dell'utente dei relativi elementi di interfaccia può esporre tipi di carattere specifici alla progettazione superficie di attacco nella propria pagina delle impostazioni in **strumenti > Opzioni**.  
  
### <a name="editor-font-customization-and-resizing"></a>Personalizzazione di editor di tipo di carattere e il ridimensionamento  
 Utenti spesso verranno allargare o ingrandire le dimensioni e/o il colore del testo nell'editor in base alle loro preferenze, indipendente dell'interfaccia utente generali. Poiché il tipo di carattere ambiente viene utilizzato per gli elementi che potrebbero essere visualizzati all'interno o come parte di un editor o la finestra di progettazione, è importante notare il comportamento previsto quando una di queste classificazioni di tipo di carattere viene modificata.  
  
 Durante la creazione di elementi dell'interfaccia utente che vengono visualizzati nell'editor, ma sono non fa parte di *contenuto*, è importante utilizzare il tipo di carattere ambiente e non il tipo di carattere, in modo da elementi ridimensionati in modo prevedibile.  
  
1.  Per il testo nell'editor di codice, ridimensionare con l'impostazione del tipo di carattere testo codice e rispondere a livello di zoom del testo dell'editor.  
  
2.  Tutti gli altri elementi dell'interfaccia devono essere collegati al tipo di carattere ambiente e riflettere le modifiche nell'ambiente globale. Questo include (ma non limitato a):  
  
    -   Testo nel menu di scelta rapida  
  
    -   Testo in un'area di controllo dell'editor, come testo del menu lampadina, riquadro dell'editor di ricerca veloce e passare al riquadro  
  
    -   Etichetta di testo nelle finestre di dialogo, ad esempio **Cerca nei file** o **effettuare il refactoring**  
  
### <a name="accessing-the-environment-font"></a>L'accesso il tipo di carattere ambiente  
 Nel codice nativo o Windows Form, il tipo di carattere ambiente è possibile accedere tramite la chiamata al metodo `IUIHostLocale::GetDialogFont` dopo l'esecuzione di query l'interfaccia di `SID_SUIHostLocale` servizio.  
  
 Per Windows Presentation Foundation (WPF), derivare la classe di finestra di dialogo della shell `DialogWindow` classe anziché di WPF `Window` classe.  
  
 In XAML, il codice simile al seguente:  
  
```  
<ui:DialogWindow  
    x:Class"MyNameSpace.MyWindow"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:s="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:ui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.11.0"  
    ShowInTaskbar="False"  
    WindowStartupLocation="CenterOwner"  
    Title="My Dialog">  
</ui:DialogWindow>  
  
code behind:  
  
internal partial class WebConfigModificationWindow : DialogWindow  
{  
}  
```  
  
 (Sostituire `Microsoft.VisualStudio.Shell.11.0` con la versione corrente della dll MPF.)  
  
 Per visualizzare la finestra di dialogo, chiamare "`ShowModal()`" nella classe su `ShowDialog()`. `ShowModal()`Imposta lo stato modale corretto nella shell di, assicura che la finestra di dialogo viene centrata in una finestra padre e così via.  
  
 Il codice è indicato di seguito:  
  
```  
MyWindow window = new MyWindow();  
window.ShowModal()  
```  
  
 `ShowModal`Restituisce un valore bool? (valore booleano che ammette valori null) con il `DialogResult`, che può essere utilizzato se necessario. Il valore restituito è true se è stata chiusa la finestra di dialogo con **OK**.  
  
 Se è necessario visualizzare alcuni UI WPF non è una finestra di dialogo che è ospitato nel proprio `HwndSource`, ad esempio una finestra popup o una finestra figlio WPF di una finestra padre di Win32/Windows Form, è necessario impostare il `FontFamily` e `FontSize` per l'elemento radice di WPF e lemento. (La shell imposta le proprietà nella finestra principale, ma verranno ereditate non oltre un `HWND`). La shell fornisce risorse a cui possono essere associate le proprietà e simile al seguente:  
  
```  
<Setter property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" />  
<Setter property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />  
```  
  
###  <a name="BKMK_Formatting"></a>Formattazione di riferimento (scalabilità/grassetto)  
 Alcune finestre di dialogo richiedono particolare testo in grassetto o una dimensione diverso dal tipo di carattere ambiente. In precedenza, i tipi di carattere maggiori di tipo di carattere ambiente fosse codificate come "`environment font +2`" o simile. Utilizzo dei frammenti di codice fornito supporterà schermi ad alta risoluzione e verificare che il testo di visualizzazione viene sempre visualizzata nel server di dimensioni corrette e peso (ad esempio, chiaro o Semilight).  
  
> **Nota: Prima di applicare la formattazione, verificare che si sta seguendo le linee guida fornite in [lo stile del testo](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).**  
  
 Per ridimensionare il tipo di carattere ambiente, impostare lo stile del controllo TextBlock o etichetta come indicato. Ognuno di questi frammenti di codice, se usati correttamente, verrà generato il tipo di carattere corretto, tra cui le variazioni di dimensioni e peso appropriate.  
  
 Dove "`vsui`" è un riferimento allo spazio dei nomi `Microsoft.VisualStudio.Shell`:  
  
```  
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0" 
```  
  
#### <a name="375-environment-font--light"></a>Tipo di carattere ambiente 375% + Light  
 **Viene visualizzato come:** pt 34 Segoe UI Light  
 **Utilizzo per:** (raro) univoco personalizzazione dell'interfaccia utente, ad esempio nella pagina iniziale

 **Codice procedurale:** in `textBlock` è definita in precedenza TextBlock e `label` è un'etichetta definita in precedenza:  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);  
```  
  
 **XAML:** impostare lo stile del controllo TextBlock o etichetta, come illustrato.  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>  
```  
  
#### <a name="310-environment-font--light"></a>Tipo di carattere ambiente 310% + Light  
 **Viene visualizzato come:** pt 28 Segoe UI Light   
 **Utilizzo per:** titoli di finestra di dialogo firma di grandi dimensioni, la voce report principali  
  
 **Codice procedurale:** in `textBlock` è definita in precedenza TextBlock e `label` è un'etichetta definita in precedenza:  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);    
```  
  
 **XAML:** impostare lo stile del controllo TextBlock o etichetta, come illustrato.  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>     
```  
  
#### <a name="200-environment-font--semilight"></a>Tipo di carattere ambiente 200% + Semilight  
 **Viene visualizzato come:** 18 pt Segoe UI Semilight    
 **Utilizzo per:** sottotitoli, i titoli di finestre di dialogo di piccole e medie dimensioni  
  
 **Codice procedurale:** in `textBlock` è definita in precedenza TextBlock e `label` è un'etichetta definita in precedenza: 
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);    
```  
  
 **XAML:** impostare lo stile del controllo TextBlock o etichetta, come illustrato:  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>    
```  
  
#### <a name="155-environment-font"></a>Tipo di carattere ambiente 155%  
 **Viene visualizzato come:** 14 pt Segoe UI    
 **Utilizzo per:** intestazioni delle sezioni nel documento e dell'interfaccia utente o report  
  
 **Codice procedurale:** in `textBlock` è definita in precedenza TextBlock e `label` è un'etichetta definita in precedenza:  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);    
```  
  
 **XAML:** impostare lo stile del controllo TextBlock o etichetta, come illustrato:  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>  
```  
  
#### <a name="133-environment-font"></a>Tipo di carattere ambiente 133%  
 **Viene visualizzato come:** 12 pt Segoe UI    
 **Utilizzo per:** sottotitoli inferiori nel documento e le finestre di dialogo di firma e dell'interfaccia utente  
  
 **Codice procedurale:** in `textBlock` è definita in precedenza TextBlock e `label` è un'etichetta definita in precedenza:  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);    
```  
  
 **XAML:** impostare lo stile del controllo TextBlock o etichetta, come illustrato:  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>    
```  
  
#### <a name="122-environment-font"></a>Tipo di carattere ambiente 122%  
 **Viene visualizzato come:** 11 pt Segoe UI    
 **Utilizzo per:** sezione intestazioni nelle finestre di dialogo firma, primi nodi nella visualizzazione ad albero, spostamento tramite tabulazione verticale  
  
 **Codice procedurale:** in `textBlock` è definita in precedenza TextBlock e `label` è un'etichetta definita in precedenza:  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);    
```  
  
 **XAML:** impostare lo stile del controllo TextBlock o etichetta, come illustrato:  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>    
```  
  
#### <a name="environment-font--bold"></a>Tipo di carattere ambiente + grassetto  
 **Viene visualizzato come:** in grassetto 9 punti Segoe UI    
 **Utilizzo per:** etichette e i sottotitoli nel documento, report e le finestre di dialogo di firma e l'interfaccia utente  
  
 **Codice procedurale:** in `textBlock` è definita in precedenza TextBlock e `label` è un'etichetta definita in precedenza:  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty,    
        VsResourceKeys.TextBlockEnvironmentBoldStyleKey);   
label.SetResourceReference(Label.StyleProperty,    
        VsResourceKeys.LabelEnvironmentBoldStyleKey);    
```  
  
 **XAML:** impostare lo stile del controllo TextBlock o etichetta, come illustrato:  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock>   
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>    
```  
  
### <a name="localizable-styles"></a>Stili localizzabili  
 In alcuni casi, i localizzatori saranno necessario modificare gli stili dei caratteri per impostazioni locali diverse, ad esempio rimuovendo il grassetto dal testo per lingue dell'Asia orientale. Per rendere possibile la localizzazione degli stili di carattere, gli stili devono essere all'interno del file con estensione resx. Il modo migliore per eseguire questa operazione e modificare gli stili dei caratteri nella finestra di progettazione di form di Visual Studio è impostato in modo esplicito gli stili del carattere in fase di progettazione. Anche se questo crea un oggetto font completo e potrebbe sembrare l'ereditarietà dei tipi di carattere padre, solo la proprietà FontStyle viene utilizzata per impostare il tipo di carattere.  
  
 La soluzione consiste nell'associare il modulo di finestra di dialogo `FontChanged` evento. Nel `FontChanged` evento, esaminare tutti i controlli e controllare se il carattere è stato impostato. Se è impostato, modificarlo in un nuovo tipo di carattere in base a tipo di carattere del form e stile del carattere precedente del controllo. Un esempio di questo codice è:  
  
```  
private void Form1_FontChanged(object sender, System.EventArgs e)  
{  
          SetFontStyles();  
}  
  
/// <summary>  
/// SetFontStyles - This function will iterate all controls on a page  
/// and recreate their font with the desired fontstyle.  
/// It should be called in the OnFontChanged handler (and also in the constructor  
/// in case the IUIService is not available so OnFontChange doesn't fire).  
/// This way, when the VS shell font is given to us the controls that have  
/// a different style for the font (bolded for example) will recreate their font  
/// and use the VS shell font but with a style variation (bolded ...).  
/// </summary>   
protected void SetFontStyles()  
{  
     SetFontStyles(this, this, this.Font);  
}  
  
protected static void SetFontStyles(Control topControl, Control parent, Font referenceFont)  
{  
     foreach(Control c in parent.Controls)  
     {  
          if (c.Controls != null && c.Controls.Count > 0) {  
               SetFontStyles(topControl, c, referenceFont);  
          }  
          if (c.Font != topControl.Font) {  
               c.Font = new Font(referenceFont, c.Font.Style);  
          }  
     }  
}  
```  
  
 Con questo codice garantisce che, quando viene aggiornato il carattere del form, verrà aggiornato anche i tipi di carattere dei controlli. Questo metodo deve anche essere chiamato dal costruttore del form, in quanto la finestra di dialogo potrebbe non riuscire a ottenere un'istanza di `IUIService` e `FontChanged` mai viene generato l'evento. Associazione `FontChanged` consentirà di finestre di dialogo prelevati dinamicamente il nuovo tipo di carattere, anche se la finestra di dialogo è già aperta.  
  
### <a name="testing-the-environment-font"></a>Il tipo di carattere ambiente di test  
 Per assicurarsi che l'interfaccia utente utilizza il tipo di carattere ambiente e che rispetta le impostazioni della dimensione, aprire **strumenti > Opzioni > ambiente > tipi di carattere e colori** e selezionare "Tipo di carattere ambiente" i "Mostra impostazioni per:" dal menu a discesa.  
  
 ![Le impostazioni di tipi di carattere e colori negli strumenti di &gt; finestra di dialogo Opzioni](../../extensibility/ux-guidelines/media/0201-a_optionsfonts.png "0201 a_OptionsFonts")<br />Le impostazioni di tipi di carattere e colori negli strumenti di &gt; finestra di dialogo Opzioni
  
 Impostare il tipo di carattere su un valore molto diverso da quello predefinito. Per rendere più evidente che non l'aggiornamento dell'interfaccia utente, scegliere un tipo di carattere con grazie (ad esempio "Times New Roman") e impostare le dimensioni molto grandi. Quindi testare l'interfaccia utente per assicurarsi che rispetta l'ambiente. Di seguito è riportato un esempio tramite la finestra di dialogo di licenza:  
  
 ![Esempio di testo dell'interfaccia utente che non rispetta il tipo di carattere ambiente](../../extensibility/ux-guidelines/media/0201-b_wrongfontdialog.png "0201 b_WrongFontDialog")<br />Esempio di testo dell'interfaccia utente che non rispetta il tipo di carattere ambiente
  
 In questo caso, "Informazioni utente" e "Informazioni" sono non rispettano il tipo di carattere. In alcuni casi potrebbe trattarsi di una scelta di progettazione esplicite, ma può trattarsi di un bug, se il tipo di carattere esplicita non è specificato come parte delle specifiche con linea rossa.  
  
 Per reimpostare il tipo di carattere, fare clic su "Valori predefiniti" in **strumenti > Opzioni > ambiente > tipi di carattere e colori**.  
  
##  <a name="BKMK_TextStyle"></a>Stile del testo  
 Stile del testo fa riferimento a maiuscole e minuscole, peso e dimensioni del carattere. Per indicazioni di implementazione, vedere [il tipo di carattere ambiente](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).  
  
### <a name="text-casing"></a>Maiuscole e minuscole di testo  
  
#### <a name="all-caps"></a>Tutto maiuscole  
 Non utilizzare tutte maiuscole per i titoli o le etichette in Visual Studio.  
  
#### <a name="all-lowercase"></a>Tutti i caratteri minuscoli  
 Non usare tutti in lettere minuscole per i titoli o le etichette in Visual Studio.  
  
#### <a name="sentence-and-title-case"></a>Case frase e il titolo  
 Testo in Visual Studio deve utilizzare maiuscole o minuscole frase, in base alla situazione.  
  
|Utilizzare iniziali maiuscole per:|Frase caso di utilizzo:|  
|-------------------------|----------------------------|  
|Titoli di finestra di dialogo|Etichette|  
|Caselle di gruppo|Caselle di controllo|  
|Voci di menu|Pulsanti di opzione|  
|Voci del menu contestuale|Elementi casella di riepilogo|  
|Pulsanti|Barre di stato|  
|In una tabella pivot||  
|Intestazioni di colonna||  
|Tooltips||  
  
##### <a name="title-case"></a>Iniziali maiuscole  
 Iniziali maiuscole sono uno stile in cui sono in maiuscolo le prime lettere della maggior parte o tutte le parole all'interno di una frase. In Visual Studio, maiuscole viene utilizzata per molti elementi, tra cui:  
  
-   **Descrizioni comandi.** Esempio: "anteprima di elementi selezionati"  
  
-   **Intestazioni di colonna.** Esempio: "risposta di sistema"  
  
-   **Voci di menu.** Esempio: "Salva tutto"  
  
 Quando si utilizza iniziali maiuscole, queste sono le linee guida per quando a sfruttare appieno le parole e lasciare le lettere minuscole:  
  
|Maiuscole|Esempi e commenti|  
|---------------|---------------------------|  
|Tutti i sostantivi||  
|Tutti i verbi|Tra cui "Is" e altre forme di "per essere"|  
|Avverbi tutti|Tra cui "Di" e "When"|  
|Aggettivi tutti|Tra cui "This" e "Che"|  
|Tutti i pronomi|Tra cui l'impropri "Il" anche come "È", una contrazione del Pronome "," e il verbo "is"|  
|Primo e l'ultima parola, indipendentemente dalle parti del discorso||  
|Preposizioni che fanno parte di una frase verbo|"La chiusura di tutti i Windows" o "In corso l'arresto del sistema"|  
|Tutte le lettere di un acronimo|HTML, XML, URL, IDE, RGB|  
|La seconda parola in una parola composta in caso di un sostantivo o un aggettivo appropriate o se le parole hanno lo stesso peso|Con riferimento incrociato, Software pre-Microsoft accesso di lettura/scrittura, in fase di esecuzione|  
  
|Minuscole|Esempi|  
|---------------|--------------|  
|La seconda parola in una parola composta, se si tratta di un'altra parte del discorso o un participio modifica la prima parola|Guida procedurale, presa|  
|Gli articoli, a meno che uno è la prima parola nel titolo|un oggetto, un oggetto, il|  
|Congiunzioni coordinate|e, ma, né, o|  
|Preposizioni con parole di un massimo di quattro lettere di fuori di una frase verbo|in, in, come per fuori, nella parte superiore della|  
|"A" utilizzato in una frase infinita|"Come formattare il disco rigido"|  
  
##### <a name="sentence-case"></a>Case di frase  
 Normale è il metodo di lettere maiuscole/minuscole standard per la scrittura in cui è in maiuscolo la prima parola della frase, insieme a eventuali nomi propri e i Pronome "I". In generale, i case di frase è più semplice per un gruppo di destinatari in tutto il mondo leggere, soprattutto quando il contenuto verrà convertito da una macchina. Frase caso di utilizzo:  
  
1.  **Messaggi della barra di stato.** Questi sono semplici, breve e fornire solo informazioni sullo stato. Esempio: "caricamento file di progetto"  
  
2.  **Tutti gli altri elementi dell'interfaccia utente**, tra cui le etichette, caselle di controllo, pulsanti di opzione e casella voci di elenco. Esempio: "Seleziona tutti gli elementi nell'elenco"  
  
### <a name="text-formatting"></a>Formattazione del testo  
 In Visual Studio 2013 formattazione di testo predefinita è controllato da [il tipo di carattere ambiente](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont). Questo servizio consente di garantire un aspetto coerente del carattere nel corso dell'IDE (integrated development environment) e deve essere utilizzata per garantire un'esperienza coerente per gli utenti.  
  
 La dimensione predefinita utilizzata dal servizio di tipo di carattere di Visual Studio proviene da Windows e viene visualizzato come 9 punti.  
  
 È possibile applicare la formattazione per il tipo di carattere ambiente. Questo argomento viene illustrato come e dove utilizzino gli stili. Per informazioni sull'implementazione, vedere [il tipo di carattere ambiente](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).  
  
#### <a name="bold-text"></a>Testo in grassetto  
 Testo in grassetto è usato con cautela in Visual Studio e deve essere riservato per:  
  
-   etichette di domanda nelle procedure guidate  
  
-   la designazione del progetto attivo in Esplora soluzioni  
  
-   i valori nella finestra Proprietà strumento sottoposto a override  
  
-   alcuni eventi negli elenchi a discesa editor Visual Basic  
  
-   generato dal server di contenuto nella struttura del documento per le pagine web  
  
-   intestazioni di sezione nella finestra di dialogo complesso o di progettazione dell'interfaccia utente  
  
#### <a name="italics"></a>Italics  
 Visual Studio non usa corsivo o in grassetto il testo in corsivo.  
  
#### <a name="color"></a>Colore  
  
-   Blu è riservato per i collegamenti ipertestuali (spostamento e l'esecuzione di comandi) e non deve mai essere utilizzata per l'orientamento.  
  
-   Le intestazioni di dimensioni maggiori (tipo di carattere ambiente 155% o superiore) possono colore per i seguenti scopi:  
  
    -   Per fornire l'impatto visivo alla firma dell'interfaccia utente di Visual Studio  
  
    -   Per richiamare l'attenzione su un'area specifica  
  
    -   Per offrire rilievo dal colore del testo standard ambiente/nero grigio scuro  
  
-   Colore nelle intestazioni debba sfruttare Visual Studio esistente del marchio colori, viola principalmente principale, FF68217A #.  
  
-   Quando si utilizza colore nelle intestazioni, è necessario rispettare il [Windows colore linee guida](https://msdn.microsoft.com/en-us/library/dn742482.aspx), tra cui contrasto e altre considerazioni di accessibilità.  
  
### <a name="font-size"></a>Dimensione carattere  
 Progettazione di Visual Studio UI presenta un aspetto più chiaro con maggiore spazio vuoto. Dove possibile, chrome e titolo barre sono stati ridotte o rimosse. Mentre la densità di informazioni è un requisito in Visual Studio, tipografia continua a essere importanti, con un'enfasi sulla interlinea più aperto e una variante di pesi e le dimensioni dei caratteri.  
  
 Nella tabella seguente sono inclusi i dettagli di progettazione e gli esempi di visual per i tipi di carattere visualizzazione utilizzate in Visual Studio. Alcune varianti del tipo di carattere visualizzazione sono le dimensioni e il peso, ad esempio Semilight o chiaro, codificato nel suo aspetto.  
  
 Frammenti di codice di implementazione per tutti i caratteri sono reperibili [formattazione (scalabilità/grassetto) riferimento](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting).  
  
#### <a name="375-environment-font--light"></a>Tipo di carattere ambiente 375% + Light  
  
|||  
|-|-|  
|**Utilizzo:** rari. Unique marchio solo l'interfaccia utente.<br /><br /> **Eseguire:**<br /><br /> -Frase caso di utilizzo<br />-Utilizzare sempre leggero<br /><br /> **Non:**<br /><br /> -Utilizzare per l'interfaccia utente diverso da firma dell'interfaccia utente, ad esempio pagina iniziale<br />-Grassetto, corsivo o grassetto, corsivo<br />-Utilizzare per il corpo del testo<br />-Utilizzare le finestre degli strumenti|**Viene visualizzato come:** pt 34 Segoe UI Light<br /><br /> **Esempio di Visual:**<br /><br /> *Attualmente non utilizzato. Può essere utilizzato nella pagina iniziale.*|  
  
#### <a name="310-environment-font--light"></a>Tipo di carattere ambiente 310% + Light  
  
|||  
|-|-|  
|**Utilizzo:**<br /><br /> -Intestazione maggiori nelle finestre di dialogo firma<br />-Intestazione di report principale<br /><br /> **Eseguire:**<br /><br /> -Frase caso di utilizzo<br />-Utilizzare sempre leggero<br /><br /> **Non:**<br /><br /> -Utilizzare per l'interfaccia utente diverso da firma dell'interfaccia utente, ad esempio pagina iniziale<br />-Grassetto, corsivo o grassetto, corsivo<br />-Utilizzare per il corpo del testo<br />-Utilizzare le finestre degli strumenti|**Viene visualizzato come:** pt 28 Segoe UI Light<br /><br /> **Esempio di Visual:**<br /><br /> ![Esempio di tipo di carattere ambiente 310% &#43; Intestazione Light](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202 a_EF310")|  
  
#### <a name="200-environment-font--semilight"></a>Tipo di carattere ambiente 200% + Semilight  
  
|||  
|-|-|  
|**Utilizzo:**<br /><br /> -Sottotitoli<br />-I titoli di finestre di dialogo di piccole e medie dimensioni<br /><br /> **Eseguire:**<br /><br /> -Frase caso di utilizzo<br />: Viene sempre utilizzato il peso Semilight<br /><br /> **Non:**<br /><br /> -Grassetto, corsivo o grassetto, corsivo<br />-Utilizzare per il corpo del testo<br />-Utilizzare le finestre degli strumenti|**Viene visualizzato come:** 18 pt Segoe UI Semillight<br /><br /> **Esempio di Visual:**<br /><br /> ![Esempio di tipo di carattere ambiente 200% &#43; Semilight](../../extensibility/ux-guidelines/media/0202-b_ef200.png "0202 b_EF200")|  
  
#### <a name="155-environment-font"></a>Tipo di carattere ambiente 155%  
  
|||  
|-|-|  
|**Utilizzo:**<br /><br /> -Titoli sezione documento nonché dell'interfaccia utente<br />-Report<br /><br /> **Eseguire:** frase caso di utilizzo<br /><br /> **Non:**<br /><br /> -Grassetto, corsivo o grassetto, corsivo<br />-Utilizzare per il corpo del testo<br />-Usare i controlli standard di Visual Studio<br />-Utilizzare le finestre degli strumenti|**Viene visualizzato come:** 14 pt Segoe UI<br /><br /> **Esempio di Visual:**<br /><br /> ![Esempio di intestazione con tipo di carattere ambiente 155%](../../extensibility/ux-guidelines/media/0202-c_ef155.png "0202 c_EF155")|  
  
#### <a name="133-environment-font"></a>Tipo di carattere ambiente 133%  
  
|||  
|-|-|  
|**Utilizzo:**<br /><br /> -Sottotitoli più piccoli in finestre di dialogo firma<br />-Sottotitoli inferiori nel documento e dell'interfaccia utente<br /><br /> **Eseguire:** frase caso di utilizzo<br /><br /> **Non:**<br /><br /> -Grassetto, corsivo o grassetto, corsivo<br />-Utilizzare per il corpo del testo<br />-Usare i controlli standard di Visual Studio<br />-Utilizzare le finestre degli strumenti|**Viene visualizzato come:** 12 pt Segoe UI<br /><br /> **Esempio di Visual:**<br /><br /> ![Esempio di intestazione con tipo di carattere ambiente 133%](../../extensibility/ux-guidelines/media/0202-d_ef133.png "0202 d_EF133")|  
  
#### <a name="122-environment-font"></a>Tipo di carattere ambiente 122%  
  
|||  
|-|-|  
|**Utilizzo:**<br /><br /> -Intestazioni sezione nelle finestre di dialogo firma<br />-Primi nodi nella visualizzazione ad albero<br />-Spostamento tramite tabulazione verticale<br /><br /> **Eseguire:** frase caso di utilizzo<br /><br /> **Non:**<br /><br /> -Grassetto, corsivo o grassetto, corsivo<br />-Utilizzare per il corpo del testo<br />-Usare i controlli standard di Visual Studio<br />-Utilizzare le finestre degli strumenti|**Viene visualizzato come:** 11 pt Segoe UI<br /><br /> **Esempio di Visual:**<br /><br /> ![Esempio di intestazione con tipo di carattere ambiente 122%](../../extensibility/ux-guidelines/media/0202-e_ef122.png "0202 e_EF122")|  
  
#### <a name="environment-font--bold"></a>Tipo di carattere ambiente + grassetto  
  
|||  
|-|-|  
|**Utilizzo:**<br /><br /> -Etichette e i sottotitoli nelle finestre di dialogo firma<br />-Etichette e i sottotitoli nei report<br />-Etichette, nonché di sottotitoli nel documento dell'interfaccia utente<br /><br /> **Eseguire:**<br /><br /> -Frase caso di utilizzo<br />-Utilizzare spessore grassetto<br /><br /> **Non:**<br /><br /> -Corsivo o grassetto corsivo<br />-Utilizzare per il corpo del testo<br />-Usare i controlli standard di Visual Studio<br />-Utilizzare le finestre degli strumenti|**Viene visualizzato come:** in grassetto 9 punti Segoe UI<br /><br /> **Esempio di Visual:**<br /><br /> ![Esempio di tipo di carattere ambiente &#43; Intestazione grassetto](../../extensibility/ux-guidelines/media/0202-f_efb.png "0202 f_EFB")|  
  
#### <a name="environment-font"></a>Tipo di carattere ambiente  
  
|||  
|-|-|  
|**Utilizzo:** tutto il testo rimanente<br /><br /> **Eseguire:** frase caso di utilizzo<br /><br /> **Non:** corsivo o grassetto corsivo|**Viene visualizzato come:** 9 punti Segoe UI<br /><br /> **Esempio di Visual:**<br /><br /> ![Esempio di tipo di carattere ambiente](../../extensibility/ux-guidelines/media/0202-g_ef.png "0202 g_EF")|  
  
### <a name="padding-and-spacing"></a>Spaziatura interna e la spaziatura  
 Intestazioni richiedono spazio attorno a esse per consentire loro l'enfasi appropriato. Questo spazio varia a seconda di dimensioni del punto e in quale altro si avvicina il titolo, ad esempio una regola orizzontale o di una riga di testo nel tipo di carattere ambiente.  
  
-   La spaziatura interna ideale per un'intestazione di per sé deve essere 90% dello spazio di altezza capitali carattere. Ad esempio, un'intestazione di Segoe UI Light pt 28 ha un'altezza di limite di 26 pt e la spaziatura interna deve essere circa pt 23, ovvero circa 31 pixel.  
  
-   Lo spazio minimo intorno a un'intestazione deve essere 50% dell'altezza del carattere capitale. Meno spazio può essere utilizzata quando un'intestazione è accompagnata da una regola o un altro elemento di una stretta adattamento.  
  
-   Testo in grassetto con un carattere ambiente deve seguire la spaziatura interna e spaziatura altezza di riga predefinita.  
  
## <a name="see-also"></a>Vedere anche  
 [MSDN: I tipi di carattere (Windows)](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742483\(v=vs.85\).aspx)   
 [MSDN: Il testo dell'interfaccia utente (Windows)](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx)