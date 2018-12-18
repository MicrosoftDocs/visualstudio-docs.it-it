---
title: Debug di progetti DLL | Documenti Microsoft
ms.custom: 
ms.date: 05/23/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging DLLs
- templates, debugging DLLs
- DLLs, debugging
- debugging [Visual Studio], DLLs
ms.assetid: 433cab30-d191-460b-96f7-90d2530ca243
caps.latest.revision: "38"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7b43d7c5fb8d66e758a44b86d4918f04599d6147
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-dll-projects-from-visual-studio"></a>Debug di progetti di DLL da Visual Studio
I seguenti modelli di Visual Studio creano una DLL:  
  
-   (C++, C# e Visual Basic): Libreria di classi   

-   (C++): il progetto di DLL di Console Win32
  
     Per altre informazioni, vedere [MFC Debugging Techniques](../debugger/mfc-debugging-techniques.md).

-   (C++, C# e Visual Basic): Libreria di controlli Windows Forms
  
     Il debug di una libreria di controlli Windows Form è simile al debug di un progetto libreria di classi. Nella maggior parte dei casi si effettua una chiamata al controllo Windows da un altro progetto. Quando si esegue il debug del progetto chiamante, è possibile eseguire l'istruzione del codice del controllo Windows, impostare i punti di interruzione ed eseguire altre operazioni di debug. Per altre informazioni, vedere [Controlli Windows Form](/dotnet/framework/winforms/controls/index).  

  
##  <a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a> Building a debug version  
 Indipendentemente dalla modalità di avvio del debug, accertarsi di compilare innanzitutto la versione di debug della DLL e che tale versione si trovi nella posizione prevista dall'applicazione. Anche se ciò potrebbe sembrare ovvio, è importante non omettere questo passaggio in quanto l'applicazione potrebbe rilevare una versione differente della DLL e caricarla. A questo punto, il programma continuerebbe l'esecuzione e non si riuscirebbe a comprendere il motivo per il quale il punto di interruzione non è stato raggiunto. Durante il debug, è possibile controllare le DLL caricate dal programma visualizzando la finestra **Moduli** del debugger. In **questa** finestra sono elencate le DLL o gli EXE caricati nel processo sottoposto a debug. Per altre informazioni, vedere [How to: Use the Modules Window](../debugger/how-to-use-the-modules-window.md).  
 Affinché il debugger possa connettersi a codice scritto in C++, è necessario che venga generato l'elemento `DebuggableAttribute`. È possibile aggiungere automaticamente questo elemento al codice mediante il collegamento all'opzione del linker [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) .  
  
##  <a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> Mixed-Mode debugging  
 L'applicazione che chiama la DLL può essere scritta in codice gestito o nativo. Se la DLL gestita viene chiamata da codice nativo e si desidera eseguire il debug di entrambi, attivare sia il debugger del codice gestito sia quello del codice nativo. È possibile selezionare nel  **\<progetto > pagine delle proprietà** finestra o nella finestra di dialogo. L'esecuzione di questa operazione varia a seconda che il debug venga avviato dal progetto della DLL o da quello dell'applicazione chiamante. Per altre informazioni, vedere [How to: Debug in Mixed Mode](../debugger/how-to-debug-in-mixed-mode.md).  
  
##  <a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a> Changing default configurations  
 Quando si crea un progetto di applicazione console mediante il modello di progetto, in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] vengono definite automaticamente le impostazioni necessarie per le configurazioni di debug e di rilascio. Se necessario, è possibile modificare tali impostazioni. Per ulteriori informazioni, vedere [le impostazioni di progetto per una configurazione di Debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md), [le impostazioni di progetto per configurazioni di Debug c#](../debugger/project-settings-for-csharp-debug-configurations.md), [le impostazioni di progetto per una configurazione di Debug Visual Basic ](../debugger/project-settings-for-a-visual-basic-debug-configuration.md), e [procedura: impostare Debug e rilascio delle configurazioni](../debugger/how-to-set-debug-and-release-configurations.md).  
  
##  <a name="vxtskdebuggingdllprojectswaystodebugthedll"></a> Ways to debug the DLL  
 In ciascun progetto descritto in questa sezione viene creata una DLL. Le DLL non possono essere eseguite direttamente, ma devono essere chiamate da un'applicazione, in genere un file EXE. Per altre informazioni, vedere [Creating and Managing Visual C++ Projects](/cpp/ide/creating-and-managing-visual-cpp-projects). L'applicazione chiamante può soddisfare uno dei criteri seguenti:  
  
-   Essere un'applicazione incorporata in un altro progetto della stessa soluzione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] contenente la libreria di classi.  
  
-   Essere un'applicazione esistente già distribuita in un computer di test o di produzione.  
  
-   Trovarsi sul Web ed essere accessibile tramite un URL.  
  
-   Essere un'applicazione Web contenente una pagina Web che incorpora la DLL.  
  
###  <a name="vxtskdebuggingdllprojectsthecallingapplication"></a> Debugging the calling application  
Per eseguire il debug di una DLL, iniziare con il debug dell'applicazione chiamante, che in genere è un file EXE o un'applicazione Web. Questo debug può essere eseguito in vari modi.  
  
-   Se è disponibile un progetto per l'applicazione chiamante, è possibile aprirlo e avviare l'esecuzione dal menu **Debug** . Per ulteriori informazioni, vedere [Introduzione al debugger](../debugger/getting-started-with-the-debugger.md).  
  
-   Se l'applicazione chiamante è un programma già distribuito in un computer di test o di produzione ed è già in esecuzione, è possibile stabilire una connessione. Utilizzare questa modalità se la DLL è un controllo ospitato in Internet Explorer oppure un controllo in una pagina Web. Per altre informazioni, vedere [How to: Attach to a Running Process](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
-   È possibile eseguire il debug dal progetto di DLL. Per altre informazioni, vedere [How to: Debug from a DLL Project](../debugger/how-to-debug-from-a-dll-project.md).  
  
-   È possibile eseguire il debug dal [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [finestra controllo immediato](#vxtskdebuggingdllprojectstheimmediatewindow). In tal caso, la finestra **Controllo immediato** svolgerà il ruolo dell'applicazione.  
  
Prima di iniziare il debug dell'applicazione chiamante, è possibile impostare un punto di interruzione nella libreria di classi. Per altre informazioni, vedere [Using Breakpoints](../debugger/using-breakpoints.md). Una volta raggiunto il punto di interruzione, è possibile eseguire il codice un'istruzione alla volta, osservandone l'esecuzione in ciascuna riga fino a isolare il problema. Per ulteriori informazioni, vedere [esplorare il codice nel debugger](../debugger/navigating-through-code-with-the-debugger.md).
  
###  <a name="vxtskdebuggingdllprojectstheimmediatewindow"></a> Finestra di controllo immediato  
 È possibile valutare le funzioni o i metodi nella DLL senza disporre di un'applicazione chiamante, ma eseguendo il debug in fase di progettazione e utilizzando la finestra **Controllo immediato** . Per eseguire questo tipo di debug, effettuare le seguenti operazioni dopo avere aperto il progetto di DLL:  
  
1.  Visualizzare la finestra di controllo **immediato** del debugger.  
  
2.  Per testare un metodo denominato `Test` nella classe `Class1`, creare un'istanza di un oggetto di tipo `Class1` digitando il codice C# seguente nella finestra Controllo immediato. Questo codice gestito funziona per Visual Basic e C++ con opportune modifiche alla sintassi:  
  
    ```  
    Class1 obj = new Class1();  
    ```  
  
     In C# tutti i nomi devono essere completi. Inoltre, i metodi o le variabili devono trovarsi nell'ambito e nel contesto correnti della sessione di debug.  
  
3.  Se `Test` accetta un parametro `int` , valutare `Test` usando la finestra **Controllo immediato** :  
  
    ```  
    ?obj.Test(10)  
    ```  
  
     Il risultato verrà indicato nella finestra di controllo **immediato**.  
  
4.  Se si desidera continuare a eseguire il debug di `Test` , inserire un punto di interruzione nel metodo e valutare di nuovo la funzione:  
  
    ```  
    ?obj.Test(10);  
    ```  
  
     Quando verrà raggiunto il punto di interruzione, sarà possibile eseguire `Test`un'istruzione alla volta. Al termine dell'esecuzione di `Test`, nel debugger verrà ripristinata la modalità di progettazione.

## <a name="vxtskdebuggingdllprojectsexternal"></a>Eseguire il debug di una DLL esterna da un progetto C++

Se si esegue il debug di una DLL esterna al progetto, le funzionalità di debug disponibili (ad esempio avanzamento tramite codice) dipenderà il [configurazione di debug della DLL](#vxtskdebuggingdllprojectsbuildingadebugversion) quando è stato compilato e indica se il [file con estensione PDB](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) e altri file necessari per la DLL sono disponibili.

Il progetto deve essere in grado di trovare la DLL e il file con estensione pdb utilizzato per il debug. È possibile creare un'attività di compilazione personalizzata per copiare i file di  **\<cartella del progetto > \Debug.** cartella di output oppure è possibile copiare manualmente i file nella cartella di output.

È possibile impostare facilmente i percorsi dei file di intestazione e i file *.lib nelle pagine delle proprietà (fare clic sul progetto C++ e scegliere **Visualizza proprietà**, quindi scegliere **tutte le configurazioni**) senza la necessità di copiare li nella cartella di output:

- Cartella C/C++ (categoria generale) - specificare la cartella contenente file di intestazione di **directory di inclusione aggiuntive** campo.
- Cartella Linker (categoria generale) - specificare la cartella contenente il file con estensione LIB nel **Directory librerie aggiuntive** campo. 
- Cartella Linker (categoria Input) - specificare il percorso completo e nome per il file con estensione LIB nel **dipendenze aggiuntive** campo.

Quando la configurazione è corretta, è possibile eseguire il debug dall'avvio dell'esecuzione dal **Debug** menu.

Per ulteriori informazioni sulle impostazioni di progetto, vedere [pagine delle proprietà (Visual C++)](/cpp/ide/property-pages-visual-cpp).
  
## <a name="see-also"></a>Vedere anche  
 [Debug di codice gestito](../debugger/debugging-managed-code.md)   
 [Tipi di progetto di Visual C++](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [Tipi di progetto C#, F# e Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Impostazioni di progetto per una configurazione di Debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Impostazioni di progetto per le configurazioni di debug C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Impostazioni di progetto per una configurazione di debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Sicurezza del debugger](../debugger/debugger-security.md)