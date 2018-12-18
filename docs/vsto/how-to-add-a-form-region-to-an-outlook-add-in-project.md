---
title: 'Procedura: aggiungere un''area del modulo a un progetto di componente aggiuntivo di Outlook | Documenti Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VSTO.NewFormRegionWizard.Page1
- VSTO.NewFormRegionWizard.Page3
- VSTO.NewFormRegionWizard.Page2
- VSTO.NewFormRegionWizard.Page0
dev_langs:
- VB
- CSharp
helpviewer_keywords: form regions [Office development in Visual Studio], adding
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 2029b154ca97f2e856a9e6af8ef58b82f4438df6
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-a-form-region-to-an-outlook-add-in-project"></a>Procedura: Aggiungere un'area del modulo a un progetto di componente aggiuntivo per Outlook
  Creare un'area del modulo per estendere un modulo standard o personalizzato di Microsoft Office Outlook usando la procedura guidata **Nuova area del modulo di Outlook** . È possibile creare una nuova area del modulo e progettare l'interfaccia utente in Visual Studio oppure importare un'area del modulo progettata in Outlook e aggiungere codice Visual Basic o C#.  
  
 Un'area del modulo di Outlook di un altro progetto di Outlook può essere riutilizzata nel progetto corrente di componente aggiuntivo VSTO per Outlook con la finestra di dialogo **Aggiungi elemento esistente** . Per altre informazioni, vedere [Creating Outlook Form Regions](../vsto/creating-outlook-form-regions.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
### <a name="to-add-a-new-form-region-to-an-outlook-project"></a>Per aggiungere una nuova area del modulo a un progetto di Outlook  
  
1.  Aprire o creare un progetto di componente aggiuntivo VSTO di Outlook in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Per altre informazioni, vedere [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  In **Esplora soluzioni**selezionare il nodo del progetto di componente aggiuntivo VSTO di Outlook.  
  
3.  Nel menu **Progetto** fare clic su **Aggiungi nuovo elemento**.  
  
4.  Nella finestra di dialogo **Aggiungi nuovo elemento** selezionare **Area del modulo di Outlook**.  
  
5.  Nella casella **Nome** digitare un nome per l'area del modulo, quindi scegliere **Aggiungi**.  
  
     Il **area del modulo NewOutlook** avviata.  
  
6.  Nella pagina **Selezionare la modalità di creazione dell'area del modulo** scegliere se si vuole progettare l'area del modulo trascinando i controlli gestiti in una finestra di progettazione visiva o importare un'area del modulo progettata in Outlook.  
  
    > [!NOTE]  
    >  Se si sceglie di importare un'area del modulo progettata in Outlook, è necessario specificare il percorso di un file OFS (Outlook Form Storage). Non è possibile aggiungere controlli gestiti a un'area del modulo progettata in Outlook, ma solo aggiungere codice associato all'interfaccia utente esistente. Per altre informazioni, vedere [Creating Outlook Form Regions](../vsto/creating-outlook-form-regions.md).  
  
7.  Nella pagina **Selezionare il tipo di area del modulo da creare** esaminare i tipi di area del modulo e selezionarne uno, quindi scegliere **Avanti**. Per altre informazioni sui tipi di area del modulo, vedere [Creating Outlook Form Regions](../vsto/creating-outlook-form-regions.md).  
  
8.  Nella casella **Nome** della pagina **Fornire un testo descrittivo e selezionare le preferenze di visualizzazione** digitare un nome per l'area del modulo. Per i tipi di area del modulo di sostituzione e di sostituzione completa, sono disponibili anche le caselle **Titolo** e **Descrizione** .  
  
     Per informazioni sulla posizione in cui vengono visualizzati il nome, il titolo e la descrizione in Outlook quando si distribuisce l'area del modulo, vedere [Creating Outlook Form Regions](../vsto/creating-outlook-form-regions.md).  
  
9. Selezionare una o più modalità di visualizzazione in cui si vuole visualizzare l'area del modulo.  
  
     Tutti i tipi di area del modulo possono essere visualizzati nei controlli, in modalità composizione (per la creazione di elementi) e in modalità lettura (per la visualizzazione di elementi). I tipi di area del modulo adiacenti, di sostituzione e di sostituzione completa possono essere visualizzati anche nel riquadro di lettura.  
  
10. Scegliere **Avanti**.  
  
11. Nella pagina **Identificare le classi di messaggi per la visualizzazione dell'area del modulo** selezionare le classi messaggio standard di Outlook o digitare i nomi di una o più classi messaggio personalizzate, quindi fare clic su **Fine**. Per altre informazioni, vedere [Associating a Form Region with an Outlook Message Class](../vsto/associating-a-form-region-with-an-outlook-message-class.md).  
  
## <a name="see-also"></a>Vedere anche  
 [L'accesso a un'area del modulo in fase di esecuzione](../vsto/accessing-a-form-region-at-run-time.md)   
 [Soluzioni Outlook](../vsto/outlook-solutions.md)   
 [Creazione di aree del modulo di Outlook](../vsto/creating-outlook-form-regions.md)   
 [Linee guida per la creazione di aree del modulo di Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [Procedura dettagliata: Progettazione di un'area del modulo di Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Procedura dettagliata: Importazione di un'area del modulo progettata in Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)   
 [Azioni personalizzate nelle aree del modulo di Outlook](../vsto/custom-actions-in-outlook-form-regions.md)  
  
  