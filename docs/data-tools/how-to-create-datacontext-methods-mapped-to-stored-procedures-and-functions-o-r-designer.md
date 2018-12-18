---
title: 'Procedura: creare metodi DataContext mappati a stored procedure e funzioni (O-R Designer) | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: a56bacfd2d726e2ec7bedf69f6c79ce347e3556e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>Procedura: creare metodi DataContext mappati a stored procedure e funzioni (O/R Designer)
Stored procedure e funzioni possono essere aggiunti al [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] come <xref:System.Data.Linq.DataContext> metodi. La chiamata al metodo e passando i parametri obbligatori viene eseguita la stored procedure o funzione nel database e restituisce i dati nel tipo restituito del <xref:System.Data.Linq.DataContext> metodo. Per informazioni dettagliate su <xref:System.Data.Linq.DataContext> metodi, vedere [metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).  
  
> [!NOTE]
>  Le stored procedure possono essere usate anche per eseguire l'override del comportamento in fase di esecuzione [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] predefinito che esegue i comandi di inserimento, aggiornamento ed eliminazione durante il salvataggio delle modifiche dalle classi di entità in un database. Per ulteriori informazioni, vedere [procedura: assegnare stored procedure per eseguire aggiornamenti, inserimenti ed eliminazioni (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
## <a name="creating-datacontext-methods"></a>Creazione di metodi DataContext  
 È possibile creare <xref:System.Data.Linq.DataContext> metodi trascinando stored procedure o funzioni da **Esplora Server/Esplora Database** sul [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
> [!NOTE]
>  Il tipo restituito del metodo <xref:System.Data.Linq.DataContext> generato varia a seconda della posizione in cui si rilascia la stored procedure o funzione in [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Il rilascio degli elementi direttamente in una classe di entità esistente crea un metodo <xref:System.Data.Linq.DataContext> con il tipo restituito della classe di entità, mentre il rilascio degli elementi in un'area vuota di [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] crea un metodo <xref:System.Data.Linq.DataContext> che restituisce un tipo generato automaticamente. È possibile modificare il tipo restituito di un <xref:System.Data.Linq.DataContext> metodo dopo averlo aggiunto al riquadro dei metodi. Per controllare o modificare il tipo restituito di un <xref:System.Data.Linq.DataContext> (metodo), selezionarlo e controllare il **Return Type** proprietà il **proprietà** finestra. Per ulteriori informazioni, vedere [procedura: modificare il tipo restituito di un metodo DataContext (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>Per creare metodi DataContext che restituiscono tipi generati automaticamente  
  
1.  In **Esplora Server**/**Esplora Database**, espandere il **Stored procedure** nodo del database in uso.  
  
2.  Individuare la stored procedure desiderata e trascinarla in un'area vuota di [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
     Il <xref:System.Data.Linq.DataContext> (metodo) viene creato con un tipo restituito generato automaticamente e visualizzato nel **metodi** riquadro.  
  
#### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>Per creare metodi DataContext con il tipo restituito di una classe di entità  
  
1.  In **Esplora Server**/**Esplora Database**, espandere il **Stored procedure** nodo del database in uso.  
  
2.  Individuare la stored procedure desiderata e trascinarla in una classe di entità esistente di [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
     Il <xref:System.Data.Linq.DataContext> metodo viene creato con il tipo restituito della classe di entità selezionata e viene visualizzato nel **metodi** riquadro.  
  
> [!NOTE]
>  Per informazioni sulla modifica del tipo restituito di esistente <xref:System.Data.Linq.DataContext> metodi, vedere [procedura: modificare il tipo restituito di un metodo DataContext (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
## <a name="see-also"></a>Vedere anche  
 [LINQ to SQL Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Procedura dettagliata: Creazione di classi LINQ to SQL](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)   
 [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)   
 [Introduzione a LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ in C#](/dotnet/csharp/linq/linq-in-csharp)