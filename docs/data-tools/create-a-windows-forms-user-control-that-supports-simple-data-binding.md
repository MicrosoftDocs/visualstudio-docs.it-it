---
title: Creare un controllo utente che supporta il data binding semplice
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom controls [Visual Studio], Data Sources Window
- Data Sources Window, controls
ms.assetid: b1488366-6dfb-454e-9751-f42fd3f3ddfb
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 1088a20181d9af5072d5335c63f3cb3ace47f4db
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="create-a-windows-forms-user-control-that-supports-simple-data-binding"></a>Creare un controllo utente Windows Form che supporta l'associazione dati semplice
Quando si visualizzano dati su form in applicazioni di Windows, è possibile scegliere i controlli esistenti dal **della casella degli strumenti**, oppure è possibile creare controlli personalizzati se l'applicazione richiede funzionalità che non sono disponibili nei controlli standard. In questa procedura dettagliata è illustrato come creare un controllo che implementa <xref:System.ComponentModel.DefaultBindingPropertyAttribute>. I controlli che implementano <xref:System.ComponentModel.DefaultBindingPropertyAttribute> possono contenere una proprietà associabile ai dati. Tali controlli sono simili a <xref:System.Windows.Forms.TextBox> o <xref:System.Windows.Forms.CheckBox>.

 Per ulteriori informazioni sulla creazione di controlli, vedere [lo sviluppo di controlli Windows Form in fase di progettazione](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

 Quando si creano controlli da usare in scenari di associazione dati, è necessario implementare uno degli attributi di associazione di dati seguenti:

|Utilizzo dell'attributo di associazione dati|
|-----------------------------------|
|Implementare <xref:System.ComponentModel.DefaultBindingPropertyAttribute> su controlli semplici, ad esempio <xref:System.Windows.Forms.TextBox>, che visualizzano una singola colonna, o proprietà, di dati. Il processo è descritto in questa pagina di procedura dettagliata.|
|Implementare <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> su controlli, ad esempio <xref:System.Windows.Forms.DataGridView>, che visualizzano elenchi, o tabelle, di dati. Per ulteriori informazioni, vedere [creare un controllo utente Windows Form che supporta l'associazione dati complessa](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|
|Implementare <xref:System.ComponentModel.LookupBindingPropertiesAttribute> su controlli, ad esempio <xref:System.Windows.Forms.ComboBox>, che visualizzano elenchi, o tabelle, di dati ma che devono anche presentare una singola colonna o proprietà. Per ulteriori informazioni, vedere [creare un controllo utente Windows Form che supporta l'associazione di dati di ricerca](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|

 Questa procedura dettagliata crea un controllo semplice che visualizza i dati di una singola colonna in una tabella. Questo esempio usa la colonna `Phone` della tabella `Customers` del database di esempio Northwind. Il controllo utente semplice visualizzerà i numeri di telefono dei clienti in un formato di numero di telefono standard, tramite un <xref:System.Windows.Forms.MaskedTextBox> e impostando la maschera su un numero di telefono.

 Durante questa procedura dettagliata, si apprenderà come:

-   Creare un nuovo **applicazione Windows Form**.

-   Aggiungere un nuovo **controllo utente** al progetto.

-   Progettare visivamente il controllo utente.

-   Implementare l'attributo `DefaultBindingProperty`.

-   Creare un set di dati con il **configurazione guidata origine dati** procedura guidata.

-   Impostare il **Phone** colonna il **origini dati** finestra per l'utilizzo del nuovo controllo.

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

4. Denominare il progetto **SimpleControlWalkthrough**, quindi scegliere **OK**.

     Il **SimpleControlWalkthrough** progetto viene creato e aggiunto a **Esplora**.

## <a name="add-a-user-control-to-the-project"></a>Aggiungere un controllo utente al progetto
 Questa procedura dettagliata crea un controllo di data binding semplice da un **controllo utente**, quindi aggiungere un **controllo utente** elemento il **SimpleControlWalkthrough** progetto.

#### <a name="to-add-a-user-control-to-the-project"></a>Per aggiungere un controllo utente al progetto

1.  Dal **progetto** menu, scegliere **Aggiungi controllo utente**.

2.  Tipo `PhoneNumberBox` nell'area nome, quindi fare clic su **Aggiungi**.

     Il **PhoneNumberBox** controllo viene aggiunto al **Esplora**e nella finestra di progettazione.

## <a name="design-the-phonenumberbox-control"></a>La progettazione del controllo PhoneNumberBox
 Questa procedura dettagliata estende l'oggetto <xref:System.Windows.Forms.MaskedTextBox> per creare il controllo `PhoneNumberBox`.

#### <a name="to-design-the-phonenumberbox-control"></a>Per progettare il controllo PhoneNumberBox

1.  Trascinare un <xref:System.Windows.Forms.MaskedTextBox> dal **della casella degli strumenti** nell'area di progettazione del controllo utente.

2.  Selezionare lo smart tag nel <xref:System.Windows.Forms.MaskedTextBox> appena trascinato e scegliere **Imposta maschera**.

3.  Selezionare **il numero di telefono** nel **maschera di Input** la finestra di dialogo e fare clic su **OK** per impostare la maschera.

## <a name="add-the-required-data-binding-attribute"></a>Aggiungere l'attributo di data binding richiesto
 Per controlli semplici che supportano il data binding, implementare l'attributo <xref:System.ComponentModel.DefaultBindingPropertyAttribute>.

#### <a name="to-implement-the-defaultbindingproperty-attribute"></a>Per implementare l'attributo DefaultBindingProperty

1.  Passare al controllo `PhoneNumberBox` per la visualizzazione del codice. (Nel **vista** menu, scegliere **codice**.)

2.  Sostituire il codice nel controllo `PhoneNumberBox` con la stringa seguente:

     [!code-csharp[VbRaddataDisplaying#3](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.cs)]
     [!code-vb[VbRaddataDisplaying#3](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.vb)]

3.  Scegliere **Compila soluzione** dal menu **Compila**.

## <a name="create-a-data-source-from-your-database"></a>Creare un'origine dati dal database
 Questo passaggio viene utilizzata la **configurazione guidata origine dati**procedura guidata per creare un'origine dati in base il `Customers` tabella nel database di esempio Northwind. Per creare la connessione, è necessario avere accesso al database di esempio Northwind. Per informazioni sull'impostazione di database di esempio Northwind, vedere [procedura: installare database di esempio](../data-tools/installing-database-systems-tools-and-samples.md).

#### <a name="to-create-the-data-source"></a>Per creare l'origine dati

1.  Scegliere **Mostra origini dati** dal menu **Dati**.

2.  Nel **origini dati** selezionare **Aggiungi nuova origine dati** per avviare il **configurazione guidata origine dati** procedura guidata.

3.  Nel **scegliere un tipo di origine dati** selezionare **Database**e quindi fare clic su **Avanti**.

4.  Nel **Seleziona connessione dati** pagina, effettuare una delle operazioni seguenti:

    -   Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.

    -   Selezionare **nuova connessione** per avviare il **Aggiungi/Modifica connessione** la finestra di dialogo.

5.  Se il database richiede una password, selezionare l'opzione per includere dati riservati e quindi fare clic su **Avanti**.

6.  Nel **Salva stringa di connessione nel file di configurazione dell'applicazione** pagina, fare clic su **Avanti**.

7.  Nel **Seleziona oggetti di Database** espandere la **tabelle** nodo.

8.  Selezionare il `Customers` tabella e quindi fare clic su **fine**.

     Il **NorthwindDataSet** viene aggiunto al progetto e `Customers` tabella viene visualizzata nel **origini dati** finestra.

## <a name="set-the-phone-column-to-use-the-phonenumberbox-control"></a>Impostare la colonna telefono per usare il controllo PhoneNumberBox
 All'interno di **origini dati** finestra, è possibile impostare il controllo da creare prima il trascinamento degli elementi nel form.

#### <a name="to-set-the-phone-column-to-bind-to-the-phonenumberbox-control"></a>Per impostare la colonna Telefono allo scopo di eseguire l'associazione al controllo PhoneNumberBox

1.  Aprire **Form1** nella finestra di progettazione.

2.  Espandere il **clienti** nodo il **origini dati** finestra.

3.  Fare clic sulla freccia a discesa di **clienti** nodo e scegliere **dettagli** dall'elenco di controllo.

4.  Fare clic sulla freccia a discesa di **Phone** colonna e scegliere **Personalizza**.

5.  Selezionare il **PhoneNumberBox** dall'elenco di **controlli associati** nel **le opzioni di personalizzazione dell'interfaccia utente dati** la finestra di dialogo.

6.  Fare clic sulla freccia a discesa di **Phone** colonna e scegliere **PhoneNumberBox**.

## <a name="add-controls-to-the-form"></a>Aggiungere controlli al form
 È possibile creare i controlli con associazione a dati trascinando elementi dal **origini dati** finestra al form.

#### <a name="to-create-data-bound-controls-on-the-form"></a>Per creare controlli associati a dati nel form

-   Trascinare principale **clienti** nodo dal **origini dati** finestra nei form e verificare che il `PhoneNumberBox` controllo viene utilizzato per visualizzare i dati nel `Phone` colonna.

     Il form mostra i controlli associati a dati con etichette descrittive e un controllo Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) per lo spostamento all'interno dei record. Oggetto [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter <xref:System.Windows.Forms.BindingSource>, e <xref:System.Windows.Forms.BindingNavigator> vengono visualizzati nella barra dei componenti.

## <a name="run-the-application"></a>Esecuzione dell'applicazione

#### <a name="to-run-the-application"></a>Per eseguire l'applicazione

-   Premere F5 per eseguire l'applicazione.

## <a name="next-steps"></a>Passaggi successivi
 A seconda dei requisiti dell'applicazione, dopo la creazione di un controllo che supporta il data binding sarà possibile eseguire diverse operazioni. Ecco alcuni dei passaggi più comuni:

-   Posizionamento dei controlli personalizzati in una libreria di controlli in modo da poterli usare di nuovo in altre applicazioni.

-   Creazione di controlli che supportano scenari di associazioni di dati più complessi. Per ulteriori informazioni, vedere [creare un controllo utente Windows Form che supporta l'associazione dati complessa](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md) e [creare un controllo utente Windows Form che supporta l'associazione di dati di ricerca](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).

## <a name="see-also"></a>Vedere anche

- [Associare controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)