---
title: Debug di HTML e CSS nelle App UWP | Documenti Microsoft
ms.custom: ''
ms.date: 07/17/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- VS.WebClient.DomExplorer
dev_langs:
- JavaScript
helpviewer_keywords:
- debugging, CSS
- debugging, HTML
- debugging, JavaScript [UWP apps]
- DOM Explorer [UWP apps]
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: b5673a2ab191f71b9aec14f08c5adfc65883ff24
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="debug-html-and-css-in-uwp-apps-in-visual-studio"></a>Debug di HTML e CSS nelle App UWP in Visual Studio
  
 Per le app JavaScript, Visual Studio offre un'esperienza di debug completa che include funzionalità note agli sviluppatori di Visual Studio e Internet Explorer. Queste funzionalità sono supportate per App UWP e App create con Visual Studio Tools per Apache Cordova.  
  
 Usando il modello di debug interattivo fornito dagli strumenti di ispezione DOM, è possibile visualizzare e modificare il codice HTML e CSS sottoposto a rendering. È possibile eseguire tutte queste operazioni senza arrestare e riavviare il debugger.
  
 Per informazioni su altre funzionalità, ad esempio utilizzando la finestra JavaScript Console e l'impostazione di punti di interruzione, di debug JavaScript, vedere [Guida introduttiva: eseguire il Debug di JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md) e [Debug delle App in Visual Studio](../debugger/debug-store-apps-in-visual-studio.md).  
  
##  <a name="InspectingDOM"></a> Controllo del DOM attivo  
 DOM Explorer presenta una visualizzazione della pagina sottoposta a rendering. È possibile usarlo per modificare i valori e vedere immediatamente i risultati. In questo modo è possibile testare le modifiche senza arrestare e riavviare il debugger. Il codice sorgente nel progetto non viene modificato quando si interagisce con la pagina usando questo metodo. Pertanto è possibile apportare le modifiche al codice sorgente quando si trovano le correzioni del codice desiderate.  
  
> [!TIP]
>  Per evitare di arrestare e riavviare il debugger quando si apportano modifiche al codice sorgente, è possibile aggiornare l'app usando il pulsante **Aggiorna applicazione Windows** sulla barra degli strumenti di debug (o premendo F4). Per altre informazioni, vedere [aggiornare un'applicazione (JavaScript)](../debugger/refresh-an-app-javascript.md).  
  
 È possibile usare DOM Explorer per:  
  
-   Passare al sottoalbero di elementi DOM e controllare il codice HTML, CSS e JavaScript sottoposto a rendering.  
  
-   Modificare dinamicamente gli attributi e gli stili CSS per gli elementi sottoposti a rendering e visualizzare immediatamente i risultati.  
  
-   Controllare l'applicazione degli stili CSS agli elementi della pagina e tenere traccia delle regole applicate.  
  
 Quando si esegue il debug delle app, è spesso necessario selezionare elementi in DOM Explorer. Quando si seleziona un elemento, i valori visualizzati nelle schede a destra di DOM Explorer vengono aggiornati automaticamente per riflettere l'elemento selezionato in DOM Explorer. Si tratta delle schede **Stili**, **Calcolata**e **Layout**. App UWP supportano anche il **eventi** e **modifiche** schede. Per altre informazioni sulla selezione di elementi, vedere [Selecting elements](#SelectingElements).  
  
> [!TIP]
>  Se la finestra DOM Explorer è chiusa, scegliere **Debug**>**Finestre** > **DOM Explorer** per riaprirla. La finestra viene visualizzata solo durante una sessione di debug di script.  
  
 Nella routine seguente viene illustrato il processo di debug interattivo di un'app usando DOM Explorer. Verrà creata un'app che usa un controllo `FlipView` , quindi verrà eseguito il debug. L'app contiene diversi errori.  
  
> [!WARNING]
>  L'app di esempio seguente è un'app UWP. Le stesse funzionalità sono supportate per Cordova, ma l'app sarebbe differente.  
  
#### <a name="to-debug-by-inspecting-the-live-dom"></a>Per eseguire il debug controllando il DOM attivo  
  
1.  Creare una nuova soluzione in Visual Studio scegliendo **File** > **Nuovo progetto**.  
  
