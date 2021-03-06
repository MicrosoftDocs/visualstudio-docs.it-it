---
title: Proprietà non valide nel file OFS per la classe Message "
description: Informazioni su come correggere un errore che si verifica quando una o più proprietà nel file OFS non sono valide per la classe messaggio selezionata.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VSTO.NewFormRegionWizard.OFSPropertyError
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b22870cdb038adee84adc0fd7a56c269cb048626
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841914"
---
# <a name="invalid-properties-in-the-ofs-file-for-the-message-class"></a>Proprietà non valide nel file OFS per la classe Message

  L'errore "una o più proprietà nel file OFS non sono valide per la classe messaggio selezionata" viene visualizzato quando si importa un'area del modulo progettata in Outlook, ma uno o più campi nell'area del modulo non sono compatibili con le classi di messaggio selezionate nella pagina finale della procedura guidata **nuova area del modulo** .

Ad esempio, è possibile selezionare **Task (IPM.Task)** nella pagina finale della procedura guidata **Nuova area del modulo** . Se l'area del modulo contiene un campo dell' **indirizzo di business** , questo errore viene visualizzato perché un'attività non dispone di un indirizzo di business. Pertanto, il campo **indirizzo di business** non è compatibile con la `IPM.Task` classe Message.

 È possibile selezionare **Task (IPM). Attività)** nella pagina finale della procedura guidata **nuova area del modulo** . Se l'area del modulo contiene un campo dell' **indirizzo di business** , questo errore viene visualizzato perché un'attività non dispone di un indirizzo di business. Pertanto, il campo **indirizzo di business** non è compatibile con la `IPM.Task` classe Message.

## <a name="to-correct-this-error"></a>Per correggere l'errore

- Nella pagina finale della procedura guidata **Nuova area del modulo** selezionare una classe messaggio compatibile con i campi dell'area del modulo.

- In progettazione form in Outlook rimuovere i campi non compatibili con le classi messaggio. Rimuovere i campi che si intende selezionare nella pagina finale della procedura guidata **nuova area del modulo** .

## <a name="see-also"></a>Vedi anche
- [Procedura dettagliata: importare un'area del modulo progettata in Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
