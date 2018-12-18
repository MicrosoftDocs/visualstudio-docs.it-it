---
title: Layout per Visual Studio | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2e26caa6e47f0f2ee2a20611cf12e166832e007b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="layout-for-visual-studio"></a>Layout per Visual Studio
La maggior parte delle finestre di dialogo di Visual Studio è [layout di finestra di dialogo utilità](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout), che sono il unthemed finestre di dialogo standard di seguire [principi di layout di finestra di dialogo Windows Desktop](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742499\(v=vs.85\).aspx). Mentre Visual Studio viene spostato aggiornare la relativa interfaccia utente, alcune delle finestre di dialogo ruolo più significativo hanno una nuova progettazione che stabilisce le esperienze come definizione di prodotto. Questi [layout di finestra di dialogo con tema](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout) hanno un aspetto con tema.  
  
##  <a name="BKMK_UtilityDialogLayout"></a> Layout di finestra di dialogo utilità  
  
-   Tutti i controlli all'interno di una finestra di dialogo utilità devono iniziare nella parte superiore o sinistra e verso il basso del flusso.  
  
-   Mai center controlli in una finestra di dialogo per riempire una vasta area.  
  
-   Utilizzare il tipo di carattere ambiente per tutto il testo della finestra di dialogo. Quando si scrive una specifica visual, specificare il tipo di carattere ambiente invece di selezionare un particolare tipo di carattere e dimensioni. Vedere [il tipo di carattere ambiente](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).  
  
-   Utilizzare controllo coerenti con spaziatura e la selezione host per supportare l'obiettivo per prodotti di qualità.  
  
-   Le finestre di dialogo può diventare più complesse da un numero maggiore di controlli, un contatto univoca dei controlli o entrambi. Per questi casi complessi, consentire spazio sufficiente tra i raggruppamenti di controllo per consentire all'utente di un flusso logico da analizzare.  
  
### <a name="utility-dialog-layout-examples"></a>Esempi di layout di finestra di dialogo utilità  
 Tutte le dimensioni sono espressi in pixel.  
  
 ![Spaziatura della finestra di dialogo per le etichette sopra i controlli](../../extensibility/ux-guidelines/media/0801-a_utilityspacingabove.png "0801 a_UtilitySpacingAbove")  
  
 **Figura 08.01-r: Linee guida per le finestre di dialogo utilità con etichette sopra i controlli di spaziatura**  
  
 ![Spaziatura della finestra di dialogo per le etichette a sinistra dei controlli](../../extensibility/ux-guidelines/media/0801-b_utilityspacingleft.png "0801 b_UtilitySpacingLeft")  
  
 **Figura 08.01-b: Spaziatura linee guida per le finestre di dialogo utilità con etichette a sinistra dei controlli**  
  
### <a name="layout-details"></a>Dettagli del layout  
  
#### <a name="margins"></a>Margini  
  
-   Tutti i dialoghi devono avere un bordo di 12 pixel intorno ai contorni.  
  
-   I margini all'interno di una cornice di gruppo devono essere 9 pixel dal bordo del frame.  
  
-   I margini all'interno di un controllo struttura a schede devono essere di 6 pixel dal bordo del controllo scheda.  
  
#### <a name="command-buttons"></a>Pulsanti di comando  
  
-   Pulsanti di comando operano su frame finestra di dialogo, non sul contenuto. Che deve essere posizionati nella parte inferiore destra e deve avere sufficiente spazio delle variabili per impostare i pulsanti separati.  
  
-   Se sono presenti pulsanti orizzontali che operano nella finestra di dialogo, la configurazione di pulsante di comando alternativo è una pila verticale in alto a destra. Vedere [pulsanti di comando interni](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons) sotto.  
  
-   Lo spazio a sinistra dei pulsanti di comando (inferiore sinistra/al centro della finestra di dialogo) viene considerato parte della "banda" dei controlli di finestra di dialogo operazione. L'unico elemento che deve comparire in tale spazio è un collegamento alla Guida che è pertinente per l'attività generale o di una finestra di dialogo.  
  
