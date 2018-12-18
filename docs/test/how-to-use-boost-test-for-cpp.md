---
title: Come usare Boost.Test per C++ in Visual Studio | Microsoft Docs
ms.date: 01/29/2018
ms.technology: vs-ide-test
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 69cf4403e6a47d30df03e90f0d4ffa51bac2c9c2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-use-boosttest-for-c-in-visual-studio"></a>Come usare Boost.Test per C++ in Visual Studio

In **Visual Studio 2017 versione 15.5** e versioni successive l'adattatore di test Boost.Test è integrato nell'IDE di Visual Studio come componente del carico di lavoro **Sviluppo di applicazioni desktop con C++**.

![Adattatore di test per Boost.Test](media/cpp-boost-component.png "Adattatore per il componente Boost.Test")

Se il carico di lavoro **Sviluppo di applicazioni desktop con C++** non è installato, aprire il **programma di installazione di Visual Studio** e selezionare **Modifica**. Selezionare il carico di lavoro **Sviluppo di applicazioni desktop con C++**, quindi scegliere il pulsante **Modifica**.

## <a name="install-boost"></a>Installare Boost

Per usare Boost.Test è necessario installare [Boost](http://www.boost.org/). Se Boost non è stato installato, è consigliabile usare il sistema di gestione pacchetti Vcpkg.

1. Seguire le istruzioni in [vcpkg: gestione pacchetti per C++ per Windows](/cpp/vcpkg) per installare vcpkg, se non è già stato installato.

1. Installare la libreria statica o dinamica Boost.Test:

    - Eseguire **vcpkg install boost-test** per installare la libreria dinamica Boost.Test.

       OPPURE

    - Eseguire **vcpkg install boost-test:x86-windows-static** per installare la libreria statica Boost.Test.

1. Eseguire **vcpkg integrate install** per configurare Visual Studio con la libreria e includere i percorsi delle intestazioni e dei file binari di Boost.

## <a name="add-the-item-template-visual-studio-2017-version-156-and-later"></a>Aggiungere il modello di elemento (Visual Studio 2017 versione 15.6 e versioni successive)

1. Per creare un file con estensione cpp per i test, fare clic con il pulsante destro del mouse sul nodo di progetto in **Esplora soluzioni** e scegliere **Aggiungi nuovo elemento**.

   ![Modello di elemento Boost.Test](media/boost_test_item_template.png "Modello di elemento Boost.Test")

1. Il nuovo file contiene un metodo di test di esempio. Compilare il progetto per consentire a **Esplora test** di individuare il metodo.

Il modello di elemento usa la variante con singola intestazione di Boost.Test, ma è possibile modificare il percorso #include per usare la variante con libreria autonoma. Per altre informazioni vedere [Aggiungere direttive include](#add_include_directives).

## <a name="create-a-test-project-visual-studio-2017-version-155"></a>Creare un progetto di test (Visual Studio 2017 versione 15.5)

In Visual Studio 2017 versione 15.5 non sono disponibili progetti di test preconfigurati o modelli di elementi per Boost.Test. Pertanto, è necessario creare e configurare un progetto di applicazione console per contenere i test.

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo della soluzione e scegliere **Aggiungi** > **Nuovo progetto**.

1. Nel riquadro sinistro scegliere **Visual C++** > **Desktop di Windows** e quindi scegliere il modello **Applicazione console di Windows**.

1. Specificare un nome per il progetto e scegliere **OK**.
1. Eliminare la funzione `main` nel file con estensione cpp.

1. Se si usa la versione della libreria con singola intestazione o dinamica di Boost.Test, passare ad [Aggiungere direttive include](#add_include_directives). Se si usa la versione della libreria statica, è necessario eseguire un'ulteriore configurazione:

   a. Per modificare il file di progetto, per prima cosa scaricarlo. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Scarica progetto**. Quindi, fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Modifica <nome\>.vcxproj**.

   b. Aggiungere due righe al gruppo di proprietà **Variabili globali** come illustrato di seguito:

    ```xml
    <PropertyGroup Label="Globals">
    ....
        <VcpkgTriplet>x86-windows-static</VcpkgTriplet>
        <VcpkgEnabled>true</VcpkgEnabled>
    </PropertyGroup>
    ```
   c. Salvare e chiudere il file \*.vcxproj e quindi ricaricare il progetto.

   d. Per aprire le **pagine delle proprietà**, fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Proprietà**.

   d. Espandere **C/C++** > **Generazione di codice**, quindi selezionare **Libreria di Runtime**. Selezionare **/MTd** per la libreria di runtime statica di debug o **/MT** per la libreria di runtime statica di versione.

   f. Espandere **Linker > Sistema**. Verificare che **SubSystem** sia impostato su **Console**.

   g. Scegliere **OK** per chiudere le pagine delle proprietà.

## <a name="add-include-directives"></a>Aggiungere direttive include

1. Nel file con estensione cpp del test aggiungere le direttive `#include` necessarie per rendere visibili al codice di test i tipi e le funzioni del programma. Il programma si trova in genere al livello superiore della gerarchia di cartelle. Se si digita `#include "../"`, viene visualizzata una finestra di IntelliSense che consente di selezionare il percorso completo del file di intestazione.

   ![Aggiungere direttive #include](media/cpp-gtest-includes.png "Aggiungere direttive include al file con estensione cpp del test")

   È possibile usare la libreria autonoma con:

   ```cpp
   #include <boost/test/unit_test.hpp>
   ```

   In alternativa, usare la versione a una sola intestazione con:

   ```cpp
   #include <boost/test/included/unit_test.hpp>
   ```

   Quindi, definire `BOOST_TEST_MODULE`.

L'esempio seguente è sufficiente per rendere individuabile il test in **Esplora test**:

```cpp
#define BOOST_TEST_MODULE MyTest
#include <boost/test/included/unit_test.hpp\> //single-header
#include "../MyProgram/MyClass.h" // project being tested
#include <string>

BOOST_AUTO_TEST_CASE(my\_boost_test)
{
    std::string expected_value = "Bill";

    // assume MyClass is defined in MyClass.h
    // and get_value() has public accessibility
    MyClass mc;
    BOOST_CHECK(expected_value == mc.get_value());
}
```

## <a name="write-and-run-tests"></a>Scrivere ed eseguire i test
È ora possibile scrivere ed eseguire i Boost Test. Per informazioni sulle macro dei test, vedere la [documentazione della libreria Boost Test](http://www.boost.org/doc/libs/release/libs/test/doc/html/index.html). Per informazioni sull'individuazione, l'esecuzione e il raggruppamento dei test usando **Esplora test**, vedere [Eseguire unit test con Esplora test](run-unit-tests-with-test-explorer.md).

## <a name="see-also"></a>Vedere anche
[Scrittura di unit test per C/C++](writing-unit-tests-for-c-cpp.md)
