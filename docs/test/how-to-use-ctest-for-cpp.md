---
title: Come usare CTest per C++ in Visual Studio | Microsoft Docs
ms.date: 11/07/2017
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: mblome
manager: douge
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: 5956c605eb838721185598d4c5713c59164db071
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-use-ctest-for-c-in-visual-studio"></a>Come usare CTest per C++ in Visual Studio

CMake, che include CTest, è integrato nell'IDE di Visual Studio per impostazione predefinita come componente del carico di lavoro **Sviluppo di applicazioni desktop con C++**. Se è necessario installarlo nel computer, aprire il programma di installazione di Visual Studio, fare clic sul pulsante **Modifica**, quindi selezionare [CMake Tools per Visual C++](/cpp/ide/cmake-tools-for-visual-cpp) nell'elenco dei componenti del carico di lavoro.

## <a name="to-write-tests"></a>Per scrivere i test

Il supporto di CMake in Visual Studio non riguarda il sistema di progetti di Visual Studio. Di conseguenza, i test di CTest vengono scritti e configurati come in qualsiasi ambiente CMake. Per altre informazioni sull'uso di CMake in Visual Studio, vedere [CMake Tools for Visual C++](/cpp/ide/cmake-tools-for-visual-cpp) (Strumenti CMake per Visual C++).

## <a name="to-run-tests-visual-studio-2017-version-156"></a>Per eseguire i test (Visual Studio 2017 versione 15.6)

In Visual Studio 2017 versione 15.6, CTest è completamente integrato con **Esplora test** e supporta anche i framework di testing unità Google e Boost. Questi framework sono inclusi per impostazione predefinita come componenti del carico di lavoro **Sviluppo di applicazioni desktop con C+++**. Tuttavia, se si aggiorna un progetto da una versione precedente di Visual Studio, potrebbe essere necessario installare questi framework usando il programma di installazione di Visual Studio.

La figura seguente mostra i risultati di un'esecuzione di CTest con il framework Google Test:

![CTest con il framework Google Test in VS2017 15.6](media/ctest-test-explorer.png "CTest e Google Test in Esplora test")

Se si usa CTest ma non gli adattatori Google o Boost, i risultati vengono visualizzati a livello di CTest anziché a livello del singolo metodo di test. È possibile eseguire il debug ed eseguire istruzione per istruzione eseguibili solo CTest, ma non sono supportate analisi dello stack per singoli test.

## <a name="to-run-tests-visual-studio-2017-version-155"></a>Per eseguire i test (Visual Studio 2017 versione 15.5)

In **Visual Studio 2017 versione 15.5** CTest non è integrato con **Esplora test**. È possibile eseguire i test dal menu principale di CMake o dal menu di scelta rapida di un file **CMakeLists.txt** in **Esplora soluzioni**. I risultati del test vengono indirizzati alla **finestra di output** di Visual Studio.

![Eseguire test CTest in VS2017 15.5](media/cpp-cmake-run-tests.png "Eseguire test CTest in 15.5")

## <a name="see-also"></a>Vedere anche

[Scrittura di unit test per C/C++](writing-unit-tests-for-c-cpp.md)