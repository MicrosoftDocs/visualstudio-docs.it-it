---
title: Creazione di un'area di controllo di visualizzazione, i comandi e le impostazioni | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 4a2df0a3-42da-4f7b-996f-ee16a35ac922
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 57a7696eae0da92d88babf64c580a4767775dffd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-a-view-adornment-commands-and-settings-column-guides"></a>Procedura dettagliata: Creazione di un'area di controllo di visualizzazione, comandi e le impostazioni (guide colonne)
È possibile estendere l'editor di testo o codice di Visual Studio con i comandi e visualizzare gli effetti.  In questo argomento viene illustrato come iniziare con una funzionalità di estensione comuni, le guide di colonna.  Le guide di colonna sono visivamente chiara linee disegnate su visualizzazione dell'editor di testo che consentono di gestire il codice per la larghezza delle colonne specifiche.  Codice di formattazione specifica può essere importante per gli esempi si includere nei documenti, post di blog o report di bug.  
  
 In questa procedura dettagliata, sarà possibile:  
  
-   Creare un progetto VSIX  
  
-   Aggiungere un'area di controllo di visualizzazione dell'editor  
  
-   Aggiungere il supporto per il salvataggio e recupero delle impostazioni (in cui disegnare colonna Guide alle procedure e il colore)  
  
-   Aggiungere comandi (aggiunta o rimozione di guide di colonna, modificarne il colore)  
  
-   Inserire i comandi del menu di modifica e i menu di scelta rapida documento di testo  
  
