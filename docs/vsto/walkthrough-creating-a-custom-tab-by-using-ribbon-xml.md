---
title: 'Procedura dettagliata: Creazione di una scheda personalizzata utilizzando la barra multifunzione XML | Documenti Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- customizing the Ribbon, tabscustom Ribbon, tabs
- Ribbon [Office development in Visual Studio], XML
- XML [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Custom tab [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1b736ace651854b3b6a527685e150f6f1ec7194c
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-a-custom-tab-by-using-ribbon-xml"></a>Procedura dettagliata: creazione di una scheda personalizzata utilizzando l'elemento XML della barra multifunzione
  Questa procedura dettagliata viene illustrato come creare una scheda della barra multifunzione personalizzata usando il **della barra multifunzione (XML)** elemento.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 Questa procedura dettagliata illustra le attività seguenti:  
  
-   Aggiunta di pulsanti per la **Add-Ins** scheda. Il **Add-Ins** scheda è l'impostazione predefinita che è definito nel file XML della barra multifunzione.  
  
-   Automazione di Microsoft Office Word utilizzando i pulsanti nella **Add-Ins** scheda.  
  
> [!NOTE]  
>  I nomi o i percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word.  
  
## <a name="creating-the-project"></a>Creazione del progetto  
 Il primo passaggio consiste nel creare un progetto di componente aggiuntivo VSTO per Word. Successivamente si personalizzerà la **Add-Ins** scheda di questo documento.  
  
#### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto  
  
1.  Creare un **componente aggiuntivo per Word** progetto con il nome **MyRibbonAddIn**.  
  
     Per altre informazioni, vedere [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Apre il **ThisAddIn.cs** o **ThisAddIn. vb** file di codice e aggiunge il **MyRibbonAddIn** progetto **Esplora soluzioni**.  
  
## <a name="creating-the-vsto-add-ins-tab"></a>Creazione della scheda Componenti aggiuntivi VSTO  
 Per creare il **Add-Ins** scheda, aggiungere un **della barra multifunzione (XML)** elemento al progetto. Più avanti nella procedura dettagliata verranno aggiunti alcuni pulsanti a questa scheda.  
  
#### <a name="to-create-the-add-ins-tab"></a>Per creare la scheda Componenti aggiuntivi  
  
1.  Nel menu **Progetto** fare clic su **Aggiungi nuovo elemento**.  
  
2.  Nel **Aggiungi nuovo elemento** nella finestra di dialogo **della barra multifunzione (XML)**.  
  
3.  Modificare il nome della nuova barra multifunzione in **MyRibbon**e quindi scegliere **Aggiungi**.  
  
     Il **MyRibbon.cs** o **MyRibbon. vb** file verrà aperto nella finestra di progettazione. Un file XML denominato **MyRibbon.xml** viene inoltre aggiunto al progetto.  
  
4.  In **Esplora**, fare doppio clic su **ThisAddin.cs** o **ThisAddIn. vb**, quindi fare clic su **Visualizza codice**.  
  
5.  Aggiungere il codice seguente alla classe **ThisAddIn** . Questo codice esegue l'override del metodo CreateRibbonExtensibilityObject e restituisce la classe Ribbon XML all'applicazione di Office.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]  
  
6.  In **Esplora**, fare doppio clic su di **MyRibbonAddIn** del progetto e quindi fare clic su **compilare**. Verificare che il progetto venga compilato senza errori.  
  
## <a name="adding-buttons-to-the-add-ins-tab"></a>Aggiunta di pulsanti alla scheda Componenti aggiuntivi  
 L'obiettivo di questo componente aggiuntivo VSTO consiste nell'offrire all'utente un modo per aggiungere testo standard e una tabella specifica al documento attivo. Per fornire l'interfaccia utente, aggiungere due pulsanti per la **Add-Ins** scheda modificando il file XML della barra multifunzione. Più avanti nella procedura dettagliata verranno definiti i metodi di callback per i pulsanti. Per ulteriori informazioni sul file XML della barra multifunzione, vedere [XML della barra multifunzione](../vsto/ribbon-xml.md).  
  
#### <a name="to-add-buttons-to-the-add-ins-tab"></a>Per aggiungere pulsanti alla scheda Componenti aggiuntivi  
  
1.  In **Esplora**, fare doppio clic su **MyRibbon.xml** e quindi fare clic su **aprire**.  
  
2.  Sostituire il contenuto del **scheda** elemento con il seguente codice XML. Questo codice XML modifica l'etichetta del gruppo di controllo predefinito per **contenuto**, e vengono aggiunti due nuovi pulsanti con le etichette **Insert Text** e **Inserisci tabella**.  
  
    ```  
    <tab idMso="TabAddIns">  
        <group id="ContentGroup" label="Content">  
            <button id="textButton" label="Insert Text"  
                 screentip="Text" onAction="OnTextButton"  
                 supertip="Inserts text at the cursor location."/>  
            <button id="tableButton" label="Insert Table"  
                 screentip="Table" onAction="OnTableButton"  
                 supertip="Inserts a table at the cursor location."/>  
        </group>  
    </tab>  
    ```  
  
## <a name="automating-the-document-by-using-the-buttons"></a>Automazione del documento usando i pulsanti  
 È necessario aggiungere `onAction` metodi di callback per la **Insert Text** e **Inserisci tabella** pulsanti per eseguire azioni quando l'utente fa clic su loro. Per ulteriori informazioni sui metodi di callback per i controlli della barra multifunzione, vedere [XML della barra multifunzione](../vsto/ribbon-xml.md).  
  
#### <a name="to-add-callback-methods-for-the-buttons"></a>Per aggiungere i metodi di callback per i pulsanti  
  
1.  In **Esplora**, fare doppio clic su **MyRibbon. cs** o **MyRibbon. vb**, quindi fare clic su **aprire**.  
  
2.  Aggiungere il codice seguente all'inizio del **MyRibbon.cs** o **MyRibbon. vb** file. Tramite questo codice viene creato un alias per lo spazio dei nomi <xref:Microsoft.Office.Interop.Word>.  
  
     [!code-csharp[Trin_RibbonButtons#1](../vsto/codesnippet/CSharp/Trin_RibbonButtons/MyRibbon.cs#1)]
     [!code-vb[Trin_RibbonButtons#1](../vsto/codesnippet/VisualBasic/Trin_RibbonButtons/MyRibbon.vb#1)]  
  
3.  Aggiungere il metodo seguente alla classe `MyRibbon`. Si tratta di un metodo di callback per la **Insert Text** pulsante che aggiunge una stringa al documento attivo nella posizione corrente del cursore.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#2](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#2](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb#2)]  
  
4.  Aggiungere il metodo seguente alla classe `MyRibbon`. Si tratta di un metodo di callback per la **Inserisci tabella** pulsante che consente di aggiungere una tabella al documento attivo nella posizione corrente del cursore.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#3](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#3](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb#3)]  
  
## <a name="testing-the-vsto-add-in"></a>Test del componente aggiuntivo VSTO  
 Quando si esegue il progetto, verrà visualizzata la parola e la scheda denominata **Add-Ins** nella barra multifunzione. Fare clic su di **Insert Text** e **Inserisci tabella** pulsanti il **Add-Ins** scheda per testare il codice.  
  
#### <a name="to-test-your-vsto-add-in"></a>Per testare il componente aggiuntivo VSTO  
  
1.  Premere F5 per eseguire il progetto.  
  
2.  Verificare che il **Add-Ins** scheda è visibile sulla barra multifunzione.  
  
3.  Fare clic sulla scheda **Componenti aggiuntivi** .  
  
4.  Verificare che il **contenuto** gruppo è visibile sulla barra multifunzione.  
  
5.  Fare clic su di **Insert Text** pulsante il **contenuto** gruppo.  
  
     Verrà aggiunta una stringa in corrispondenza della posizione corrente del cursore nel documento.  
  
6.  Fare clic su di **Inserisci tabella** pulsante il **contenuto** gruppo.  
  
     Verrà aggiunta una tabella in corrispondenza della posizione corrente del cursore nel documento.  
  
## <a name="next-steps"></a>Passaggi successivi  
 È possibile trovare ulteriori informazioni sulla personalizzazione dell'interfaccia utente di Office nei seguenti argomenti:  
  
-   Personalizzare la barra multifunzione di un'applicazione di Office diversa. Per ulteriori informazioni sulle applicazioni che supportano la personalizzazione della barra multifunzione, vedere [Panoramica della barra multifunzione](../vsto/ribbon-overview.md).  
  
-   Personalizzare la barra multifunzione di un'applicazione di Office usando la finestra di progettazione della barra multifunzione. Per altre informazioni, vedere [Ribbon Designer](../vsto/ribbon-designer.md).  
  
-   Creare un riquadro azioni personalizzato. Per altre informazioni, vedere [Actions Pane Overview](../vsto/actions-pane-overview.md).  
  
-   Personalizzare l'interfaccia utente di Microsoft Office Outlook usando le aree del modulo di Outlook. Per ulteriori informazioni, vedere [procedura dettagliata: progettazione di un'area del modulo di Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)   
 [Barra multifunzione XML](../vsto/ribbon-xml.md)   
 [Procedura dettagliata: creazione di una scheda personalizzata mediante la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)  
  
  