2.  Scegliere **JavaScript** > **universali di Windows**, quindi scegliere **WinJS App**.  
  
3.  Digitare un nome per il progetto, ad esempio `FlipViewApp`e scegliere **OK** per creare l'app.  
  
4.  Nell'elemento BODY di index.html, aggiungere questo codice:  
  
    ```html  
    <div id="flipTemplate" data-win-control="WinJS.Binding.Template"  
             style="display:none">  
        <div class="fixedItem" >  
            <img src="#" data-win-bind="src: flipImg" />  
        </div>  
    </div>  
    <div id="fView" style="width:100px;height:100px"  
        data-win-control="WinJS.UI.FlipView" data-win-options="{  
        itemDataSource: Data.items.dataSource, itemTemplate: flipTemplate }">  
    </div>  
    ```  
  
5.  Aprire default.css e aggiungere il codice CSS seguente:  
  
    ```css  
    #fView {  
        background-color:#0094ff;  
        height: 100%;  
        width: 100%;  
        margin: 25%;  
    }  
    ```  
  
6.  Sostituire il codice nel file default.js con questo codice:  
  
    ```javascript  
    (function () {  
        "use strict";  
  
        var app = WinJS.Application;  
        var activation = Windows.ApplicationModel.Activation;  
  
        var myData = [];  
        for (var x = 0; x < 4; x++) {  
            myData[x] = { flipImg: "/images/logo.png" }  
        };  
  
        var pages = new WinJS.Binding.List(myData, { proxy: true });  
  
        app.onactivated = function (args) {  
            if (args.detail.kind === activation.ActivationKind.launch) {  
                if (args.detail.previousExecutionState !==  
                activation.ApplicationExecutionState.terminated) {  
                    // TODO: . . .  
                } else {  
                    // TODO: . . .  
                }  
                args.setPromise(WinJS.UI.processAll());  
  
                updateImages();  
            }  
        };  
  
        function updateImages() {  
  
            pages.setAt(0, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg" });  
            pages.setAt(1, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-77.jpg" });  
            pages.setAt(2, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-78.jpg" });  
        };  
  
        app.oncheckpoint = function (args) {  
        };  
  
        app.start();  
  
        var publicMembers = {  
            items: pages  
        };  
  
        WinJS.Namespace.define("Data", publicMembers);  
  
    })();  
    ```  
  
     Nella figura seguente mostra cosa accade se Esegui questa app. Tuttavia, per ottenere questo stato dell'app occorre prima risolvere diversi bug.  
  
     ![App FlipView con i risultati previsti](../debugger/media/js_dom_appfixed.png "JS_DOM_AppFixed")  
  
7.  Scegliere **computer locale** dall'elenco a discesa elenco accanto al **Avvia debug** pulsante il **Debug** barra degli strumenti:  
  
     ![Elenco di destinazione di debug selezionare](../debugger/media/js_select_target.png "JS_Select_Target")  
  
8.  Scegliere **Debug** > **Avvia debug**o premere F5 per eseguire l'app in modalità debug.  
  
     L'app viene eseguita, ma vedrai una schermata per lo più vuota perché gli stili presentano alcuni bug. La prima immagine `FlipView` è contenuta in un piccolo quadrato in prossimità del centro dello schermo.  
  
10. Passare a Visual Studio e scegliere la scheda **DOM Explorer** .  
  
    > [!TIP]
    >  È possibile premere ALT+TAB o F12 per passare da Visual Studio all'app in esecuzione.  
  
