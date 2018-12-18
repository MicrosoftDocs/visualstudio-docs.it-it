---
title: Pattern di controllo comuni per Visual Studio | Documenti Microsoft
ms.custom: 
ms.date: 04/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ded7ed6dd843a7879100704276766bfcb528b6f7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="common-control-patterns-for-visual-studio"></a>Pattern di controllo comuni per Visual Studio
##  <a name="BKMK_CommonControls"></a>Controlli comuni  
  
### <a name="overview"></a>Panoramica  
Controlli comuni di costituiscono la maggior parte dell'interfaccia utente in Visual Studio. Controlli più comuni utilizzati nell'interfaccia di Visual Studio devono seguire il [linee guida di Windows Desktop interazione](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx). In questo argomento è specifico di Visual Studio e vengono illustrati i dettagli che aumentano le linee guida di Windows o situazioni particolari.  
  
#### <a name="common-controls-in-this-topic"></a>Controlli comuni in questo argomento  
  
-   [Barre di scorrimento](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)  
  
-   [Campi di input](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)  
  
-   [Elenchi a discesa e caselle combinate](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)  
  
-   [Caselle di controllo](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)  
  
-   [Pulsanti di opzione](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)  
  
-   [Frame di gruppo](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)  
  
-   [Controlli testo](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)  
  
-   [I pulsanti e collegamenti ipertestuali](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)  
  
-   [Visualizzazioni struttura ad albero](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)  
  
#### <a name="visual-style"></a>Stile di visualizzazione  
La prima cosa prendere in considerazione i controlli di stile è se i controlli verranno utilizzati nell'interfaccia utente con temi. Controlli dell'interfaccia utente standard sono non applicare un tema dell'interfaccia utente e deve seguire [stile Desktop di Windows normale](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742399\(v=vs.85\).aspx), vale a dire che non sono basati su modelli r e verrà visualizzato il relativo aspetto del controllo predefinito.  
  
-   **Finestre di dialogo standard (utilità):** non applicare un tema. Non reimpostare come modelli. Usa impostazioni predefinite di stile di controllo di base.  
  
-   **Strumento di windows, editor di documenti, aree di progettazione e finestre di dialogo con tema:** utilizzare aspetto con tema specializzato mediante il servizio di colore.  
  
