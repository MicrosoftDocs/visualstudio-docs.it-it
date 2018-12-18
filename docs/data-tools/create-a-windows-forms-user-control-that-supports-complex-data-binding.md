---
title: Creare un controllo utente Windows Form con associazione dati | Documenti Microsoft
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
- data binding, complex
- user controls [Visual Studio], complex data binding
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: dc3ebe35c7b9697921e50a9ea310723128b494be
ms.sourcegitcommit: 49aa031cbebdd9c7ec070c713afb1a97d1ecb701
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2018
---
# <a name="create-a-windows-forms-user-control-that-supports-complex-data-binding"></a>Creare un controllo utente Windows Form che supporta l'associazione dati complessa

Quando si visualizzano dati su form in applicazioni di Windows, è possibile scegliere i controlli esistenti dal **della casella degli strumenti**, oppure è possibile creare controlli personalizzati se l'applicazione richiede funzionalità che non sono disponibili nei controlli standard. In questa procedura dettagliata è illustrato come creare un controllo che implementa <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>. I controlli che implementano <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> contengono `DataSource` e la proprietà `DataMember` che può essere associata ai dati. Tali controlli sono simili a <xref:System.Windows.Forms.DataGridView> o <xref:System.Windows.Forms.ListBox>.

Per ulteriori informazioni sulla creazione di controlli, vedere [lo sviluppo di controlli Windows Form in fase di progettazione](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

Quando si creano controlli da usare in scenari di associazione di dati è necessario implementare uno degli attributi di associazione di dati seguenti:

|Utilizzo dell'attributo di associazione dati|
|-----------------------------------|
|Implementare <xref:System.ComponentModel.DefaultBindingPropertyAttribute> su controlli semplici, ad esempio <xref:System.Windows.Forms.TextBox>, che visualizzano una singola colonna, o proprietà, di dati. Per ulteriori informazioni, vedere [creare un controllo utente Windows Form che supporta l'associazione dati semplice](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|
|Implementare <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> su controlli, ad esempio <xref:System.Windows.Forms.DataGridView>, che visualizzano elenchi, o tabelle, di dati. Il processo è descritto in questa pagina di procedura dettagliata.|
|Implementare <xref:System.ComponentModel.LookupBindingPropertiesAttribute> su controlli, ad esempio <xref:System.Windows.Forms.ComboBox>, che visualizzano elenchi, o tabelle, di dati ma che devono anche presentare una singola colonna o proprietà. Per ulteriori informazioni, vedere [creare un controllo utente Windows Form che supporta l'associazione di dati di ricerca](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|

 Questa procedura dettagliata crea un controllo complesso che visualizza righe di dati da una tabella. In questo esempio viene usata la tabella `Customers` del database di esempio Northwind. Il controllo utente complesso visualizzerà la tabella dei clienti in un oggetto <xref:System.Windows.Forms.DataGridView> nel controllo personalizzato.

Durante questa procedura dettagliata, si apprenderà come:

- Creare un nuovo **applicazione Windows Form**.

- Aggiungere un nuovo **controllo utente** al progetto.

- Progettare visivamente il controllo utente.

- Implementare l'attributo `ComplexBindingProperty`.

- Creare un set di dati con il [configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png).

- Impostare il **clienti** tabella il [finestra Origini dati](add-new-data-sources.md) per usare il nuovo controllo complesso.

- Aggiungere il nuovo controllo trascinandolo dal **finestra Origini dati** su **Form1**.

## <a name="prerequisites"></a>Prerequisiti

Questa procedura dettagliata Usa SQL Server Express LocalDB e database di esempio Northwind.

1. Se non si dispone di SQL Server Express LocalDB, installarlo tramite il [pagina di download di SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), o tramite il **programma di installazione di Visual Studio**. Nel programma di installazione Visual Studio, SQL Server Express LocalDB può essere installato come parte di **l'elaborazione e archiviazione dei dati** carico di lavoro, o come un singolo componente.

1. Installare il database di esempio Northwind attenendosi alla procedura seguente:

    1. In Visual Studio, aprire il **Esplora oggetti di SQL Server** finestra. (Esplora oggetti di SQL Server viene installato come parte di **l'elaborazione e archiviazione dei dati** carico di lavoro in Visual Studio Installer.) Espandere il **SQL Server** nodo. Fare clic sull'istanza del database locale e selezionare **nuova Query...** .

       Verrà visualizzata una finestra dell'editor di query.

    1. Copia il [script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) negli Appunti. Questo script T-SQL crea il database Northwind da zero e la popola con dati.

    1. Incollare lo script T-SQL nell'editor di query e quindi scegliere il **Execute** pulsante.

       Dopo un breve periodo di tempo, la query viene completata l'esecuzione e viene creato il database Northwind.

## <a name="create-a-windows-forms-application"></a>Creare un'applicazione Windows Form

 Il primo passaggio consiste nel creare un **applicazione Windows Form**.

### <a name="to-create-the-new-windows-project"></a>Per creare il nuovo progetto Windows

1. In Visual Studio, sul **File** dal menu **New**, **progetto...** .

1. Espandere **Visual c#** o **Visual Basic** nel riquadro a sinistra, quindi selezionare **Windows Desktop classico**.

1. Nel riquadro centrale, selezionare il **App di Windows Form** tipo di progetto.

1. Denominare il progetto **ComplexControlWalkthrough**, quindi scegliere **OK**.

    Il **ComplexControlWalkthrough** progetto viene creato e aggiunto a **Esplora**.

## <a name="add-a-user-control-to-the-project"></a>Aggiungere un controllo utente al progetto

Poiché questa procedura dettagliata crea un controllo complesso associabili ai dati da un **controllo utente**, è necessario aggiungere un **controllo utente** elemento al progetto.

### <a name="to-add-a-user-control-to-the-project"></a>Per aggiungere un controllo utente al progetto

1. Dal **progetto** menu, scegliere **Aggiungi controllo utente**.

1. Tipo **ComplexDataGridView** nel **nome** area e quindi fare clic su **Aggiungi**.

    Il **ComplexDataGridView** controllo viene aggiunto al **Esplora**e nella finestra di progettazione.

## <a name="design-the-complexdatagridview-control"></a>La progettazione del controllo ComplexDataGridView

Questo passaggio aggiunge un oggetto <xref:System.Windows.Forms.DataGridView> al controllo utente.

### <a name="to-design-the-complexdatagridview-control"></a>Per progettare il controllo ComplexDataGridView

- Trascinare un <xref:System.Windows.Forms.DataGridView> dal **della casella degli strumenti** nell'area di progettazione del controllo utente.

## <a name="add-the-required-data-binding-attribute"></a>Aggiungere l'attributo di data binding richiesto

Per controlli semplici che supportano il data binding, è possibile implementare l'attributo <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>.
  
### <a name="to-implement-the-complexbindingproperties-attribute"></a>Per implementare l'attributo ComplexBindingProperties

1. Opzione di **ComplexDataGridView** controllo alla visualizzazione codice. (Nel **vista** dal menu **codice**.)

1. Sostituire il codice nel controllo `ComplexDataGridView` con la stringa seguente:

    [!code-csharp[VbRaddataDisplaying#4](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.cs)]
    [!code-vb[VbRaddataDisplaying#4](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.vb)]

1. Scegliere **Compila soluzione** dal menu **Compila**.

## <a name="creating-a-data-source-from-your-database"></a>Creazione di un'origine dati dal database

Questo passaggio viene utilizzata la **configurazione guidata origine dati** procedura guidata per creare un'origine dati in base il `Customers` tabella nel database di esempio Northwind.

### <a name="to-create-the-data-source"></a>Per creare l'origine dati

1.  Scegliere **Mostra origini dati** dal menu **Dati**.

2.  Nel **origini dati** selezionare **Aggiungi nuova origine dati** per avviare il **configurazione guidata origine dati** procedura guidata.

3.  Selezionare **Database** nella pagina **Scegliere un tipo di origine dati** e scegliere **Avanti**.

4.  Nel **Seleziona connessione dati** eseguire pagina una delle operazioni seguenti:

    - Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.

    - Selezionare **nuova connessione** per avviare il **Aggiungi/Modifica connessione** la finestra di dialogo.

5.  Se il database richiede una password, selezionare l'opzione per includere dati riservati e quindi fare clic su **Avanti**.

6.  Nel **Salva stringa di connessione nel file di configurazione dell'applicazione** pagina, fare clic su **Avanti**.

7.  Nel **Seleziona oggetti di Database** espandere la **tabelle** nodo.

8.  Selezionare il `Customers` tabella e quindi fare clic su **fine**.

    Il **NorthwindDataSet** viene aggiunto al progetto e `Customers` tabella viene visualizzata nel **origini dati** finestra.

## <a name="set-the-customers-table-to-use-the-complexdatagridview-control"></a>Impostare la tabella Customers per usare il controllo ComplexDataGridView

All'interno di **origini dati** finestra, è possibile impostare il controllo da creare prima il trascinamento degli elementi nel form.

### <a name="to-set-the-customers-table-to-bind-to-the-complexdatagridview-control"></a>Per impostare la tabella Customers allo scopo di associare il controllo ComplexDataGridView

1. Aprire **Form1** nella finestra di progettazione.

1. Espandere il **clienti** nodo il **origini dati** finestra.

1. Fare clic sulla freccia a discesa di **clienti** nodo e scegliere **Personalizza**.

1. Selezionare il **ComplexDataGridView** dall'elenco di **controlli associati** nel **le opzioni di personalizzazione dell'interfaccia utente dati** la finestra di dialogo.

1. Fare clic sulla freccia a discesa di `Customers` tabella e scegliere **ComplexDataGridView** dall'elenco di controllo.

## <a name="add-controls-to-the-form"></a>Aggiungere controlli al form

È possibile creare i controlli con associazione a dati trascinando elementi dal **origini dati** finestra nel form.

### <a name="to-create-data-bound-controls-on-the-form"></a>Per creare controlli associati a dati nel form

Trascinare principale **clienti** nodo dal **origini dati** finestra al form. Verificare che il **ComplexDataGridView** controllo viene utilizzato per visualizzare i dati della tabella.  

## <a name="running-the-application"></a>Esecuzione dell'applicazione

### <a name="to-run-the-application"></a>Per eseguire l'applicazione

Premere F5 per eseguire l'applicazione.

## <a name="next-steps"></a>Passaggi successivi

A seconda dei requisiti dell'applicazione, dopo la creazione di un controllo che supporta il data binding sarà possibile eseguire diverse operazioni. Ecco alcuni dei passaggi più comuni:

- Posizionamento dei controlli personalizzati in una libreria di controlli in modo da poterli usare di nuovo in altre applicazioni.

- Creazione di controlli che supportano scenari di ricerca. Per ulteriori informazioni, vedere [creare un controllo utente Windows Form che supporta l'associazione di dati di ricerca](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).

## <a name="see-also"></a>Vedere anche

[Associare controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)  
[Impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)  
[Controlli Windows Form](/dotnet/framework/winforms/controls/index)