11. Nella finestra DOM Explorer selezionare l'elemento DIV per la sezione che presenta un ID `"fView"`. Usare i tasti di direzione per visualizzare e selezionare l'elemento DIV corretto. (Il tasto freccia destra consente di visualizzare gli elementi figlio dell'elemento).  
  
     ![DOM Explorer](../debugger/media/js_dom_explorer.png "JS_DOM_Explorer")  
  
    > [!TIP]
    >  È anche possibile selezionare l'elemento DIV nell'angolo inferiore sinistro della finestra della JavaScript Console digitando `select(fView)` nel >> input prompt dei comandi e quindi premere INVIO.  
  
     I valori visualizzati nelle schede sul lato destro della finestra di DOM Explorer vengono aggiornati automaticamente per riflettere l'elemento corrente in DOM Explorer.  
  
12. Scegliere la scheda **Calcolata** a destra.  
  
     Questa scheda mostra il valore calcolato o finale di ogni proprietà dell'elemento DOM selezionato.  
  
13. Aprire la regola CSS relativa all'altezza. Si noti che non esiste un stile inline è impostato su 100px, non è coerente con il valore dell'altezza del 100% impostato per il `#fView` selettore CSS. Il testo barrato per il selettore `#fView` indica che lo stile inline ha la precedenza su questo stile.  
  
     La figura seguente illustra la scheda **Calcolata** .  
  
     ![Scheda calcolato di DOM Explorer](../debugger/media/js_dom_explorer_computed.png "JS_DOM_Explorer_Computed")  
  
14. Nella finestra principale di DOM Explorer fare doppio clic sullo stile inline per l'altezza e la larghezza dell'elemento DIV `fView` . Ora è possibile modificare i valori qui. In questo scenario si vuole rimuoverli completamente.  
  
15. Nella finestra principale, fare doppio clic su `width: 100px;height: 100px;`, premere il **eliminare** chiave e quindi premere **invio**. Dopo aver premuto INVIO, i nuovi valori vengono immediatamente riflessi nell'app, anche se non hai arrestato la sessione di debug.  
  
    > [!IMPORTANT]
    >  Così come è possibile aggiornare gli attributi nella finestra DOM Explorer, è anche possibile aggiornare i valori visualizzati nelle schede **Stili**, **Calcolata**e **Layout** . Per altre informazioni, vedere [gli stili di Debug CSS utilizzando DOM Explorer](../debugger/debug-css-styles-using-dom-explorer.md) e [Debug layout utilizzando DOM Explorer](../debugger/debug-layout-using-dom-explorer.md).  
  
16. Passa all'app selezionandolo oppure usando Alt + Tab.  
  
     Il controllo `FlipView` sembra più grande delle dimensioni dello schermo del simulatore o dell'emulatore Windows Phone. Non si tratta del risultato desiderato. Per controllare, passare di nuovo a Visual Studio.  
  
17. In DOM Explorer selezionare di nuovo la scheda **Calcolata** e aprire la regola dell'altezza. L'elemento fView Mostra ancora un valore pari al 100%, come previsto dal CSS, ma il valore calcolato è uguale all'altezza dello schermo dell'applicazione (ad esempio 800px, 667.67px o un altro valore), ovvero non è auspicabile per questa applicazione. Esaminare i passaggi successivi si rimuove l'altezza e larghezza per il `fView` elemento DIV.  
  
18. Nella scheda **Stili** deselezionare le proprietà height e width per il selettore CSS `#fView` .  
  
     La scheda **Calcolata** mostra ora un'altezza di 400px. Le informazioni indicano che questo valore deriva dal selettore .win-flipview specificato in ui-dark.css, un file di piattaforma CSS.  
  
19. Tornare all'app.  
  
     Le cose sono migliorate. C'è ancora un problema da risolvere. I margini sembrano troppo grandi.  
  
20. Per analizzare il problema, passa a Visual Studio e scegli la **Layout** scheda per esaminare il modello di riquadro dell'elemento.  
  
     Nel **Layout** scheda, verrà visualizzato quanto segue:  
  
    -   255px (Offset) e 255px (margine) o valori simili, a seconda della risoluzione del dispositivo. 
  
     La figura seguente mostra come **Layout** scheda appare se si usa un emulatore con 100px per offset e margine).  
  
     ![Scheda Layout di DOM Explorer](../debugger/media/js_dom_explorer_layout.png "JS_DOM_Explorer_Layout")  
  
     Ciò non sembra corretto. Anche la scheda **Calcolata** mostra gli stessi valori per i margini.  
  
21. Scegliere la scheda **Stili** e trovare il selettore CSS `#fView` . Per la proprietà **margin** il valore è 25%.  
  
22. Selezionare il 25%, impostarlo su 25px e premere Invio.  
  
23. Nella scheda **Stili** scegliere la regola relativa all'altezza per il selettore .win-flipview, modificare 400px in 500px e premere INVIO.  
  
24. Tornare all'app. Ora la posizione degli elementi viene visualizzata correttamente. Per apportare correzioni all'origine e aggiornare l'app senza arrestare e riavviare il debugger, vedere la routine riportata di seguito.  
  
