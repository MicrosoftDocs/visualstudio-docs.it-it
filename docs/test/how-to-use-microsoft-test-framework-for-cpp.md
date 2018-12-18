---
title: Usare il framework di testing unità Microsoft per C++ in Visual Studio | Microsoft Docs
ms.date: 11/15/2017
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: mblome
manager: douge
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: a2d0998185a7b550b22d0cbfaad43477bb036ad7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="use-the-microsoft-unit-testing-framework-for-c-in-visual-studio"></a>Usare il framework di testing unità Microsoft per C++ in Visual Studio

Per impostazione predefinita il framework di testing unità Microsoft per C++ è incluso nel carico di lavoro **Sviluppo di applicazioni desktop con C++**.

##  <a name="separate_project"></a> Per scrivere unit test in un progetto separato
In genere, il codice di test viene eseguito nel relativo progetto nella stessa soluzione del codice da testare. Per impostare e configurare un nuovo progetto di test, vedere [Scrittura di unit test per C/C++](writing-unit-tests-for-c-cpp.md).

##  <a name="same_project"></a> Per scrivere unit test nello stesso progetto
In alcuni casi, ad esempio durante il test di funzioni non esportate in una DLL, potrebbe essere necessario creare i test nello stesso progetto del programma che si sta testando. Per scrivere unit test nello stesso progetto:

1.  Modificare le proprietà del progetto per includere le intestazioni e i file di libreria necessari per il testing unità.

    1.  In Esplora soluzioni fare clic con il pulsante destro del mouse sul nodo di progetto del programma che sta testando, quindi scegliere **Proprietà | Proprietà di configurazione | Directory di VC++**.

    3.  Fare clic sulla freccia GIÙ nelle righe seguenti e scegliere **<Edit>**:

        |||
        |-|-|
        |**Directory di inclusione**|**$(VCInstallDir)UnitTest\include;$(IncludePath)**|
        |**Directory delle librerie**|**$(VCInstallDir)UnitTest\lib;$(LibraryPath)**|

2.  Aggiungere un file di unit test C++:

    -   Fare clic con il pulsante destro del mouse sul nodo di progetto in **Esplora soluzioni** e scegliere **Aggiungi | Nuovo elemento | Unit test C++**.

## <a name="write-the-tests"></a>Scrivere i test
Tutti i file con estensione cpp con classi di test devono includere "CppUnitTest.h" e avere un'istruzione using per `using namespace Microsoft::VisualStudio::CppUnitTestFramework`. Il progetto di test è già configurato. Include anche una definizione dello spazio dei nomi e una TEST_CLASS con un TEST_METHOD per iniziare. È possibile modificare il nome dello spazio dei nomi e i nomi tra parentesi nelle macro della classe e del metodo.

Sono disponibili macro speciali per l'inizializzazione di moduli di test, classi e metodi e per la pulizia delle risorse al termine dei test. Queste macro generano codice che viene eseguito prima del primo accesso a una classe o un metodo e dopo l'esecuzione dell'ultimo test. Per altre informazioni, vedere [Initialize and cleanup](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#Initialize_and_cleanup) (Inizializzare ed eseguire la pulizia).

Usare i metodi statici nella classe [Assert](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#general_asserts) per definire le condizioni di test. Usare la classe [Logger](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md#logger) per scrivere messaggi nella **finestra di output**. Aggiungere attributi ai metodi di test

## <a name="run-the-tests"></a>Eseguire i test

1.  Nel menu **Test** scegliere **Finestre**, **Esplora test**.
2. Se non è visibile alcun test nella finestra, compilare il progetto di test facendo clic con il pulsante destro del mouse sul relativo nodo in **Esplora soluzioni** e scegliendo **Compila** o **Ricompila**.

2.  In Esplora test scegliere **Esegui tutto** o selezionare i test specifici da eseguire. Fare clic con il pulsante destro del mouse su un test per le altre opzioni, inclusa l'esecuzione in modalità di debug con i punti di interruzione abilitati.
3. Nel **finestra di output** scegliere **Test** nel menu a discesa per visualizzare i messaggi scritti dalla classe `Logger`:

  ![Finestra di output di C++ con messaggi di test](media/cpp-test-output-window.png "Finestra di output")

## <a name="define-traits-to-enable-grouping"></a>Definire i tratti per abilitare il raggruppamento
È possibile definire i tratti nei metodi di test che consentono di classificare e raggruppare i test in **Esplora test**. Per definire un tratto, usare la macro `TEST_METHOD_ATTRIBUTE`. Ad esempio, per definire un tratto denominato `TEST_MY_TRAIT`:

```cpp
#define TEST_MY_TRAIT(traitValue) TEST_METHOD_ATTRIBUTE(L"MyTrait", traitValue)
```

 Per usare il tratto definito negli unit test:

```
BEGIN_TEST_METHOD_ATTRIBUTE(Method1)
    TEST_OWNER(L"OwnerName")
    TEST_PRIORITY(1)
    TEST_MY_TRAIT(L"thisTraitValue")
END_TEST_METHOD_ATTRIBUTE()

TEST_METHOD(Method1)
{
    Logger::WriteMessage("In Method1");
    Assert::AreEqual(0, 0);
}
```

### <a name="c-trait-attribute-macros"></a>Macro di attributo di tratto C++
  I tratti predefiniti seguenti sono disponibili in `CppUnitTest.h`. Per altre informazioni, vedere [The Microsoft Unit Testing Framework for C++ API Reference](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md) (Informazioni di riferimento sulle API del framework di testing unità Microsoft per C++).

|Macro|Descrizione|
|-----------|-----------------|
|`TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)`|Usare la macro TEST_METHOD_ATTRIBUTE per definire un tratto.|
|`TEST_OWNER(ownerAlias)`|Usare il tratto Owner predefinito per specificare un proprietario del metodo di test.|
|`TEST_PRIORITY(priority)`|Usare il tratto Priority predefinito per assegnare priorità relative ai metodi di test.|


## <a name="see-also"></a>Vedere anche
[Guida introduttiva allo sviluppo basato su test con Esplora test](../test/quick-start-test-driven-development-with-test-explorer.md)

