---
title: Sulla barra multifunzione Panoramica | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- customizing the Ribbon, multiple Ribbons
- Ribbon [Office development in Visual Studio], about Ribbon
- toolbars [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], multiple Ribbons
- toolbars [Office development in Visual Studio]
- custom Ribbon, multiple Ribbons
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: dcd53d1b5d38ff144536f0dea62e441cb2b23072
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="ribbon-overview"></a>Cenni preliminari sulla barra multifunzione
  La barra multifunzione rappresenta uno strumento per organizzare i comandi correlati in modo da semplificarne la ricerca. Sulla barra i comandi vengono visualizzati come controlli, I controlli sono organizzati in *gruppi* lungo una striscia orizzontale all'estremità superiore di una finestra dell'applicazione. I gruppi correlati sono organizzati in schede.  
  
 La maggior parte delle funzionalità che erano accessibili con i menu e le barre degli strumenti nelle versioni precedenti di Microsoft Office ora è accessibile con la barra multifunzione. Per ulteriori informazioni, vedere l'articolo tecnico [Developer panoramica dell'interfaccia utente per Microsoft Office System 2007](http://go.microsoft.com/fwlink/?LinkID=70860).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
## <a name="customizing-the-microsoft-office-ribbon"></a>Personalizzazione della barra multifunzione di Microsoft Office  
 Per personalizzare la barra multifunzione, aggiungere uno dei seguenti elementi della barra al progetto di Office:  
  
-   **Barra multifunzione (finestra di progettazione visiva)**  
  
-   **Barra multifunzione (XML)**  
  
 Ad esempio, per personalizzare la barra multifunzione di Excel, aggiungere un elemento di tale barra a un progetto di componente aggiuntivo VSTO per Excel.  
  
### <a name="ribbon-visual-designer-item"></a>Elemento Barra multifunzione (finestra di progettazione visiva)  
 Il **della barra multifunzione (finestra di progettazione visiva)** elemento fornisce strumenti avanzati che semplificano la progettazione e lo sviluppo di una barra multifunzione personalizzata. Utilizzare il **della barra multifunzione (finestra di progettazione visiva)** elemento per personalizzare la barra multifunzione nei modi seguenti:  
  
-   Aggiunta di schede personalizzate o incorporate a una barra multifunzione  
  
-   Aggiunta di gruppi personalizzati a una scheda personalizzata o incorporata  
  
    > [!NOTE]  
    >  Una scheda o un gruppo incorporato rappresentano una scheda o un gruppo già presenti sulla barra multifunzione di un'applicazione Microsoft Office. Ad esempio, il **dati** scheda è una scheda incorporata in Excel. Il **connessioni** è un gruppo predefinito sul **dati** scheda.  
  
-   Aggiunta di controlli personalizzati a un gruppo personalizzato.  
  
-   Aggiunta di controlli personalizzati alla visualizzazione backstage.  
  
 Per ulteriori informazioni su come personalizzare una barra multifunzione utilizzando il **della barra multifunzione (finestra di progettazione visiva)** elemento, vedere [progettazione della barra multifunzione](../vsto/ribbon-designer.md).  
  
### <a name="ribbon-xml-item"></a>Elemento Barra multifunzione (XML)  
 Utilizzare il **della barra multifunzione (XML)** elemento se si desidera personalizzare la barra multifunzione in modo che non è supportato dal **della barra multifunzione (finestra di progettazione visiva)** elemento. Utilizzare il **della barra multifunzione (XML)** elemento per personalizzare la barra multifunzione nei modi seguenti:  
  
-   Aggiungere *incorporato* gruppi per una scheda personalizzata o incorporata.  
  
-   Aggiunta di controlli incorporati a un gruppo personalizzato.  
  
-   Aggiunta di codice personalizzato per eseguire l'override dei gestori eventi dei controlli incorporati.  
  
-   Personalizzazione della barra di accesso rapido.  
  
-   Condivisione di una personalizzazione della barra multifunzione tra diversi componenti aggiuntivi VSTO usando un ID completo.  
  
 Per ulteriori informazioni su come personalizzare la barra multifunzione utilizzando il **della barra multifunzione (XML)** elemento, vedere [XML della barra multifunzione](../vsto/ribbon-xml.md).  
  
## <a name="exporting-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Esportazione di una barra multifunzione dalla finestra di progettazione in un elemento XML della barra  
 Se si crea una barra multifunzione utilizzando la finestra di progettazione della barra multifunzione e quindi decidere che si desidera personalizzare la barra multifunzione in modo che il **della barra multifunzione (finestra di progettazione visiva)** l'elemento non supporta, è possibile esportare la barra multifunzione in XML.  
  
 Visual Studio crea automaticamente un **della barra multifunzione (XML)** elemento e il file XML della barra multifunzione con elementi e attributi per ogni controllo sulla barra multifunzione viene popolato.  
  
 Non tutte le proprietà presenti il **proprietà** finestra di progettazione della barra multifunzione vengono trasferite nel file XML della barra multifunzione.  Ad esempio, Visual Studio non esportare il valore di **immagine** o **testo** proprietà. Questa situazione si verifica perché è necessario creare un metodo di callback nel file di codice della barra multifunzione del progetto esportato per assegnare un'immagine o impostare il testo di un controllo. In Visual Studio non vengono generati automaticamente metodi di callback come parte del processo di esportazione.  
  
 In più, i valori di proprietà predefiniti rimasti invariati non vengono visualizzati nel file XML risultante della barra multifunzione.  
  
 Per ulteriori informazioni su come esportare la barra multifunzione in XML, vedere [procedura: esportare una barra multifunzione dalla finestra di progettazione della barra multifunzione in XML della barra multifunzione](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md).  
  
### <a name="updating-the-code"></a>Aggiornamento del codice  
 Viene aggiunto un nuovo file di codice della barra multifunzione per **Esplora**. Questo file contiene la classe XML della barra multifunzione. È necessario creare metodi di callback nell'area `Ribbon Callbacks` di questa classe per gestire le azioni dell'utente, ad esempio la selezione di un pulsante. Spostare il codice dai gestori eventi in questi metodi di callback e modificarlo in modo che usi il modello di programmazione di estendibilità della barra multifunzione (RibbonX). Per altre informazioni, vedere [Ribbon XML](../vsto/ribbon-xml.md).  
  
 È inoltre necessario aggiungere codice per il `ThisAddIn`, `ThisWorkbook`, o `ThisDocument` che esegue l'override del metodo CreateRibbonExtensibilityObject e restituisce la classe Ribbon XML all'applicazione di Office.  
  
 Per altre informazioni, vedere [Ribbon XML](../vsto/ribbon-xml.md).  
  
## <a name="adding-multiple-ribbon-items-to-a-project"></a>Aggiunta di più elementi della barra multifunzione a un progetto  
 È possibile aggiungere più elementi della barra multifunzione a un singolo progetto. Questa operazione è utile per eseguire una delle due attività seguenti:  
  
-   Creazione di barre multifunzione per Outlook *controlli*. Per ulteriori informazioni, vedere [personalizzazione di una barra multifunzione per Outlook](../vsto/customizing-a-ribbon-for-outlook.md).  
  
    > [!NOTE]  
    >  Un controllo rappresenta una finestra che viene aperta quando gli utenti eseguono determinate attività, ad esempio la creazione di un messaggio di posta elettronica.  
  
-   Selezione della barra multifunzione da visualizzare in fase di esecuzione.  
  
### <a name="selecting-which-ribbons-to-display-at-run-time"></a>Selezione delle barre multifunzione da visualizzare in fase di esecuzione.  
 Dal momento che un progetto può contenere più barre multifunzione, è possibile selezionare quella da visualizzare in fase di esecuzione.  
  
 Per selezionare una barra multifunzione da visualizzare in fase di esecuzione, eseguire l'override del metodo CreateRibbonExtensibilityObject nella `ThisAddin`, `ThisWorkbook`, o `ThisDocument` classe del progetto e restituire la barra multifunzione che si desidera visualizzare. L'esempio seguente controlla il valore di un campo denominato `myCondition` e viene restituita la barra multifunzione appropriata.  
  
> [!NOTE]  
>  La sintassi utilizzata in questo esempio restituisce una barra multifunzione che è stata creata utilizzando il **della barra multifunzione (finestra di progettazione visiva)** elemento. La sintassi per la restituzione di una barra multifunzione che viene creata utilizzando un **della barra multifunzione (XML)** elemento è leggermente diverso. Per ulteriori informazioni sulla restituzione di un **della barra multifunzione (XML)** elemento, vedere [XML della barra multifunzione](../vsto/ribbon-xml.md).  
  
 Aggiungere il codice seguente:  
  
 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_ribbon_choose_ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_ribbon_choose_ribbon_4/ThisWorkbook.cs#1)]  
  
### <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Procedura: Iniziare a personalizzare la barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md)|Viene illustrato come personalizzare la barra multifunzione di un'applicazione di Microsoft Office, aggiungere un **della barra multifunzione (finestra di progettazione visiva)** o **della barra multifunzione (XML)** elemento a un progetto di Office.|  
|[Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)|Descrive come usare la finestra di progettazione della barra multifunzione per aggiungere schede, gruppi e controlli personalizzati alla barra multifunzione di un'applicazione di Microsoft Office.|  
|[Procedura dettagliata: creazione di una scheda personalizzata mediante la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Illustra come creare una scheda personalizzata della barra multifunzione usando la finestra di progettazione della barra multifunzione. Questa finestra di progettazione può essere usata per aggiungere e posizionare controlli sulla scheda personalizzata.|  
|[Panoramica del modello a oggetti della barra multifunzione](../vsto/ribbon-object-model-overview.md)|Fornisce una panoramica di un modello a oggetti fortemente tipizzato per ottenere e impostare le proprietà dei controlli della barra multifunzione in fase di esecuzione.|  
|[Procedura dettagliata: aggiornamento dei controlli di una barra multifunzione in fase di esecuzione](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)|Illustra come usare il modello a oggetti della barra multifunzione per aggiornare i controlli di una barra multifunzione dopo che la barra multifunzione è stata caricata nell'applicazione Office.|  
|[Personalizzazione di una barra multifunzione per Outlook](../vsto/customizing-a-ribbon-for-outlook.md)|Fornisce materiale sussidiario per personalizzare la barra multifunzione in Microsoft Office Outlook.|  
|[Personalizzazione di una barra multifunzione per InfoPath](../vsto/customizing-a-ribbon-for-infopath.md)|Fornisce materiale sussidiario per personalizzare la barra multifunzione in Microsoft Office InfoPath.|  
|[Accesso alla barra multifunzione in fase di esecuzione](../vsto/accessing-the-ribbon-at-run-time.md)|Illustra come mostrare, nascondere o modificare la barra multifunzione e consentire agli utenti di eseguire il codice dai controlli in un riquadro attività personalizzato, un riquadro azioni o un'area del modulo di Outlook.|  
|[Procedura: Modificare la posizione di una scheda nella barra multifunzione](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)|Illustra come modificare l'ordine delle schede nella barra multifunzione.|  
|[Procedura: Personalizzare una scheda predefinita](../vsto/how-to-customize-a-built-in-tab.md)|Illustra come aggiungere gruppi e controlli a una scheda incorporata.|  
|[Procedura: Aggiungere controlli alla visualizzazione Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)|Viene illustrato come aggiungere controlli al menu visualizzato quando si sceglie il **File**.|  
|[Procedura: Aggiungere un pulsante di visualizzazione della finestra di dialogo a un gruppo della barra multifunzione](../vsto/how-to-add-a-dialog-box-launcher-to-a-ribbon-group.md)|Illustra come aggiungere un pulsante di visualizzazione della finestra di dialogo a qualsiasi gruppo della barra multifunzione.|  
|[Procedura: Esportare una barra multifunzione dalla finestra di progettazione in un XML della barra multifunzione](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)|Illustra come personalizzare la barra multifunzione in modalità avanzate esportandola dalla finestra di progettazione nell'elemento XML della barra multifunzione.|  
|[XML della barra multifunzione](../vsto/ribbon-xml.md)|Descrive come è possibile personalizzare una barra multifunzione usando l'elemento XML della barra multifunzione.|  
|[Procedura dettagliata: creazione di una scheda personalizzata mediante la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Di seguito viene illustrato come creare una scheda della barra multifunzione personalizzata utilizzando il **della barra multifunzione (XML)** elemento.|  
  
  