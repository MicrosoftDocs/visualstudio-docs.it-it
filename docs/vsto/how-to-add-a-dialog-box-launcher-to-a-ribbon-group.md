---
title: 'Procedura: aggiungere un pulsante di visualizzazione della finestra di dialogo a un gruppo della barra multifunzione | Documenti Microsoft'
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
- dialog box launcher [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], dialog box launcher
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 49dee3d090e2b7f985fd85a6061dea3a2c204e4a
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Procedura: aggiungere un pulsante di visualizzazione della finestra di dialogo a un gruppo della barra multifunzione
  È possibile aggiungere un pulsante di visualizzazione della finestra di dialogo a qualsiasi gruppo della barra multifunzione. Visualizzazione di una finestra di dialogo è una piccola icona visualizzata in un gruppo. Gli utenti fanno clic sull'icona per aprire finestre di dialogo correlate o riquadri attività che forniscono ulteriori opzioni correlate al gruppo.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Per aggiungere un pulsante di visualizzazione della finestra di dialogo a un gruppo della barra multifunzione  
  
1.  Selezionare il file di codice della barra multifunzione (file con estensione vb o cs) in **Esplora**.  
  
2.  Nel **vista** menu, fare clic su **progettazione**.  
  
3.  Nella finestra di progettazione della barra multifunzione, fare doppio clic su qualsiasi gruppo e quindi fare clic su **Aggiungi DialogBoxLauncher**.  
  
     Aggiungere codice per il <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick> evento del gruppo per aprire una finestra di dialogo personalizzata o incorporata.  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)   
 [Accessing the Ribbon at Run Time](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Procedure dettagliate ed esempi di sviluppo di office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)   
 [Panoramica del modello a oggetti della barra multifunzione](../vsto/ribbon-object-model-overview.md)   
 [Barra multifunzione XML](../vsto/ribbon-xml.md)   
 [Procedura: esportare una barra multifunzione dalla finestra di progettazione della barra multifunzione alla barra multifunzione XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [Procedura: modificare la posizione di una scheda della barra multifunzione](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [Procedura: personalizzare una scheda incorporata](../vsto/how-to-customize-a-built-in-tab.md)   
 [Procedura: aggiungere controlli alla visualizzazione Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Personalizzazione di una barra multifunzione per Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Procedura: iniziare a personalizzare la barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Procedura: visualizzare gli errori dell'interfaccia utente del componente aggiuntivo](../vsto/how-to-show-add-in-user-interface-errors.md)   
 [Procedura dettagliata: Creazione di una scheda personalizzata utilizzando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Procedura dettagliata: Aggiornamento dei controlli in una barra multifunzione in fase di esecuzione](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [Procedura dettagliata: creazione di una scheda personalizzata mediante l'XML della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  