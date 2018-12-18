---
title: Utilizzo dell'ActivityDesigner Legacy | Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- activities, configuring
- custom activities
- Activity Designer
- child activities, adding
- activities, adding child
- activities, creating custom
ms.assetid: 2fea8a05-6e58-423d-94bf-a822b15ffb80
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c69c2dfdd6fb81bcb6a544f27da0874a7dc99331
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="using-the-legacy-activity-designer"></a>Utilizzo dell'ActivityDesigner legacy
In questo argomento viene descritto come utilizzare la finestra di progettazione di attività in Progettazione flussi di lavoro Windows legacy. Usare la finestra di progettazione legacy quando si fa riferimento a [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o a [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 La Finestra di progettazione dell’attività consente di creare attività personalizzate.

## <a name="creating-a-custom-activity"></a>Creazione di un'attività personalizzata
 Seguire questi passaggi per creare un'attività personalizzata usando la Finestra di progettazione dell’attività:

1.  Nel **progetto** menu, fare clic su **aggiungere attività**.

2.  Selezionare il **attività** o **attività (con separazione del codice)** modello.

    1.  Utilizzare il **attività** modello per creare un'attività con la definizione di attività e il codice utente nello stesso file di codice.

    2.  Utilizzare il **attività (con separazione del codice)** modello per creare un'attività con la definizione di attività espressa come markup del flusso di lavoro e il codice utente in un file di codice separato.

3.  Digitare un nome di attività o mantenere il nome predefinito e quindi fare clic su **Aggiungi**.

 È inoltre possibile creare un set di attività personalizzate creando un nuovo progetto di tipo **Workflow Activity Library**. Per ulteriori informazioni su questo tipo di progetto, vedere [procedura: creare una libreria di attività del flusso di lavoro (Legacy)](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md).

## <a name="configuring-an-activity"></a>Configurazione di un'attività.
 Mentre la Finestra di progettazione dell’attività è attiva, è possibile usare il visualizzatore proprietà per configurare le proprietà elencate nella tabella seguente.

|Proprietà|Commenti|
|--------------|--------------|
|**Name**|Nome dell’attività.|
|**Classe di base**|Classe base dalla quale è derivata l’attività. La classe base predefinita è [SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020). Nel **proprietà** finestra, fare clic su di **di una classe Base** i puntini di sospensione **[…]**  per selezionare un'altra classe base di [Cerca e seleziona una casella di dialogo tipo .NET (Legacy)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md).|
|**Descrizione**|Descrizione dell'attività definita dall'utente.|
|**Enabled**|Impostare su **True** per impostazione predefinita per consentire l'esecuzione dell'attività e la convalida. Impostare su **False** per disabilitare l'esecuzione dell'attività e la convalida. Per informazioni sulla convalida e l'esecuzione dell'attività, vedere [sviluppo di attività del flusso di lavoro](http://go.microsoft.com/fwlink?LinkID=65024).|

## <a name="adding-child-activities"></a>Aggiunta di attività figlio.
 È possibile trascinare le attività figlio dalla Casella degli strumenti all'attività che si sta progettando. È quindi possibile configurare ogni attività figlio usando il visualizzatore proprietà.

## <a name="see-also"></a>Vedere anche

- [Lo sviluppo di attività del flusso di lavoro](http://go.microsoft.com/fwlink?LinkID=65024)
- [Creazione di attività personalizzate](http://go.microsoft.com/fwlink?LinkID=65021)
- [Attività del flusso di lavoro legacy](../workflow-designer/legacy-workflow-activities.md)
- [Esempi di attività personalizzate](http://go.microsoft.com/fwlink?LinkID=65022)
- [Procedura: Creare una libreria di attività del flusso di lavoro (legacy)](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md)
- [Uso di Progettazione flussi di lavoro legacy](../workflow-designer/using-the-legacy-workflow-designer.md)