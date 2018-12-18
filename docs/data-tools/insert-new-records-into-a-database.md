---
title: Inserire nuovi record in un database
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, inserting new records into
- data [Visual Studio], saving
- databases, inserting new records into
- records, inserting
- saving data
ms.assetid: ea118fff-69b1-4675-b79a-e33374377f04
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 8ec5ee4a56e36696ca88f032c3e2cf2622170f96
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="insert-new-records-into-a-database"></a>Inserire nuovi record in un database
Per inserire nuovi record in un database, è possibile utilizzare il `TableAdapter.Update` metodo, o uno dei metodi DBDirect di TableAdapter (in particolare il `TableAdapter.Insert` (metodo)). Per ulteriori informazioni, vedere [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

 Se l'applicazione non utilizza gli oggetti TableAdapter, è possibile utilizzare gli oggetti comando (ad esempio, <xref:System.Data.SqlClient.SqlCommand>) per inserire nuovi record nel database.

 Se l'applicazione utilizza set di dati per archiviare i dati, utilizzare il `TableAdapter.Update` metodo. Il `Update` metodo invia tutte le modifiche (aggiornamenti, inserimenti ed eliminazioni) al database.

 Se l'applicazione utilizza oggetti per archiviare i dati oppure, se si desidera un maggiore controllo sulla creazione di nuovi record nel database, utilizzare il `TableAdapter.Insert` metodo.

 Se l'oggetto TableAdapter non ha un `Insert` (metodo), significa che il TableAdapter è configurato per utilizzare le stored procedure o dai relativi `GenerateDBDirectMethods` è impostata su `false`. Provare a impostare il TableAdapter `GenerateDBDirectMethods` proprietà `true` dall'interno di **Progettazione Dataset**e quindi salvare il set di dati. Il TableAdapter verrà rigenerata. Se il TableAdapter non è presente un `Insert` (metodo), quindi la tabella non vengono fornite informazioni di schema sufficienti per distinguere tra righe singole (ad esempio, non potrebbero esserci alcun set di chiave primaria nella tabella).

## <a name="insert-new-records-by-using-tableadapters"></a>Inserire nuovi record con gli oggetti TableAdapter
 Gli oggetti TableAdapter forniscono diversi modi per inserire nuovi record in un database, a seconda dei requisiti dell'applicazione.

 Se l'applicazione utilizza set di dati per archiviare i dati, quindi è possibile aggiungere nuovi record semplicemente all'oggetto desiderato <xref:System.Data.DataTable> nel set di dati e quindi chiamare il `TableAdapter.Update` metodo. Il `TableAdapter.Update` metodo invia tutte le modifiche di <xref:System.Data.DataTable> al database (inclusi i record modificati ed eliminati).

#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>Per inserire nuovi record in un database utilizzando il metodo di TableAdapter

1.  Aggiunta di nuovi record all'oggetto desiderato <xref:System.Data.DataTable> creando un nuovo <xref:System.Data.DataRow> e aggiungendolo al <xref:System.Data.DataTable.Rows%2A> insieme.

2.  Dopo aver aggiunto le nuove righe di <xref:System.Data.DataTable>, chiamare il `TableAdapter.Update` metodo. È possibile controllare la quantità di dati per aggiornare passando un un'intera <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, una matrice di <xref:System.Data.DataRow>s o un singolo oggetto <xref:System.Data.DataRow>.

 Il codice seguente viene illustrato come aggiungere un nuovo record per un <xref:System.Data.DataTable> e quindi chiamare il `TableAdapter.Update` per salvare la nuova riga per il database. (Questo esempio viene utilizzato il `Region` tabella nel database Northwind.)

 [!code-vb[VbRaddataSaving#14](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_1.vb)]
 [!code-csharp[VbRaddataSaving#14](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_1.cs)]

#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>Per inserire nuovi record in un database utilizzando il metodo di TableAdapter
Se l'applicazione utilizza oggetti per archiviare i dati, è possibile utilizzare il `TableAdapter.Insert` metodo per creare nuove righe direttamente nel database. Il `Insert` metodo accetta i singoli valori per ogni colonna come parametri. La chiamata al metodo inserisce un nuovo record nel database con i valori dei parametri passati.

- Chiamare il TableAdapter `Insert` , passando i valori per ogni colonna come parametri.

 La procedura seguente viene illustrato l'utilizzo di `TableAdapter.Insert` per inserire righe. In questo esempio consente di inserire dati nel `Region` tabella nel database Northwind.

 > [!NOTE]
 >  Se non si dispone di un'istanza disponibile, creare un'istanza dell'oggetto TableAdapter che si desidera utilizzare.

 [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_2.vb)]
 [!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_2.cs)]

## <a name="insert-new-records-by-using-command-objects"></a>Inserire nuovi record con gli oggetti comando
È possibile inserire nuovi record direttamente in un database utilizzando oggetti comando.

#### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>Per inserire nuovi record in un database utilizzando oggetti comando

-   Creare un nuovo oggetto comando e quindi impostare il relativo `Connection`, `CommandType`, e `CommandText` proprietà.

 Nell'esempio seguente viene illustrato l'inserimento di record in un database utilizzando l'oggetto comando. Inserisce dati nel `Region` tabella nel database Northwind.

 [!code-vb[VbRaddataSaving#16](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_3.vb)]
 [!code-csharp[VbRaddataSaving#16](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_3.cs)]

## <a name="net-framework-security"></a>Sicurezza di .NET Framework
 È necessario avere accesso a cui si sta tentando di connettersi al database, nonché dell'autorizzazione per eseguire l'inserimento nella tabella desiderata.

## <a name="see-also"></a>Vedere anche

- [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)