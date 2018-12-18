---
title: Strutture Visual C++ in Progettazione classi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: d0621b5a2a82786a41e8d566954f03341affa905
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="visual-c-structures-in-class-designer"></a>Strutture Visual C++ in Progettazione classi
Progettazione classi supporta le strutture C++, che vengono dichiarate con la parola chiave `struct`, come nell'esempio seguente:  
  
```cpp
struct MyStructure  
{  
   char a;  
   int i;  
   long j;  
};  
```  
  
Per altre informazioni sull'uso del tipo `struct`, vedere [struct](/cpp/cpp/struct-cpp).  
  
Una forma struttura C++ in un diagramma classi è simile per aspetto e funzionamento a una forma classe, ad eccezione del fatto che l'etichetta della forma struttura è **Struct** ed è contraddistinta da angoli squadrati anziché arrotondati.  
  
|Elemento del codice|Visualizzazione di Progettazione classi|  
|------------------|-------------------------|  
|`struct StructureName {};`|**NomeStruttura**<br /><br /> Struct|  
  
## <a name="see-also"></a>Vedere anche
[Uso del codice di Visual C++](working-with-visual-cpp-code.md)   
[Classi e struct](/cpp/cpp/classes-and-structs-cpp)   
[struct](/cpp/cpp/struct-cpp)