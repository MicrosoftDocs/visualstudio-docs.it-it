---
title: Generare unit test per il codice con IntelliTest in Visual Studio | Microsoft Docs
ms.date: 2015-10-05
ms.technology: vs-ide-test
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.CreateIntelliTest
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 6a6929db0b5100ed57ba6d7c3113ede5b7431aa4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="generate-unit-tests-for-your-code-with-intellitest"></a>Generare unit test per il codice con IntelliTest
IntelliTest esplora il codice .NET per generare dati di test e un gruppo di unit test. Per ogni istruzione nel codice viene generato un input di test che eseguirà l'istruzione. Viene eseguita un'analisi del caso per ogni branch condizionale nel codice. Vengono ad esempio analizzate le istruzioni `if`, le asserzioni e tutte le operazioni che possono generare eccezioni. Questa analisi viene usata per generare dati di test per uno unit test con parametri per ognuno dei metodi, creando unit test con un elevato code coverage.

 Quando si esegue IntelliTest, è possibile visualizzare facilmente i test non superati e aggiungere l'eventuale codice necessario per correggerli. È possibile scegliere quali dei test generati salvare in un progetto di test per fornire un gruppo di regressione. Quando si modifica il codice, eseguire nuovamente IntelliTest per mantenere i test generati sincronizzati con le modifiche apportate al codice.

## <a name="availability-and-extensions"></a>Disponibilità ed estensioni

I comandi di menu **Crea IntelliTest** ed **Esegui IntelliTest**:

* Sono disponibili solo nell'Enterprise Edition di Visual Studio 2015 e versioni successive.

* Supportano solo il codice C# che fa riferimento a .NET Framework.

