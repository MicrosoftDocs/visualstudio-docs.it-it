---
title: 'Procedura: esportare una barra multifunzione dalla finestra di progettazione della barra multifunzione alla barra multifunzione XML | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, XML
- customizing the Ribbon, XML
- Ribbon [Office development in Visual Studio], XML
- Ribbon [Office development in Visual Studio], exporting
- XML [Office development in Visual Studio], Ribbon
- Ribbon Designer [Office development in Visual Studio]
- exporting Ribbon
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7aff56d1d7ee3533a83ef3edbdd8ba9271efd862
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Procedura: esportare una barra multifunzione dalla finestra di progettazione in un elemento XML della barra
  Il **della barra multifunzione (finestra di progettazione visiva)** elemento non supporta tutti i possibili tipi di personalizzazione della barra multifunzione. Per personalizzare la barra multifunzione in modalità avanzate, è possibile esportare la barra multifunzione dalla finestra di progettazione XML della barra multifunzione e modificare direttamente il file XML.  
  
> [!NOTE]  
>  Non tutti i valori di proprietà visualizzate nel file XML della barra multifunzione. Per ulteriori informazioni, vedere [Panoramica della barra multifunzione](../vsto/ribbon-overview.md).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Per esportare una barra multifunzione dalla finestra di progettazione della barra multifunzione in XML della barra multifunzione  
  
1.  Il file di codice della barra multifunzione in **Esplora**, quindi fare clic su **Visualizza finestra di progettazione**.  
  
2.  Fare clic sulla finestra di progettazione della barra multifunzione e quindi fare clic su **Esporta barra multifunzione in XML**.  
  
     Visual Studio aggiunge un file XML della barra multifunzione e un file di codice XML della barra multifunzione al progetto.  
  
3.  Nel codice della barra multifunzione, individuare i commenti che iniziano con `TODO:`.  
  
4.  Copiare il blocco di codice in questi commenti per la **ThisAddin**, **ThisWorkbook**, o **ThisDocument** classe, a seconda di quale tipo di soluzione che stai sviluppando.  
  
     Questo codice consente all'applicazione di Microsoft Office di individuare e caricare la barra multifunzione personalizzata. Per altre informazioni, vedere [Ribbon XML](../vsto/ribbon-xml.md).  
  
5.  Nel **ThisAddin**, **ThisWorkbook**, o **ThisDocument** classe, rimuovere il commento il blocco di codice.  
  
     Dopo che si rimuove il commento nel codice, dovrebbe essere simile l'esempio seguente. In questo esempio viene chiamata la classe Ribbon `MyRibbon`.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]  
  
6.  Passare al file di codice XML della barra multifunzione e cercare il `Ribbon Callbacks` area.  
  
     Si tratta in cui scrivere metodi di callback per gestire le azioni utente, ad esempio un pulsante.  
  
7.  Creare un metodo di callback per ogni gestore eventi che è stato scritto il codice di progettazione della barra multifunzione.  
  
8.  Spostare tutto il codice dai gestori eventi per i metodi di callback e modificare il codice per funzionare con la Ribbon extensibility (RibbonX) nel modello di programmazione.  
  
     Per informazioni sulla scrittura di metodi di callback e l'utilizzo del modello di programmazione RibbonX, vedere [XML della barra multifunzione](../vsto/ribbon-xml.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)   
 [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)   
 [Barra multifunzione XML](../vsto/ribbon-xml.md)   
 [Procedura dettagliata: Creazione di una scheda personalizzata usando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Procedura dettagliata: creazione di una scheda personalizzata mediante l'XML della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  