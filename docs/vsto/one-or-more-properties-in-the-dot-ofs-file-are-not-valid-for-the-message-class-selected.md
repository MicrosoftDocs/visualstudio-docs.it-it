---
title: "Uno o più proprietà nel file ofs non sono valide per la classe messaggio selezionata | Documenti Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VSTO.NewFormRegionWizard.OFSPropertyError
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 6ab0b36921911ac8c70501096868f47a40371f79
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="one-or-more-properties-in-the-ofs-file-are-not-valid-for-the-message-class-selected"></a>Una o più proprietà del file con estensione ofs non sono valide per la classe messaggio selezionata
  Questo errore viene visualizzato quando si importa un'area del modulo progettata in Outlook, ma uno o più campi nell'area del modulo non sono compatibili con le classi messaggio selezionate nella pagina finale della procedura guidata **Nuova area del modulo** .  
  
 Ad esempio, è possibile selezionare **Task (IPM.Task)** nella pagina finale della procedura guidata **Nuova area del modulo** . Se l'area del modulo contiene un campo **Business Address** , l'errore viene visualizzato perché un'attività non contiene un indirizzo della società. Quindi, il campo **Business Address** non è compatibile con la classe messaggio IPM.Task.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Nella pagina finale della procedura guidata **Nuova area del modulo** selezionare una classe messaggio compatibile con i campi dell'area del modulo.  
  
-   In Progettazione Form in Outlook rimuovere i campi non compatibili con le classi messaggio che si intende selezionare nella pagina finale della procedura guidata **Nuova area del modulo** .  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: importazione di un'area del modulo progettata in Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  