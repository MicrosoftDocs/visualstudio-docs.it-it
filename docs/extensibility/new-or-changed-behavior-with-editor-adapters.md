---
title: Comportamento nuovo o modificato con schede Editor | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapter behavior
ms.assetid: 5555b116-cfdb-4773-ba62-af80fda64abd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 22028b1b2725f184c3d5748f2885a17d4bff0c60
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="new-or-changed-behavior-with-editor-adapters"></a>Comportamento nuovo o modificato con schede dell'Editor
Se si sta aggiornando il codice che è stato scritto in versioni precedenti di editor di componenti di base di Visual Studio e si prevede di utilizzare l'editor schede (o shim) invece di usare la nuova API, è necessario essere consapevoli delle seguenti differenze nel comportamento delle schede di editor rispetto all'editor principale precedente.  
  
## <a name="features"></a>Funzionalità  
  
#### <a name="using-setsite"></a>Utilizzo di SetSite)  
 È necessario chiamare <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite.SetSite%2A> quando si CoCreate i buffer di testo, visualizzazioni di testo e codice di windows prima di eseguire operazioni su di essi. Tuttavia, ciò non è necessaria se si utilizza il <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> per crearle, perché la chiamata metodo di creazione metodi del servizio, questo <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.SetSite%2A>.  
  
#### <a name="hosting-ivscodewindow-and-ivstextview-in-your-own-content"></a>Hosting IVsCodeWindow e IVsTextView nel proprio contenuto.  
 È possibile ospitare entrambi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> i contenuti desiderati utilizzando la modalità di Win32 o WPF. Tuttavia, è necessario tenere presente che esistono alcune differenze nelle due modalità.  
  
##### <a name="using-win32-and-wpf-versions-of-ivscodewindow"></a>Versioni di Win32 e WPF di IVsCodeWindow  
 Finestra editor del codice è derivata da <xref:Microsoft.VisualStudio.Shell.WindowPane>, che implementa Win32 precedente <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interfaccia nonché il nuovo controllo WPF <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> interfaccia. È possibile utilizzare il <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsWindowPane%23CreatePaneWindow%2A> metodo per creare un ambiente di hosting basato su HWND, o <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsUIElementPane%23CreateUIElementPane%2A> metodo per creare un ambiente di hosting di WPF. L'editor sottostante utilizza sempre WPF, ma è possibile creare il tipo di riquadro che soddisfi i requisiti di hosting se si intende incorporare questo riquadro direttamente nel proprio contenuto.  
  
##### <a name="using-win32-and-wpf-versions-of-ivstextview"></a>Versioni di Win32 e WPF di IVsTextView  
 È possibile impostare un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> in modalità Win32 o in modalità WPF.  
  
 Quando un factory dell'editor viene creata una visualizzazione di testo, per impostazione predefinita è ospitato all'interno di un HWND, e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> restituisce un HWND. Utilizzare questa modalità non di incorporare l'editor all'interno di un controllo WPF.  
  
 Per impostare una visualizzazione di testo alla modalità WPF, è necessario chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.Initialize%2A> e passare <xref:Microsoft.VisualStudio.TextManager.Interop.TextViewInitFlags3> come uno dell'inizializzazione flag nel `InitView` parametro. È possibile ottenere il <xref:System.Windows.FrameworkElement> chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane.CreateUIElementPane%2A>.  
  
 Modalità WPF è diverso dalla modalità Win32 in due modi. La visualizzazione del testo in primo luogo, può essere ospitata in un contesto WPF. È possibile accedere al riquadro WPF eseguendo il cast di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> e chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElement.GetUIObject%2A>. In secondo luogo, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> comunque restituisce un HWND, ma questo HWND può essere usata solo per controllare la posizione e impostare lo stato attivo su di esso. Non utilizzare questo HWND per rispondere a un messaggio WM_PAINT, perché come l'editor Disegna la finestra non avrà alcun effetto. HWND è presente solo per semplificare la transizione al nuovo editor di codice tramite le schede. È consigliabile che non devono usare `VIF_NO_HWND_SUPPORT` se il componente richiede un HWND, a causa di limitazioni nell'HWND restituito da `GetWindowHandle` in questa modalità.  
  
#### <a name="passing-arrays-as-parameters-in-native-code"></a>Passaggio di matrici come parametri in codice nativo  
 Sono disponibili molti metodi nell'API legacy editor che dispongono di parametri che includono una matrice e il relativo conteggio. Esempi sono:  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.AppendViewOnlyMarkerTypes%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.RemoveViewOnlyMarkerTypes%2A>  
  
 Se si chiama questi metodi nel codice nativo, è necessario passare in un solo elemento alla volta. Se si passa in più di un elemento, la chiamata verrà rifiutata a causa di problemi con l'implementazione di interoperabilità primario.  
  
 Il problema è più complesso con metodi come <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetIgnoreMarkerTypes%2A>. Ogni volta che viene chiamato questo metodo, Cancella l'elenco precedente dei tipi di marcatore ignorati, pertanto non è possibile semplicemente chiamare questo metodo per tre volte con tre tipi di marcatore diverso. L'unico remedy consiste nel chiamare questo metodo solo nel codice gestito.  
  
