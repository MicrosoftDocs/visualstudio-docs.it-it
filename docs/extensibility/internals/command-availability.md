---
title: Comando disponibilità | Documenti Microsoft
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 08f6ceb6c57eccf359b4aa23db7d693df3b86453
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="command-availability"></a>Disponibilità dei comandi

Il contesto di Visual Studio determina quali comandi sono disponibili. Il contesto può cambiare a seconda del progetto corrente, l'editor corrente, i pacchetti VSPackage che vengono caricati e altri aspetti dell'ambiente di sviluppo integrato (IDE).

## <a name="command-contexts"></a>Contesti di comando

I seguenti contesti di comando sono i più comuni.

-   **IDE** comandi forniti dall'IDE sono sempre disponibili.

-   **VSPackage** VSPackage è possono definire quando i comandi sono per essere visualizzato o nascosto.

-   **Progetto** comandi progetto vengono visualizzate solo per il progetto selezionato.

-   **Editor** unico editor può essere attivo alla volta. Sono disponibili i comandi da editor attivo. Un editor collabora a stretto contatto con un servizio di linguaggio. Il servizio di linguaggio deve elaborare i comandi nel contesto dell'editor associato.

-   **Tipo di file** un editor può caricare più di un tipo di file. I comandi disponibili possono variare a seconda del tipo di file.

-   **Finestra attiva** l'ultima finestra di documento attivo imposta il contesto dell'interfaccia utente per i tasti di scelta rapida. Tuttavia, una finestra degli strumenti che dispone di una tabella di chiave di associazione che il browser interno è simile può anche impostare il contesto dell'interfaccia utente. Per le finestre di documento a schede, ad esempio l'editor HTML, ogni scheda ha un contesto di comandi diversi GUID. Dopo la registrazione di una finestra degli strumenti, è sempre disponibile il **vista** menu.

-   **Contesto dell'interfaccia utente** contesti dell'interfaccia utente vengono identificati per i valori del <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> classe, ad esempio <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> durante la compilazione, la soluzione o <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> quando è attivo il debugger. Più contesti dell'interfaccia utente possono essere attivi contemporaneamente.

## <a name="defining-custom-context-guids"></a>Definizione di GUID di contesto personalizzato

Se GUID non è già stato definito un contesto di comando appropriato, è possibile definire uno nel pacchetto VSPackage e programmarlo per essere attivi o inattivi come richiesto per controllare la visibilità dei comandi.

1.  Registrare i GUID di contesto chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> metodo.

2.  Ottenere lo stato di un GUID di contesto chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> metodo.

3.  Attivare e disattivare la GUID di contesto chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> metodo.

    > [!CAUTION]
    > Assicurarsi che il pacchetto VSPackage non influisce sulla qualsiasi GUID di contesto esistente perché altri pacchetti VSPackage potrebbe dipendere da essi.

## <a name="see-also"></a>Vedere anche

- [Oggetti del contesto di selezione](../../extensibility/internals/selection-context-objects.md)
- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)