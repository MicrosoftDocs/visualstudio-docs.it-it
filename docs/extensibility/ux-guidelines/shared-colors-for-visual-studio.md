---
title: Condiviso di colori per Visual Studio | Documenti Microsoft
ms.custom: ''
ms.date: 04/26/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b9093eef6166c86eb6e1ffdf602b4fb75841834d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="shared-colors-for-visual-studio"></a>Colori condivisi per Visual Studio
Quando si progetta un'interfaccia utente che usa elementi comuni della shell di Visual Studio, o si vuole elementi dell'interfaccia siano coerenti con funzionalità simili, utilizzare nomi di token esistenti in file di definizione del pacchetto per scegliere e assegnare i colori. In questo modo, l'interfaccia utente resta coerente con l'intero ambiente di Visual Studio e viene aggiornata automaticamente quando vengono aggiunti o aggiornati temi.  

Questo articolo descrive gli elementi dell'interfaccia utente comuni e i nomi di token usati da questi elementi, a cui è possibile fare riferimento durante la compilazione di un'interfaccia utente simile. Per informazioni specifiche su come accedere a questi token di colore, vedere [il servizio VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).  

Assicurarsi di usare correttamente i nomi di token:  

-   **Usare nomi di token in base a funzione e non al colore stesso.** I colori condivisi comuni sono associati a elementi dell'interfaccia specifici e destinati solo a essere usati per le stesse funzionalità o altre simili. Ad esempio, evitare di riutilizzare il colore di una casella combinata premuta per un'animazione di stato rotante solo perché si ha una preferenza per questo colore. Le funzioni di una casella combinata e dell'animazione sono diverse e se il colore associato con la casella combinata cambia, non potrebbe essere non è più un colore appropriato per l'elemento animazione. Un uso coerente del colore aiuta a orientare correttamente gli utenti e a impedire confusione.  

-   **Utilizzare i colori di sfondo e del testo nella combinazione corretta.** I colori di sfondo destinati a essere usati con il testo implicano un colore del testo associato. Non usare colori del testo diversi da quelli specificati per un determinato sfondo. Se non è un colore del testo associato, non usare il colore di sfondo per alcuna superficie in cui si prevede di visualizzare il testo. Altre combinazioni di colori di sfondo e del testo potrebbe essere un'interfaccia illeggibile.  

-   **Utilizzare i colori di controllo appropriate per la loro posizione.** Alcuni stati, alcuni controlli di Visual Studio non hanno colori di sfondo e dei bordi separati. Al contrario, selezionano questi colori dalle superfici sottostanti. Assicurarsi di usare sempre i nomi di token appropriati per la posizione in cui si posiziona il controllo.  

> [!IMPORTANT]
> Non utilizzare i token inclusi nelle categorie "Pagina iniziale" o "Cider".  

## <a name="common-shared-controls"></a>Controlli condivisi comuni

Quando si utilizza una barra dei comandi di Visual Studio standard nella propria funzionalità, sarà possibile accedere a controlli della shell con stile. Non è consigliabile reimpostare come modelli questi controlli comuni. Tuttavia, se si intende compilare una barra dei comandi personalizzata, potrebbe essere necessario compilare anche controlli personalizzati. In questo caso, assicurarsi di usare i nomi di token corretti per ognuno dei controlli seguenti, in modo che l'interfaccia utente sia coerente con il resto di Visual Studio.

### <a name="button-controls"></a>Controlli pulsante

![Button (controllo) con linea rossa](../../extensibility/ux-guidelines/media/0303-155_buttoncontrolredline.png "0303 155_ButtonControlRedline")

| Usare... | Non usare... |
| --- | --- |
| ... per i pulsanti nell'area dei documenti che si desidera integrare con temi di Visual Studio (chiaro, scuro, blu o un tema a contrasto elevato system). | ... per i pulsanti che verranno visualizzati su uno sfondo personalizzato che non fa parte di un tema di Visual Studio. |

**Button: stato standard**

![Pulsante standard](../../extensibility/ux-guidelines/media/03.03.Button.Standard.png "03.03.Button.Standard")<br />Pulsante standard

| Elemento | Nome token: Category.color |
| --- | --- |
| Button | `CommonControls.Button` |
| Bordo del pulsante | `CommonControls.ButtonBorder` |

**Button: stato predefinito**

![Pulsante predefinito](../../extensibility/ux-guidelines/media/03.03.Button.Default.png "03.03.Button.Default")<br />Pulsante predefinito

| Elemento | Nome token: Category.color | 
| --- | --- | 
| Button | `CommonControls.ButtonDefault` |
| Bordo del pulsante | `CommonControls.ButtonBorderDefault` |

**Button: stato disabilitato**  

![Pulsante disabilitato](../../extensibility/ux-guidelines/media/03.03.Button.Disabled.png "03.03.Button.Disabled")<br />Pulsante disabilitato  

| Elemento | Nome token: Category.color |
| --- | --- |
| Button | `CommonControls.ButtonDisabled` |
| Bordo del pulsante | `CommonControls.ButtonBorderDisabled` |

**Sul pulsante: stato del mouse**  

![Pulsante del mouse](../../extensibility/ux-guidelines/media/03.03.Button.hover.png "03.03.Button.hover")<br />Pulsante al passaggio del mouse  

| Elemento | Nome token: Category.color |
| --- | --- |
| Button | `CommonControls.ButtonHover` |
| Bordo del pulsante | `CommonControls.ButtonBorderHover` |

**Button: stato pressed**  

![Pulsante premuto](../../extensibility/ux-guidelines/media/03.03.Button.Pressed.png "03.03.Button.Pressed")<br />Pulsante premuto  

| Elemento | Nome token: Category.color |
| --- | --- |
| Button | `CommonControls.ButtonPressed` |
| Bordo del pulsante | `CommonControls.ButtonBorderPressed` |

**Pulsanti: con lo stato attivo allo stato**  

![Pulsante con stato attivo](../../extensibility/ux-guidelines/media/03.03.Button.Focused.png "03.03.Button.Focused")<br />Pulsante con stato attivo  

| Elemento | Nome token: Category.color |
| --- | --- |
| Button | `CommonControls.ButtonFocused` |
| Bordo del pulsante | `CommonControls.ButtonBorderFocused` |

### <a name="check-box-controls"></a>Controlli casella di controllo  
![Casella di controllo (con linea rossa)](../../extensibility/ux-guidelines/media/0303-161_checkboxredline.png "0303 161_CheckboxRedline")<br />Casella di controllo (con linea rossa)  

| Usare... | Non usare... |
| --- | --- |
| per i controlli casella di controllo contenuti all'interno del documento nonché.... | per qualsiasi interfaccia utente che non è un controllo casella di controllo. |

**Casella di controllo: stato predefinito**  

![Casella di controllo](../../extensibility/ux-guidelines/media/0303-162_checkbox.png "0303 162_Checkbox")<br />Casella di controllo predefinito

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `CommonControls.CheckBoxBackground` |
| Bordo | `CommonControls.CheckBoxBorder` |
| Testo | `CommonControls.CheckBoxText` |
| Icona | `CommonControls.CheckBoxGlyph` |

**Casella di controllo: stato disabilitato**  

![Casella di controllo disabilitata](../../extensibility/ux-guidelines/media/0303-163_checkboxdisabled.png "0303 163_CheckboxDisabled")<br />Casella di controllo disabilitata  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `CommonControls.CheckBoxBackgroundDisabled` |
| Bordo | `CommonControls.CheckBoxBorderDisabled` |
| Testo | `CommonControls.CheckBoxTextDisabled` |
| Icona | `CommonControls.CheckBoxGlyphDisabled` |

**Casella di controllo: passare il puntatore dello stato**  

 ![Casella di controllo al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-164_checkboxhover.png "0303 164_CheckboxHover")<br />Casella di controllo al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `CommonControls.CheckBoxBackgroundHover` |
| Bordo | `CommonControls.CheckBoxBorderHover` |
| Testo | `CommonControls.CheckBoxTextHover` |
| Icona | `CommonControls.CheckBoxGlyphHover` |  

**Casella di controllo: stati**  

![Casella di controllo premuta](../../extensibility/ux-guidelines/media/0303-165_checkboxpressed.png "0303 165_CheckboxPressed")<br />Tasto premuto sulla casella di controllo  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `CommonControls.CheckBoxBackgroundPressed` |
| Bordo | `CommonControls.CheckBoxBorderPressed` |
| Testo | `CommonControls.CheckBoxTextPressed` |
| Icona | `CommonControls.CheckBoxGlyphPressed` |  

**Casella di controllo: con stato attivo dello stato**  

![Casella di controllo mirato](../../extensibility/ux-guidelines/media/0303-166_checkboxfocused.png "0303 166_CheckboxFocused")<br />Casella di controllo con stato attivo  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `CommonControls.CheckBoxBackgroundFocused` |
| Bordo | `CommonControls.CheckBoxBorderFocused` |
| Testo | `CommonControls.CheckBoxTextFocused` |
| Icona | `CommonControls.CheckBoxGlyphFocused` |

### <a name="drop-downs-and-combo-boxes"></a>Elenchi a discesa e combinata finestre
![Casella combinata/a discesa-rilascio (con linea rossa)](../../extensibility/ux-guidelines/media/0303-167_dropdowncomboboxredline.png "0303 167_DropDownComboBoxRedline")<br />Casella di riepilogo o combinata a discesa (con linea rossa)  

| Usare... | Non usare... |
| --- | --- |
| ... per elenchi a discesa e combinata caselle nel documento anche. | ... per qualsiasi interfaccia utente che non è un'elenco a discesa o una casella combinata. |  
| | ... per la barra dei comandi [elenchi a discesa](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown) o [caselle combinate](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox). |

**Elenchi a discesa e combinata caselle: stato predefinito**  

![Casella combinata/a discesa-rilascio predefinito](../../extensibility/ux-guidelines/media/0303-168_dropdowncombobox.png "0303 168_DropDownComboBox")<br />Casella di riepilogo o combinata a discesa predefinito

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `CommonControls.ComboBoxBackground` |
| Bordo | `CommonControls.ComboBoxBorder` |
| Testo | `CommonControls.ComboBoxText` |
| Separatore | `CommonControls.ComboBoxSeparator` |
| Glifo | `CommonControls.ComboBoxGlyph` |
| Sfondo del glifo | `CommonControls.ComboBoxGlyphBackground` |

**Elenchi a discesa e combinata caselle: stato disabilitato**  

![Casella combinata/a discesa-rilascio disabilitata](../../extensibility/ux-guidelines/media/0303-169_dropdowncomboboxdisabled.png "0303 169_DropDownComboBoxDisabled")<br />Casella di riepilogo o combinata a discesa disabilitata

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `CommonControls.ComboBoxBackgroundDisabled` |
| Bordo | `CommonControls.ComboBoxBorderDisabled` |
| Testo | `CommonControls.ComboBoxTextDisabled` |
| Separatore | `CommonControls.ComboBoxSeparatorDisabled` |
| Glifo | `CommonControls.ComboBoxGlyphDisabled` |
| Sfondo del glifo | `CommonControls.ComboBoxGlyphBackgroundDisabled` |

**Elenchi a discesa e combinata caselle: passare il puntatore dello stato**  

![Casella di riepilogo o combinata a discesa al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-170_dropdowncomboboxhover.png "0303 170_DropDownComboBoxHover")<br />Casella combinata/a discesa al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `CommonControls.ComboBoxBackgroundHover` |
| Bordo | `CommonControls.ComboBoxBorderHover` |
| Testo | `CommonControls.ComboBoxTextHover` |
| Separatore | `CommonControls.ComboBoxSeparatorHover` |
| Glifo | `CommonControls.ComboBoxGlyphHover` |
| Sfondo del glifo | `CommonControls.ComboBoxGlyphBackgroundHover` |

**Elenchi a discesa e combinata caselle: stati**  

![Casella combinata/a discesa-rilascio selezionata](../../extensibility/ux-guidelines/media/0303-171_dropdowncomboboxpressed.png "0303 171_DropDownComboBoxPressed")<br />Casella di riepilogo o combinata a discesa selezionata  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `CommonControls.ComboBoxBackgroundPressed` |
| Bordo | `CommonControls.ComboBoxBorderPressed` |
| Testo | `CommonControls.ComboBoxTextPressed` |
| Separatore | `CommonControls.ComboBoxSeparatorPressed` |
| Glifo | `CommonControls.ComboBoxGlyphPressed` |
| Sfondo del glifo | `CommonControls.ComboBoxGlyphBackgroundPressed` |

**Elenchi a discesa e combinata le finestre di visualizzazione elemento elenco: stati**  

 ![Casella combinata/a discesa-rilascio premuto visualizzazione elemento elenco](../../extensibility/ux-guidelines/media/0303-174_dropdowncomboboxlistview.png "0303 174_DropDownComboBoxListView")<br />Casella di riepilogo o combinata a discesa premuto visualizzazione elemento elenco  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo |  `CommonControls.ComboBoxListBackground`<br />`CommonControls.ComboBoxListBackgroundHover`<br />`CommonControls.ComboBoxListItemBackgroundPressed`<br />`CommonControls.ComboBoxListItemBackgroundFocused` |
| Bordo | `CommonControls.ComboBoxListBorder`<br />`CommonControls.ComboBoxListBorderHover`<br />`CommonControls.ComboBoxListBorderPressed`<br />`CommonControls.ComboBoxListBorderFocused` |
| Testo dell'elemento | `CommonControls.ComboBoxListItemText`<br /> `CommonControls.ComboBoxListItemTextHover`<br />`CommonControls.ComboBoxListItemTextPressed`<br />`CommonControls.ComboBoxListItemTextFocused` |
| Ombreggiatura dello sfondo | `CommonControls.ComboBoxListBackgroundShadow` |

**Elenchi a discesa e combinata caselle: con stato attivo dello stato**  

![Casella combinata/a discesa-rilascio con lo stato attivo](../../extensibility/ux-guidelines/media/0303-172_dropdowncomboboxfocused.png "0303 172_DropDownComboBoxFocused")<br />Casella di riepilogo o combinata a discesa con stato attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `CommonControls.ComboBoxBackgroundFocused` |
| Bordo | `CommonControls.ComboBoxBorderFocused` |
| Testo | `CommonControls.ComboBoxTextFocused` |
| Separatore | `CommonControls.ComboBoxSeparatorFocused` |
| Glifo | `CommonControls.ComboBoxGlyphFocused` |
| Sfondo del glifo | `CommonControls.ComboBoxGlyphBackgroundFocused` |

**Elenchi a discesa e combinata caselle: selezione di input di testo**  

![Selezione di input di testo della casella combinata/a discesa-rilascio](../../extensibility/ux-guidelines/media/0303-173_dropdowncomboboxtextinput.png "0303 173_DropDownComboBoxTextInput")<br />Selezione di input di testo della casella di riepilogo o combinata a discesa  

| Elemento | Nome token: Category.color |
| --- | --- |
| Evidenziazione | `CommonControls.ComboBoxTextInputSelection` |

### <a name="tabular-data-grid-controls"></a>Controlli per dati tabulari (griglia)  
I controlli per dati tabulari, noti anche come controlli griglia, sono controlli comuni per Visual Studio, che possono essere usati per presentare grandi quantità di dati in più colonne. I controlli per dati tabulari standard possono trovarsi in diverse posizioni all'interno di Visual Studio, ad esempio nella finestra degli strumenti Elenco errori, nei report IntelliTrace e nella visualizzazione degli heap della memoria. Usare sempre i controlli per dati tabulari standard forniti. In alcuni casi rari, si potrebbe non avere accesso ai controlli per dati tabulari standard. In questi casi, usare i nomi di token seguenti per garantire che l'interfaccia utente sia coerente con gli altri controlli per dati tabulari in Visual Studio.  

![Controllo dati tabulari/griglia (con linea rossa)](../../extensibility/ux-guidelines/media/0303-197_tabulardatagridcontrolredline.png "0303 197_TabularDataGridControlRedline")<br />Controllo dati tabulari o griglia (con linea rossa)

| Usare... | Non usare... |
| --- | --- |
| … for tabulari o i controlli griglia. | per qualsiasi interfaccia utente che non è un controllo tabulare o griglia. |

#### <a name="column-headers"></a>Intestazioni di colonna  
Le intestazioni di colonna sono costituite da uno sfondo, un bordo, il testo del titolo e un glifo facoltativo, usato in genere quando una griglia viene ordinata in base alla colonna.  

