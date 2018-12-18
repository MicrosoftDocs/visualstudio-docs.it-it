---
title: "Procedura: configurare l'ereditarietà utilizzando la finestra di progettazione O-R | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
caps.latest.revision: "4"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: b53dec270481ca8aa6009b9ddd27bdcdfeae6037
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-inheritance-by-using-the-or-designer"></a>Procedura: configurare l'ereditarietà tramite O/R Designer
[!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] ([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]) supporta il concetto di ereditarietà a tabella singola in quanto viene spesso implementato nei sistemi relazionali. Nell'ereditarietà a tabella singola, è presente una singola tabella di database che contiene campi per le informazioni padre e le informazioni figlio. Insieme ai dati relazionali, una colonna discriminatore contiene il valore che determina la classe a cui appartiene un record.  
  
Ad esempio, si consideri una tabella Persons che contiene tutte le persone impiegate in una società, alcune delle quali sono dipendenti mentre altre sono manager. La tabella Persons contiene una colonna denominata `EmployeeType` con un valore 1 per i manager e un valore 2 per i dipendenti e che costituisce la colonna discriminatore. In questo scenario è possibile creare una sottoclasse di dipendenti e popolarla solo con i record che hanno un valore 2 in `EmployeeType`. È anche possibile rimuovere le colonne non appropriate da ognuna delle classi.  
  
La creazione di un modello a oggetti che usa l'ereditarietà (e corrisponde ai dati relazionali) può generare una certa confusione. Nella procedura riportata di seguito vengono illustrati i passaggi necessari per la configurazione dell'ereditarietà con Progettazione relazionale oggetti. Poiché potrebbe essere difficile seguire passaggi generici senza fare riferimento a una tabella e a colonne esistenti, viene fornita una procedura dettagliata in cui vengono usati dati effettivi. Per istruzioni dettagliate per la configurazione dell'ereditarietà utilizzando il [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], vedere [procedura dettagliata: creazione di classi LINQ to SQL da tramite ereditarietà a tabella singola (O/R Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md).  
  
## <a name="to-create-inherited-data-classes"></a>Per creare classi di dati ereditate
  
1.  Aprire il [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] aggiungendo un **classi LINQ to SQL** elemento a un progetto di Visual Basic o c# esistente.  
  
2.  Trascinare la tabella che si desidera usare come classe di base in [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
3.  Trascinare una seconda copia della tabella nel [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] e rinominarlo. In tal modo si otterrà la classe derivata o sottoclasse.  
  
4.  Fare clic su **ereditarietà** nel **Object Relational Designer** scheda della finestra di **della casella degli strumenti**e quindi selezionare la sottoclasse (la tabella rinominata) e connetterla alla classe di base.  
  
    > [!NOTE]
    >  Fare clic su di **ereditarietà** elemento il **della casella degli strumenti** e rilasciare il pulsante del mouse, scegliere la seconda copia della classe creata nel passaggio 3, quindi la prima classe creata nel passaggio 2. La freccia della linea di ereditarietà punterà alla prima classe.  
  
5.  In ogni classe eliminare le proprietà dell'oggetto che non si desidera visualizzare e che non sono usate per le associazioni. Si riceverà un errore se si tenta di eliminare le proprietà dell'oggetto utilizzate per le associazioni: [la proprietà \<nome proprietà > non può essere eliminato perché è inclusa nell'associazione \<nome associazione >](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md).  
  
    > [!NOTE]
    >  Poiché una classe derivata eredita le proprietà definite nella relativa classe di base, non è possibile definire le stesse colonne in ogni classe (le colonne vengono implementate come proprietà). Per consentire la creazione di colonne nella classe derivata, è possibile impostare il modificatore di ereditarietà sulla proprietà della classe di base. Per ulteriori informazioni, vedere [nozioni fondamentali sull'ereditarietà (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics).  
  
6.  Selezionare la linea di ereditarietà in [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
7.  Nel **proprietà** finestra, impostare il **proprietà Discriminator** al nome della colonna che viene utilizzato per distinguere i record nelle classi.  
  
8.  Impostare il **Derived Class Discriminator Value** nel database che designa il record come tipo ereditato il valore della proprietà. (si tratta del valore archiviato nella colonna discriminatore e usato per designare la classe ereditata).  
  
9. Impostare il **Base Class Discriminator Value** sul valore che designa il record come tipo di base. (si tratta del valore archiviato nella colonna discriminatore e usato per designare la classe di base).  
  
10. Facoltativamente, è possibile impostare anche la **Inheritance Default** proprietà per definire un tipo in una gerarchia di ereditarietà utilizzata durante il caricamento di righe che non corrispondono ad alcun codice di ereditarietà definito. In altre parole, se un record include un valore nella relativa colonna discriminatore che non corrisponde al valore nel **Derived Class Discriminator Value** o **Base Class Discriminator Value** proprietà, il record verrà caricato nel tipo designato come il **Inheritance Default**.  
  
## <a name="see-also"></a>Vedere anche
[LINQ to SQL Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
[Procedura dettagliata: Creazione di classi LINQ to SQL (O-R Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)   
[Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)   
[LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)   
[Procedura dettagliata: Creazione di classi LINQ to SQL tramite ereditarietà a tabella singola (O/R Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)   
[Nozioni fondamentali sull'ereditarietà (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)  
[Ereditarietà](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)