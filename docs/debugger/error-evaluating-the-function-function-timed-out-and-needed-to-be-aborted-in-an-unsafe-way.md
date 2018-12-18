---
title: 'Errore: Valutare la funzione &#39; function &#39; timeout e deve essere interrotto in modo non protetto | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vs.debug.error.unsafe_func_eval_abort
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ff5dedb9bf0ffe44ec1a7c031d4c1d0eeeea08ec
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="error-evaluating-the-function-39function39-timed-out-and-needed-to-be-aborted-in-an-unsafe-way"></a>Errore: Valutare la funzione &#39; function &#39; timeout e deve essere interrotto in modo non protetto

Testo del messaggio completo: la valutazione della funzione 'function' timeout e deve essere interrotto in modo non protetto. Questo potrebbe essere danneggiato il processo di destinazione. 

Per rendere più semplice controllare lo stato degli oggetti .NET, il debugger forzerà automaticamente di eseguire codice aggiuntivo (in genere i metodi di richiamo di proprietà e le funzioni di ToString) il processo sottoposto a debug. Nella maggior parte degli scenari di tutti, queste funzioni vengono completate rapidamente e semplificare il debug. Tuttavia, il debugger non eseguirla l'applicazione in un ambiente sandbox. Di conseguenza, un metodo Get della proprietà o metodo ToString che chiama una funzione nativa che si blocca può causare timeout lungo che potrebbe non essere ripristinabile. Se si verifica questo messaggio di errore, ciò è accaduto.
 
Uno dei motivi comune per questo problema è che quando il debugger valuta una proprietà, consente solo il thread in esame per l'esecuzione. Pertanto, se la proprietà è in attesa di esecuzione all'interno dell'applicazione in fase di debug di altri thread, e se è in attesa in modo che il Runtime .NET non è in grado di interrompere, si verifica questo problema.
 
## <a name="to-correct-this-error"></a>Per correggere l'errore
 
Esistono tre possibili soluzioni al problema.
 
### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>Soluzione &#1;: Impedire il debugger di chiamare la proprietà di getter o il metodo ToString
 
Il messaggio di errore indicherà il nome della funzione, che il debugger ha tentato di chiamare. Se è possibile modificare questa funzione, è possibile impedire al debugger di chiamare il metodo Get della proprietà o il metodo ToString. Provare una delle operazioni seguenti:
 
* Modificare il metodo a un altro tipo di codice, oltre a una metodo Get della proprietà o metodo ToString e il problema non verrà più visualizzato.
    oppure
* (Per ToString) Definire un attributo DebuggerDisplay sul tipo e consentire al debugger di restituire un valore diverso da ToString.
    oppure
* (Per un getter di proprietà) Inserire il `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]` attributo sulla proprietà. Può essere utile se si dispone di un metodo che debba rimanere una proprietà per motivi di compatibilità delle API, ma deve essere effettivamente un metodo.
 
### <a name="solution-2-have-the-target-code-ask-the-debugger-to-abort-the-evaluation"></a>Soluzione #2: Ha il codice di destinazione chiedere il debugger per interrompere la valutazione
 
Il messaggio di errore indicherà il nome della funzione, che il debugger ha tentato di chiamare. Se il metodo Get della proprietà o il metodo ToString a volte non viene eseguito correttamente, specialmente in situazioni in cui il problema è che un altro thread per eseguire il codice è necessario codice, quindi la funzione di implementazione può chiamare `System.Diagnostics.Debugger.NotifyOfCrossThreadDependency` chiedere il debugger per interrompere la funzione valutazione. Con questa soluzione, è comunque possibile valutare in modo esplicito queste funzioni, ma il comportamento predefinito prevede che l'esecuzione viene arrestata quando si verifica la chiamata di NotifyOfCrossThreadDependency.
 
### <a name="solution-3-disable-all-implicit-evaluation"></a>Soluzione #3: Disabilitare tutti valutazione implicita
 
Se le soluzioni precedenti non risolve il problema, passare a *strumenti* > *opzioni*e deselezionare l'impostazione *debug*  >   *Generale* > *Attiva valutazione delle proprietà e altre chiamate di funzioni implicite*. Questo disabiliterà la maggior parte delle valutazioni di funzioni implicite e dovrebbe risolvere il problema.



  