* Sono [estendibili](#extend-framework) e supportano l'emissione di test in formato MSTest, MSTest V2, NUnit, xUnit.

* Non supportano la configurazione x64.

## <a name="explore-use-intellitest-to-explore-your-code-and-generate-unit-tests"></a>Esplorare: usare IntelliTest per esplorare il codice e generare unit test
 Per generare unit test, i tipi devono essere pubblici. In caso contrario, [creare unit test](#NoRun) prima di generarli.

1.  Aprire la soluzione in Visual Studio. Aprire quindi il file di classe contenente i metodi da testare.

2.  Fare clic con il pulsante destro del mouse nel codice e scegliere **Esegui IntelliTest** per generare gli unit test per il codice nel metodo.

     ![Fare clic con il pulsante destro del mouse per generare unit test](../test/media/runpex.png "RunPEX")

     IntelliTest esegue il codice più volte con input diversi. Ogni esecuzione viene rappresentata nella tabella che mostra i dati di test di input e l'output o l'eccezione risultante.

     ![Viene visualizzata la finestra Risultati dell'esplorazione contenente i test](../test/media/pexexplorationresults.png "PEXExplorationResults")

     Per generare unit test per tutti i metodi pubblici di una classe, è sufficiente fare clic con il pulsante destro del mouse nella classe invece che in un metodo specifico. Quindi, scegliere **Esegui IntelliTest**. Usare l'elenco a discesa nella finestra Risultati esplorazione per visualizzare gli unit test e i dati di input per ogni metodo della classe.

     ![Selezionare i risultati del test per visualizzarli nell'elenco](../test/media/selectpextest.png "SelectPEXTest")

     Per i test che vengono superati verificare che i risultati indicati nella colonna dei risultati corrispondano a quanto previsto per il codice. Per i test che non vengono superati correggere il codice nel modo appropriato. Eseguire quindi di nuovo IntelliTest per verificare le correzioni.

## <a name="persist-save-the-unit-tests-as-a-regression-suite"></a>Rendere persistenti: salvare gli unit test come gruppo di regressione

1.  Selezionare le righe dei dati da salvare con lo unit test con parametri in un progetto di test.

     ![Selezionare i test, fare clic con il pulsante destro del mouse e scegliere Salva](../test/media/savepextests.png "SavePEXTests")

     È possibile visualizzare il progetto di test e lo unit test con parametri creato. I singoli unit test, corrispondenti alle singole righe, vengono salvati nel file con estensione g.cs nel progetto di test e uno unit test con parametri viene salvato nel file con estensione cs corrispondente. È possibile eseguire gli unit test e visualizzare i risultati da Esplora test come se si trattasse di unit test creati manualmente.

     ![Aprire il file di classe nel metodo di test per visualizzare unit test](../test/media/testmethodpex.png "TestMethodPEX")

     Al progetto di test vengono aggiunti anche gli eventuali riferimenti necessari.

     Se il codice del metodo viene modificato, eseguire di nuovo IntelliTest per mantenere gli unit test sincronizzati con le modifiche apportate.

## <a name="assist-use-intellitest-to-focus-code-exploration"></a>Fornire assistenza: usare IntelliTest per concentrarsi sull'esplorazione del codice

1.  In presenza di codice più complesso, IntelliTest consente di concentrarsi sull'esplorazione del codice. Se ad esempio si ha un metodo che contiene un'interfaccia come parametro ed è presente più di una classe che implementa tale interfaccia, IntelliTest trova tali classi e segnala un avviso.

     Visualizzare gli avvisi per decidere le azioni da intraprendere.

     ![Visualizzare gli avvisi](../test/media/pexviewwarning.png "PEXViewWarning")

2.  Dopo aver esaminato il codice e aver compreso le parti da testare, è possibile correggere l'avviso per consentire la scelta delle classi da usare per testare l'interfaccia.

     ![Fare clic con il pulsante destro del mouse sull'avviso e scegliere Correggi](../test/media/pexfixwarning.png "PEXFixWarning")

     La scelta viene quindi aggiunta nel file PexAssemblyInfo.cs.

     `[assembly: PexUseType(typeof(Camera))]`

3.  A questo punto è possibile eseguire di nuovo IntelliTest per generare uno unit test con parametri e dati di test usando solo la classe che è stata corretta.

     ![Riesecuzione di IntelliTest per generare i dati di test](../test/media/pexwarningsfixed.png "PEXWarningsFixed")

## <a name="specify-use-intellitest-to-validate-correctness-properties-that-you-specify-in-code"></a>Specificare: usare IntelliTest per convalidare le proprietà di correttezza specificate nel codice

Specificare la relazione generale tra input e output da verificare con gli unit test generati. Questa specifica viene incapsulata in un metodo simile a un metodo di test, ma universalmente quantificato. Si tratta del metodo di unit test con parametri e tutte le asserzioni effettuate devono essere mantenute per tutti i possibili valori di input che IntelliTest può generare.

##  <a name="QandALink"></a> Domande e risposte

### <a name="q-can-you-use-intellitest-for-unmanaged-code"></a>D: È possibile usare IntelliTest per il codice non gestito?

**R:** No, IntelliTest funziona solo con codice gestito.

### <a name="q-when-does-a-generated-test-pass-or-fail"></a>D: Quando un test generato viene considerato superato o non superato?

**R:** Viene considerato superato come qualsiasi altro unit test se non si verificano eccezioni. Viene invece considerato non superato in caso di errori dell'asserzione o se il codice analizzato genera un'eccezione non gestita.

 Se un test può essere considerato superato se vengono generate determinate eccezioni, è possibile impostare uno dei seguenti attributi in base ai requisiti a livello di metodo di test, classe di test o di assembly:

-   **PexAllowedExceptionAttribute**

-   **PexAllowedExceptionFromTypeAttribute**

-   **PexAllowedExceptionFromTypeUnderTestAttribute**

-   **PexAllowedExceptionFromAssemblyAttribute**

### <a name="q-can-i-add-assumptions-to-the-parameterized-unit-test"></a>D: È possibile aggiungere presupposti allo unit test con parametri?

**R:** Sì, usare i presupposti per specificare quali dati di test non sono obbligatori per lo unit test relativo a un metodo specifico. Per aggiungere presupposti, usare la classe <xref:Microsoft.Pex.Framework.PexAssume> . Ad esempio, è possibile aggiungere un presupposto per indicare che la variabile lengths è non Null come nell'esempio seguente.

 `PexAssume.IsNotNull(lengths);`

 Se si aggiunge un presupposto e si esegue di nuovo IntelliTest, i dati di test che non sono più rilevanti verranno rimossi.

### <a name="q-can-i-add-assertions-to-the-parameterized-unit-test"></a>D: È possibile aggiungere asserzioni allo unit test con parametri?

**R:** Sì, IntelliTest verificherà che quanto asserito nell'istruzione è di fatto corretto durante l'esecuzione degli unit test. Per aggiungere asserzioni, usare la classe <xref:Microsoft.Pex.Framework.PexAssert> o l'API di asserzione fornita con il framework di test. Ad esempio, è possibile aggiungere un'asserzione per indicare che due variabili sono uguali.

 `PexAssert.AreEqual(a, b);`

 Se si aggiunge un'asserzione e si esegue di nuovo IntelliTest, verrà verificata la validità dell'asserzione e il test verrà considerato non superato se l'asserzione non è valida.

###  <a name="NoRun"></a> D: È possibile generare unit test con parametri senza eseguire prima IntelliTest?

**R:** Sì, fare clic con il pulsante destro del mouse nella classe o nel metodo, quindi scegliere **Crea IntelliTest**.

 ![Fare clic con il pulsante destro del mouse sull'editor e scegliere Crea IntelliTest](../test/media/pexcreateintellitest.png "PEXCreateIntelliTest")

 Accettare il formato predefinito per generare i test o modificare la modalità di denominazione del progetto e dei test. È possibile creare un nuovo progetto di test o salvare i test in un progetto esistente.

 ![Creare IntelliTest nel formato MSTest predefinito](../test/media/pexcreateintellitestmstest.png "PEXCreateIntelliTestMSTest")

<a name="extend-framework"></a>
### <a name="q-can-i-use-other-unit-test-frameworks-with-intellitest"></a>D: È possibile usare altri framework di unit test con IntelliTest?

**R:** Sì, seguire questa procedura per [trovare e installare altri framework](../test/install-third-party-unit-test-frameworks.md).
Le estensioni del framework di test sono disponibili anche in Visual Studio Marketplace:

* [NUnit Extension for the Test Generators](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension) (Estensione NUnit per Test Generators)
* [xUnit Extension for the Test Generators](https://marketplace.visualstudio.com/items?itemName=BradWilson.xUnitnetTestExtensions) (Estensione xUnit per Test Generators)


Dopo aver riavviato Visual Studio e riaperto la soluzione, fare doppio clic nella classe o nel metodo, quindi scegliere **Crea IntelliTest**. Selezionare qui il framework installato:

![Selezionare altri framework unit test per IntelliTest](../test/media/pexcreateintellitestextensions.png "PEXCreateIntelliTestExtensions")

Eseguire quindi IntelliTest per generare i singoli unit test nei relativi file con estensione g.cs.


### <a name="q-can-i-learn-more-about-how-the-tests-are-generated"></a>D: È possibile reperire maggiori informazioni sulla modalità di generazione dei test?

**R:** Sì, per ottenere una panoramica dettagliata, leggere questo [post di blog](http://blogs.msdn.com/b/visualstudioalm/archive/2015/07/05/intellitest-one-test-to-rule-them-all.aspx).
