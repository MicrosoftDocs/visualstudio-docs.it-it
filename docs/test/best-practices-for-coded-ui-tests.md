---
title: Procedure consigliate per i test codificati dell'interfaccia utente | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- coded UI tests, best practices
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 8a77c9c31cc12a802360a64499f730335762a508
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="best-practices-for-coded-ui-tests"></a>Procedure consigliate per i test codificati dell'interfaccia utente

Questo argomento descrive le procedure consigliate da seguire quando si sviluppano i test codificati dell'interfaccia utente.

**Requisiti**  

- Visual Studio Enterprise

## <a name="best-practices"></a>Suggerimenti

Usare le linee guida seguenti per creare un test codificato dell'interfaccia utente flessibile.
  
-   Quando è possibile, usare sempre il **Generatore di test codificati dell'interfaccia utente**.  
  
-   Non modificare direttamente il file `UIMap.designer.cs`. Così facendo, le modifiche apportate al file verrebbero sovrascritte.  
  
-   Creare il test come sequenza di metodi registrati. Per altre informazioni sulla registrazione di un metodo, vedere [Creazione di test codificati dell'interfaccia utente](../test/use-ui-automation-to-test-your-code.md).
  
-   Ogni metodo registrato dovrebbe agire su una sola pagina, form o finestra di dialogo. Creare un nuovo metodo di test per ogni nuova pagina, form o finestra di dialogo.  
  
-   Quando si crea un metodo, usare un nome di metodo significativo invece del nome predefinito. Un nome significativo consente di identificare lo scopo del metodo.  
  
-   Quando è possibile, limitare ogni metodo registrato a meno di 10 azioni. Questo approccio modulare semplifica la sostituzione di un metodo se viene modificata l'interfaccia utente.  
  
-   Creare ogni asserzione usando il **Generatore di test codificati dell'interfaccia utente**, che aggiunge automaticamente un metodo di asserzione al file `UIMap.Designer.cs`.  
  
-   Se l'interfaccia utente viene modificata, registrare nuovamente i metodi di test o i metodi di asserzione oppure registrare nuovamente le sezioni interessate di un metodo di test esistente.  
  
-   Creare un file <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> separato per ogni modulo nell'applicazione sottoposta a test. Per altre informazioni, vedere [Test di un'applicazione di grandi dimensioni con più mappe dell'interfaccia utente](../test/testing-a-large-application-with-multiple-ui-maps.md).  
  
-   Nell'applicazione sottoposta a test usare nomi significativi quando si creano controlli dell'interfaccia utente. In questo modo i nomi dei controlli generati automaticamente risulteranno più significativi e facilmente utilizzabili.  
  
-   Se si stanno creando asserzioni scrivendo codice con l'API, creare un metodo per ogni asserzione nella parte della classe <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> presente nel file `UIMap.cs`. Chiamare questo metodo dal metodo di test per eseguire l'asserzione.  
  
-   Se si sta scrivendo codice direttamente con l'API, usare il più possibile nel codice le proprietà e i metodi nelle classi generate nel file `UIMap.Designer.cs`. Queste classi renderanno il lavoro più semplice e più affidabile e consentiranno di aumentare la produttività.  
  
 I test codificati dell'interfaccia utente si adattano automaticamente a diverse modifiche nell'interfaccia utente. Se, ad esempio, un elemento dell'interfaccia utente ha cambiato posizione o colore, nella maggior parte dei casi il test codificato dell'interfaccia utente troverà ugualmente l'elemento corretto.  
  
 Durante l'esecuzione dei test, i controlli dell'interfaccia utente vengono individuati dal framework di test usando un set di proprietà di ricerca che vengono applicate a ogni classe di controlli nelle definizioni create dal **Generatore di test codificati dell'interfaccia utente** nel file `UIMap.Designer.cs`. Le proprietà di ricerca contengono coppie nome-valore di nomi di proprietà e valori di proprietà che possono essere usate per identificare il controllo, ad esempio le proprietà <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.FriendlyName%2A>, <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.Name%2A> e <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.ControlType%2A> del controllo. Se le proprietà di ricerca rimangono invariate, il test codificato dell'interfaccia utente riuscirà a trovare il controllo nell'interfaccia utente. Se le proprietà di ricerca vengono modificate, i test codificati dell'interfaccia utente hanno un algoritmo di correlazione automatica che applica l'euristica per trovare controlli e finestre nell'interfaccia utente. Quando l'interfaccia utente viene modificata, è possibile modificare le proprietà di ricerca di elementi identificati in precedenza per assicurarsi che vengano trovati.  

## <a name="if-your-user-interface-changes"></a>Se l'interfaccia utente cambia

Le interfacce utente vengono modificate spesso durante lo sviluppo. Di seguito sono indicati alcuni modi per ridurre l'effetto di queste modifiche:  
  
-   Trovare il metodo registrato che fa riferimento a questo controllo e usare il **Generatore di test codificati dell'interfaccia utente** per registrare di nuovo le azioni per questo metodo. È possibile usare lo stesso nome per il metodo per sovrascrivere le azioni esistenti.  
  
-   Se un controllo dispone di un'asserzione che non è più valida:  
  
    -   Eliminare il metodo che contiene l'asserzione.  
  
    -   Rimuovere la chiamata a questo metodo dal metodo di test.  
  
    -   Aggiungere una nuova asserzione trascinando il pulsante del selettore di precisione sul controllo dell'interfaccia utente, aprire la mappa dell'interfaccia utente e aggiungere la nuova asserzione.  
  
 Per altre informazioni su come registrare i test codificati dell'interfaccia utente, vedere [Usare l'automazione dell'interfaccia utente per testare il codice](../test/use-ui-automation-to-test-your-code.md).  
  
## <a name="if-a-background-process-needs-to-complete-before-the-test-can-continue"></a>Se è necessario completare un processo in background prima che il test possa continuare

Potrebbe essere necessario attendere fino al termine di un processo prima di poter procedere con la successiva azione dell'interfaccia utente. A tale scopo, è possibile usare <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.WaitForReadyLevel%2A> per attendere la continuazione del test, come nell'esempio seguente.  

```csharp
// Set the playback to wait for all threads to finish  
Playback.PlaybackSettings.WaitForReadyLevel = WaitForReadyLevel.AllThreads;  
  
// Press the submit button  
this.UIMap.ClickSubmit();  
  
// Reset the playback to wait only for the UI thread to finish  
Playback.PlaybackSettings.WaitForReadyLevel = WaitForReadyLevel.UIThreadOnly;  
```

## <a name="see-also"></a>Vedere anche

<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>   
<xref:Microsoft.VisualStudio.TestTools.UITesting>   
[Usare l'automazione dell'interfaccia utente per testare il codice](../test/use-ui-automation-to-test-your-code.md)   
[Creazione di test codificati dell'interfaccia utente](../test/use-ui-automation-to-test-your-code.md)   
[Test di un'applicazione di grandi dimensioni con più mappe dell'interfaccia utente](../test/testing-a-large-application-with-multiple-ui-maps.md)   
[Configurazioni e piattaforme supportate per i test codificati dell'interfaccia utente e le registrazioni delle azioni](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
