---
title: Introduzione al Debugger di Visual Studio | Documenti Microsoft
ms.custom: H1Hack27Feb2017
ms.date: 02/07/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: get-started-article
ms.assetid: 0b3138c4-b840-446a-a15c-10ed8e2dd050
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 171b07d453c81883354848f70458bab39daa313e
ms.sourcegitcommit: 9a2f937e42305db6e3eaa7aadc235b0ba9aafc83
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2018
---
# <a name="get-started-with-the-visual-studio-debugger"></a>Iniziare con il Debugger di Visual Studio
Il debugger di Visual Studio è facile da utilizzare in qualsiasi linguaggio. Di seguito viene illustrato come eseguire il debug di un semplice programma c#, ma è possibile applicare gli stessi passaggi al codice in altri linguaggi come C++ e JavaScript.

Per guardare un video che illustra la funzionalità simili, vedere [Introduzione al Debugger](https://www.youtube.com/watch?v=FtGCi5j30YU&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=6).
  
##  <a name="BKMK_Start_debugging_a_VS_project"></a>Debug di un progetto c# di base  
 Iniziamo con una semplice applicazione console c# (**File > Nuovo > progetto**, quindi selezionare **Visual c#** e quindi **applicazione Console**). Se non si è mai lavorato con Visual Studio in precedenza, vedere [procedura dettagliata: creare una semplice applicazione](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md). Il **Main** metodo semplicemente aggiunge 1 a una variabile integer 10 volte e stampa il risultato nella console:  
  
```csharp  
static void Main(string[] args)  
{  
    int testInt = 0;  
    for (int i = 1; i <= 10; i++)  
    {  
        testInt += 1;  
    }  
    Console.WriteLine(testInt);  
}  
```  
  
 Compilare questo codice nel **Debug** configurazione. La configurazione è impostata per impostazione predefinita. Per ulteriori informazioni sulle configurazioni, vedere [informazioni sulle configurazioni della Build](../ide/understanding-build-configurations.md).  
  
 Eseguire questo codice nel debugger facendo **Debug > Avvia debug** (o **avviare** sulla barra degli strumenti o **F5**). L'applicazione si chiude quasi immediatamente, pertanto è possibile affermare se nella finestra della Console è stato stampato qualcosa.  
  
 È possibile interrompere l’esecuzione per un tempo sufficiente a visualizzare la finestra Console impostando un punto di interruzione e quindi procedendo. Per impostare un punto di interruzione, posizionare il cursore di `Console.WriteLine` di riga e fare clic su **Debug > Nuovo punto di interruzione > punto di interruzione di funzione**, oppure fare semplicemente clic nel margine sinistro della stessa riga. Il punto di interruzione apparirà come segue:  
  
 ![Impostare un punto di interruzione](../debugger/media/getstartedbreakpoint.png "GetStartedBreakpoint")  
  
 Per ulteriori informazioni sui punti di interruzione, vedere [utilizzando i punti di interruzione](../debugger/using-breakpoints.md).  
  
##  <a name="BKMK_Inspect_Variables"></a>Controllare le variabili  
 Debug spesso riguarda la ricerca di variabili che non contengono i valori desiderati in un momento specifico. Verranno illustrati alcuni dei metodi che è possibile controllare le variabili.  
  
 Avviare di nuovo il debug. L’esecuzione si interrompe prima dell’esecuzione del codice `Console.WriteLine`. È possibile causarne l'esecuzione procedendo (fare clic su **Debug > Esegui istruzione/routine** o **F10**). In questo caso è possibile scegliere **Esegui istruzione** (**F11**) si otterrebbe lo stesso risultato è la differenza sarà spiegata in un secondo momento. La riga con l’ultima parentesi graffa del metodo dovrebbe essere diventata gialla. Esaminare la finestra Console. Dovrebbe essere **10**.  
  
 È possibile passare il mouse su di **testInt** variabile per visualizzare il valore corrente in un suggerimento dati.  
  
 ![DBG&#95;Basics&#95;Data&#95;Tips](../debugger/media/dbg_basics_data_tips.png "DBG_Basics_Data_Tips")  
  
 Sotto la finestra del codice dovrebbe essere il **Auto**, **variabili locali**, e **espressioni di controllo** windows. Tali finestre mostrano i valori correnti delle variabili al momento dell’esecuzione. Entrambi i **Auto** e **variabili locali** Mostra windows **testInt** con un valore di **10**.  
  
 ![Durante il debug nella finestra Auto](../debugger/media/getstartedwindows.png "GetStartedWindows")  
  
 Per ulteriori informazioni su queste finestre, vedere [finestra variabili locali e Auto](../debugger/autos-and-locals-windows.md).  
  
 Di seguito viene illustrato come il valore della variabile cambia mentre si esegue il programma. Impostare un punto di interruzione di `testInt += 1;` di riga e riavviare il debug. Si noterà che **testInt** nel **variabili locali** e **Auto** Windows **0**, e **si** è **1**. Quando si continua il debug (**Debug > Continua**, o **continua** sulla barra degli strumenti o **F5**), è possibile vedere che il valore di **testInt** passa a **1**, quindi **2**e così via. Dopo aver verificato di tali modifiche, rimuovere il punto di interruzione (**Debug > Attiva/Disattiva punto di interruzione**, oppure fare clic su di esso nel margine) e continuare il debug. Se si desidera rimuovere tutti i punti di interruzione, fare clic su **Debug > eliminare tutti i punti di interruzione**, o **CTRL + MAIUSC + F9**, fare clic su **Sì** nella finestra di dialogo che chiede **eseguire si desidera rimuovere tutti i punti di interruzione?** .  
  
## <a name="stepping-into-and-over-function-calls"></a>Step Into e Step Over nelle chiamate di funzione  
 È possibile eseguire codice nel debugger istruzione per istruzione (**Esegui istruzione**) o è possibile eseguire codice mentre il debugger ignora funzioni (**Esegui istruzione/routine**) per ottenere rapidamente al codice che ti interessa più ( codice della funzione viene comunque eseguita). È possibile passare tra entrambi i metodi nella stessa sessione di debug.  
  
 Per visualizzare la differenza tra **Esegui istruzione** e **Esegui istruzione/routine**, è necessario aggiungere un metodo che viene chiamato da un altro metodo. Aggiungere un metodo all’applicazione C# e chiamarlo dal metodo Main. Il codice dovrebbe apparire come segue:  
  
```csharp  
static void Main(string[] args)  
{  
    Method1();  
    Console.WriteLine("end");  
}  
  
private static void Method1()  
{  
    Console.WriteLine("in Method1");  
}  
```  
  
 Impostare un punto di interruzione nella chiamata `Method1();` nel metodo Main e avviare il debug. Quando si interrompe l'esecuzione, fare clic su **Debug > Esegui istruzione** (o **Esegui istruzione** sulla barra degli strumenti o **F11**). L’esecuzione di interrompe di nuovo alla prima parentesi graffa in Method1():  
  
 ![L'esecuzione di istruzioni nel codice](../debugger/media/getstartedstepinto.png "GetStartedStepInto")  
  
 Arrestare il debug e avviare di nuovo quando l'esecuzione si interrompe al punto di interruzione, fare clic su **Debug > Esegui istruzione/routine** (o **Esegui istruzione/routine** sulla barra degli strumenti o **F10**). L'esecuzione si interrompe nuovamente in `Console.WriteLine("end");`.  
  
 Per ulteriori informazioni sull'esplorazione del codice con il debugger, vedere [spostarsi nel codice con il Debugger](../debugger/navigating-through-code-with-the-debugger.md).