-   Aggiungere il supporto per richiamare i comandi nella finestra di comando Visual Studio  
  
 È possibile provare una versione della funzionalità di guide di colonna con questo Visual Studio Gallery[estensione](https://visualstudiogallery.msdn.microsoft.com/da227a0b-0e31-4a11-8f6b-3a149cf2e459?SRC=Home).  
  
 **Nota**: in questa procedura dettagliata è incollare una grande quantità di codice in alcuni file generati da modelli di estensione di visual studio, ma non appena questa procedura dettagliata farà riferimento a una soluzione completa su github con altri esempi di estensione.  Il codice completo è leggermente diverso in quanto dispone le icone reale anziché generictemplate icone.  
  
## <a name="getting-started"></a>Introduzione  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per ulteriori informazioni, vedere [l'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="setting-up-the-solution"></a>Impostazione della soluzione  
 Si verrà innanzitutto creare un progetto VSIX, aggiungere un'area di controllo di visualizzazione dell'editor e quindi aggiungere un comando (che aggiunge un VSPackage per il comando proprietari).  L'architettura di base è la seguente:  
  
-   Si dispone di un listener di creazione visualizzazione di testo che crea un `ColumnGuideAdornment` oggetto per ogni visualizzazione.  Questo oggetto è in attesa per gli eventi relativi alla visualizzazione di modifica o impostazioni di modifica, le guide di colonna grafico o ad aggiornamento in base alle esigenze.  
  
-   È presente un `GuidesSettingsManager` che gestisce la lettura e scrittura dall'archiviazione di impostazioni di Visual Studio.  Gestione impostazioni dispone anche di operazioni per l'aggiornamento delle impostazioni che supportano i comandi dell'utente (aggiungere la colonna, rimuovere una colonna, modificare i colori).  
  
-   È un pacchetto VSIP che è necessario se si dispone di comandi per l'utente, ma è solo il codice di boilerplate che inizializza l'oggetto di implementazione di comandi.  
  
-   È presente un `ColumnGuideCommands` oggetto che implementa i comandi dell'utente e i gestori di comando per i comandi dichiarati nel file vsct.  
  
 **VSIX**.  Uso **File &#124; New...**  comando per creare un progetto.  Scegliere il nodo di estendibilità in c# nel riquadro di spostamento a sinistra e scegliere **progetto VSIX** nel riquadro di destra.  Immettere il nome ColumnGuides e scegliere **OK** per creare il progetto.  
  
 **Visualizzazione dell'area di controllo**.  Premere il pulsante destro del puntatore sul nodo del progetto in Esplora soluzioni.  Scegliere il **aggiungere &#124; nuovo elemento...**  comando per aggiungere un nuovo elemento dell'area di controllo di visualizzazione.  Scegliere **estendibilità &#124; Editor** nel riquadro di spostamento a sinistra e scegliere **dell'area di controllo di Editor Viewport** nel riquadro di destra.  Immettere il nome ColumnGuideAdornment come il nome dell'elemento e scegliere **Aggiungi** per aggiungerlo.  
  
 È possibile visualizzare il modello di elemento aggiunti due file al progetto (così come i riferimenti e così via): ColumnGuideAdornment.cs e ColumnGuideAdornmentTextViewCreationListener.cs.  I modelli solo un rettangolo di colore viola nella vista.  Di seguito si cambia un paio di righe nel listener di creazione di visualizzazione e sostituire il contenuto di ColumnGuideAdornment.cs.  
  
 **I comandi**.  Premere il pulsante destro del puntatore sul nodo del progetto in Esplora soluzioni.  Scegliere il **aggiungere &#124; nuovo elemento...**  comando per aggiungere un nuovo elemento dell'area di controllo di visualizzazione.  Scegliere **estendibilità &#124; VSPackage** nel riquadro di spostamento a sinistra e scegliere **comando personalizzato** nel riquadro di destra.  Immettere il nome ColumnGuideCommands come il nome dell'elemento e scegliere **Aggiungi** per aggiungerlo.  Oltre ai riferimenti diversi, aggiungendo i comandi e un pacchetto aggiunto ColumnGuideCommands.cs ColumnGuideCommandsPackage.cs e ColumnGuideCommandsPackage.vsct.  Di seguito, si sostituirà il contenuto dei file e il cognome per definire e implementare i comandi.  
  
## <a name="setting-up-the-text-view-creation-listener"></a>Configurare il Listener di creazione di visualizzazione testo  
 Aprire ColumnGuideAdornmentTextViewCreationListener.cs nell'editor.  Questo codice implementa un gestore per ogni volta che Visual Studio crea le visualizzazioni di testo.  Sono disponibili gli attributi che controllano quando viene chiamato il gestore a seconda delle caratteristiche della visualizzazione.  
  
 Il codice deve dichiarare anche un livello di area di controllo.  Quando l'editor visualizzazioni degli aggiornamenti, ottiene i livelli dell'area di controllo per la visualizzazione e dal che ottiene gli elementi dell'area di controllo.  È possibile dichiarare l'ordinamento del livello rispetto alle altre con attributi.  Sostituire la riga seguente:  
  
```csharp  
[Order(After = PredefinedAdornmentLayers.Caret)]  
```  
  
 con queste due righe:  
  
```csharp  
[Order(Before = PredefinedAdornmentLayers.Text)]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
```  
  
 La riga che è stato sostituito è in un gruppo di attributi che dichiarano un livello di area di controllo.   La prima riga sono stati modificati solo le modifiche apportate in cui vengono visualizzate le linee guida di colonna.  Disegnano le righe del "testo nella visualizzazione significa che appaiono dietro o sotto il testo prima".  La seconda riga dichiara che le aree di controllo di Guida di colonna sono applicabili alle entità di testo che soddisfano la nozione di un documento, ma è possibile dichiarare l'area di controllo, ad esempio, per solo il lavoro per il testo modificabile.  Altre informazioni di [servizio di linguaggio e i punti di estensione di Editor](../extensibility/language-service-and-editor-extension-points.md)  
  
## <a name="implementing-the-settings-manager"></a>Gestione delle impostazioni di implementazione  
 Sostituire il contenuto del GuidesSettingsManager.cs con il codice seguente (illustrato di seguito):  
  
```csharp  
using Microsoft.VisualStudio.Settings;  
using Microsoft.VisualStudio.Shell;  
using Microsoft.VisualStudio.Shell.Settings;  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Windows.Media;  
  
namespace ColumnGuides  
{  
    internal static class GuidesSettingsManager  
    {  
        // Because my code is always called from the UI thred, this succeeds.  
        internal static SettingsManager VsManagedSettingsManager =  
            new ShellSettingsManager(ServiceProvider.GlobalProvider);  
  
        private const int _maxGuides = 5;  
        private const string _collectionSettingsName = "Text Editor";  
        private const string _settingName = "Guides";  
        // 1000 seems reasonable since primary scenario is long lines of code  
        private const int _maxColumn = 1000;   
  
        static internal bool AddGuideline(int column)  
        {  
            if (! IsValidColumn(column))  
                throw new ArgumentOutOfRangeException(  
                    "column",  
                    "The paramenter must be between 1 and " + _maxGuides.ToString());  
            var offsets = GuidesSettingsManager.GetColumnOffsets();  
            if (offsets.Count() >= _maxGuides)  
                return false;  
            // Check for duplicates  
            if (offsets.Contains(column))  
                return false;  
            offsets.Add(column);  
            WriteSettings(GuidesSettingsManager.GuidelinesColor, offsets);  
            return true;  
        }  
  
        static internal bool RemoveGuideline(int column)  
        {  
            if (!IsValidColumn(column))  
                throw new ArgumentOutOfRangeException(  
                    "column", "The paramenter must be between 1 and 10,000");  
            var columns = GuidesSettingsManager.GetColumnOffsets();  
            if (! columns.Remove(column))  
            {  
                // Not present.  Allow user to remove the last column   
                // even if they're not on the right column.  
                if (columns.Count != 1)  
                    return false;  
  
                columns.Clear();  
            }  
            WriteSettings(GuidesSettingsManager.GuidelinesColor, columns);  
            return true;  
        }  
  
        static internal bool CanAddGuideline(int column)  
        {  
            if (!IsValidColumn(column))  
                return false;  
            var offsets = GetColumnOffsets();  
            if (offsets.Count >= _maxGuides)  
                return false;  
            return ! offsets.Contains(column);  
        }  
  
        static internal bool CanRemoveGuideline(int column)  
        {  
            if (! IsValidColumn(column))  
                return false;  
            // Allow user to remove the last guideline regardless of the column.  
            // Okay to call count, we limit the number of guides.  
            var offsets = GuidesSettingsManager.GetColumnOffsets();  
            return offsets.Contains(column) || offsets.Count() == 1;  
        }  
  
        static internal void RemoveAllGuidelines()  
        {  
            WriteSettings(GuidesSettingsManager.GuidelinesColor, new int[0]);  
        }  
  
        private static bool IsValidColumn(int column)  
        {  
            // zero is allowed (per user request)  
            return 0 <= column && column <= _maxColumn;  
        }  
  
        // This has format "RGB(<int>, <int>, <int>) <int> <int>...".  
        // There can be any number of ints following the RGB part,   
        // and each int is a column (char offset into line) where to draw.  
        static private string _guidelinesConfiguration;  
        static private string GuidelinesConfiguration  
        {  
            get  
            {  
                if (_guidelinesConfiguration == null)  
                {  
                    _guidelinesConfiguration =   
                        GetUserSettingsString(  
                            GuidesSettingsManager._collectionSettingsName,  
                            GuidesSettingsManager._settingName)  
                        .Trim();  
                }  
                return _guidelinesConfiguration;  
            }  
  
            set  
            {  
                if (value != _guidelinesConfiguration)  
                {  
                    _guidelinesConfiguration = value;  
                    WriteUserSettingsString(  
                        GuidesSettingsManager._collectionSettingsName,  
                        GuidesSettingsManager._settingName, value);  
                    // Notify ColumnGuideAdornments to update adornments in views.  
                    var handler = GuidesSettingsManager.SettingsChanged;  
                    if (handler != null)  
                        handler();  
                }  
            }  
        }  
  
        internal static string GetUserSettingsString(string collection, string setting)  
        {  
            var store = GuidesSettingsManager  
                            .VsManagedSettingsManager  
                            .GetReadOnlySettingsStore(SettingsScope.UserSettings);  
            return store.GetString(collection, setting, "RGB(255,0,0) 80");  
        }  
  
        internal static void WriteUserSettingsString(string key, string propertyName,  
                                                     string value)  
        {  
            var store = GuidesSettingsManager  
                            .VsManagedSettingsManager  
                            .GetWritableSettingsStore(SettingsScope.UserSettings);  
            store.CreateCollection(key);  
            store.SetString(key, propertyName, value);  
        }  
  
        // Persists settings and sets property with side effect of signaling  
        // ColumnGuideAdornments to update.  
        static private void WriteSettings(Color color, IEnumerable<int> columns)  
        {  
            string value = ComposeSettingsString(color, columns);  
            GuidelinesConfiguration = value;  
        }  
  
        private static string ComposeSettingsString(Color color,  
                                                    IEnumerable<int> columns)  
        {  
            StringBuilder sb = new StringBuilder();  
            sb.AppendFormat("RGB({0},{1},{2})", color.R, color.G, color.B);  
            IEnumerator<int> columnsEnumerator = columns.GetEnumerator();  
            if (columnsEnumerator.MoveNext())  
            {  
                sb.AppendFormat(" {0}", columnsEnumerator.Current);  
                while (columnsEnumerator.MoveNext())  
                {  
                    sb.AppendFormat(", {0}", columnsEnumerator.Current);  
                }  
            }  
            return sb.ToString();  
        }  
  
        // Parse a color out of a string that begins like "RGB(255,0,0)"  
        static internal Color GuidelinesColor  
        {  
            get  
            {  
                string config = GuidelinesConfiguration;  
                if (!String.IsNullOrEmpty(config) && config.StartsWith("RGB("))  
                {  
                    int lastParen = config.IndexOf(')');  
                    if (lastParen > 4)  
                    {  
                        string[] rgbs = config.Substring(4, lastParen - 4).Split(',');  
  
                        if (rgbs.Length >= 3)  
                        {  
                            byte r, g, b;  
                            if (byte.TryParse(rgbs[0], out r) &&  
                                byte.TryParse(rgbs[1], out g) &&  
                                byte.TryParse(rgbs[2], out b))  
                            {  
                                return Color.FromRgb(r, g, b);  
                            }  
                        }  
                    }  
                }  
                return Colors.DarkRed;  
            }  
  
            set  
            {  
                WriteSettings(value, GetColumnOffsets());  
            }  
        }  
  
        // Parse a list of integer values out of a string that looks like  
        // "RGB(255,0,0) 1, 5, 10, 80"  
        static internal List<int> GetColumnOffsets()  
        {  
            var result = new List<int>();  
            string settings = GuidesSettingsManager.GuidelinesConfiguration;  
            if (String.IsNullOrEmpty(settings))  
                return new List<int>();  
  
            if (!settings.StartsWith("RGB("))  
                return new List<int>();  
  
            int lastParen = settings.IndexOf(')');  
            if (lastParen <= 4)  
                return new List<int>();  
  
            string[] columns = settings.Substring(lastParen + 1).Split(',');  
  
            int columnCount = 0;  
            foreach (string columnText in columns)  
            {  
                int column = -1;  
                // VS 2008 gallery extension didn't allow zero, so per user request ...  
                if (int.TryParse(columnText, out column) && column >= 0)  
                {  
                    columnCount++;  
                    result.Add(column);  
                    if (columnCount >= _maxGuides)  
                        break;  
                }  
            }  
            return result;  
        }  
  
        // Delegate and Event to fire when settings change so that ColumnGuideAdornments   
        // can update.  We need nothing special in this event since the settings manager   
        // is statically available.  
        //  
        internal delegate void SettingsChangedHandler();  
        static internal event SettingsChangedHandler SettingsChanged;  
  
    }  
}  
  
```  
  
 La maggior parte di questo codice appena creato e analizza il formato delle impostazioni: "RGB (\<int >,\<int >,\<int >) \<int >, \<int >,...".  I numeri interi alla fine sono le colonne in base uno in cui si desidera guide colonne.  L'estensione di guide colonna acquisisce tutte le relative impostazioni in una stringa di valore di singola impostazione.  
  
 Esistono alcune parti del codice vale la pena evidenziazione.  La riga di codice seguente ottiene il wrapper gestito di Visual Studio per l'archiviazione delle impostazioni.  La maggior parte, questo astrae tramite il Registro di sistema di Windows, ma questa API è indipendente del meccanismo di archiviazione.  
  
```csharp  
internal static SettingsManager VsManagedSettingsManager =  
    new ShellSettingsManager(ServiceProvider.GlobalProvider);  
```  
  
 L'archiviazione delle impostazioni di Visual Studio utilizza un identificatore di categoria e un identificatore di impostazione per identificare in modo univoco tutte le impostazioni:  
  
```csharp  
private const string _collectionSettingsName = "Text Editor";  
private const string _settingName = "Guides";  
```  
  
 Non è necessario utilizzare `"Text Editor"` come categoria, nome ed è possibile scegliere liberamente.  
  
 Il primo alcune funzioni sono i punti di ingresso per modificare le impostazioni.  Archivieranno i vincoli di alto livello come numero massimo di guide è consentito.  Quindi chiamano `WriteSettings` che compone una stringa di impostazioni e imposta la proprietà `GuideLinesConfiguration`.  Impostazione di questa proprietà Salva il valore di impostazioni per l'archivio di impostazioni di Visual Studio e viene attivato il `SettingsChanged` evento per aggiornare tutte le `ColumnGuideAdornment` oggetti, ognuno associato a una visualizzazione di testo.  
  
 Esistono un paio di funzioni di punto di ingresso, ad esempio `CanAddGuideline`, che vengono utilizzate per implementare i comandi che modificano le impostazioni.  Quando Visual Studio Mostra i menu, viene eseguita una query le implementazioni di comando per vedere se il comando è attualmente abilitato, il nome e così via.  Di seguito, si noterà come collegare questi punti di ingresso per le implementazioni di comando.  Vedere [estensione menu e comandi](../extensibility/extending-menus-and-commands.md) per ulteriori informazioni sui comandi.  
  
## <a name="implementing-the-columnguideadornment-class"></a>L'implementazione della classe ColumnGuideAdornment  
 Il `ColumnGuideAdornment` viene creata un'istanza di classe per ogni visualizzazione di testo che può avere elementi grafici.  Questa classe è in attesa per gli eventi relativi alla visualizzazione di modifica o impostazioni di modifica, le guide di colonna grafico o ad aggiornamento in base alle esigenze.  
  
 Sostituire il contenuto del ColumnGuideAdornment.cs con il codice seguente (illustrato di seguito):  
  
```csharp  
using System;  
using System.Windows.Media;  
using Microsoft.VisualStudio.Text.Editor;  
using System.Collections.Generic;  
using System.Windows.Shapes;  
using Microsoft.VisualStudio.Text.Formatting;  
using System.Windows;  
  
namespace ColumnGuides  
{  
    /// <summary>  
    /// Adornment class, one instance per text view that draws a guides on the viewport  
    /// </summary>  
    internal sealed class ColumnGuideAdornment  
    {  
        private const double _lineThickness = 1.0;  
        private IList<Line> _guidelines;  
        private IWpfTextView _view;  
        private double _baseIndentation;  
        private double _columnWidth;  
  
        /// <summary>  
        /// Creates editor column guidelines  
        /// </summary>  
        /// <param name="view">The <see cref="IWpfTextView"/> upon   
        /// which the adornment will be drawn</param>  
        public ColumnGuideAdornment(IWpfTextView view)  
        {  
            _view = view;  
            _guidelines = CreateGuidelines();  
            GuidesSettingsManager.SettingsChanged +=   
                new GuidesSettingsManager.SettingsChangedHandler(SettingsChanged);  
            view.LayoutChanged +=   
                new EventHandler<TextViewLayoutChangedEventArgs>(OnViewLayoutChanged);  
            _view.Closed += new EventHandler(OnViewClosed);  
        }  
  
        void SettingsChanged()  
        {  
            _guidelines = CreateGuidelines();  
            UpdatePositions();  
            AddGuidelinesToAdornmentLayer();  
        }  
  
        void OnViewClosed(object sender, EventArgs e)  
        {  
            _view.LayoutChanged -= OnViewLayoutChanged;  
            _view.Closed -= OnViewClosed;  
            GuidesSettingsManager.SettingsChanged -= SettingsChanged;  
        }  
  
        private bool _firstLayoutDone;  
  
        void OnViewLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)  
        {  
            bool fUpdatePositions = false;  
  
            IFormattedLineSource lineSource = _view.FormattedLineSource;  
            if (lineSource == null)  
            {  
                return;  
            }  
            if (_columnWidth != lineSource.ColumnWidth)  
            {  
                _columnWidth = lineSource.ColumnWidth;  
                fUpdatePositions = true;  
            }  
            if (_baseIndentation != lineSource.BaseIndentation)  
            {  
                _baseIndentation = lineSource.BaseIndentation;  
                fUpdatePositions = true;  
            }  
            if (fUpdatePositions ||  
                e.VerticalTranslation ||  
                e.NewViewState.ViewportTop != e.OldViewState.ViewportTop ||  
                e.NewViewState.ViewportBottom != e.OldViewState.ViewportBottom)  
            {  
                UpdatePositions();  
            }  
            if (!_firstLayoutDone)  
            {  
                AddGuidelinesToAdornmentLayer();  
                _firstLayoutDone = true;  
            }  
        }  
  
        private static IList<Line> CreateGuidelines()  
        {  
            Brush lineBrush = new SolidColorBrush(GuidesSettingsManager.GuidelinesColor);  
            DoubleCollection dashArray = new DoubleCollection(new double[] { 1.0, 3.0 });  
            IList<Line> result = new List<Line>();  
            foreach (int column in GuidesSettingsManager.GetColumnOffsets())  
            {  
                Line line = new Line()  
                {  
                    // Use the DataContext slot as a cookie to hold the column  
                    DataContext = column,  
                    Stroke = lineBrush,  
                    StrokeThickness = _lineThickness,  
                    StrokeDashArray = dashArray  
                };  
                result.Add(line);  
            }  
            return result;  
        }  
  
        void UpdatePositions()  
        {  
            foreach (Line line in _guidelines)  
            {  
                int column = (int)line.DataContext;  
                line.X2 = _baseIndentation + 0.5 + column * _columnWidth;  
                line.X1 = line.X2;  
                line.Y1 = _view.ViewportTop;  
                line.Y2 = _view.ViewportBottom;  
            }  
        }  
  
        void AddGuidelinesToAdornmentLayer()  
        {  
            // Grab a reference to the adornment layer that this adornment   
            // should be added to  
            // Must match exported name in ColumnGuideAdornmentTextViewCreationListener  
            IAdornmentLayer adornmentLayer =   
                _view.GetAdornmentLayer("ColumnGuideAdornment");  
            if (adornmentLayer == null)  
                return;  
            adornmentLayer.RemoveAllAdornments();  
            // Add the guidelines to the adornment layer and make them relative   
            // to the viewport  
            foreach (UIElement element in _guidelines)  
                adornmentLayer.AddAdornment(AdornmentPositioningBehavior.OwnerControlled,  
                                            null, null, element, null);  
        }  
    }  
  
}  
```  
  
 Le istanze di questa classe contengono associato <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> e un elenco di `Line` oggetti disegnati nella vista.  
  
 Il costruttore (chiamato da `ColumnGuideAdornmentTextViewCreationListener` quando Visual Studio crea le nuove visualizzazioni) consente di creare la Guida di colonna `Line` oggetti.  Il costruttore aggiunti anche i gestori eventi per il `SettingsChanged` evento (definito in `GuidesSettingsManager`) e gli eventi di visualizzazione `LayoutChanged` e `Closed`.  
  
 Il `LayoutChanged` evento viene generato a causa di diversi tipi di modifiche nella vista, incluse quelle in cui Visual Studio crea la visualizzazione.  Il `OnViewLayoutChanged` chiamate del gestore `AddGuidelinesToAdornmentLayer` da eseguire.  Il codice in `OnViewLayoutChanged` determina se è necessario aggiornare le posizioni delle righe in base alle modifiche, ad esempio modifiche delle dimensioni del carattere, i margini di visualizzazione, lo scorrimento orizzontale e così via.  Il codice in `UpdatePositions` fa sì che le linee guida disegnare tra i caratteri o subito dopo la colonna di testo che è l'offset del carattere specificato nella riga di testo.  
  
 Ogni volta che vengono modificate le impostazioni di `SettingsChanged` funzione appena ricrea tutti i `Line` oggetti con tutte le nuove impostazioni stanno.  Dopo aver impostato le posizioni di riga, il codice rimuove tutti i precedenti `Line` oggetti dal `ColumnGuideAdornment` layer di elementi grafici e aggiunge i nuovi file.  
  
## <a name="defining-the-commands-menus-and-menu-placements"></a>Definizione di posizioni di Menu, menu e comandi  
 Può essere molto dichiarando menu e comandi, l'inserimento di gruppi di menu o comandi in diversi altri menu e associazione di gestori di comandi.  Questa procedura dettagliata illustra funzionano dei comandi in questa estensione, ma per informazioni più approfondite, vedere [estensione menu e comandi](../extensibility/extending-menus-and-commands.md).  
  
### <a name="introduction-to-the-code"></a>Introduzione al codice  
 L'estensione guide colonne sono illustrate la dichiarazione di un gruppo di comandi correlati (aggiungere la colonna, rimuovere una colonna, modificare il colore di linea) e quindi tale gruppo in un sottomenu del menu di scelta rapida dell'editor.  L'estensione guide colonne aggiunge anche i comandi principale **modifica** menu ma li mantiene invisibile, descritti come un modello comune di seguito.  
  
 Esistono tre parti per l'implementazione di comandi: ColumnGuideCommandsPackage.cs ColumnGuideCommandsPackage.vsct e ColumnGuideCommands.cs.  Il codice generato dai modelli inserisce un comando di **strumenti** menu che viene visualizzata una finestra di dialogo dell'implementazione.  È possibile esaminare come implementato nel file vsct e ColumnGuideCommands.cs file perché è piuttosto semplice.  Si sostituirà il codice in questi file riportato di seguito.  
  
 Il codice del pacchetto è dichiarazioni standard che sono necessari rilevare che l'estensione sono disponibili comandi e dove posizionare i comandi di Visual Studio.  Quando il pacchetto è stato inizializzato, crea un'istanza della classe di implementazione di comandi.  Visualizzare i comandi di collegamento sopra per altre informazioni sui pacchetti relativi ai comandi.  
  
### <a name="a-common-commands-pattern"></a>Un modello comune di comandi  
 I comandi nell'estensione di guide di colonna sono un esempio di uno schema molto comune in Visual Studio.  Inserire i comandi correlati in un gruppo, e inserire tale gruppo in un menu principale, spesso con "`<CommandFlag>CommandWellOnly</CommandFlag>`" impostata per rendere invisibile il comando.  Inserire i comandi dei menu principale (ad esempio **modifica**) in questo modo fornisce nomi nice (ad esempio **Edit.AddColumnGuide**) che sono utili per individuare i comandi quando si assegnano nuovamente i tasti di scelta rapida in  **Opzioni degli strumenti** e il recupero di completamento quando si richiama i comandi di **finestra di comando**.  
  
 Quindi aggiungere il gruppo di comandi al menu di scelta rapida o sub in cui si prevede di utente di utilizzare i comandi di menu.  Visual Studio vengono trattati `CommandWellOnly` come un flag di invisibilità per i menu principali.  Quando si posiziona lo stesso gruppo di comandi in un menu di scelta rapida o un sottomenu, i comandi sono visibili.  
  
 Come parte del modello comune, l'estensione guide colonne crea un secondo gruppo che contiene un sottomenu singolo.  Il sottomenu contiene a sua volta al primo gruppo con i comandi di Guida quattro colonne.  Il secondo gruppo che contiene il sottomenu è l'asset riutilizzabile che si attribuisce ai menu di scelta rapida diversi, che assegna un sottomenu per i menu di scelta rapida.  
  
### <a name="the-vsct-file"></a>Il File con estensione vsct  
 Il file con estensione vsct dichiara i comandi e in cui passano, insieme a icone e così via.  Sostituire il contenuto del file con estensione vsct con il codice seguente (illustrato di seguito):  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  
  <!--  This is the file that defines the actual layout and type of the commands.  
        It is divided in different sections (e.g. command definition, command  
        placement, ...), with each defining a specific set of properties.  
        See the comment before each section for more details about how to  
        use it. -->  
  
  <!--  The VSCT compiler (the tool that translates this file into the binary  
        format that VisualStudio will consume) has the ability to run a preprocessor  
        on the vsct file; this preprocessor is (usually) the C++ preprocessor, so  
        it is possible to define includes and macros with the same syntax used  
        in C++ files. Using this ability of the compiler here, we include some files  
        defining some of the constants that we will use inside the file. -->  
  
  <!--This is the file that defines the IDs for all the commands exposed by   
      VisualStudio. -->  
  <Extern href="stdidcmd.h"/>  
  
  <!--This header contains the command ids for the menus provided by the shell. -->  
  <Extern href="vsshlids.h"/>  
  
  <!--The Commands section is where commands, menus, and menu groups are defined.  
      This section uses a Guid to identify the package that provides the command   
      defined inside it. -->  
  <Commands package="guidColumnGuideCommandsPkg">  
    <!-- Inside this section we have different sub-sections: one for the menus, another    
    for the menu groups, one for the buttons (the actual commands), one for the combos   
    and the last one for the bitmaps used. Each element is identified by a command id  
    that is a unique pair of guid and numeric identifier; the guid part of the identifier  
    is usually called "command set" and is used to group different command inside a  
    logically related group; your package should define its own command set in order to  
    avoid collisions with command ids defined by other packages. -->  
  
    <!-- In this section you can define new menu groups. A menu group is a container for   
         other menus or buttons (commands); from a visual point of view you can see the   
         group as the part of a menu contained between two lines. The parent of a group   
         must be a menu. -->  
    <Groups>  
  
      <!-- The main group is parented to the edit menu. All the buttons within the group  
           have the "CommandWellOnly" flag, so they're actually invisible, but it means  
           they get canonical names that begin with "Edit". Using placements, the group  
           is also placed in the GuidesSubMenu group. -->  
      <!-- The priority 0xB801 is chosen so it goes just after   
           IDG_VS_EDIT_COMMANDWELL -->  
      <Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"  
             priority="0xB801">  
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />  
      </Group>  
  
      <!-- Group for holding the "Guidelines" sub-menu anchor (the item on the menu that  
           drops the sub menu). The group is parented to  
           the context menu for code windows. That takes care of most editors, but it's  
           also placed in a couple of other windows using Placements -->  
      <Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"   
             priority="0x0600">  
        <Parent guid="guidSHLMainMenu" id="IDM_VS_CTXT_CODEWIN" />  
      </Group>  
  
    </Groups>  
  
    <Menus>  
      <Menu guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" priority="0x1000"  
            type="Menu">  
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup" />  
        <Strings>  
          <ButtonText>&Column Guides</ButtonText>  
        </Strings>  
      </Menu>  
    </Menus>  
  
    <!--Buttons section. -->  
    <!--This section defines the elements the user can interact with, like a menu command or a button   
        or combo box in a toolbar. -->  
    <Buttons>  
      <!--To define a menu group you have to specify its ID, the parent menu and its   
          display priority.   
          The command is visible and enabled by default. If you need to change the   
          visibility, status, etc, you can use the CommandFlag node.  
          You can add more than one CommandFlag node e.g.:  
              <CommandFlag>DefaultInvisible</CommandFlag>  
              <CommandFlag>DynamicVisibility</CommandFlag>  
          If you do not want an image next to your command, remove the Icon node or   
          set it to <Icon guid="guidOfficeIcon" id="msotcidNoIcon" /> -->  
  
      <Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"   
              priority="0x0100" type="Button">  
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />  
        <Icon guid="guidImages" id="bmpPicAddGuide" />  
        <CommandFlag>CommandWellOnly</CommandFlag>  
        <CommandFlag>AllowParams</CommandFlag>  
        <Strings>  
          <ButtonText>&Add Column Guide</ButtonText>  
        </Strings>  
      </Button>  
  
      <Button guid="guidColumnGuidesCommandSet" id="cmdidRemoveColumnGuide"   
              priority="0x0101" type="Button">  
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />  
        <Icon guid="guidImages" id="bmpPicRemoveGuide" />  
        <CommandFlag>CommandWellOnly</CommandFlag>  
        <CommandFlag>AllowParams</CommandFlag>  
        <Strings>  
          <ButtonText>&Remove Column Guide</ButtonText>  
        </Strings>  
      </Button>  
  
      <Button guid="guidColumnGuidesCommandSet" id="cmdidChooseGuideColor"   
              priority="0x0103" type="Button">  
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />  
        <Icon guid="guidImages" id="bmpPicChooseColor" />  
        <CommandFlag>CommandWellOnly</CommandFlag>  
        <Strings>  
          <ButtonText>Column Guide &Color...</ButtonText>  
        </Strings>  
      </Button>  
  
      <Button guid="guidColumnGuidesCommandSet" id="cmdidRemoveAllColumnGuides"   
              priority="0x0102" type="Button">  
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />  
        <CommandFlag>CommandWellOnly</CommandFlag>  
        <Strings>  
          <ButtonText>Remove A&ll Columns</ButtonText>  
        </Strings>  
      </Button>  
    </Buttons>  
  
    <!--The bitmaps section is used to define the bitmaps that are used for the  
        commands.-->  
    <Bitmaps>  
      <!--  The bitmap id is defined in a way that is a little bit different from the  
            others:   
            the declaration starts with a guid for the bitmap strip, then there is the  
            resource id of the bitmap strip containing the bitmaps and then there are   
            the numeric ids of the elements used inside a button definition. An important  
            aspect of this declaration is that the element id   
            must be the actual index (1-based) of the bitmap inside the bitmap strip. -->  
      <Bitmap guid="guidImages" href="Resources\ColumnGuideCommands.png"   
              usedList="bmpPicAddGuide, bmpPicRemoveGuide, bmpPicChooseColor" />  
    </Bitmaps>  
  
  </Commands>  
  
  <CommandPlacements>  
  
    <!-- Define secondary placements for our groups -->  
  
    <!-- Place the group containing the three commands in the sub-menu -->  
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"   
                      priority="0x0100">  
      <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />  
    </CommandPlacement>  
  
    <!-- The HTML editor context menu, for some reason, redefines its own groups  
         so we need to place a copy of our context menu there too. -->  
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"   
                      priority="0x1001">  
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_HTML" />  
    </CommandPlacement>  
  
    <!-- The HTML context menu in Dev12 changed. -->  
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"   
                      priority="0x1001">  
      <Parent guid="CMDSETID_HtmEdGrp_Dev12" id="IDMX_HTM_SOURCE_HTML_Dev12" />  
    </CommandPlacement>  
  
    <!-- Similarly for Script -->  
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"  
                      priority="0x1001">  
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_SCRIPT" />  
    </CommandPlacement>  
  
    <!-- Similarly for ASPX  -->  
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"   
                      priority="0x1001">  
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_ASPX" />  
    </CommandPlacement>  
  
    <!-- Similarly for the XAML editor context menu -->  
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"  
                      priority="0x0600">  
      <Parent guid="guidXamlUiCmds" id="IDM_XAML_EDITOR" />  
    </CommandPlacement>  
  
  </CommandPlacements>  
  
  <!-- This defines the identifiers and their values used above to index resources  
       and specify commands. -->  
  <Symbols>  
    <!-- This is the package guid. -->  
    <GuidSymbol name="guidColumnGuideCommandsPkg"   
                value="{e914e5de-0851-4904-b361-1a3a9d449704}" />  
  
    <!-- This is the guid used to group the menu commands together -->  
    <GuidSymbol name="guidColumnGuidesCommandSet"   
                value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">  
      <IDSymbol name="GuidesContextMenuGroup" value="0x1020" />  
      <IDSymbol name="GuidesMenuItemsGroup" value="0x1021" />  
      <IDSymbol name="GuidesSubMenu" value="0x1022" />  
      <IDSymbol name="cmdidAddColumnGuide" value="0x0100" />  
      <IDSymbol name="cmdidRemoveColumnGuide" value="0x0101" />  
      <IDSymbol name="cmdidChooseGuideColor" value="0x0102" />  
      <IDSymbol name="cmdidRemoveAllColumnGuides" value="0x0103" />  
    </GuidSymbol>  
  
    <GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">  
      <IDSymbol name="bmpPicAddGuide" value="1" />  
      <IDSymbol name="bmpPicRemoveGuide" value="2" />  
      <IDSymbol name="bmpPicChooseColor" value="3" />  
    </GuidSymbol>  
  
    <GuidSymbol name="CMDSETID_HtmEdGrp_Dev12"   
                value="{78F03954-2FB8-4087-8CE7-59D71710B3BB}">  
      <IDSymbol name="IDMX_HTM_SOURCE_HTML_Dev12" value="0x1" />  
    </GuidSymbol>  
  
    <GuidSymbol name="CMDSETID_HtmEdGrp" value="{d7e8c5e1-bdb8-11d0-9c88-0000f8040a53}">  
      <IDSymbol name="IDMX_HTM_SOURCE_HTML" value="0x33" />  
      <IDSymbol name="IDMX_HTM_SOURCE_SCRIPT" value="0x34" />  
      <IDSymbol name="IDMX_HTM_SOURCE_ASPX" value="0x35" />  
    </GuidSymbol>  
  
    <GuidSymbol name="guidXamlUiCmds" value="{4c87b692-1202-46aa-b64c-ef01faec53da}">  
      <IDSymbol name="IDM_XAML_EDITOR" value="0x103" />  
    </GuidSymbol>  
  </Symbols>  
  
</CommandTable>  
  
```  
  
 **GUID**.  Per Visual Studio per trovare i gestori di comando e richiamarli, è necessario assicurarsi che il pacchetto che GUID dichiarato nel file ColumnGuideCommandsPackage.cs (generato dal modello di elemento di progetto) corrisponda il pacchetto che GUID dichiarato nel file vsct (copiato dall'alto ).  Se si utilizza nuovamente questo codice di esempio, assicurarsi che si dispone di un GUID diverso in modo che non sono in conflitto con tutti gli utenti che siano stati copiati questo codice.  
  
 Trovare la riga in ColumnGuideCommandsPackage.cs e copiare il GUID tra virgolette:  
  
```csharp  
public const string PackageGuidString = "ef726849-5447-4f73-8de5-01b9e930f7cd";  
```  
  
 Incolla il GUID nel file vsct in modo da avere la seguente riga `Symbols` dichiarazioni:  
  
```xml  
<GuidSymbol name="guidColumnGuideCommandsPkg"   
            value="{ef726849-5447-4f73-8de5-01b9e930f7cd}" />  
```  
  
 Impostare i GUID per il comando e il file di immagine bitmap deve essere univoco per le estensioni troppo:  
  
```xml  
<GuidSymbol name="guidColumnGuidesCommandSet"   
            value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">  
<GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">  
```  
  
 Tuttavia, non è necessario modificare il set di comandi e bitmap immagine GUID per ottenere il codice per utilizzare questa procedura dettagliata.  Il comando set GUID deve corrispondere la dichiarazione nel file ColumnGuideCommands.cs, ma si sostituirà il contenuto del file. di conseguenza, i GUID corrisponderanno.  
  
 Altri GUID nel file vsct identificare preesistente i menu a cui vengono aggiunti i comandi di Guida di colonna, in modo da non modificare mai.  
  
 **Sezioni del file**.  File vsct ha tre sezioni outer: i comandi, posizioni e simboli.  Nella sezione commands definisce i gruppi di comandi, menu, pulsanti o voci di menu e le bitmap per le icone.  Nella sezione posizioni dichiara esiti gruppi nei menu o posizioni aggiuntive nel menu preesistenti.  La sezione simboli dichiara gli identificatori utilizzati in un' posizione nel file vsct, che rende più leggibile rispetto a GUID e i numeri esadecimali ovunque nel codice con estensione vsct.  
  
 **I comandi di sezione, raggruppa le definizioni**.  Nella sezione commands prima definisce gruppi di comandi.  I gruppi di comandi sono i comandi visualizzati nei menu con piccole righe grigio che separa i gruppi.  Un gruppo può inoltre compilare un sottomenu intero, come nel seguente esempio, e non viene visualizzato il grigio che separa le righe in questo caso.  I file con estensione vsct dichiara due gruppi, il `GuidesMenuItemsGroup` che è l'elemento padre per il `IDM_VS_MENU_EDIT` (principale **modifica** menu) e `GuidesContextMenuGroup` che è l'elemento padre per il `IDM_VS_CTXT_CODEWIN` (menu di scelta rapida dell'editor di codice).  
  
 La seconda dichiarazione gruppo ha un `0x0600` priorità:  
  
```xml  
<Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"   
             priority="0x0600">  
```  
  
 L'idea è di inserire la colonna Guide sottomenu alla fine di qualsiasi menu di scelta rapida in cui è aggiungere il gruppo di menu secondario.  Tuttavia, è necessario non presupporre che si conosce meglio e forza il sottomenu siano sempre ultima con una priorità pari a `0xFFFF`.  È necessario sperimentare con questo numero per vedere dove il sottomenu si trova nel menu di scelta rapida in cui inserirlo.  In questo caso `0x0600` è sufficientemente elevato da inserire alla fine del menu per quanto riguarda possiamo vedere, ma lascia spazio ad altri utenti per progettare l'estensione per essere inferiore all'estensione di guide di colonna, se necessario.  
  
 **Sezione, definizione del menu dei comandi**.  Avanti la sezione comando definisce il sottomenu `GuidesSubMenu`, che è associato al `GuidesContextMenuGroup`.  Il `GuidesContextMenuGroup` è il gruppo è aggiungere tutti i menu di contesto pertinente.  Nella sezione posizioni, il codice inserisce il gruppo con i comandi di Guida quattro colonne questo menu sub.  
  
 **Sezione dei comandi, pulsanti definizioni**.  Nella sezione commands definisce quindi le voci di menu o pulsanti che sono le quattro colonne Guida comandi.  `CommandWellOnly`, discussi in precedenza, significa che i comandi non sono visibili quando viene inserita in un menu principale.  Due della voce di menu pulsante dichiarazioni (Guida per aggiungere e rimuovere Guida) hanno anche un `AllowParams` flag:  
  
```xml  
<CommandFlag>AllowParams</CommandFlag>  
```  
  
 Questo flag consente, insieme alla possibilità di posizioni di menu principale, il comando per ricevere argomenti quando viene richiamato il gestore del comando.  Se l'utente richiama il comando nella finestra di comando, l'argomento Ottiene passato al gestore del comando in argomenti dell'evento.  
  
 **Comando sezioni, definizioni di bitmap**.  Infine, nella sezione commands dichiara la bitmap o icone utilizzate per i comandi.  Si tratta di una dichiarazione semplice che identifica la risorsa del progetto ed elenca gli indici basati su una delle icone utilizzate.  La sezione di simboli del file con estensione vsct dichiara i valori degli identificatori utilizzati come gli indici.  Questa procedura dettagliata viene utilizzata la striscia di bitmap fornita con il modello di elemento di comando personalizzato aggiunto al progetto.  
  
 **Sezione posizionamenti**.  Dopo i comandi è la sezione posizioni:  La prima è in cui il codice aggiunge il primo gruppo discussi in precedenza che contiene la Guida di quattro colonna comandi al menu sub in cui vengono visualizzati i comandi:  
  
```xml  
<CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"   
                  priority="0x0100">  
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />  
</CommandPlacement>  
```  
  
 Tutte le selezioni host per aggiungere il `GuidesContextMenuGroup` (che contiene il `GuidesSubMenu`) per altri menu di scelta rapida dell'editor.  Quando il codice dichiarato il `GuidesContextMenuGroup`, è stato definito come padre al menu di scelta rapida dell'editor di codice.  Che è il motivo per cui non viene visualizzata una posizione per il menu di scelta rapida dell'editor di codice.  
  
 **Simboli sezione**.  Come descritto in precedenza, la sezione simboli dichiara gli identificatori utilizzati in un' posizione nel file vsct, che rende più leggibile rispetto a GUID e i numeri esadecimali ovunque nel codice con estensione vsct.  Gli aspetti importanti in questa sezione sono che il GUID del pacchetto devono essere coerenti con la dichiarazione di classe del pacchetto e il set di comandi che GUID deve essere coerente con la dichiarazione della classe di implementazione del comando.  
  
## <a name="implementing-the-commands"></a>Implementazione dei comandi  
 Il file ColumnGuideCommands.cs implementa i comandi e associa i gestori.  Quando Visual Studio il pacchetto viene caricato e inizializzato, il pacchetto è a sua volta chiama `Initialize` nella classe di implementazione di comandi.  L'inizializzazione di comandi crea semplicemente un'istanza della classe e il costruttore Aggancia tutti i gestori di comando.  
  
 Sostituire il contenuto del file ColumnGuideCommands.cs con il codice seguente (illustrato di seguito):  
  
```csharp  
using System;  
using System.ComponentModel.Design;  
using System.Globalization;  
using Microsoft.VisualStudio.Shell;  
using Microsoft.VisualStudio.Shell.Interop;  
using Microsoft.VisualStudio.TextManager.Interop;  
using Microsoft.VisualStudio.Text.Editor;  
using Microsoft.VisualStudio;  
  
namespace ColumnGuides  
{  
    /// <summary>  
    /// Command handler  
    /// </summary>  
    internal sealed class ColumnGuideCommands  
    {  
  
        const int cmdidAddColumnGuide = 0x0100;  
        const int cmdidRemoveColumnGuide = 0x0101;  
        const int cmdidChooseGuideColor = 0x0102;  
        const int cmdidRemoveAllColumnGuides = 0x0103;  
  
        /// <summary>  
        /// Command menu group (command set GUID).  
        /// </summary>  
        static readonly Guid CommandSet =   
            new Guid("c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e");  
  
        /// <summary>  
        /// VS Package that provides this command, not null.  
        /// </summary>  
        private readonly Package package;  
  
        OleMenuCommand _addGuidelineCommand;  
        OleMenuCommand _removeGuidelineCommand;  
  
        /// <summary>  
        /// Initializes the singleton instance of the command.  
        /// </summary>  
        /// <param name="package">Owner package, not null.</param>  
        public static void Initialize(Package package)  
        {  
            Instance = new ColumnGuideCommands(package);  
        }  
  
        /// <summary>  
        /// Gets the instance of the command.  
        /// </summary>  
        public static ColumnGuideCommands Instance  
        {  
            get;  
            private set;  
        }  
  
        /// <summary>  
        /// Initializes a new instance of the <see cref="ColumnGuideCommands"/> class.  
        /// Adds our command handlers for menu (commands must exist in the command   
        /// table file)  
        /// </summary>  
        /// <param name="package">Owner package, not null.</param>  
        private ColumnGuideCommands(Package package)  
        {  
            if (package == null)  
            {  
                throw new ArgumentNullException("package");  
            }  
  
            this.package = package;  
  
            // Add our command handlers for menu (commands must exist in the .vsct file)  
  
            OleMenuCommandService commandService =  
                this.ServiceProvider.GetService(typeof(IMenuCommandService))  
                    as OleMenuCommandService;  
            if (commandService != null)  
            {  
                // Add guide  
                _addGuidelineCommand =   
                    new OleMenuCommand(AddColumnGuideExecuted, null,  
                                       AddColumnGuideBeforeQueryStatus,  
                                       new CommandID(ColumnGuideCommands.CommandSet,  
                                                     cmdidAddColumnGuide));  
                _addGuidelineCommand.ParametersDescription = "<column>";  
                commandService.AddCommand(_addGuidelineCommand);  
                // Remove guide  
                _removeGuidelineCommand =  
                    new OleMenuCommand(RemoveColumnGuideExecuted, null,  
                                       RemoveColumnGuideBeforeQueryStatus,  
                                       new CommandID(ColumnGuideCommands.CommandSet,  
                                                     cmdidRemoveColumnGuide));  
                _removeGuidelineCommand.ParametersDescription = "<column>";  
                commandService.AddCommand(_removeGuidelineCommand);  
                // Choose color  
                commandService.AddCommand(  
                    new MenuCommand(ChooseGuideColorExecuted,  
                                    new CommandID(ColumnGuideCommands.CommandSet,  
                                                  cmdidChooseGuideColor)));  
                // Remove all  
                commandService.AddCommand(  
                    new MenuCommand(RemoveAllGuidelinesExecuted,  
                                    new CommandID(ColumnGuideCommands.CommandSet,  
                                                  cmdidRemoveAllColumnGuides)));  
            }  
        }  
  
        /// <summary>  
        /// Gets the service provider from the owner package.  
        /// </summary>  
        private IServiceProvider ServiceProvider  
        {  
            get  
            {  
                return this.package;  
            }  
        }  
  
        private void AddColumnGuideBeforeQueryStatus(object sender, EventArgs e)  
        {  
            int currentColumn = GetCurrentEditorColumn();  
            _addGuidelineCommand.Enabled =  
                GuidesSettingsManager.CanAddGuideline(currentColumn);  
        }  
  
        private void RemoveColumnGuideBeforeQueryStatus(object sender, EventArgs e)  
        {  
            int currentColumn = GetCurrentEditorColumn();  
            _removeGuidelineCommand.Enabled =  
                GuidesSettingsManager.CanRemoveGuideline(currentColumn);  
        }  
  
        private int GetCurrentEditorColumn()  
        {  
            IVsTextView view = GetActiveTextView();  
            if (view == null)  
            {  
                return -1;  
            }  
  
            try  
            {  
                IWpfTextView textView = GetTextViewFromVsTextView(view);  
                int column = GetCaretColumn(textView);  
  
                // Note: GetCaretColumn returns 0-based positions. Guidelines are 1-based  
                // positions.  
                // However, do not subtract one here since the caret is positioned to the  
                // left of  
                // the given column and the guidelines are positioned to the right. We  
                // want the  
                // guideline to line up with the current caret position. e.g. When the  
                // caret is  
                // at position 1 (zero-based), the status bar says column 2. We want to  
                // add a  
                // guideline for column 1 since that will place the guideline where the  
                // caret is.  
                return column;  
            }  
            catch (InvalidOperationException)  
            {  
                return -1;  
            }  
        }  
  
        /// <summary>  
        /// Find the active text view (if any) in the active document.  
        /// </summary>  
        /// <returns>The IVsTextView of the active view, or null if there is no active  
        /// document or the  
        /// active view in the active document is not a text view.</returns>  
        private IVsTextView GetActiveTextView()  
        {  
            IVsMonitorSelection selection =  
                this.ServiceProvider.GetService(typeof(IVsMonitorSelection))  
                                                    as IVsMonitorSelection;  
            object frameObj = null;  
            ErrorHandler.ThrowOnFailure(  
                selection.GetCurrentElementValue(  
                    (uint)VSConstants.VSSELELEMID.SEID_DocumentFrame, out frameObj));  
  
            IVsWindowFrame frame = frameObj as IVsWindowFrame;  
            if (frame == null)  
            {  
                return null;  
            }  
  
            return GetActiveView(frame);  
        }  
  
        private static IVsTextView GetActiveView(IVsWindowFrame windowFrame)  
        {  
            if (windowFrame == null)  
            {  
                throw new ArgumentException("windowFrame");  
            }  
  
            object pvar;  
            ErrorHandler.ThrowOnFailure(  
                windowFrame.GetProperty((int)__VSFPROPID.VSFPROPID_DocView, out pvar));  
  
            IVsTextView textView = pvar as IVsTextView;  
            if (textView == null)  
            {  
                IVsCodeWindow codeWin = pvar as IVsCodeWindow;  
                if (codeWin != null)  
                {  
                    ErrorHandler.ThrowOnFailure(codeWin.GetLastActiveView(out textView));  
                }  
            }  
            return textView;  
        }  
  
        private static IWpfTextView GetTextViewFromVsTextView(IVsTextView view)  
        {  
  
            if (view == null)  
            {  
                throw new ArgumentNullException("view");  
            }  
  
            IVsUserData userData = view as IVsUserData;  
            if (userData == null)  
            {  
                throw new InvalidOperationException();  
            }  
  
            object objTextViewHost;  
            if (VSConstants.S_OK  
                   != userData.GetData(Microsoft.VisualStudio  
                                                .Editor  
                                                .DefGuidList.guidIWpfTextViewHost,  
                                       out objTextViewHost))  
            {  
                throw new InvalidOperationException();  
            }  
  
            IWpfTextViewHost textViewHost = objTextViewHost as IWpfTextViewHost;  
            if (textViewHost == null)  
            {  
                throw new InvalidOperationException();  
            }  
  
            return textViewHost.TextView;  
        }  
  
        /// <summary>  
        /// Given an IWpfTextView, find the position of the caret and report its column  
        /// number. The column number is 0-based  
        /// </summary>  
        /// <param name="textView">The text view containing the caret</param>  
        /// <returns>The column number of the caret's position. When the caret is at the  
        /// leftmost column, the return value is zero.</returns>  
        private static int GetCaretColumn(IWpfTextView textView)  
        {  
            // This is the code the editor uses to populate the status bar.  
            Microsoft.VisualStudio.Text.Formatting.ITextViewLine caretViewLine =  
                textView.Caret.ContainingTextViewLine;  
            double columnWidth = textView.FormattedLineSource.ColumnWidth;  
            return (int)(Math.Round((textView.Caret.Left - caretViewLine.Left)  
                                       / columnWidth));  
        }  
  
        /// <summary>  
        /// Determine the applicable column number for an add or remove command.  
        /// The column is parsed from command arguments, if present. Otherwise  
        /// the current position of the caret is used to determine the column.  
        /// </summary>  
        /// <param name="e">Event args passed to the command handler.</param>  
        /// <returns>The column number. May be negative to indicate the column number is  
        /// unavailable.</returns>  
        /// <exception cref="ArgumentException">The column number parsed from event args  
        /// was not a valid integer.</exception>  
        private int GetApplicableColumn(EventArgs e)  
        {  
            var inValue = ((OleMenuCmdEventArgs)e).InValue as string;  
            if (!string.IsNullOrEmpty(inValue))  
            {  
                int column;  
                if (!int.TryParse(inValue, out column) || column < 0)  
                    throw new ArgumentException("Invalid column");  
                return column;  
            }  
  
            return GetCurrentEditorColumn();  
        }  
  
        /// <summary>  
        /// This function is the callback used to execute a command when the a menu item  
        /// is clicked. See the Initialize method to see how the menu item is associated  
        /// to this function using the OleMenuCommandService service and the MenuCommand  
        /// class.  
        /// </summary>  
        private void AddColumnGuideExecuted(object sender, EventArgs e)  
        {  
            int column = GetApplicableColumn(e);  
            if (column >= 0)  
            {  
                GuidesSettingsManager.AddGuideline(column);  
            }  
        }  
  
        private void RemoveColumnGuideExecuted(object sender, EventArgs e)  
        {  
            int column = GetApplicableColumn(e);  
            if (column >= 0)  
            {  
                GuidesSettingsManager.RemoveGuideline(column);  
            }  
        }  
  
        private void RemoveAllGuidelinesExecuted(object sender, EventArgs e)  
        {  
            GuidesSettingsManager.RemoveAllGuidelines();  
        }  
  
        private void ChooseGuideColorExecuted(object sender, EventArgs e)  
        {  
            System.Windows.Media.Color color = GuidesSettingsManager.GuidelinesColor;  
  
            using (System.Windows.Forms.ColorDialog picker =   
                new System.Windows.Forms.ColorDialog())  
            {  
                picker.Color = System.Drawing.Color.FromArgb(255, color.R, color.G,  
                                                             color.B);  
                if (picker.ShowDialog() == System.Windows.Forms.DialogResult.OK)  
                {  
                    GuidesSettingsManager.GuidelinesColor =   
                        System.Windows.Media.Color.FromRgb(picker.Color.R,  
                                                           picker.Color.G,   
                                                           picker.Color.B);  
                }  
            }  
        }  
  
    }  
}  
  
```  
  
 **Risolvere i riferimenti**.  Manca un riferimento a questo punto.  Premere il pulsante destro del puntatore sul nodo Riferimenti in Esplora soluzioni.  Scegliere il **Aggiungi...**  comando.  Il **Aggiungi riferimento** finestra di dialogo include una casella di ricerca nell'angolo superiore destro.  Immettere "editor" (senza le virgolette doppie).  Scegliere il **Microsoft.VisualStudio.Editor** elemento (è necessario selezionare la casella a sinistra dell'elemento, non è sufficiente seleziona l'elemento) e scegliere **OK** per aggiungere il riferimento.  
  
 **Inizializzazione**.  Quando si inizializza la classe del pacchetto, chiama `Initialize` nella classe di implementazione di comandi.  Il `ColumnGuideCommands` inizializzazione crea un'istanza della classe e Salva l'istanza di classe e il riferimento del pacchetto nei membri della classe.  
  
 Ecco uno del gruppo di continuità gestore hook del comando dal costruttore della classe:  
  
```csharp  
_addGuidelineCommand =   
    new OleMenuCommand(AddColumnGuideExecuted, null,  
                       AddColumnGuideBeforeQueryStatus,  
                       new CommandID(ColumnGuideCommands.CommandSet,  
                                     cmdidAddColumnGuide));  
  
```  
  
 Si crea un `OleMenuCommand`.  Visual Studio utilizza il sistema di comando di Microsoft Office.  Gli argomenti chiavi durante la creazione di un OleMenuCommand è la funzione che implementa il comando (`AddColumnGuideExecuted`), la funzione da chiamare quando un menu con il comando in Visual Studio (`AddColumnGuideBeforeQueryStatus`) e l'ID di comando.  Visual studio chiama la funzione di stato query prima della visualizzazione di un comando in un menu in modo che il comando possa stesso invisibile o grigio per una visualizzazione specifica del menu (ad esempio, la disattivazione **copia** se non è stata effettuata alcuna selezione), modificare la relativa icona, o anche modificarne il nome (ad esempio, da aggiungere un elemento per rimuovere un elemento) e così via.  L'ID di comando deve corrispondere a un ID di comando dichiarato nel file vsct.  Impostare le stringhe per il comando e le guide alla colonna aggiungere comando deve corrispondere tra il file con estensione vsct e il ColumnGuideCommands.cs.  
  
 Quando gli utenti richiamano il comando tramite la finestra di comando (come illustrato di seguito), la riga seguente fornisce assistenza per:  
  
```csharp  
_addGuidelineCommand.ParametersDescription = "<column>";  
```  
  
 **Una query sullo stato**.  Le funzioni di stato query `AddColumnGuideBeforeQueryStatus` e `RemoveColumnGuideBeforeQueryStatus` verificare alcune impostazioni (ad esempio il numero massimo di guide o colonna max) o se è presente una Guida di colonna da rimuovere.  I comandi consentono se sono soddisfatte le condizioni.  Query sullo stato funzioni devono essere molto efficiente perché vengono eseguite ogni volta che Visual Studio visualizza un menu, per ogni comando del menu.  
  
 **Funzione AddColumnGuideExecuted**.  La parte interessante di aggiunta di una Guida è facile evincere la posizione di visualizzazione e del punto di inserimento nell'editor corrente.  Questa funzione chiama innanzitutto `GetApplicableColumn` che controlla se non c'è un argomento fornito dall'utente negli argomenti di eventi del gestore dei comandi e, se presente, la funzione controlla la visualizzazione dell'editor:  
  
```csharp  
private int GetApplicableColumn(EventArgs e)  
{  
    var inValue = ((OleMenuCmdEventArgs)e).InValue as string;  
    if (!string.IsNullOrEmpty(inValue))  
    {  
        int column;  
        if (!int.TryParse(inValue, out column) || column < 0)  
            throw new ArgumentException("Invalid column");  
        return column;  
    }  
  
    return GetCurrentEditorColumn();  
}  
  
```  
  
 `GetCurrentEditorColumn` deve essere esamino più a fondo per ottenere un <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> visualizzazione del codice.  Se si esegue la traccia tramite `GetActiveTextView`, `GetActiveView`, e `GetTextViewFromVsTextView`, è possibile vedere come eseguire questa operazione.  Di seguito è riportato il codice pertinente astratto, a partire dalla selezione corrente, quindi ottenere frame della selezione e recupero DocView del frame come un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>, quindi ottenendo un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> dal IVsTextView, recupero di un host, visualizzazione e Infine IWpfTextView:  
  
```csharp  
   IVsMonitorSelection selection =  
       this.ServiceProvider.GetService(typeof(IVsMonitorSelection))   
           as IVsMonitorSelection;  
   object frameObj = null;  
  
ErrorHandler.ThrowOnFailure(selection.GetCurrentElementValue(  
                                (uint)VSConstants.VSSELELEMID.SEID_DocumentFrame,  
                                out frameObj));  
  
   IVsWindowFrame frame = frameObj as IVsWindowFrame;  
   if (frame == null)  
       <<do nothing>>;  
  
...  
   object pvar;  
   ErrorHandler.ThrowOnFailure(frame.GetProperty((int)__VSFPROPID.VSFPROPID_DocView,  
                                                  out pvar));  
  
   IVsTextView textView = pvar as IVsTextView;  
   if (textView == null)  
   {  
       IVsCodeWindow codeWin = pvar as IVsCodeWindow;  
       if (codeWin != null)  
       {  
           ErrorHandler.ThrowOnFailure(codeWin.GetLastActiveView(out textView));  
       }  
   }  
  
...  
   if (textView == null)  
       <<do nothing>>  
  
   IVsUserData userData = textView as IVsUserData;  
   if (userData == null)  
       <<do nothing>>  
  
   object objTextViewHost;  
   if (VSConstants.S_OK   
           != userData.GetData(Microsoft.VisualStudio.Editor.DefGuidList  
                                                            .guidIWpfTextViewHost,  
                                out objTextViewHost))  
   {  
       <<do nothing>>  
   }  
  
   IWpfTextViewHost textViewHost = objTextViewHost as IWpfTextViewHost;  
   if (textViewHost == null)  
       <<do nothing>>  
  
   IWpfTextView textView = textViewHost.TextView;  
  
```  
  
 Dopo aver creato un oggetto IWpfTextView, è possibile ottenere la colonna in cui si trova il punto di inserimento:  
  
```csharp  
private static int GetCaretColumn(IWpfTextView textView)  
{  
    // This is the code the editor uses to populate the status bar.  
    Microsoft.VisualStudio.Text.Formatting.ITextViewLine caretViewLine =  
        textView.Caret.ContainingTextViewLine;  
    double columnWidth = textView.FormattedLineSource.ColumnWidth;  
    return (int)(Math.Round((textView.Caret.Left - caretViewLine.Left)  
                                / columnWidth));  
}  
  
```  
  
 Con la colonna corrente in corso in cui l'utente ha fatto clic, il codice chiama semplicemente nella gestione delle impostazioni per aggiungere o rimuovere la colonna.  Gestione delle impostazioni di generazione dell'evento per cui tutti `ColumnGuideAdornment` oggetti in attesa.  Quando viene generato l'evento, questi oggetti aggiornare le visualizzazioni di testo associato con nuove impostazioni della Guida di colonna.  
  
## <a name="invoking-command-from-the-command-window"></a>Richiama comando dalla finestra di comando  
 L'esempio di guide di colonna consente agli utenti di richiamare i due comandi della finestra di comando come una forma di estensibilità.  Se si utilizza il **View &#124; altre finestre &#124; finestra di comando** comando, è possibile visualizzare la finestra di comando.  È possibile interagire con la finestra di comando, immettere "Modifica" e con il completamento del nome di comando e fornire l'argomento 120, disporre di quanto segue:  
  
```  
> Edit.AddColumnGuide 120  
>  
```  
  
 Gli elementi dell'esempio di questo approccio sono nelle dichiarazioni di file con estensione vsct, abilitare il `ColumnGuideCommands` costruttore della classe quando si esegue l'hook dei gestori di comando e le implementazioni di gestori di comandi che consentono di controllare gli argomenti dell'evento.  
  
 Si è visto "`<CommandFlag>CommandWellOnly</CommandFlag>`" nel file vsct, nonché di posizioni nel menu principale modifica anche se è non visualizzare i comandi di **modifica** menu dell'interfaccia utente.  Dal menu di modifica principale che offre loro nomi come **Edit.AddColumnGuide**.  I comandi di dichiarazione che contiene che i quattro comandi posizionato direttamente il gruppo dal menu Modifica gruppo:  
  
```xml  
<Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"  
             priority="0xB801">  
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />  
      </Group>  
  
```  
  
 La sezione di pulsanti dichiarata in un secondo momento i comandi `CommandWellOnly` per mantenerle invisibile nel menu principale e dichiarato con `AllowParams`:  
  
```xml  
<Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"   
        priority="0x0100" type="Button">  
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />  
  <Icon guid="guidImages" id="bmpPicAddGuide" />  
  <CommandFlag>CommandWellOnly</CommandFlag>  
  <CommandFlag>AllowParams</CommandFlag>  
  
```  
  
 Si è visto il gestore del comando di associare il codice nel `ColumnGuideCommands` costruttore della classe fornita una descrizione del parametro consentito:  
  
```csharp  
_addGuidelineCommand.ParametersDescription = "<column>";  
  
```  
  
 Si è visto il `GetApplicableColumn` funzione controlli `OleMenuCmdEventArgs` per un valore prima di archiviare la visualizzazione dell'editor per una colonna corrente:  
  
```csharp  
private int GetApplicableColumn(EventArgs e)  
{  
    var inValue = ((OleMenuCmdEventArgs)e).InValue as string;  
    if (!string.IsNullOrEmpty(inValue))  
    {  
        int column;  
        if (!int.TryParse(inValue, out column) || column < 0)  
            throw new ArgumentException("Invalid column");  
        return column;  
    }  
  
```  
  
## <a name="trying-your-extension"></a>Tentativo di estensione  
 È ora possibile premere **F5** per eseguire l'estensione di guide di colonna.  Aprire un file di testo e utilizzare il menu di scelta rapida dell'editor per aggiungere le linee guida, rimuoverli e modificarne il colore.  È necessario fare clic sul testo (non gli spazi vuoti superato la fine della riga) per aggiungere una colonna Guida o l'editor aggiunge l'ultima colonna della riga.  Se si utilizza la finestra di comando e richiamano i comandi con un argomento, è possibile aggiungere le guide di colonna in qualsiasi punto.  
  
 Se si desidera provare diversi elementi commandplacement, modificare i nomi, icone e così via, e di problemi con visualizzato il codice più recente nel menu di Visual Studio, è possibile ripristinare l'hive sperimentale in cui si esegue il debug.  Visualizzare il **Menu Start di Windows** e digitare "Ripristina".  Cercare e richiamare il comando **reimpostare l'istanza sperimentale di Studio Visual Avanti**.  Viene pulito hive del Registro di sistema sperimentale di tutti i componenti di estensione.  Non eliminare le impostazioni dei componenti, pertanto tutte le guide era al momento dell'arresto hive sperimentale di Visual Studio sarà ancora disponibile quando il codice legge l'archivio di impostazioni all'avvio successivo.  
  
## <a name="finished-code-project"></a>Progetto di codice completato  
 Vi sarà presto un progetto di github degli esempi di estensibilità di Visual Studio e il progetto completato sarà disponibile.  Questo argomento per il punto di quel punto verrà aggiornato.  Il progetto di esempio completo potrebbe essere GUID diversi e avrà una striscia di bitmap diversi per le icone di comando.  
  
 È possibile provare una versione della funzionalità di guide di colonna con questo Visual Studio Gallery[estensione](https://visualstudiogallery.msdn.microsoft.com/da227a0b-0e31-4a11-8f6b-3a149cf2e459?SRC=Home).  
  
## <a name="see-also"></a>Vedere anche  
 [All'interno dell'Editor](../extensibility/inside-the-editor.md)   
 [Estensione dell'Editor e i servizi di linguaggio](../extensibility/extending-the-editor-and-language-services.md)   
 [Servizio di linguaggio e i punti di estensione di Editor](../extensibility/language-service-and-editor-extension-points.md)   
 [Estensione di menu e comandi](../extensibility/extending-menus-and-commands.md)   
 [Aggiunta di un sottomenu a un Menu](../extensibility/adding-a-submenu-to-a-menu.md)   
 [Creazione di un'estensione con un modello di elemento dell'editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)