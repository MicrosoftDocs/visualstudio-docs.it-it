---
title: Aggiornare i dati mediante un TableAdapter
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], saving
- data [Visual Studio], TableAdapters
- updating data, TableAdapters
- TableAdapters, updating data
- data [Visual Studio], updating
- saving data
ms.assetid: 5e32e10e-9bac-4969-9bdd-b8f6919d3516
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 05a61aa42c086ba3fd0a71fa221426c763df14d7
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="update-data-by-using-a-tableadapter"></a>Aggiornare i dati mediante un TableAdapter

Dopo aver modificati e convalidare i dati nel set di dati, è possibile inviare i dati aggiornati in un database tramite la chiamata di `Update` metodo di un [TableAdapter](../data-tools/create-and-configure-tableadapters.md). Il `Update` metodo aggiorna una singola tabella di dati ed esegue il comando corretto (INSERT, UPDATE o DELETE) in base il <xref:System.Data.DataRow.RowState%2A> di ogni riga di dati nella tabella. Quando un set di dati con le tabelle correlate, Visual Studio genera una classe TableAdapterManager utilizzato per gli aggiornamenti. La classe TableAdapterManager garantisce che gli aggiornamenti vengono eseguiti nell'ordine corretto in base ai vincoli di chiave esterna che sono definiti nel database. Quando si utilizzano controlli con associazione a dati, l'architettura di associazione dati crea una variabile membro della classe TableAdapterManager chiamata tableAdapterManager.

> [!NOTE]
> Quando si tenta di aggiornare un'origine dati con il contenuto di un set di dati, è possibile ottenere gli errori. Per evitare errori, è consigliabile inserire il codice che chiama l'adapter `Update` metodo all'interno di un `try` / `catch` blocco.

 La procedura esatta per l'aggiornamento di un'origine dati può variare a seconda delle esigenze aziendali, ma include i passaggi seguenti:

1.  Chiamare l'adapter `Update` metodo in un `try` / `catch` blocco.

2.  Se viene intercettata un'eccezione, individuare la riga di dati che ha causato l'errore.

3.  Risolvere il problema nei dati di riga (a livello di codice, se possibile, o presentando la riga non valida per l'utente per la modifica) e quindi riprovare a eseguire l'aggiornamento (<xref:System.Data.DataRow.HasErrors%2A>, <xref:System.Data.DataTable.GetErrors%2A>).

## <a name="save-data-to-a-database"></a>Salvare i dati in un database

Chiamare il `Update` metodo di un oggetto TableAdapter. Passare il nome della tabella dati contenente i valori da scrivere nel database.

### <a name="to-update-a-database-by-using-a-tableadapter"></a>Per aggiornare un database mediante un TableAdapter

-   Racchiudere il TableAdapter`Update` metodo in un `try` / `catch` blocco. Nell'esempio seguente viene illustrato come aggiornare il contenuto del `Customers` tabella `NorthwindDataSet` dall'interno un `try` / `catch` blocco.

     [!code-csharp[VbRaddataSaving#9](../data-tools/codesnippet/CSharp/update-data-by-using-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataSaving#9](../data-tools/codesnippet/VisualBasic/update-data-by-using-a-tableadapter_1.vb)]

## <a name="see-also"></a>Vedere anche

- [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)