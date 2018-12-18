---
title: Accesso alla barra multifunzione in fase di esecuzione | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Globals class, Ribbon
- Ribbon [Office development in Visual Studio], accessing
- RibbonManager class
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a6129779b66406ffe24dbe65e03b289cb917c1ae
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="accessing-the-ribbon-at-run-time"></a>Accesso alla barra multifunzione in fase di esecuzione
  È possibile scrivere codice per mostrare, nascondere o modificare la barra multifunzione e consentire agli utenti di eseguire il codice dai controlli in un riquadro attività personalizzato, un riquadro azioni o un'area del modulo di Outlook.  

 È possibile accedere alla barra multifunzione mediante la classe `Globals`. Per progetti Outlook è possibile accedere alla barra multifunzione che viene visualizzata in una finestra di esplorazione o di controllo di Outlook specifica.  

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  

## <a name="accessing-the-ribbon-by-using-the-globals-class"></a>Accesso alla barra multifunzione usando la classe Globals  
 È possibile usare la classe `Globals` per accedere alla barra multifunzione in un progetto a livello di documento o un progetto di componente aggiuntivo VSTO da qualsiasi posizione nel progetto.  

 Per ulteriori informazioni sul `Globals` classe, vedere [accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md).  

 Il seguente esempio usa la classe `Globals` per accedere a una barra multifunzione personalizzata denominata `Ribbon1` e impostare il testo visualizzato in una casella combinata nella barra multifunzione su `Hello World`.  

 [!code-vb[Trin_Outlook_FR_Access#4](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#4)]
 [!code-csharp[Trin_Outlook_FR_Access#4](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#4)]  

## <a name="accessing-a-collection-of-ribbons-that-appear-in-a-specific-outlook-inspector-window"></a>Accesso a una raccolta di barre multifunzione visualizzate in una finestra di controllo di Outlook specifica  
 È possibile accedere a una raccolta di barre multifunzione visualizzate in Outlook *controlli*. Un controllo rappresenta una finestra che viene aperta in Outlook quando gli utenti eseguono determinate attività, ad esempio la creazione di messaggi di posta elettronica. Per accedere alla barra multifunzione di una finestra di controllo, chiamare la proprietà `Ribbons` della classe `Globals` e passare un oggetto <xref:Microsoft.Office.Interop.Outlook.Inspector> che rappresenta il controllo.  

 Il seguente esempio ottiene una raccolta della barra multifunzione del controllo attualmente attivo. In questo esempio quindi si accede a una barra multifunzione denominata `Ribbon1` e imposta il testo visualizzato su una casella combinata nella barra multifunzione su `Hello World`.  

 [!code-vb[Trin_Outlook_FR_Access#5](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#5)]
 [!code-csharp[Trin_Outlook_FR_Access#5](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#5)]  

## <a name="accessing-a-collection-of-ribbons-that-appear-for-a-specific-outlook-explorer"></a>Accesso a una raccolta di barre multifunzione visualizzate in una finestra di esplorazione di Outlook specifica  
 È possibile accedere a una raccolta di barre multifunzione visualizzate in un Outlook *Esplora*. Una finestra di esplorazione è l'interfaccia utente dell'applicazione principale per un'istanza di Outlook. Per accedere alla barra multifunzione di una finestra di esplorazione, chiamare la proprietà `Ribbons` della classe `Globals` e passare un oggetto <xref:Microsoft.Office.Interop.Outlook.Explorer> che rappresenta la finestra di esplorazione.  

 Il seguente esempio ottiene una raccolta della barra multifunzione della finestra di esplorazione attualmente attiva. In questo esempio quindi si accede a una barra multifunzione denominata `Ribbon1` e imposta il testo visualizzato su una casella combinata nella barra multifunzione su `Hello World`.  

 [!code-vb[Trin_Outlook_FR_Access#6](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#6)]
 [!code-csharp[Trin_Outlook_FR_Access#6](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#6)]  

## <a name="see-also"></a>Vedere anche  
 [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)   
 [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)   
 [Barra multifunzione XML](../vsto/ribbon-xml.md)   
 [Panoramica del modello a oggetti della barra multifunzione](../vsto/ribbon-object-model-overview.md)   
 [Procedura dettagliata: Creazione di una scheda personalizzata usando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Procedura dettagliata: Aggiornamento dei controlli in una barra multifunzione in fase di esecuzione](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [Personalizzazione di una barra multifunzione per Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Accesso a un'area del modulo in fase di esecuzione](../vsto/accessing-a-form-region-at-run-time.md)  
