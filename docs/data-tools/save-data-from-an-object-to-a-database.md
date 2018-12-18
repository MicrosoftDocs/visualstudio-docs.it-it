---
title: Salvare i dati da un oggetto in un database
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], saving
- data access [Visual Studio], objects
- saving data
ms.assetid: efd6135a-40cf-4b0d-8f8b-41a5aaea7057
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 42bbdb5cff0d244701e28730ab6b12d70b49a920
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="save-data-from-an-object-to-a-database"></a>Salvare i dati da un oggetto in un database
È possibile salvare i dati negli oggetti a un database passando i valori dall'oggetto a uno dei metodi DBDirect di TableAdapter (ad esempio, `TableAdapter.Insert`). Per ulteriori informazioni, vedere [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

 Per salvare i dati da una raccolta di oggetti, scorrere la raccolta di oggetti (ad esempio, un ciclo for-next) e inviare i valori per ogni oggetto al database utilizzando uno dei metodi DBDirect di TableAdapter.

 Per impostazione predefinita, i metodi DBDirect vengono creati in un oggetto TableAdapter che può essere eseguito direttamente nel database. Questi metodi possono essere chiamati direttamente e non richiedono <xref:System.Data.DataSet> o <xref:System.Data.DataTable> oggetti per risolvere le modifiche per inviare gli aggiornamenti a un database.

> [!NOTE]
>  Quando si configura un oggetto TableAdapter, la query principale deve fornire informazioni sufficienti per i metodi DBDirect da creare. Ad esempio, se un oggetto TableAdapter è configurato per eseguire query sui dati da una tabella che non dispone di una colonna chiave primaria definita, non genera DBDirect (metodi).

|Metodo DBDirect di TableAdapter|Descrizione|
|----------------------------------|-----------------|
|`TableAdapter.Insert`|Aggiunge nuovi record in un database e consente di passare valori di singole colonne come parametri di metodo.|
|`TableAdapter.Update`|Aggiorna i record esistenti in un database. Il `Update` accetta valori di colonna originali e quelli nuovi come parametri del metodo. I valori originali vengono utilizzati per individuare il record originale e i nuovi valori vengono utilizzati per aggiornare il record.<br /><br /> Il `TableAdapter.Update` metodo viene utilizzato anche per risolvere le modifiche in un set di dati al database tramite l'aggiunta di un <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, o una matrice di <xref:System.Data.DataRow>come parametri del metodo.|
|`TableAdapter.Delete`|Elimina i record dal database in base ai valori di colonna originale passati come parametri del metodo esistenti.|

### <a name="to-save-new-records-from-an-object-to-a-database"></a>Per salvare i nuovi record da un oggetto in un database

-   Creare i record passando i valori per il `TableAdapter.Insert` metodo.

     L'esempio seguente crea un nuovo record di cliente nel `Customers` tabella passando i valori nel `currentCustomer` dell'oggetto per il `TableAdapter.Insert` metodo.

     [!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_1.cs)]
     [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_1.vb)]

### <a name="to-update-existing-records-from-an-object-to-a-database"></a>Per aggiornare i record esistenti da un oggetto a un database

-   Modificare i record di `TableAdapter.Update` (metodo), passando i nuovi valori per aggiornare il record e i valori originali per individuare il record.

    > [!NOTE]
    >  L'oggetto deve mantenere i valori originali per passarli al `Update` metodo. In questo esempio Usa le proprietà con un `orig` prefisso per archiviare i valori originali.

     Nell'esempio seguente viene aggiornato un record esistente nella `Customers` tabella passando i valori nuovi e originali nel `Customer` dell'oggetto per il `TableAdapter.Update` metodo.

     [!code-csharp[VbRaddataSaving#24](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_2.cs)]
     [!code-vb[VbRaddataSaving#24](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_2.vb)]

### <a name="to-delete-existing-records-from-a-database"></a>Per eliminare i record esistenti da un database

-   Eliminare i record chiamando il `TableAdapter.Delete` metodo e passando i valori originali per individuare il record.

    > [!NOTE]
    >  L'oggetto deve mantenere i valori originali per passarli al `Delete` metodo. In questo esempio Usa le proprietà con un `orig` prefisso per archiviare i valori originali.

     Nell'esempio seguente viene eliminato un record dal `Customers` tabella passando i valori originali nel `Customer` dell'oggetto per il `TableAdapter.Delete` metodo.

     [!code-csharp[VbRaddataSaving#25](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_3.cs)]
     [!code-vb[VbRaddataSaving#25](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_3.vb)]

## <a name="net-framework-security"></a>Sicurezza di .NET Framework
 È necessario disporre dell'autorizzazione per eseguire selezionata INSERT, UPDATE o DELETE sulla tabella nel database.

## <a name="see-also"></a>Vedere anche

- [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)