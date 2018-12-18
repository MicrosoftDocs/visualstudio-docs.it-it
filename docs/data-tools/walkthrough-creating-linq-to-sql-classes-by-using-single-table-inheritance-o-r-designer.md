---
title: "Procedura dettagliata: Creazione di classi LINQ to SQL tramite ereditarietà a tabella singola (O-R Designer) | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
ms.assetid: 63bc6328-e0df-4655-9ce3-5ff74dbf69a4
caps.latest.revision: "4"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: b6e255492f0859689b41723657338140ffee5931
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-or-designer"></a>Procedura dettagliata: creazione di classi LINQ to SQL tramite ereditarietà a una sola tabella (O/R Designer)
Il [LINQ to SQL Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) supporta l'ereditarietà a tabella singola come viene in genere implementato nei sistemi relazionali. Questa procedura dettagliata espande i passaggi generici forniti nel [procedura: configurare l'ereditarietà tramite O/R Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) argomento e fornisce alcuni dati reali per illustrare l'utilizzo dell'ereditarietà nel [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
 In particolare, verranno illustrate le attività seguenti:  
  
-   Creazione di una tabella di database e aggiunta di dati ad essa.  
  
-   Creazione di un'applicazione Windows Form.  
  
-   Aggiunta di un file [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] a un progetto.  
  
-   Creazione di nuove classi di entità.  
  
-   Configurazione delle classi di entità per l'uso dell'ereditarietà.  
  
-   Esecuzione di una query sulla classe ereditata.  
  
-   Visualizzazione dei dati in un Windows Form.  
  
## <a name="create-a-table-to-inherit-from"></a>Creazione di una tabella da cui ereditare  
 Per verificare il funzionamento dell'ereditarietà, verrà creata una piccola tabella Person, usata come classe di base, e verrà creato quindi un oggetto Employee che eredita dalla tabella.  
  
#### <a name="to-create-a-base-table-to-demonstrate-inheritance"></a>Per creare una tabella di base per l'illustrazione dell'ereditarietà  
  
1.  In **Esplora Server**/**Esplora Database**, fare doppio clic su di **tabelle** nodo e fare clic su **Aggiungi nuova tabella**.  
  
    > [!NOTE]
    >  È possibile usare il database Northwind o qualsiasi altro database a cui sia possibile aggiungere una tabella.  
  
2.  In Progettazione tabelle aggiungere le seguenti colonne alla tabella:  
  
    |Nome colonna|Tipo di dati|Ammetti Null|  
    |-----------------|---------------|-----------------|  
    |**ID**|**int**|**False**|  
    |**Type**|**int**|**True**|  
    |**FirstName**|**nvarchar (200)**|**False**|  
    |**Cognome**|**nvarchar (200)**|**False**|  
    |**Manager**|**int**|**True**|  
  
3.  Impostare la colonna ID come chiave primaria.  
  
4.  Salvataggio della tabella e denominarla **persona**.  
  
## <a name="add-data-to-the-table"></a>Aggiunta di dati alla tabella  
 Allo scopo di verificare che l'ereditarietà sia configurata correttamente, è necessario aggiungere alcuni dati alla tabella per ogni classe nell'ereditarietà a tabella singola.  
  
#### <a name="to-add-data-to-the-table"></a>Per aggiungere dati alla tabella  
  
1.  Aprire la tabella nella visualizzazione dati (Fare doppio clic su di **persona** tabella **Esplora Server**/**Esplora Database** e fare clic su **Mostra dati tabella**.)  
  
