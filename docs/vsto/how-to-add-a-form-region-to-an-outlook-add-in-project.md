---
title: "Procedura: Aggiungere un'area del modulo a un progetto di componente aggiuntivo di Outlook"
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VSTO.NewFormRegionWizard.Page1
- VSTO.NewFormRegionWizard.Page3
- VSTO.NewFormRegionWizard.Page2
- VSTO.NewFormRegionWizard.Page0
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], adding
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c1a9c9201050bf4ccb3bd6beb2ada837c2b808b4
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255968"
---
# <a name="how-to-add-a-form-region-to-an-outlook-add-in-project"></a>Procedura: Aggiungere un'area del modulo a un progetto di componente aggiuntivo di Outlook
  Creare un'area del modulo per estendere un modulo standard o personalizzato di Microsoft Office Outlook usando la procedura guidata **Nuova area del modulo di Outlook** . È possibile creare una nuova area del modulo e progettare l'interfaccia utente in Visual Studio oppure importare un'area del modulo progettata in Outlook e aggiungere codice Visual Basic o C#.

 Un'area del modulo di Outlook di un altro progetto di Outlook può essere riutilizzata nel progetto corrente di componente aggiuntivo VSTO per Outlook con la finestra di dialogo **Aggiungi elemento esistente** . Per altre informazioni, vedere [creare aree del modulo di Outlook](../vsto/creating-outlook-form-regions.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

### <a name="to-add-a-new-form-region-to-an-outlook-project"></a>Per aggiungere una nuova area del modulo a un progetto di Outlook

1. Aprire o creare un progetto di componente aggiuntivo VSTO di Outlook in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Per altre informazioni, vedere [Procedura: Creazione di progetti di Office in](../vsto/how-to-create-office-projects-in-visual-studio.md)Visual Studio.

2. In **Esplora soluzioni**selezionare il nodo del progetto di componente aggiuntivo VSTO di Outlook.

3. Nel menu **Progetto** fare clic su **Aggiungi nuovo elemento**.

4. Nella finestra di dialogo **Aggiungi nuovo elemento** selezionare **Area del modulo di Outlook**.

5. Nella casella **Nome** digitare un nome per l'area del modulo, quindi scegliere **Aggiungi**.

     Viene avviata la procedura guidata **area del modulo NewOutlook** .

6. Nella pagina **Selezionare la modalità di creazione dell'area del modulo** scegliere se si vuole progettare l'area del modulo trascinando i controlli gestiti in una finestra di progettazione visiva o importare un'area del modulo progettata in Outlook.

    > [!NOTE]
    > Se si sceglie di importare un'area del modulo progettata in Outlook, è necessario specificare il percorso di un file*OFS*(Outlook Form Storage). Non è possibile aggiungere controlli gestiti a un'area del modulo progettata in Outlook, ma solo aggiungere codice associato all'interfaccia utente esistente. Per altre informazioni, vedere [creare aree del modulo di Outlook](../vsto/creating-outlook-form-regions.md).

7. Nella pagina **Selezionare il tipo di area del modulo da creare** esaminare i tipi di area del modulo e selezionarne uno, quindi scegliere **Avanti**. Per altre informazioni sui tipi di area del modulo, vedere [creare aree del modulo di Outlook](../vsto/creating-outlook-form-regions.md).

8. Nella casella **Nome** della pagina **Fornire un testo descrittivo e selezionare le preferenze di visualizzazione** digitare un nome per l'area del modulo. Per i tipi di area del modulo di sostituzione e di sostituzione completa, sono disponibili anche le caselle **Titolo** e **Descrizione** .

     Per informazioni su dove vengono visualizzati il nome, il titolo e la descrizione in Outlook quando si distribuisce l'area del modulo, vedere [creare aree del modulo di Outlook](../vsto/creating-outlook-form-regions.md).

9. Selezionare una o più modalità di visualizzazione in cui si vuole visualizzare l'area del modulo.

     Tutti i tipi di area del modulo possono essere visualizzati nei controlli, in modalità composizione (per la creazione di elementi) e in modalità lettura (per la visualizzazione di elementi). I tipi di area del modulo adiacenti, di sostituzione e di sostituzione completa possono essere visualizzati anche nel riquadro di lettura.

10. Scegliere **Avanti**.

11. Nella pagina **Identificare le classi di messaggi per la visualizzazione dell'area del modulo** selezionare le classi messaggio standard di Outlook o digitare i nomi di una o più classi messaggio personalizzate, quindi fare clic su **Fine**. Per altre informazioni, vedere [associare un'area del modulo a una classe messaggio di Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md).

## <a name="see-also"></a>Vedere anche
- [Accedere a un'area del modulo in fase di esecuzione](../vsto/accessing-a-form-region-at-run-time.md)
- [Soluzioni Outlook](../vsto/outlook-solutions.md)
- [Creazione di aree del modulo di Outlook](../vsto/creating-outlook-form-regions.md)
- [Linee guida per la creazione di aree del modulo di Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Procedura dettagliata: Progettare un'area del modulo di Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Procedura dettagliata: Importare un'area del modulo progettata in Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
- [Azioni personalizzate nelle aree del modulo di Outlook](../vsto/custom-actions-in-outlook-form-regions.md)