#### <a name="threading"></a>Threading  
 È necessario chiamare l'adapter buffer sempre dal thread dell'interfaccia utente. La scheda di buffer è un oggetto gestito, che significa che la chiamata al suo interno da codice gestito possono ignorare il marshalling COM e la chiamata verrà automaticamente effettuare il marshalling al thread dell'interfaccia utente.  Se si chiama l'adapter di buffer da un thread in background, è necessario utilizzare <xref:System.Windows.Threading.Dispatcher.Invoke%2A> o un metodo simile.  
  
#### <a name="lockbuffer-methods"></a>Metodi LockBuffer  
 Tutti i metodi LockBuffer() sono deprecati. Esempi sono:  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.LockBuffer%2A>  
  
#### <a name="commit-events"></a>Eseguire il commit di eventi  
 Eseguire il commit non sono supportati. Chiamare il metodo che richiede per questi eventi, il metodo restituire un codice di errore.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUndoRedoClusterWithCommitEvents>  
  
#### <a name="texteditorevents"></a>TextEditorEvents  
 Il <xref:EnvDTE.TextEditorEvents> non attivazione non è più in commit (). Vengono invece attivati a ogni modifica del testo.  
  
#### <a name="text-markers"></a>Marcatori di testo  
 È necessario chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker.Invalidate%2A> su <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker> oggetti quando vengono rimossi. Nelle versioni precedenti, è necessario solo rilasciare i marcatori.  
  
#### <a name="line-numbers"></a>Numeri di riga  
 Per un'ampia gamma di metodi su <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>, i numeri di riga corrispondano ai numeri di riga del buffer sottostante, numeri di riga non che il fattore nella struttura e di ritorno a capo automatico, come in Visual Studio 2008.  
  
 I metodi interessati includono le operazioni seguenti (l'elenco non è completo):  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.CenterLines%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetCaretPos%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineAndColumn%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetNearestPosition%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetPointOfLineColumn%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetTextStream%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWordExtent%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.ReplaceTextOnLine%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetCaretPos%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetSelection%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetTopLine%2A>  
  
#### <a name="outlining"></a>struttura  
 I client di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> visualizzeranno solo le aree della struttura che sono stati aggiunti mediante <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSessionEx.AddHiddenRegionsEx%2A>. Non visualizzerà le aree ad hoc, perché non aggiunti tramite le schede dell'editor. Analogamente, questi saranno visibili ai client non aggiunte dai linguaggi (c# e C++ inclusi) che utilizzano il nuovo editor di codice, piuttosto che le schede dell'editor di aree della struttura.  
  
#### <a name="line-heights"></a>Altezza di riga  
 Nel nuovo editor, le righe di testo possono avere altezza diversa, a seconda delle dimensioni del carattere e le trasformazioni di riga possibile che è possano spostare la riga relativa alle altre linee. L'altezza di riga restituito da metodi quali <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineHeight%2A> è l'altezza di una riga con dimensioni del carattere predefinite non trasformazioni di riga applicate. L'altezza o meno potrebbe non riflettere l'effettivo altezza di una riga nella visualizzazione.  
  
#### <a name="eventing-and-undo"></a>Gestione degli eventi e annullamento  
 Nell'editor di nuovo, la visualizzazione continua a eseguire operazioni quali il rendering e la generazione di eventi in modo continuo, anche quando è aperto un cluster di annullamento. Questo comportamento è diverso da quello delle visualizzazioni legacy, che non ha eseguito le operazioni fino a dopo la chiusura del cluster di annullamento.  
  
#### <a name="intellisense"></a>IntelliSense  
  
-   Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateTipWindow%2A> metodo avrà esito negativo se viene passato in una classe che non implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextTipWindow2> o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow3>. Win32 personalizzato popup proprietario non sono più supportate.  
  
#### <a name="smarttags"></a>Degli smart tag  
 Non è supportata per gli smart tag creati con adapter <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagData>, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow>, e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow2> interfacce.  
  
#### <a name="dte"></a>DTE  
 <xref:EnvDTE80.IncrementalSearch> Non è implementata.  
  
## <a name="unimplemented-methods"></a>Non implementati  
 Alcuni metodi non sono state implementate della scheda di buffer testo, un adattatore di visualizzazione di testo e un adapter livello testo.  
  
|Interfaccia|Non implementato|  
|---------------|---------------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|`Reload(false)` Non è implementata.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.EnumSpans%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetBufferMappingModes%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.ReleaseMarkerData%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CanReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CopyLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.EnumLayerMarkers%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetBaseBuffer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLengthOfLine%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineCount%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.LockBufferEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.MapLocalSpansToTextOriginatingLayer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReleaseMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLinesEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.UnlockBufferEx%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView.GetSelectedAtom%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetSelectionDataObject%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RestrictViewRange%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateViewFrameCaption%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.InvokeInsertionUI%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetHoverWaitTimer%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetViewClassID%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.AfterCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.BeforeCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetContextLocation%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetServiceProvider%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.ReplaceSubjectTextSpan%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateSmartTagWindow%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost.SetSubjectFromPrimaryBuffer%2A> viene implementata negli adapter ma ignorato dall'interfaccia utente della struttura.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx.GetBannerAttr%2A> viene implementata negli adapter ma ignorato dall'interfaccia utente della struttura.|