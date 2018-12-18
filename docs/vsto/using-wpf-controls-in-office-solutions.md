---
title: Utilizzo di controlli WPF nelle soluzioni Office | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d4aa0fce1700f6608d36231a3ab38db97e5ce826
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="using-wpf-controls-in-office-solutions"></a>Utilizzo dei controlli WPF nelle soluzioni Office
  Anche se le soluzioni create tramite gli strumenti di sviluppo di Office in Visual Studio sono progettate per essere usate direttamente con i controlli Windows Form, è possibile usare anche i controlli WPF nelle soluzioni. Windows Presentation Foundation (WPF) è un'alternativa a Windows Form per progettare interfacce utente. In WPF viene usato un linguaggio di markup, denominato Extensible Application Markup Language (XAML), che offre nuove tecniche per l'incorporazione di interfacce utente, supporti e documenti. Per ulteriori informazioni, vedere [Introduzione a WPF in Visual Studio 2015](/dotnet/framework/wpf/getting-started/introduction-to-wpf-in-vs).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Qualsiasi elemento dell'interfaccia utente che può contenere i controlli Windows Form in una soluzione Office può ospitare anche i controlli WPF, tra cui:  
  
-   Documenti e fogli di lavoro nelle personalizzazioni a livello di documento.  
  
-   Riquadri azione nelle personalizzazioni a livello di documento.  
  
-   Riquadri attività personalizzati nei componenti aggiuntivi VSTO.  
  
-   Aree del modulo nei componenti aggiuntivi VSTO per Outlook.  
  
## <a name="adding-wpf-controls-to-office-projects-at-design-time"></a>Aggiunta di controlli WPF a progetti Office in fase di progettazione  
 Non è possibile aggiungere i controlli WPF direttamente agli elementi dell'interfaccia utente nelle soluzioni Office. Aggiungere invece un **controllo utente (WPF)** elemento al progetto e usarlo come area di progettazione per i controlli WPF. Aggiungere quindi il controllo utente WPF a un elemento dell'interfaccia utente nel progetto.  
  
#### <a name="to-add-wpf-controls-to-an-actions-pane-custom-task-pane-or-form-region"></a>Per aggiungere i controlli WPF a un riquadro azioni, un riquadro attività personalizzato o un'area del modulo  
  
1.  Aprire un progetto al quale si vuole aggiungere un riquadro attività personalizzato, un riquadro azioni o un'area del modulo.  
  
2.  Aggiungere un **controllo utente (WPF)** elemento al progetto.  
  
3.  Dal **della casella degli strumenti**, aggiungere i controlli WPF all'area di progettazione controllo utente WPF.  
  
     Per impostazione predefinita, quando la finestra di progettazione controlli utente WPF è aperto, il **della casella degli strumenti** contiene solo i controlli WPF.  
  
4.  Compilare il progetto.  
  
