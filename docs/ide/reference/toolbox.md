---
title: Finestra della casella degli strumenti
ms.date: 01/18/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- vs.toolbox.general
- vs.toolbox
helpviewer_keywords:
- Toolbox [Visual Studio]
- custom controls [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: feddaf034394e7f27411562d85631b66de3b66e3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55012612"
---
# <a name="toolbox"></a>Casella degli strumenti

Nella finestra **Casella degli strumenti** sono visualizzati i controlli che è possibile aggiungere ai progetti di Visual Studio. Per aprire la casella degli strumenti, scegliere **Casella degli strumenti** dal menu **Visualizza**.

![Finestra della casella degli strumenti](media/toolbox.png)

È possibile trascinare diversi controlli sulla superficie della finestra di progettazione in uso nonché ridimensionare e posizionare tali controlli.

La casella degli strumenti viene visualizzata insieme alle visualizzazioni delle finestre di progettazione, ad esempio la visualizzazione Progettazione di un file XAML. La **casella degli strumenti** visualizza solo i controlli che possono essere usati nella finestra di progettazione corrente. È possibile eseguire una ricerca all'interno della **casella degli strumenti** per restringere ulteriormente gli elementi visualizzati.

> [!NOTE]
> Per alcuni tipi di progetto, nella **casella degli strumenti** potrebbe non essere visualizzato alcun elemento.

La versione di.NET Framework di destinazione del progetto influisce sul set di controlli visibili nella casella degli strumenti. È possibile impostare come destinazione per il progetto una versione diversa di .NET Framework dalle pagine delle proprietà del progetto. Selezionare il nodo del progetto in **Esplora soluzioni** e quindi scegliere **Progetto** > **Proprietà nomeprogetto** nella barra dei menu. Nella scheda **Applicazione** usare l'elenco a discesa **Framework di destinazione**.

## <a name="manage-the-toolbox-window-and-its-controls"></a>Gestire la finestra della casella degli strumenti e i relativi controlli

Per impostazione predefinita, la **casella degli strumenti** viene compressa lungo la parte sinistra dell'IDE di Visual Studio e viene visualizzata quando il cursore viene spostato su di essa. È possibile bloccare la **casella degli strumenti**, facendo clic sull'icona **Blocca** nella barra degli strumenti della casella degli strumenti, in modo che resti aperta quando il cursore viene spostato. È anche possibile disancorare la finestra della **casella degli strumenti** e trascinarla in qualsiasi posizione sullo schermo. È possibile ancorare, disancorare e nascondere la **casella degli strumenti** facendo clic con il pulsante destro del mouse sulla relativa barra degli strumenti e scegliendo una delle opzioni.

È possibile riordinare gli elementi di una scheda della **casella degli strumenti** o aggiungere schede ed elementi personalizzati usando i comandi seguenti nel menu di scelta rapida:

- **Rinomina elemento**: rinomina l'elemento selezionato.

- **Mostra tutto**: visualizza tutti i controlli possibili, non solo quelli applicabili alla finestra di progettazione corrente.

- **Elenco**: visualizza i controlli in un elenco verticale. Se deselezionati, i controlli vengono visualizzati in orizzontale.

- **Scegli elementi**: apre la finestra di dialogo **Scegli elementi della Casella degli strumenti** che consente di specificare gli elementi visualizzati nella **casella degli strumenti**. È possibile visualizzare o nascondere un elemento selezionando o deselezionando la relativa casella di controllo.

- **Ordina elementi alfabeticamente**: ordina gli elementi per nome.

- **Reimposta barra degli strumenti**: ripristina le impostazioni e gli elementi predefiniti della **casella degli strumenti**.

- **Aggiungi scheda**: aggiunge una nuova scheda della **casella degli strumenti**.

- **Sposta su**: sposta l'elemento selezionato verso l'alto.

- **Sposta giù**: sposta l'elemento selezionato verso il basso.

## <a name="create-and-distribute-custom-toolbox-controls"></a>Creare e distribuire controlli della casella degli strumenti personalizzati

È possibile creare controlli della **casella degli strumenti** personalizzati partendo da un modello di progetto basato su [Windows Presentation Foundation](../../extensibility/creating-a-wpf-toolbox-control.md) o [Windows Form](../../extensibility/creating-a-windows-forms-toolbox-control.md). È quindi possibile distribuire il controllo personalizzato ai colleghi del team o pubblicarlo sul Web usando il [programma di installazione dei controlli della casella degli strumenti ](http://download.microsoft.com/download/8/3/6/836657BD-9CCB-4ED4-B9D2-FB769473B284/TCI_whitepaper.docx).

## <a name="help-on-toolbox-tabs"></a>Guida sulle schede della casella degli strumenti

Negli argomenti seguenti sono disponibili altre informazioni su alcune delle schede disponibili per la **casella degli strumenti**:

- [Casella degli strumenti, scheda Dati](../../ide/reference/toolbox-data-tab.md)
- [Casella degli strumenti, scheda Componenti](../../ide/reference/toolbox-components-tab.md)
- [Casella degli strumenti, scheda HTML](../../ide/reference/toolbox-html-tab.md)

## <a name="see-also"></a>Vedere anche

- [Scegli elementi della Casella degli strumenti, Componenti WPF](choose-toolbox-items-wpf-components.md)