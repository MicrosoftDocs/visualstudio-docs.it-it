---
title: Uno o più elementi selezionati contengono un tipo di dati che non è supportato dalla finestra di progettazione | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 71dcd4f9-2946-42c5-9ce4-99c819ea2785
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 35b45a407b5c07bc5c6ab6db87e972b3787890ad
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58969993"
---
# <a name="one-or-more-selected-items-contain-a-data-type-that-is-not-supported-by-the-designer"></a>Uno o più elementi selezionati contengono un tipo di dati non supportato dalla finestra di progettazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Uno o più elementi trascinati da **Esplora Server**/**Database Explorer** nel [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] contiene un tipo di dati che non è supportato dal [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] (ad esempio, [Tipi CLR definiti dall'utente](http://msdn.microsoft.com/library/9f70e0b0-3a0d-4eb1-b914-07a5d0c167c2)).  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
1.  Creare una visualizzazione basata sulla tabella desiderata e che non includa il tipo di dati non supportato.  
  
2.  Trascinare la visualizzazione dal **Esplora Server**/**Esplora Database** nella finestra di progettazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Procedura dettagliata: Creazione di classi LINQ to SQL (O-R Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
