---
title: Impostare i test codificati dell'interfaccia utente per l'attesa di eventi specifici in Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5c288958ba2864c9db962b050ad3139dbb4f7ccf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="making-coded-ui-tests-wait-for-specific-events-during-playback"></a>Impostazione dei test codificati dell'interfaccia utente per l'attesa di eventi specifici durante la riproduzione

Nella riproduzione di un test codificato dell'interfaccia utente è possibile fare in modo che il test attenda che si verifichino determinati eventi, ad esempio che venga visualizzata finestra, venga nascosto l'indicatore di stato e così via. A tale scopo, usare il metodo UITestControl.WaitForControlXXX() appropriato, come descritto nella tabella seguente. Per un esempio di test codificato dell'interfaccia utente in cui si attende che un controllo venga abilitato usando il metodo <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlEnabled%2A>, vedere [Procedura dettagliata: creazione, modifica e gestione di un test codificato dell'interfaccia utente](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md).

 **Requisiti**

 Visual Studio Enterprise

> [!TIP]
>  È inoltre possibile aggiungere ritardi prima delle azioni usando l'Editor di test codificati dell'interfaccia utente. Per altre informazioni, vedere [Procedura: Inserire un ritardo prima di un'azione dell'interfaccia utente usando l'editor di test codificati dell'interfaccia utente](http://msdn.microsoft.com/Library/509f8ef7-e105-4049-b11b-d64549e055b0).

 **Metodi UITestControl.WaitForControlXXX()**

 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlReady%2A>

 Attende che il controllo sia pronto ad accettare l'input di tastiera e mouse. Il motore chiama in modo implicito questa API per tutte le azioni, in modo da attendere che il controllo sia pronto prima di eseguire qualsiasi operazione. Tuttavia, in scenari particolari, potrebbe essere necessaria una chiamata esplicita.

 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlEnabled%2A>

 Attende che il controllo venga abilitato quando la procedura guidata esegue una convalida asincrona dell'input effettuando chiamate al server. Ad esempio, è possibile fare in modo che un metodo attenda che il pulsante **Next** della procedura guidata venga abilitato (). Per un esempio di questo metodo, vedere [Procedura dettagliata: Creazione, modifica e gestione di un test codificato dell'interfaccia utente](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md).

 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlExist%2A>

 Attende che il controllo venga visualizzato nell'interfaccia utente. Ad esempio, è prevista una finestra di dialogo di errore dopo che l'applicazione ha eseguito la convalida dei parametri. Il tempo impiegato per la convalida è variabile. È possibile usare questo metodo per attendere la finestra di dialogo di errore.

 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlNotExist%2A>

 Attende che il controllo venga rimosso dall'interfaccia utente. Ad esempio, è possibile attendere che l'indicatore di stato venga rimosso.

 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlPropertyEqual%2A>

 Attende che alla proprietà specificata del controllo venga assegnato il valore indicato. Ad esempio, si attende che il testo dello stato diventi **Done**.

 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlPropertyNotEqual%2A>

 Attende che alla proprietà specificata del controllo venga assegnato il valore contrario a quello specificato. Ad esempio, si attende che la casella di modifica sia non di sola lettura, ovvero sia modificabile.

 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlCondition%2A>

 Attende che il predicato specificato restituisca `true`. Può essere usato per un'operazione di attesa complessa (ad esempio, una condizione OR) su un determinato controllo. Ad esempio, è possibile attendere finché il testo dello stato non diventa **Succeeded** o **Failed**, come mostrato nel codice seguente:

```csharp

// Define the method to evaluate the condition
private static bool IsStatusDone(UITestControl control)
{
    WinText statusText = control as WinText;
    return statusText.DisplayText == "Succeeded" || statusText.DisplayText == "Failed";
}

// In test method, wait till the method evaluates to true
statusText.WaitForControlCondition(IsStatusDone);

```

 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForCondition%2A>

 Tutti i metodi precedenti sono metodi di istanza di UITestControl. Questo metodo è un metodo statico Questo metodo attende inoltre che il predicato specificato sia `true`, ma può essere usato per un'operazione di attesa complessa (ad esempio, una condizione OR) su più controlli. Ad esempio, è possibile attendere finché il testo dello stato non è **Succeeded** o finché non viene visualizzato un messaggio di errore, come mostrato nel codice seguente:

