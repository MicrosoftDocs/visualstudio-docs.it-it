---
title: Controllare l'app con il debug cronologico | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 629b5d93-39b2-430a-b8ba-d2a47fdf2584
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d6a8e4ec27c73516d2eb4ea79ee8beee91dfd19c
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="inspect-your-app-with-intellitrace-historical-debugging-in-visual-studio"></a>Controllare l'app con IntelliTrace in Visual Studio di debug cronologico
È possibile utilizzare [debug cronologico](../debugger/historical-debugging.md) per spostarsi all'indietro e avanti l'esecuzione dell'applicazione e controllare lo stato.  
  
È possibile utilizzare IntelliTrace in Visual Studio Enterprise edition ma non le edizioni Professional o Community.  
  
## <a name="navigate-your-code-with-historical-debugging"></a>Passare il codice con il debug cronologico  
 Iniziamo con un semplice programma che dispone di un bug. Aggiungere il codice seguente al file App.xaml.cs nell'applicazione:  
  
```csharp  
static void Main(string[] args)  
{  
    int testInt = 0;  
    int resultInt = AddAll(testInt);  
    Console.WriteLine(resultInt);  
}  
private static int AddAll(int j)  
{  
    for (int i = 0; i < 20; i++)  
    {  
        j = AddInt(j);  
    }  
    return j;  
}  
  
private static int AddInt(int add)  
{  
    if (add == 10)  
    {  
        return add += 25;  
    }  
    return ++add;  
}  
```  
  
 Si presuppone che il valore previsto di `resultInt` dopo la chiamata `AddAll()` è 20 (il risultato di incremento `testInt` 20 volte). (Si presuppone inoltre che è possibile visualizzare i bug in `AddInt()`). Ma il risultato è effettivamente 44. Come è possibile individuare i bug senza scorrere `AddAll()` 10 volte? È possibile usare il debug cronologico per individuare l'errore più veloce e più facilmente. Ecco come:  
  
1.  In **strumenti > Opzioni > IntelliTrace > Generale**, verificare che IntelliTrace sia abilitato e selezionare **eventi IntelliTrace e informazioni sulla chiamata**. Se non si seleziona questa opzione, non sarà in grado di visualizzare la barra di navigazione (come illustrato di seguito).  
  
2.  Impostare un punto di interruzione su `Console.WriteLine(resultInt);` linea  
  
3.  Avviare il debug. Il codice viene eseguito fino al punto di interruzione. Nel **variabili locali** finestra, è possibile vedere che il valore di `resultInt` è 44.  
  
4.  Aprire il **strumenti di diagnostica** finestra (**Debug > Mostra strumenti di diagnostica**). La finestra codici dovrebbe risultare simile alla seguente:  
  
     ![Finestra del codice nel punto di interruzione](../debugger/media/historicaldebuggingbreakpoint.png "HistoricalDebuggingBreakpoint")  
  
5.  Verrà visualizzata una doppia freccia accanto al margine sinistro, appena sopra il punto di interruzione. Quest'area viene chiamata la barra di navigazione e viene utilizzata per il debug cronologico. Fare clic sulla freccia.  
  
     Nella finestra del codice, si noterà che la riga di codice precedente (`int resultInt = AddIterative(testInt);`) è di colore rosa. Sopra la finestra, si verrà visualizzato un messaggio che ci si trova nel debug cronologico.  
  
     La finestra del codice è ora simile al seguente:  
  
     ![finestra di codice in modalità di debug cronologico](../debugger/media/historicaldebuggingback.png "HistoricalDebuggingBack")  
  
6.  Ora in cui è possibile eseguire il `AddAll()` metodo (**F11**, o **Esegui istruzione** pulsante nella barra di navigazione. Passo avanti (**F10**, o **passare alla prossima connessione** nella barra di navigazione. La riga rosa contiene ora il `j = AddInt(j);` riga. **F10** in questo caso non esegue le istruzioni per la riga successiva del codice. Al contrario, i passaggi per la successiva chiamata di funzione. Il debug cronologico consente di passare da una chiamata a altra e ignora le righe di codice che non includono una chiamata di funzione.  
  
7.  Eseguire un'istruzione nel metodo `AddInt()` Verrà visualizzato immediatamente il bug nel codice.  

## <a name="next-steps"></a>Passaggi successivi

Questa procedura solo un assaggio delle operazioni eseguibili con il debug cronologico.

- Per visualizzare gli snapshot durante il debug, vedere [visualizzare snapshot tramite IntelliTrace passaggio-back](../debugger/how-to-use-intellitrace-step-back.md).
- Per ulteriori informazioni sulle diverse impostazioni e gli effetti dei diversi pulsanti nella barra di navigazione, vedere [funzionalità IntelliTrace](../debugger/intellitrace-features.md).