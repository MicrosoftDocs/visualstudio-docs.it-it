---
title: Come creare una relazione tra classi LINQ to SQL usando Progettazione relazionale oggetti | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 5c86eff5c25dbabb368d7d90ed46be718b8db8e7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-an-association-between-linq-to-sql-classes-or-designer"></a>Procedura: creare un'associazione tra classi LINQ to SQL (O/R Designer)
Le associazioni tra classi di entità in [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] sono analoghe alle relazioni tra tabelle in un database. È possibile creare associazioni tra classi di entità tramite il **Editor di associazione** la finestra di dialogo.  
  
È necessario selezionare una classe padre e una classe figlio quando si utilizza il **Editor di associazione** la finestra di dialogo per creare un'associazione. La classe padre è la classe di entità che contiene la chiave primaria, mentre la classe figlio è la classe di entità che contiene la chiave esterna. Ad esempio, se vengono create classi di entità con mapping alle tabelle Customers e Orders di Northwind, la classe Customer rappresenta la classe padre e la classe Order rappresenta la classe figlio.  
  
> [!NOTE]
>  Quando si trascinano tabelle da **Esplora Server**/**Esplora Database** sul [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] ([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]), le associazioni vengono create automaticamente in base a esistente relazioni di chiave esterna nel database.  

## <a name="association-properties"></a>Proprietà di associazione
Dopo aver creato un'associazione, quando si seleziona l'associazione nella finestra di Progettazione relazionale, esistono alcune proprietà configurabili di **proprietà** finestra. (l'associazione rappresenta la linea tra le classi correlate). Nella tabella seguente vengono descritte le proprietà di un'associazione.  
  
|Proprietà|Descrizione|  
|--------------|-----------------|  
|**Cardinalità**|Controlla se l'associazione è uno-a-molti o uno-a-uno.|  
|**Proprietà figlio**|Specifica se creare una proprietà nella chiave esterna dell'associazione nell'elemento padre, che è una raccolta o un riferimento a record figlio. Ad esempio, nell'associazione tra Customer e Order, se il **proprietà figlio** è impostato su **True**, viene creata una proprietà denominata Orders nella classe padre.|  
|**Proprietà padre**|Proprietà nella classe figlio che fa riferimento alla classe padre associata. Ad esempio, nell'associazione tra Customer e Order, proprietà denominata Customer che fa riferimento al cliente associato per un ordine creato nella classe Order.|  
|**Proprietà partecipanti**|Visualizza le proprietà dell'associazione e fornisce un **i puntini di sospensione** pulsante (…) che consente di aprire nuovamente la **Editor di associazione** la finestra di dialogo.|  
|**Univoco**|Specifica se le colonne esterne di destinazione presentano un vincolo di univocità.|  
  
## <a name="to-create-an-association-between-entity-classes"></a>Per creare un'associazione tra classi di entità
  
1.  La classe di entità che rappresenta la classe padre nell'associazione destro, scegliere **Aggiungi**, quindi fare clic su **associazione**.  
  
2.  Verificare che il corretto **classe padre** è selezionata nel **Editor di associazione** la finestra di dialogo.  
  
3.  Selezionare il **classe figlio** nella casella combinata.  
  
4.  Selezionare il **proprietà associazione** che mettono in relazione le classi. In genere, questa operazione consente di eseguire il mapping alla relazione di chiave esterna definita nel database. Ad esempio, nell'associazione tra Customers e Orders, il **proprietà associazione** rappresentano il valore CustomerID per ogni classe.  
  
5.  Fare clic su **OK** per creare l'associazione.  
  
## <a name="see-also"></a>Vedere anche
[LINQ to SQL Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
[Procedura dettagliata: Creazione di classi LINQ to SQL](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)   
[LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)   
[Metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)   
[Procedura: rappresentare le chiavi primarie](/dotnet/framework/data/adonet/sql/linq/how-to-represent-primary-keys)