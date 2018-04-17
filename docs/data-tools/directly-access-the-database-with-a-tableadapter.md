---
title: Accedere direttamente al database con un TableAdapter | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- databases [Visual Basic], accessing with a TableAdapter
- DBDirect methods
- datasets [Visual Basic], adding to projects
- data [Visual Studio], saving
- TableAdapter.Delete method
- GenerateDbDirectMethods property
- TableAdapter.Insert method
- TableAdapter.GenerateDBDirectMethods property
- TableAdapter.Update method
- saving data
- TableAdapters
ms.assetid: 012c5924-91f7-4790-b2a6-f51402b7014b
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c1238fb665740df03af63292f1feacd1ec92f0db
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>Accedere direttamente al database con un TableAdapter
Oltre al `InsertCommand`, `UpdateCommand`, e `DeleteCommand`, vengono creati gli oggetti TableAdapter con metodi che possono essere eseguiti direttamente nel database. Questi metodi (`TableAdapter.Insert`, `TableAdapter.Update`, e `TableAdapter.Delete`) può essere chiamato per manipolare i dati direttamente nel database.  
  
 Se non si desidera creare questi metodi diretti, impostare il TableAdapter `GenerateDbDirectMethods` proprietà `false` nel **proprietà** finestra. Se tutte le query vengono aggiunti a un oggetto TableAdapter oltre la query TableAdapter principale sono query autonomo che non generano queste DbDirect (metodi).  
  
## <a name="send-commands-directly-to-a-database"></a>Inviare comandi direttamente a un database  
 Chiamare il metodo DbDirect di TableAdapter che esegue l'attività che si sta tentando di eseguire.  
  
#### <a name="to-insert-new-records-directly-into-a-database"></a>Per inserire nuovi record direttamente in un database  
  
-   Chiamare il TableAdapter `Insert` , passando i valori per ogni colonna come parametri. La procedura seguente usa il `Region` tabella nel database Northwind come esempio.  
  
    > [!NOTE]
    >  Se non si dispone di un'istanza disponibile, creare un'istanza dell'oggetto TableAdapter che si desidera utilizzare.  
  
     [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_1.vb)]
     [!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_1.cs)]  
  
#### <a name="to-update-records-directly-in-a-database"></a>Per aggiornare i record direttamente in un database  
  
-   Chiamare il TableAdapter `Update` , passando i valori nuovi e originali per ogni colonna come parametri.  
  
    > [!NOTE]
    >  Se non si dispone di un'istanza disponibile, creare un'istanza dell'oggetto TableAdapter che si desidera utilizzare.  
  
     [!code-vb[VbRaddataSaving#18](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_2.vb)]
     [!code-csharp[VbRaddataSaving#18](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_2.cs)]  
  
#### <a name="to-delete-records-directly-from-a-database"></a>Per eliminare i record direttamente da un database  
  
-   Chiamata dell'oggetto TableAdapter `Delete` passando i valori per ogni colonna come parametri del metodo di `Delete` metodo. La procedura seguente usa il `Region` tabella nel database Northwind come esempio.  
  
    > [!NOTE]
    >  Se non si dispone di un'istanza disponibile, creare un'istanza dell'oggetto TableAdapter che si desidera utilizzare.  
  
     [!code-vb[VbRaddataSaving#21](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_3.vb)]
     [!code-csharp[VbRaddataSaving#21](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_3.cs)]  
  
## <a name="see-also"></a>Vedere anche  
 [Compilare i set di dati usando oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)