**Intestazione di colonna: stato predefinito**

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Header.Default` |
| Primo piano (testo) | `Environment.CommandBarTextActive` |
| Primo piano (glifo) | `Header.Glyph` |
| Bordo | `Header.SeparatorLine` |

**Intestazione di colonna: passare il puntatore dello stato**

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Header.MouseOver` |
| Primo piano (testo) | `Environment.CommandBarTextHover` |
| Primo piano (glifo) | `Header.MouseOverGlyph` |
| Bordo | `Header.SeparatorLine` |

**Intestazione di colonna: stati**

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `CommonControls.CheckBoxBackgroundPressed` |
| Primo piano (testo) | `CommonControls.CheckBoxBorderPressed` |
| Primo piano (glifo) | `CommonControls.CheckBoxTextPressed` |
| Bordo | `CommonControls.CheckBoxGlyphPressed` |

#### <a name="list-view-items"></a>Elementi della visualizzazione elenco  
 Gli elementi della visualizzazione elenco sono costituiti da uno sfondo e da contenuto. Il contenuto può essere sotto forma di testo, icona o entrambi.  

**Elencare gli elementi di visualizzazione: stato predefinito**

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | Trasparente |
| Primo piano (testo) | `Environment.CommandBarTextActive` |
| Bordo | Nessuno |

**Elencare gli elementi di visualizzazione: lo stato attivo**

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `TreeView.SelectedItemActive` |
| Primo piano (testo) | `TreeView.SelectedItemActiveText` |
| Bordo | Nessuno |

**Elencare gli elementi di visualizzazione: stato inattivo**

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `TreeView.SelectedItemInactive` |
| Primo piano (testo) | `TreeView.SelectedItemInactiveText` |
| Bordo | Nessuno |  

### <a name="ui-text"></a>Testo dell'interfaccia utente

#### <a name="instructional-text"></a>Testo esplicativo
Testo esplicativo fornisce una spiegazione principale principali delle operazioni da eseguire in una pagina della finestra di dialogo o documento.

![Testo esplicativo predefinito](../../extensibility/ux-guidelines/media/0303_InstructionalText.png "0303_InstructionalText.png")<br />Testo informativo predefinito

| Elemento | Nome token: Category.color |
| --- | --- |
| In primo piano (testo) | `Environment.ControlText` |

#### <a name="secondary-instructional-text"></a>Testo esplicativo secondario
Nelle pagine di documento con un numero elevato di testo e controlli, del testo esplicativo utilizza un valore di colore diverso. Ciò consente di trasmettere le informazioni che sono la più importante e ridurre la densità di elementi dell'interfaccia utente. (Vedere anche la seguente sezione nel testo di suggerimento.)

![Testo esplicativo secondario](../../extensibility/ux-guidelines/media/0303_SecondaryInstructionalText.png "0303_SecondaryInstructionalText.png")<br />Testo esplicativo secondario

| Elemento | Nome token: Category.color |
| --- | --- |
| In primo piano (testo) | `Environment.ControlEditHintText` |

#### <a name="hint-text"></a>Testo di suggerimento
Testo di suggerimento viene visualizzato in un controllo vuoto, di sotto di un controllo o su una superficie di un documento vuoto per indicare all'utente per procedere. È possibile utilizzare testo di suggerimento con sfondi finestra o del controllo.

**Testo di suggerimento predefinito**

![Testo di suggerimento predefinito](../../extensibility/ux-guidelines/media/0303_HintText.png "0303_HintText.png")<br />Testo di suggerimento predefinito

| Elemento | Nome token: Category.color |
| --- | --- |
| In primo piano (testo) | `Environment.ControlEditHintText` |

**Testo di suggerimento obbligatorio**

![Testo di suggerimento obbligatorio](../../extensibility/ux-guidelines/media/0303_RequiredHintText.png "0303_RequiredHintText.png")<br />Testo di suggerimento obbligatorio

| Elemento | Nome token: Category.color |
| --- | --- |
| In primo piano (testo) | `Environment.ControlRequiredHintText` |
| Sfondo | `Environment.ControlRequiredBackground` |

**Testo di controllo casella di ricerca**

> Vedere [caselle di ricerca](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_SearchBoxes) per altri token di colore correlati al controllo di ricerca.

![Testo della casella di controllo di ricerca](../../extensibility/ux-guidelines/media/0303_SearchBoxControl.png "0303_SearchBoxControl.png")<br />Testo di controllo casella di ricerca

| Elemento | Nome token: Category.color |
| --- | --- |
| In primo piano (testo) | `SearchControl.UnfocusedWatermarkText` |

### <a name="hyperlink"></a>Hyperlink  
Il collegamento ipertestuale è un controllo che non dispone di una coppia di primo piano/sfondo. In tutti i casi, usare il colore primo piano di collegamento ipertestuale, che verrà visualizzati correttamente su sfondi scuri, grigi e bianchi. Se non si usa il token di colore per il controllo collegamento ipertestuale, si verrà visualizzato il colore di sistema predefinito per "premuto", che sarà di colore rosso lampeggiante. Che indica che il controllo non sta utilizzando il token di colore di ambiente corretto.  

![Collegamento ipertestuale (con linea rossa)](../../extensibility/ux-guidelines/media/0303-133_hyperlinkredline.png "0303 133_HyperlinkRedline")<br />Collegamento ipertestuale (con linea rossa)

| Usare... | Non usare... |
| --- | --- |
| ... quando è necessario creare un collegamento ipertestuale personalizzato. | per qualsiasi elemento che non è un collegamento ipertestuale. |

**Un collegamento ipertestuale: stato predefinito**  

![Collegamento ipertestuale predefinito](../../extensibility/ux-guidelines/media/0303-134_hyperlink.png "0303 134_Hyperlink")<br />Collegamento ipertestuale predefinito

| Elemento | Nome token: Category.color |
| --- | --- |
| Primo piano (testo) | `Environment.PanelHyperlink` |

**Collegamento ipertestuale: stato mouse**

![Collegamento ipertestuale al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-135_hyperlinkhover.png "0303 135_HyperlinkHover")<br />Collegamento ipertestuale al passaggio del mouse  

| Elemento | Nome token: Category.color |
| --- | --- |
| Primo piano (testo) | `Environment.PanelHyperlinkHover` |

**Collegamento ipertestuale: stato pressed**

![Collegamento ipertestuale premuto](../../extensibility/ux-guidelines/media/0303-136_hyperlinkpressed.png "0303 136_HyperlinkPressed")<br />Collegamento ipertestuale selezionato  

| Elemento | Nome token: Category.color |
| --- | --- |
| Primo piano (testo) | `Environment.PanelHyperlinkPressed` |

**Collegamento ipertestuale: stato disabilitato**

![Collegamento ipertestuale disabilitato](../../extensibility/ux-guidelines/media/0303-137_hyperlinkdisabled.png "0303 137_HyperlinkDisabled")<br />Collegamento ipertestuale disabilitato  

| Elemento | Nome token: Category.color |
| --- | --- |
| Primo piano (testo) | `Environment.PanelHyperlinkDisabled` |

### <a name="infobars"></a>Barre informazioni  
Le barre informazioni vengono usate per fornire altre informazioni su un contesto specifico e sono sempre visualizzate nella parte superiore della finestra di un documento o di una finestra degli strumenti.  

![Barra informazioni (con linea rossa)](../../extensibility/ux-guidelines/media/0303-138_infobarredline.png "0303 138_InfobarRedline")<br />Barra informazioni (con linea rossa)

| Usare... | Non usare... |
| --- | --- |
| ... quando si creano barre informazioni personalizzate. | ... per gli elementi dell'interfaccia utente che non sono simili a una barra informazioni. |

**Barra informazioni: stato predefinito**

![Barra informazioni predefinite](../../extensibility/ux-guidelines/media/0303-139_infobar.png "0303 139_Infobar")<br />Barra informazioni predefinito

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `InfoBar.InfoBarBackground` |
| Primo piano (testo) | `InfoBar.InfoBar` |
| Bordo | `InfoBar.InfoBarBorder` |

**Barra informazioni Close (&times;) pulsante: stato predefinito**

![Predefinito barra informazioni chiusura (&times;) sul pulsante](../../extensibility/ux-guidelines/media/0303_InfobarCloseDefault.png "0303_InfobarCloseDefault.png")<br />Barra informazioni chiudere predefinito (&times;) pulsante

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `InfoBar.CloseButton` |
| Bordo | `InfoBar.CloseButtonBorder` |
| Icona | `InfoBar.CloseButtonGlyph` |

**Barra informazioni Close (&times;) pulsante: passare il puntatore dello stato**

![Barra informazioni chiusura (&times;) pulsante del mouse](../../extensibility/ux-guidelines/media/0303_InfobarCloseHover.png "0303_InfobarCloseHover.png")<br />Barra informazioni Close (&times;) pulsante al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `InfoBar.CloseButtonHover` |
| Bordo | `InfoBar.CloseButtonHoverBorder` |
| Icona | `InfoBar.CloseButtonHoverGlyph` |

**Barra informazioni Close (&times;) pulsante: stati**

![Premuto barra informazioni chiusura (&times;) sul pulsante](../../extensibility/ux-guidelines/media/0303_InfobarClosePressed.png "0303_InfobarClosePressed.png")<br />Barra informazioni chiudere premuto (&times;) pulsante

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `InfoBar.CloseButtonDown` |
| Bordo | `InfoBar.CloseButtonDownBorder` |
| Icona | `InfoBar.CloseButtonDownGlyph` |

**Pulsante barra informazioni del collegamento ipertestuale: stato predefinito**

