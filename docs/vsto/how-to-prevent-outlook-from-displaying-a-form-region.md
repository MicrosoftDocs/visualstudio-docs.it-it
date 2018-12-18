---
title: "Procedura: impedire la visualizzazione di un'area del modulo Outlook | Documenti Microsoft"
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], canceling display
- canceling form region display
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a5fffde6cd92d490df2a5567763da77e723ed4f3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-prevent-outlook-from-displaying-a-form-region"></a>Procedura: impedire la visualizzazione di un'area del modulo in Outlook
  Potrebbero esistere situazioni in cui si desidera non Microsoft Office Outlook per visualizzare un'area del modulo per un particolare elemento. Se, ad esempio, un contatto non contiene un indirizzo aziendale, è possibile impedire un'area del modulo che mostra la posizione dell'azienda in una mappa.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
### <a name="to-prevent-outlook-from-displaying-a-form-region"></a>Per impedire la visualizzazione di un'area del modulo di Outlook  
  
1.  Aprire il file di codice per l'area del modulo che si desidera modificare.  
  
2.  Espandere il **Factory area del modulo** area di codice.  
  
3.  Aggiungere codice per il `FormRegionInitializing` gestore eventi che imposta il <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> proprietà del <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> classe **true**.  
  
 In questo esempio, se il contatto non contiene un indirizzo, il <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> è impostata su **true**, e non viene visualizzata l'area del modulo.  
  
## <a name="example"></a>Esempio  
 [!code-csharp[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#1)]
 [!code-vb[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#1)]  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di aree del modulo di Outlook](../vsto/creating-outlook-form-regions.md)   
 [Procedura dettagliata: Progettazione di un'area del modulo di Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Procedura: aggiungere un'area del modulo a un progetto di componente aggiuntivo di Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Procedura dettagliata: Progettazione di un'area del modulo di Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Procedura dettagliata: importazione di un'area del modulo progettata in Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  