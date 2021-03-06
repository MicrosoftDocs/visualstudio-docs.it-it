---
title: Visualizzare dati correlati in applicazioni WPF
description: Visualizzare i dati correlati nelle applicazioni WPF. Utilizzare i dati di più tabelle o entità correlate tra loro in una relazione padre-figlio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 3aa80194-0191-474d-9d28-5ec05654b426
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 3467b2a3c4f49b22ab36b44ff0d3ea47d143e971
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866957"
---
# <a name="display-related-data-in-wpf-applications"></a>Visualizzare dati correlati in applicazioni WPF

In alcune applicazioni, potrebbe essere necessario utilizzare dati provenienti da più tabelle o entità correlate l'una all'altra in una relazione padre-figlio. Ad esempio, potrebbe essere necessario visualizzare una griglia in cui vengono visualizzati i clienti di una `Customers` tabella. Quando l'utente seleziona un cliente specifico, in un'altra griglia vengono visualizzati gli ordini per il cliente da una tabella correlata `Orders` .

È possibile creare controlli associati a dati che visualizzano dati correlati trascinando gli elementi dalla finestra **origini dati** a WPF Designer.

## <a name="to-create-controls-that-display-related-records"></a>Per creare controlli che visualizzano record correlati

1. Scegliere **Mostra origini dati** dal menu **Dati** per aprire la finestra **Origini dati**.

2. Fare clic su **Aggiungi nuova origine dati** e completare la **Configurazione guidata origine dati**.

3. Aprire WPF Designer e assicurarsi che la finestra di progettazione contenga un contenitore che rappresenta un obiettivo di rilascio valido per gli elementi nella finestra **origini dati** .

     Per altre informazioni sugli obiettivi di rilascio validi, vedere [associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

4. Nella finestra **origini dati** espandere il nodo che rappresenta la tabella o l'oggetto padre nella relazione. La tabella o l'oggetto padre si trova sul lato "uno" di una relazione uno-a-molti.

5. Trascinare il nodo padre (o tutti gli elementi singoli del nodo padre) dalla finestra **origini dati** in un obiettivo di rilascio valido nella finestra di progettazione.

     Visual Studio genera il codice XAML che crea nuovi controlli associati a dati per ogni elemento trascinato. In XAML viene inoltre aggiunto un nuovo <xref:System.Windows.Data.CollectionViewSource> oggetto per la tabella o l'oggetto padre alle risorse dell'obiettivo di rilascio. Per alcune origini dati, Visual Studio genera anche codice per caricare i dati nella tabella o nell'oggetto padre. Per altre informazioni, vedere [associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

6. Nella finestra **origini dati** individuare la tabella o l'oggetto figlio correlato. Le tabelle e gli oggetti figlio correlati vengono visualizzati come nodi espandibili nella parte inferiore dell'elenco di dati del nodo padre.

7. Trascinare il nodo figlio (o tutti gli elementi singoli del nodo figlio) dalla finestra **origini dati** in un obiettivo di rilascio valido nella finestra di progettazione.

     Visual Studio genera XAML per creare nuovi controlli associati a dati per ognuno degli elementi trascinati. Il codice XAML aggiunge anche un nuovo <xref:System.Windows.Data.CollectionViewSource> oggetto per la tabella o l'oggetto figlio alle risorse dell'obiettivo di rilascio. Questo nuovo <xref:System.Windows.Data.CollectionViewSource> è associato alla proprietà della tabella o dell'oggetto padre che è stato appena trascinato nella finestra di progettazione. Per alcune origini dati, Visual Studio genera anche codice per caricare i dati nella tabella o nell'oggetto figlio.

     Nella figura seguente viene illustrata la tabella **Orders** correlata della tabella **Customers** in un set di dati nella finestra **origini dati** .

     ![Finestra Origini dati con visualizzazione delle relazioni](../data-tools/media/datasources2.gif)

## <a name="see-also"></a>Vedi anche

- [Associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Creare tabelle di ricerca in applicazioni WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)
