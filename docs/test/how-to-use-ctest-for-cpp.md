---
title: Come usare CTest per C++ in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/07/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
author: mikeblome
ms.openlocfilehash: 529e070a3db1e6587989f8d0c55dc04e6db0388c
ms.sourcegitcommit: 49aa031cbebdd9c7ec070c713afb1a97d1ecb701
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2018
---
# <a name="how-to-use-ctest-for-c-in-visual-studio"></a>Come usare CTest per C++ in Visual Studio
CMake, che include CTest, è integrato nell'IDE di Visual Studio come componente del carico di lavoro **Sviluppo di applicazioni desktop con C++**. Per installarlo nel computer, aprire il programma di installazione di Visual Studio e trovare [CMake Tools per Visual C++](/cpp/ide/cmake-tools-for-visual-cpp) (Strumenti CMake per Visual C++) nell'elenco dei componenti del carico di lavoro.

Il supporto di CMake in Visual Studio non riguarda il sistema di progetti di Visual Studio. Di conseguenza, i test di CTest vengono scritti e configurati come in qualsiasi ambiente CMake. Per altre informazioni sull'uso di CMake in Visual Studio, vedere [CMake Tools for Visual C++](/cpp/ide/cmake-tools-for-visual-cpp) (Strumenti CMake per Visual C++).

**Visual Studio 2017 versione 15.5** CTest non è attualmente integrato con **Esplora test**. È possibile eseguire i test dal menu principale di CMake o dal menu di scelta rapida di un file **CMakeLists.txt** in **Esplora soluzioni**. I risultati del test vengono indirizzati alla **finestra di output** di Visual Studio.

![Eseguire test CTest](media/cpp-cmake-run-tests.png "Eseguire test CTest")

## <a name="see-also"></a>Vedere anche
[Scrittura di unit test per C/C++](writing-unit-tests-for-c-cpp.md)