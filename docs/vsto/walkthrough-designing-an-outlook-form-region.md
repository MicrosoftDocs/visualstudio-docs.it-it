---
title: 'Procedura dettagliata: Progettazione di un''area del modulo di Outlook | Documenti Microsoft'
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
helpviewer_keywords: form regions [Office development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: afe17d19ebe87d34ae4857b1477be6cb3e894bb7
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-designing-an-outlook-form-region"></a>Procedura dettagliata: progettazione di un'area del modulo di Outlook
  Le aree del modulo personalizzate estendono i moduli standard o personalizzati di Microsoft Office Outlook. In questa procedura dettagliata verrà progettata un'area del modulo personalizzata che viene visualizzata come una nuova pagina nella finestra di controllo di un contatto. Quest'area del modulo visualizza una mappa di ogni indirizzo elencato per il contatto, inviando le informazioni sull'indirizzo al sito Web di ricerca locale di Windows Live. Per informazioni sulle aree del modulo, vedere [la creazione di aree del modulo di Outlook](../vsto/creating-outlook-form-regions.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 Questa procedura dettagliata illustra le attività seguenti:  
  
-   Creazione di un nuovo progetto di componente aggiuntivo VSTO per Outlook.  
  
-   Aggiunta di un'area del modulo al progetto di componente aggiuntivo VSTO.  
  
-   Progettazione del layout dell'area del modulo.  
  
-   Personalizzazione del comportamento dell'area del modulo.  
  
-   Test dell'area del modulo di Outlook.  
  
> [!NOTE]  
>  I nomi o i percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] o [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)].  
  
 ![collegamento a video](../vsto/media/playvideo.gif "collegamento a video") per una versione video di questo argomento, vedere [procedura Video: progettazione di un'area del modulo di Outlook](http://go.microsoft.com/fwlink/?LinkID=140824).  
  
## <a name="creating-a-new-outlook-vsto-add-in-project"></a>Creazione di un nuovo progetto di componente aggiuntivo VSTO di Outlook  
 Creare prima un progetto di componente aggiuntivo VSTO di base.  
  
#### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>Per creare un nuovo progetto di componente aggiuntivo VSTO di Outlook  
  
1.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], creare un progetto di componente aggiuntivo VSTO di Outlook con il nome **MapItAddIn**.  
  
2.  Nella finestra di dialogo **Nuovo progetto** selezionare **Crea directory per soluzione**.  
  
