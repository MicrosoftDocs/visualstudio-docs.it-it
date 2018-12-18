---
title: "Aggiungere codice al set di dati nelle applicazioni a più livelli | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: n-tier applications, extending datasets
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 775c03583a2fac35f2b62525bf5a18a67f250cef
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>Aggiungere codice al set di dati nelle applicazioni a più livelli
È possibile estendere la funzionalità di un set di dati creando un file di classe parziale per il set di dati e aggiungere codice (anziché l'aggiunta di codice per il *DatasetName*. File di DataSet). Classi parziali consentono al codice per una classe specifica da dividere tra più file fisici. Per ulteriori informazioni, vedere [parziale](/dotnet/visual-basic/language-reference/modifiers/partial) o [classi e metodi parziali](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).  
  
Il codice che definisce un set di dati viene generato ogni volta che vengono apportate modifiche alla definizione del set di dati (nel set di dati tipizzato). Questo codice viene generato anche quando si apportano modifiche durante l'esecuzione di una procedura guidata che consente di modificare la configurazione di un set di dati. Per impedire che il codice da eliminare durante la rigenerazione di un set di dati, aggiungere codice al file di classe parziale del set di dati.  
  
Per impostazione predefinita, una volta separato il dataset e TableAdapter codice, il risultato è un file di classe discreto in ogni progetto. Il progetto originale include un file denominato *DatasetName*. Designer (o *DatasetName*. Designer.cs) che contiene il codice del TableAdapter. Il progetto che è designato nel **progetto Dataset** proprietà dispone di un file denominato *DatasetName*. DataSet.Designer.vb (o *DatasetName*. DataSet.Designer.cs). Questo file contiene il codice del dataset.  
  
> [!NOTE]
>  Quando si separano i DataSet e TableAdapter (impostando il **progetto DataSet** proprietà), classi parziali del dataset esistenti nel progetto non verranno spostate automaticamente. Le classi parziali del dataset devono essere spostate manualmente nel progetto di dataset.  
  
> [!NOTE]
>  Quando è necessario aggiungere il codice di convalida, il dataset tipizzato fornisce la funzionalità per la generazione di <xref:System.Data.DataTable.ColumnChanging> e <xref:System.Data.DataTable.RowChanging> gestori eventi. Per ulteriori informazioni, vedere [aggiungere la convalida a un dataset a più livelli](../data-tools/add-validation-to-an-n-tier-dataset.md).  
  
## <a name="to-add-code-to-datasets-in-n-tier-applications"></a>Per aggiungere codice al set di dati nelle applicazioni a più livelli  
  
1.  Individuare il progetto che contiene il file con estensione XSD. 
  
2.  Selezionare il **XSD** file da aprire il set di dati.  
  
3.  Fare doppio clic nella tabella di dati a cui si desidera aggiungere il codice (il nome della tabella nella barra del titolo) e quindi selezionare **Visualizza codice**.  
  
     Una classe parziale viene creata e aperto nell'Editor di codice.  
  
4.  Aggiungere codice all'interno della dichiarazione di classe parziale.  
  
     Nell'esempio seguente viene illustrato dove aggiungere il codice in CustomersDataTable NorthwindDataSet:  
  
    ```vb  
    Partial Public Class CustomersDataTable  
        ' Add code here to add functionality   
        ' to the CustomersDataTable.  
    End Class  
    ```    
    ```csharp  
    partial class CustomersDataTable  
    {  
        // Add code here to add functionality  
        // to the CustomersDataTable.  
    }  
    ```  
  
## <a name="see-also"></a>Vedere anche
[Panoramica delle applicazioni dati a più livelli](../data-tools/n-tier-data-applications-overview.md)   
[Aggiungere il codice nei TableAdapter di applicazioni a più livelli](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)  
[Creare e configurare gli oggetti TableAdapter](create-and-configure-tableadapters.md)  
[Panoramica di aggiornamento gerarchico](hierarchical-update.md)     
[Strumenti di set di dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)