---
title: 'Procedura dettagliata: Scrittura di un visualizzatore in c# | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- visualizers, writing
- walkthroughs [Visual Studio], visualizers
ms.assetid: 53467461-8e0f-45ee-9bc4-374bbaeaf00f
caps.latest.revision: "33"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 6e161b3c914d0a87a720f1217b52a571b85f5ff9
ms.sourcegitcommit: 03a74d29a1e0584ff4808ce6c9e812b51e774905
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2018
---
# <a name="walkthrough-writing-a-visualizer-in-c"></a>Procedura dettagliata: scrittura di un visualizzatore in C# #
Questa procedura dettagliata viene illustrato come scrivere un visualizzatore semplice usando c#. Il visualizzatore che si creerà in questa procedura dettagliata consente di visualizzare il contenuto di una stringa utilizzando una finestra di messaggio Windows Form. Questo visualizzatore semplice di stringhe non è particolarmente utile in sé, ma mostra i passaggi di base che è necessario seguire per creare più utili visualizzatori per altri tipi di dati.  
  
> [!NOTE]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero non corrispondere a quelli descritti nella Guida in quanto dipendono dall'edizione o dalle impostazioni in uso. Per modificare le impostazioni, utilizzare il **strumenti** menu e scegliere **Importa / Esporta impostazioni**. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
 Il codice del visualizzatore deve trovarsi in una DLL, che verrà letti dal debugger. Di conseguenza, il primo passaggio consiste nel creare un progetto libreria di classi per la DLL.  

## <a name="create-a-visualizer-manually"></a>Creare manualmente un visualizzatore

Eseguire le attività seguenti per creare un visualizzatore.
  
#### <a name="to-create-a-class-library-project"></a>Per creare un progetto Libreria di classi  
  
1.  Nel **File** menu, scegliere **nuovo > progetto**.  
  
2.  Nel **nuovo progetto** nella finestra di dialogo **Visual c#**selezionare **.NET Standard**.  
  
3.  Nel riquadro centrale, scegliere **libreria di classi**.  
  
4.  Nel **nome** , digitare un nome appropriato per la libreria di classi, ad esempio MyFirstVisualizer.  
  
5.  Fare clic su **OK**.  
  
 Dopo aver creato la libreria di classi, è necessario aggiungere un riferimento a Microsoft.VisualStudio.DebuggerVisualizers.DLL in modo da poter utilizzare le classi definite in. Prima di aggiungere il riferimento, tuttavia, è necessario rinominare alcune classi in modo che abbiano nomi significativi.  
  
#### <a name="to-rename-class1cs-and-add-microsoftvisualstudiodebuggervisualizers"></a>Per rinominare Class1. cs e aggiungere DebuggerVisualizers  
  
1.  In **Esplora**, fare doppio clic su Class1. cs e scegliere **rinominare** nel menu di scelta rapida.  
  
2.  Modificare il nome Class1. cs in un nome significativo, ad esempio DebuggerSide.cs.  
  
    > [!NOTE]
    >  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]la dichiarazione di classe in base al nome del nuovo file DebuggerSide.cs modificata automaticamente.  
  
3.  In **Esplora**, fare doppio clic su **riferimenti** e scegliere **Aggiungi riferimento** nel menu di scelta rapida.  
  
4.  Nel **Aggiungi riferimento** della finestra di dialogo di **.NET** scegliere Microsoft.VisualStudio.DebuggerVisualizers.DLL.  
  
5.  Fare clic su **OK**.  
  
6.  In DebuggerSide.cs aggiungere l'istruzione seguente alle istruzioni `using`:  
  
    ```csharp  
    using Microsoft.VisualStudio.DebuggerVisualizers;  
    ```  
  
 A questo punto si è pronti per creare il codice del lato debugger. Questo codice verrà eseguito all'interno del debugger per visualizzare le informazioni desiderate. Innanzitutto, è necessario modificare la dichiarazione del `DebuggerSide` in modo che eredita dalla classe di base dell'oggetto `DialogDebuggerVisualizer`.  
  
#### <a name="to-inherit-from-dialogdebuggervisualizer"></a>Per ereditare da DialogDebuggerVisualizer  
  
1.  In DebuggerSide.cs, passare alla riga di codice seguente:  
  
    ```csharp  
    public class DebuggerSide  
    ```  
  
2.  Modificare il codice per:  
  
    ```csharp  
    public class DebuggerSide : DialogDebuggerVisualizer  
    ```  
  
 `DialogDebuggerVisualizer`è un metodo astratto (`Show`) che è necessario eseguire l'override.  
  
#### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>Per eseguire l'override del metodo DialogDebuggerVisualizer.Show  
  
