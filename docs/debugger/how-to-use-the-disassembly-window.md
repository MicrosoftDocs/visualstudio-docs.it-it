---
title: Visualizzare il codice Disassembly nel Debugger di Visual Studio | Documenti Microsoft
ms.custom: H1Hack27Feb2017
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.disassembly
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- assembly language, debugging inline assembly code
- breakpoints, Disassembly window
- Disassembly window
- machine code
ms.assetid: eaf84dd0-c82d-481b-af51-690b74e7794c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 46c0ae689a9d514983aeb747bebc6cb9905c6e11
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="view-disassembly-code-in-the-visual-studio-debugger"></a>Visualizzare il codice Disassembly nel Debugger di Visual Studio
Questa funzionalità è disponibile solo se è abilitato il debug a livello di indirizzo di **opzioni** nella finestra di dialogo **debug** nodo. Non è invece disponibile per il debug di script o SQL.  
  
 Il **Disassembly** finestra viene visualizzato il codice assembly corrispondente alle istruzioni create dal compilatore. Se si sta eseguendo il debug di codice gestito, tali istruzioni in linguaggio assembly corrispondono al codice nativo creato dal compilatore JIT (Just-In-Time), non al linguaggio MSIL (Microsoft Intermediate Language) generato dal compilatore di Visual Studio.  
  
 Oltre alle istruzioni di assembly, il **Disassembly** finestra consente di visualizzare le seguenti informazioni facoltative:  
  
-   L'indirizzo di memoria in cui si trova ciascuna istruzione. Per applicazioni native, si tratta dell'indirizzo di memoria effettivo. Per Visual Basic, C# o codice gestito, si tratta dell'offset dall'inizio della funzione.  
  
-   Codice sorgente dal quale deriva il codice assembly.  
  
-   Byte del codice: rappresentazioni in byte delle effettive istruzioni in linguaggio macchina o MSIL.  
  
-   Nomi di simboli per gli indirizzi di memoria.  
  
-   Numeri di riga corrispondenti al codice sorgente.  
  
 Le istruzioni in linguaggio assembly sono costituite da elementi mnemonici, che sono abbreviazioni di nomi di istruzioni e simboli che rappresentano variabili, registri e costanti. Ogni istruzione in linguaggio macchina è rappresentata da un elemento mnemonico in linguaggio assembly, seguito in genere da una o più variabili, registri o costanti.  
  
 Se non si è in grado di leggere il linguaggio assembly e si desidera sfruttare appieno i vantaggi della finestra Disassembly, consultare un buon manuale sulla programmazione in linguaggio assembly. Tale argomento esula dallo scopo di questa breve introduzione alla finestra Disassembly.  
  
 Dal momento che il codice assembly si basa in modo rilevante sui registri del processore o, nel caso di codice gestito, sui registri di Common Language Runtime, sarà particolarmente vantaggioso utilizzare la finestra Disassembly insieme alla finestra Registri, in cui può essere esaminato il contenuto dei registri.  
  
 È poco probabile che si abbia desiderio o necessità di visualizzare istruzioni in linguaggio macchina nel loro formato numerico non elaborato anziché in formato di linguaggio assembly. Tuttavia, qualora ciò fosse necessario, sarà possibile utilizzare la finestra Memoria o scegliere Mostra byte del codice dal menu di scelta rapida della finestra Disassembly.  
  
> [!NOTE]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-display-the-disassembly-window"></a>Per visualizzare la finestra Disassembly  
  
-   Durante il debug, selezionare **Debug > Windows** e quindi fare clic su **Disassembly**.
  
### <a name="to-turn-optional-information-on-or-off"></a>Per attivare o disattivare la visualizzazione delle informazioni opzionali  
  
-   Fare doppio clic su di **Disassembly** finestra e selezionare o deselezionare le opzioni desiderate nel menu di scelta rapida.  
  
     Una freccia gialla sul margine sinistro indica la posizione del punto di esecuzione corrente. Per il codice nativo la posizione corrisponde al contatore di programma della CPU. Questo indicatore mostra l'istruzione successiva che verrà eseguita dal programma.  
  
     Per ulteriori informazioni, vedere [spostamento verso l'alto o verso il basso nella memoria](../debugger/how-to-page-up-or-down-in-memory.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione dei dati nel Debugger](../debugger/viewing-data-in-the-debugger.md)   
 [Procedura: Usare la finestra Registri](../debugger/how-to-use-the-registers-window.md)