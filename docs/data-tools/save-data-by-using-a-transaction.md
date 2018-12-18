---
title: 'Procedura: salvare dati utilizzando una transazione | Documenti Microsoft'
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
- saving data, using transactions
- System.Transactions namespace
- transactions, saving data
- data [Visual Studio], saving
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 9f2373e3a851899d139360caf0f6bb8b6ab0efa5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-save-data-by-using-a-transaction"></a>Procedura: salvare dati utilizzando una transazione
Salvare i dati in una transazione utilizzando il <xref:System.Transactions> dello spazio dei nomi. Utilizzare il <xref:System.Transactions.TransactionScope> oggetto di partecipare a una transazione che viene gestita automaticamente.  
  
I progetti non vengono creati con un riferimento all'assembly System. Transactions, pertanto è necessario aggiungere manualmente un riferimento a progetti che utilizzano le transazioni.  
  
Il modo più semplice per implementare una transazione viene creata un'istanza un <xref:System.Transactions.TransactionScope> dell'oggetto un `using` istruzione. (Per ulteriori informazioni, vedere [istruzione Using](/dotnet/visual-basic/language-reference/statements/using-statement), e [utilizzando l'istruzione](/dotnet/csharp/language-reference/keywords/using-statement).) Il codice eseguito all'interno di `using` istruzione partecipa alla transazione.  
  
Per eseguire il commit della transazione, chiamare il <xref:System.Transactions.TransactionScope.Complete%2A> bloccare l'ultima istruzione nel usando il metodo.  
  
Per eseguire il rollback della transazione, generare un'eccezione prima di chiamare il <xref:System.Transactions.TransactionScope.Complete%2A> metodo.  
  
## <a name="to-add-a-reference-to-the-systemtransactionsdll"></a>Per aggiungere un riferimento per il file System.Transactions.dll  
  
1.  Nel **progetto** dal menu **Aggiungi riferimento**.  
  
2.  Nel **.NET** scheda (**SQL Server** scheda per i progetti di SQL Server), selezionare **System. Transactions**, quindi selezionare **OK**.  
  
     Per il progetto viene aggiunto un riferimento a System.Transactions.dll.  
  
## <a name="to-save-data-in-a-transaction"></a>Per salvare i dati in una transazione  
  
-   Aggiungere il codice per salvare i dati di usando l'istruzione che contiene la transazione. Il codice seguente viene illustrato come creare e creare un'istanza di un <xref:System.Transactions.TransactionScope> oggetto in un utilizzando istruzione:  
  
     [!code-vb[VbRaddataSaving#11](../data-tools/codesnippet/VisualBasic/save-data-by-using-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#11](../data-tools/codesnippet/CSharp/save-data-by-using-a-transaction_1.cs)]  
  
## <a name="see-also"></a>Vedere anche
[Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)  
[Procedura dettagliata: Salvare dati in una transazione](../data-tools/save-data-in-a-transaction.md)  