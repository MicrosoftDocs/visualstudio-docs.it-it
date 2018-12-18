---
title: "Aggiungere codice agli oggetti TableAdapter nelle applicazioni a più livelli | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, extending TableAdapters
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 54df2144511e847988c6f11212e9c9a4941d0b38
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>Aggiungere codice agli oggetti TableAdapter nelle applicazioni a più livelli
È possibile estendere la funzionalità di un oggetto TableAdapter mediante la creazione di un file di classe parziale per l'oggetto TableAdapter e aggiungendovi il codice (anziché l'aggiunta di codice per il *DatasetName*. File di DataSet). Classi parziali consentono al codice per una classe specifica da dividere tra più file fisici. Per ulteriori informazioni, vedere [parziale](/dotnet/visual-basic/language-reference/modifiers/partial) o [parziale (tipo)](/dotnet/csharp/language-reference/keywords/partial-type).  
  
Il codice che definisce un oggetto TableAdapter viene generato ogni volta che vengono apportate modifiche all'oggetto TableAdapter nel set di dati. Questo codice viene generato anche quando vengono apportate modifiche durante l'esecuzione di una procedura guidata che consente di modificare la configurazione dell'oggetto TableAdapter. Per impedire che il codice da eliminare durante la rigenerazione di un oggetto TableAdapter, aggiungere codice al file di classe parziale del TableAdapter.  
  
Per impostazione predefinita, una volta separato il dataset e TableAdapter codice, il risultato è un file di classe discreto in ogni progetto. Il progetto originale include un file denominato *DatasetName*. Designer (o *DatasetName*. Designer.cs) che contiene il codice del TableAdapter. Il progetto che è designato nel **progetto Dataset** proprietà dispone di un file denominato *DatasetName*. DataSet.Designer.vb (o *DatasetName*. DataSet.Designer.cs) che contiene il codice del dataset.  
  
> [!NOTE]
>  Quando si separano i DataSet e TableAdapter (impostando il **progetto DataSet** proprietà), classi parziali del dataset esistenti nel progetto non vengono spostate automaticamente. Le classi parziali del dataset devono essere spostate manualmente nel progetto di dataset.  
  
> [!NOTE]
>  Il set di dati fornisce funzionalità per la generazione di <xref:System.Data.DataTable.ColumnChanging> e <xref:System.Data.DataTable.RowChanging> gestori di eventi quando la convalida è necessaria. Per ulteriori informazioni, vedere [aggiungere la convalida a un dataset a più livelli](../data-tools/add-validation-to-an-n-tier-dataset.md).  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>Aggiungere il codice utente in un oggetto TableAdapter in un'applicazione a più livelli  
  
1.  Individuare il progetto che contiene il file con estensione XSD.
  
2.  Fare doppio clic il **XSD** file da aprire la **Progettazione Dataset**.  
  
3.  Fare doppio clic su TableAdapter che si desidera aggiungere il codice per e quindi selezionare **Visualizza codice**.  
  
     Una classe parziale viene creata e aperto nell'Editor di codice.  
  
4.  Aggiungere codice all'interno della dichiarazione di classe parziale.  
  
5.  Nell'esempio seguente viene illustrato dove aggiungere il codice di `CustomersTableAdapter` nel `NorthwindDataSet`:  
  
    ```vb  
    Partial Public Class CustomersTableAdapter  
        ' Add code here to add functionality   
        ' to the CustomersTableAdapter.  
    End Class  
    ```  
  
    ```csharp  
    public partial class CustomersTableAdapter  
    {  
        // Add code here to add functionality  
        // to the CustomersTableAdapter.  
    }  
    ```  
  
## <a name="see-also"></a>Vedere anche
[Panoramica delle applicazioni dati a più livelli](../data-tools/n-tier-data-applications-overview.md)   
[Aggiungere codice al set di dati nelle applicazioni a più livelli](../data-tools/add-code-to-datasets-in-n-tier-applications.md)   
[Creare e configurare gli oggetti TableAdapter](create-and-configure-tableadapters.md)   
[Panoramica di aggiornamento gerarchico](hierarchical-update.md)   
