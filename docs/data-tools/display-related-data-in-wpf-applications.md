---
title: Visualizzare i dati correlati nelle applicazioni WPF
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 3aa80194-0191-474d-9d28-5ec05654b426
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b293656a0eeffeba304ef4692f9c021ae9639d22
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="display-related-data-in-wpf-applications"></a>Visualizzare i dati correlati nelle applicazioni WPF
In alcune applicazioni, si potrebbe voler lavorare con dati provenienti da più tabelle o entità che sono correlate tra loro in una relazione padre-figlio. Potrebbe ad esempio, si desidera visualizzare una griglia in cui vengono visualizzati i clienti da un `Customers` tabella. Quando l'utente seleziona un cliente specifico, in un'altra griglia vengono visualizzati gli ordini per cliente da un processo di `Orders` tabella.

È possibile creare controlli associati a dati che visualizzano dati correlati trascinando elementi dal **origini dati** finestra alla finestra di progettazione WPF.

## <a name="to-create-controls-that-display-related-records"></a>Per creare controlli che visualizzano i record correlati

1. Nel **dati** menu, fare clic su **Mostra origini dati** per aprire la **origini dati** finestra.

2. Fare clic su **Aggiungi nuova origine dati**e completare il **configurazione guidata origine dati** procedura guidata.

3. Aprire la finestra di progettazione WPF e assicurarsi che la finestra di progettazione contiene un contenitore che è una destinazione di rilascio validi per gli elementi di **origini dati** finestra.

     Per ulteriori informazioni sulle destinazioni di rilascio validi, vedere [WPF di associare i controlli a dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

4. Nel **origini dati** finestra, espandere il nodo che rappresenta la tabella padre o l'oggetto nella relazione. La tabella padre o l'oggetto è sul lato "uno" di una relazione uno-a-molti.

5. Trascinare il nodo padre (o i singoli elementi nel nodo padre) di **origini dati** finestra su una destinazione di rilascio valide nella finestra di progettazione.

     Visual Studio genera XAML che crea i nuovi controlli associati a dati per ogni elemento che si trascina. Il codice XAML aggiunge inoltre un nuovo <xref:System.Windows.Data.CollectionViewSource> per l'oggetto per le risorse di destinazione o la tabella padre. Per alcune origini dati, Visual Studio genera inoltre il codice per caricare i dati in un oggetto o la tabella padre. Per ulteriori informazioni, vedere [WPF di associare i controlli a dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

6. Nel **origini dati** finestra, individuare la tabella figlio correlata o l'oggetto. Le tabelle figlio correlate e gli oggetti vengono visualizzati come nodi espandibili nella parte inferiore dell'elenco del nodo padre dei dati.

7. Trascinare il nodo figlio (o i singoli elementi nel nodo figlio) di **origini dati** finestra su una destinazione di rilascio valide nella finestra di progettazione.

     Visual Studio genera XAML che crea nuovi controlli associati a dati per ognuno degli elementi trascinati. Il codice XAML aggiunge inoltre un nuovo <xref:System.Windows.Data.CollectionViewSource> per l'oggetto per le risorse dell'obiettivo di rilascio o una tabella figlio. Questa nuova <xref:System.Windows.Data.CollectionViewSource> è associato alla proprietà dell'oggetto trascinato nella finestra di progettazione o tabella padre. Per alcune origini dati, Visual Studio genera inoltre il codice per caricare i dati nella tabella figlio o nell'oggetto.

     La figura seguente illustra gli **ordini** tabella il **clienti** tabella in un set di dati nel **origini dati** finestra.

     ![Finestra Origini dati che mostrano relazione](../data-tools/media/datasources2.gif "DataSources2")

## <a name="see-also"></a>Vedere anche

- [Associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Creare tabelle di ricerca in applicazioni WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)