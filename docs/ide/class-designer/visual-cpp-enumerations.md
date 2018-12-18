---
title: Enumerazioni Visual C++ in Progettazione classi | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ad55c68e16fcd340d69178dc24a4b92cada9e2f3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="visual-c-enumerations-in-class-designer"></a>Enumerazioni Visual C++ in Progettazione classi
Progettazione classi supporta C++ `enum` e i tipi `enum class` con ambito. Di seguito è riportato un esempio:  
  
```cpp
enum CardSuit {  
   Diamonds = 1,  
   Hearts = 2,  
   Clubs = 3,  
   Spades = 4  
};  
  
// or...  
enum class CardSuit {  
   Diamonds = 1,  
   Hearts = 2,  
   Clubs = 3,  
   Spades = 4  
};
```  
  
Una forma di enumerazione C++ in un diagramma classi viene visualizzata e funziona come una forma di struttura, tranne per il fatto che l'etichetta **Enum** o **Enum class** è di colore rosa anziché blu e ha un bordo colorato sui margini sinistro e superiore. Entrambe le forme di enumerazione e struttura hanno angoli quadrati.  
  
Per altre informazioni sull'uso del tipo `enum`, vedere [Enumerazioni](/cpp/cpp/enumerations-cpp).  
  
## <a name="see-also"></a>Vedere anche
[Uso del codice di Visual C++](working-with-visual-cpp-code.md)   
[Enumerazioni](/cpp/cpp/enumerations-cpp)