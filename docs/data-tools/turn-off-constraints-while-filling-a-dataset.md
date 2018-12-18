---
title: Disattivare i vincoli durante la compilazione di un set di dati | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DataRow.BeginEdit
- DataRow.EndEdit
- DataRow.CancelEdit
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- updating datasets, constraints
- constraints [Visual Basic], datasets
- datasets [Visual Basic], constraints
- constraints [Visual Basic], suspending during dataset update
ms.assetid: 553f7d0c-2faa-4c17-b226-dd02855bf1dc
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 88c8687511dd600802cc7c6ecdc12f0827fd7f6f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>Disattivare i vincoli durante la compilazione di un set di dati
Se un set di dati contiene i vincoli (ad esempio i vincoli di chiave esterna), possono generare errori relativi all'ordine delle operazioni che vengono eseguite a fronte del set di dati. Ad esempio, il caricamento dei record figlio prima del caricamento correlati record padre possono violano un vincolo e causare un errore. Non appena si carica un record figlio, il vincolo di verifica per il record padre correlate e genera un errore.  
  
 Se sono non stati alcun meccanismo per consentire di sospensione temporanea dei vincoli, verrà generato un errore ogni volta che si è tentato di caricare un record nella tabella figlio. È possibile sospendere tutti i vincoli in un set di dati con il <xref:System.Data.DataRow.BeginEdit%2A>, e <xref:System.Data.DataRow.EndEdit%2A> proprietà.  
  
> [!NOTE]
>  Gli eventi di convalida (ad esempio, <xref:System.Data.DataTable.ColumnChanging> e<xref:System.Data.DataTable.RowChanging>) non verrà generato quando i vincoli sono disabilitati.  
  
### <a name="to-suspend-update-constraints-programmatically"></a>Per sospendere i vincoli di aggiornamento a livello di codice  
  
-   Nell'esempio seguente viene illustrato come disattivare temporaneamente la verifica dei vincoli in un set di dati:  
  
     [!code-csharp[VbRaddataEditing#10](../data-tools/codesnippet/CSharp/turn-off-constraints-while-filling-a-dataset_1.cs)]
     [!code-vb[VbRaddataEditing#10](../data-tools/codesnippet/VisualBasic/turn-off-constraints-while-filling-a-dataset_1.vb)]  
  
### <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>Per sospendere i vincoli di aggiornamento tramite Progettazione Dataset  
  
1.  Aprire il dataset nel **Progettazione Dataset**. Per ulteriori informazioni, vedere [procedura dettagliata: creazione di un set di dati in Progettazione Dataset](walkthrough-creating-a-dataset-with-the-dataset-designer.md).  
  
2.  Nel **proprietà** finestra, impostare il <xref:System.Data.DataSet.EnforceConstraints%2A> proprietà `false`.  
  
## <a name="see-also"></a>Vedere anche  
 [Compilare i set di dati utilizzando gli oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Relazioni nei set di dati](../data-tools/relationships-in-datasets.md)