#### <a name="to-refresh-your-app-while-debugging"></a>Per aggiornare l'app durante il debug  
  
1.  Quando l'app è ancora in esecuzione, passare a Visual Studio.  
  
2.  Aprire il file default.html e modificare il codice sorgente cambiando l'altezza e la larghezza dell'elemento DIV `"fView"` in 100%.  
  
3.  Scegliere il pulsante **Aggiorna applicazione Windows** sulla barra degli strumenti Debug oppure premere F4. Il pulsante è simile al seguente: ![pulsante di aggiornamento Windows app](../debugger/media/js_refresh.png "JS_Refresh").  
  
     Le pagine dell'app vengono ricaricate e il simulatore o l'emulatore Windows Phone torna in primo piano.  
  
     Per ulteriori informazioni sulla funzionalità Aggiorna, vedi [aggiornare un'applicazione (JavaScript)](../debugger/refresh-an-app-javascript.md).  
  
##  <a name="SelectingElements"></a> Selecting elements  
 È possibile selezionare gli elementi DOM in tre modi durante il debug di un'app:  
  
-   Facendo clic sugli elementi direttamente nella finestra di DOM Explorer oppure usando i tasti di direzione.  
  
-   Usando il pulsante **Seleziona elemento** (CTRL+B).  
  
-   Usando il pulsante `select` , uno dei [JavaScript Console commands](../debugger/javascript-console-commands.md).  
  
 Quando si usa la finestra DOM Explorer per selezionare elementi e si posiziona il puntatore del mouse su un elemento, l'elemento corrispondente viene evidenziato nell'app in esecuzione. Fare clic sull'elemento in DOM Explorer per selezionarlo oppure usare i tasti freccia per evidenziare e selezionare elementi. La selezione di elementi in DOM Explorer può essere fatta anche tramite il pulsante **Seleziona elemento** . La figura seguente illustra il pulsante **Seleziona elemento** .  
  
 ![Pulsante Seleziona elemento in DOM Explorer](../debugger/media/js_dom_select_element_button.png "JS_DOM_Select_Element_Button")  
  
 Quando si fa clic su **Seleziona elemento** o si preme CTRL+B, la modalità di selezione cambia per consentire di selezionare un elemento in DOM Explorer facendo clic su di esso nell'app in esecuzione. La modalità torna alla modalità di selezione normale dopo un singolo clic. Quando si fa clic su **Seleziona elemento**, l'app passa in primo piano e il cursore cambia per riflettere la nuova modalità di selezione. Quando si fa clic sull'elemento con contorni, DOM Explorer ritorna in primo piano con l'elemento specificato selezionato.  
  
 Prima di scegliere **Seleziona elemento**, è possibile specificare se evidenziare elementi nell'app in esecuzione attivando e disattivando il pulsante **Visualizza pagina Web in evidenza** . La figura seguente mostra questo pulsante. Le evidenziazioni vengono visualizzate per impostazione predefinita.  
  
 ![Visualizzare la pagina web il pulsante delle evidenziazioni](../debugger/media/js_dom_display_highlights_button.png "JS_DOM_Display_Highlights_Button")  
  
 Quando si sceglie di evidenziare elementi, gli elementi su cui si posiziona il puntatore del mouse nel Simulatore vengono evidenziati. I colori per gli elementi evidenziati corrispondono al modello di riquadro visualizzato nella scheda **Layout** di DOM Explorer.  
  
> [!NOTE]
>  L'evidenziazione degli elementi al passaggio del mouse è supportata solo in parte nell'emulatore Windows Phone.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug apps in Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)   
 [Aggiornare un'applicazione (JavaScript)](../debugger/refresh-an-app-javascript.md)   
 [Eseguire il debug di un controllo WebView](../debugger/debug-a-webview-control.md)   
 [Tasti di scelta rapida](../debugger/keyboard-shortcuts-html-and-javascript.md)   
 [Comandi della JavaScript Console](../debugger/javascript-console-commands.md)   
 [Il debug del codice di esempio HTML, CSS e JavaScript](../debugger/debug-html-css-and-javascript-sample-code.md)   
 [Supporto tecnico e accessibilità](http://msdn.microsoft.com/library/tzbxw1af\(VS.120\).aspx)