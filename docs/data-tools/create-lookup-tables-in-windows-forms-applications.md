---
title: Creare tabelle di ricerca nelle applicazioni Windows Form
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- lookup tables
- lookup tables, creating
ms.assetid: 0edd5385-c381-4b17-9096-74e2778db9d5
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 15f7b481d3473854e38d99680ed9823a03e103f4
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="create-lookup-tables-in-windows-forms-applications"></a>Creare tabelle di ricerca nelle applicazioni Windows Form
Il termine *tabella di ricerca* vengono descritti i controlli associati a due tabelle dati correlate. Questi controlli di ricerca visualizzano i dati della prima tabella in base a un valore selezionato nella seconda tabella.

 È possibile creare tabelle di ricerca trascinando il nodo principale di una tabella padre (dal [finestra Origini dati](add-new-data-sources.md)) su un controllo sul form che è già associato alla colonna della tabella figlio correlata.

 Ad esempio, si consideri una tabella `Orders` in un database sales. Ogni record di `Orders` tabella include un `CustomerID`, che indica il cliente che ha effettuato l'ordine. Il `CustomerID` è una chiave esterna che punta a un record cliente di `Customers` tabella. In questo scenario, si espande il `Orders` tabella il **origini dati** finestra e impostare il nodo principale **dettagli**. Quindi impostare il `CustomerID` colonna da utilizzare un <xref:System.Windows.Forms.ComboBox> (o qualsiasi altro controllo che supporta l'associazione di ricerca) e trascinare il `Orders` nodo nel form. Infine, trascinare il `Customers` nodo nel controllo associato alla colonna correlata, in questo caso, il <xref:System.Windows.Forms.ComboBox> associato al `CustomerID` colonna.

## <a name="to-databind-a-lookup-control"></a>Come associare un controllo di ricerca

1.  Aprire il **origini dati** finestra.

    > [!NOTE]
    >  Tabelle di ricerca richiedono che siano disponibili in due tabelle o oggetti correlati di **origini dati** finestra. Per ulteriori informazioni, vedere [relazioni nei DataSet](relationships-in-datasets.md).

2.  Espandere i nodi di **origini dati** finestra fino a quando non è possibile visualizzare la tabella padre e tutte le relative colonne e la tabella figlio correlata e tutte le relative colonne.

    > [!NOTE]
    >  Il nodo della tabella figlio è il nodo che viene visualizzato come nodo figlio espandibile nella tabella padre.

3.  Modificare il tipo di rilascio della tabella figlio **dettagli** selezionando **dettagli** dall'elenco di controllo sul nodo della tabella figlio. Per ulteriori informazioni, vedere [impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

4.  Individuare il nodo che correla le due tabelle (il `CustomerID` nodo nell'esempio precedente). Modificare il tipo di trascinamento per un <xref:System.Windows.Forms.ComboBox> selezionando **ComboBox** dall'elenco di controllo.

5.  Trascinare il nodo della tabella figlio principale dal **origini dati** finestra nel form.

     Controlli con associazione a dati (con etichette descrittive) e un controllo ToolStrip (<xref:System.Windows.Forms.BindingNavigator>) vengono visualizzati nel form. Oggetto [DataSet](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource>, e <xref:System.Windows.Forms.BindingNavigator> vengono visualizzati nella barra dei componenti.

6.  Trascinare il nodo della tabella padre principale dal **origini dati** finestra direttamente al controllo di ricerca (il <xref:System.Windows.Forms.ComboBox>).

     Le associazioni di ricerca sono ora stabilite. Fare riferimento alla tabella di seguito per le proprietà specifiche che sono stati impostati sul controllo.

    |Proprietà|Spiegazione dell'impostazione|
    |--------------|----------------------------|
    |**Origine dati**|Questa proprietà viene impostata da Visual Studio sul <xref:System.Windows.Forms.BindingSource> creato per la tabella trascinata nel controllo (a differenza del <xref:System.Windows.Forms.BindingSource> creato al momento della creazione del controllo).<br /><br /> Se è necessario apportare modifiche, quindi impostare il <xref:System.Windows.Forms.BindingSource> della tabella con la colonna che si desidera visualizzare.|
    |**DisplayMember**|Questa proprietà viene impostata da Visual Studio sulla prima colonna successiva alla chiave primaria con tipo di dati stringa per la tabella che si intende trascinare nel controllo.<br /><br /> Se è necessario apportare modifiche, quindi impostare il nome della colonna che si desidera visualizzare.|
    |**ValueMember**|Questa proprietà viene impostata da Visual Studio sulla prima colonna che partecipa alla chiave primaria o la prima colonna della tabella nel caso in cui non sia stata definita alcuna chiave.<br /><br /> Se è necessario apportare modifiche, quindi impostare la chiave primaria nella tabella con la colonna che si desidera visualizzare.|
    |**SelectedValue**|Visual Studio imposta questa proprietà per la colonna originale trascinata dal **origini dati** finestra.<br /><br /> Se è necessario apportare modifiche, quindi impostare la colonna chiave esterna nella tabella correlata.|

## <a name="see-also"></a>Vedere anche

- [Associare controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)