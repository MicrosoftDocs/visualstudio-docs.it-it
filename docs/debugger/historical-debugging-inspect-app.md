---
title: Esaminare l'app con il debug cronologico | Microsoft Docs
description: Seguire un'indagine che usa il debug cronologico di IntelliTrace per tenere traccia di un bug in un'applicazione console C#.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 629b5d93-39b2-430a-b8ba-d2a47fdf2584
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 87987beed3750d8eda5d680b561a46b0866473b1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908414"
---
# <a name="inspect-your-app-with-intellitrace-historical-debugging-in-visual-studio-c-visual-basic-c"></a>Esaminare l'app con il debug cronologico di IntelliTrace in Visual Studio (C#, Visual Basic, C++)

È possibile utilizzare il [debug cronologico](../debugger/historical-debugging.md) per spostarsi avanti e indietro durante l'esecuzione dell'applicazione ed esaminarne lo stato.

È possibile utilizzare IntelliTrace in Visual Studio Enterprise edition (ma non le edizioni Professional o Community).

## <a name="navigate-your-code-with-historical-debugging"></a>Esplorare il codice con il debug cronologico

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

Si presuppone che il valore previsto di `resultInt` dopo la chiamata `AddAll()` è pari a 20 (il risultato di incremento `testInt` 20 volte). Si presuppone anche che il bug non sia visibile in `AddInt()` . Ma il risultato è effettivamente 44. Come è possibile individuare i bug senza scorrere `AddAll()` 10 volte? È possibile utilizzare il debug cronologico per individuare l'errore in modo più semplice e rapido. Ecco come:

1. In **strumenti > opzioni > intellitrace > generale**, verificare che IntelliTrace sia abilitato e selezionare **eventi IntelliTrace e informazioni sulle chiamate**. Se non si seleziona questa opzione, non sarà in grado di visualizzare la barra di navigazione (come illustrato di seguito).

2. Impostare un punto di interruzione nella riga `Console.WriteLine(resultInt);` .

3. Avviare il debug. Il codice viene eseguito fino al punto di interruzione. Nella finestra **Variabili locali** verificare che il valore corrente di `resultInt` sia 44.

4. Aprire la finestra **Strumenti di diagnostica** (**Debug > Mostra strumenti di diagnostica**). La finestra codici dovrebbe risultare simile alla seguente:

    ![Finestra del codice al punto di interruzione](../debugger/media/historicaldebuggingbreakpoint.png "HistoricalDebuggingBreakpoint")

5. Verrà visualizzata una doppia freccia accanto al margine sinistro, appena sopra il punto di interruzione. Quest'area viene chiamata barra di navigazione e viene usata per il debug cronologico. Fare clic sulla freccia.

    Nella finestra del codice, si noterà che la riga di codice precedente (`int resultInt = AddIterative(testInt);`) è di colore rosa. Sopra la finestra si noterà un messaggio che indica che ci si trova nel debug cronologico.

    La finestra del codice è ora simile al seguente:

    ![finestra del codice in modalità Debug cronologico](../debugger/media/historicaldebuggingback.png "HistoricalDebuggingBack")

6. Ora è possibile eseguire il metodo `AddAll()` (**F11** o il pulsante **Esegui istruzione** nella barra di navigazione. Andare avanti (**F10** o **Passa a chiamata successiva** nella barra di navigazione. La riga rosa contiene ora il `j = AddInt(j);` riga. **F10** in questo caso non passa alla riga di codice successiva. Al contrario, i passaggi per la successiva chiamata di funzione. Il debug cronologico consente di passare da una chiamata a altra e ignora le righe di codice che non includono una chiamata di funzione.

7. Eseguire un'istruzione nel metodo `AddInt()` Verrà visualizzato immediatamente il bug nel codice.

## <a name="next-steps"></a>Passaggi successivi

Questa procedura è solo un breve accenno delle operazioni che si possono eseguire con il debug cronologico.

- Per visualizzare gli snapshot durante il debug, vedere [esaminare gli Stati delle app precedenti con IntelliTrace](../debugger/view-historical-application-state.md).
- Per altre informazioni sulle diverse impostazioni e gli effetti dei diversi pulsanti nella barra di navigazione, vedere [Funzionalità IntelliTrace](../debugger/intellitrace-features.md).
