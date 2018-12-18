---
title: Uso di membri Microsoft.VisualStudio.TestTools.UnitTesting in unit test | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 3e0be7d788d4471f249b50f8c846343514b1c346
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="using-microsoftvisualstudiotesttoolsunittesting-members-in-unit-tests"></a>Uso di membri Microsoft.VisualStudio.TestTools.UnitTesting in unit test
Il framework di unit test supporta gli unit test in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Usare le classi e membri dello spazio dei nomi Microsoft.VisualStudio.TestPlatform.UnitTestFramework quando si esegue la codifica di unit test. È possibile usarli sia quando si scrive uno unit test da zero che per la modifica di uno unit test generato dal codice sottoposto a test.  
  
## <a name="groups-of-elements"></a>Gruppi di elementi  
 Per offrire una panoramica più accurata del framework di unit test, in questa sezione gli elementi dello spazio dei nomi UnitTesting vengono organizzati in gruppi di funzionalità correlate.  
  
> [!NOTE]
>  Gli elementi di attributo, i cui nomi terminano con la stringa Attribute, possono essere usati con o senza la stringa Attribute. I due esempi di codice seguenti presentano lo stesso funzionamento:  
>   
>  `[TestClass()]`  
>   
>  `[TestClassAttribute()]`  
  
### <a name="elements-used-for-data-driven-testing"></a>Elementi usati per i test basati sui dati  
 Usare gli elementi seguenti per configurare unit test basati sui dati. Per altre informazioni, vedere [Procedura: Creare uno unit test basato sui dati](../test/how-to-create-a-data-driven-unit-test.md) e [Procedura dettagliata: Uso di un file di configurazione per definire un'origine dati](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md).  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataAccessMethod  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataSourceAttribute 
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataSourceElement  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataSourceElementCollection  
  
## <a name="attributes-used-to-establish-a-calling-order"></a>Attributi usati per stabilire un ordine di chiamata

Un elemento di codice decorato con uno degli attributi seguenti viene chiamato nel momento specificato. Per altre informazioni, vedere [Anatomia di un unit test](http://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144).

### <a name="for-assemblies"></a>Per gli assembly  
 AssemblyInitialize e AssemblyCleanup vengono chiamati subito dopo il caricamento e subito prima dello scaricamento dell'assembly.  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssemblyInitializeAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssemblyCleanupAttribute  
  
### <a name="for-classes"></a>Per le classi  
 ClassInitialize e ClassCleanup vengono chiamati subito dopo il caricamento e subito prima dello scaricamento della classe.  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.ClassInitializeAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.ClassCleanupAttribute  
  
### <a name="for-test-methods"></a>Per i metodi di test  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestInitializeAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestCleanupAttribute  
  
## <a name="attributes-used-to-identify-test-classes-and-methods"></a>Attributi usati per identificare classi e metodi di test

Ogni classe di test deve avere l'attributo TestClass e ogni metodo di test deve avere l'attributo TestMethod. Per altre informazioni, vedere [Anatomia di un unit test](http://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144).
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestClassAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestMethodAttribute  
  
## <a name="assert-classes-and-related-exceptions"></a>Classi Assert ed eccezioni correlate  
 Gli unit test possono verificare il comportamento specifico dell'applicazione in base all'uso di vari tipi di istruzioni, eccezioni e attributi Assert. Per altre informazioni, vedere [Uso di classi Assert](../test/using-the-assert-classes.md).  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.Assert 
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.CollectionAssert  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.StringAssert  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssertFailedException  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssertInconclusiveException  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.UnitTestAssertException  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.ExpectedExceptionAttribute  
  
## <a name="the-testcontext-class"></a>Classe TestContext  
 I seguenti attributi e i valori ad essi assegnati sono visualizzati nella finestra Proprietà di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per un determinato metodo di test. Questi attributi non sono pensati per essere accessibili tramite il codice dello unit test. Influiscono invece sui modi in cui lo unit test viene usato o eseguito, dallo sviluppatore tramite l'IDE di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oppure dal motore di test di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Ad esempio, alcuni di questi attributi sono visualizzati come colonne nella finestra Gestione test e nella finestra Risultati del test, quindi è possibile usarli per raggruppare e ordinare i test e i risultati dei test. Uno di questi attributi è TestPropertyAttribute, che viene usato per aggiungere metadati arbitrari agli unit test. È ad esempio possibile usarlo per archiviare il nome del superamento di un test coperto da questo test, contrassegnando lo unit test con `[TestProperty("TestPass", "Accessibility")]`. In alternativa, è possibile usarlo per archiviare un indicatore del tipo di test: `[TestProperty("TestKind", "Localization")]`. La proprietà creata usando questo attributo e il valore di proprietà assegnato sono visualizzati nella finestra Proprietà di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], sotto l'intestazione **Specifico del test**.  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.OwnerAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DeploymentItemAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DescriptionAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.HostTypeAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.IgnoreAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.PriorityAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestPropertyAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.WorkItemAttribute  
  
## <a name="test-configuration-classes"></a>Classi di configurazione di test  
  
-   Microsoft.TeamFoundation.TestManagement.Client.ObjectTypes>  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestConfigurationSection  
  
## <a name="attributes-used-for-generating-reports"></a>Attributi usati per la generazione di report  
 Gli attributi in questa sezione correlano il metodo di test che decorano alle entità nella gerarchia del progetto di un progetto team di [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)].  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.CssIterationAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.CssProjectStructureAttribute  
  
## <a name="classes-used-with-private-accessors"></a>Classi usate con funzioni di accesso private

È possibile generare uno unit test per un metodo privato. Questa generazione crea una classe di funzioni di accesso private, che crea un'istanza di un oggetto della classe PrivateObject. La classe PrivateObject è una classe wrapper che usa la reflection come parte del processo della funzione di accesso privata. La classe PrivateType è simile, ma viene usata per chiamare metodi statici privati anziché metodi di istanza privata.

- Microsoft.VisualStudio.TestPlatform.UnitTestFramework.PrivateObject

- Microsoft.VisualStudio.TestPlatform.UnitTestFramework.PrivateType