-   Pulsanti di comando devono essere x 23 di 75 pixel.  
  
-   Pulsanti di comando devono essere di 6 pixel di distanza.  
  
 ![Allineamento di base dei pulsanti](../../extensibility/ux-guidelines/media/0801-c_buttonalign.png "0801 c_ButtonAlign")  
  
 **Figura 08.01-c: Allineamento di base dei pulsanti**  
  
#### <a name="labels"></a>Etichette  
  
-   Allinea a sinistra di tutte le etichette.  
  
-   Per le etichette che si trovano di sopra di un controllo, essi devono allineare a sinistra con precisione con il controllo sottostanti e inferiore dell'etichetta deve essere di 5 pixel di sopra di altro controllo (ad esempio, una casella combinata).  
  
-   Per le etichette che si trovano a sinistra dei controlli, la larghezza minima tra l'etichetta e il controllo di input è di 10 pixel. Per allineare le caselle di testo, caselle combinate o altri controlli, è necessario stabilire una seconda colonna implicita.  
  
-   Le etichette sono normale e sono seguite da due punti. Vedere [lo stile del testo](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).  
  
#### <a name="distance-between-controls"></a>Distanza tra i controlli  
 Stack ragionevolmente controlli. Non vi è alcun riferimento assoluto per la spaziatura tra i controlli in pila. Il livello tra i controlli può variare leggermente tra le finestre di dialogo. La spaziatura consigliata è 20 pixel per le coppie di controllo/etichetta verticale e 9 pixel per coppie orizzontale/etichetta del controllo. Spaziatura orizzontale coppie controllo minimo è 6 pixel.  
  
 ![Distanza tra i controlli consigliati](../../extensibility/ux-guidelines/media/0801-d_controldistance.png "0801 d_ControlDistance")  
  
 **Figura 08.01-d: Indicazioni per la distanza tra i controlli**  
  
#### <a name="control-indentation"></a>Controllo rientro  
 Quando i controlli sono nidificati, allineare i controlli interni in senso orizzontale con il bordo sinistro del controllo precedente, in genere l'etichetta.  
  
 ![Allineamento dei controlli annidati](../../extensibility/ux-guidelines/media/0801-e_controlalign.png "0801 e_ControlAlign")  
  
 **Figura 08.01-e: L'allineamento del controllo Nested**  
  
#### <a name="control-width"></a>Larghezza del controllo  
 La larghezza di una casella di testo o altri controlli simili deve essere non più lungo l'input medio per il campo. La parola inglese Media è cinque caratteri. Ad esempio, una casella di testo che richiede un nome di percorso lungo deve essere a condizione che consente il layout orizzontale, mentre un elenco a discesa per i nomi di piattaforma devono avere una lunghezza che consente la voce più lunga.  
  
#### <a name="helper-text"></a>Testo di supporto  
  
-   Una finestra di dialogo è possibile visualizzare il testo di supporto che fornisce ulteriori informazioni sullo scopo della finestra di dialogo. Ciò in genere si trova nella parte superiore e può essere frasi 1-2.  
  
-   La lunghezza di riga deve essere una larghezza di un utente analizzare e leggere familiarità. Una finestra di dialogo medio deve essere non più di 550 pixel di larghezza.  
  
####  <a name="BKMK_InteriorCommandButtons"></a> Pulsanti di comando interno  
 Nelle finestre di dialogo più complessi, un controllo interno potrebbe essere relativi pulsanti correlati, che possono influire in cui si trovano i pulsanti di commit della finestra di dialogo.  
  
-   Utilizzare i pulsanti quando l'allineamento verticale (colonna) della parte interna **OK**/**Annulla** orizzontalmente nell'angolo inferiore destro.  
  
