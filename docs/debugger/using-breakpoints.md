---
title: Utilizzare i punti di interruzione nel Debugger di Visual Studio | Documenti Microsoft
ms.custom: H1Hack27Feb2017
ms.date: 02/07/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.breakpointswin
- vs.debug.disassembly.insert
- vs.debug.sourcewin.edit
- vs.debug.file
- vs.debug.breakpt.new
- vs.debug.whenbreakpointishit
- vs.debug.breakpt.choose
- vs.debug.breakpt.location.address
- vs.debug.breakpt.constraints
- vs.debug.breakpoints.delete
- vs.debug.breakpt.location.data
- vc.breakpoints
- vs.debug.breakpt.condition
- vs.debug.breakpt.location.function
- vs.debug.breakpoints
- vs.debug.menu.insert
- vs.debug.filenames
- vs.debug.breakpt.action
- vs.debug.sourcewin.insert
- vs.debug.address
- vs.debug.data
- vs.debug.func
- vs.debug.breakpt.location.file
helpviewer_keywords:
- breakpoints, about breakpoints
ms.assetid: 020b2e97-3b3e-4b2c-872d-b5c6025e120e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 80f1ad8f7b3bc4ac1a93718943803d445aa6ca9a
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="use-breakpoints-in-the-visual-studio-debugger"></a>Utilizzare i punti di interruzione nel Debugger di Visual Studio
È possibile impostare i punti di interruzione quando si desidera arrestare l'esecuzione del debugger, ad esempio per visualizzare lo stato delle variabili di codice o per esaminare lo stack di chiamate. I punti di interruzione rappresentano una delle tecniche di debug più importanti nella casella degli strumenti dello sviluppatore.  
  
##  <a name="BKMK_Overview"></a> L'impostazione di un punto di interruzione nel codice sorgente  
 Impostare un punto di interruzione nel codice sorgente facendo clic sul margine sinistro di un file di codice sorgente o posizionando il cursore su una riga di codice e premendo F9. Il punto di interruzione viene visualizzato come un punto rosso nel margine sinistro ed anche la riga di codice risulta colorata:  
  
 ![Impostare un punto di interruzione](../debugger/media/basicbreakpoint.png "BasicBreakpoint")  
  
 Quando si esegue questo codice nel debugger, l'esecuzione viene interrotta ogni volta che viene raggiunto il punto di interruzione, prima che venga eseguito il codice su tale riga. La riga di codice sorgente è di colore giallo:  
  
 ![Esecuzione punto di interruzione arrestata](../debugger/media/breakpointexecution.png "BreakpointExecution")  
  
 A questo punto il valore di `testInt` è ancora 1.  
  
 È possibile esaminare lo stato corrente dell'applicazione, inclusi i valori delle variabili e lo stack di chiamate. Per altre informazioni sullo stack di chiamate, vedere [How to: Use the Call Stack Window](../debugger/how-to-use-the-call-stack-window.md).  
  
 È possibile impostare un punto di interruzione in qualsiasi riga di codice eseguibile. Ad esempio, nel codice C# sopra riportato è possibile impostare un punto di interruzione nella dichiarazione di variabile, nel ciclo `for` o in qualsiasi codice all'interno del ciclo `for` , ma non è possibile impostare un punto di interruzione nello spazio dei nomi, nelle dichiarazioni di classe o nella firma del metodo.  
  
##  <a name="BKMK_Set_a_breakpoint_in_a_source_file"></a> L'impostazione di un punto di interruzione (funzione)  
  È possibile interrompere l'esecuzione quando viene chiamata una funzione.
  
1. Aprire la **punti di interruzione** finestra e scegliere **nuovo > punto di interruzione di funzione**.