-   In `public class DebuggerSide`, aggiungere il seguente **metodo:**  
  
    ```csharp  
    protected override void Show(IDialogVisualizerService windowService, IVisualizerObjectProvider objectProvider)  
    {  
    }  
    ```  
  
 Il `Show` metodo contiene il codice per la creazione della finestra di dialogo o un'altra interfaccia utente e visualizza le informazioni che sono state passate al visualizzatore dal debugger. Questo codice deve essere aggiunto dallo sviluppatore. In questa procedura dettagliata, si eseguirà questo utilizzando una finestra di messaggio Windows Form. In primo luogo, è necessario aggiungere un riferimento e `using` istruzione per Forms.  
  
#### <a name="to-add-systemwindowsforms"></a>Per aggiungere System.Windows.Forms  
  
1.  In **Esplora**, fare doppio clic su **riferimenti** e scegliere **Aggiungi riferimento** nel menu di scelta rapida.  
  
2.  Nel **Aggiungi riferimento** della finestra di dialogo di **.NET** scheda, scegliere System.  
  
3.  Fare clic su **OK**.  
  
4.  In DebuggerSide.cs aggiungere l'istruzione seguente alle istruzioni `using`:  
  
    ```csharp  
    using System.Windows.Forms;  
    ```  
  
 A questo punto, si aggiungerà codice per creare e visualizzare l'interfaccia utente del visualizzatore. Poiché si tratta del primo visualizzatore creato, si manterrà l'interfaccia utente semplice e utilizzare una finestra di messaggio.  
  
#### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>Per visualizzare l'Output del visualizzatore in una finestra di dialogo  
  
1.  Nel metodo `Show` aggiungere la riga di codice seguente:  
  
    ```csharp  
    MessageBox.Show(objectProvider.GetObject().ToString());  
    ```  
  
     Questo codice di esempio non include la gestione degli errori. È necessario includere in un vero visualizzatore o qualsiasi altro tipo di applicazione di gestione degli errori.  
  
2.  Nel **compilare** menu, scegliere **Compila MyFirstVisualizer**. La compilazione del progetto dovrebbe avvenire senza problemi. Correggere gli eventuali errori di compilazione prima di continuare.  
  
 Che corrisponde alla fine del codice sul lato debugger. È un altro passaggio, tuttavia; l'attributo che indica il lato oggetto del debug la raccolta di classi che comprende il visualizzatore.  
  
#### <a name="to-add-the-debuggee-side-code"></a>Per aggiungere il codice del lato oggetto del debug  
  
1.  Aggiungere il seguente codice di attributo a DebuggerSide.cs, dopo il `using` istruzioni ma prima che `namespace MyFirstVisualizer`:  
  
    ```csharp  
    [assembly:System.Diagnostics.DebuggerVisualizer(  
    typeof(MyFirstVisualizer.DebuggerSide),  
    typeof(VisualizerObjectSource),  
    Target = typeof(System.String),  
    Description = "My First Visualizer")]  
    ```  
  
2.  Nel **compilare** menu, scegliere **Compila MyFirstVisualizer**. La compilazione del progetto dovrebbe avvenire senza problemi. Correggere gli eventuali errori di compilazione prima di continuare.  
  
 A questo punto il visualizzatore è pronto. Se la procedura è stata completata in modo corretto, è possibile compilare il visualizzatore e installarlo in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Prima di installare un visualizzatore in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], è tuttavia consigliabile testarlo per assicurarsi che funzioni in modo corretto. Di seguito viene descritto come creare un test harness per eseguire il visualizzatore senza installarlo in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
#### <a name="to-add-a-test-method-to-show-the-visualizer"></a>Per aggiungere un metodo di Test per mostrare il Visualizzatore  
  
1.  Aggiungere il metodo seguente alla classe `public DebuggerSide`:  
  
    ```csharp  
    public static void TestShowVisualizer(object objectToVisualize)  
    {  
       VisualizerDevelopmentHost visualizerHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));  
       visualizerHost.ShowVisualizer();  
    }  
    ```  
  
2.  Nel **compilare** menu, scegliere **Compila MyFirstVisualizer**. La compilazione del progetto dovrebbe avvenire senza problemi. Correggere gli eventuali errori di compilazione prima di continuare.  
  
 Creare quindi un progetto eseguibile per chiamare la DLL del visualizzatore. Per semplicità, si utilizzerà un progetto applicazione Console.  
  
#### <a name="to-add-a-console-application-project-to-the-solution"></a>Per aggiungere un progetto applicazione console alla soluzione  
  
1.  Nel **File** menu, scegliere **Aggiungi** e quindi fare clic su **nuovo progetto**.  
  
2.  Nel **Aggiungi nuovo progetto** della finestra di dialogo di **modelli** scegliere **applicazione Console**.  
  
3.  Nel **nome** , digitare un nome significativo per l'applicazione console, ad esempio `MyTestConsole`.  
  
4.  Fare clic su **OK**.  
  
 A questo punto è necessario aggiungere i riferimenti appropriati affinché MyTestConsole possa chiamare MyFirstVisualizer.  
  
#### <a name="to-add-necessary-references-to-mytestconsole"></a>Per aggiungere riferimenti necessari a MyTestConsole  
  
