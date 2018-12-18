---
title: Utilizzando la finestra di progettazione del flusso di lavoro macchina stati (Legacy) | Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- StateFinalizationActivity activity
- StateActivity activity
- SetStateActivity activity
- EventDrivenActivity activity
- state machine workflow designer
- state machine workflows, designer
- state machine workflows, activities
- StateInitializationActivity activity
ms.assetid: 2cd21123-35c2-4eaf-82f6-86fce7a8f04d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 16178d2f83ef9cc45ef7007350e30d2b36d6993a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="using-the-legacy-state-machine-workflow-designer"></a>Utilizzo della finestra di progettazione flusso di lavoro di una macchina a stati (legacy)
Quando si crea un progetto flusso di lavoro macchina a stati nuovo in [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] che si riferisce al [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)], è possibile scegliere di utilizzare il **applicazione Console flusso di lavoro macchina a stati** o il  **Libreria del flusso di lavoro macchina a stati** modello di progetto legacy. Se si sceglie uno di questi modelli di progetto della macchina a stati, la finestra di progettazione della macchina a stati viene presentata come interfaccia utente della finestra di progettazione del flusso di lavoro legacy. Per informazioni sui modelli di progetto macchina stato legacy, vedere [procedura: creare stato macchina del flusso di lavoro applicazioni Console (Legacy)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md) e [procedura: creare una libreria del flusso di lavoro macchina a stati (Legacy)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md).

 Il flusso di lavoro di una macchina a stati è costituito da un set di stati. Uno stato è indicato come stato iniziale. Ogni stato può ricevere un determinato set di eventi. In base a un evento, può essere fatta una transizione a un altro stato. Il flusso di lavoro di una macchina a stati può avere uno stato finale. Quando viene effettuata una transizione allo stato finale, l'esecuzione del flusso di lavoro è completata.

## <a name="state-machine-designer-views"></a>Visualizzazioni della finestra di progettazione della macchina a stati
 La finestra di progettazione della macchina a stati è una finestra di progettazione con figura a mano libera, ciò vuol dire che le attività possono essere spostate liberamente sull'area di progettazione. La finestra di progettazione di computer di stato è disponibili due visualizzazioni: *stato* Vista e *basato su eventi* visualizzazione.

 La visualizzazione di stato mostra le attività di stato e le attività basate sugli eventi che possono essere contenute all'interno di un'attività di stato. In questa visualizzazione, le transizioni da uno stato a un altro vengono rappresentate da righe che si estendono dall'attività basata sugli eventi in uno stato a un altro stato. È anche possibile creare transizioni tracciando una linea. Per tracciare la transizione, selezionare l'attività basata sugli eventi e quindi selezionare uno degli handle sull'attività e trascinarlo. Questa azione consente di tracciare una riga. Questa riga viene quindi allegata allo stato di destinazione, indicando una transizione tra stati.

 Per accedere alla visualizzazione basata sugli eventi, fare doppio clic su un'attività basata sugli eventi. La finestra di progettazione che verrà visualizzata è molto simile alla finestra di progettazione del flusso di lavoro sequenziale. All'inizio della finestra di progettazione, una barra di navigazione illustra la gerarchia delle attività fino all'attività basata sugli eventi visualizzata. È possibile tornare alla visualizzazione di stato facendo clic su qualsiasi elemento nella gerarchia visualizzata. Se è stata tracciata una transizione da uno stato all’altro nella visualizzazione di stato e se si sta visualizzando la visualizzazione basata sugli eventi di quell'attività, un'attività di stato fissa verrà aggiunta all'attività basata sugli eventi. Se si modificano le proprietà dell'attività di stato fissa, questa modifica è riflessa nella visualizzazione di stato.

## <a name="state-machine-workflow-activities"></a>Attività del flusso di lavoro di una macchina a stati
 Nella tabella seguente sono descritte le attività principali usate nella finestra di progettazione del flusso di lavoro della macchina a stati.

|Nome della casella degli strumenti|Attività|Descrizione|
|------------------|--------------|-----------------|
|**Stato**|[StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)|Rappresenta uno stato in una macchina a stati; può contenere ulteriori **StateActivity** attività. Per ulteriori informazioni, vedere [utilizzo dell'attività StateActivity](http://go.microsoft.com/fwlink?LinkID=65083).|
|**SetState**|[SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041)|Specifica una transizione a un nuovo stato. Per ulteriori informazioni, vedere [utilizzo dell'attività SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65082).|
|**StateInitialization**|[StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)|Viene eseguita quando viene immesso uno stato; può contenere altre attività. Per ulteriori informazioni, vedere [utilizzo dell'attività StateInitialization](http://go.microsoft.com/fwlink?LinkID=65006).|
|**StateFinalization**|[StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)|Esegue attività contenute quando si esce da un [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) attività. Per ulteriori informazioni, vedere [utilizzo dell'attività StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65008).|
|**EventDriven**|[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)|Viene usata per stati che si basano su un evento esterno per avviare l’esecuzione. Il **EventDrivenActivity** attività deve avere un'attività che implementa il [IEventActivity](http://go.microsoft.com/fwlink?LinkID=65032) interfaccia come prima attività figlio. Per ulteriori informazioni, vedere [utilizzando l'attività EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65068).|

 Il componente principale in un flusso di lavoro macchina è il [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) attività. Dato che gli eventi vengono acquisiti nei vari punti del flusso di lavoro della macchina a stati, vengono immessi stati diversi per gestire le attività associate agli eventi. Nel corso della durata del flusso di lavoro, il flusso di lavoro può uscire da e accedere a molti stati diversi. Questi stati sono connessi tra loro tramite la [SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041) attività.

 Quando si trascina un nuovo **StateActivity** nell'area di progettazione del flusso di lavoro, è possibile aggiungere [EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029), [StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044), [ StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043), o altro **StateActivity** attività come attività figlio.

> [!CAUTION]
> Quando si utilizza la finestra di progettazione dello stato del flusso di lavoro macchina a creare flussi di lavoro, è necessario monitorare la struttura del flusso di lavoro si sta progettando con la **struttura documento** finestra di visualizzazione. La visualizzazione della struttura del flusso di lavoro macchina nel **struttura documento** visualizzazione finestra rispecchia il layout logico delle attività nel file di markup del flusso di lavoro. Il layout fisico delle attività del flusso di lavoro, così come vengono visualizzate nell'area di progettazione, potrebbe non rispecchiare il layout logico delle attività nel file di markup del flusso di lavoro.
>
> Per aprire il **struttura documento** finestra, scegliere il **vista** dal menu **altre finestre**e quindi selezionare **struttura documento**.

## <a name="see-also"></a>Vedere anche

- [Procedura: Creare applicazioni console flusso di lavoro di una macchina a stati (legacy)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md)
- [Procedura: Creare una libreria del flusso di lavoro di macchina a stati (legacy)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md)
- [Flussi di lavoro della macchina a stati](http://go.microsoft.com/fwlink?LinkID=65016)
- [Utilizzo dell'attività StateActivity](http://go.microsoft.com/fwlink?LinkID=65083)
- [Utilizzo dell'attività StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65006)
- [Utilizzo dell'attività StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65008)
- [Utilizzo dell'attività SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65082)
- [Utilizzo dell'attività EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65068)