2. Immettere un nome di funzione per il **nome della funzione** casella. 

   Per restringere la specifica di funzione:
   
   Utilizzare il nome completo di funzione. 
   Esempio: Namespace1.ClassX.MethodA()
   
   Aggiungere i tipi di parametro di una funzione in overload. 
   Esempio: MethodA (int, string)
   
   Utilizzo di '!' simbolo per specificare il modulo.
   Esempio: App1.dll! MethodA
   
   Utilizzare l'operatore di contesto in C++ nativo.
   {(funzione), [modulo]} [+&lt;offset di riga dall'inizio del metodo&gt;] esempio: {MethodA, App1.dll}+2

3. Nel **Language** elenco a discesa, scegliere la lingua della funzione di cui si desidera interrompere l'esecuzione.
  
##  <a name="BKMK_Set_a_breakpoint_in_a_function"></a> Impostazione di altri tipi di punti di interruzione  
 È possibile anche impostare i punti di interruzione nello stack di chiamate, nella finestra Disassembly e nel codice C++ nativo, in una condizione dati o in un indirizzo di memoria.  
  
## <a name="BKMK_Set_a_breakpoint_in_the_call_stack_window"></a> Impostazione di un punto di interruzione nella finestra Stack di chiamate  
 È possibile interrompere l'esecuzione in corrispondenza dell'istruzione o della riga restituita da una funzione chiamante impostando un punto di interruzione nella finestra **Stack di chiamate** . Per altre informazioni sullo stack di chiamate, vedere [How to: Use the Call Stack Window](../debugger/how-to-use-the-call-stack-window.md). L'esecuzione del debugger deve essere stata interrotta.  
  
1.  Avviare il debug dell'applicazione e attendere che l'esecuzione venga interrotta (ad esempio, in un punto di interruzione). Aprire il **Stack di chiamate** finestra (**Debug > Windows > Stack di chiamate**, o **CTRL + ALT + C**).  
  
2.  La funzione chiamante e quindi scegliere **punto di interruzione > Inserisci punto di interruzione**, oppure usare semplicemente il tasto di scelta rapida **F9**.  
  
3.  Sul margine sinistro dello stack di chiamate, accanto al nome della chiamata di funzione, verrà visualizzato il simbolo del punto di interruzione.  
  
 Nella finestra **Punti di interruzione** , il punto di interruzione dello stack di chiamate viene visualizzato come indirizzo con una posizione di memoria corrispondente alla successiva istruzione eseguibile nella funzione. Il debugger interrompe l'esecuzione in corrispondenza dell'istruzione.  
  
 Visivamente traccia i punti di interruzione durante l'esecuzione di codice, vedere [mappare i metodi sullo stack di chiamate durante il debug](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
## <a name="setting-a-breakpoint-in-the-disassembly-window"></a>Impostazione di un punto di interruzione nella finestra Disassembly  
 Per impostare un punto di interruzione in corrispondenza di un'istruzione di assembly, è necessario che il debugger sia in modalità di interruzione.  
  
1.  Avviare il debug dell'applicazione e attendere che l'esecuzione venga interrotta (ad esempio, in un punto di interruzione). Aprire il **Disassembly** finestra (**Debug > Windows > Disassembly**, o **Ctrl + Alt + D**).  
  
2.  Fare clic sul margine sinistro dell'istruzione che si desidera interrompere o impostare il cursore nell'istruzione e premere **F9**.  
  
## <a name="BKMK_set_a_data_breakpoint_native_cplusplus_only"></a>Impostazione di un punto di interruzione dei dati (solo C++ nativo)  
 I punti di interruzione dei dati interrompono l'esecuzione quando un valore archiviato in un indirizzo di memoria specificato viene modificato. Se il valore viene letto ma non modificato, l'esecuzione non viene interrotta. Per impostare i punti di interruzione dei dati, è necessario che il debugger sia in modalità di interruzione.  
  
1.  Avviare il debug dell'applicazione e attendere che venga raggiunto un punto di interruzione. Nel **Debug** menu, scegliere **nuovo punto di interruzione > interruzione dei dati** (o aprire il **i punti di interruzione** finestra e scegliere **nuovo >interruzionedeidati**.  
  
2.  Nella casella **Indirizzo** digitare un indirizzo di memoria o un'espressione che restituisca un indirizzo di memoria. Ad esempio, digitare `&avar` per eseguire l'interruzione quando viene modificato il contenuto della variabile `avar` .  
  
3.  Nell'elenco a discesa **Conteggio byte** selezionare il numero di byte che si desidera controllare tramite il debugger. Ad esempio, se si seleziona **4**, il debugger controllerà i quattro byte a partire da `&avar` e si interromperà se viene modificato il valore di uno di questi byte.  
  
 Tenere presente che i punti di interruzione dei dati dipendono dall'applicabilità di indirizzi di memoria specifici.  
  
-   L'indirizzo di una variabile cambia da una sessione di debug a quella successiva. I punti di interruzione dei dati vengono disabilitati automaticamente alla fine di ogni sessione di debug.  
  
-   Se si imposta un punto di interruzione dei dati in una variabile locale, il punto di interruzione resta abilitato quando la funzione termina, ma l'indirizzo di memoria non è più applicabile e il comportamento del punto di interruzione è imprevedibile. Se si imposta un punto di interruzione dei dati su una variabile locale, è consigliabile rimuoverlo o disabilitarlo prima che la funzione termini.  
  
 I punti di interruzione dei dati non funzionano nei seguenti casi:  
  
-   Un processo di cui non viene eseguito il debug scrive nella posizione di memoria  
  
-   La posizione di memoria è condivisa tra due o più processi  
  
-   La posizione di memoria viene aggiornata all'interno del kernel. Ad esempio, se passata alla funzione `ReadFile` di Windows a 32 bit, la memoria viene aggiornata dalla modalità kernel e il debugger non viene interrotto durante la scrittura nella memoria.  
  
## <a name="setting-a-breakpoint-with-a-memory-address-native-c-only"></a>Impostazione di un punto di interruzione con un indirizzo di memoria (solo C++ nativo)  
 È possibile anche usare l'indirizzo di un oggetto per impostare un punto di interruzione in un metodo chiamato per un'istanza specifica di una classe.  Di seguito è riportato un esempio:  
  
 Si consideri ad esempio un oggetto di tipo `my_class` con l'indirizzo, è possibile impostare un punto di interruzione della funzione in un metodo denominato `my_method` chiamato da tale istanza.  
  
1.  Impostare un punto di interruzione dopo la creazione dell'istanza della classe.  
  
2.  Trovare l'indirizzo dell'istanza (ad esempio `0xcccccccc`).  
  
3.  Fare clic su **Debug > Nuovo punto di interruzione > interruzione della funzione** (o **ALT + F9, B**).  
  
4.  Aggiungere il testo seguente nella casella **Nome funzione** :  
  
    ```C++  
    ((my_class *) 0xcccccccc)->my_method  
    ```  
  
##  <a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a> Gestione di punti di interruzione  
 È possibile utilizzare il **i punti di interruzione** finestra (**Debug > Windows > i punti di interruzione**, o **CTRL + ALT + B**) per vedere tutti i punti di interruzione impostati nella soluzione:  
  
 ![Finestra punti di interruzione](../debugger/media/breakpointswindow.png "BreakpointsWindow")  
  
 La finestra **Punti di interruzione** costituisce tuttavia una posizione centrale da cui gestire tutti i punti di interruzione, che può essere particolarmente utile per una soluzione di grandi dimensioni o per uno scenario di debug complesso in cui i punti di interruzione sono cruciali. Se è necessario salvare o condividere lo stato e la posizione di un set di punti di interruzione, è possibile esportare e importare i punti di interruzione unicamente dalla finestra **Punti di interruzione** .  
  
##  <a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a> Punti di interruzione avanzati  
  
## <a name="breakpoint-conditions"></a>Condizioni punto di interruzione  
 È possibile controllare dove e quando un punto di interruzione viene eseguito impostando le condizioni.  
  
1.  Fare clic con il pulsante destro del mouse sul punto di interruzione o passare il mouse sul punto di interruzione e scegliere l'icona di impostazioni.  
  
2.  Nel menu di scelta rapida, selezionare **Condizioni**. Viene visualizzata la finestra **Impostazioni del punto di interruzione** :  
  
 ![Impostazioni punto di interruzione](../debugger/media/breakpointsettings.png "BreakpointSettings")  
  
 Quando si seleziona la casella **Condizioni** , la finestra si espande per visualizzare i diversi tipi di condizioni.  
  
 **Espressione condizionale:** quando si seleziona Espressione condizionale, è possibile scegliere due condizioni: **È true** e **Se modificato**. Scegliere **È true** se si desidera interrompere l'esecuzione quando l'espressione viene soddisfatta, oppure scegliere **Se modificato** se si desidera interrompere l'esecuzione quando il valore dell'espressione è cambiato.  
  
 Nell'esempio seguente il punto di interruzione viene impostato in modo che venga raggiunto solo quando il valore di `testInt` è **4**:  
  
 ![Condizione punto di interruzione è true](../debugger/media/breakpointconditionistrue.png "BreakpointConditionIsTrue")  
  
 Nell'esempio seguente il punto di interruzione viene impostato in modo che venga raggiunto solo quando il valore di `testInt` viene modificato:  
  
 ![Punto di interruzione quando modificato](../debugger/media/breakpointwhenchanged.png "BreakpointWhenChanged")  
  
 Il comportamento del campo Se modificato è diverso per i diversi linguaggi di programmazione. Se si sceglie **Se modificato** per il codice nativo, la prima valutazione della condizione non viene considerata una modifica dal debugger, pertanto il punto di interruzione non viene raggiunto alla prima valutazione. Se si sceglie **quando modificato** per codice gestito, il punto di interruzione viene raggiunto alla prima valutazione dopo **quando modificato** è selezionata.  
  
 Se si imposta una condizione del punto di interruzione con sintassi non valida, viene visualizzato un messaggio di avviso. Se viene specificata una condizione del punto di interruzione con sintassi valida ma con semantica non valida, viene visualizzato un messaggio di avviso la prima volta che si raggiunge il punto di interruzione. In entrambi i casi, il debugger interrompe l'esecuzione quando si raggiunge il punto di interruzione non valido. Il punto di interruzione viene ignorato solo se la condizione è valida e restituisce `false`.  
  
 La condizione può essere una qualsiasi espressione valida riconosciuta dal debugger. Per altre informazioni sulle espressioni valide, vedere [Expressions in the Debugger](../debugger/expressions-in-the-debugger.md).  

> [!NOTE]
> È possibile utilizzare **CTRL + INVIO** per chiudere la **impostazioni punto di interruzione** finestra.
  
## <a name="using-object-ids-in-breakpoint-conditions-c-and-f"></a>Uso di ID oggetto in condizioni del punto di interruzione (C# e F#)  
 Possono esistere situazioni in cui si vuole osservare il comportamento di un oggetto specifico, ad esempio si potrebbe voler scoprire perché un oggetto è stato inserito più volte in una raccolta. In C# e F# è possibile creare ID oggetto per istanze specifiche dei [tipi riferimento](/dotnet/csharp/language-reference/keywords/reference-types) e usarle nelle condizioni del punto di interruzione. L'ID oggetto viene generato dai servizi di debug di Common Language Runtime (CLR) e associato all'oggetto.  Per creare un ID oggetto, procedere come segue:  
  
1.  Impostare un punto di interruzione nel codice dopo la creazione dell'oggetto.  
  
2.  Avviare il debug e quando l'esecuzione si arresta nel punto di interruzione, trovare il punto di interruzione nella finestra **Variabili locali** , fare clic con il pulsante destro del mouse su di esso e scegliere **Crea ID oggetto**.  
  
     Nella finestra **$** verrà visualizzato il simbolo **Variabili locali** . Si tratta dell'ID oggetto.  
  
3.  Aggiungere un nuovo punto di interruzione condizionale nella posizione da analizzare, ad esempio il momento in cui l'oggetto viene aggiunto alla raccolta.  
  
4.  Usare l'ID oggetto nel campo Espressione condizionale. Ad esempio, se c'è una variabile `item` che fa riferimento all'oggetto da aggiungere alla raccolta, inserire **item == $n**, dove **n** è il numero ID dell'oggetto.  
  
     L'esecuzione si interromperà in corrispondenza del punto in cui l'oggetto deve essere aggiunto alla raccolta.  
  
 Se in un secondo momento si vuole eliminare l'ID oggetto, fare doppio con il pulsante destro del mouse nella finestra **Variabili locali** e scegliere **Elimina ID oggetto**.  
  
 Notare che gli ID oggetto creano riferimenti deboli e non impediscono all'oggetto di essere sottoposto a Garbage Collection. Sono validi solo per la sessione di debug corrente.  
  
## <a name="hit-count"></a>Numero di passaggi  
 Se si ritiene che un ciclo nel codice inizi a presentare un comportamento errato dopo un certo numero di iterazioni, è possibile impostare un punto di interruzione per arrestare l'esecuzione dopo un numero specificato di passaggi alla riga di codice, anziché dover premere ripetutamente associata **F5**  per raggiungere il livello di iterazione.  
  
 Nella finestra **Impostazioni del punto di interruzione** impostare la condizione su **Numero di passaggi**. È quindi possibile specificare il numero di iterazioni. Nell'esempio seguente il punto di interruzione viene impostato in modo che venga raggiunto con qualsiasi altra iterazione:  
  
 ![Numero di passaggi punto di interruzione](../debugger/media/breakpointhitcount.png "BreakpointHitCount")  
  
## <a name="filter"></a>Filtro  
 È possibile limitare un punto di interruzione da attivare solo su dispositivi specificati o in thread e processi specificati.  
  
 Nella finestra **Impostazioni del punto di interruzione**impostare la condizione su **Filtro**. Immettere una o più delle espressioni seguenti.  
  
-   MachineName = "name"  
  
-   ProcessId = value  
  
-   ProcessName = "name"  
  
-   ThreadId = value  
  
-   ThreadName = "name"  
  
 Racchiudere i valori String tra virgolette doppie. È possibile combinare clausole usando `&` (AND), `||` (OR), `!` (NOT) e le parentesi.  
  
##  <a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a> Azioni dei punti di interruzione e punti di analisi  
 Un punto di analisi è un punto di interruzione che visualizza un messaggio nella finestra Output. Un punto di analisi può fungere da istruzione di analisi temporanea nel linguaggio di programmazione.  
  
 Nella finestra **Impostazioni del punto di interruzione** selezionare la casella **Azioni** . Scegliere **Registra un messaggio nella finestra di output** nel gruppo **Azione** . È possibile visualizzare una stringa generica, ad esempio **Questo è un test**. Per includere il valore di una variabile o espressione, racchiuderlo tra parentesi graffe.  È inoltre possibile utilizzare identificatori di formato ([c#](../debugger/format-specifiers-in-csharp.md) e [C++](../debugger/format-specifiers-in-cpp.md)) per i valori inclusi in un punto di analisi.
  
 Per interrompere l'esecuzione quando viene raggiunto il punto di analisi, deselezionare la casella di controllo **Continua esecuzione** . Se l'opzione **Continua esecuzione** è selezionata, l'esecuzione non viene interrotta. In entrambi i casi, il messaggio viene visualizzato.  
  
 È possibile usare le seguenti parole chiave speciali nel **Messaggio**.  
  
|||  
|-|-|  
|**$ADDRESS**|Istruzione corrente|  
|**$CALLER**|Scegliere il nome della funzione|  
|**$CALLSTACK**|Stack di chiamate|  
|**$FUNCTION**|Nome della funzione corrente|  
|**$PID**|ID processo|  
|**$PNAME**|Nome processo|  
|**$TID**|ID thread|  
|**$TNAME**|Nome thread|  
|**$TICK**||  
|**$TNAME**||  
  
##  <a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a> Etichette dei punti di interruzione  
 Le etichette dei punti di interruzione sono usate solo nella finestra **Punti di interruzione** per ordinare e filtrare l'elenco dei punti di interruzione. Per aggiungere un'etichetta a un punto di interruzione, scegliere la riga del punto di interruzione, quindi scegliere **Etichetta** dal menu di scelta rapida.  
  
## <a name="export-and-import-breakpoints"></a>Esportare e importare punti di interruzione  
 È possibile esportare un punto di interruzione in un file XML facendo clic con il pulsante destro del mouse sul punto di interruzione e selezionando **Esporta**. Il file viene salvato per impostazione predefinita nella directory della soluzione. Per importare i punti di interruzione, aprire la finestra **Punti di interruzione** (**CTRL+ALT+B**) e nella barra degli strumenti fare clic sulla freccia rivolta verso destra (la descrizione comando è **Importa i punti di interruzione da un file**).  
  
## <a name="see-also"></a>Vedere anche  
[Risolvere i punti di interruzione nel Debugger di Visual Studio](../debugger/troubleshooting-breakpoints.md)  
[Spostarsi nel codice con il Debugger](../debugger/navigating-through-code-with-the-debugger.md)
