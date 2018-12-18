---
title: "Impossibile eliminare la classe selezionata perché è utilizzato come tipo restituito per uno o più metodi DataContext | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 78107218af8c4b32e1cace3137fa15fe31fcbc52
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>Impossibile eliminare la classe selezionata perché è utilizzata come tipo restituito per uno o più metodi DataContext
Il tipo restituito di uno o più metodi <xref:System.Data.Linq.DataContext> rappresenta la classe di entità selezionata. L'eliminazione di una classe di entità usata come tipo restituito di un metodo <xref:System.Data.Linq.DataContext> determinerà l'esito negativo della compilazione del progetto. Per eliminare la classe di entità selezionata, identificare i metodi <xref:System.Data.Linq.DataContext> che l'usano e impostare i relativi tipi restituiti su una classe di entità diversa.  
  
 Per ripristinare i tipi restituiti di <xref:System.Data.Linq.DataContext> metodi tipi generati automaticamente originali, eliminare prima il <xref:System.Data.Linq.DataContext> metodo dal riquadro dei metodi e quindi trascinare l'oggetto da **Esplora Server** / **Esplora database** in Progettazione relazionale nuovamente.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
1.  Identificare <xref:System.Data.Linq.DataContext> metodi che usano la classe di entità come tipo restituito selezionando un <xref:System.Data.Linq.DataContext> metodo nei metodi riquadro e controllando il **Return Type** proprietà il **proprietà** finestra .  
  
2.  Impostare il **Return Type** su una classe di entità diversa oppure eliminare il <xref:System.Data.Linq.DataContext> metodo dal riquadro dei metodi.  
  
## <a name="see-also"></a>Vedere anche
[Messaggi di Object Relational Designer](../data-tools/o-r-designer-messages.md)  
[Gli strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)