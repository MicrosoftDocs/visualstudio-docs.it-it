---
title: Ereditarietà delle classi di dati (O-R Designer)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: af32653c-f4e6-4217-8c5a-e32b322b4918
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 7362a396c25adc5b909a92179c32bf7bae5b2fbb
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="data-class-inheritance-or-designer"></a>Ereditarietà delle classi di dati (O/R Designer)

Analogamente ad altri oggetti, le classi [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] possono usare l'ereditarietà ed essere derivate da altre classi. Nel codice è possibile specificare le relazioni di ereditarietà tra oggetti dichiarando che una classe eredita da un'altra. In un database le relazioni di ereditarietà vengono create in diversi modi. [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] ([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]) supporta il concetto di ereditarietà a tabella singola in quanto viene spesso implementato nei sistemi relazionali.

Nell'ereditarietà a tabella singola è presente una singola tabella di database che contiene colonne per le classi base e derivate. Insieme ai dati relazionali, una colonna discriminante contiene il valore che determina la classe a cui appartiene uno specifico record. Ad esempio, si consideri una tabella Persons che contiene tutte le persone impiegate in una società, alcune delle quali sono dipendenti mentre altre sono manager. La tabella Persons contiene una colonna denominata Type, che presenta un valore 1 per i manager e un valore 2 per i dipendenti, e che costituisce la colonna discriminante. In questo scenario, è possibile creare una sottoclasse di dipendenti e popolare la classe solo con i record che hanno un valore 2 nella colonna Type.

Quando si configura l'ereditarietà nelle classi di entità tramite il [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], trascinare la singola tabella che contiene i dati di ereditarietà nella finestra di progettazione due volte: una volta per ogni classe nella gerarchia di ereditarietà. Dopo aver aggiunto le tabelle nella finestra di progettazione, connetterle con un elemento di ereditarietà dal **Object Relational Designer** casella degli strumenti e quindi impostare le quattro proprietà di ereditarietà nel **proprietà** finestra.

## <a name="inheritance-properties"></a>Proprietà di ereditarietà

Nella tabella seguente sono elencate le proprietà di ereditarietà e le rispettive descrizioni:

|Proprietà|Descrizione|
|--------------|-----------------|
|Proprietà Discriminator|Proprietà (mappata alla colonna) che determina a quale classe appartiene il record corrente.|
|Valore discriminante classe base|Valore (nella colonna definita come proprietà Discriminator) che determina che un record fa parte della classe base.|
|Valore discriminante classe derivata|Valore (nella proprietà definita come proprietà Discriminator) che determina che un record fa parte della classe derivata.|
|Valore predefinito di ereditarietà|La classe da popolare quando il valore nella proprietà definita come il **proprietà Discriminator** non corrisponde alla **Base Class Discriminator Value** o **classe derivata Valore discriminante**.|

La creazione di un modello a oggetti che usa l'ereditarietà e corrisponde ai dati relazionali può generare una certa confusione. Questo argomento fornisce informazioni sui concetti di base e sulle proprietà singole richieste per la configurazione dell'ereditarietà. Negli argomenti seguenti viene fornita una spiegazione più chiara di come configurare l'ereditarietà con [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].

|Argomento|Descrizione|
|-----------|-----------------|
|[Procedura: configurare l'ereditarietà tramite O/R Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)|Viene descritto come configurare le classi di entità che usano l'ereditarietà mediante [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].|
|[Procedura dettagliata: Creazione di classi LINQ to SQL tramite ereditarietà a tabella singola (O/R Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)|Vengono fornite istruzioni dettagliate per la configurazione delle classi di entità che usano l'ereditarietà a tabella singola con [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].|

## <a name="see-also"></a>Vedere anche

- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Procedura dettagliata: Creazione di classi LINQ to SQL (O-R Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Procedura dettagliata: Creazione di classi LINQ to SQL tramite ereditarietà a tabella singola (O/R Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [Introduzione](/dotnet/framework/data/adonet/sql/linq/getting-started)