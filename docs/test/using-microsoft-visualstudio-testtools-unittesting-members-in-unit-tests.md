---
title: Uso di membri Microsoft.VisualStudio.TestTools.UnitTesting in unit test | Microsoft Docs
ms.date: 03/02/2018
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 593a07af6ef25389a541f66383077b8a373d86eb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="use-the-mstest-framework-in-unit-tests"></a>Usare il framework MSTest negli unit test

Il framework [MSTest](<xref:Microsoft.VisualStudio.TestTools.UnitTesting>) supporta unit test in Visual Studio. Usare le classi e membri nello spazio dei nomi <xref:Microsoft.VisualStudio.TestTools.UnitTesting> durante la codifica di unit test. È possibile usarli anche durante la messa a punto di uno unit test generato dal codice.

## <a name="framework-members"></a>Membri del framework

Per offrire una panoramica più accurata del framework di testing unità, in questa sezione i membri dello spazio dei nomi <xref:Microsoft.VisualStudio.TestTools.UnitTesting> vengono organizzati in gruppi di funzionalità correlate.

> [!NOTE]
> Gli elementi attributo, i cui nomi terminano con "Attribute", possono essere usati con o senza "Attribute" alla fine. I due esempi di codice seguenti presentano lo stesso funzionamento:
>
> `[TestClass()]`
>
> `[TestClassAttribute()]`

### <a name="members-used-for-data-driven-testing"></a>Membri usati per i test basati sui dati

Usare gli elementi seguenti per configurare unit test basati sui dati. Per altre informazioni, vedere [Creare uno unit test basato sui dati](../test/how-to-create-a-data-driven-unit-test.md) e [Usare un file di configurazione per definire un'origine dati](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataAccessMethod>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElement>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElementCollection>

## <a name="attributes-used-to-establish-a-calling-order"></a>Attributi usati per stabilire un ordine di chiamata

Un elemento di codice decorato con uno degli attributi seguenti viene chiamato nel momento specificato. Per altre informazioni, vedere [Anatomia di un unit test](http://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144).

### <a name="attributes-for-assemblies"></a>Attributi per gli assembly

AssemblyInitialize e AssemblyCleanup vengono chiamati subito dopo il caricamento e subito prima dello scaricamento dell'assembly.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyCleanupAttribute>

### <a name="attributes-for-classes"></a>Attributi per classi

ClassInitialize e ClassCleanup vengono chiamati subito dopo il caricamento e subito prima dello scaricamento della classe.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassCleanupAttribute>

### <a name="attributes-for-test-methods"></a>Attributi per i metodi di test

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>

## <a name="attributes-used-to-identify-test-classes-and-methods"></a>Attributi usati per identificare classi e metodi di test

Ogni classe di test deve avere l'attributo `TestClass` e ogni metodo di test deve avere l'attributo `TestMethod`. Per altre informazioni, vedere [Anatomia di un unit test](http://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>

## <a name="assert-classes-and-related-exceptions"></a>Classi Assert ed eccezioni correlate

Gli unit test possono verificare il comportamento specifico dell'applicazione in base all'uso di vari tipi di asserzioni, eccezioni e attributi. Per altre informazioni, vedere [Uso di classi Assert](../test/using-the-assert-classes.md).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute>

## <a name="the-testcontext-class"></a>Classe TestContext

I seguenti attributi e i valori ad essi assegnati sono visualizzati nella finestra Proprietà di Visual Studio per un determinato metodo di test. Questi attributi non sono pensati per essere accessibili tramite il codice dello unit test. Influiscono invece sui modi in cui viene usato o eseguito lo unit test, ovvero manualmente tramite l'IDE di Visual Studio o dal motore di test di Visual Studio. Ad esempio, alcuni di questi attributi sono visualizzati come colonne nella finestra **Gestione test** e nella finestra **Risultati del test**, quindi è possibile usarli per raggruppare e ordinare i test e i risultati dei test. Uno di questi attributi è <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>, che viene usato per aggiungere metadati arbitrari agli unit test. È ad esempio possibile usarlo per archiviare il nome del superamento di un test coperto da questo test, contrassegnando lo unit test con `[TestProperty("TestPass", "Accessibility")]`. In alternativa, è possibile usarlo per archiviare un indicatore del tipo di test con `[TestProperty("TestKind", "Localization")]`. La proprietà creata usando questo attributo e il valore di proprietà assegnato vengono entrambi visualizzati nella finestra **Proprietà** di Visual Studio, sotto l'intestazione **Specifico del test**.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DeploymentItemAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DescriptionAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.IgnoreAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.WorkItemAttribute>

## <a name="test-configuration-classes"></a>Classi di configurazione di test

- <xref:Microsoft.TeamFoundation.TestManagement.Client.ObjectTypes>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection>

## <a name="attributes-used-to-generate-reports"></a>Attributi usati per generare report

Gli attributi in questa sezione correlano il metodo di test che decorano alle entità nella gerarchia del progetto di un progetto team di Team Foundation Server.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssIterationAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssProjectStructureAttribute>

## <a name="classes-used-with-private-accessors"></a>Classi usate con funzioni di accesso private

È possibile generare uno unit test per un metodo privato. Questa generazione crea una classe di funzione di accesso privata, che crea un'istanza di un oggetto della classe <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject>. La classe <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject> è una classe wrapper che usa la reflection come parte del processo della funzione di accesso privata. La classe <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateType> è simile, ma viene usata per chiamare metodi statici privati anziché metodi di istanza privata.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateType>

## <a name="see-also"></a>Vedere anche

- Documentazione di riferimento per <xref:Microsoft.VisualStudio.TestTools.UnitTesting>
