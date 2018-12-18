---
title: Separare DataSet e TableAdapter in progetti diversi | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, separating Datasets and TableAdapters
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: af4e082bfa3e1b7669eb43218977b03a47c2f0bd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="separate-datasets-and-tableadapters-into-different-projects"></a>Set di dati separati e gli oggetti TableAdapter in progetti diversi
I dataset tipizzati sono stati migliorati in modo che il [TableAdapter](create-and-configure-tableadapters.md) e classi di set di dati possono essere generate in progetti separati. Ciò consente di separare i livelli dell'applicazione rapidamente e generare applicazioni dati a più livelli.  
  
La procedura seguente descrive il processo di utilizzo di **Progettazione Dataset** per generare il codice di set di dati in un progetto separato dal progetto che contiene il codice generato di TableAdapter.  
  
## <a name="separate-datasets-and-tableadapters"></a>Set di dati separati e gli oggetti TableAdapter  
Quando si separa il codice del dataset dal codice del TableAdapter, il progetto che contiene il codice del dataset deve trovarsi nella soluzione corrente. Se non si trova il progetto nella soluzione corrente, non sarà disponibile nel **progetto DataSet** nell'elenco di **proprietà** finestra.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-separate-the-dataset-into-a-different-project"></a>Per separare il set di dati in un progetto diverso  
  
1.  Aprire una soluzione che contiene un set di dati (file con estensione XSD).  
  
    > [!NOTE]
    >  Se la soluzione non contiene il progetto in cui si desidera separare il codice di set di dati, creare il progetto o aggiungere un progetto esistente alla soluzione.  
  
2.  Fare doppio clic su un file di dataset tipizzati (un file con estensione XSD) in **Esplora** per aprire il dataset nel **Progettazione Dataset**.  
  
3.  Selezionare un'area vuota del **Progettazione Dataset**.  
  
4.  Nel **proprietà** finestra, individuare il **progetto DataSet** nodo.  
  
5.  Nel **progetto DataSet** elenco, selezionare il nome del progetto in cui si desidera generare il codice del dataset.  
  
     Dopo aver selezionato il progetto in cui si desidera generare il codice del set di dati, il **DataSet File** proprietà viene popolata con un nome file predefinito. Se necessario, è possibile modificare questo nome. Inoltre, se si desidera generare il codice di set di dati in una directory specifica, è possibile impostare il **cartella progetto** proprietà sul nome di una cartella.  
  
    > [!NOTE]
    >  Quando si separano i DataSet e TableAdapter (impostando il **progetto DataSet** proprietà), classi parziali del dataset esistenti nel progetto non verranno spostate automaticamente. Le classi parziali del dataset devono essere spostate manualmente nel progetto di dataset.  
  
6.  Salvare il set di dati.  
  
     Viene generato il codice del dataset nel progetto selezionato nel **progetto DataSet** , proprietà e **TableAdapter** viene generato codice nel progetto corrente.  
  
Per impostazione predefinita, una volta separato il dataset e TableAdapter codice, il risultato è un file di classe discreto in ogni progetto. Il progetto originale include un file denominato NomeDataset.Designer.vb (o NomeDataset.Designer.cs) che contiene il codice del TableAdapter. Il progetto che è designato nel **progetto Dataset** proprietà dispone di un file denominato NomeDataset (o NomeDataset) che contiene il codice del dataset.  
  
> [!NOTE]
>  Per visualizzare il file di classe generata, selezionare il set di dati o di un progetto di TableAdapter. Quindi, nel **Esplora**selezionare **Mostra tutti i file**.  
  
## <a name="see-also"></a>Vedere anche
[Panoramica delle applicazioni dati a più livelli](../data-tools/n-tier-data-applications-overview.md)   
[Procedura dettagliata: Creazione di un'applicazione dati a più livelli](../data-tools/walkthrough-creating-an-n-tier-data-application.md)   
[Aggiornamento gerarchico](../data-tools/hierarchical-update.md)   
[Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)   
[ADO.NET](/dotnet/framework/data/adonet/index)