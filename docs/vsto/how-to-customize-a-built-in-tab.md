---
title: 'Procedura: personalizzare una scheda incorporata | Documenti Microsoft'
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
- built-in tabs [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 251c1cf70ab1d528f65d558208f0f2d43e10388a
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-customize-a-built-in-tab"></a>Procedura: personalizzare una scheda incorporata
  È possibile aggiungere gruppi e controlli in una scheda incorporata, cioè una scheda già presente sulla barra multifunzione di un'applicazione di Microsoft Office. Ad esempio, il **dati** scheda è una scheda incorporata in Excel. Quando si crea un gruppo personalizzato, esso viene visualizzato per ultimo nella scheda, ma è possibile spostarlo in un punto qualsiasi della scheda.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
> [!NOTE]  
>  È possibile aggiungere gruppi in una scheda incorporata, ma non è possibile rimuovere gruppi incorporati da una scheda incorporata.  
  
### <a name="to-add-groups-to-a-built-in-tab"></a>Per aggiungere gruppi in una scheda incorporata  
  
1.  Il file di codice della barra multifunzione in **Esplora**, quindi fare clic su **Visualizza finestra di progettazione**.  
  
    > [!NOTE]  
    >  Se non viene visualizzato il file di codice della barra multifunzione **Esplora**, è necessario aggiungere un **elemento barra multifunzione** al progetto. Vedere [procedura: iniziare a personalizzare la barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
2.  Fare doppio clic su una scheda nella finestra di progettazione della barra multifunzione e quindi fare clic su **proprietà**.  
  
3.  Nel **proprietà** finestra, espandere il **ControlId** proprietà e quindi impostare il **ControlIdType** proprietà **Office**.  
  
4.  Impostare il **OfficeId** proprietà per il *ID controllo* della scheda incorporata che si desidera personalizzare.  
  
     L'ID di controllo è il nome che identifica in modo univoco le schede, i gruppi e i controlli incorporati nelle applicazioni Microsoft Office.  
  
     Per un elenco ID di controllo, vedere [file della Guida di Office 2010: identificatori utente Office Fluent interfaccia controllo](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
5.  Dal **controlli della barra multifunzione di Office** scheda della finestra il **della casella degli strumenti**, trascinare i gruppi nella scheda.  
  
    > [!NOTE]  
    >  I gruppi incorporati non sono visualizzati nella finestra di progettazione. Pertanto, l'unico modo per determinare se si sta utilizzando una scheda incorporata consiste nell'esaminare il **ControlId** proprietà della scheda.  
  
### <a name="to-position-groups-on-a-built-in-tab"></a>Per posizionare gruppi in una scheda incorporata  
  
1.  Selezionare un gruppo personalizzato nella finestra di progettazione della barra multifunzione.  
  
2.  Nel **proprietà** finestra, espandere il **posizione** proprietà.  
  
3.  Impostare il **PositionType** proprietà sul valore appropriato:  
  
    -   **BeforeOfficeId** posiziona il gruppo prima di un determinato gruppo incorporato.  
  
    -   **AfterOfficeId** posiziona il gruppo dopo un determinato gruppo incorporato.  
  
4.  Impostare il **OfficeId** proprietà ID di controllo di un gruppo incorporato.  
  
     Per un elenco ID di controllo, vedere [file della Guida di Office 2010: identificatori utente Office Fluent interfaccia controllo](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)   
 [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)   
 [Barra multifunzione XML](../vsto/ribbon-xml.md)   
 [Procedura dettagliata: Creazione di una scheda personalizzata utilizzando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Procedura dettagliata: Creazione di una scheda personalizzata utilizzando la barra multifunzione XML](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)   
 [Procedura: iniziare a personalizzare la barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Procedura: modificare la posizione di una scheda della barra multifunzione](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [Procedura: aggiungere controlli alla visualizzazione Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Procedura: Visualizzare gli errori dell'interfaccia utente del componente aggiuntivo](../vsto/how-to-show-add-in-user-interface-errors.md)  
  
  