1.  In **Esplora**, fare doppio clic su **MyTestConsole** e scegliere **Aggiungi riferimento** nel menu di scelta rapida.  
  
2.  Nel **Aggiungi riferimento** nella finestra di dialogo **.NET** scegliere Microsoft.VisualStudio.DebuggerVisualizers.DLL.  
  
3.  Fare clic su **OK**.  
  
4.  Fare doppio clic su **MyTestConsole** e scegliere **Aggiungi riferimento** nuovamente.  
  
5.  Nel **Aggiungi riferimento** la finestra di dialogo, fare clic su di **progetti** scheda e quindi selezionare MyFirstVisualizer.  
  
6.  Fare clic su **OK**.  
  
 A questo punto verrà aggiunto il codice per completare il test harness.  
  
#### <a name="to-add-code-to-mytestconsole"></a>Per aggiungere codice a MyTestConsole  
  
1.  In **Esplora**, Program.cs e **rinominare** nel menu di scelta rapida.  
  
2.  Modificare il nome di Program.cs con nomi più significativi, ad esempio TestConsole.cs.  
  
     **Nota** [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] la dichiarazione di classe in base al nome del nuovo file TestConsole.cs modificata automaticamente.  
  
3.  In TestConsole.cs aggiungere il codice seguente per il `using` istruzioni:  
  
    ```csharp  
    using MyFirstVisualizer;  
    ```  
  
4.  Nel metodo `Main` aggiungere il codice seguente:  
  
    ```csharp  
    String myString = "Hello, World";  
    DebuggerSide.TestShowVisualizer(myString);  
    ```  
  
 A questo punto, si è pronti per il test del visualizzatore.  
  
#### <a name="to-test-the-visualizer"></a>Per eseguire il test del visualizzatore  
  
1.  In **Esplora**, fare doppio clic su **MyTestConsole** e scegliere **imposta come progetto di avvio** nel menu di scelta rapida.  
  
2.  Nel **Debug** menu, scegliere **avviare**.  
  
     Avvio dell'applicazione console e il visualizzatore viene visualizzata e consente di visualizzare la stringa "Hello, World".  
  
 Il visualizzatore è stato compilato e sottoposto a test.  
  
 Se si desidera utilizzare il visualizzatore in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] anziché chiamarlo semplicemente dal test harness, è necessario installarlo. Per ulteriori informazioni, vedere [procedura: installare un visualizzatore](../debugger/how-to-install-a-visualizer.md).  
  
## <a name="create-a-visualizer-using-the-visualizer-item-template"></a>Creare un visualizzatore utilizzando il modello di elemento di Visualizzatore  
 Finora, questa procedura dettagliata è stato illustrato come creare manualmente un visualizzatore. A scopo di apprendimento. Ora che si conosce il funzionamento di un visualizzatore semplice, è un modo più semplice per creare uno: utilizzando il modello di elemento.  
  
 In primo luogo, è necessario creare un nuovo progetto libreria di classi.  
  
#### <a name="to-create-a-new-class-library"></a>Per creare una nuova libreria di classi  
  
1.  Nel **File** menu, scegliere **nuovo > progetto**.  
  
2.  Nel **nuovo progetto** nella finestra di dialogo **Visual c#**selezionare **.NET Standard**.  
  
3.  Nel riquadro centrale, scegliere **libreria di classi**.   
  
4.  Nel **nome** , digitare un nome appropriato per la libreria di classi, ad esempio MySecondVisualizer.  
  
5.  Fare clic su **OK**.  
  
 A questo punto, è possibile aggiungere un elemento visualizzatore a esso:  
  
#### <a name="to-add-a-visualizer-item"></a>Per aggiungere una voce del Visualizzatore  
  
1.  In **Esplora**, fare doppio clic su MySecondVisualizer.  
  
2.  Nel menu di scelta rapida scegliere **Aggiungi** e quindi fare clic su **nuovo elemento**.  
  
3.  Nel **Aggiungi nuovo elemento** nella finestra di dialogo **elementi di Visual c#**selezionare **visualizzatore del Debugger**.  
  
4.  Nel **nome** , digitare un nome appropriato, ad esempio SecondVisualizer.cs.  
  
5.  Fare clic su **Aggiungi**.  
  
 Che è tutto a esso. Esaminare il file SecondVisualizer.cs e visualizzare il codice che il modello aggiunto automaticamente. Proseguo e provare con il codice. Ora che si conoscono i concetti di base, si utilizza la modalità di creazione di visualizzatori personalizzati più complessi e utili.  
  
## <a name="see-also"></a>Vedere anche  
 [Architettura del Visualizzatore](../debugger/visualizer-architecture.md)   
 [Procedura: installare un visualizzatore](../debugger/how-to-install-a-visualizer.md)   
 [Creazione di visualizzatori personalizzati](../debugger/create-custom-visualizers-of-data.md)
