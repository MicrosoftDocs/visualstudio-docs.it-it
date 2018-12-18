---
title: Strutture Visual C++ in Progettazione classi | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d6f2aa3893a230abd52dd5cf19ed9d751e56e50c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
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