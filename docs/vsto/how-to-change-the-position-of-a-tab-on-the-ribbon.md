---
title: 'Procedura: modificare la posizione di una scheda della barra multifunzione | Documenti Microsoft'
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
helpviewer_keywords: Ribbon [Office development in Visual Studio], tabs
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 5016651a6cc4f1316536c22d555a65aaba64b788
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-change-the-position-of-a-tab-on-the-ribbon"></a>Procedura: modificare la posizione di una scheda nella barra multifunzione
  È possibile modificare l'ordine delle schede personalizzate in una barra multifunzione utilizzando il **scheda Editor della raccolta**. È possibile posizionare le schede personalizzate prima o dopo una scheda incorporata nella barra multifunzione. Una scheda incorporata rappresenta una scheda già presente sulla barra multifunzione di un'applicazione di Microsoft Office. Ad esempio, il **dati** scheda è una scheda incorporata in Excel.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-change-the-order-of-tabs-on-the-ribbon"></a>Per modificare l'ordine delle schede sulla barra multifunzione  
  
1.  Selezionare il file di codice della barra multifunzione (file con estensione vb o cs) in **Esplora**.  
  
2.  Nel **vista** menu, fare clic su **progettazione**.  
  
3.  Fare clic sulla finestra di progettazione della barra multifunzione e quindi fare clic su **proprietà**.  
  
4.  Nel **proprietà** finestra, seleziona il **schede** , proprietà e quindi fare clic sul pulsante con puntini di sospensione (![ellisse di ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "ASP.NET per dispositivi mobili Ellisse progettazione")).  
  
     Il **scheda Editor della raccolta** viene visualizzato.  
  
5.  Nel **scheda Editor della raccolta**nella **membri** elenco, selezionare la scheda che si desidera spostare e fare clic sulla freccia in giù per modificare l'ordine di tabulazione.  
  
### <a name="to-position-a-tab-before-or-after-a-built-in-tab-on-the-ribbon"></a>Per posizionare una scheda prima o dopo una scheda incorporata nella barra multifunzione  
  
1.  Nella finestra di progettazione della barra multifunzione, selezionare una scheda personalizzata.  
  
2.  Nel **proprietà** finestra, espandere il **ControlId** proprietà, quindi assicurarsi che il valore del **ControlIdType** è impostata su **personalizzato**.  
  
3.  Nel **proprietà** finestra, espandere il **posizione** proprietà.  
  
4.  Impostare il **PositionType** proprietà sul valore appropriato:  
  
    -   **BeforeOfficeId** posiziona il gruppo prima di una determinata scheda incorporata.  
  
    -   **AfterOfficeId** posiziona il gruppo dopo una determinata scheda incorporata.  
  
5.  Impostare il **OfficeId** proprietà ID di controllo di una scheda incorporata.  
  
     Per un elenco ID di controllo, vedere [file della Guida di Office 2010: identificatori utente Office Fluent interfaccia controllo](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)   
 [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)   
 [Barra multifunzione XML](../vsto/ribbon-xml.md)   
 [Procedura dettagliata: Creazione di una scheda personalizzata utilizzando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Procedura dettagliata: creazione di una scheda personalizzata mediante l'XML della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  