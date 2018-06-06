---
title: 'Finestra di progettazione del flusso di lavoro - procedura: aggiungere commenti a un flusso di lavoro'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Presentation.Annotations.Annotation.UI
- Annotation
ms.assetid: 9aa0e8d6-8129-4438-8389-d460611581a7
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: d740614ed94d0fd91ba9f3e73a083791b9112919
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34752027"
---
# <a name="how-to-add-comments-to-a-workflow-in-the-workflow-designer"></a>Procedura: aggiungere commenti a un flusso di lavoro in Progettazione del flusso di lavoro

Per facilitare la creazione di flussi di lavoro più ampi e complessi, .NET Framework 4.5 consente allo sviluppatore di aggiungere annotazioni ai seguenti tipi di elemento nella finestra di progettazione:

-   <xref:System.Activities.Activity>

-   <xref:System.Activities.Statements.State>

-   <xref:System.Activities.Statements.Transition>

-   Classi derivate da <xref:System.Activities.Statements.FlowNode>

-   <xref:System.Activities.Variable>

-   <xref:System.Activities.Argument>

> [!IMPORTANT]
> Il contenuto di un'annotazione viene salvato come testo normale nel file XAML associato al flusso di lavoro e potrebbe potenzialmente essere letto da altri. Prestare attenzione quando vengono fornite informazioni riservate in un'unica annotazione.

## <a name="adding-an-annotation-to-an-activity-in-the-designer"></a>Aggiunta di un'annotazione a un'attività nella finestra di progettazione

1. Nella finestra di progettazione del flusso di lavoro, fare clic su un elemento nel flusso di lavoro della finestra di progettazione e seleziona **annotazioni**, **Aggiungi annotazione**.

1. Aggiungere il testo dell'annotazione nello spazio disponibile.

   L'elemento viene visualizzata un'icona di annotazione. Passaggio del mouse sull'icona di annotazione, viene visualizzato il testo dell'annotazione.

## <a name="displaying-an-annotation-in-an-activitys-designer"></a>Visualizzazione di un'annotazione della finestra di progettazione dell'attività

1.  Con un ActivityDesigner che dispone di un'annotazione verrà visualizzata all'esterno dell'attività, fare clic su di **Pin** sull'icona dello strumento decorativo di annotazione.

   L'annotazione verrà visualizzata nella finestra di progettazione dell'attività. Nella schermata riportata di seguito, l'annotazione "inizia attività nel flusso di lavoro" viene visualizzata nella finestra di progettazione dell'attività.

   ![Annotazione visualizzata nella finestra di progettazione dell'attività](../workflow-designer/media/annotationindesigner.png)

1. Per visualizzare l'annotazione all'esterno di progettazione dell'attività, passa il mouse sull'area dell'annotazione nella finestra di progettazione dell'attività e scegliere il **Sblocca** icona

   ![Annotazione visualizzata all'esterno della finestra di progettazione dell'attività](../workflow-designer/media/annotationoutsidedesigner.png)

## <a name="showing-or-hiding-all-annotations"></a>Mostra o nascondi tutte le annotazioni

1. Fare clic con il pulsante destro del mouse su un'attività che dispone di annotazione. Selezionare **annotazioni**, **Mostra tutte le annotazioni**.

   Tutte le annotazioni vengono visualizzate nelle finestre di progettazione dell'attività.

1. Per visualizzare tutte le annotazioni di fuori di finestre di progettazione dell'attività, fare clic su attività e selezionare **annotazioni**, **nascondere tutte le annotazioni**.

## <a name="editing-or-deleting-an-annotation-for-an-activity"></a>Modifica o eliminazione di un'annotazione per un'attività

1. Fare clic con il pulsante destro del mouse su un'attività che dispone di un'annotazione.

1. Selezionare **annotazioni**, **Modifica annotazione** o **Elimina annotazione**.

   L'annotazione viene aperto per la modifica o eliminata.

1. Per eliminare tutte le annotazioni in una sola volta, fare doppio clic sul flusso di lavoro della finestra di progettazione e seleziona **annotazione**, **Elimina tutte le annotazioni**.

## <a name="adding-editing-and-deleting-an-annotation-for-a-variable-or-argument"></a>Aggiunta, modifica ed eliminazione di un'annotazione per una variabile o un argomento

1. Fare clic con il pulsante destro del mouse su una variabile o un argomento e selezionare Aggiungi annotazione.

1. Immettere il testo dell'annotazione. La variabile o argomento consente di visualizzare un'icona dell'annotazione.

1. Fare clic con il pulsante destro del mouse su una variabile o un argomento che dispone di un'annotazione. Selezionare Modifica annotazione.

   L'annotazione viene aperto per la modifica.

1. Fare clic con il pulsante destro del mouse su una variabile o un argomento che dispone di un'annotazione. Selezionare Elimina annotazione.

   L'annotazione viene eliminata.