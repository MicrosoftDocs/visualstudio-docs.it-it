---
title: Come usare Boost.Test per C++ in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 01/05/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bdf772be03f6021f499b9bf777922d6d2743e0dc
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="how-to-use-boosttest-for-c-in-visual-studio"></a>Come usare Boost.Test per C++ in Visual Studio

In **Visual Studio 2017 versione 15.5** e versioni successive l'adattatore di test Boost.Test è integrato nell'IDE di Visual Studio come componente del carico di lavoro **Sviluppo di applicazioni desktop con C++**.

![Adattatore di test per Boost.Test](media/cpp-boost-component.png "Adattatore per il componente Boost.Test")

Se il carico di lavoro **Sviluppo di applicazioni desktop con C++** non è installato, aprire il **programma di installazione di Visual Studio** e selezionare **Modifica**. Selezionare il carico di lavoro **Sviluppo di applicazioni desktop con C++**, quindi scegliere il pulsante **Modifica**.

## <a name="install-boost"></a>Installare Boost

Per usare Boost.Test è necessario installare [Boost](http://www.boost.org/). Se Boost non è stato installato, è consigliabile usare il sistema di gestione pacchetti Vcpkg.

1. Seguire le istruzioni in [vcpkg: gestione pacchetti per C++ per Windows](/cpp/vcpkg) per installare vcpkg, se non è già stato installato.

1. Installare la libreria statica o dinamica Boost.Test:

    - Eseguire `vcpkg install boost-test` per installare la libreria dinamica Boost.Test.
    
       OPPURE
       
    - Eseguire `vcpkg install boost-test:x86-windows-static` per installare la libreria statica Boost.Test.

1. Eseguire `vcpkg integrate install` per configurare Visual Studio con la libreria e includere i percorsi delle intestazioni e dei file binari di Boost.

## <a name="create-a-project-for-your-tests"></a>Creare un progetto per i test

> [!NOTE]
> In Visual Studio 2017 versione 15.5 non sono disponibili progetti di test preconfigurati o modelli di elementi per Boost.Test. Pertanto, è necessario creare un progetto di applicazione console per contenere i test. L'inserimento dei modelli di test per Boost.Test è previsto per le versioni future di Visual Studio.

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo della soluzione e scegliere **Aggiungi** > **Nuovo progetto**.

1. Nel riquadro sinistro scegliere **Visual C++** > **Desktop di Windows** e quindi scegliere il modello **Applicazione console di Windows**.

1. Specificare un nome per il progetto e scegliere **OK**.

## <a name="link-and-configuration-boost-static-library-only"></a>Collegamento e configurazione (solo libreria Boost statica)

Configurare il progetto per eseguire i test di Boost.Test.

1. Per modificare il file di progetto, per prima cosa scaricarlo. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Scarica progetto**. Quindi, fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Modifica <nome\>.vcxproj**.

1. Aggiungere due righe al gruppo di proprietà **Variabili globali** come illustrato di seguito:

    ```xml
    <PropertyGroup Label="Globals">
    ....
        <VcpkgTriplet>x86-windows-static</VcpkgTriplet>
        <VcpkgEnabled>true</VcpkgEnabled>
    </PropertyGroup>
    ```
1. Salvare e chiudere il file \*.vcxproj e quindi ricaricare il progetto.

1. Per aprire le **pagine delle proprietà**, fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Proprietà**.

1. Espandere **C/C++** > **Generazione di codice**, quindi selezionare **Libreria di Runtime**. Selezionare `/MTd` per la libreria di runtime statica di debug o `/MT` per la libreria di runtime statica di versione.

1. Espandere **Linker > Sistema**. Verificare che **SubSystem** sia impostato su **Console**.

1. Scegliere **OK** per chiudere le pagine delle proprietà.

## <a name="add-include-directives"></a>Aggiungere direttive include

1. Se è presente una funzione `main` nel file CPP del test, eliminarla.

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
È ora possibile scrivere ed eseguire i Boost Test. Per informazioni sulle macro dei test, vedere la [documentazione della libreria Boost Test](http://www.boost.org/doc/libs/1_38_0/libs/test/doc/html/index.html). Per informazioni sull'individuazione, l'esecuzione e il raggruppamento dei test usando **Esplora test**, vedere [Eseguire unit test con Esplora test](run-unit-tests-with-test-explorer.md).

## <a name="see-also"></a>Vedere anche
[Scrittura di unit test per C/C++](writing-unit-tests-for-c-cpp.md)