###  <a name="BKMK_Scrollbars"></a>Barre di scorrimento  
 Barre di scorrimento devono seguire [barre di scorrimento di modelli di interazione comune per Windows](https://msdn.microsoft.com/en-us/library/windows/desktop/bb787527\(v=vs.85\).aspx) a meno che non si è integrate con le informazioni sul contenuto, come nell'editor di codice.  
  
###  <a name="BKMK_InputFields"></a>Campi di input  
 Per la modalità di interazione tipica, seguire la [linee guida di Windows Desktop per le caselle di testo](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742442\(v=vs.85\).aspx).  
  
#### <a name="visual-style"></a>Stile di visualizzazione  
  
-   Campi di input non devono essere applicato uno stile nelle finestre di dialogo utilità. Utilizzare lo stile di base intrinseco al controllo.  
  
-   Esclusivamente ai campi di input con temi in finestre di dialogo temi e le finestre degli strumenti.  
  
#### <a name="specialized-interactions"></a>Interazioni specializzate  
  
-   Campi di sola lettura avrà uno sfondo grigio (disattivato) ma di primo piano predefinito (attivo).  
  
-   Necessario campi devono avere  **\<necessari >** come filigrane al loro interno. Non è necessario modificare il colore di sfondo in rare situazioni, ad eccezione.  
  
-   Convalida di errori: vedere [notifiche e l'avanzamento di Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)  
  
-   Campi di input devono essere dimensionati per adattarle al contenuto, non si adattino alla larghezza della finestra in cui vengono visualizzati né arbitrariamente corrisponde alla lunghezza dei campi lunghi, ad esempio un percorso. Lunghezza potrebbe essere un'indicazione all'utente di limitazioni per il numero di caratteri consentito nel campo.  
  
     ![Lunghezza del campo di input non corretto: è improbabile che il nome sarà questo tempo. ] (../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707 01_IncorrectInputFieldControl")<br />Lunghezza del campo di input non corretto: è improbabile che il nome sarà questo tempo.
  
     ![Correggere la lunghezza del campo di input: il campo di input è una larghezza ragionevole per il contenuto previsto. ] (../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707 02_CorrectInputFieldControl")<br />Correggere la lunghezza del campo di input: il campo di input è una larghezza ragionevole per il contenuto previsto.
  
###  <a name="BKMK_ComboBoxesAndDropDowns"></a>Elenchi a discesa e caselle combinate  
Per la modalità di interazione tipica, seguire la [linee guida di Windows Desktop per elenchi a discesa e caselle combinate](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742404\(v=vs.85\).aspx).  
  
#### <a name="visual-style"></a>Stile di visualizzazione  
  
-   Nelle finestre di dialogo utilità, non reimpostare come modelli del controllo. Utilizzare lo stile di base intrinseco al controllo.  
  
-   Nell'interfaccia utente con temi, gli elenchi a discesa e caselle combinate seguire i temi standard per i controlli.  
  
#### <a name="layout"></a>Layout  
Elenchi a discesa e caselle combinate di ridimensionamento per adattare il contenuto, non si adattino alla larghezza della finestra in cui vengono visualizzati né arbitrariamente corrisponde alla lunghezza dei campi lunghi, ad esempio un percorso.  
  
![Non è corretto: la larghezza dell'elenco a discesa è troppo lunga per il contenuto che verrà visualizzato. ] (../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707 03_IncorrectDropDownLayout")<br />Non è corretto: la larghezza dell'elenco a discesa è troppo lunga per il contenuto che verrà visualizzato.
  
![Corretti: elenco a discesa viene ridimensionato per tener conto della crescita traduzione, ma non eccessivamente lunghe. ] (../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707 04_CorrectDropDownLayout")<br />Corretti: elenco a discesa viene ridimensionato per tener conto della crescita traduzione, ma non eccessivamente lunghe. 
  
###  <a name="BKMK_CheckBoxes"></a>Caselle di controllo  
Per la modalità di interazione tipica, seguire la [linee guida di Windows Desktop per le caselle di controllo](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742401\(v=vs.85\).aspx).  
  
#### <a name="visual-style"></a>Stile di visualizzazione  
  
-   Nelle finestre di dialogo utilità, non reimpostare come modelli del controllo. Utilizzare lo stile di base intrinseco al controllo.  
  
-   Caselle di controllo dell'interfaccia utente con temi, seguire i temi standard per i controlli.  
  
#### <a name="specialized-interactions"></a>Interazioni specializzate  
  
-   L'interazione con una casella di controllo non deve mai pop una finestra di dialogo o passare a un'altra area.  
  
-   Allinea le caselle di controllo con la linea di base della prima riga di testo.  
  
     ![Non è corretto: la casella di controllo viene centrata sul testo. ] (../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707 05_IncorrectCheckBoxAlign")<br />Non è corretto: la casella di controllo viene centrata sul testo.
  
     ![Corretto: la casella di controllo è allineata con la prima riga del testo. ] (../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707 06_CorrectCheckBoxAlign")<br />Corretto: la casella di controllo è allineata con la prima riga del testo.
  
###  <a name="BKMK_RadioButtons"></a>Pulsanti di opzione  
Per la modalità di interazione tipica, seguire la [linee guida di Windows Desktop per pulsanti di opzione](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742436\(v=vs.85\).aspx).  
  
#### <a name="visual-style"></a>Stile di visualizzazione  
Nelle finestre di dialogo utilità, eseguire non pulsanti di opzione di stile. Utilizzare lo stile di base intrinseco al controllo.  
  
#### <a name="specialized-interactions"></a>Interazioni specializzate  
Non è necessario utilizzare una cornice di gruppo per racchiudere le opzioni a scelta, a meno che non è necessario mantenere distinzione di gruppo in un layout di una stretta.  
  
###  <a name="BKMK_GroupFrames"></a>Frame di gruppo  
Per la modalità di interazione tipica, seguire la [linee guida di Windows Desktop per frame gruppo](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742405\(v=vs.85\).aspx).  
  
#### <a name="visual-style"></a>Stile di visualizzazione  
Nelle finestre di dialogo utilità, non applicare uno stile frame di gruppo. Utilizzare lo stile di base intrinseco al controllo.  
  
#### <a name="layout"></a>Layout  
  
-   Non è necessario utilizzare una cornice di gruppo per racchiudere le opzioni a scelta, a meno che non è necessario mantenere distinzione di gruppo in un layout di una stretta.  
  
-   Non utilizzare mai una cornice di gruppo per un singolo controllo.  
  
-   Talvolta è accettabile usare una regola orizzontale anziché un contenitore di frame di gruppo.  
  
##  <a name="BKMK_TextControls"></a>Controlli di testo

### <a name="static-text-fields"></a>Campi di testo statico

Un campo di testo statico fornisce informazioni di sola lettura e non può essere selezionato dall'utente. Evitare di utilizzarla per qualsiasi testo che l'utente potrebbe scegliere di copiare negli Appunti. Testo statico di sola lettura possa tuttavia modificare in modo da riflettere una modifica nello stato. Nell'esempio seguente, il testo statico nome Output con le modifiche del gruppo di informazioni in modo da riflettere le modifiche apportate alla casella di testo radice Namespace sopra di esso.

Esistono due modi per visualizzare le informazioni di testo statico.

Può essere testo statico in un proprio in una finestra di dialogo senza alcun contenuto quando non si verifichino conflitti di raggruppamento. Decidere se le righe aggiuntive di una casella siano effettivamente necessarie. Un esempio è la visualizzazione di un percorso di directory in una sezione creata da una linea di gruppo, come illustrato di seguito:  

![Le informazioni di testo statico in controlli testo](../../extensibility/ux-guidelines/media/DisplayingStaticText.png "DisplayingStaticText.png")<br />Informazioni di testo statico in controlli di testo

In una finestra di dialogo in cui esistono altre aree raggruppati e indipendenza delle informazioni consente di migliorare la leggibilità, e quando una sezione può essere nascosta o visualizzata (come nel **finestra proprietà** riquadro Descrizione) o si desidera essere coerente con l'interfaccia utente simile, Inserire il testo statico in una casella. Questa casella di gruppo deve essere una singola regola e colorati con il `ButtonShadow`:

![Testo statico nella finestra proprietà](../../extensibility/ux-guidelines/media/PropertiesWindow.png "PropertiesWindow.png")<br />Testo statico nella finestra proprietà

### <a name="read-only-text-box"></a>Casella di testo di sola lettura

Ciò consente all'utente di selezionare il testo all'interno del campo, ma non modificarlo. Queste caselle di testo vengono delimitate dal consueto Scalpello 3D con un `ButtonShadow` riempimento.

Una casella di testo può diventare attiva (modificabile) quando un utente modifica un controllo associato, ad esempio il controllo o se si deseleziona una casella di controllo o la selezione o deselezione di un pulsante di opzione. Ad esempio, nel **strumenti &gt; opzioni** pagina riportato di seguito, il **Home Page** casella di testo diventa attiva quando il **Usa predefinito** casella di controllo è deselezionata.

![Casella di testo di sola lettura, che mostra gli stati attivi e inattivi](../../extensibility/ux-guidelines/media/ReadOnlyTextBox.png "ReadOnlyTextBox.png")<br />Casella di testo di sola lettura, che mostra inattivo allo stato attivo

### <a name="using-text-in-dialogs"></a>Utilizzo di testo in finestre di dialogo

Linee guida fondamentali per il testo nelle finestre di dialogo:

-   Le etichette per le caselle di testo, caselle di riepilogo e frame nelle finestre di dialogo unthemed iniziano con un verbo, attiva l'iniziale maiuscola solo la prima parola e terminano con un virgola.

    > Seguono i controlli di testo nelle finestre di dialogo con tema [linee guida sull'esperienza utente desktop Windows](https://msdn.microsoft.com/library/windows/desktop/dn742479.aspx) e non accettano punteggiatura finale, ad eccezione dei punti interrogativi i collegamenti della Guida.

-   Le etichette per le caselle di controllo e pulsanti di opzione iniziano con un verbo HTTP, l'iniziale maiuscola solo la parola prima e non contenere punteggiatura finale.

-   Le etichette per i pulsanti, menu, le voci di menu e le schede hanno maiuscole iniziali su ogni parola (maiuscole).

-   Terminologia di etichetta deve essere coerente con le etichette simili nelle altre finestre di dialogo.

-   Se possibile, avere un writer/editor di scrivere o approvare il testo prima dell'aggiunta allo sviluppatore per l'implementazione.

-   Tutti i controlli devono avere etichette tranne in casi speciali in cui la tabulazione è sufficiente.
Utilizzare il testo di supporto quando appropriato.

### <a name="helper-text"></a>Testo di supporto

Incluse nelle finestre di dialogo per consentire all'utente di comprendere scopo della finestra di dialogo o per indicare l'azione da eseguire. Testo di supporto deve essere utilizzato solo quando necessario per evitare ingombrare finestre di dialogo semplice. Due varianti di testo di supporto sono finestra di dialogo e il limite.

Seguire i percorsi comuni per il testo di supporto e selettivo per una presentazione introduttiva nuove aree. Scenari comuni per il testo di supporto sono:

-   Testo di supporto nelle finestre di dialogo, per assegnare la direzione aggiuntiva su come interagire con una finestra di dialogo complesso.

-   Testo della filigrana in vuoto finestre degli strumenti o finestre di dialogo, per non spiegare il motivo di alcun contenuto visibile.

-   Il riquadro Descrizione, come in fondo il **finestra proprietà**.

-   Filigrana testo in un editor vuoto, per illustrare l'azione che l'utente deve intraprendere per iniziare.
  
### <a name="dialog-helper-text"></a>Testo di supporto della finestra di dialogo

Una finestra di progettazione di esperienza utente può determinare quando il testo di supporto appropriato. La finestra di progettazione è possibile definire in cui è presente testo di supporto e il relativo contenuto generale. Documentazione per gli utenti possa scrittura e modifica il testo effettivo.

### <a name="watermarks"></a>Filigrane

Le finestre di dialogo trarre vantaggio da linee guida filigrana leggermente diversa. Poiché una finestra di dialogo può apparire occupato con molti elementi dell'interfaccia utente (etichette, testo di suggerimento, pulsanti e altri controlli contenitore con il testo), in particolare quando quelli visualizzati in nero, filigrane evidenti in grigio scuro (VSColor: `ButtonShadow`). Viene visualizzato in genere una filigrana all'interno di un controllo casella di riepilogo con uno sfondo bianco (VSColor: `Window`).

-   Il testo viene visualizzato in grigio scuro (VSColor: `ButtonShadow`). Tuttavia, se viene visualizzata la filigrana in un grigio medio o in altri colori (VSColor: `ButtonFace`) in background ed è presente riguardano sulla leggibilità, passare con testo nero (VSColor: `WindowText`).

-   Le filigrane possono essere centrate o allineamento a sinistra. Applicare le regole di progettazione standard nel prendere decisioni di allineamento. Impossibile selezionare la filigrana sullo sfondo.

![Esempio di testo filigrana](../../extensibility/ux-guidelines/media/WatermarkTextExample.gif)<br />Esempio di testo filigrana

### <a name="context-specific-dynamic-text"></a>Testo (dinamico) specifici del contesto

Testo dinamico può essere utilizzato in due modi in una finestra di dialogo o dell'interfaccia utente non modale: come un'etichetta dinamica o contenuto dinamico.

-   Etichetta dinamica: un utilizzo comune di testo dinamico consiste nei pannelli descrittivi che offrono ulteriori informazioni per l'elemento selezionato, ad esempio in una finestra di dialogo che contiene un elenco di elementi e proprietà per gli elementi visualizzati in una griglia a destra. L'etichetta per la griglia delle proprietà può essere dinamica in modo che quando viene selezionato un elemento a sinistra, nella griglia a destra vengono visualizzate informazioni per l'elemento specifico.

-   Testo dinamico: può essere molto utile nei casi in cui è necessario visualizzare informazioni specifiche e non le informazioni in questo modo, ma è necessario fare attenzione a non abusare.

Se si desidera che gli utenti hanno la possibilità di copiare le informazioni, deve essere testo dinamico in un campo di testo di sola lettura.
  
##  <a name="BKMK_ButtonsAndHyperlinks"></a>I pulsanti e collegamenti ipertestuali  
  
### <a name="overview"></a>Panoramica  
I controlli di pulsanti e collegamento (collegamenti ipertestuali) devono seguire [linee guida di Windows Desktop di base sui collegamenti ipertestuali](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742406\(v=vs.85\).aspx) per l'utilizzo, testo, dimensioni e la spaziatura.  
  
### <a name="choosing-between-buttons-and-links"></a>Scelta tra i pulsanti e collegamenti  
In genere, i pulsanti sono stati utilizzati per le azioni e i collegamenti ipertestuali sono stati riservati per la navigazione. Pulsanti possono essere utilizzati in tutti i casi, ma il ruolo dei collegamenti è stata espansa in Visual Studio in modo che i pulsanti e i collegamenti sono più intercambiabili in alcune condizioni.  
  
Quando utilizzare i pulsanti di comando:  
  
-   Comandi principali  
  
-   Visualizzazione di windows utilizzato per raccogliere l'input o la scelta delle opzioni, anche se sono comandi secondari  
  
-   Azioni distruttive o irreversibili  
  
-   Pulsanti di impegno all'interno di procedure guidate e dei flussi di pagina  
  
Evitare di pulsanti di comando nelle finestre degli strumenti, o se è necessario più di due parole per l'etichetta. Collegamenti possono avere più etichette.  
  
 Quando usare i collegamenti:  
  
-   Spostamento di un'altra finestra, documento o pagina web  
  
-   Situazioni che richiedono un'etichetta più breve frase per descrivere lo scopo dell'azione  
  
-   Una stretta spazi in un pulsante sarebbe sovraccarico l'interfaccia utente, purché l'azione non distruttiva o irreversibili  
  
-   Ridimensionando comandi secondari nelle situazioni in cui sono presenti molti comandi  
  
#### <a name="examples"></a>Esempi  
![Comando collegamenti usati nella barra informazioni seguendo un messaggio di stato](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703 01_CommandLinkInfobar")<br />Comandi collegamenti usati nella barra informazioni seguendo un messaggio di stato
  
![Collegamenti usati nel popup CodeLens](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703 02_LinksInCodeLens")<br />Collegamenti usati nel popup CodeLens
  
![Collegamenti usati per i comandi secondari in cui è opportuno considerare una quantità eccessiva attenzione pulsanti](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703 03_LinksAsSecondaryCommands")<br />Collegamenti usati per i comandi secondari in cui è opportuno considerare una quantità eccessiva attenzione pulsanti
  
### <a name="common-buttons"></a>Pulsanti comuni  
  
#### <a name="text"></a>Testo  
Seguire le istruzioni di scrittura in [dell'interfaccia utente testo e la terminologia](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).  
  
#### <a name="visual-style"></a>Stile di visualizzazione  
  
##### <a name="standard-unthemed"></a>Standard (unthemed)  
La maggior parte dei pulsanti in Visual Studio verranno visualizzato nelle finestre di dialogo utilità e non devono essere applicato uno stile. Riflettono l'aspetto dei pulsanti standard dettato dal sistema operativo.  
  
##### <a name="themed"></a>Applicare un tema  
In alcuni casi, i pulsanti possono essere utilizzati all'interno dell'interfaccia con stile e questi pulsanti devono essere applicato uno stile in modo appropriato. Vedere [finestre di dialogo](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) per informazioni sui controlli con temi.  
  
### <a name="special-buttons"></a>Pulsanti speciali  
  
#### <a name="browse-buttons"></a>Sfoglia pulsanti  
**[Sfoglia...]**  vengono utilizzati i pulsanti in griglie, finestre di dialogo e le finestre degli strumenti e altri elementi dell'interfaccia utente non modale. Verranno inoltre visualizzati un controllo di selezione che assiste l'utente durante la compilazione di un valore in un controllo. Esistono due varianti di questo pulsante, lunga e breve.  
  
![Il pulsante [Sfoglia...] lungo](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703 04_BrowseLong")<br />Il pulsante [Sfoglia...] lungo
  
![Pulsante breve soli puntini di sospensione […]](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703 05_BrowseShort")<br />Pulsante breve soli puntini di sospensione […]
  
Quando utilizzare il pulsante puntini di sospensione sola breve:  
  
-   Se è più lungo **[Sfoglia...]**  pulsante in una finestra di dialogo, ad esempio se consentano di diversi campi per l'esplorazione. Utilizzare breve **[…]**  per ognuno evitare la confusione chiavi di accesso create da questa situazione (**& Sfoglia** e **B & digita** nella stessa finestra di dialogo).  
  
-   In una finestra di dialogo ridotto o non è ragionevole per inserire il pulsante lungo.  
  
-   Se il pulsante verrà visualizzato in un controllo griglia.  
  
Linee guida per il pulsante:  
  
-   Non usare una chiave di accesso. Per accedervi mediante la tastiera, l'utente deve scheda dal controllo adiacente. Verificare che l'ordine di tabulazione è tale che qualsiasi pulsante si immediatamente dopo il campo che riempirà. Non utilizzare mai un carattere di sottolineatura seguito dal primo periodo.  
  
-   Impostare Microsoft Active Accessibility (MSAA) **nome** proprietà **Sfoglia...**  (inclusi i puntini di sospensione) in modo che schermata verrà letto, come "Sfoglia" e non "punto-punto-punto" o "periodo periodo periodo." Per controlli gestiti, ciò significa impostazione di **AccessibleName** proprietà.  
  
-   Non utilizzare mai i puntini di sospensione **[…]**  pulsante per un valore diverso da un'azione di esplorazione. Ad esempio, se è necessario un **[novità]**  pulsante ma non dispone di spazio sufficiente per il testo, quindi la finestra di dialogo debba essere riprogettata.  
  
##### <a name="sizing-and-spacing"></a>Ridimensionamento e la spaziatura  
![Pulsanti [Sfoglia...] di ridimensionamento: versione standard è 75 x 23 pixel, la versione breve è 26 x 23 pixel](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703 06_BrowseSizing")<br />Ridimensionamento dei pulsanti [Sfoglia...]
  
![Pulsanti [Sfoglia...] spaziatura: spaziatura tra i pixel di 7 pulsante Sfoglia standard e di controllo correlato, la spaziatura tra controllo correlato e breve Sfoglia pulsante 5 pixel](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703 07_BrowseSpacing")<br />Spaziatura dei pulsanti [Sfoglia...]
  
#### <a name="graphical-buttons"></a>Pulsanti grafici  
Alcuni pulsanti devono sempre utilizzare un'immagine grafica e testo per risparmiare spazio ed evitare problemi di localizzazione non includere mai. Questi vengono spesso utilizzati in altri elenchi ordinabile e le selezioni di campo.  
  
> **Nota:** gli utenti debbano premere tab per questi pulsanti (non sono presenti chiavi di accesso), inserire in un ordine appropriato. Mappa il `name` proprietà del pulsante per l'azione che richiede in modo che gli screen reader interpretare correttamente l'azione del pulsante.  
  
| Funzione | Button |  
| --- | --- |  
| Aggiunta | ![Grafica pulsante "Aggiungi"](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703 08_ButtonAdd") |
| Rimuovi | ![Pulsante grafico "Rimuovi"](../../extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703 09_ButtonRemove") |
| Aggiungi tutti | ![Pulsante grafico "Aggiungi tutto"](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703 10_ButtonAddAll") |
| Rimozione di tutti i | ![Pulsante grafico "Rimuovi tutto"](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703 11_ButtonRemoveAll") |
| Sposta su | ![Pulsante grafico "Sposta su"](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703 12_ButtonMoveUp") |
| Sposta giù | ![Pulsante grafico "Sposta giù"](../../extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703 13_ButtonMoveDown") |
| Eliminare | ![Pulsante grafico "Elimina"](../../extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703 14_ButtonDelete") |
  
##### <a name="sizing-and-spacing"></a>Ridimensionamento e la spaziatura  
Definizione delle dimensioni per i pulsanti con interfaccia grafico sono la stessa di una versione ridotta del **[Sfoglia...]**  pulsante (26 x 23 pixel):  
  
![Aspetto di un'immagine grafica sul pulsante con e senza colore trasparente visualizzato](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703 15_GraphicalButtonSpacing")<br />Aspetto di un'immagine grafica sul pulsante con e senza colore trasparente visualizzato
  
### <a name="hyperlinks"></a>Collegamenti ipertestuali  
I collegamenti ipertestuali sono particolarmente adatti per azioni basate su navigazione, ad esempio l'apertura di un argomento della Guida, finestra di dialogo modale o configurazione guidata. Se un collegamento ipertestuale viene utilizzato per un comando, viene sempre visualizzato una modifica visibile e significativa per l'interfaccia utente. In generale, le azioni che eseguono il commit a un'azione (ad esempio, salvare, annullamento ed eliminare) meglio vengono comunicate tramite un pulsante.  
  
#### <a name="writing-style"></a>Stile di scrittura  
Seguire il [materiale sussidiario per il Desktop di Windows per il testo dell'interfaccia utente](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx). Non utilizzare "Ulteriori informazioni," "Indicare me ulteriori informazioni su" o "Get help con questo" enunciazione. Al contrario, una frase di testo di collegamento della Guida in termini di domande primario per il contenuto della Guida. Ad esempio, "**come aggiungere un server in Esplora Server?**"  
  
#### <a name="visual-style"></a>Stile di visualizzazione  
  
-   Utilizzano sempre i collegamenti ipertestuali [il servizio VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService). Se un collegamento ipertestuale non viene applicato lo stile corretto, lampeggia rosso quando è attivo o Mostra un colore diverso dopo viene visitato.  
  
-   Non includere sottolineatura il controllo posizionato stato, a meno che il collegamento è un frammento di frase all'interno di una frase completa, ad esempio una filigrana.  
  
-   Sottolineature dovrebbero risultare al passaggio del mouse. I commenti e suggerimenti per l'utente che il collegamento è attivo viene invece una modifica del colore leggero e il cursore di collegamento appropriato.  
  
##  <a name="BKMK_TreeViews"></a>Visualizzazioni struttura ad albero  
  
Visualizzazioni dell'albero forniscono un modo per organizzare complessi elencati in gruppi padre-figlio. Un utente è possibile espandere o comprimere i gruppi padre per mostrare o nascondere gli elementi figlio sottostante. È possibile selezionare ogni elemento all'interno di una visualizzazione albero per fornire un'ulteriore azione.  
  
###  <a name="BKMK_TreeViewVisualStyle"></a>Stili di visualizzazione albero  
  
#### <a name="expanders"></a>Espansori  
Controlli visualizzazione albero devono essere conforme alla progettazione expander utilizzata da Windows e Visual Studio. Ogni nodo Usa un controllo expander per mostrare o nascondere elementi sottostanti. Utilizzo di un controllo expander fornisce coerenza per gli utenti che possono verificarsi visualizzazioni albero diverso all'interno di Windows e Visual Studio.  
  
![Corretto: stile corretto del nodo della visualizzazione albero con un controllo expander](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705 1_TreeViewCorrect")<br />Corretto: stile corretto del nodo della visualizzazione albero con un controllo expander
  
![Non corretta: stile non corretto del nodo della visualizzazione albero](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705 2_TreeViewIncorrect1")<br />Non corretta: lo stile non corretto visualizzazione della struttura ad albero
  
#### <a name="selection"></a>Selection  
Quando si seleziona un nodo all'interno della visualizzazione struttura ad albero, è necessario espandere l'evidenziazione per l'intera larghezza del controllo di visualizzazione albero. Questo consente agli utenti di identificare chiaramente quale elemento selezionato. Selezione colori devono riflettere il tema corrente di Visual Studio.  
  
![Corretti: evidenziazione del nodo selezionato è adatta l'intera larghezza del controllo di visualizzazione albero. ] (../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705 1_TreeViewCorrect")<br />Corretti: evidenziazione del nodo selezionato è adatta l'intera larghezza del controllo di visualizzazione albero.
  
![Non corretta: evidenziazione del nodo selezionato non si adatta l'intera larghezza del controllo di visualizzazione albero. ] (../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705 3_TreeViewIncorrect2")<br />Non corretta: evidenziazione del nodo selezionato non si adatta l'intera larghezza del controllo di visualizzazione albero.
  
#### <a name="icons"></a>Icone  
Icone devono essere utilizzate in controlli visualizzazione albero solo se è aiutare a identificare visivamente le differenze tra gli elementi. In generale, le icone devono essere utilizzate solo negli elenchi eterogenei in cui le icone forniscono informazioni per distinguere i tipi di elementi. In un elenco omogeneo usando icone possono spesso essere considerata come rumore e deve essere evitato. In questo caso l'icona del gruppo (padre) può fornire il tipo di elementi in esso contenuti. L'eccezione a questa regola può essere se l'icona è dinamica e viene utilizzata per indicare lo stato.  
  
#### <a name="scroll-bars"></a>Barre di scorrimento  
Barre di scorrimento devono sempre essere nascosto se il contenuto si adatta all'interno del controllo di visualizzazione albero. È accettabile per le barre di scorrimento per essere nascosta o semi-trasparente in una finestra scorrevole e vengono visualizzati quando la finestra contenente la visualizzazione albero ha lo stato attivo o al momento del passaggio del mouse della struttura ad albero visualizzare anch'esso.  
  
![Entrambe le barre di scorrimento orizzontale e verticale vengono visualizzate perché il contenuto è stato superato i limiti del controllo di visualizzazione albero. ] (../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705 4_Scrollbars")<br />Entrambe le barre di scorrimento orizzontale e verticale vengono visualizzate perché il contenuto è stato superato i limiti del controllo di visualizzazione albero.
  
###  <a name="BKMK_TreeViewInteractions"></a>Interazioni di visualizzazione albero  
  
#### <a name="context-menus"></a>Menu di scelta rapida  
Un nodo della visualizzazione struttura ad albero può evidenziare le opzioni di sottomenu in un menu di scelta rapida. In genere, ciò si verifica quando un utente dispone di un elemento di pulsante destro del mouse o premuto il tasto Menu su una tastiera di Windows con l'elemento selezionato. È importante che il nodo lo stato attivo e che sia selezionato. Ciò consente all'utente di identificare quale elemento a cui appartiene il sottomenu.  
  
![L'elemento che ha generato il contesto menu riceve lo stato attivo per notificare all'utente quale elemento è stato selezionato. ] (../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705 5_ContextMenu")<br />L'elemento che ha generato il contesto menu riceve lo stato attivo per notificare all'utente quale elemento è stato selezionato.
  
#### <a name="keyboard"></a>Tastiera  
Visualizzazione albero dovrebbe offrire la possibilità di selezionare gli elementi e di espansione/compressione di nodi utilizzando la tastiera. In questo modo si garantisce che navigazione soddisfi i requisiti di accessibilità.  
  
##### <a name="tree-view-control"></a>Controllo di visualizzazione albero  
Albero (controlli) Visual Studio devono seguire la navigazione da tastiera comuni:  
  
-   **Freccia:** selezionare gli elementi con lo spostamento della struttura ad albero  
  
-   **Freccia in giù:** selezionare gli elementi con lo spostamento verso il basso la struttura ad albero  
  
-   **Freccia destra:** espandere un nodo dell'albero  
  
-   **Freccia sinistra:** comprimere un nodo dell'albero  
  
-   **Immettere una chiave:** avviare, caricare, eseguire l'elemento selezionato  
  
##### <a name="trid-tree-view-and-grid-view"></a>Albero (visualizzazione struttura ad albero e griglia)  
Un controllo albero è un controllo complesso che contiene una visualizzazione albero in una griglia. Espansione e compressione di esplorare l'albero deve rispettare gli stessi comandi di tasti come una visualizzazione albero, con le seguenti aggiunte:  
  
-   **Freccia destra:** espandere un nodo. Dopo aver espanso il nodo, deve continuare a esplorare alla colonna più vicino a destra. Navigazione deve essere interrotta alla fine della riga.  
  
-   **Scheda:** consente di passare alla cella più vicino a destra.  Alla fine della riga, navigazione continua alla riga successiva.  
  
-   **Maiusc + Tab:** consente di passare alla cella più vicino a sinistra.  All'inizio della riga, navigazione continua alla cella a destra nella riga precedente.  
  
![Un controllo albero in Visual Studio](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705 6_Trid")<br />Un controllo albero in Visual Studio