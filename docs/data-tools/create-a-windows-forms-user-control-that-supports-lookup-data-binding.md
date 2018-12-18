---
title: Utilizzo di tabelle di ricerca nel data binding, controlli Windows Form | Documenti Microsoft
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
- data binding, user controls
- LookupBindingPropertiesAttribute class, examples
- user controls [Visual Basic], creating
ms.assetid: c48b4d75-ccfc-4950-8b14-ff8adbfe4208
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 8c17803a6a1f0f2681b7b1c8510ebe66072c9c38
ms.sourcegitcommit: 49aa031cbebdd9c7ec070c713afb1a97d1ecb701
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2018
---
# <a name="create-a-windows-forms-user-control-that-supports-lookup-data-binding"></a>Creare un controllo utente Windows Form che supporta l'associazione di dati di ricerca
Quando si visualizzano dati nei Windows Form, è possibile scegliere i controlli esistenti dal **della casella degli strumenti**, oppure è possibile creare controlli personalizzati se l'applicazione richiede funzionalità non disponibili nei controlli standard. In questa procedura dettagliata è illustrato come creare un controllo che implementa <xref:System.ComponentModel.LookupBindingPropertiesAttribute>. I controlli che implementano <xref:System.ComponentModel.LookupBindingPropertiesAttribute> possono contenere tre proprietà associabili ai dati. Tali controlli sono simili a <xref:System.Windows.Forms.ComboBox>.  
  
 Per ulteriori informazioni sulla creazione di controlli, vedere [lo sviluppo di controlli Windows Form in fase di progettazione](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).  
  
 Quando si creano controlli da usare in scenari di associazione di dati è necessario implementare uno degli attributi di associazione di dati seguenti:  
  