5.  Aggiungere un riquadro azioni, un'area del modulo o un riquadro attività personalizzato al progetto:  
  
    -   Le aree del modulo, aggiungere un **area del modulo di Outlook** elemento al progetto. Per ulteriori informazioni, vedere [procedura: aggiungere un'area del modulo a un progetto di componente aggiuntivo di Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
    -   Per i riquadri azioni aggiungere un **controllo riquadro azioni** o **controllo utente** elemento al progetto. Per ulteriori informazioni, vedere [procedura: aggiungere un riquadro azioni ai documenti Word o le cartelle di lavoro di Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md) e [procedura: aggiungere un riquadro azioni ai documenti Word o le cartelle di lavoro di Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).  
  
    -   Per i riquadri attività personalizzati, aggiungere un **controllo utente** elemento al progetto. Per ulteriori informazioni, vedere [procedura: aggiungere un riquadro attività personalizzato a un'applicazione](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).  
  
6.  Dal *ProjectName* **controlli utente WPF** scheda della finestra di **della casella degli strumenti**, trascinare il controllo utente WPF nella finestra di progettazione per il riquadro azioni, l'area del modulo o riquadro attività personalizzato.  
  
     Visual Studio crea automaticamente un oggetto <xref:System.Windows.Forms.Integration.ElementHost> che contiene il controllo utente WPF nell'elemento dell'interfaccia utente.  
  
7.  Ricompilare il progetto.  
  
#### <a name="to-add-wpf-controls-to-a-document-or-worksheet-in-a-document-level-project"></a>Per aggiungere controlli WPF a un documento o un foglio di lavoro in un progetto a livello di documento  
  
1.  Aprire un progetto a livello di documento per Word o Excel.  
  
2.  Aggiungere un **controllo utente (WPF)** elemento al progetto.  
  
3.  Dal **della casella degli strumenti**, aggiungere i controlli WPF all'area di progettazione controllo utente WPF.  
  
4.  Compilare il progetto.  
  
5.  Aggiungere un **controllo utente** elemento (ovvero, un controllo utente Windows Form) al progetto.  
  
6.  Aprire la finestra di progettazione per il controllo utente Windows Form.  
  
7.  Dal *ProjectName* **controlli utente WPF** scheda della finestra di **della casella degli strumenti**, trascinare il controllo utente WPF nella finestra di progettazione.  
  
     Visual Studio crea automaticamente un oggetto <xref:System.Windows.Forms.Integration.ElementHost> che contiene il controllo utente WPF nel controllo utente Windows Form.  
  
8.  Scrivere il codice che aggiunge a livello di codice il controllo utente Windows Form al documento o alla cartella di lavoro. Per altre informazioni, vedere [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
    > [!NOTE]  
    >  Non è possibile trascinare il controllo utente Windows Form nel documento o nel foglio di lavoro nella finestra di progettazione.  
  
9. Ricompilare il progetto.  
  
## <a name="hosting-wpf-controls-by-using-the-elementhost-class"></a>Hosting dei controlli WPF mediante la classe ElementHost  
 In Visual Studio vengono fornite funzionalità che consentono di usare i controlli Windows Form nelle soluzioni Office, ma non vengono fornite funzionalità simili per i controlli WPF. Ad esempio, è possibile aggiungere controlli Windows Form a documenti e fogli di lavoro in fase di progettazione trascinando i controlli dal **della casella degli strumenti**, o in fase di esecuzione utilizzando i metodi di supporto. Questi strumenti non sono tuttavia disponibili per i controlli WPF.  
  
 I controlli WPF usano la classe <xref:System.Windows.Forms.Integration.ElementHost> come livello di integrazione tra un form o un controllo Windows Form e i controlli WPF. Quando si aggiungono i controlli WPF alla soluzione in fase di progettazione, Visual Studio genera automaticamente un oggetto <xref:System.Windows.Forms.Integration.ElementHost>.  
  
## <a name="wpf-resources"></a>Risorse WPF  
 Per altre informazioni sulle problematiche di progettazione e architettura per l'hosting dei controlli WPF in form e controlli Windows Form, vedere gli argomenti seguenti:  
  
-   [Architettura di input per l'interoperabilità tra Windows Form e WPF](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture)  
  
-   [Mapping di proprietà di Windows Form e WPF](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-property-mapping)  
  
-   [Interoperatività di WPF e Windows Form](/dotnet/framework/wpf/advanced/wpf-and-windows-forms-interoperation)  
  
-   [Controlli Windows Form e controlli WPF equivalenti](/dotnet/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls)  
  
 Per altre informazioni sull'aggiunta dei controlli WPF a form e controlli Windows Form in Visual Studio in fase di progettazione, vedere gli argomenti seguenti:  
  
-   [Procedura dettagliata: Creazione di nuovo contenuto WPF in Windows Form in fase di progettazione](/dotnet/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time)  
  
-   [Procedura dettagliata: Disposizione del contenuto WPF in Windows Form in fase di progettazione](/dotnet/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time)  
  
-   [Procedura dettagliata: Applicazione di stili al contenuto WPF](/dotnet/framework/winforms/advanced/walkthrough-styling-wpf-content)  
  
## <a name="see-also"></a>Vedere anche  
 [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md)   
 [Controlli Windows Form nei documenti di Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Panoramica del riquadro azioni](../vsto/actions-pane-overview.md)   
 [Riquadri attività personalizzati](../vsto/custom-task-panes.md)   
 [Creazione di aree del modulo di Outlook](../vsto/creating-outlook-form-regions.md)   
 [Procedura: aggiungere un riquadro azioni ai documenti Word o le cartelle di lavoro di Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Procedura: aggiungere un riquadro azioni ai documenti Word o le cartelle di lavoro di Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Procedura: aggiungere un riquadro attività personalizzato a un'applicazione](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [Procedura: Aggiungere un'area del modulo a un progetto di componente aggiuntivo per Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)  
  
  