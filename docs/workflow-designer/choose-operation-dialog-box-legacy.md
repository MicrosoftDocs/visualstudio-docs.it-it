---
title: Scegliere la finestra di dialogo operazione (Legacy) | Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Design.OperationPickerDialog.UI
ms.assetid: bc3ec902-7797-494e-af48-e70c97eb6779
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5b4bd8318c4b10dab878ffd96667ce7057e653ae
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="choose-operation-dialog-box-legacy"></a>Finestra di dialogo Seleziona operazione (legacy)

Questo argomento viene descritto come utilizzare il **Seleziona operazione** nella finestra di dialogo di progettazione del flusso di lavoro Windows legacy. Usare la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] legacy quando è necessario fare riferimento a [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 Il **Seleziona operazione** viene utilizzata la finestra di dialogo per selezionare un'operazione da associare a un <xref:System.Workflow.Activities.ReceiveActivity> attività o un <xref:System.Workflow.Activities.SendActivity> attività. Per ulteriori informazioni sull'utilizzo di questa finestra di dialogo con le attività, vedere [procedura: implementare un'operazione del contratto WCF (Legacy)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) e [procedura: richiamare un'operazione del contratto WCF (Legacy)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md).

 Nella tabella seguente vengono descritti gli elementi dell'interfaccia utente di **Seleziona operazione** la finestra di dialogo.

|Elemento dell'interfaccia utente|Descrizione|
|----------------|-----------------|
|**Aggiungi contratto**|Crea un nuovo contratto, in cui è possibile definire nuove operazioni. (Utilizzato solo con <xref:System.Workflow.Activities.ReceiveActivity>.)|
|**L'operazione di aggiunta**|Aggiunge nuove operazioni a un nuovo contratto creato nel **Seleziona operazione** la finestra di dialogo. **Nota:** è possibile aggiungere nuove operazioni solo ai contratti creati tramite il **Seleziona operazione** la finestra di dialogo. <br /><br /> (Utilizzato solo con <xref:System.Workflow.Activities.ReceiveActivity>.)|
|**Importa...**|Importa un contratto definito in precedenza e consente di selezionare un'operazione da tale contratto.|
|**Nome dell'operazione**|Nome dell'operazione attualmente selezionata. Questa casella di testo è disponibile per la modifica solo se è stata creata un'operazione tramite il **Seleziona operazione** la finestra di dialogo.|
|**Parametri**|Scheda contenente le definizioni di parametro per l'operazione attualmente selezionata. **Nota:** le definizioni di parametro possono essere modificate solo se è stata creata un'operazione tramite il **Seleziona operazione** la finestra di dialogo.|
|**Proprietà**|Scheda contenente le impostazioni di <xref:System.Net.Security.ProtectionLevel> per i messaggi scambiati fra il client e il servizio. **Nota:** questa scheda è abilitata solo se è stata creata un'operazione tramite il **Seleziona operazione** la finestra di dialogo.|
|**Autorizzazioni**|Scheda contenente le proprietà <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionName%2A> e <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionRole%2A> degli utenti autorizzati a chiamare tale operazione. Ad esempio, se solo gli utenti dal gruppo Administrators sono autorizzati a chiamare tale operazione, quindi si scriverebbe "Administrators" **ruolo** casella di testo.<br /><br /> Questa scheda è abilitata per le operazioni create tramite il **ChooseOperation** la finestra di dialogo e le operazioni che sono state importate tramite il **importazione** pulsante.|

> [!NOTE]
> Il **Seleziona operazione** la finestra di dialogo vengono visualizzati solo i contratti o operazioni che vengono utilizzate da altri <xref:System.Workflow.Activities.SendActivity> attività nel flusso di lavoro. Analogamente, il **Seleziona operazione** la finestra di dialogo per <xref:System.Workflow.Activities.ReceiveActivity> le attività vengono visualizzati solo i contratti o operazioni che vengono utilizzate da altri **ReceiveActivity** attività nel flusso di lavoro.

## <a name="see-also"></a>Vedere anche

- [Procedura: implementare un'operazione del contratto WCF (Legacy)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)
- [Procedura: richiamare un'operazione del contratto WCF (Legacy)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)
- [Finestra di progettazione legacy per la Guida interfaccia utente di Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)