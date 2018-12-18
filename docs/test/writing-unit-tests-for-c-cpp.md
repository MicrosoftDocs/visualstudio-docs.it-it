---
title: Scrivere unit test per C/C++ in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
author: mikeblome
ms.openlocfilehash: d926e28dc918900715090d32f929b6b7ff5cb482
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="write-unit-tests-for-cc-in-visual-studio"></a>Scrivere unit test per C/C++ in Visual Studio
È possibile scrivere ed eseguire gli unit test C++ usando la finestra **Esplora test**, come per altri linguaggi. Per altre informazioni sull'uso di **Esplora test**, vedere [Eseguire unit test con Esplora test](run-unit-tests-with-test-explorer.md). 

> [!NOTE]
> Alcune funzionalità, ad esempio Live Unit Testing, i test codificati dell'interfaccia utente e IntelliTest, non sono supportate per C++. 

Visual Studio include questi framework di test C++ senza richiedere download aggiuntivi:
 -  Framework di testing unità Microsoft per C++  
 -  Google Test
 -  Boost.Test
 -  CTest

Oltre ai framework installati, è possibile scrivere adattatori di test personalizzati per qualsiasi framework che si desidera usare all'interno di Visual Studio. Un adattatore di test consente di integrare unit test nella finestra **Esplora test**. Sono disponibili vari adattatori di terze parti in [Visual Studio Marketplace](https://marketplace.visualstudio.com). Per altre informazioni, vedere [Installare framework di unit test di terze parti](install-third-party-unit-test-frameworks.md).

**Visual Studio 2017 versione 15.5**  

1) L'**adattatore per Google Test** è incluso come componente predefinito del carico di lavoro **Sviluppo di applicazioni desktop con C++**. Questo adattatore include un modello di progetto che è possibile aggiungere a una soluzione tramite il menu di scelta rapida **Aggiungi nuovo progetto** nel nodo della soluzione in **Esplora soluzioni** e le opzioni possono essere configurate tramite **Strumenti | Opzioni**. Per altre informazioni, vedere [How to use Google Test for C++ in Visual Studio](how-to-use-google-test-for-cpp.md) (Come usare Google Test per C++ in Visual Studio).

2) **Boost.Test** è incluso come componente predefinito del carico di lavoro **Sviluppo di applicazioni desktop con C++**. È integrato in **Esplora test** ma attualmente non include un modello di progetto, pertanto è necessario configurarlo manualmente. Per altre informazioni, vedere [How to use Boost.Test for C++ in Visual Studio](how-to-use-boost-test-for-cpp.md) (Come usare Boost.Test per C++ in Visual Studio). 

3) Il supporto per **CTest** è incluso nel componente [CMake Tools for Visual Studio](/cpp/ide/cmake-tools-for-cpp) che fa parte del carico di lavoro **Sviluppo di applicazioni desktop con C++**. Tuttavia, CTest non è ancora completamente integrato con **Esplora test**. Per altre informazioni, vedere [How to: use CTest in Visual Studio](how-to-use-ctest-for-cpp.md) (Come usare CTest in Visual Studio).


**Visual Studio 2015 e versioni precedenti**
  
È possibile scaricare le estensioni degli adattatori per Google Test e Boost.Test Adapter in Visual Studio Marketplace nelle pagine [Test Adapter for Boost.Test](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforBoostTest) e [Test Adapter for Google Test](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforGoogleTest). 

  
## <a name="basic-test-workflow"></a>Flusso di lavoro di test di base
Le sezioni seguenti illustrano i passaggi di base per iniziare con il testing unità in C++. La configurazione di base è molto simile per i framework di Microsoft e Google Test. Per Boost.Test è necessario creare manualmente un progetto di test. 
  
### <a name="create-a-test-project"></a>Creare un progetto di test
I test vengono definiti ed eseguiti all'interno di uno o più progetti di test inclusi nella stessa soluzione del codice da testare. Per aggiungere un nuovo progetto di test a una soluzione esistente, fare clic con il pulsante destro del mouse sul nodo della soluzione in **Esplora soluzioni** e scegliere **Aggiungi | Nuovo progetto**. Nel riquadro sinistro scegliere **Progetto di test Visual C++** e scegliere uno dei tipi di progetto nel riquadro centrale. La figura seguente mostra i progetti di test disponibili quando è installato il carico di lavoro **Sviluppo di applicazioni desktop con C++**:

![Progetti di test C++](media/cpp-new-test-project.png "Nuovi modelli di progetti di test C++")

### <a name="create-references-to-other-projects-in-the-solution"></a>Creare riferimenti ad altri progetti nella soluzione
Per abilitare il codice di test per l'accesso alle funzioni nel progetto da testare, aggiungere un riferimento al progetto nel progetto di test. Fare clic con il pulsante destro del mouse sul nodo del progetto in **Esplora soluzioni** e scegliere **Aggiungi | Riferimento**. Nella finestra di dialogo scegliere quindi i progetti da testare.

