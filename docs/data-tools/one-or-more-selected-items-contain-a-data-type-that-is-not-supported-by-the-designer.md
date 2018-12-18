---
title: "Uno o più elementi selezionati contengono un tipo di dati che non è supportato dalla finestra di progettazione | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 71dcd4f9-2946-42c5-9ce4-99c819ea2785
caps.latest.revision: "4"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 2a652cc1a48e851f0c13c1b50d4a145531b87147
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="one-or-more-selected-items-contain-a-data-type-that-is-not-supported-by-the-designer"></a>Uno o più elementi selezionati contengono un tipo di dati non supportato dalla finestra di progettazione
Uno o più elementi trascinati da **Esplora Server**/**Esplora Database** sul [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] contiene un tipo di dati che non è supportato dal [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] , ad esempio, [Tipi CLR definiti dall'utente](/dotnet/framework/data/adonet/sql/clr-user-defined-types).  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
1.  Creare una visualizzazione basata sulla tabella desiderata e che non includa il tipo di dati non supportato.  
  
2.  Trascinare la visualizzazione da **Esplora Server**/**Esplora Database** nella finestra di progettazione.  
  
## <a name="see-also"></a>Vedere anche
[Messaggi di Object Relational Designer](../data-tools/o-r-designer-messages.md)  
[Gli strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)