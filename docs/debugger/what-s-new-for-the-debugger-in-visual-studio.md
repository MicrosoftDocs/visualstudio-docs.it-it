---
title: Novità relative al Debugger di Visual Studio 2017 | Documenti Microsoft
ms.custom: ''
ms.date: 03/07/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, what's new
- what's new [debugger]
- debugging [Visual Studio], what's new
- what's new [Visual Studio], debugging
ms.assetid: 2aed9caa-2384-4e49-8595-82d8b06cf271
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 07f25edb63e3418bab44d71bc8314d3aa83e7a84
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="whats-new-for-the-debugger-in-includevsdev15miscincludesvsdev15mdmd"></a>Novità relative al Debugger di [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]

Il debugger include le nuove funzionalità:

- Novità di 15,5, il **Debugger Snapshot** un'istantanea delle applicazioni in produzione quando viene eseguito codice che si è interessati. Per indicare al debugger di creare uno snapshot, impostare punti di ancoraggio e punti di registrazione nel codice. Il debugger consente di vedere esattamente cosa non ha funzionato, senza alcun impatto sul traffico dell'applicazione di produzione. Snapshot Debugger può essere utile per ridurre notevolmente il tempo necessario per risolvere i problemi che si verificano negli ambienti di produzione.

    La raccolta di snapshot è disponibile per le seguenti app Web in esecuzione in Servizio app di Azure:

    * Applicazioni ASP.NET in esecuzione in .NET Framework 4.6.1 o versioni successive.
    * Applicazioni ASP.NET Core in esecuzione in .NET Core 2.0 o versioni successive in Windows.

    Per ulteriori informazioni, vedere [Debug in tempo reale delle App ASP.NET utilizzando il Debugger Snapshot](../debugger/debug-live-azure-applications.md).

- Novità di 15,5 solo in Visual Studio Enterprise **IntelliTrace passaggio-back** automaticamente un'istantanea dell'applicazione in ogni punto di interruzione e il debugger evento di passaggio. Gli snapshot registrati consentono di tornare indietro ai punti di interruzione o ai passaggi precedenti e visualizzare stati passati dell'applicazione. La funzionalità per tornare indietro di IntelliTrace può consentire di risparmiare tempo quando si vuole visualizzare uno stato precedente dell'applicazione senza riavviare il debug o ricreare lo stato dell'app desiderato.

    È possibile esplorare e visualizzare gli snapshot tramite i pulsanti **Vai indietro** e **Vai avanti** sulla barra degli strumenti di Debug. Questi pulsanti consentono di spostarsi tra gli eventi visualizzati nella scheda **Eventi** della finestra **Strumenti di diagnostica**.

    ![Passo indietro e Avanti pulsanti](../debugger/media/intellitrace-step-back-icons-description.png  "pulsanti con le versioni precedenti di passaggio e l'inoltro")

    Per altre informazioni, vedere la pagina [Visualizzare gli snapshot con la funzionalità per tornare indietro di IntelliTrace](../debugger/how-to-use-intellitrace-step-back.md).

- Il **supporto eccezioni** sostituisce le informazioni sulle eccezioni e visualizzato in una finestra di dialogo non modale in cui si è verificato l'errore. Il **supporto eccezioni** fornisce un accesso più rapido per eventuali eccezioni interne, analisi aggiuntive per il debugger (se disponibile) e l'accesso immediato al **impostazioni eccezioni** per l'eccezione. L'Helper eccezioni possono anche essere trascinata in una vista mobile, se è bloccato da un elemento che si desidera visualizzare.

    Ad esempio, un **NullReferenceException** ora mostra la variabile contenente il riferimento null (informazioni aggiuntive).

    ![Supporto di eccezioni del debugger](../debugger/media/dbg-exception-helper.png "DbgExceptionHelper")

    Per altre informazioni, vedere il post del blog relativo all'[uso del nuovo supporto eccezione in Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/31/using-the-new-exception-helper-in-visual-studio-15-preview/).

- È ora possibile eseguire una riga di codice durante la pausa nel debugger selezionando il **esecuzione qui** icona freccia verde (l'icona visualizzata durante il passaggio del mouse su una riga di codice). In questo modo si elimina la necessità di impostare punti di interruzione temporanei.

    ![Esecuzione del debugger alla fare clic su](../debugger/media/dbg-run-to-click.png "DbgRunToClick") 

- È possibile impostare le condizioni per le eccezioni nel **impostazioni eccezioni** la finestra di dialogo (è possibile farlo tramite il **modifica condizione** icona nella finestra di dialogo Impostazioni eccezioni o utilizzando il menu di scelta rapida nel eccezione). Le condizioni attualmente supportate includono i nomi di modulo da includere o escludere per l'eccezione.

    ![Le condizioni di un'eccezione](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

- Connettersi al processo, finestra di dialogo include una nuova funzionalità di ricerca che è possibile identificare più rapidamente il processo che si desidera associare a.

    ![Ricerca nella connessione al processo](../debugger/media/dbg-attach-to-process-search.png "DbgAttachToProcessSearch") 

Per ulteriori informazioni su queste nuove funzionalità, vedere il [note sulla versione per [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] ](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes#debuggingdiag).
  
## <a name="see-also"></a>Vedere anche  
 [Debug in Visual Studio](../debugger/index.md)  
 [Tour delle funzionalità del debugger](../debugger/debugger-feature-tour.md)