![Aggiungi riferimento](media/cpp-add-ref-test-project.png "Test C++, aggiungere un riferimento ai progetti da testare")

### <a name="add-include-directives-for-header-files"></a>Aggiungere direttive #include per il file di intestazione
Nel file cpp dell'unit test aggiungere quindi una direttiva `#include` per tutti i file di intestazione che dichiarano i tipi e le funzioni da testare. Digitare `#include "`. Verrà attivato Intellisense per facilitare la scelta. Ripetere per eventuali intestazioni aggiuntive.

![Aggiungere le direttive include](media/cpp-add-includes-test-project.png "Test C++, aggiungere le direttive include per i file di intestazione")

### <a name="write-test-methods"></a>Scrivere i metodi di test
> [!NOTE] 
> Questa sezione mostra la sintassi per il framework di testing unità Microsoft per C/C++. La documentazione è disponibile in [Informazioni di riferimento sulle API di Microsoft.VisualStudio.TestTools.CppUnitTestFramework](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). Per la documentazione di Google Test, vedere [Google Test Primer](https://github.com/google/googletest/blob/master/googletest/docs/Primer.md) (Introduzione a Google Test). Per Boost.Test, vedere [Boost Test Library: The Unit Test Framework](http://www.boost.org/doc/libs/1_46_0/libs/test/doc/html/utf.html) (Libreria di test Boost: il framework di unit test).

Il file con estensione cpp nel progetto di test include una classe stub e un metodo definiti come esempio per la scrittura del codice di test. Si noti che le firme usano le macro TEST_CLASS e TEST_METHOD, che rendono individuabili i metodi dalla finestra Esplora test.

![Aggiungere le direttive include](media/cpp-write-test-methods.png "Test C++, aggiungere le direttive include per i file di intestazione")

TEST_CLASS e TEST_METHOD fanno parte del [framework di test nativo Microsoft]((microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). **Esplora test** consente di individuare i metodi di test in altri framework supportati in modo analogo.

TEST_METHOD restituisce void. Per produrre un risultato di test, usare i metodi statici nella classe `Assert` per testare i risultati effettivi rispetto a quanto previsto. Nell'esempio seguente si presuppone che `MyClass` includa un costruttore che accetta `std::string`. È possibile verificare che il costruttore inizializzi la classe come previsto in questo modo:

```cpp
        TEST_METHOD(TestClassInit)
        {
            std::string name = "Bill";
            MyClass mc(name);
            Assert::AreEqual(name, mc.GetName());
        }
```
Nell'esempio precedente, il risultato della chiamata `Assert::AreEqual` determina l'esito positivo o negativo del test. La classe Assert contiene molti altri metodi per il confronto dei risultati previsti con quelli effettivi. 

È possibile aggiungere *tratti* ai metodi di test per specificare il proprietario, la priorità e altre informazioni per i test. È quindi possibile usare questi valori per ordinare e raggruppare i test in **Esplora test**. Per altre informazioni, vedere [Eseguire unit test con Esplora test](run-unit-tests-with-test-explorer.md).


### <a name="run-the-tests"></a>Eseguire i test  
  
1.  Nel menu **Test** scegliere **Finestre**, **Esplora test**. La figura seguente illustra un progetto di test con test non ancora eseguiti. 

![Esplora test prima dell'esecuzione dei test](media/cpp-test-explorer.png "Esplora test C++")

> [!NOTE]
> L'integrazione di CTest con **Esplora test** non è ancora disponibile. Eseguire test CTest dal menu principale di CMake.

2. Se non è visibile alcun test nella finestra, compilare il progetto di test facendo clic con il pulsante destro del mouse sul relativo nodo in **Esplora soluzioni** e scegliendo **Compila** o **Ricompila**.
  
3.  In Esplora test scegliere **Esegui tutto** o selezionare i test specifici da eseguire. Fare clic con il pulsante destro del mouse su un test per le altre opzioni, inclusa l'esecuzione in modalità di debug con i punti di interruzione abilitati. Dopo aver eseguito tutti i test, la finestra mostra i test superati e quelli non superati:

![Esplora test dopo l'esecuzione dei test](media/cpp-test-explorer-passed.png "Esplora test C++ dopo l'esecuzione dei test")

Per i test non superati, il messaggio include dettagli utili per diagnosticare la causa. È possibile fare clic con il pulsante destro del mouse sul test non superato e scegliere **Esegui debug test selezionati** per esaminare la funzione in cui si è verificato l'errore. 

Per altre informazioni sull'uso di **Esplora test**, vedere [Eseguire unit test con Esplora test](run-unit-tests-with-test-explorer.md).

Per le procedure consigliate correlate al testing unità, vedere [Nozioni fondamentali sugli unit test](unit-test-basics.md).

## <a name="see-also"></a>Vedere anche
[Eseguire unit test del codice](unit-test-your-code.md)

