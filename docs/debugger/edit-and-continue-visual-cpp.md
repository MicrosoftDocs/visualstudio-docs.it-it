---
title: Modifica e continuazione (Visual C++) | Documenti Microsoft
ms.custom: 
ms.date: 05/31/2017
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
- Edit and Continue [C++]
- debugging [C++], Edit and Continue
- C/C++, Edit and Continue
ms.assetid: 1815251e-a877-433e-9e5e-69bd9ba254c7
caps.latest.revision: "25"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d1b9326aa862bd03bb989a4d6863e94dae7bddef
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="edit-and-continue-visual-c"></a>Modifica e continuazione (Visual C++)
È possibile usare Modifica e continuazione nei progetti Visual C++. Vedere [modifiche di codice supportato (C++)](../debugger/supported-code-changes-cpp.md) per informazioni sulle limitazioni di modifica e continuazione.
  
Per ulteriori informazioni sui miglioramenti apportati a Visual Studio 2015 Update 3, vedere [C++ Modifica e continuazione in Visual Studio 2015 Update 3](https://blogs.msdn.microsoft.com/vcblog/2016/07/01/c-edit-and-continue-in-visual-studio-2015-update-3/).  
  
 Il [/Zo (ottimizzare il debug)](/cpp/build/reference/zo-enhance-optimized-debugging) opzione del compilatore che è stata introdotta in Visual Studio 2013 Update 3 aggiunge al file con estensione pdb (simbolo) informazioni aggiuntive per i file binari compilati senza il [/Od (disabilita (Debug)) ](http://msdn.microsoft.com/library/aafb762y.aspx) opzione.  
  
 **/Zo** Disabilita modifica e continuazione. Vedere [procedura: Debug di codice ottimizzato](../debugger/how-to-debug-optimized-code.md).  
  
##  <a name="BKMK_Enable_or_disable_automatic_invocation_of_Edit_and_Continue"></a> Abilitare o disabilitare Modifica e continuazione  
 È consigliabile disabilitare la chiamata automatica di Modifica e continuazione se si apportano modifiche al codice che non si vuole applicare durante la sessione di debug corrente. È anche possibile riabilitare la chiamata automatica di Modifica e continuazione.

> [!IMPORTANT]
> Per le impostazioni di compilazione necessari e altre informazioni sulla compatibilità di funzionalità, vedere [C++ Modifica e continuazione in Visual Studio 2015 Update 3] (https://blogs.msdn.microsoft.com/vcblog/2016/07/01/c-edit-and-continue-in-visual-studio-2015-update-3/.
  
1.  Se trovano in una sessione di debug, terminare il debug (**MAIUSC + F5**).

2. Scegliere **Opzioni** dal menu **Strumenti**.
  
3.  Nel **opzioni** nella finestra di dialogo **Debug > Generale**.

4.  Per abilitare, selezionare **Abilita modifica e continuazione**. Per disabilitare, deselezionare la casella di controllo.
  
5.  Nel gruppo **Modifica e continuazione** selezionare o deselezionare la casella di controllo **Abilita Modifica e continuazione nativo** .  
  
 La modifica di questa impostazione influisce su tutti i progetti attivi. Non è necessario ricompilare l'applicazione dopo la modifica di questa impostazione. Se si compila l'applicazione dalla riga di comando o da un makefile, ma si esegue il debug nell'ambiente di Visual Studio, è possibile comunque utilizzare Modifica e continuazione se si imposta la **/ZI** opzione.  
  
##  <a name="BKMK_How_to_apply_code_changes_explicitly"></a> Come applicare modifiche al codice in modo esplicito  
 In Visual C++, Modifica e continuazione consente di applicare modifiche al codice in due modi: in modo implicito, quando si sceglie un comando di esecuzione, o in modo esplicito, quando si usa il comando **Applica modifiche del codice** .  
  
 Quando si applicano le modifiche al codice in modo esplicito, il programma rimane in modalità di interruzione - non viene eseguito.  
  
-   Per applicare le modifiche al codice in modo esplicito, nel menu **Debug** scegliere **Applica modifiche del codice**.  
  
##  <a name="BKMK_How_to_stop_code_changes"></a> Come interrompere l'applicazione delle modifiche al codice  
 In Modifica e continuazione è possibile scegliere di interrompere l'applicazione delle modifiche al codice.  
  
 Per interrompere l'applicazione delle modifiche al codice:  
  
-   Nel menu **Debug** scegliere **Interrompi applicazione modifiche del codice**.  
  
 Questa voce di menu viene visualizzata solo durante l'applicazione delle modifiche al codice.  
  
 Se si sceglie questa opzione, non verrà completata nessuna delle modifiche del codice.  
  
##  <a name="BKMK_How_to_reset_the_point_of_execution"></a> Come reimpostare il punto di esecuzione  
 Alcune modifiche al codice applicate in modalità Modifica e continuazione possono causare uno spostamento automatico del punto di esecuzione in una nuova posizione. Nonostante il punto di esecuzione venga collocato nel modo più accurato possibile, in alcuni casi il risultato potrebbe non essere corretto.  
  
 In Visual C++ la modifica del punto di esecuzione viene segnalata tramite una finestra di dialogo. Si consiglia di verificare che la posizione sia corretta prima di continuare con il debug. In caso negativo, usare il comando **Imposta istruzione successiva** . Per altre informazioni, vedere [Impostare l'istruzione successiva da eseguire](http://msdn.microsoft.com/library/y740d9d3.aspx#BKMK_Set_the_next_statement_to_execute).  
  
##  <a name="BKMK_How_to_work_with_stale_code"></a> Come usare il codice non aggiornato  
 In alcuni casi la funzionalità Modifica e continuazione non consente di applicare immediatamente modifiche all'eseguibile, ma può apportare automaticamente tali modifiche in un secondo momento se si continua il debug. Ciò si verifica quando si modifica una funzione che chiama la funzione corrente o si aggiungono più di 64 byte di nuove variabili ad una funzione presente nello stack di chiamate.  
  
 In questi casi, il debugger continua a eseguire il codice originale, fino a quando non è possibile applicare le modifiche. Il codice non aggiornato è visualizzato in una finestra del file di origine temporanea di una finestra di origine distinta, caratterizzata da un titolo simile a `enc25.tmp`. L'origine modificata continua ad essere visualizzata nella finestra di origine originale. Se si tenta di modificare il codice non aggiornato, viene visualizzato un messaggio di avviso.  
  
## <a name="see-also"></a>Vedere anche  
 [Modifiche al codice supportate (C++)](../debugger/supported-code-changes-cpp.md)