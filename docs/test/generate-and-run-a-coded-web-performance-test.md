---
title: Test codificati delle prestazioni Web in Visual Studio | Microsoft Docs
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, walkthroughs
- Web performance tests, creating
- code, Web performance tests
- Web performance tests, coded
ms.assetid: 169e48f9-52fd-4d0b-83d9-54913bde506b
dev_langs:
- CSharp
- VB
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: aa6f1e07bffc59030865018610c4367489d4ba9a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="generate-and-run-a-coded-web-performance-test"></a>Generare ed eseguire un test delle prestazioni Web codificato

I test delle prestazioni Web vengono registrati tramite l'esplorazione dell'app Web. I test vengono inclusi nei test di carico per misurare le prestazioni dell'applicazione Web quando viene usata da molteplici utenti. Un test delle prestazioni Web può essere convertito in uno script basato su codice che è possibile modificare e personalizzare come qualsiasi altro codice sorgente. Ad esempio, è possibile aggiungere costrutti di ciclo e di branching.

## <a name="generate-a-coded-web-performance-test"></a>Generare un test prestazioni Web codificato

1.  Se non è stato creato un test delle prestazioni Web, vedere [Registrare un test delle prestazioni Web](/vsts/load-test/run-performance-tests-app-before-release#create-a-web-performance-and-load-test-project).

2.  Generare il test codificato.

     ![Generare un test prestazioni Web codificato](../test/media/web_test_coded_generate.png)

3.  Denominare il test.

     ![Immettere un nome per il test prestazioni Web codificato](../test/media/web_test_coded_generate_nametest.png)

     Il nuovo test codificato verrà aperto nell'editor di codice.

     Il codice viene generato in Visual Basic o Visual C#, a seconda del modello di progetto di test di prestazioni Web e di test di carico aggiunto alla soluzione.

     ![Il nuovo test codificato viene aperto nell'editor del codice](../test/media/web_test_coded_generate_opencodeeditor.png)

     È possibile vedere nel codice che il metodo GetRequestEnumerator() in C# o il metodo Run() in Visual Basic contiene ogni regola di convalida e ogni richiesta Web presente nel test ricodificato.

4.  Per dimostrare l'aggiunta di codice semplice, scorrere alla fine del metodo e, dopo il codice relativo all'ultima richiesta Web, aggiungere il seguente codice:

    ```c#
    if (DateTime.Today.DayOfWeek == DayOfWeek.Wednesday)
    {
        WebTestRequest customRequest = new WebTestRequest("http://weather.msn.com/");
        yield return customRequest;
    }
    else
    {
        WebTestRequest customRequest = new WebTestRequest("http://msdn.microsoft.com/");
        yield return customRequest;
    }
    ```

    ```vb
    If DateTime.Today.DayOfWeek = DayOfWeek.Wednesday Then
        Dim customRequest As WebTestRequest = New WebTestRequest("http://weather.msn.com/")
        MyBase.Send(customRequest)
    Else
        Dim customRequest As WebTestRequest = New WebTestRequest("http://msdn.microsoft.com/")
        MyBase.Send(customRequest)
    End If
    ```

5.  Compilare la soluzione per verificare che il codice personalizzato venga compilato.

6.  Eseguire il test.

     ![Eseguire il test codificato delle prestazioni Web](../test/media/web_test_coded_generate_run.png "Web_Test_Coded_Generate_Run")

     E poiché il giorno in cui è stato eseguito era un mercoledì...

     ![Risultati del test codificato delle prestazioni Web](../test/media/web_test_coded_generate_results.png "Web_Test_Coded_Generate_Results")

## <a name="qa"></a>Domande e risposte

### <a name="q-can-i-run-more-than-one-test-at-a-time"></a>D: È possibile eseguire più test contemporaneamente?
 **R:** Sì, usare il menu di scelta rapida in Esplora soluzioni.

### <a name="q-should-i-add-a-data-source-before-or-after-i-generate-a-coded-test"></a>D: È necessario aggiungere un'origine dati prima o dopo avere generato un test codificato?
 **R:** È più semplice aggiungere un'[origine dati](../test/add-a-data-source-to-a-web-performance-test.md) prima di generare il test codificato perché il codice verrà generato automaticamente.

 Quando si esegue un test codificato con un 'origine dati, può venire visualizzato il messaggio di errore seguente:

 **Impossibile eseguire il test \<Nome test> sull'agente \<Nome computer>: Riferimento oggetto non impostato su un'istanza di un oggetto.**

 Questo errore può verificarsi perché per la classe di test è definito un oggetto DataSourceAttribute senza un oggetto DataBindingAttribute corrispondente. Per risolvere questo errore, aggiungere un oggetto DataBindingAttribute appropriato, eliminarlo oppure impostarlo come commento nel codice.

### <a name="q-should-i-add-validation-and-extraction-rules-before-or-after-i-generate-a-coded-test"></a>D: È necessario aggiungere regole di convalida e di estrazione prima o dopo avere generato un test codificato?
 **R:** È più semplice aggiungere regole di convalida e regole di estrazione prima di generare il test codificato. È tuttavia consigliabile usare [test codificati dell'interfaccia utente](../test/use-ui-automation-to-test-your-code.md) ai fini della convalida.