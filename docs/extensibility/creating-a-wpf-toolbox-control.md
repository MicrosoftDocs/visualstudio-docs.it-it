---
title: Creazione di un controllo della casella degli strumenti WPF | Microsoft Docs
description: Informazioni su come usare il modello di controllo della casella degli strumenti WPF per creare un controllo della casella degli strumenti che è possibile distribuire ad altri utenti.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- toolbox control
- toolbox
- wpf
ms.assetid: 9cc34db9-b0d1-4951-a02f-7537fbbb51ad
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1dccdeb09a938b3b0bbbab803faeed538001b825
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089251"
---
# <a name="create-a-wpf-toolbox-control"></a>Creare un controllo della casella degli strumenti WPF

Il modello di controllo della casella degli strumenti WPF (Windows Presentation Framework) consente di creare controlli WPF che vengono aggiunti automaticamente alla **casella degli strumenti** quando l'estensione viene installata. In questa procedura dettagliata viene illustrato come utilizzare il modello per creare un controllo della **casella degli strumenti** che è possibile distribuire ad altri utenti.

A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. Viene inclusa come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare Visual Studio SDK in un secondo momento. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-the-toolbox-control"></a>Creare il controllo della casella degli strumenti

### <a name="create-an-extension-with-a-wpf-toolbox-control"></a>Creare un'estensione con un controllo della casella degli strumenti WPF

1. Creare un progetto VSIX denominato `MyToolboxControl` . È possibile trovare il modello di progetto VSIX nella finestra di dialogo **nuovo progetto** cercando "VSIX".

2. Quando si apre il progetto, aggiungere un modello di elemento di **controllo della casella degli strumenti WPF** denominato `MyToolboxControl` . Nella **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Aggiungi**  >  **nuovo elemento**. Nella finestra di dialogo **Aggiungi nuovo elemento** passare a estensibilità di **Visual C#**  >   e selezionare **controllo della casella degli strumenti WPF**. Nel campo **nome** nella parte inferiore della finestra modificare il nome del file di comando in *MyToolboxControl. cs*.

    La soluzione ora contiene un controllo utente, un `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> che aggiunge il controllo alla **casella degli strumenti** e una voce di asset **Microsoft. VisualStudio. ToolboxControl** nel manifesto VSIX per la distribuzione.

#### <a name="to-create-the-control-ui"></a>Creare l'interfaccia utente del controllo

1. Aprire *MyToolboxControl. XAML* nella finestra di progettazione.

    La finestra di progettazione mostra un controllo <xref:System.Windows.Controls.Grid> che contiene un controllo <xref:System.Windows.Controls.Button>.

2. Disporre il layout della griglia. Quando si seleziona il <xref:System.Windows.Controls.Grid> controllo, le barre di controllo blu vengono visualizzate sui bordi superiore e sinistro della griglia. È possibile aggiungere righe e colonne alla griglia facendo clic sulle barre.

3. Aggiungere i controlli figlio alla griglia. È possibile posizionare un controllo figlio trascinandolo dalla **casella degli strumenti** in una sezione della griglia oppure impostando i relativi `Grid.Row` `Grid.Column` attributi e in XAML. Nell'esempio seguente vengono aggiunte due etichette nella riga superiore della griglia e un pulsante nella seconda riga.

    ```xaml
    <Grid>
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />
    </Grid>
    ```

## <a name="renaming-the-control"></a>Ridenominazione del controllo

 Per impostazione predefinita, il controllo verrà visualizzato nella **casella degli strumenti** come **MyToolboxControl** in un gruppo denominato **MyToolboxControl. MyToolboxControl**. È possibile modificare questi nomi nel file *MyToolboxControl. XAML. cs* .

1. Aprire *MyToolboxControl. XAML. cs* nella visualizzazione codice.

2. Trovare la `MyToolboxControl` classe e rinominarla in TestControl. Il modo più rapido per eseguire questa operazione consiste nel rinominare la classe, quindi selezionare **Rinomina** dal menu di scelta rapida e completare i passaggi. Per ulteriori informazioni sul comando **Rinomina** , vedere [refactoring di ridenominazione (C#)](../ide/reference/rename.md).

3. Passare all' `ProvideToolboxControl` attributo e modificare il valore del primo parametro in **test**. Si tratta del nome del gruppo che conterrà il controllo nella **casella degli strumenti**.

    Il codice risultante dovrebbe essere simile al seguente:

    ```csharp
    [ProvideToolboxControl("Test", true)]
    public partial class TestControl : UserControl
    {
        public TestControl()
        {
            InitializeComponent();
        }
    }
    ```

## <a name="build-test-and-deployment"></a>Compilazione, test e distribuzione

 Quando si esegue il debug del progetto, è necessario trovare il controllo installato nella **casella degli strumenti** dell'istanza sperimentale di Visual Studio.

### <a name="to-build-and-test-the-control"></a>Per compilare e testare il controllo

1. Ricompilare il progetto e avviare il debug.

2. Nella nuova istanza di Visual Studio creare un progetto di applicazione WPF. Verificare che il finestra di progettazione XAML sia aperto.

3. Individuare il controllo nella **casella degli strumenti** e trascinarlo nell'area di progettazione.

4. Avviare il debug dell'applicazione WPF.

5. Verificare che il controllo sia visualizzato.

### <a name="to-deploy-the-control"></a>Per distribuire il controllo

1. Dopo aver compilato il progetto testato, è possibile trovare il file con *estensione VSIX* nella cartella * \Bin\Debug \* del progetto.

2. È possibile installarlo in un computer locale facendo doppio clic sul file con *estensione VSIX* e seguendo la procedura di installazione. Per disinstallare il controllo, passare a **strumenti**  >  **estensioni e aggiornamenti** e cercare l'estensione del controllo, quindi fare clic su **Disinstalla**.

3. Caricare il file *VSIX* in una rete o in un sito Web.

    Se si carica il file nel sito Web di [Visual Studio Marketplace](https://marketplace.visualstudio.com/) , altri utenti possono usare gli **strumenti**  >  **estensioni e aggiornamenti** in Visual Studio per trovare il controllo online e installarlo.
