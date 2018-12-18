---
title: Errori dei criteri per l'analisi del codice
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- vs.codeanalysis.policyfailures
helpviewer_keywords:
- policy errors, code analysis
ms.assetid: d1f221cd-68c0-4277-9397-b76ad0dbae77
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 625b67972095728d1e9f5c0fd9fa9e5d8da60786
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="code-analysis-policy-errors"></a>Errori dei criteri per l'analisi del codice
Se i criteri di analisi codice non sono soddisfatti al momento dell'archiviazione, si verificano gli errori seguenti:

 **Le impostazioni di analisi del codice per uno o più progetti non sono compatibili con i criteri di analisi del codice.**

 I requisiti di analisi codice il controllo controllo del codice sorgente il progetto team non è stata soddisfatta per uno o più progetti di codice. Questo errore può essere causato da uno o più delle condizioni seguenti:

1.  Analisi del codice non è abilitato in fase di compilazione per tutti i progetti nella soluzione.

2.  La regola locale, imposta per il progetto in Visual Studio è meno restrittivo **azione** impostazione che la regola di progetto team, ad esempio, imposta una regola che è impostata su **azione**=**errore**  sul server è relativo **azione** impostato su **avviso** o **Nessuno** nella regola, imposta l'esecuzione in Visual Studio).

3.  Il set specificata in Visual Studio di regole non contiene tutte le regole che vengono specificate nella regola specificata nei criteri di controllo di analisi del codice per il progetto team.

 **I criteri di analisi codice non è riuscita. Sono presenti errori nel progetto {0} o la compilazione non è aggiornata.**

 La compilazione contiene errori o sono stati corretti gli errori, ma non è stata eseguita l'analisi del codice dopo la correzione.

 **Check-in non è riuscita. I criteri di analisi codice richiede l'archiviazione avvenga tramite Visual Studio con una soluzione aperta.**

 I criteri di analisi codice richiedono che tutti i file da archiviare devono essere nella soluzione attualmente aperta. Per correggere l'errore, aprire la soluzione che contiene il file da archiviare.

 **Non tutti i file di archiviazione è in sospeso sono all'interno della soluzione attualmente aperta.**

 I criteri di analisi codice richiedono che tutti i file da archiviare devono essere nella soluzione attualmente aperta. Questo errore viene generato quando è presente una soluzione aperta, ma alcuni file nella vista "archiviazione in sospeso" non fanno parte della soluzione attualmente aperta. Per correggere l'errore, aprire la soluzione che contiene il file da archiviare.

 **La versione di '{0}' non è corretta. Il nome sicuro specificato nei criteri è '\\{1 \\}'.**

 Questo errore si applica ai progetti .NET. Una DLL di regola richiesta dai criteri di analisi del codice presente nel computer locale, ma la versione/chiave pubblica non corrisponde. Per correggere l'errore, l'autore dei criteri è necessario aggiornare il file con estensione dll in *C:\Program Files\Microsoft Visual Studio 8 \ Team Tools\Static Analysis Tools\FxCop\Rules\\*  directory nel proprio computer.

 **assembly '{0}' specificati nei criteri non esiste.**

 Questo errore si applica ai progetti .NET. Una regola richiesta dai criteri di analisi del codice non dispone del file dll corrispondente installato nel computer client. Per correggere l'errore, l'autore dei criteri deve aggiornare la dll in *C:\Program Files\Microsoft Visual Studio 8 \ Team Tools\Static Analysis Tools\FxCop\Rules\\*  directory nel proprio computer.

 **Le impostazioni delle regole {0} progetto non sono in conformità con criteri di analisi codice.**

 Questo errore si applica ai progetti .NET. Le impostazioni delle regole di codice gestito non sono più rigorose di quanto richiesto dai criteri. Per correggere l'errore, l'impostazione del client deve essere uguale o più restrittivo rispetto dei requisiti dei criteri nel server.

 **Analisi del codice non è abilitata nella configurazione attiva. Passare alla configurazione {0} e compilare \\{1 \\} progetto prima dell'archiviazione.**

 In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], la configurazione attiva non dispone di analisi del codice attivata, ma non esiste almeno un'analisi del codice abilitata.

 **È necessario abilitare l'analisi del codice per i file binari gestiti nelle proprietà del progetto {0} e compilare prima dell'archiviazione.**

 Questo errore si applica a [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] applicazioni .NET. I criteri richiedono di eseguire l'analisi codice gestito, ma non è abilitato nel progetto corrente nel client.

 **È necessario abilitare l'analisi del codice nelle proprietà del progetto {0} e compilare prima dell'archiviazione.**

 Questo errore si applica a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] progetti e i progetti Web. I criteri richiedono di eseguire l'analisi codice gestito, ma non è abilitato nel progetto corrente nel client.

 **È necessario attivare l'analisi del codice C/C++ nelle proprietà del progetto {0} e compilare prima dell'archiviazione.**

 Questo errore si applica ai progetti non gestiti. I criteri di analisi codice richiedono l'analisi del codice per C/C++, ma non è abilitato nel progetto corrente nel client.

## <a name="see-also"></a>Vedere anche
 [Errori nell'applicazione dell'analisi del codice](../code-quality/code-analysis-application-errors.md)