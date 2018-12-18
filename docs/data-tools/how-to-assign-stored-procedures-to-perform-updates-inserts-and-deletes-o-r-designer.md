---
title: Usa stored procedure per eseguire l'aggiornamento, inserimento ed eliminazione in Linq to SQL O/R Designer | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 20669a4ec19865e99a9498e87e896aa645321257
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-or-designer"></a>Procedura: assegnare stored procedure per eseguire aggiornamenti, inserimenti ed eliminazioni (O/R Designer)
È possibile aggiungere a Progettazione relazionale oggetti stored procedure ed eseguirle come metodi <xref:System.Data.Linq.DataContext> tipici. Possono inoltre essere utilizzati per sostituire il valore predefinito [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] il comportamento di runtime che esegue inserimenti, aggiornamenti ed eliminazione durante il salvataggio delle modifiche dalle classi di entità a un database (ad esempio, quando si chiama il <xref:System.Data.Linq.DataContext.SubmitChanges%2A> (metodo)).  
  
> [!NOTE]
>  Se le stored procedure restituiscono valori che devono essere inviati al client, ad esempio valori calcolati nelle stesse stored procedure, creare parametri di output all'interno di esse. Se non è possibile usare parametri di output, è preferibile scrivere l'implementazione di un metodo parziale anziché basarsi sugli override generati da Progettazione relazionale oggetti. I membri con mapping ai valori generati dal database devono essere impostati su valori appropriati dopo il completamento delle operazioni INSERT o UPDATE. Per ulteriori informazioni, vedere [responsabilità dello sviluppatore nell'override del comportamento predefinito](/dotnet/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior).  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] gestisce automaticamente i valori generati dal database per le colonne identity (incremento automatico) e rowguidcol (GUID generato dal database) e timestamp. I valori degli altri tipi di colonne sono costituiti da valori null non previsti. Per restituire i valori generati dal database, è necessario impostare manualmente <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> su `true` e <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> su uno dei seguenti valori: <xref:System.Data.Linq.Mapping.AutoSync>, <xref:System.Data.Linq.Mapping.AutoSync> o <xref:System.Data.Linq.Mapping.AutoSync>.  
  
## <a name="configuring-the-update-behavior-of-an-entity-class"></a>Configurazione del comportamento di aggiornamento di un classe di entità  
 Per impostazione predefinita, la logica per aggiornare un database (inserimenti, aggiornamenti ed eliminazioni) con le modifiche apportate ai dati di [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] classi di entità viene eseguito il [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] runtime. Il runtime crea impostazione predefinita i comandi INSERT, UPDATE e DELETE che si basano le lo schema della tabella (la colonna e informazioni sulla chiave primarie). Quando il comportamento predefinito non è necessaria, è possibile configurare il comportamento di aggiornamento assegnando stored procedure specifiche per l'esecuzione di comandi di inserimento, aggiornamenti ed eliminazioni necessarie per modificare i dati nella tabella. Questa operazione può essere eseguita anche quando non viene generato il comportamento predefinito, ad esempio quando viene eseguito il mapping delle classi di entità alle visualizzazioni. Infine, è possibile eseguire l'override del comportamento di aggiornamento predefinito quando il database richiede l'accesso alla tabella tramite stored procedure.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-assign-stored-procedures-to-override-the-default-behavior-of-an-entity-class"></a>Per assegnare stored procedure per l'override del comportamento predefinito di una classe di entità  
  
1.  Aprire il **LINQ to SQL** file nella finestra di progettazione. (Fare doppio clic sul file. dbml in **Esplora**.)  
  
2.  In **Esplora Server**/**Esplora Database**, espandere **Stored procedure** e individuare le stored procedure che si desidera utilizzare per l'inserimento, aggiornamento e/o i comandi di eliminazione della classe di entità.  
  
3.  Trascinare la stored procedure in Progettazione relazionale oggetti.  
  
     La stored procedure viene aggiunta al riquadro dei metodi come metodo <xref:System.Data.Linq.DataContext>. Per ulteriori informazioni, vedere [metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).  
  
4.  Selezionare la classe di entità per cui si desidera usare la stored procedure per eseguire gli aggiornamenti.  
  
5.  Nel **proprietà** finestra, selezionare il comando per eseguire l'override (**inserire**, **aggiornamento**, o **eliminare**).  
  
6.  Fare clic sui puntini di sospensione (...) accanto alle parole **Usa fase di esecuzione** per aprire la **Configura comportamento** la finestra di dialogo.  
  
7.  Selezionare **personalizzare**.  
  
8.  Selezionare la stored procedure desiderata nel **Personalizza** elenco.  
  
9. Controllare l'elenco di **gli argomenti del metodo** e **proprietà della classe** per verificare che il **gli argomenti del metodo** mappa appropriati **proprietà della classe**. Eseguire il mapping degli argomenti di metodo originali (Original _*NomeArgomento*) alle proprietà originali (*PropertyName* (Original)) per i comandi Update e Delete.  
  
    > [!NOTE]
    >  Per impostazione predefinita, viene eseguito il mapping degli argomenti di metodo alle proprietà di classe quando i nomi corrispondono. Se non vi è più corrispondenza tra i nomi modificati nella tabella e nella classe di entità, potrebbe essere necessario selezionare la proprietà di classe equivalente a cui eseguire il mapping nel caso in cui la finestra di progettazione non sia in grado di determinare il mapping corretto.  
  
10. Fare clic su **OK** o **applicare**.  
  
    > [!NOTE]
    >  È possibile continuare a configurare il comportamento per ogni combinazione di classe/comportamento purché faccia clic su **applica** dopo ogni modifica apportata. Se si modifica la classe o il comportamento prima di scegliere **applica**, una finestra di dialogo di avviso offre la possibilità di applicare le modifiche verrà visualizzati.  
  
Per ripristinare l'utilizzo della logica di runtime predefinita per gli aggiornamenti, fare clic sui puntini di sospensione accanto a Insert, Update, comando o eliminazione nel **proprietà** finestra e quindi selezionare **utilizzare runtime** nel  **Configurare il comportamento** la finestra di dialogo.  
  
## <a name="see-also"></a>Vedere anche
[Gli strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
[Metodi DataContext](../data-tools/datacontext-methods-o-r-designer.md)   
[LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)   
[Inserimento, aggiornamento ed eliminazione di operazioni (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/insert-update-and-delete-operations)