-   Utilizzare i pulsanti l'allineamento orizzontale (riga) dell'interno quando **OK**/**Annulla** sono orientati in verticale in alto a destra. Questa situazione è meno comune.  
  
-   Dimensione del controllo button interno deve avere come destinazione le dimensioni di un pulsante standard di 75 x 23 pixel, la dimensione di corrispondenza **OK**/**Annulla** pulsanti quando possibile. Se un'etichetta rende il pulsante superano le dimensioni di un pulsante standard, gli altri pulsanti in tale set deve essere allineato con la dimensione più ampia.  
  
 ![Pulsanti OK e Annulla orizzontali](../../extensibility/ux-guidelines/media/0801-f_horizokcan.png "0801 f_HorizOKCan")  
  
 **Figura 08.01-f: Pulsanti verticale interno con OK/Annulla orizzontale**  
  
 ![Pulsanti OK e Annulla verticali](../../extensibility/ux-guidelines/media/0801-g_vertokcan.png "0801 g_VertOKCan")  
  
 **Figura 08.01-g Orizzontali interno i pulsanti con OK/Annulla verticale**  
  
#### <a name="browse-button"></a>[Sfoglia...] pulsante  
 **[Sfoglia...]**  pulsanti che seguono una casella di testo devono spiegare chiaramente "Sfoglia..." in modo completo, inclusi i puntini di sospensione. Se lo spazio è ridotto o sono presenti più **[Sfoglia...]**  pulsanti sullo schermo, il pulsante possono essere ridotto a semplicemente i puntini di sospensione.  
  
##  <a name="BKMK_ThemedDialogLayout"></a> Layout di finestra di dialogo con tema  
 Finestre di dialogo con tema in Visual Studio hanno un aspetto più chiaro e offrono più spazi. Tipografia fornisce ulteriori enfasi e interesse, che offre più aperto interlinea e una variante di pesi e le dimensioni dei caratteri. Dove possibile, chrome e titolo barre sono stati ridotte o rimosse. Il layout di queste finestre di dialogo deve seguire questo modello di base:  
  
1.  Lo sfondo della finestra di dialogo è bianco.  
  
2.  È disponibile un bordo della regola 1 pixel in un valore medio di grigio.  
  
3.  Non è più il titolo della finestra di dialogo si trova in una barra del titolo, ma fornisce l'interesse visivo ed enfasi un aumento delle dimensioni del punto. (Vedere la sezione di dimensioni del carattere in [lo stile del testo](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).)  
  
4.  Devono essere associate a un testo aggiuntivo, ad esempio una descrizione, etichette **tipo di carattere ambiente + grassetto**.  
  
5.  Colonne interne sono separate da una regola 1 pixel in grigio chiaro.  
  
6.  Collegamenti predefiniti non sono alcun carattere di sottolineatura. Al passaggio del mouse e premuti stati dispongono di una modifica del colore più di un carattere di sottolineatura.  
  
7.  Eseguire il commit pulsanti (ad esempio **OK**/**Annulla**) si trovano nell'angolo inferiore destro.  
  
### <a name="themed-dialog-layout-examples"></a>Esempi di layout di finestra di dialogo con tema  
 ![Layout di finestra di dialogo con tema](../../extensibility/ux-guidelines/media/0801-h_themeddialog.png "0801 h_ThemedDialog")  
  
 **Figura 08.01-h: Finestra di dialogo con tema**  
  
 ![Le dimensioni di finestra di dialogo con tema](../../extensibility/ux-guidelines/media/0801-i_themeddialogdimensions.png "0801 i_ThemedDialogDimensions")  
  
 **Figura 08.01-ricerca per categorie: Finestra di dialogo con tema - dimensioni**  
  
 ![I tipi di carattere di finestra di dialogo con tema](../../extensibility/ux-guidelines/media/0801-j_themeddialogfonts.png "0801 j_ThemedDialogFonts")  
  
 **Figura 08.01-j: Finestra di dialogo con tema - caratteri**  
  
 ![I colori di finestra di dialogo con tema](../../extensibility/ux-guidelines/media/0801-k_themeddialogcolors.png "0801 k_ThemedDialogColors")  
  
 **Figura 08.01-k: Finestra di dialogo con tema - colori**  
  
## <a name="see-also"></a>Vedere anche  
 [Modelli di applicazione per Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)   
 [Controlli (Windows)](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx)   
 [Finestre di dialogo (Windows)](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742499\(v=vs.85\).aspx)