![Pulsante di collegamento ipertestuale predefinito barra informazioni](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Pulsante di collegamento ipertestuale predefinito barra informazioni

| Elemento | Nome token: Category.color |
| --- | --- |
| In primo piano (testo) | `InfoBar.Hyperlink` |

**Pulsante barra informazioni del collegamento ipertestuale: passare il puntatore dello stato**

![Barra informazioni pulsante collegamento ipertestuale al passaggio del mouse](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonHover.png "0303_InfobarHyperlinkButtonHover.png")<br />Barra informazioni pulsante di collegamento ipertestuale al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| In primo piano (testo) | `Infobar.HyperlinkMouseOver`<br />(Con carattere di sottolineatura) |

**Pulsante barra informazioni del collegamento ipertestuale: stati**

![Pulsante premuto barra informazioni del collegamento ipertestuale](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonPressed.png "0303_InfobarHyperlinkButtonPressed.png")<br />Pulsante premuto barra informazioni

| Elemento | Nome token: Category.color |
| --- | --- |
| In primo piano (testo) | `Infobar.HyperlinkMouseDown`<br />(Con carattere di sottolineatura) |

**Collegamento ipertestuale inline barra informazioni (all'interno di una frase): stato predefinito**

![Pulsante di collegamento ipertestuale predefinito inline barra informazioni](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Pulsante di collegamento ipertestuale predefinito inline barra informazioni

| Elemento | Nome token: Category.color |
| --- | --- |
| In primo piano (testo) | `InfoBar.Hyperlink` |

**Collegamento ipertestuale inline barra informazioni (all'interno di una frase): passare il puntatore dello stato**

![Pulsante di collegamento ipertestuale incorporato barra informazioni del mouse](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlineHover.png "0303_InfobarHyperlinkInlineHover.png")<br />Pulsante di collegamento ipertestuale incorporato barra informazioni al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| In primo piano (testo) | `Infobar.HyperlinkMouseOver`<br />(Con carattere di sottolineatura) |

**Collegamento ipertestuale inline barra informazioni (all'interno di una frase): stati**

![Pulsante di collegamento ipertestuale incorporato barra informazioni premuto](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlinePressed.png "0303_InfobarHyperlinkInlinePressed.png")<br />Barra informazioni in linea un collegamento ipertestuale pulsante selezionato

| Elemento | Nome token: Category.color |
| --- | --- |
| In primo piano (testo) | `Infobar.HyperlinkMouseDown`<br />(Con carattere di sottolineatura) |

**Pulsante barra informazioni: stato predefinito**

![Pulsante barra informazioni predefinito](../../extensibility/ux-guidelines/media/0303_InfobarButtonDefault.png "0303_InfobarButtonDefault.png")<br />Pulsante barra informazioni predefinito

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `InfoBar.Button` |
| In primo piano (testo) | `InfoBar.Button` |
| Bordo | `InfoBar.ButtonBorder` |

**Pulsante barra informazioni: passare il puntatore dello stato**

![Barra informazioni pulsante del mouse](../../extensibility/ux-guidelines/media/0303_InfobarButtonHover.png "0303_InfobarButtonHover.png")<br />Pulsante al passaggio del mouse sulla barra informazioni

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `InfoBar.ButtonMouseOver` |
| In primo piano (testo) | `InfoBar.ButtonMouseOver` |
| Bordo | `InfoBar.ButtonMouseOverBorder` |

**Pulsante barra informazioni: stati**

![Pulsante barra informazioni premuto](../../extensibility/ux-guidelines/media/0303_InfobarButtonPressed.png "0303_InfobarButtonPressed.png")<br />Pulsante premuto barra informazioni

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `InfoBar.ButtonMouseDown` |
| In primo piano (testo) | `InfoBar.ButtonMouseDown` |
| Bordo | `InfoBar.ButtonMouseDownBorder` |

**Pulsante barra informazioni: stato disabilitato**

![Pulsante barra informazioni disabilitato](../../extensibility/ux-guidelines/media/0303_InfobarButtonDisabled.png "0303_InfobarButtonDisabled.png")<br />Pulsante disabilitato barra informazioni

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `InfoBar.ButtonDisabled` |
| In primo piano (testo) | `InfoBar.ButtonDisabled` |
| Bordo | `InfoBar.ButtonDisabledBorder` |

**Pulsante barra informazioni: con stato attivo dello stato**

![Pulsante barra informazioni con lo stato attivo](../../extensibility/ux-guidelines/media/0303_InfobarButtonFocus.png "0303_InfobarButtonFocus.png")<br />Pulsante con stato attivo sulla barra informazioni

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `InfoBar.ButtonFocus` |
| In primo piano (testo) | `InfoBar.ButtonFocus` |
| Bordo | `InfoBar.ButtonFocusBorder` |

### <a name="scroll-bars"></a>Barre di scorrimento  
Barre di scorrimento vengono applicato uno stile dall'ambiente di Visual Studio e non sarà necessario applicare un tema. Tuttavia, è possibile che si desidera sfruttare i colori usati nelle barre di scorrimento in modo che l'interfaccia utente appaia sempre coerenza con questa parte dell'ambiente di Visual Studio.  

![Barra di scorrimento (con linea rossa)](../../extensibility/ux-guidelines/media/0303-140_scrollbarredline.png "0303 140_ScrollbarRedline")<br />Barra di scorrimento (con linea rossa)

| Usare... | Non usare... |
| --- | --- |
| ... durante la creazione dell'interfaccia utente che si desidera recuperare le barre di scorrimento di Visual Studio. | ... per tutti gli elementi che non si desidera sempre corrispondere dell'interfaccia utente della barra di scorrimento. |

**Barra di scorrimento: stato predefinito**  

![Barra di scorrimento predefinito](../../extensibility/ux-guidelines/media/0303-141_scrollbar.png "0303 141_Scrollbar")<br />Barra di scorrimento predefinito

| Elemento | Nome token: Category.color |
| --- | --- |
| Barra di scorrimento | `Environment.ScrollBarBackground` |
| Primo piano (anteprima) | `Environment.ScrollBarThumbBackground` |

**Barra di scorrimento: passare il puntatore dello stato**

![Barra di scorrimento al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-143_scrollbarhover.png "0303 143_ScrollbarHover")<br />Barra di scorrimento al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Barra di scorrimento | `Environment.ScrollBarBackground` |
| Primo piano (anteprima) | `Environment.ScrollBarThumbMouseOverBackground` |

*Barra di scorrimento: stati**

![Barra di scorrimento premuto](../../extensibility/ux-guidelines/media/0303-145_scrollbarpressed.png "0303 145_ScrollbarPressed")<br />Barra di scorrimento premuto  

| Elemento | Nome token: Category.color |
| --- | --- |
| Barra di scorrimento | `Environment.ScrollBarBackground` |
| Primo piano (anteprima) | `Environment.ScrollBarThumbPressedBackground` |

**Barra freccia di scorrimento: stato predefinito**  

![Freccia della barra di scorrimento predefinito](../../extensibility/ux-guidelines/media/0303-142_scrollbararrow.png "0303 142_ScrollbarArrow")<br />Freccia della barra di scorrimento predefinito

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ScrollBarArrowBackground`<br />(Impostato sullo stesso colore della barra di scorrimento). |
| Primo piano (glifo) | `Environment.ScrollBarArrowGlyph` |

**Barra freccia di scorrimento: passare il puntatore dello stato**

![Freccia su hover delle barre di scorrimento](../../extensibility/ux-guidelines/media/0303-144_scrollbararrowhover.png "0303 144_ScrollbarArrowHover")<br />Freccia della barra di scorrimento al passaggio del mouse  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ScrollBarArrowMouseOverBackground`<br />(Impostato sullo stesso colore della barra di scorrimento). |
| Primo piano (glifo) | `Environment.ScrollBarArrowGlyphMouseOver` |

**Barra freccia di scorrimento: stati**  

![Freccia della barra di scorrimento premuto](../../extensibility/ux-guidelines/media/0303-146_scrollbararrowpressed.png "0303 146_ScrollbarArrowPressed")<br />Freccia della barra di scorrimento premuto

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ScrollBarArrowPressedBackground`<br />(Impostato sullo stesso colore della barra di scorrimento). |
| Primo piano (glifo) | `Environment.ScrollBarArrowGlyphPressed` |

### <a name="BKMK_SearchBoxes"></a>Caselle di ricerca  
Quando è possibile, usare il controllo di ricerca comune fornito dall'ambiente di Visual Studio. I colori della casella di ricerca si trovano nella categoria "SearchControl" nel file **ShellColors.pkgdef** , che contiene i nomi di token per il campo di input, il pulsante di azione, il pulsante a discesa e il menu a discesa.  

Una casella di ricerca può avere diversi stati, alcuni dei quali si escludono a vicenda:  

-   "Con stato attivo" e "con stato non attivo" indicano se il cursore si trova o meno nella casella di testo.  

-   "Attivo" e "inattivo" indicano se l'utente ha inserito una query di ricerca nella casella di testo.  

-   "Passaggio del mouse" significa che l'utente ha posizionato il cursore del mouse sulla casella di ricerca (questo stato sostituisce tutti gli altri).  

-   "Disabilitato" significa che la funzionalità di ricerca è disattivata per il contesto corrente.  

![Casella di ricerca (con linea rossa)](../../extensibility/ux-guidelines/media/0303-110_searchboxredline.png "0303 110_SearchBoxRedline")<br />Casella di ricerca (con linea rossa)  

| Usare... | Non usare... |
| --- | --- |
| ... quando si progetta una casella di ricerca personalizzato. | per qualsiasi elemento che non è una casella di ricerca. |
| | per qualsiasi elemento che non si desidera sempre corrispondere la ricerca... casella interfaccia utente. |

**Con stato attivo di campo di input di ricerca**

![Campo di input di ricerca con stato attivo](../../extensibility/ux-guidelines/media/0303-111_searchinputfieldfocused.png "0303 111_SearchInputFieldFocused")<br />Con stato attivo di campo di input di ricerca  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `SearchControl.FocusedBackground` |
| Primo piano (testo) | `SearchControl.FocusedBackground` |
| Bordo | `SearchControl.FocusedBorder` |
| Separatore | `SearchControl.FocusedDropDownSeparator` |

**Campo di input di ricerca con stato non attivo, attivo**

![Campo di input ricerca con stato non attivo](../../extensibility/ux-guidelines/media/0303-114_searchinputfieldunfocused.png "0303 114_SearchInputFieldUnfocused")<br />Campo di input di ricerca con stato non attivo, attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `SearchControl.SearchActiveBackground` |
| Primo piano (testo) | `SearchControl.SearchActiveBackground` |
| Bordo | `SearchControl.UnfocusedBorder` |
| Separatore | `SearchControl.DropDownSeparator` |

**Campo di input di ricerca con stato non attivo e inattivo**

![Campo di input di ricerca con stato non attivo e inattivo](../../extensibility/ux-guidelines/media/0303-114-1_searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br />Campo di input di ricerca con stato non attivo e inattivo  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `SearchControl.Unfocused` |
| Primo piano (testo) | `SearchControl.Unfocused` |
| Bordo | `SearchControl.UnfocusedBorder` |
| Separatore | `SearchControl.DropDownSeparator` |

**Campo di input di ricerca evidenziato (solo testo)**

![Campo di input di ricerca evidenziato](../../extensibility/ux-guidelines/media/0303-120_searchinputfieldhighlight.png "0303 120_SearchInputFieldHighlight")<br />Campo di input di ricerca evidenziato

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `SearchControl.Selection` |
| Primo piano (testo) | `SearchControl.FocusedBackground` |
| Bordo | Nessuno |
| Separatore | `SearchControl.FocusedDropDownSeparator` |

**Campo di input di ricerca disabilitato**

![Campo di input di ricerca disabilitato](../../extensibility/ux-guidelines/media/0303-121_searchinputfielddisabled.png "0303 121_SearchInputFieldDisabled")<br />Campo di input di ricerca disabilitato

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `SearchControl.Disabled` |
| Primo piano (testo) | `SearchControl.Disabled` |
| Bordo | `SearchControl.DisabledBorder` |
| Separatore | `SearchControl.DropDownSeparator` |

**Pulsante di azione di ricerca con stato attivo**

![Pulsante di azione di ricerca con stato attivo](../../extensibility/ux-guidelines/media/0303-112_searchactionbuttonfocused.png "0303 112_SearchActionButtonFocused")<br />Pulsante di azione di ricerca con stato attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | Nessuno |
| Primo piano (glifo Cerca) | `SearchControl.SearchGlyph` |
| Primo piano (glifo Arresta) | `SearchControl.StopGlyph` |
| Primo piano (glifo Cancella) | `SearchControl.ClearGlyph` |
| Bordo | N/D |

**Pulsante di azione di ricerca con stato non attivo**  

![Pulsante di azione di ricerca con stato non attivo](../../extensibility/ux-guidelines/media/0303-115_searchactionbuttonunfocused.png "0303 115_SearchActionButtonUnfocused")<br />Pulsante di azione di ricerca con stato non attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | N/D |
| Primo piano (glifo Cerca) | `SearchControl.SearchGlyph` |
| Primo piano (glifo Arresta) | `SearchControl.StopGlyph` |
| Primo piano (glifo Cancella) | `SearchControl.ClearGlyph` |
| Bordo | N/D |

**Pulsante di azione di ricerca selezionato**

![Pulsante di azione di ricerca premuto](../../extensibility/ux-guidelines/media/0303-116-1_searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br />Pulsante di azione di ricerca selezionato

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `SearchControl.ActionButtonMouseDown` |
| Primo piano (glifo) | `SearchControl.ActionButtonMouseDownGlyph` |
| Bordo | `SearchControl.ActionButtonMouseDownBorder` |

**Pulsante di azione di ricerca disabilitato**

![Pulsante di azione di ricerca disabilitato](../../extensibility/ux-guidelines/media/0303-122_searchactionbuttondisabled.png "0303 122_SearchActionButtonDisabled")<br />Pulsante di azione di ricerca disabilitato

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | Nessuno |
| Primo piano (glifo) | `SearchControl.ActionButtonDisabledGlyph` |
| Bordo | Nessuno |

**Pulsante di menu a discesa di ricerca con stato attivo**

![Pulsante di menu a discesa di ricerca con stato attivo](../../extensibility/ux-guidelines/media/0303-113_searchdropdownbuttonfocused.png "0303 113_SearchDropdownButtonFocused")<br />Pulsante di menu a discesa di ricerca con stato attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `SearchControl.FocusedDropDownButton` |
| Primo piano (glifo) | `SearchControl.FocusedDropDownButtonGlyph` |
| Bordo | `SearchControl.FocusedDropDownButtonBorder` |

**Pulsante di menu a discesa di ricerca con stato non attivo**

![Pulsante di menu a discesa di ricerca con stato non attivo](../../extensibility/ux-guidelines/media/0303-116_searchdropdownbuttonunfocused.png "0303 116_SearchDropdownButtonUnfocused")<br />Pulsante di menu a discesa di ricerca con stato non attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `SearchControl.UnfocusedDropDownButton` |
| Primo piano (glifo) | `SearchControl.UnfocusedDropDownButtonGlyph` |
| Bordo | `SearchControl.UnfocusedDropDownButtonBorder` |

**Pulsante di menu a discesa di ricerca selezionato**

![Pulsante di menu a discesa di ricerca premuto](../../extensibility/ux-guidelines/media/0303-116-2_searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br />Pulsante di menu a discesa di ricerca selezionato

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `SearchControl.MouseDownDropDownButton` |
| Primo piano (glifo) | `SearchControl.MouseDownDropDownButtonGlyph` |
| Bordo | `SearchControl.MouseDownDropDownButtonBorder` |

**Pulsante di menu a discesa di ricerca disabilitato**

![Pulsante di menu a discesa di ricerca disabilitato](../../extensibility/ux-guidelines/media/0303-123_searchdropdownbuttondisabled.png "0303 123_SearchDropdownButtonDisabled")<br />Pulsante di menu a discesa di ricerca disabilitato

| Elemento | Nome token: Category.color |
| --- | --- |  
| Sfondo | Nessuno |
| Primo piano (glifo) | `SearchControl.DisabledDownButtonGlyph` |
| Bordo | Nessuno |

#### <a name="search-drop-down-lists"></a>Elenchi a discesa di ricerca  
Il menu di riepilogo a discesa di casella di ricerca è in grado di essere leggermente più complesso rispetto ad altri menu a discesa in Visual Studio. Le sezioni "Opzioni di ricerca" e il "ricerche suggerite" possono essere visualizzati singolarmente o insieme nel menu, e ciascuna di esse è colorata separatamente. Una linea separa le due sezioni quando sono visualizzate insieme e un bordo circonda l'intero menu a discesa.  

![Elenco di riepilogo a discesa di ricerca (con linea rossa)](../../extensibility/ux-guidelines/media/0303-124_searchdropdownredline.png "0303 124_SearchDropdownRedline")<br />Elenco di riepilogo a discesa di ricerca (con linea rossa)

| Usare... | Non usare... |
| --- | --- |
| ... quando si crea un elenco di riepilogo a discesa di ricerca personalizzato. | per elenchi a discesa visualizzati in altri contesti. |
| ... i nomi di token corretti per i componenti di elenco corretto. | ... in qualsiasi combinazione sfondo/primo piano diversa da quella specificata. |

**Elementi di elenco a discesa di ricerca**

| Elemento | Nome token: Category.color |
| --- | --- |
| Bordo | `SearchControl.PopupBorder` |
| Separatore | `SearchControl.PopupSectionHeaderSeparator` |
| Ombreggiatura | `Environment.DropShadowBackground` |

**Ricerche suggerite: stato predefinito**

![Predefinito ricerche suggerite](../../extensibility/ux-guidelines/media/0303-125_searchsuggested.png "0303 125_SearchSuggested")<br />Ricerche suggerite predefinito  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `SearchControl.PopupItemsListBackgroundGradientBegin`<br />(Sfumatura per questo token non utilizzato nell'interfaccia utente con temi) |
| Primo piano (testo) | `SearchControl.PopupItemText` |

**Ricerche suggerite: passare il puntatore dello stato**

![Suggeriti ricerche al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-128_searchsuggestedhover.png "0303 128_SearchSuggestedHover")<br />Ricerche suggerite al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Sfumatura per questo token non utilizzato nell'interfaccia utente con temi) |
| Primo piano (testo) | `SearchControl.PopupMouseOverItemText` |
| Bordo | `SearchControl.PopupControlMouseOverBorder` |

**Le opzioni di ricerca: stato predefinito**

![Casella di controllo di ricerca](../../extensibility/ux-guidelines/media/0303-126_searchcheckbox.png "0303 126_SearchCheckbox")<br />Opzioni di ricerca predefinite (casella di controllo)  

![Le opzioni di ricerca](../../extensibility/ux-guidelines/media/0303-127_searchoptions.png "0303 127_SearchOptions")<br />Opzioni di ricerca predefinite (collegamento)  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `SearchControl.PopupSectionBackgroundGradientBegin`<br />(Sfumatura per questo token non utilizzato nell'interfaccia utente con temi) |
| Primo piano (testo della casella di controllo) | `SearchControl.PopupCheckboxText` |
| Primo piano (testo del collegamento) | `SearchControl.PopupButtonText` |
| Sfondo dell'intestazione | `SearchControl.PopupSectionHeaderGradientBegin`<br />(Sfumatura per questo token non utilizzato nell'interfaccia utente con temi) |
| Primo piano (testo dell'intestazione) | `SearchControl.PopupSectionHeaderText` |

**Le opzioni di ricerca: passare il puntatore dello stato**

![Opzioni (finestra di controllo) di ricerca al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-129_searchcheckboxhover.png "0303 129_SearchCheckboxHover")<br />Opzioni di ricerca (casella di controllo) al passaggio del mouse  

![Opzioni (collegamento) di ricerca al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-130_searchoptionshover.png "0303 130_SearchOptionsHover")<br />Opzioni di ricerca (collegamento) al passaggio del mouse  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Sfumatura per questo token non utilizzato nell'interfaccia utente con temi) |
| Primo piano (testo della casella di controllo) | `SearchControl.PopupCheckboxMouseDownText` |
| Primo piano (testo del collegamento) | `SearchControl.PopupButtonMouseDownText` |
| Bordo | `SearchControl.PopupControlMouseOverBorder` |

**Le opzioni di ricerca: stati**  

![Opzioni di ricerca (casella di controllo) premuto](../../extensibility/ux-guidelines/media/0303-131_searchsuggestedpressed.png "0303 131_SearchSuggestedPressed")<br />Premuto opzioni di ricerca (casella di controllo)   

![Opzioni di ricerca (collegamento) premuto](../../extensibility/ux-guidelines/media/0303-132_searchoptionspressed.png "0303 132_SearchOptionsPressed")<br />Opzioni di ricerca (collegamento) premuto  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo della casella di controllo | `SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br />`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br />(Sfumatura per questo token non utilizzato nell'interfaccia utente con temi) |
| Primo piano (testo della casella di controllo) | `SearchControl.PopupCheckboxMouseDownText` |
| Sfondo del collegamento | `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br />(Sfumatura per questo token non utilizzato nell'interfaccia utente con temi) |
| Primo piano (testo del collegamento) | `SearchControl.PopupButtonMouseDownText` |

###  <a name="BKMK_TreeView"></a> Visualizzazioni dell'albero  
Diverse finestre, tra cui Esplora soluzioni, Esplora Server e visualizzazione classi, implementano uno schema organizzativo gerarchico i cui colori sono controllati dai nomi di colore nel `TreeView` categoria. Tutti gli elementi in una visualizzazione albero hanno colori di sfondo e del testo. Gli elementi che hanno elementi figlio annidati hanno anche glifi che indicano se ogni elemento è espanso o compresso.  

![Visualizzazione struttura ad albero (con linea rossa)](../../extensibility/ux-guidelines/media/0303-147_treeviewredline.png "0303 147_TreeViewRedline")<br />Visualizzazione struttura ad albero (con linea rossa)

| Usare... | Non usare... |
| --- | --- |
| ... in qualsiasi punto è necessario implementare una visualizzazione organizzativa gerarchica. | per qualsiasi elemento che non è simile a una visualizzazione albero. |
| | ... in qualsiasi combinazione sfondo/primo piano diversa da quella specificata. |

**Elemento della visualizzazione albero: stato predefinito**

![Elemento di visualizzazione della struttura predefinita](../../extensibility/ux-guidelines/media/0303-148_treeview.png "0303 148_TreeView")<br />Elemento della visualizzazione struttura predefinito

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `TreeView.Background` |
| Primo piano (testo) | `TreeView.Background` |
| Primo piano (glifo) | `TreeView.Glyph` |
| Bordo | Nessuno |

**Elemento della visualizzazione albero: passare il puntatore dello stato**

![Elemento della visualizzazione albero al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-149_treeviewhover.png "0303 149_TreeViewHover")<br />Elemento della visualizzazione albero al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `TreeView.Background` |  
| Primo piano (testo) | `TreeView.Background` |
| Primo piano (glifo) | `TreeView.GlyphMouseOver` |
| Bordo | Nessuno |

**Elemento della visualizzazione albero: trascinare sullo stato**

![Struttura ad albero elemento di visualizzazione sul trascinamento su](../../extensibility/ux-guidelines/media/0303-150_treeviewdragover.png "0303 150_TreeViewDragOver")<br />Elemento in visualizzazione della struttura trascinare su  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `TreeView.DragOverItem` |
| Primo piano (testo) | `TreeView.DragOverItem` |
| Primo piano (glifo) | `TreeView.DragOverItemGlyph` |
| Bordo | Nessuno |

**Elemento della visualizzazione albero: selezionata, con stato attivo dello stato**

![Selezionato e con stato attivo di elemento di visualizzazione della struttura](../../extensibility/ux-guidelines/media/0303-151_treeviewfocused.png "0303 151_TreeViewFocused")<br />Elemento della visualizzazione albero con stato attivo e selezionato

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `TreeView.SelectedItemActive` |
| Primo piano (testo) | `TreeView.SelectedItemActive` |
| Primo piano (glifo) | `TreeView.SelectedItemActiveGlyph` |
| Bordo | `TreeView.FocusVisualBorder` |

**Elemento della visualizzazione albero: stato selezionato, con stato non attivo**  

![Elemento della visualizzazione albero con stato non attivo e selezionato](../../extensibility/ux-guidelines/media/0303-152_treeviewunfocused.png "0303 152_TreeViewUnfocused")<br />Elemento della visualizzazione albero con stato non attivo e selezionato

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `TreeView.SelectedItemInactive` |
| Primo piano (testo) | `TreeView.SelectedItemInactive` |
| Primo piano (glifo) | `TreeView.SelectedItemInactiveGlyph` |
| Bordo | Nessuno |

**Elemento della visualizzazione albero: al passaggio del mouse, selezionato e con stato attivo dello stato**

![Selezionato e con stato attivo di elemento di visualizzazione dell'albero al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-153_treeviewfocusedhover.png "0303 153_TreeViewFocusedHover")<br />Elemento della visualizzazione albero con stato attivo e selezionato al passaggio del mouse  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `TreeView.SelectedItemActive` |
| Primo piano (testo) | `TreeView.SelectedItemActive` |
| Primo piano (glifo) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Bordo | `TreeView.FocusVisualBorder` |

**Elemento della visualizzazione albero: lo stato al passaggio del mouse, selezionato e con stato non attivo**

![Elemento della visualizzazione albero con stato non attivo e selezionato al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-154_treeviewunfocusedhover.png "0303 154_TreeViewUnfocusedHover")<br />Elemento della visualizzazione albero con stato non attivo e selezionato al passaggio del mouse  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `TreeView.SelectedItemInactive` |
| Primo piano (testo) | `TreeView.SelectedItemInactive` |
| Primo piano (glifo) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Bordo | Nessuno |

## <a name="shell-appearance"></a>Aspetto della shell

### <a name="background"></a>Sfondo  
Lo sfondo dell'ambiente è costituito da due livelli. Il livello inferiore è un colore a tinta unita che ricopre l'intero IDE. Il livello superiore si trova sotto lo scaffale dei comandi tra i canali Nascondi automaticamente della finestra degli strumenti, nei bordi destro e sinistro dell'IDE. I livelli di sfondo superiore e inferiore vengono impostati sullo stesso colore nei temi chiaro e scuro.  

![In background di Visual Studio shell (con linea rossa)](../../extensibility/ux-guidelines/media/0303-187_shellbackgroundredline.png "0303 187_ShellBackgroundRedline")<br />In background di Visual Studio shell (con linea rossa)

| Usare... | Non usare... |
| --- | --- |
| ... per le posizioni in cui si desidera corrispondere allo sfondo dell'ambiente di Visual Studio. | ... come riempimento per i punti che non sono superfici di sfondo. |
| | ... come sfondo per inserire elementi in primo piano in. |

**Aspetto della shell di basso livello**

| Elemento | Nome token: Category.color |
| --- | --- |  
| Sfondo | `Environment.EnvironmentBackground` |

**Aspetto della shell di livello superiore**

> Cursori sfumatura impostati sullo stesso valore di colore dei temi Chiaro e Scuro di Visual Studio 2013.

| Elemento | Nome token: Category.color |
| --- | --- |  
| Sfondo | `Environment.EnvironmentBackgroundGradientBegin`<br />`Environment.EnvironmentBackgroundGradientEnd`<br />`Environment.EnvironmentBackgroundGradientMiddle1`<br />`Environment.EnvironmentBackgroundGradientMiddle2` |  

### <a name="command-shelf"></a>Scaffale dei comandi  
Due set di nomi di token vengono usati per gli sfondi dello scaffale dei comandi, uno per il punto in cui si trova la barra dei menu e l'altro per il punto in cui si trova la barra dei comandi. Un singolo gruppo della barra dei comandi ha valori di colore di sfondo propri, che vengono descritti in modo più dettagliato nella sezione "Barra dei comandi". Il testo della barra dei menu e della barra dei comandi viene descritto nelle rispettive sezioni.  

![Scaffale dei comandi di Visual Studio (con linea rossa)](../../extensibility/ux-guidelines/media/0303-188_commandshelfredline.png "0303 188_CommandShelfRedline")<br />Scaffale dei comandi di Visual Studio (con linea rossa)  

| Usare... | Non usare... |
| --- | --- |
| ... per le aree in cui si posizionano menu o barre degli strumenti. | ... per le aree che non sono simili a uno scaffale dei comandi. |
|... con la combinazione di nome del token corretto sfondo/primo piano. | |

**Sulla barra dei menu scaffale dei comandi**

> Cursori sfumatura impostati sullo stesso valore di colore dei temi Chiaro e Scuro di Visual Studio 2013.

| Elemento | Nome token: Category.color |
| --- | --- |  
| Sfondo | `Environment.CommandShelfHighlightGradientBegin`<br /><br />`Environment.CommandShelfHighlightGradientMiddle`<br />`Environment.CommandShelfHighlightGradientEnd` |

* * Comando scaffale dei comandi della barra * *

> Cursori sfumatura impostati sullo stesso valore di colore dei temi Chiaro e Scuro di Visual Studio 2013.

| Elemento | Nome token: Category.color |
| --- | --- |  
| Sfondo | `Environment.CommandShelfBackgroundGradientBegin`<br />`Environment.CommandShelfBackgroundGradientMiddle`<br />`Environment.CommandShelfBackgroundGradientEnd` |

## <a name="manifest-designer"></a>Finestra Progettazione manifesto  
La finestra Progettazione manifesto è stata progettata come strumento per semplificare la modifica del file manifesto in progetti Windows 8 e Windows Phone 8. Benché non sia disponibile per l'utilizzo alcun framework condiviso, potrebbe essere appropriato fare in modo che il layout di progettazione e i colori delle schede di orientamento/spostamento corrispondano alla struttura complessiva. Per ulteriori informazioni sui dettagli del layout, vedere [Layout per Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).  

![Progettazione manifesto (con linea rossa)](../../extensibility/ux-guidelines/media/0303-175_manifestdesignerredline.png "0303 175_ManifestDesignerRedline")<br />Progettazione manifesto (con linea rossa)

| Usare... | Non usare... |
| --- | --- |
| ... per le finestre di progettazione simile alla finestra Progettazione manifesto. | ... Se si dispone di più di sei schede. |
| invece di usare controlli scheda comuni nella parte superiore di un editor all'interno del documento nonché.... | per qualsiasi interfaccia utente... che non è strutturata come la finestra Progettazione manifesto. |

**Scheda selezionata progettazione manifesto: stato predefinito**

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `ManifestDesigner.TabActive` |
| Bordo | Nessuno |

**Riquadro di descrizione selezionato progettazione manifesto: stato predefinito**

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `ManifestDesigner.DescriptionPane` |

**Pagina contenuto selezionato progettazione manifesto: stato predefinito**

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `ManifestDesigner.Background` |
| Testo di supporto della finestra di dialogo | `ManifestDesigner.WatermarkText`<br />(Questo nome di token non corrisponde alla sua funzione). |

**Scheda Progettazione manifesto: stato deselezionato**

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `ManifestDesigner.Tab.Inactive` |

**Scheda Progettazione manifesto: passare il puntatore dello stato**

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `ManifestDesigner.Tab.Mouseover` |

## <a name="command-structures"></a>Strutture dei comandi  

###  <a name="BKMK_CommandMenus"></a> Menu  
I menu possono trovarsi in diverse posizioni all'interno di Visual Studio: barra dei menu principale, incorporata in documenti o degli strumenti di windows, o sul pulsante destro del mouse in diverse posizioni dell'IDE. Le implementazioni dei menu associati ad altri elementi dell'interfaccia utente vengono descritte nella sezione relativa al rispettivo elemento. È preferibile usare sempre l'implementazione dei menu standard fornita dall'ambiente di Visual Studio. Tuttavia, in alcuni casi rari si potrebbe non avere accesso ai menu standard di Visual Studio. In questi casi, usare i nomi di token seguenti per garantire che l'interfaccia utente sia coerente con gli altri menu in Visual Studio.  

![Menu di Visual Studio (con linea rossa)](../../extensibility/ux-guidelines/media/0303-000_menuredline.png "0303 000_MenuRedline")<br />Menu di Visual Studio (con linea rossa)

| Usare... | Non usare... |
| --- | --- |
| ... quando è necessario creare un menu personalizzato.| ... il colore di sfondo da solo. Usare sempre la combinazione sfondo/primo piano specificata. |
| ... quando si dispone di un nuovo componente dell'interfaccia utente che si desidera trovare una corrispondenza i menu di Visual Studio.| |

#### <a name="menu-titles"></a>Titoli di menu  
I titoli dei menu sono costituiti da uno sfondo, un bordo e il testo del titolo, nonché da un glifo facoltativo, in genere quando il menu si trova in una barra dei comandi.  

![Titolo menu (con linea rossa)](../../extensibility/ux-guidelines/media/0303-001_menutitleredline.png "0303 001_MenuTitleRedline")<br />Titolo del menu (con linea rossa)  

| Usare... | Non usare... |
| --- | --- |
| ... ogni volta che si sta creando un titolo di menu personalizzato. | per qualsiasi elemento che non si desidera sempre corrispondere il titolo del menu. |
| | ... in qualsiasi combinazione sfondo/primo piano diversa da quella specificata. |

**Titolo menu: stato predefinito**

![Titolo menu predefinito](../../extensibility/ux-guidelines/media/0303-002_menutitledefault.png "0303 002_MenuTitleDefault")<br />Titolo menu predefinito

![Titolo menu con glifo predefinito](../../extensibility/ux-guidelines/media/0303-003_menutitlewithglyphdefault.png "0303 003_MenuTitleWithGlyphDefault")<br />Titolo menu con glifo

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | Nessuno |
| In primo piano (testo) | `Environment.CommandBarTextActive` |
| In primo piano (glifo) | `Environment.CommandBarMenuGlyph` |
| Bordo | Nessuno |

**Titolo menu: passare il puntatore dello stato**  

![Titolo menu al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-004_menutitlehover.png "0303 004_MenuTitleHover")<br />Titolo menu al passaggio del mouse  

![Titolo menu con glifo al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-005_menutitlewithglyphhover.png "0303 005_MenuTitleWithGlyphHover")<br />Titolo menu con glifo al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Sfumatura per questo token non utilizzato nell'interfaccia utente con temi) |
| In primo piano (testo) | `Environment.CommandBarTextHover` |
| In primo piano (glifo) | `Environment.CommandBarMenuMouseOverGlyph` |  
| Bordo | `Environment.CommandBarBorder` |

**Titolo menu: stati**  

![Titolo menu premuto](../../extensibility/ux-guidelines/media/0303-006_menutitlepressed.png "0303 006_MenuTitlePressed")<br />Titolo menu selezionato

![Titolo menu con glifo premuto](../../extensibility/ux-guidelines/media/0303-007_menutitlewithglyphpressed.png "0303 007_MenuTitleWithGlyphPressed")<br />Titolo menu con glifo premuto

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.CommandBarMenuBackgroundGradientBegin`<br/>(Sfumatura per questo token non utilizzato nell'interfaccia utente con temi) |
| Primo piano (testo) | `Environment.CommandBarTextActive` |
| Primo piano (glifo) | `Environment.CommandBarMenuMouseDownGlyph` |
| Bordo | `Environment.CommandBarMenuBorder`<br />(Solo sinistro, superiore e destro.) |  

**Titolo menu: stato disabilitato**  

![Titolo menu con glifo disabilitato](../../extensibility/ux-guidelines/media/0303-008_menutitlewithglyphdisabled.png "0303 008_MenuTitleWithGlyphDisabled")<br />Titolo menu disabilitato con glifo

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | Nessuno |
| Primo piano (testo) | `Environment.CommandBarTextInactive` |
| Primo piano (glifo) | `Environment.CommandBarTextInactive` |
| Bordo | Nessuno |

#### <a name="menu-items"></a>Voci di menu
Una singola voce di menu è costituita dal testo del menu e da un'icona facoltativa, una casella di controllo o un glifo del sottomenu. Il colore di sfondo e del testo cambiano al passaggio del mouse. Questo token di colore è una coppia sfondo/primo piano.  

![Voci di menu con linea rossa](../../extensibility/ux-guidelines/media/0303-009_menuitemredline.png "0303 009_MenuItemRedline")  

| Usare... | Non usare...  |
|---|---|
| ... per qualsiasi elenco a discesa che viene avviata da una barra dei menu o una barra dei comandi. | ... per qualsiasi elenco a discesa in un altro contesto. |
| | ... in qualsiasi combinazione sfondo/primo piano diversa da quella specificata. |

**Voci di menu: stato predefinito**

![Voci di menu predefinito](../../extensibility/ux-guidelines/media/0303-010_menudefault.png "0303 010_MenuDefault")<br />Voci di menu predefinito  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.CommandBarMenuBackgroundGradientBegin`<br />(Sfumatura per questo token non utilizzato nell'interfaccia utente con temi) |
| Primo piano (testo) | `Environment.CommandBarTextActive` |
| Primo piano (glifo del sottomenu) | `Environment.CommandBarMenuSubmenuGlyph` |
| Bordo | `Environment.CommandBarMenuBorder` |
| Sfondo del canale delle icone | `Environment.CommandBarMenuIconBackground` |
| Separatore | `Environment.CommandBarMenuSeparator` |
| Ombreggiatura | `Environment.DropShadowBackground` |

**Voci di menu: scelto e selezionato gli Stati**  

![Menu scelto](../../extensibility/ux-guidelines/media/0303-011_menuchecked.png "0303 011_MenuChecked")<br />Voce di menu selezionata

![Menu selezionato](../../extensibility/ux-guidelines/media/0303-012_menuselected.png "0303 012_MenuSelected")<br />Voce di menu selezionata    

| Elemento | Nome token: Category.color |
| --- | --- |
| Segno di spunta | `Environment.CommandBarCheckBox` |  
| Sfondo del segno di spunta | `Environment.CommandBarSelectedIcon` |  
| Sfondo dell'icona | `Environment.CommandBarSelected` |
| Bordo dell'icona | `Environment.CommandBarSelectedBorder` |

**Voci di menu: passare il puntatore dello stato**  

![Passaggio del mouse dal menu](../../extensibility/ux-guidelines/media/0303-013_menuhover.png "0303 013_MenuHover")<br />Voce di menu al passaggio del mouse

![Passaggio di menu selezionata](../../extensibility/ux-guidelines/media/0303-014_menuhoverchecked.png "0303 014_MenuHoverChecked")<br />Selezionata la voce di menu al passaggio del mouse

![Passaggio del mouse dal menu selezionato](../../extensibility/ux-guidelines/media/0303-015_menuhoverselected.png "0303 015_MenuHoverSelected")<br />Voce di menu selezionata al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.CommandBarMenuItemMouseOver` |
| Primo piano (testo) | `Environment.CommandBarMenuItemMouseOver` |
| Primo piano (glifo del sottomenu) | `Environment.CommandBarMenuMouseOverSubmenuGlyph` |
| Segno di spunta | `Environment.CommandBarCheckBoxMouseOver` |
| Sfondo del segno di spunta | `Environment.CommandBarHoverOverSelectedIcon` |
| Sfondo dell'icona | `Environment.CommandBarHoverOverSelected` |
| Bordo dell'icona | `Environment.CommandBarHoverOverSelectedIconBorder` |

**Voci di menu: stato disabilitato**  

![Menu disabilitato](../../extensibility/ux-guidelines/media/0303-016_menudisabled.png "0303 016_MenuDisabled")<br />Voce di menu disabilitata

![Menu disabilitato selezionato](../../extensibility/ux-guidelines/media/0303-017_menudisabledchecked.png "0303 017_MenuDisabledChecked")<br />Voce di menu disabilitata con segno di spunta

| Elemento | Nome token: Category.color |
| --- | --- |
| Primo piano (testo) | `Environment.CommandBarTextInactive` |
| Primo piano (glifo del sottomenu) | `Environment.CommandBarMenuSubmenuGlyph` |
| Segno di spunta | `Environment.CommandBarCheckBoxDisabled` |
| Sfondo del segno di spunta | `Environment.CommandBarSelectedIconDisabled` |

### <a name="command-bars"></a>Barre dei comandi  
Una barra dei comandi può apparire in più posizioni all'interno dell'IDE di Visual Studio, in particolare la scaffale dei comandi e strumento incorporato in o le finestre di documento.  

In generale, usare sempre l'implementazione della barra dei menu standard fornita dall'ambiente di Visual Studio. L'uso del meccanismo standard garantisce che tutti i dettagli visivi vengano visualizzati correttamente e che gli elementi interattivi abbiano un comportamento coerente con gli altri controlli della barra dei comandi di Visual Studio. Tuttavia, se è necessario compilare una barra dei comandi personalizzata, assicurarsi di applicare lo stile corretto usando i nomi di token seguenti.  

![Sulla barra dei comandi con linea rossa](../../extensibility/ux-guidelines/media/0303-018_commandbarredline.png "0303 018_CommandBarRedline")<br />Barra dei comandi (con linea rossa)  

![Pulsante di overflow con linea rossa](../../extensibility/ux-guidelines/media/0303-019_overflowbuttonredline.png "0303 019_OverflowButtonRedline")<br />Pulsante di overflow (con linea rossa)  

| Usare... | Non usare... |
| --- | --- |
| ... nei luoghi in cui è necessario una barra dei comandi incorporata, ma non è possibile utilizzare l'implementazione di barra dei comandi standard di Visual Studio. | ... per gli elementi dell'interfaccia utente che non sono simili a una barra dei comandi. |
| | ... per i componenti della barra dei comandi diversi da quelli per cui vengono specificati i nomi di token. |

#### <a name="command-bar-groups"></a>Gruppi di barra dei comandi  
Un gruppo della barra dei comandi è costituito da un set correlato di controlli della barra dei comandi e può contenere un numero qualsiasi di pulsanti, pulsanti di menu combinato, menu a discesa, caselle combinate o menu. I colori per questi controlli sono determinati da nomi di token separati e vengono descritti singolarmente in altre sezioni di questa guida. Viene usata una linea di separazione per dividere un gruppo della barra dei comandi in sottogruppi correlati.  

![Gruppo della barra dei comandi con linea rossa](../../extensibility/ux-guidelines/media/0303-020_commandbargroupredline.png "0303 020_CommandBarGroupRedline")<br />Gruppo barra dei comandi (con linea rossa)

| Usare... | Non usare... |
| --- | --- |  
| ... nei luoghi in cui è necessario una barra dei comandi incorporata, ma non è possibile utilizzare l'implementazione di barra dei comandi standard di Visual Studio. | ... per gli elementi dell'interfaccia utente che non sono simili a una barra dei comandi. |
| | ... per i componenti della barra dei comandi diversi da quelli per cui vengono specificati i nomi di token. |

**Gruppo della barra dei comandi: stato predefinito**  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.CommandBarGradientBegin`<br />(Sfumatura per questo token non utilizzato nell'interfaccia utente con temi) |
| Bordo | `Environment.CommandBarToolBarBorder` |
| Quadratino di trascinamento | `Environment.CommandBarDragHandle` |
| Separatore | `Environment.CommandBarToolBarSeparator`<br />`Environment.CommandBarToolBarSeparatorHighlight` |

#### <a name="command-icons"></a>Icone dei comandi  
![Icona del comando con linea rossa](../../extensibility/ux-guidelines/media/0303-021_commandiconredline1.png "0303 021_CommandIconRedline1")<br />Icona del comando (con linea rossa)  

![Icona del comando con il testo con linea rossa](../../extensibility/ux-guidelines/media/0303-022_commandiconredline2.png "0303 022_CommandIconRedline2")<br />Icona del comando con il testo (con linea rossa)  

| Usare... | Non usare... |
| --- | --- |
| ... per i pulsanti che verrà inserito in una barra dei comandi. | ... per i controlli che hanno i propri nomi di token. |
| | ... in qualsiasi combinazione sfondo/primo piano diversa da quella specificata. |

**Icona del comando: stato predefinito**  

![Comando icona predefinita](../../extensibility/ux-guidelines/media/0303-023_commandicondefault.png "0303 023_CommandIconDefault")<br />Icona del comando predefinita

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | N/D (eredita dallo sfondo della barra dei comandi) |
| Primo piano (testo) | `Environment.CommandBarTextActive` |
| Bordo | N/D |

**Icona del comando: stato, selezionato predefinito**

![Impostazione predefinita, l'icona del comando selezionato](../../extensibility/ux-guidelines/media/0303-024_commandicondefaultselected.png "0303 024_CommandIconDefaultSelected")<br />Impostazione predefinita, l'icona del comando selezionato  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.CommandBarSelected` |
| Primo piano (testo) | `Environment.CommandBarTextSelected` |
| Bordo | `Environment.CommandBarSelectedBorder` |

**Icona del comando: stati al passaggio del mouse o lo stato attivo**  

![Icona del comando al passaggio del mouse o all'elemento attivo](../../extensibility/ux-guidelines/media/0303-025_commandiconhover.png "0303 025_CommandIconHover")<br />Icona del comando al passaggio del mouse o lo stato attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Sfumatura per questo token non utilizzato nell'interfaccia utente con temi) |
| Primo piano (testo) | `Environment.CommandBarTextHover` |
| Bordo | `Environment.CommandBarBorder` |

**Icona del comando: stati al passaggio del mouse o lo stato attivo, selezionati**

![Icona del comando al passaggio del mouse o all'elemento attivo selezionato](../../extensibility/ux-guidelines/media/0303-026_commandiconhoverselected.png "0303 026_CommandIconHoverSelected")<br />Icona del comando selezionata al passaggio del mouse o lo stato attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.CommandBarHoverOverSelected` |
| Primo piano (testo) | `Environment.CommandBarTextHoverOverSelected` |
| Bordo | `Environment.CommandBarHoverOverSelectedIconBorder` |

 **Icona del comando: stati**  

![Icona del comando premuto](../../extensibility/ux-guidelines/media/0303-027_commandiconpressed.png "0303 027_CommandIconPressed")<br />Icona del comando premuta

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Sfumatura per questo token non utilizzato nell'interfaccia utente con temi) |
| Primo piano (testo) | `Environment.CommandBarTextMouseDown` |
| Bordo | `Environment.CommandBarBorder` |

**Icona del comando: stato disabilitato**  

![Icona del comando disabilitata](../../extensibility/ux-guidelines/media/0303-028_commandicondisabled.png "0303 028_CommandIconDisabled")<br />Icona del comando disabilitata

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | N/D (eredita dallo sfondo della barra dei comandi) |
| Primo piano (testo) | `Environment.CommandBarTextInactive` |
| Bordo | N/D |

####  <a name="BKMK_CommandComboBox"></a> Caselle combinate della barra di comando

> [!IMPORTANT]
> Le caselle combinate sono simili agli elenchi a discesa, ma includono un'area di testo modificabile. Se l'elenco a discesa non include un'area di testo modificabile, usare i token di colore per [barra a discesa dei comandi](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown).  

![Comando della barra di casella combinata con linea rossa](../../extensibility/ux-guidelines/media/0303-029_comboboxredline.png "0303 029_ComboBoxRedline")<br />Casella combinata della barra di comando (con linea rossa)  

| Usare... | Non usare... |
| --- | --- |
| ... quando si compilano caselle combinate personalizzate. | ... per tutti gli elementi non si desidera sempre corrispondere il comando interfaccia utente della barra. |
| ... durante la creazione di un controllo barra dei comandi che è simile a una casella combinata. | ... quando si ha accesso a una casella combinata con stile. |

**Campo input casella combinata barra dei comandi: stato predefinito**

![Comando barra finestra campo di input combinata](../../extensibility/ux-guidelines/media/0303-030_comboboxinputfield.png "0303 030_ComboBoxInputField")<br />Campo input casella combinata barra dei comandi  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ComboBoxBackground` |
| Primo piano (testo) | `Environment.ComboBoxText` |
| Bordo | `Environment.ComboBoxBorder` |
| Separatore | Nessun separatore |

**Pulsante di menu a discesa della barra dei comandi: stato predefinito**  

![Rilascio di casella combinata&#45;verso il basso sul pulsante](../../extensibility/ux-guidelines/media/0303-031_comboboxdropdownbutton.png "0303 031_ComboBoxDropdownButton")<br />Pulsante di comando della barra dei menu a discesa

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | N/D (eredita dallo sfondo della barra dei comandi) |
| Primo piano (glifo) | `Environment.ComboBoxGlyph` |

**Elenco elenco a discesa sulla barra dei comandi: stato predefinito**

![Elenco di comandi barra dei menu a discesa](../../extensibility/ux-guidelines/media/0303-032_comboboxdropdownlist.png "0303 032_ComboBoxDropdownList")<br />Elenco elenco a discesa sulla barra dei comandi

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ComboBoxPopupBackgroundBegin`<br />(Sfumatura per questo token non utilizzato nell'interfaccia utente con temi) |
| Primo piano (testo) | `Environment.ComboBoxItemText` |
| Bordo | `Environment.ComboBoxPopupBorder` |

**Comando barra finestra campo di input combinata: passare il puntatore dello stato**  

![Comando barra input campo della casella combinata al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-033_comboboxinputfieldhover.png "0303 033_ComboBoxInputFieldHover")<br />Comando barra input campo della casella combinata al passaggio del mouse  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ComboBoxMouseOverBackgroundBegin`<br />(Sfumatura per questo token non utilizzato nell'interfaccia utente con temi) |
| Primo piano (testo) | `Environment.ComboBoxMouseOverText` |
| Bordo | `Environment.ComboBoxMouseOverBorder` |
| Separatore | `Environment.ComboBoxMouseOverSeparator` |

 **Pulsante di menu a discesa della barra dei comandi: passare il puntatore dello stato**  

![Pulsante di comando della barra dei menu a discesa al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-034_comboboxdropdownbuttonhover.png "0303 034_ComboBoxDropdownButtonHover")<br />Pulsante di comando della barra dei menu a discesa al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ComboBoxButtonMouseOverBackground` |
| Primo piano (glifo) | `Environment.ComboBoxMouseOverGlyph` |

**Elenco elenco a discesa sulla barra dei comandi: passare il puntatore dello stato**

 ![Elenco di comandi barra dei menu a discesa al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-035_comboboxdropdownlisthover.png "0303 035_ComboBoxDropdownListHover")<br />Elenco di comandi barra dei menu a discesa al passaggio del mouse  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo (voce di menu) | `Environment.ComboBoxItemMouseOverBackground` |
| Primo piano (testo) | `Environment.ComboBoxItemMouseOverText` |
| Bordo (voce di menu) | `Environment.ComboBoxItemMouseOverBorder` |

 **Comando barra finestra campo di input combinata: con stato attivo dello stato**  

![Con stato attivo sulla barra dei campo input della casella combinata comandi](../../extensibility/ux-guidelines/media/0303-036_comboboxinputfieldfocused.png "0303 036_ComboBoxInputFieldFocused")<br />Con stato attivo campo input casella combinata barra dei comandi

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ComboBoxFocusedBackground` |
| Primo piano (testo) | `Environment.ComboBoxFocusedText` |
| Bordo | `Environment.ComboBoxFocusedBorder` |
| Separatore | `Environment.ComboBoxFocusedButtonSeparator` |

**Pulsante di menu a discesa della barra dei comandi: con stato attivo dello stato**  

![Con stato attivo sulla barra dei menu a discesa sul pulsante comandi](../../extensibility/ux-guidelines/media/0303-037_comboboxdropdownbuttonfocused.png "0303 037_ComboBoxDropdownButtonFocused")<br />Barra pulsante a discesa dei comandi con lo stato attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ComboBoxFocusedButtonBackground` |
| Primo piano (glifo) | `Environment.ComboBoxFocusedGlyph` |

 **Comando barra finestra campo di input combinata: stati**  

![Premuto Comando barra campo input della casella combinata](../../extensibility/ux-guidelines/media/0303-038_comboboxinputfieldpressed.png "0303 038_ComboBoxInputFieldPressed")<br />Premuto campo input casella combinata barra dei comandi

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ComboBoxMouseDownBackground` |
| Primo piano (testo) | `Environment.ComboBoxMouseDownText` |
| Bordo | `Environment.ComboBoxMouseDownBorder` |
| Separatore | `Environment.ComboBoxMouseDownSeparator` |

**Pulsante di menu a discesa della barra dei comandi: stati**

![Sulla barra dei menu a discesa sul pulsante comandi premuto](../../extensibility/ux-guidelines/media/0303-039_comboboxdropdownbuttonpressed.png "0303 039_ComboBoxDropdownButtonPressed")<br />Premuto barra pulsante a discesa dei comandi  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ComboBoxButtonMouseDownBackground` |
| Primo piano (glifo) | `Environment.ComboBoxMouseDownGlyph` |

**Campo input casella combinata barra dei comandi: stato disabilitato**  

![Comando barra campo input della casella combinata disabilitato](../../extensibility/ux-guidelines/media/0303-041_comboboxinputfielddisabled.png "0303 041_ComboBoxInputFieldDisabled")<br />Comando disattivato il campo di input casella combinata della barra  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ComboBoxDisabledBackground` |
| Primo piano (testo) | `Environment.ComboBoxDisabledText` |
| Bordo | `Environment.ComboBoxDisabledBorder` |
| Separatore | Nessun separatore |

**Pulsante di menu a discesa della barra dei comandi: stato disabilitato**  

![Sulla barra dei menu a discesa sul pulsante comandi disabilitata](../../extensibility/ux-guidelines/media/0303-040_comboboxdropdownbuttondisabled.png "0303 040_ComboBoxDropdownButtonDisabled")<br />Comando disattivato il pulsante di menu a discesa della barra

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | Nessuno |
| Primo piano (glifo) | `Environment.ComboBoxDisabledGlyph` |

####  <a name="BKMK_CommandDropDown"></a> Elenchi a discesa barra dei comandi

> [!IMPORTANT]
>  Gli elenchi a discesa sono simili alle caselle combinate, ma non contengono aree di testo modificabili. Se l'elenco a discesa include un'area di testo modificabile, usare i token di colore per [comando caselle combinate della barra](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox).  

![Nella barra dei menu a discesa (con linea rossa)](../../extensibility/ux-guidelines/media/0303-042_dropdownredline.png "0303 042_DropdownRedline")<br />Nella barra dei menu a discesa (con linea rossa)

| Usare... | Non usare... |
| --- | --- |
| ... quando si creano controlli elenco a discesa personalizzati. | per qualsiasi elemento che non è simile a un elenco a discesa. |
| | ... per le caselle combinate o pulsanti di menu combinato. |   

**Campo di selezione elenco a discesa sulla barra di comando: stato predefinito**  

![Predefinito comando della barra di campo di selezione a discesa](../../extensibility/ux-guidelines/media/0303-043_dropdownselectionfield.png "0303 043_DropdownSelectionField")<br />Campo selezione elenco a discesa sulla barra di comando predefinito  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.DropDownBackground` |
| Primo piano (testo) | `DropDownText` |
| Bordo | `DropDownBorder` |
| Separatore | Nessun separatore |

**Pulsante di menu a discesa della barra dei comandi: stato predefinito**

![Sulla barra dei menu a discesa sul pulsante comandi predefinito](../../extensibility/ux-guidelines/media/0303-044_dropdownbutton.png "0303 044_DropdownButton")<br />Elenco a discesa pulsante predefinito  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | Nessuno |
| Primo piano (glifo) | `Environment.DropDownGlyph` |

**Elenco elenco a discesa sulla barra dei comandi: stato predefinito**

![Sulla barra dei menu a discesa elenco comandi predefinito](../../extensibility/ux-guidelines/media/0303-045_dropdownlist.png "0303 045_DropdownList")<br />Elenco elenco a discesa sulla barra dei comandi predefiniti  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.DropDownPopupBackgroundBegin`<br />(Sfumatura per questo token non utilizzato nell'interfaccia utente con temi) |
| Primo piano (testo) | `Environment.ComboBoxItemText` |
| Bordo | `Environment.DropDownPopupBorder` |
| Ombreggiatura | `Environment.DropShadowBackground` |

**Campo di selezione elenco a discesa sulla barra di comando: passare il puntatore dello stato**  

![Campo di selezione a discesa sulla barra comando al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-046_dropdownselectionfieldhover.png "0303 046_DropdownSelectionFieldHover")<br />Campo di selezione elenco a discesa sulla barra di comando al passaggio del mouse  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.DropDownMouseOverBackgroundBegin`<br />(Sfumatura per questo token non utilizzato nell'interfaccia utente con temi) |
| Primo piano (testo) | `Environment.DropDownMouseOverText` |
| Bordo | `Environment.DropDownMouseOverBorder` |
| Separatore | `Environment.DropDownButtonMouseOverSeparator` |

**Pulsante di menu a discesa della barra dei comandi: passare il puntatore dello stato**  

![Pulsante di comando della barra dei menu a discesa al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-047_dropdownbuttonhover.png "0303 047_DropdownButtonHover")<br />Pulsante di comando della barra dei menu a discesa al passaggio del mouse  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.DropDownButtonMouseOverBackground` |
| Primo piano (glifo) | `Environment.DropDownMouseOverGlyph` |

**Elenco elenco a discesa sulla barra dei comandi: passare il puntatore dello stato**  

![Elenco di comandi barra dei menu a discesa al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-048_dropdownlisthover.png "0303 048_DropdownListHover")<br />Elenco di comandi barra dei menu a discesa al passaggio del mouse  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo (voce di menu) | `Environment.ComboBoxItemMouseOverBackground` |
| Primo piano (testo) | `Environment.ComboBoxItemMouseOverText` |
| Bordo (voce di menu) | `Environment.ComboBoxItemMouseOverBorder` |

 **Campo di selezione elenco a discesa sulla barra di comando: stati**  

![Eliminare&#45;verso il basso il campo di selezione premuto](../../extensibility/ux-guidelines/media/0303-049_dropdownselectionfieldpressed.png "0303 049_DropdownSelectionFieldPressed")<br />Premuto comando della barra di campo di selezione a discesa

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.DropDownMouseDownBackground` |
| Primo piano (testo) | `Environment.DropDownMouseDownText` |
| Bordo | `Environment.DropDownMouseDownBorder` |
| Separatore | `Environment.DropDownButtonMouseDownSeparator` |

**Pulsante di menu a discesa della barra dei comandi: stati**

![Sulla barra dei menu a discesa sul pulsante comandi premuto](../../extensibility/ux-guidelines/media/0303-050_dropdownbuttonpressed.png "0303 050_DropdownButtonPressed")<br />Premuto barra pulsante a discesa dei comandi  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.DropDownButtonMouseDownBackground` |
| Primo piano (glifo) | `Environment.DropDownMouseDownGlyph` |

**Campo di selezione elenco a discesa sulla barra di comando: stato disabilitato**  

![Comando della barra di campo di selezione a discesa disabilitato](../../extensibility/ux-guidelines/media/0303-051_dropdownselectionfielddisabled.png "0303 051_DropdownSelectionFieldDisabled")<br />Comando disabilitato barra campo di selezione a discesa

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.DropDownDisabledBackground` |
| Primo piano (testo) | `Environment.DropDownDisabledText` |
| Bordo | `Environment.DropDownDisabledBorder` |
| Separatore | Nessun separatore |

**Pulsante di menu a discesa della barra dei comandi: stato disabilitato**

![Sulla barra dei menu a discesa sul pulsante comandi disabilitata](../../extensibility/ux-guidelines/media/0303-052_dropdownbuttondisabled.png "0303 052_DropdownButtonDisabled")<br />Comando disattivato il pulsante di menu a discesa della barra

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | N/D |
| Primo piano (glifo) | `Environment.DropDownDisabledGlyph` |

#### <a name="command-bar-split-buttons"></a>Barra dei comandi di pulsanti di menu combinato
I pulsanti di menu combinato condividono molti nomi di token con altri controlli della barra dei comandi, come pulsanti, menu e testo della barra dei comandi. Tutti i nomi di token dei pulsanti a discesa e di azione necessari vengono ripetuti qui per praticità. Gli elenchi di riepilogo a discesa pulsante di menu combinato sono implementazioni di [barra menu dei comandi](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus).  

![Pulsante di menu combinato con linea rossa](../../extensibility/ux-guidelines/media/0303-053_splitbuttonredline.png "0303 053_SplitButtonRedline")<br />Pulsante di menu combinato della barra di comando (con linea rossa)  

| Usare... | Non usare... |
| --- | --- |
| ... quando si crea un pulsante di menu combinato personalizzato. | ... per altri tipi di pulsanti. |
| | ... in qualsiasi combinazione sfondo/primo piano diversa da quella specificata. |

**Pulsante di menu combinato sulla barra dei comandi: stato predefinito**  

![Pulsante di menu combinato della barra di comando predefinito](../../extensibility/ux-guidelines/media/0303-054_splitbutton.png "0303 054_SplitButton")<br />Pulsante di menu combinato barra dei comandi predefinita  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | Nessuno |
| Primo piano (testo) | `Environment.CommandBarTextActive` |
| Primo piano (glifo) | `Environment.CommandBarSplitButtonGlyph` |
| Bordo | N/D |
| Separatore | N/D |

**Pulsante di menu combinato sulla barra dei comandi: passare il puntatore dello stato**  

![Pulsante al passaggio del mouse sulla barra dei comandi Dividi](../../extensibility/ux-guidelines/media/0303-055_splitbuttonhover.png "0303 055_SplitButtonHover")<br />Pulsante al passaggio del mouse di menu combinato barra dei comandi

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Sfumatura per questo token non utilizzato nell'interfaccia utente con temi) |
| Primo piano (testo) | `Environment.CommandBarTextHover` |
| Primo piano (glifo) | `Environment.CommandBarSplitButtonMouseOverGlyph` |
| Bordo | `Environment.CommandBarBorder` |
| Separatore | `Environment.CommandBarSplitButtonSeparator` |

**Pulsante di menu combinato sulla barra dei comandi: stati**  

![Premuto comando pulsante di menu combinato della barra](../../extensibility/ux-guidelines/media/0303-056_splitbuttonpressed.png "0303 056_SplitButtonPressed")<br />Pulsante di menu combinato barra dei comandi premuto  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Sfumatura per questo token non utilizzato nell'interfaccia utente con temi) |
| Primo piano (testo) | `Environment.CommandBarTextMouseDown` |
| Primo piano (glifo) | `Environment.CommandBarSplitButtonMouseDownGlyph` |
| Bordo | `Environment.CommandBarBorder` |
| Separatore | N/D |

**Pulsante di menu combinato sulla barra dei comandi: stato disabilitato**

![Disabilitato comando pulsante di menu combinato della barra](../../extensibility/ux-guidelines/media/0303-057_splitbuttondisabled.png "0303 057_SplitButtonDisabled")<br />Pulsante di menu combinato barra dei comandi disabilitata

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | N/D |
| Primo piano (testo) | `Environment.ComboBoxItemTextInactive` |
| Primo piano (glifo) | `Environment.CommandBarTextInactive` |
| Bordo | N/D |
| Separatore | N/D |

#### <a name="command-bar-more-options-and-overflow-buttons"></a>Pulsanti di comando della barra "Altre opzioni" e "Overflow"  
Il pulsante "Altre opzioni" viene usato quando un gruppo della barra dei comandi può essere personalizzato aggiungendo o rimuovendo pulsanti della barra dei comandi correlati. Il pulsante "Overflow" viene visualizzato quando una barra dei comandi è troncata a causa della mancanza di spazio orizzontale e, dopo avervi fatto clic sopra, mostra un menu che contiene i pulsanti della barra dei comandi che non possono essere visualizzati. I colori per questi due pulsanti sono controllati dallo stesso set di nomi di token.  

![Comando barra pulsante "Altre opzioni" (con linea rossa)](../../extensibility/ux-guidelines/media/0303-058_moreoptionsredline.png "0303 058_MoreOptionsRedline")<br />Comando barra pulsante "Altre opzioni" (con linea rossa)  

| Usare... | Non usare... |
| --- | --- |
| … for personalizzato 'altre opzioni"e"Overflow"pulsanti. | ... per i pulsanti che non dispongono di una funzionalità simile a un pulsante di "Overflow" o "Altre opzioni". |

**Comando 'Altre opzioni' e 'Overflow' pulsanti delle barre: stato predefinito**  

![Comando barra pulsante 'Opzioni' default](../../extensibility/ux-guidelines/media/0303-059_moreoptions.png "0303 059_MoreOptions")<br />Predefinito "Altre opzioni" barra dei comandi

![Comando barra 'Overflow' pulsante predefinito](../../extensibility/ux-guidelines/media/0303-060_overflow.png "0303 060_Overflow")<br />Pulsante "Overflow" predefinito

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.CommandBarOptionsBackground` |
| Primo piano (glifo) | `Environment.CommandBarOptionsGlyph` |

**Comando 'Altre opzioni' e 'Overflow' pulsanti delle barre: passare il puntatore dello stato**

![Comando barra pulsante "Altre opzioni" del mouse](../../extensibility/ux-guidelines/media/0303-061_moreoptionshover.png "0303 061_MoreOptionsHover")<br />Nella barra dei pulsante 'Opzioni' al passaggio del mouse  

!['Overflow' pulsante del mouse](../../extensibility/ux-guidelines/media/0303-062_overflowoptions.png "0303 062_OverflowOptions")<br />'Overflow' pulsante al passaggio del mouse   

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.CommandBarOptionsMouseOverBackgroundBegin`<br />(Sfumatura per questo token non utilizzato nell'interfaccia utente con temi) |
| Primo piano (glifo) | `Environment.CommandBarOptionsMouseDownGlyph` |

**Comando 'Altre opzioni' e 'Overflow' pulsanti delle barre: stati**  

![Comando barra pulsante 'Opzioni' premuto](../../extensibility/ux-guidelines/media/0303-063_moreoptionspressed.png "0303 063_MoreOptionsPressed")<br />Comando barra pulsante 'Opzioni' premuto  

![Overflow premuto](../../extensibility/ux-guidelines/media/0303-064_overflowpressed.png "0303 064_OverflowPressed")<br />Premuto 'Overflow' pulsante della barra dei comandi  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.CommandBarOptionsMouseDownBackgroundBegin`<br />(Sfumatura per questo token non utilizzato nell'interfaccia utente con temi) |
| Primo piano (glifo) | `Environment.CommandBarOptionsMouseDownGlyph` |

## <a name="document-windows"></a>Finestre dei documenti  
Non è necessario replicare le finestre di documento, perché si fornite dall'ambiente di Visual Studio. Tuttavia, si potrebbe scegliere di sfruttare i colori usati nelle finestre dei documenti in modo che l'interfaccia utente appaia sempre coerente con questa parte dell'ambiente di Visual Studio.  

Quando si utilizzano i token di colore finestra documento, prestare attenzione a usarli solo per elementi simili e sempre in coppia. Se non tale scopo, si potrebbero ottenere risultati imprevisti nell'interfaccia utente.  

### <a name="document-window-frames"></a>Cornici della finestra di documento  
Le finestre dei documenti possono essere ancorate nell'IDE o mobili come finestre separate. Quando una finestra del documento è mobile all'esterno dell'IDE, comunque si trova in una finestra del documento e di sfondo, bordo, testo e colori delle schede che sono le stesse di quando è parte dell'IDE. Tuttavia, il documento si trova all'interno di una cornice che ha colori di sfondo, del bordo e del testo propri. Quando le finestre degli strumenti sono ancorate nell'area dei documenti, ereditano il comportamento e il colore per le rispettive schede dai nomi di token delle finestre dei documenti.  

![Finestra del documento ancorata (con linea rossa)](../../extensibility/ux-guidelines/media/0303-065_dockeddocumentwindowredline.png "0303 065_DockedDocumentWindowRedline")<br />Finestra del documento ancorata (con linea rossa)  

![Finestra mobile del documento (con linea rossa)](../../extensibility/ux-guidelines/media/0303-066_floatingdocumentwindowredline.png "0303 066_FloatingDocumentWindowRedline")<br />Finestra mobile del documento (con linea rossa)  

| Usare... | Non usare... |
| --- | --- |
| ... si crea un punto qualsiasi dell'interfaccia utente che si desidera associare la finestra di documento. | ... per qualsiasi interfaccia utente che non si desidera automaticamente cambiare se la shell include un aggiornamento del tema. |

**Finestra del documento ancorato o mobile: stato predefinito**  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | Dipende dal tipo di documento |
| Primo piano (testo) | Dipende dal tipo di documento |
| Bordo | `Environment.ToolWindowBorder` |

**Con lo stato attivo, a virgola mobile cornice della finestra documento: stato predefinito**

![Impostazione predefinita con stato attivo, a virgola mobile cornice della finestra documento](../../extensibility/ux-guidelines/media/0303-067_framefocused.png "0303 067_FrameFocused")<br />Impostazione predefinita con stato attivo, a virgola mobile cornice della finestra di documento

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ToolWindowFloatingFrame` |
| Primo piano (testo) | `Environment.ToolWindowFloatingFrame` |
| Primo piano (glifo) | `Environment.RaftedWindowButtonActiveGlyph` |
| Bordo | `Environment.MainWindowActiveDefaultBorder` |
| Bordo (glifo) | `Environment.RaftedWindowButtonActiveBorder`<br />(Impostato su trasparente) |

**Cornice della finestra documento mobile, con stato non attivo: stato predefinito**  

![Cornice della finestra documento mobile, con stato non attivo predefinito](../../extensibility/ux-guidelines/media/0303-068_frameunfocused.png "0303 068_FrameUnfocused")<br />Predefinito cornice della finestra documento mobile, con stato non attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ToolWindowFloatingFrameInactive` |
| Primo piano (testo) | `Environment.ToolWindowFloatingFrameInactive` |
| Primo piano (glifo) | `Environment.RaftedWindowButtonInactiveGlyph` |
| Bordo | `Environment.MainWindowInactiveBorder` |
| Bordo (glifo) | `Environment.RaftedWindowButtonInactiveBorder`<br />(Impostato su trasparente) |

**Con lo stato attivo, a virgola mobile cornice della finestra documento: passare il puntatore dello stato**

![Con lo stato attivo, a virgola mobile cornice della finestra documento al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-069_framefocusedhover.png "0303 069_FrameFocusedHover")<br />Lo stato attivo, a virgola mobile cornice della finestra documento al passaggio del mouse  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo (glifo) | `Environment.RaftedWindowButtonHoverActive` |
| Primo piano (glifo) | `Environment.RaftedWindowButtonHoverActiveGlyph` |
| Bordo (glifo) | `Environment.RaftedWindowButtonHoverActiveBorder` |

**Cornice della finestra documento mobile, con stato non attivo: passare il puntatore dello stato**  

![Cornice della finestra documento mobile, con stato non attivo al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-070_frameunfocusedhover.png "0303 070_FrameUnfocusedHover")<br />Cornice della finestra documento mobile, con stato non attivo al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo (glifo) | `EnvironmentRaftedWindowButtonHoverInactive` |
| Primo piano (glifo) | `Environment.RaftedWindowButtonHoverInactiveGlyph` |
| Bordo (glifo) | `Environment.RaftedWindowButtonHoverInactiveBorder` |

**Con lo stato attivo, a virgola mobile cornice della finestra documento: stati**  

![Con lo stato attivo, a virgola mobile cornice della finestra documento nella macchina](../../extensibility/ux-guidelines/media/0303-071_framefocusedpressed.png "0303 071_FrameFocusedPressed")<br />Lo stato attivo, a virgola mobile cornice della finestra di documento in premere

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo (glifo) | `Environment.RaftedWindowButtonDown` |
| Primo piano (glifo) | `Environment.RaftedWindowButtonDownGlyph` |
| Bordo (glifo) | `Environment.RaftedWindowButtonDownBorder` |

### <a name="document-tabs"></a>Schede dei documenti  
Le schede dei documenti si trovano nel canale delle schede per indicare i documenti attualmente aperti, insieme al documento selezionato o attivo corrente. Anche le finestre degli strumenti possono essere ancorate nel canale delle schede dei documenti se l'utente le aggiunge in questa posizione. In questo caso, usano gli stessi colori delle schede delle finestre dei documenti. Se si crea un'interfaccia utente che deve corrispondere sempre ai colori delle finestre dei documenti (inclusi gli aggiornamenti dei temi o se vengono installati nuovi temi), fare riferimento a questi token di colore.  

![Documento a schede (con linea rossa)](../../extensibility/ux-guidelines/media/0303-072_documenttabredline.png "0303 072_DocumentTabRedline")<br />Schede dei documenti (con linea rossa)

| Usare... | Non usare... |
| --- | --- |
| ... ovunque si sta creando un'interfaccia utente che si desidera corrispondono schede dei documenti e selezionato automaticamente gli aggiornamenti dei temi o nuovi colori del tema. | per qualsiasi interfaccia utente che non si desidera cambiare automaticamente se la shell include un tema di aggiornamento. |

#### <a name="open-document-tabs"></a>Schede dei documenti aperti  
Per ogni documento aperto è presente una scheda nel canale delle schede dei documenti che ne visualizza il nome. I documenti possono essere selezionati o aperti in background e le rispettive schede riflettono questi stati:  

-   La scheda selezionata rappresenta il documento attualmente visualizzato nell'area dei documenti. Una scheda selezionata ha un bordo di documento che si estende fino al bordo superiore dell'area dei documenti.  

-   Le schede in secondo piano sono tutte le schede dei documenti diverse da quella attualmente selezionata. Se selezionate, diventano la scheda selezionata e acquisiscono tutti i colori di sfondo, del bordo e del testo da questi nomi di token.  

![Scheda documento aperto (con linea rossa)](../../extensibility/ux-guidelines/media/0303-073_opendocumenttabredline.png "0303 073_OpenDocumentTabRedline")<br />Scheda documento aperto (con linea rossa)

| Usare...  | Non usare... |
| --- | --- |
| ... quando si creano schede dei documenti personalizzate. | ... per schede provvisorie (anteprima). |
| | ... per qualsiasi interfaccia utente che non si desidera cambiare automaticamente se la shell include un aggiornamento del tema. |

**Scheda documento selezionata, con stato attivo**  

![Selezionata, con stato attivo sulla scheda documento](../../extensibility/ux-guidelines/media/0303-074_selectedtabfocused.png "0303 074_SelectedTabFocused")<br />Scheda documento selezionata, con stato attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.FileTabSelectedGradientTop`<br />(Sfumatura per questo token non utilizzato nell'interfaccia utente con temi) |
| Primo piano (testo) | `Environment.FileTabSelectedText` |
| Bordo | `Environment.FileTabSelectedBorder`<br />(Impostato sullo stesso colore dello sfondo). |
| Bordo del documento | `Environment.FileTabDocumentBorderBackground` |

**Scheda documento selezionata, con stato non attivo**

![Scheda documento selezionata, con stato non attivo](../../extensibility/ux-guidelines/media/0303-075_selectedtabunfocused.png "0303 075_SelectedTabUnfocused")<br />Scheda documento selezionata, con stato non attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.FileTabInactiveGradientTop`<br />(Sfumatura per questo token non utilizzato nell'interfaccia utente con temi) |
| Primo piano (testo) | `Environment.FileTabInactiveText` |
| Bordo | `Environment.FileTabInactiveBorder`<br />(Impostato sullo stesso colore dello sfondo). |
| Bordo del documento | `Environment.FileTabInactiveDocumentBorderBackground` |

**Scheda di documento in background: stato predefinito**  

![Scheda di documento in background predefinita](../../extensibility/ux-guidelines/media/0303-076_backgroundtab.png "0303 076_BackgroundTab")<br />Scheda di documento in background predefinita  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.FileTabBackground` |
| Primo piano (testo) | `Environment.FileTabText` |
| Bordo | `Environment.FileTabBorder`<br />(Impostato sullo stesso colore dello sfondo). |

**Scheda di documento in background: passare il puntatore dello stato**  

![Scheda documento sfondo al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-077_backgroundtabhover.png "0303 077_BackgroundTabHover")<br />Scheda documento sfondo al passaggio del mouse  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.FileTabHotGradientTop`<br />(Sfumatura per questo token non utilizzato nell'interfaccia utente con temi) |
| Primo piano (testo) | `Environment.FileTabHotText` |
| Bordo | `Environment.FileTabHotBorder`<br />(Impostato sullo stesso colore dello sfondo). |

#### <a name="preview-tab"></a>Scheda anteprima  
Chiamato anche una scheda "provvisoria". La scheda anteprima è visualizzata sul lato destro del canale delle schede dei documenti quando l'utente fa clic su un elemento nella finestra degli strumenti Esplora soluzione. Questa scheda funge da anteprima del documento e offre all'utente anche l'opzione di mantenere il documento aperto sul lato sinistro del canale delle schede dei documenti. Può essere aperta una sola scheda anteprima per volta. Le schede anteprima hanno sia uno sfondo sia stati selezionati, come le schede aperte, e possono avere stato attivo o non attivo quando sono attive.  

![Scheda Anteprima (con linea rossa)](../../extensibility/ux-guidelines/media/0303-078_previewtabredline.png "0303 078_PreviewTabRedline")<br />Scheda Anteprima (con linea rossa)

| Usare... | Non usare... |
| --- | --- |
| ... ovunque si sta creando provvisorio anteprima e alcuni elementi in modo che corrisponda il colore della scheda Anteprima. | per qualsiasi tipo di documento o scheda non provvisoria (anteprima). |
| | ... per qualsiasi interfaccia utente che non si desidera cambiare automaticamente se la shell include un aggiornamento del tema. |

**Scheda Anteprima con stato attivo, selezionato**  

![Scheda Anteprima con stato attivo, selezionato](../../extensibility/ux-guidelines/media/0303-079_previewtabfocused.png "0303 079_PreviewTabFocused")<br />Scheda Anteprima con stato attivo, selezionato

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.FileTabProvisionalSelectedActive` |
| Primo piano (testo) | `Environment.FileTabProvisionalSelectedActiveForeground` |
| Bordo | `Environment.FileTabProvisionalSelectedActiveBorder`<br />(Impostato sullo stesso colore dello sfondo). |
| Bordo del documento | `Environment.FileTabProvisionalSelectedActiveBorder` |

**Scheda anteprima selezionata, con stato non attivo**  

![Scheda Anteprima con stato non attivo, selezionato](../../extensibility/ux-guidelines/media/0303-080_previewtabunfocused.png "0303 080_PreviewTabUnfocused")<br />Scheda anteprima selezionata, con stato non attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.FileTabProvisionalSelectedInactive` |
| Primo piano (testo) | `Environment.FileTabProvisionalSelectedInactiveForeground` |
| Bordo | `Environment.FileTabProvisionalSelectedInactiveBorder` |
| Bordo del documento | `Environment.FileTabProvisionalSelectedInactiveBorder` |

**Scheda Anteprima sfondo: stato predefinito**  

![Scheda Anteprima sfondo predefinito](../../extensibility/ux-guidelines/media/0303-081_previewbackgroundtab.png "0303 081_PreviewBackgroundTab")<br />Scheda Anteprima di sfondo predefinito  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.FileTabProvisionalInactive` |
| Primo piano (testo) | `Environment.FileTabProvisionalInactiveForeground` |
| Bordo | `Environment.FileTabProvisionalInactiveBorder`<br />(Impostato sullo stesso colore dello sfondo). |

**Scheda Anteprima sfondo: passare il puntatore dello stato**  

![Scheda Anteprima sfondo al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-082_previewbackgroundtabhover.png "0303 082_PreviewBackgroundTabHover")<br />Scheda Anteprima sfondo al passaggio del mouse  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.FileTabProvisionalHover` |
| Primo piano (testo) | `Environment.FileTabProvisionalHoverForeground` |
| Bordo | `Environment.FileTabProvisionalHoverBorder`<br />(Impostato sullo stesso colore dello sfondo). |

#### <a name="document-overflow-button"></a>Pulsante di overflow dei documenti  
Il pulsante di overflow dei documenti è presente se ci sono uno o più documenti aperti, indipendentemente dal fatto che nella configurazione corrente sia disponibile spazio sufficiente da contenere tutte le schede dei documenti. Il menu a discesa di overflow di documento, è controllato dal [barra menu dei comandi](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus) colori, visualizza un elenco di tutti i documenti aperti, sia visibili sia nascosti e il glifo di overflow cambia a seconda che tutti i documenti aperti siano visualizzati nel canale delle schede.  

![Pulsante di overflow dei documenti (con linea rossa)](../../extensibility/ux-guidelines/media/0303-083_overflowredline.png "0303 083_OverflowRedline")<br />Pulsante di overflow dei documenti (con linea rossa)

| Usare... | Non usare... |
| --- | --- |
| ... quando si crea un pulsante di overflow di documento personalizzato. | ... per l'interfaccia utente che non è simile a un pulsante di overflow. |
| | ... per i pulsanti di overflow della barra dei comandi. |

**Pulsante di overflow dei documenti: stato predefinito**  

![Pulsante di overflow dei documenti predefiniti](../../extensibility/ux-guidelines/media/0303-084_overflow.png "0303 084_Overflow")<br />Pulsante di overflow dei documenti predefiniti

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.DocWellOverflowButtonBackground` |
| Primo piano (glifo) | `Environment.DocWellOverflowButtonGlyph` |
| Bordo | N/D |

**Pulsante di overflow dei documenti: passare il puntatore dello stato**

![Pulsante di overflow dei documenti al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-085_overflowhover.png "0303 085_OverflowHover")<br />Pulsante di overflow dei documenti al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.DocWellOverflowButtonMouseOverBackground` |
| Primo piano (glifo) | `Environment.DocWellOverflowButtonMouseOverGlyph` |
| Bordo | `Environment.DocWellOverflowButtonMouseOverBorder` |

**Pulsante di overflow dei documenti: stati**  

![Pulsante di overflow dei documenti nella macchina](../../extensibility/ux-guidelines/media/0303-086_overflowpressed.png "0303 086_OverflowPressed")<br />Pulsante di overflow documento premere

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.DocWellOverflowButtonMouseDownBackground` |
| Primo piano (glifo) | `Environment.DocWellOverflowButtonMouseDownGlyph` |
| Bordo | `Environment.DocWellOverflowButtonMouseDownBorder` |

### <a name="tagging"></a>Assegnazione di tag  
Visual Studio supporta l'assegnazione di tag, che permette a un utente di dichiarare parole chiave da cercare per scopi di verifica. Ad esempio, i project manager e gli sviluppatori possono usare Team Foundation Server (TFS) per assegnare tag a elementi di lavoro. La tabella seguente indica i nomi di colore per il tag stesso e il glifo dell'icona di chiusura visualizzato negli stati corrispondenti al passaggio del mouse e alla selezione.  

![Assegnazione di tag in Visual Studio (con linea rossa)](../../extensibility/ux-guidelines/media/0303-176_taggingredline.png "0303 176_TaggingRedline")<br />Assegnazione di tag in Visual Studio (con linea rossa)  

| Usare... | Non usare... |
| --- | --- |
| ... per l'interfaccia utente che supporta l'assegnazione di tag. | per qualsiasi altro tipo di interfaccia utente. |

#### <a name="tags"></a>Tag  

**Tag: stato predefinito**

![Predefinito tag](../../extensibility/ux-guidelines/media/0303-177_tag.png "0303 177_Tag")<br />Tag predefinito

| Elemento | Nome token: Category.color |
| --- | --- |  
| Sfondo | `Tag.Background` |
| Primo piano (testo) | `Tag.Background` |

**Tag: stato del mouse**  

![Tag al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-178_taghover.png "0303 178_TagHover")<br />Tag al passaggio del mouse  

| Elemento | Nome token: Category.color |
| --- | --- |  
| Sfondo | `Tag.HoverBackground` |
| Primo piano (testo) | `Tag.HoverBackgroundText` |

**Tag: premuto stato**

![Tag premuto](../../extensibility/ux-guidelines/media/0303-179_tagpressed.png "0303 179_TagPressed")<br />Tag premuto  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Tag.PressedBackground` |
| Primo piano (testo) | `Tag.PressedBackgroundText` |

**Tag: stato selezionato**

![Tag selezionato](../../extensibility/ux-guidelines/media/0303-180_tagselected.png "0303 180_TagSelected")<br />Tag selezionato  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Tag.SelectedBackground` |
| Primo piano (testo) | `Tag.SelectedBackgroundText` |

#### <a name="close-times-tag-glyph"></a>Close (&times;) tag glifo

**Close (&times;) glifo del tag: stato predefinito**

![Predefinito di chiusura (&times;) glifo del tag](../../extensibility/ux-guidelines/media/0303-181_tagglyph.png "0303 181_TagGlyph")<br />Predefinito di chiusura (&times;) tag glifo

| Elemento | Nome token: Category.color |
| --- | --- |  
| Sfondo | N/D |
| Primo piano (glifo) | `Tag.TagHoverGlyph` |

**Close (&times;) glifo del tag: passare il puntatore dello stato**

![Close (&times;) tag glifo al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-182_tagglyphhover.png "0303 182_TagGlyphHover")<br />Close (&times;) tag glifo al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Tag.TagHoverGlyphHoverBackground` |
| Primo piano (glifo) | `Tag.TagHoverGlyphHover` |
| Bordo | `Tag.TagHoverGlyphHoverBorder` |

**Close (&times;) glifo del tag: stati**

![Premuto chiusura (&times;) glifo del tag](../../extensibility/ux-guidelines/media/0303-183_tagglyphpressed.png "0303 183_TagGlyphPressed")<br />Chiudi premuto (&times;) tag glifo

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Tag.TagHoverGlyphPressedBackground` |
| Primo piano (glifo) | `Tag.TagHoverGlyphPressed` |
| Bordo | `Tag.TagHoverGlyphPressedBorder` |

**Seleziona tag con chiusura (&times;) glifo: stato predefinito**

![Tag selezionato con chiusura predefinito (&times;) glifo](../../extensibility/ux-guidelines/media/0303-184_tagselected.png "0303 184_TagSelected")<br />Tag selezionato con chiusura predefinito (&times;) glifo

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | N/D |
| Primo piano (glifo) | `Tag.TagSelectedGlyph` |

**Seleziona tag con chiusura (&times;) glifo: passare il puntatore dello stato**  

![Seleziona tag con chiusura (&times;) glifo al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-185_tagselectedhover.png "0303 185_TagSelectedHover")<br />Selezionare i tag di chiusura (&times;) glifo al passaggio del mouse  


| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Tag.TagSelectedGlyphHoverBackground` |
| Primo piano (glifo) | `Tag.TagSelectedGlyphHover` |
| Bordo | `Tag.TagSelectedGlyphHoverBorder` |

**Seleziona tag con chiusura (&times;) glifo: stati**  

![Selezionata, premuto tag con chiusura (&times;) glifo](../../extensibility/ux-guidelines/media/0303-186_tagselectedpressed.png "0303 186_TagSelectedPressed")<br />Selezionata, premuto tag di chiusura (&times;) glifo

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Tag.TagSelectedGlyphPressedBackground` |
| Primo piano (glifo) | `Tag.TagSelectedGlyphPressed` |
| Bordo | `Tag.TagSelectedGlyphPressedBorder` |

## <a name="tool-windows"></a>Finestre degli strumenti  
Non è necessario per replicare le finestre degli strumenti, perché si fornite dall'ambiente di Visual Studio. Tuttavia, si potrebbe scegliere di sfruttare i colori usati nelle finestre degli strumenti in modo che l'interfaccia utente appaia sempre coerente con questa parte dell'ambiente di Visual Studio.  

![Finestra degli strumenti (con linea rossa)](../../extensibility/ux-guidelines/media/0303-087_toolwindowredline.png "0303 087_ToolWindowRedline")<br />Finestra degli strumenti (con linea rossa)

| Usare... | Non usare... |
| --- | --- |
| ... si crea un punto qualsiasi dell'interfaccia utente che si desidera trovare una corrispondenza finestre degli strumenti. | ... per qualsiasi interfaccia utente che non si desidera cambiare automaticamente se la shell include un aggiornamento del tema. |

### <a name="tool-window-frame"></a>Cornice delle finestre degli strumenti  
Le finestre degli strumenti in Visual Studio vengono usate per molte attività diverse e possono avere stati diversi. Se una finestra degli strumenti è aperta, può essere assegnata a uno qualsiasi dei quattro lati dell'area del documento. Le finestre degli strumenti possono anche essere mobili al di fuori dell'IDE, per poter essere riposizionate in qualsiasi punto dello schermo dell'utente. Le finestre mobili sono sempre in primo piano nell'IDE. Infine, le finestre degli strumenti possono essere ancorate come finestre dei documenti ed essere visualizzate come scheda nell'area dei documenti. Le finestre degli strumenti ancorate come finestre dei documenti vengono colorate in parte usando i nomi di token delle finestre dei documenti.  

![Frame finestra degli strumenti (con linea rossa)](../../extensibility/ux-guidelines/media/0303-088_toolwindowframeredline.png "0303 088_ToolWindowFrameRedline")<br />Frame finestra degli strumenti (con linea rossa)

| Usare... | Non usare... |
| --- | --- |
| ... si crea un punto qualsiasi dell'interfaccia utente che si desidera trovare una corrispondenza finestre degli strumenti. | ... per qualsiasi interfaccia utente che non si desidera cambiare automaticamente se la shell include un aggiornamento del tema. |

**Finestra degli strumenti ancorata**  

![Finestra degli strumenti ancorata](../../extensibility/ux-guidelines/media/0303-089_toolwindowdocked.png "0303 089_ToolWindowDocked")<br />Finestra degli strumenti ancorata  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ToolWindowBackground` |
| Bordo | `Environment.ToolWindowBorder` |

**Mobile, con stato attivo finestra degli strumenti**

![Mobile, con stato attivo finestra degli strumenti](../../extensibility/ux-guidelines/media/0303-090_toolwindowfocused.png "0303 090_ToolWindowFocused")<br />Mobile, con stato attivo finestra degli strumenti

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ToolWindowBackground` |
| Bordo | `Environment.MainWindowActiveDefaultBorder` |

**Mobile, finestra degli strumenti con stato non attivo**  

![Finestra degli strumenti mobile, con stato non attivo](../../extensibility/ux-guidelines/media/0303-091_toolwindowunfocused.png "0303 091_ToolWindowUnfocused")<br />Mobile, finestra degli strumenti con stato non attivo  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ToolWindowBackground` |
| Bordo | `Environment.MainWindowInactiveBorder` |

### <a name="toolbox-like-windows"></a>Casella degli strumenti simili alle finestre
Casella degli strumenti è uno delle finestre degli strumenti comuni utilizzate più di frequente in Visual Studio. Si tratta essenzialmente di un controllo struttura ad albero con un tema e stili speciali applicati.  

![Finestra Casella degli strumenti simili (con linea rossa)](../../extensibility/ux-guidelines/media/0303-189_toolboxredline.png "0303 189_ToolboxRedline")<br />Finestra Casella degli strumenti simili (con linea rossa)

| Usare... | Non usare... |
| --- | --- |
| ... quando si progetta una finestra degli strumenti che si desidera essere sempre coerente con la casella degli strumenti della shell. | ... per qualsiasi elemento che non è simile alla casella degli strumenti dell'interfaccia utente, o se non si è sicuri se l'interfaccia utente sarà presenti problemi di modifica dei colori della casella degli strumenti della shell. |

**I nodi della casella degli strumenti: stato predefinito**

![Nodo padre della casella degli strumenti predefinita](../../extensibility/ux-guidelines/media/0303-190_toolboxparentnode.png "0303 190_ToolboxParentNode")<br />Nodo padre di casella degli strumenti predefinita

![Nodo figlio della casella degli strumenti predefinita](../../extensibility/ux-guidelines/media/0303-191_toolboxchildnode.png "0303 191_ToolboxChildNode")<br />Nodo figlio della casella degli strumenti predefinito

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ToolboxContent`<br />(Intestazioni) |
| Sfondo | `Environment.ToolWindowBackground`<br />(Singoli elementi o intera finestra se i controlli non disponibili) |
| Bordo | Nessuno |
| Primo piano (glifo) | `Environment.ToolboxContent` |
| Primo piano (testo) | `Environment.ToolboxContent` |

**I nodi figlio della casella degli strumenti: passare il puntatore dello stato**

![Nodo figlio della casella degli strumenti al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-192_toolboxchildnodehover.png "0303 192_ToolboxChildNodeHover")<br />Nodo figlio della casella degli strumenti al passaggio del mouse  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ToolboxContentMouseOver`<br />(Solo singoli elementi) |
| Bordo | Nessuno |
| Primo piano (testo) | `Environment.ToolboxContentMouseOver`<br />(Solo singoli elementi) |

**I nodi della casella degli strumenti selezionati: con stato attivo dello stato**

![Nodo padre della casella degli strumenti con stato attivo, selezionato](../../extensibility/ux-guidelines/media/0303-193_toolboxparentnodefocused.png "0303 193_ToolboxParentNodeFocused")<br />Nodo padre della casella degli strumenti con stato attivo, selezionato  

![Nodo figlio della casella degli strumenti con stato attivo, selezionato](../../extensibility/ux-guidelines/media/0303-194_toolboxchildnodefocused.png "0303 194_ToolboxChildNodeFocused")<br />Nodo figlio della casella degli strumenti con stato attivo, selezionato

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `TreeView.SelectedItemActive`<br />Da [visualizzazione ad albero](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) categoria |
| Bordo | `TreeView.FocusVisualBorder`<br />Da [visualizzazione ad albero](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) categoria |
| Primo piano (glifo) | `TreeView.SelectedItemActive`<br />Da [visualizzazione ad albero](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) categoria |
| Primo piano (testo) | `TreeView.SelectedItemActive`<br />Da [visualizzazione ad albero](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) categoria |

**I nodi della casella degli strumenti selezionati: stato non attivo**

![Nodo padre della casella degli strumenti selezionata, con stato non attivo](../../extensibility/ux-guidelines/media/0303-195_toolboxparentnodeunfocused.png "0303 195_ToolboxParentNodeUnfocused")<br />Nodo padre della casella degli strumenti selezionata, con stato non attivo  

![Nodo figlio della casella degli strumenti selezionata, con stato non attivo](../../extensibility/ux-guidelines/media/0303-196_toolboxchildnodeunfocused.png "0303 196_ToolboxChildNodeUnfocused")<br />Nodo figlio della casella degli strumenti selezionata, con stato non attivo  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `TreeView.SelectedItemInactive`<br />Da [visualizzazione ad albero](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) categoria |
| Bordo | Nessuno |
| Primo piano (glifo) | `TreeView.SelectedItemInactive`<br />Da [visualizzazione ad albero](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) categoria |
| Primo piano (testo) | `TreeView.SelectedItemInactive`<br />Da [visualizzazione ad albero](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) categoria |

### <a name="tool-window-title-bar"></a>Barra del titolo delle finestre degli strumenti  
Il bordo della barra del titolo non è un bordo vero e proprio, è una linea spessa nella parte superiore della barra del titolo. Non dispone di un nome di token per il relativo stato non attivo.  

![Barra del titolo di finestra degli strumenti (con linea rossa)](../../extensibility/ux-guidelines/media/0303-092_toolwindowtitlebarredline.png "0303 092_ToolWindowTitleBarRedline")<br />Barra del titolo di finestra degli strumenti (con linea rossa)

| Usare... | Non usare... |
| --- | --- |
| ... si crea un punto qualsiasi dell'interfaccia utente che si desidera trovare una corrispondenza finestre degli strumenti. | ... per qualsiasi interfaccia utente che non si desidera cambiare automaticamente se la shell include un aggiornamento del tema. |

**Barra del titolo con stato attivo**

![Barra del titolo con stato attivo](../../extensibility/ux-guidelines/media/0303-093_titlebarfocused.png "0303 093_TitleBarFocused")<br />Barra del titolo con stato attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.TitleBarActiveGradientBegin`<br />(Sfumatura per questo token non utilizzato nell'interfaccia utente con temi) |
| Primo piano (testo) | `Environment.TitleBarActiveText` |
| Bordo | `Environment.TitleBarActiveBorder`<br />(Impostato sullo stesso colore dello sfondo). |
| Quadratino di trascinamento | `Environment.TitleBarDragHandleActive` |

**Barra del titolo con stato non attivo**  

![Barra del titolo con stato non attivo](../../extensibility/ux-guidelines/media/0303-094_titlebarunfocused.png "0303 094_TitleBarUnfocused")<br />Barra del titolo con stato non attivo

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.TitleBarInactiveGradientBegin`<br />(Sfumatura per questo token non utilizzato nell'interfaccia utente con temi) |
| Primo piano (testo) | `Environment.TitleBarInactiveText` |
| Bordo | N/D |
| Quadratino di trascinamento | `Environment.TitleBarDragHandle` |

#### <a name="tool-window-title-bar-buttons"></a>Pulsanti della barra del titolo finestra dello strumento  
![Della pulsante barra del titolo (con linea rossa)](../../extensibility/ux-guidelines/media/0303-095_titlebarbuttonredline.png "0303 095_TitleBarButtonRedline")<br />Title bar pulsante (con linea rossa)  

| Usare... | Non usare... |
| --- | --- |
| ... per i pulsanti visualizzati nell'interfaccia utente che utilizza il token di colore dalle barre del titolo di finestra dello strumento. | ... per i pulsanti visualizzati in altre posizioni. |
| | ... in qualsiasi combinazione sfondo/primo piano diversa da quella specificata. |

**Con stato attivo pulsanti della barra del titolo: stato predefinito**

![Impostazione predefinita, con stato attivo pulsanti della barra del titolo](../../extensibility/ux-guidelines/media/0303-096_titlebarbuttonfocused.png "0303 096_TitleBarButtonFocused")<br />Impostazione predefinita, i pulsanti della barra del titolo con stato attivo  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | N/D |
| Primo piano (glifo) | `Environment.ToolWindowButtonActiveGlyph` |
| Bordo | N/D |

**Pulsanti della barra del titolo con stato non attivo: stato predefinito**

![Impostazione predefinita, i pulsanti della barra del titolo con stato non attivo](../../extensibility/ux-guidelines/media/0303-097_titlebarbuttonunfocused.png "0303 097_TitleBarButtonUnfocused")<br />Impostazione predefinita, i pulsanti della barra del titolo con stato non attivo    

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | N/D |
| Primo piano (glifo) | `Environment.ToolWindowButtonInactiveGlyph` |
| Bordo | N/D |

**Con stato attivo pulsanti della barra del titolo: passare il puntatore dello stato**  

![Con stato attivo di pulsanti della barra del titolo del mouse](../../extensibility/ux-guidelines/media/0303-098_titlebarbuttonfocusedhover.png "0303 098_TitleBarButtonFocusedHover")<br />Pulsanti della barra del titolo con stato attivo al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ToolWindowButtonHoverActive` |
| Primo piano (glifo) | `Environment.ToolWindowButtonHoverActiveGlyph` |
| Bordo | `Environment.ToolWindowButtonHoverActiveBorder` |

**Pulsanti della barra del titolo con stato non attivo: passare il puntatore dello stato**  

![Pulsanti della barra del titolo con stato non attivo al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-099_titlebarbuttonunfocusedhover.png "0303 099_TitleBarButtonUnfocusedHover")<br />Pulsanti della barra del titolo con stato non attivo al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ToolWindowButtonHoverInactive` |
| Primo piano (glifo) | `Environment.ToolWindowButtonHoverInactiveGlyph` |
| Bordo | `Environment.ToolWindowButtonHoverInactiveBorder` |

**Con stato attivo pulsanti della barra del titolo: stati**

![Con stato attivo di pulsanti della barra del titolo nella macchina](../../extensibility/ux-guidelines/media/0303-100_titlebarbuttonfocusedpressed.png "0303 100_TitleBarButtonFocusedPressed")<br />Pulsanti della barra del titolo con stato attivo su premere

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ToolWindowButtonDown` |
| Primo piano (glifo) | `Environment.ToolWindowButtonDownActiveGlyph` |
| Bordo | `Environment.ToolWindowButtonDownBorder` |

**Pulsanti della barra del titolo con stato non attivo: stati**

![Pulsanti della barra del titolo con stato non attivo su macchina](../../extensibility/ux-guidelines/media/0303-101_titlebarbuttonunfocusedpressed.png "0303 101_TitleBarButtonUnfocusedPressed")<br />Pulsanti della barra del titolo con stato non attivo su premere  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ToolWindowButtonDown` |
| Primo piano (glifo) | `Environment.ToolWindowButtonDownInactiveGlyph` |
| Bordo | `Environment.ToolWindowButtonDownBorder` |

### <a name="tool-window-tabs"></a>Schede delle finestre degli strumenti  
![Scheda della finestra degli strumenti (con linea rossa)](../../extensibility/ux-guidelines/media/0303-102_toolwindowtabredline.png "0303 102_ToolWindowTabRedline")<br />Scheda della finestra degli strumenti (con linea rossa)

| Usare... | Non usare... |
| --- | --- |
| ... si crea un punto qualsiasi dell'interfaccia utente che si desidera trovare una corrispondenza finestre degli strumenti. | ... per qualsiasi interfaccia utente che non si desidera cambiare automaticamente se la shell include un aggiornamento del tema. |

**Scheda della finestra degli strumenti con stato attivo selezionata**

![Selezionata, con stato attivo scheda della finestra degli strumenti](../../extensibility/ux-guidelines/media/0303-103_toolwindowtabfocused.png "0303 103_ToolWindowTabFocused")<br />Scheda della finestra degli strumenti con stato attivo selezionata

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ToolWindowTabSelectedTab` |
| Primo piano (testo) | `Environment.ToolWindowTabSelectedActiveText` |
| Bordo | `Environment.ToolWindowTabSelectedBorder`<br />(Impostato sullo stesso colore dello sfondo). |

**Scheda della finestra degli strumenti con stato non attivo selezionata**  

![Scheda della finestra degli strumenti con stato non attivo selezionata](../../extensibility/ux-guidelines/media/0303-104_toolwindowtabunfocused.png "0303 104_ToolWindowTabUnfocused")<br />Scheda della finestra degli strumenti con stato non attivo selezionata

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ToolWindowTabSelectedTab` |
| Primo piano (testo) | `Environment.ToolWindowTabSelectedText` |
| Bordo | `Environment.ToolWindowTabSelectedBorder`<br />(Impostato sullo stesso colore dello sfondo). |

**Scheda della finestra degli strumenti in background: stato predefinito**

![Scheda della finestra degli strumenti predefinita in background](../../extensibility/ux-guidelines/media/0303-105_toolwindowbackgroundtab.png "0303 105_ToolWindowBackgroundTab")<br />Scheda finestra degli strumenti di sfondo predefinito  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ToolWindowTabGradientBegin`<br />`Environment.ToolWindowTabGradientEnd`<br />(Cursori sfumatura impostati sullo stesso valore di colore in Visual Studio 2013.) |
| Primo piano (testo) | `Environment.ToolWindowTabText` |
| Bordo | `Environment.ToolWindowTabBorder` |

**Scheda della finestra degli strumenti in background: passare il puntatore dello stato**

![Scheda della finestra degli strumenti sfondo al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-106_toolwindowbackgroundtabhover.png "0303 106_ToolWindowBackgroundTabHover")<br />Scheda della finestra degli strumenti in secondo piano al passaggio del mouse

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.ToolWindowTabMouseOverBackgroundBegin`<br />`Environment.ToolWindowTabMouseOverBackgroundEnd`<br />(Cursori sfumatura impostati sullo stesso valore di colore in Visual Studio 2013.) |
| Primo piano (testo) | `Environment.ToolWindowTabMouseOverText` |
| Bordo | `Environment.ToolWindowTabMouseOverBorder`<br />(Impostato sullo stesso colore dello sfondo). |  

### <a name="auto-hide-tabs"></a>Schede Nascondi automaticamente  

![Schede Nascondi automaticamente (con linea rossa)](../../extensibility/ux-guidelines/media/0303-107_autohideredline.png "0303 107_AutoHideRedline")schede Nascondi automaticamente (con linea rossa)

| Usare... | Non usare... |
| --- | --- |
| ... ovunque si sta creando un'interfaccia utente che si desidera trovare una corrispondenza schede delle finestre degli strumenti Nascondi automaticamente. | ... per qualsiasi interfaccia utente che non si desidera cambiare automaticamente se la shell include un aggiornamento del tema. |

**Schede Nascondi automaticamente: stato predefinito**  

![Scheda Nascondi automaticamente predefinita](../../extensibility/ux-guidelines/media/0303-108_autohidetab.png "0303 108_AutoHideTab")<br />Scheda Nascondi automaticamente predefinita

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.AutoHideTabBackgroundBegin`<br />(Sfumatura per questo token non utilizzato nell'interfaccia utente con temi) |
| Primo piano (testo) | `Environment.AutoHideTabText` |
| Bordo | `Environment.AutoHideTabBorder` |

**Schede Nascondi automaticamente: passare il puntatore dello stato**

![Scheda Nascondi automaticamente al passaggio del mouse](../../extensibility/ux-guidelines/media/0303-109_autohidetabhover.png "0303 109_AutoHideTabHover")<br />Scheda Nascondi automaticamente al passaggio del mouse  

| Elemento | Nome token: Category.color |
| --- | --- |
| Sfondo | `Environment.AutoHideTabMouseOverBackgroundBegin`<br />(Sfumatura per questo token non utilizzato nell'interfaccia utente con temi) |
| Primo piano (testo) | `Environment.AutoHideTabMouseOverText` |
| Bordo | `Environment.AutoHideTabMouseOverBorder` |