2.  Copiare i dati riportati di seguito nella tabella (È possibile copiarlo e quindi incollarlo nella tabella selezionando l'intera riga nel riquadro dei risultati.)  
  
    ||||||  
    |-|-|-|-|-|  
    |**ID**|**Type**|**FirstName**|**Cognome**|**Manager**|  
    |**1**|**1**|**Anne**|**Wallace**|**NULL**|  
    |**2**|**1**|**Carlos**|**Grilo**|**NULL**|  
    |**3**|**1**|**Yael**|**Peled**|**NULL**|  
    |**4**|**2**|**Gatis**|**Ozolins**|**1**|  
    |**5**|**2**|**Andreas**|**Luca Argentiero**|**1**|  
    |**6**|**2**|**Tiffany**|**Phuvasate**|**1**|  
    |**7**|**2**|**Alexey**|**Orekhov**|**2**|  
    |**8**|**2**|**Michał**|**Poliszkiewicz**|**2**|  
    |**9**|**2**|**Tai**|**Yee**|**2**|  
    |**10**|**2**|**Fabricio**|**Noriega**|**3**|  
    |**11**|**2**|**Barbara**|**Martin**|**3**|  
    |**12**|**2**|**Davide**|**Kwok**|**3**|  
  
## <a name="create-a-new-project"></a>Creazione di un nuovo progetto  
 Una volta creata la tabella, creare un nuovo progetto per illustrare la configurazione dell'ereditarietà.  
  
#### <a name="to-create-the-new-windows-forms-application"></a>Per creare la nuova applicazione Windows Form  
  
1. In Visual Studio, sul **File** dal menu **New**, **progetto...** .  
  
2. Espandere **Visual c#** o **Visual Basic** nel riquadro a sinistra, quindi selezionare **Windows Desktop classico**.  

3. Nel riquadro centrale, selezionare il **App di Windows Form** tipo di progetto.  

4. Denominare il progetto **InheritanceWalkthrough**, quindi scegliere **OK**. 
  
     Il **InheritanceWalkthrough** progetto viene creato e aggiunto a **Esplora**.  
  
## <a name="add-a-linq-to-sql-classes-file-to-the-project"></a>Aggiunta di un file di classi LINQ to SQL al progetto  
  
#### <a name="to-add-a-linq-to-sql-file-to-the-project"></a>Per aggiungere un file LINQ to SQL al progetto  
  
1.  Nel menu **Progetto** fare clic su **Aggiungi nuovo elemento**.  
  
2.  Fare clic su di **classi LINQ to SQL** modello e quindi fare clic su **Aggiungi**.  
  
     Il file .dbml viene aggiunto al progetto e viene aperto [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
## <a name="create-the-inheritance-by-using-the-or-designer"></a>Creazione dell'ereditarietà usando Progettazione relazionale oggetti  
 Configurare l'ereditarietà trascinando un **ereditarietà** dall'oggetto di **della casella degli strumenti** nell'area di progettazione.  
  
#### <a name="to-create-the-inheritance"></a>Per creare l'ereditarietà  
  
1.  In **Esplora Server**/**Esplora Database**, passare il **persona** tabella creata in precedenza.  
  
2.  Trascinare il **persona** tabella il [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] area di progettazione.  
  
3.  Trascinare una seconda **persona** tabella il [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] e impostarne il nome su **dipendente**.  
  
4.  Eliminare il **Manager** proprietà il **persona** oggetto.  
  
5.  Eliminare il **tipo**, **ID**, **FirstName**, e **LastName** le proprietà di **dipendente** oggetto. (In altre parole, eliminare tutte le proprietà, ad eccezione di **Manager**.)  
  
6.  Dal **Object Relational Designer** scheda della finestra il **della casella degli strumenti**, creare un **ereditarietà** tra il **persona** e  **Dipendente** oggetti. A tale scopo, fare clic su di **ereditarietà** elemento il **della casella degli strumenti** e rilasciare il pulsante del mouse. Successivamente, fare clic sul **dipendente** oggetto e quindi la **persona** oggetto di [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. La freccia della linea di ereditarietà punterà al **persona** oggetto.  
  
7.  Fare clic su di **ereditarietà** riga nell'area di progettazione.  
  
8.  Impostare il **proprietà Discriminator** proprietà **tipo**.  
  
9. Impostare il **Derived Class Discriminator Value** proprietà **2**.  
  
10. Impostare il **Base Class Discriminator Value** proprietà **1**.  
  
11. Impostare il **Inheritance Default** proprietà **persona**.  
  
12. Compilare il progetto.  
  
## <a name="query-the-inherited-class-and-display-the-data-on-the-form"></a>Esecuzione di una query sulla classe ereditata e visualizzazione dei dati nel form  
 A questo punto si aggiungerà codice al form che esegue una query per una classe specifica nel modello a oggetti.  
  
#### <a name="to-create-a-linq-query-and-display-the-results-on-the-form"></a>Per creare una query LINQ e visualizzare i risultati nel form  
  
1.  Trascinare un **ListBox** in Form1.  
  
2.  Fare doppio clic sul form per creare un gestore dell'evento `Form1_Load`.  
  
3.  Aggiungere il codice seguente al gestore eventi `Form1_Load`:  
  
    ```vb  
    Dim dc As New DataClasses1DataContext  
    Dim results = From emp In dc.Persons _  
        Where TypeOf emp Is Employee _  
        Select emp  
  
    For Each Emp As Employee In results  
        ListBox1.Items.Add(Emp.LastName)  
    Next  
    ```  
  
    ```csharp  
    NorthwindDataContext dc = new DataClasses1DataContext();  
    var results = from emp in dc.Persons  
                  where emp is Employee  
                  select emp;  
  
    foreach(Employee Emp in results)  
    {  
        listBox1.Items.Add(Emp.LastName)  
    }  
    ```  
  
## <a name="test-the-application"></a>Test dell'applicazione  
 Eseguire l'applicazione e verificare che i record visualizzati nella casella di riepilogo rappresentino tutti i dipendenti (record che presentano il valore 2 nella rispettiva colonna Type).  
  
#### <a name="to-test-the-application"></a>Per eseguire il test dell'applicazione  
  
1.  Premere F5.  
  
2.  Verificare che siano visualizzati solo i record che presentano il valore 2 nella rispettiva colonna Type.  
  
3.  Chiudere il form. (Nel **Debug** menu, fare clic su **Termina debug**.)  
  
## <a name="see-also"></a>Vedere anche  
 [LINQ to SQL Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Procedura dettagliata: Creazione di classi LINQ to SQL (O-R Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)   
 [Procedura: assegnare stored procedure per eseguire aggiornamenti, inserimenti ed eliminazioni (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)   
 [Procedura: Generare il modello a oggetti in Visual Basic o C#](/dotnet/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp)