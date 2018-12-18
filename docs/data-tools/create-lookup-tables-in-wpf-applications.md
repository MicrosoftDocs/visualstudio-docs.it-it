---
title: Creare tabelle di ricerca nelle applicazioni WPF | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 56a1fbff-c7e8-4187-a1c1-ffd17024bc1b
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 4b403d3bbe2e42ee74af7a2f7babe8b2700dd0d4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="create-lookup-tables-in-wpf-applications"></a>Creare tabelle di ricerca nelle applicazioni WPF
Il termine *tabella di ricerca* (detto anche un *associazione ricerca*) descrive il controllo che visualizza informazioni da una tabella dati in base al valore di un campo di chiave esterna in un'altra tabella. È possibile creare una tabella di ricerca trascinando il nodo principale di una tabella padre o oggetto di **origini dati** finestra in un controllo che è già associato a una colonna o proprietà in una tabella figlio correlata.  
  
Ad esempio, si consideri una tabella `Orders` in un database sales. Ogni record di `Orders` tabella include un `CustomerID` che indica il cliente che ha effettuato l'ordine. Il `CustomerID` è una chiave esterna che punta a un record cliente di `Customers` tabella. Quando si visualizza un elenco di ordini dal `Orders` tabella, si può essere utile visualizzare il nome effettivo del cliente anziché il `CustomerID`. Poiché il nome del cliente nel `Customers` tabella, è necessario creare una tabella di ricerca per visualizzare il nome del cliente. La tabella di ricerca utilizza il `CustomerID` valore il `Orders` registrare per esplorare la relazione e restituire il nome del cliente.  
  
## <a name="to-create-a-lookup-table"></a>Per creare una tabella di ricerca  
  
1.  Aggiungere uno dei seguenti tipi di origini dati con i dati correlati al progetto:  
  
    -   Set di dati o Entity Data Model. 
  
    -   WCF Data Service, servizio WCF o un servizio Web. Per ulteriori informazioni, vedere [procedura: connettersi ai dati in un servizio](../data-tools/how-to-connect-to-data-in-a-service.md).  
  
    -   Oggetti. Per ulteriori informazioni, vedere [associare agli oggetti in Visual Studio](bind-objects-in-visual-studio.md).  
  
    > [!NOTE]
    >  Prima di creare una tabella di ricerca, come un'origine dati per il progetto devono esistere due tabelle o oggetti correlati.  
  
2.  Aprire il **WPF Designer**e assicurarsi che la finestra di progettazione contiene un contenitore che è una destinazione di rilascio validi per gli elementi di **origini dati** finestra.  
  
     Per ulteriori informazioni sulle destinazioni di rilascio validi, vedere [WPF di associare i controlli a dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).  
  
3.  Nel **dati** menu, fare clic su **Mostra origini dati** per aprire la **origini dati** finestra.  
  
4.  Espandere i nodi di **origini dati** finestra, fino a quando non è possibile visualizzare la tabella padre o l'oggetto e la tabella figlio correlata o l'oggetto.  
  
    > [!NOTE]
    >  La tabella figlio correlata o l'oggetto è il nodo che viene visualizzato come nodo figlio espandibile sotto la tabella padre o l'oggetto.  
  
5.  Fare clic sul menu a discesa per il nodo figlio e selezionare **dettagli**.  
  
6.  Espandere il nodo figlio.  
  
7.  Sotto il nodo figlio, fare clic sul menu di riepilogo a discesa per l'elemento che correla i dati padre e figlio. (Nell'esempio precedente, si tratta di **CustomerID** nodo.) Selezionare uno dei seguenti tipi di controlli che supportano l'associazione di ricerca:  
  
    -   **ComboBox**  
  
    -   **ListBox**  
  
    -   **ListView**  
  
        > [!NOTE]
        >  Se il **ListBox** o **ListView** controllo non viene visualizzato nell'elenco, è possibile aggiungere questi controlli all'elenco. Per informazioni, vedere [impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
    -   Qualsiasi controllo personalizzato deriva da <xref:System.Windows.Controls.Primitives.Selector>.  
  
        > [!NOTE]
        >  Per informazioni su come aggiungere i controlli personalizzati per l'elenco dei controlli è possono selezionare per gli elementi di **origini dati** finestra, vedere [aggiungere controlli personalizzati alla finestra Origini dati](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
8.  Trascinare il nodo figlio dal **origini dati** finestra su un contenitore nella finestra di progettazione WPF. (Nell'esempio precedente, il nodo figlio è il **ordini** nodo.)  
  
     Visual Studio genera XAML che crea i nuovi controlli associati a dati per ogni elemento che si trascina. Il codice XAML aggiunge inoltre un nuovo <xref:System.Windows.Data.CollectionViewSource> per l'oggetto per le risorse dell'obiettivo di rilascio o una tabella figlio. Per alcune origini dati, Visual Studio genera inoltre il codice per caricare dati nella tabella o dell'oggetto. Per ulteriori informazioni, vedere [WPF di associare i controlli a dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).  
  
9. Trascinare il nodo padre di **origini dati** finestra al controllo di ricerca di associazione creato in precedenza. (Nell'esempio precedente, il nodo padre è il **clienti** nodo).  
  
     Visual Studio imposta alcune proprietà sul controllo per configurare l'associazione di ricerca. Nella tabella seguente sono elencate le proprietà modificate da Visual Studio. Se necessario, è possibile modificare queste proprietà in XAML o nel **proprietà** finestra.  
  
    |Proprietà|Spiegazione dell'impostazione|  
    |--------------|----------------------------|  
    |<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>|Questa proprietà specifica la raccolta o associazione utilizzato per ottenere i dati che viene visualizzati nel controllo. Visual Studio imposta questa proprietà il <xref:System.Windows.Data.CollectionViewSource> per i dati padre è stato trascinato sul controllo.|  
    |<xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A>|Questa proprietà specifica il percorso dell'elemento di dati che viene visualizzato nel controllo. Visual Studio imposta questa proprietà per la prima colonna o proprietà dei dati padre, dopo la chiave primaria, con un tipo di dati stringa.<br /><br /> Se si desidera visualizzare una colonna diversa o una proprietà dei dati padre, è possibile modificare questa proprietà per il percorso di una proprietà diversa.|  
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>|Visual Studio la proprietà viene associata la colonna o proprietà dei dati che è stato trascinato nella finestra di progettazione figlio. Si tratta della chiave esterna per i dati padre.|  
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValuePath%2A>|Visual Studio imposta questa proprietà per il percorso della colonna o proprietà dei dati figlio che rappresenta la chiave esterna per i dati padre.|  
  
## <a name="see-also"></a>Vedere anche
[Associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)   
[Visualizzare i dati correlati nelle applicazioni WPF](../data-tools/display-related-data-in-wpf-applications.md)   
[Procedura dettagliata: visualizzazione dei dati correlati in un'applicazione WPF](../data-tools/display-related-data-in-wpf-applications.md)