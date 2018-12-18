---
title: 'Procedura: aggiungere controlli XMLMappedRange a fogli di lavoro | Documenti Microsoft'
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
- XMLMappedRange control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 90050da5f5105ab3be4c42bedb1751d9f1664958
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-xmlmappedrange-controls-to-worksheets"></a>Procedura: aggiungere controlli XMLMappedRange a fogli di lavoro
  Quando si esegue il mapping di un elemento XML a una cella in Microsoft Office Excel, Visual Studio aggiunge automaticamente un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> controllo al foglio di lavoro.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  Il <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> controllo non è disponibile nel **della casella degli strumenti** o **origini dati** finestra. Inoltre, è possibile creare <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> controlli a livello di codice.  
  
### <a name="to-add-an-xmlmappedrange-control-to-a-worksheet"></a>Per aggiungere un controllo XMLMappedRange a un foglio di lavoro  
  
1.  Aprire la cartella di lavoro di Excel nella finestra di progettazione di Visual Studio.  
  
2.  Aprire il foglio di lavoro in cui si desidera aggiungere il controllo.  
  
3.  Nel **Developer** scheda, fare clic su **origine**.  
  
    > [!NOTE]  
    >  Se il **Developer** scheda non è visibile sulla barra multifunzione, è necessario abilitarlo. Per altre informazioni, vedere [How to: Show the Developer Tab on the Ribbon](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
     Il **origine XML** verrà visualizzato il riquadro attività.  
  
4.  Nel **origine XML** riquadro attività fare clic su **mapping XML**.  
  
5.  Nel **mapping XML** la finestra di dialogo, fare clic su **Aggiungi**.  
  
     Il **origine XML** viene visualizzata la finestra di dialogo.  
  
6.  Selezionare uno schema XML dal **origine XML** la finestra di dialogo e fare clic su **aprire**.  
  
     Lo schema viene aggiunto per il **mapping XML** la finestra di dialogo.  
  
7.  Nel **mapping XML** la finestra di dialogo, fare clic su **OK**.  
  
8.  Trascinare un elemento di **origine XML** riquadro attività a una cella del foglio di lavoro.  
  
     Un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> viene creato e aggiunto al progetto.  
  
    > [!NOTE]  
    >  Se si trascina un elemento padre di **origine XML** riquadro attività, un <xref:Microsoft.Office.Tools.Excel.ListObject> controllo viene creato.  
  
## <a name="see-also"></a>Vedere anche  
 [XmlMappedRange (controllo)](../vsto/xmlmappedrange-control.md)   
 [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Procedura: Mappare schemi a fogli di lavoro in Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)  
  
  