```csharp

// Define the method to evaluate the condition
private static bool IsStatusDoneOrError(UITestControl[] controls)
{
    WinText statusText = controls[0] as WinText;
    WinWindow errorDialog = controls[1] as WinWindow;
    return statusText.DisplayText == "Succeeded" || errorDialog.Exists;
}

// In test method, wait till the method evaluates to true
UITestControl.WaitForCondition<UITestControl[]>(new UITestControl[] { statusText, errorDialog }, IsStatusDoneOrError);

```

 Tutti questi metodi presentano il seguente comportamento:

 I metodi restituiscono true se l'attesa ha esito positivo e false se l'attesa non è riuscita.

 Il timeout implicito per l'operazione di attesa viene specificato dalla proprietà <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.WaitForReadyTimeout%2A>. Il valore predefinito di questa proprietà è 60000 millisecondi (un minuto).

 I metodi hanno un overload per accettare il timeout esplicito in millisecondi. Tuttavia, quando l'operazione di attesa restituisce una ricerca implicita del controllo o quando l'applicazione è occupata, il tempo di attesa effettivo potrebbe essere superiore al timeout specificato.

 Le funzioni precedenti sono avanzate e flessibili e dovrebbero soddisfare quasi tutte le condizioni. Tuttavia, nel caso in cui questi metodi non soddisfino le proprie esigenze e sia necessario inserire <xref:Microsoft.VisualStudio.TestTools.UITesting.Playback.Wait%2A> o <xref:System.Threading.Thread.Sleep%2A> nel codice, è consigliabile usare l'API Playback.Wait() invece di Thread.Sleep() per questi motivi:

 È possibile usare la proprietà <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.ThinkTimeMultiplier%2A> per modificare la durata della sospensione. Per impostazione predefinita, questa variabile è 1, ma è possibile aumentarla o diminuirla per modificare il tempo di attesa in tutto il codice. Ad esempio, se si sta eseguendo un test su una rete lenta o si sta verificando un altro caso di prestazioni ridotte, è possibile impostare questa variabile in una posizione (o anche nel file di configurazione) su 1,5 per aggiungere il 50% in più di attesa in tutte le posizioni.

 Playback.Wait() chiama internamente Thread.Sleep() (dopo il calcolo precedente) in blocchi più piccoli in un ciclo for-loop mentre cerca l'operazione di annullamento/interruzione dell'utente. In altre parole, Playback.Wait() consente di annullare la riproduzione prima della fine dell'attesa, mentre la sospensione potrebbe non generare un'eccezione.

> [!TIP]
> L'Editor di test codificati dell'interfaccia utente consente di modificare facilmente i test. Con l'Editor di test codificati dell'interfaccia utente è possibile individuare, visualizzare e modificare i metodi di test. È anche possibile modificare le azioni dell'interfaccia utente e i relativi controlli associati nella mappa di controllo dell'interfaccia utente. Per altre informazioni, vedere [Modifica di test codificati dell'interfaccia utente usando l'Editor di test codificati dell'interfaccia utente](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

## <a name="see-also"></a>Vedere anche

- [Usare l'automazione dell'interfaccia utente per testare il codice](../test/use-ui-automation-to-test-your-code.md)
- [Creazione di test codificati dell'interfaccia utente](../test/use-ui-automation-to-test-your-code.md)
- [Procedura dettagliata: Creazione, modifica e gestione di un test codificato dell'interfaccia utente](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
- [Composizione di un test codificato dell'interfaccia utente](../test/anatomy-of-a-coded-ui-test.md)
- [Configurazioni e piattaforme supportate per i test codificati dell'interfaccia utente e le registrazioni delle azioni](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
- [Procedura: Inserire un ritardo prima di un'azione dell'interfaccia utente usando l'editor di test codificati dell'interfaccia utente](http://msdn.microsoft.com/Library/509f8ef7-e105-4049-b11b-d64549e055b0)