3.  Salvare il progetto in qualsiasi directory.  
  
     Per altre informazioni, vedere [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
## <a name="adding-a-form-region-to-the-outlook-vsto-add-in-project"></a>Aggiunta di un'area del modulo al progetto di componente aggiuntivo VSTO di Outlook  
 Una soluzione di componente aggiuntivo VSTO di Outlook può contenere uno o più elementi dell'area del modulo di Outlook. Aggiungere un elemento area del modulo al progetto utilizzando il **nuova area del modulo di Outlook** procedura guidata.  
  
#### <a name="to-add-a-form-region-to-the-outlook-vsto-add-in-project"></a>Per aggiungere un'area del modulo al progetto di componente aggiuntivo VSTO di Outlook  
  
1.  In **Esplora**, selezionare il **MapItAddIn** progetto.  
  
2.  Nel menu **Progetto** fare clic su **Aggiungi nuovo elemento**.  
  
3.  Nel **Aggiungi nuovo elemento** nella finestra di dialogo **area del modulo di Outlook**, denominare il file **MapIt**, quindi fare clic su **Aggiungi**.  
  
     Il **area del modulo NewOutlook** avviata.  
  
4.  Nel **selezionare come si desidera creare l'area del modulo** pagina, fare clic su **Progetta nuova area del modulo**, quindi fare clic su **Avanti**.  
  
5.  Nel **selezionare il tipo di area del modulo che si desidera creare** pagina, fare clic su **separato**e quindi fare clic su **Avanti**.  
  
     Oggetto *separato* area del modulo aggiunge una nuova pagina a un modulo di Outlook. Per altre informazioni sui tipi di area del modulo, vedere [Creating Outlook Form Regions](../vsto/creating-outlook-form-regions.md).  
  
6.  Nel **fornire un testo descrittivo e selezionare le preferenze di visualizzazione** , digitare **Map It** nel **nome** casella.  
  
     Questo nome viene visualizzato sulla barra multifunzione della finestra del controllo quando il contatto è aperto.  
  
7.  Selezionare **controlli che sono in modalità composizione** e **controlli in modalità lettura**, quindi fare clic su **Avanti**.  
  
8.  Nel **identificare le classi di messaggi che consente di visualizzare l'area del modulo** pagina deseleziona **messaggio di posta elettronica**selezionare **contatto**e quindi fare clic su **fine**.  
  
     Un file MapIt.cs o MapIt.vb viene aggiunto al progetto.  
  
## <a name="designing-the-layout-of-the-form-region"></a>Progettazione del layout dell'area del modulo  
 Sviluppare visivamente le aree del modulo usando il *Progettazione aree di form*. È possibile trascinare i controlli gestiti sull'area di progettazione aree del modulo. Utilizzare la finestra di progettazione e **proprietà** modificare il layout dei controlli e l'aspetto della finestra.  
  
#### <a name="to-design-the-layout-of-the-form-region"></a>Per progettare il layout dell'area del modulo  
  
1.  In **Esplora**, espandere il **MapItAddIn** del progetto e quindi fare doppio clic su MapIt.cs o MapIt. vb per aprire Progettazione aree di modulo.  
  
2.  Pulsante destro del mouse nella finestra di progettazione e quindi fare clic su **proprietà**.  
  
3.  Nel **proprietà** finestra impostare **dimensioni** a **664, 469**.  
  
     Ciò garantisce che l'area del modulo sia sufficiente grande per visualizzare una mappa.  
  
4.  Scegliere **Casella degli strumenti** dal menu **Visualizza**.  
  
5.  Dal **controlli comuni** scheda della finestra di **della casella degli strumenti**, aggiungere un **WebBrowser** all'area del modulo.  
  
     Il **WebBrowser** visualizzerà una mappa di ogni indirizzo elencato per il contatto.  
  
## <a name="customizing-the-behavior-of-the-form-region"></a>Personalizzazione del comportamento dell'area del modulo  
 Aggiungere codice ai gestori eventi dell'area del modulo per personalizzare il modo in cui un'area del modulo si comporta in fase di esecuzione. Per questa area del modulo il codice esamina le proprietà di un elemento di Outlook e determina se visualizzare l'area del modulo Map It. Se viene visualizzata l'area del modulo, il codice consente di passare alla ricerca locale di Windows Live e caricare una mappa di ogni indirizzo elencato nel contatto di Outlook.  
  
#### <a name="to-customize-the-behavior-of-the-form-region"></a>Per personalizzare il comportamento dell'area del modulo  
  
1.  In **Esplora**, fare clic destro del mouse su MapIt.cs o MapIt. vb e quindi fare clic su **Visualizza codice**.  
  
     MapIt.cs o MapIt.vb viene aperto nell'Editor di codice.  
  
2.  Espandere il **Factory area del modulo** area di codice.  
  
     La classe della factory area del modulo denominata `MapItFactory` viene esposta.  
  
3.  Aggiungere il codice seguente al gestore eventi `MapItFactory_FormRegionInitializing`. Questo gestore eventi viene chiamato quando l'utente apre un contatto. Il codice seguente determina se il contatto contiene un indirizzo. Se il contatto non contiene un indirizzo, questo codice imposta il <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> proprietà del <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> classe **true** e non viene visualizzata l'area del modulo. In alternativa, il componente aggiuntivo VSTO genere l'evento <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> e visualizza l'area del modulo.  
  
     [!code-csharp[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#1)]
     [!code-vb[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#1)]  
  
4.  Aggiungere il codice seguente al gestore eventi <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing>. Mediante il codice vengono effettuate le seguenti attività:  
  
    -   Concatena ogni indirizzo nel contatto e crea una stringa URL.  
  
    -   Chiama il metodo <xref:System.Windows.Forms.WebBrowser.Navigate%2A> dell'oggetto <xref:System.Windows.Forms.WebBrowser> e passa la stringa URL come parametro.  
  
     Il sito Web di ricerca locale viene visualizzato nell'area del modulo Map It e presenta ogni indirizzo nel riquadro di lavoro.  
  
     [!code-csharp[Trin_Outlook_FR_Separate#2](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#2)]
     [!code-vb[Trin_Outlook_FR_Separate#2](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#2)]  
  
## <a name="testing-the-outlook-form-region"></a>Test dell'area del modulo di Outlook  
 Quando si esegue il progetto, Visual Studio apre Outlook. Aprire un contatto per visualizzare l'area del modulo Map It. L'area del modulo Map It viene visualizzata nel modulo di qualsiasi contatto che contiene un indirizzo.  
  
#### <a name="to-test-the-map-it-form-region"></a>Per eseguire il test dell'area del modulo Map It  
  
1.  Premere F5 per eseguire il progetto.  
  
     Viene aperto Outlook.  
  
2.  In Outlook, nel **Home** scheda, fare clic su **nuovi elementi**, quindi fare clic su **contatto**.  
  
3.  Nel modulo del contatto digitare **Ann Beebe** come contatto nome e quindi specificare i tre indirizzi seguenti.  
  
    |Tipo di indirizzo|Indirizzo|  
    |------------------|-------------|  
    |**Business**|**Base a Roma, NY di 4567 Main St.**|  
    |**Home Page**|**Base a Roma, NY di 1234 settentrionale Sig.**|  
    |**Altro**|**3456 Main St. Seattle, WA**|  
  
4.  Salvare e chiudere il contatto.  
  
5.  Aprire nuovamente la **Ann Beebe** contatto.  
  
6.  Nel **Mostra** gruppo della barra multifunzione dell'elemento, fare clic su **Map It** per aprire l'area del modulo Map It.  
  
     Viene visualizzata l'area del modulo Map It insieme al sito Web di ricerca locale. Il **Business**, **Home**, e **altri** indirizzi vengono visualizzati nel riquadro di lavoro. Nel riquadro di lavoro selezionare un indirizzo da mappare.  
  
## <a name="next-steps"></a>Passaggi successivi  
 È possibile trovare altre informazioni sulla personalizzazione dell'interfaccia utente di un'applicazione di Outlook negli argomenti seguenti:  
  
-   Per altre informazioni sulla personalizzazione della barra multifunzione di un elemento Outlook, vedere [Customizing a Ribbon for Outlook](../vsto/customizing-a-ribbon-for-outlook.md).  
  
## <a name="see-also"></a>Vedere anche  
 [L'accesso a un'area del modulo in fase di esecuzione](../vsto/accessing-a-form-region-at-run-time.md)   
 [Creazione di aree del modulo di Outlook](../vsto/creating-outlook-form-regions.md)   
 [Linee guida per la creazione di aree del modulo di Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [Procedura dettagliata: Importazione di un'area del modulo progettata in Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)   
 [Procedura: aggiungere un'area del modulo a un progetto di componente aggiuntivo di Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Associazione di un'area del modulo a una classe messaggio di Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)   
 [Azioni personalizzate nelle aree del modulo di Outlook](../vsto/custom-actions-in-outlook-form-regions.md)   
 [Procedura: Impedire la visualizzazione di un'area del modulo in Outlook](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)  
  
  