---
title: Visualizzare gli eventi con IntelliTrace | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e1c9c91a-0009-4c4e-9b4f-c9ab3a6022a7
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: ebc3067ea154c8b9a5f6e180f397c5421f2be470
ms.sourcegitcommit: 9a2f937e42305db6e3eaa7aadc235b0ba9aafc83
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2018
---
# <a name="view-events-with-intellitrace-in-visual-studio"></a>Visualizzare gli eventi con IntelliTrace in Visual Studio
È possibile usare IntelliTrace per raccogliere informazioni su eventi o categorie di eventi specifici o su singole chiamate di funzione oltre agli eventi. I passaggi seguenti illustrano come eseguire quest'operazione.  
  
 È possibile utilizzare IntelliTrace in Visual Studio Enterprise edition, ma non le edizioni Professional o Community.  
  
##  <a name="GettingStarted"></a>Configurare Intellitrace  
 È possibile provare a eseguire il debug con soli eventi IntelliTrace. Gli eventi IntelliTrace sono eventi del debugger, eccezioni, eventi .NET Framework e altri eventi di sistema. È possibile attivare o disattivare eventi specifici per il controllo degli eventi che IntelliTrace registra prima di avviare il debug. Per ulteriori informazioni, vedere [funzionalità IntelliTrace](../debugger/intellitrace-features.md).  
  
 - Attivare l'evento di IntelliTrace per l'accesso ai file. Passare al **strumenti > Opzioni > IntelliTrace > eventi IntelliTrace** pagina, quindi espandere il **File** categoria. Selezionare la categoria di eventi **File** . Saranno selezionati tutti gli eventi relativi ai file (accesso,  chiusura, eliminazione).

## <a name="create-your-app"></a>Creare l'app.
  
1.  Creare un'applicazione console C#. Aprire il file Program.cs e aggiungere l’istruzione `using` seguente:  
  
    ```csharp  
    using System.IO;  
    ```  
  
2.  Creare un <xref:System.IO.FileStream> nel metodo Main, leggere da esso, chiuderlo ed eliminare il file. Aggiungere un'altra riga per disporre di un posto per impostare un punto di interruzione:  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        FileStream fs = File.Create("WordSearchInputs.txt");  
        fs.ReadByte();  
        fs.Close();  
        File.Delete("WordSearchInputs.txt");  
  
        Console.WriteLine("done");  
    }  
    ```  
  
3.  Impostare un punto di interruzione su `Console.WriteLine("done");`  

## <a name="start-debugging-and-view-intellitrace-events"></a>Avviare il debug e visualizzare gli eventi di IntelliTrace
  
1.  Avviare il debug con la modalità consueta. (Premere **F5** oppure fare clic su **Debug > Avvia debug**.  
  
    > [!TIP]
    >  Mantenere il **variabili locali** e **Auto** finestre aperte durante il debug per visualizzare e registrare i valori in queste finestre.  
  
2.  L'esecuzione verrà interrotta in corrispondenza del punto di interruzione. Se non viene visualizzato il **strumenti di diagnostica** finestra, fare clic su **Debug > Windows > eventi IntelliTrace**.  
  
     Nella finestra **Strumenti di diagnostica** trovare la scheda **Eventi** (sono presenti 3 schede: **Eventi**, **Utilizzo della memoria**e **Utilizzo della CPU**). La scheda **Eventi** visualizza un elenco cronologico di eventi, fino all'ultimo evento prima dell'interruzione dell'esecuzione del debugger. Verrà visualizzato un evento denominato **Access WordSearchInputs.txt**.  
  
     La screenshot che segue è presa da Visual Studio 2015 Update 1.  
  
     ![IntelliTrace&#45;Update1](../debugger/media/intellitrace-update1.png "IntelliTrace-Update1")  
  
3.  Selezionare l'evento per espandere i dettagli.  
  
     La screenshot che segue è presa da Visual Studio 2015 Update 1.  
  
     ![IntelliTraceUpdate1&#45;SingleEvent](../debugger/media/intellitraceupdate1-singleevent.png "IntelliTraceUpdate1-SingleEvent")  
  
     È possibile scegliere il collegamento al percorso per aprire il file. Se il nome del percorso completo non è disponibile, viene visualizzata la finestra di dialogo **Apri file** .  
  
     Fare clic su **attivare debug cronologico**, che imposta il contesto del debugger per l'ora in cui l'evento selezionato è stato raccolto, mostrando i dati cronologici nel **Stack di chiamate**, **variabili locali** e le altre finestre del debugger partecipanti. Se il codice sorgente è disponibile, Visual Studio sposta il puntatore sul codice corrispondente nella finestra di origine per consentirne l'analisi.  
  
     La screenshot che segue è presa da Visual Studio 2015 Update 1.  
  
     ![HistoricalDebugging&#45;Update1](../debugger/media/historicaldebugging-update1.png "HistoricalDebugging-Update1")  
  
4.  Se il bug non viene trovato, provare ad analizzare altri eventi. È anche possibile che IntelliTrace registri le informazioni sulle chiamate in modo da eseguire le chiamate alle funzioni. 
  
## <a name="next-steps"></a>Passaggi successivi

È possibile utilizzare alcune delle funzionalità avanzate di IntelliTrace con il debug cronologico:

 - Per visualizzare gli snapshot, vedere [visualizzare snapshot tramite IntelliTrace passaggio-back](../debugger/how-to-use-intellitrace-step-back.md)
 - Per informazioni su come controllare le variabili e spostarsi nel codice, vedere [controllare l'app con il debug cronologico](../debugger/historical-debugging-inspect-app.md)