|Utilizzo dell'attributo di associazione dati|  
|-----------------------------------|  
|Implementare <xref:System.ComponentModel.DefaultBindingPropertyAttribute> su controlli semplici, ad esempio <xref:System.Windows.Forms.TextBox>, che visualizzano una singola colonna, o proprietà, di dati. Per ulteriori informazioni, vedere [creare un controllo utente Windows Form che supporta l'associazione dati semplice](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|  
|Implementare <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> su controlli, ad esempio <xref:System.Windows.Forms.DataGridView>, che visualizzano elenchi, o tabelle, di dati. Per ulteriori informazioni, vedere [creare un controllo utente Windows Form che supporta l'associazione dati complessa](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|  
|Implementare <xref:System.ComponentModel.LookupBindingPropertiesAttribute> su controlli, ad esempio <xref:System.Windows.Forms.ComboBox>, che visualizzano elenchi, o tabelle, di dati ma che devono anche presentare una singola colonna o proprietà. Il processo è descritto in questa pagina di procedura dettagliata.|  
  
 Questa procedura dettagliata crea un controllo di ricerca che effettua l'associazione ai dati di due tabelle. Questo esempio usa le tabelle `Customers` e `Orders` del database di esempio Northwind. Il controllo di ricerca verrà associato al campo `CustomerID` dalla tabella `Orders`. Userà questo valore per eseguire la ricerca di `CompanyName` dalla tabella `Customers`.  
  
 Durante questa procedura dettagliata, si apprenderà come:  
  
-   Creare un nuovo **applicazione Windows Form**.  
  
-   Aggiungere un nuovo **controllo utente** al progetto.  
  
-   Progettare visivamente il controllo utente.  
  
-   Implementare l'attributo `LookupBindingProperty`.  
  
-   Creare un set di dati con il **configurazione guidata origine dati** procedura guidata.  
  
-   Impostare il **CustomerID** colonna il **ordini** tabella il **origini dati** finestra, utilizzare il nuovo controllo.  
  
-   Creare un form per visualizzare i dati nel controllo.  
  
## <a name="prerequisites"></a>Prerequisiti

Questa procedura dettagliata Usa SQL Server Express LocalDB e database di esempio Northwind.  

1.  Se non si dispone di SQL Server Express LocalDB, installarlo tramite il [pagina di download di SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), o tramite il **programma di installazione di Visual Studio**. Nel programma di installazione Visual Studio, SQL Server Express LocalDB può essere installato come parte di **l'elaborazione e archiviazione dei dati** carico di lavoro, o come un singolo componente.

2.  Installare il database di esempio Northwind attenendosi alla procedura seguente:  

    1. In Visual Studio, aprire il **Esplora oggetti di SQL Server** finestra. (Esplora oggetti di SQL Server viene installato come parte di **l'elaborazione e archiviazione dei dati** carico di lavoro in Visual Studio Installer.) Espandere il **SQL Server** nodo. Fare clic sull'istanza del database locale e selezionare **nuova Query...** .  

       Verrà visualizzata una finestra dell'editor di query.  

    2. Copia il [script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) negli Appunti. Questo script T-SQL crea il database Northwind da zero e la popola con dati.  

    3. Incollare lo script T-SQL nell'editor di query e quindi scegliere il **Execute** pulsante.  

       Dopo un breve periodo di tempo, la query viene completata l'esecuzione e viene creato il database Northwind.  
  
## <a name="create-a-windows-forms-application"></a>Creare un'applicazione Windows Form  
 Il primo passaggio consiste nel creare un **applicazione Windows Form**.  
  
#### <a name="to-create-the-new-windows-project"></a>Per creare il nuovo progetto Windows  
  
1. In Visual Studio, sul **File** dal menu **New**, **progetto...** .  
  
2. Espandere **Visual c#** o **Visual Basic** nel riquadro a sinistra, quindi selezionare **Windows Desktop classico**.  

3. Nel riquadro centrale, selezionare il **App di Windows Form** tipo di progetto.  

4. Denominare il progetto **LookupControlWalkthrough**, quindi scegliere **OK**. 
  
     Il **LookupControlWalkthrough** progetto viene creato e aggiunto a **Esplora**.  
  
## <a name="add-a-user-control-to-the-project"></a>Aggiungere un controllo utente al progetto  
 Questa procedura dettagliata crea un controllo di ricerca da un **controllo utente**, quindi aggiungere un **controllo utente** elemento il **LookupControlWalkthrough** progetto.  
  
#### <a name="to-add-a-user-control-to-the-project"></a>Per aggiungere un controllo utente al progetto  
  
1.  Dal **progetto** dal menu **Aggiungi controllo utente**.  
  
2.  Tipo `LookupBox` nel **nome** area e quindi fare clic su **Aggiungi**.  
  
     Il **LookupBox** controllo viene aggiunto al **Esplora**e nella finestra di progettazione.  
  
## <a name="design-the-lookupbox-control"></a>La progettazione del controllo LookupBox  
  
#### <a name="to-design-the-lookupbox-control"></a>Per progettare il controllo LookupBox  
  
-   Trascinare un <xref:System.Windows.Forms.ComboBox> dal **della casella degli strumenti** nell'area di progettazione del controllo utente.  
  
## <a name="add-the-required-data-binding-attribute"></a>Aggiungere l'attributo di data binding richiesto  
 Per controlli di ricerca che supportano il data binding, è possibile implementare l'attributo <xref:System.ComponentModel.LookupBindingPropertiesAttribute>.  
  
#### <a name="to-implement-the-lookupbindingproperties-attribute"></a>Per implementare l'attributo LookupBindingProperties  
  
1.  Opzione di **LookupBox** controllo alla visualizzazione codice. (Nel **vista** menu, scegliere **codice**.)  
  
2.  Sostituire il codice nel controllo `LookupBox` con la stringa seguente:  
  
     [!code-vb[VbRaddataDisplaying#5](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.vb)]
     [!code-csharp[VbRaddataDisplaying#5](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.cs)]  
  
3.  Scegliere **Compila soluzione** dal menu **Compila**.  
  
## <a name="create-a-data-source-from-your-database"></a>Creare un'origine dati dal database  
Questo passaggio viene creata un'origine dati usando il **configurazione guidata origine dati**procedura guidata, in base il `Customers` e `Orders` tabelle nel database di esempio Northwind.  
  
#### <a name="to-create-the-data-source"></a>Per creare l'origine dati  
  
1.  Scegliere **Mostra origini dati** dal menu **Dati**.  
  
2.  Nel **origini dati** selezionare **Aggiungi nuova origine dati** per avviare il **configurazione guidata origine dati** procedura guidata.  
  
3.  Selezionare **Database** nella pagina **Scegliere un tipo di origine dati** e scegliere **Avanti**.  
  
4.  Nel **Seleziona connessione dati** eseguire pagina una delle operazioni seguenti:  
  
    -   Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.  
  
    -   Selezionare **nuova connessione** per avviare il **Aggiungi/Modifica connessione** la finestra di dialogo.  
  
5.  Se il database richiede una password, selezionare l'opzione per includere dati riservati e quindi fare clic su **Avanti**.  
  
6.  Nel **Salva stringa di connessione nel file di configurazione dell'applicazione** pagina, fare clic su **Avanti**.  
  
7.  Nel **Seleziona oggetti di Database** espandere la **tabelle** nodo.  
  
8.  Selezionare il `Customers` e `Orders` tabelle e quindi fare clic su **fine**.  
  
     Il **NorthwindDataSet** viene aggiunto al progetto e `Customers` e `Orders` tabelle vengono visualizzate nella **origini dati** finestra.  
  
## <a name="set-the-customerid-column-of-the-orders-table-to-use-the-lookupbox-control"></a>Impostare la colonna CustomerID della tabella Orders per usare il controllo LookupBox  
 All'interno di **origini dati** finestra, è possibile impostare il controllo da creare prima il trascinamento degli elementi nel form.  
  
#### <a name="to-set-the-customerid-column-to-bind-to-the-lookupbox-control"></a>Per impostare la colonna CustomerID da associare al controllo LookupBox  
  
1.  Aprire **Form1** nella finestra di progettazione.  
  
2.  Espandere il **clienti** nodo il **origini dati** finestra.  
  
3.  Espandere il **ordini** nodo (quello il **clienti** nodo sotto il **Fax** colonna).  
  
4.  Fare clic sulla freccia a discesa di **ordini** nodo e scegliere **dettagli** dall'elenco di controllo.  
  
5.  Fare clic sulla freccia a discesa di **CustomerID** colonna (nel **ordini** nodo) e scegliere **Personalizza**.  
  
6.  Selezionare il **LookupBox** dall'elenco di **controlli associati** nel **le opzioni di personalizzazione dell'interfaccia utente dati** la finestra di dialogo.  
  
7.  Fare clic su **OK**.  
  
8.  Fare clic sulla freccia a discesa di **CustomerID** colonna e scegliere **LookupBox**.  
  
## <a name="add-controls-to-the-form"></a>Aggiungere controlli al form  
 È possibile creare i controlli con associazione a dati trascinando elementi dal **origini dati** finestra **Form1**.  
  
#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Per creare controlli associati ai dati nel Windows Form  
  
-   Trascinare il **ordini** nodo dal **origini dati** finestra Windows Form e verificare che il **LookupBox** controllo viene utilizzato per visualizzare i dati nel `CustomerID` colonna.  
  
## <a name="bind-the-control-to-look-up-companyname-from-the-customers-table"></a>Associare il controllo per cercare CompanyName dalla tabella Customers  
  
#### <a name="to-setup-the-lookup-bindings"></a>Per impostare le associazioni di ricerca  
  
-   Selezionare principale **clienti** nodo il **origini dati** finestra e trascinare casella combinata di **CustomerIDLookupBox** su **Form1** .  
  
     Viene impostata l'associazione dati per visualizzare il `CompanyName` dal `Customers` tabella, mantenendo al contempo il `CustomerID` valore il `Orders` tabella.  
  
## <a name="running-the-application"></a>Esecuzione dell'applicazione  
  
#### <a name="to-run-the-application"></a>Per eseguire l'applicazione  
  
-   Premere F5 per eseguire l'applicazione.  
  
-   Spostarsi tra alcuni record e verificare che il `CompanyName` presenti il `LookupBox` controllo.  
  
## <a name="see-also"></a>Vedere anche  
 [Associare controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
