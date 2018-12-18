---
title: Visualizzazione dei tipi e delle relazioni (Progettazione classi) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.classdesigner.CannotShowBaseType
helpviewer_keywords:
- class diagrams
- types [Visual Studio], visualizing
- relationships, class diagrams
- types [Visual Studio], class diagrams
- relationships, visualizing
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: e9ca80f3a3feb9655d53c6ee292f84c7c567d166
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2018
---
# <a name="viewing-types-and-relationships-class-designer"></a>Visualizzazione dei tipi e delle relazioni (Progettazione classi)

Progettazione classi usa i diagrammi classi per visualizzare i dettagli dei tipi, ad esempio i membri che li costituiscono e le relazioni che condividono. La visualizzazione di queste entità è effettivamente una visualizzazione dinamica nel codice. Ciò significa che è possibile modificare i tipi nella finestra di progettazione e quindi visualizzare le modifiche riflesse nel codice sorgente dell'entità. Analogamente, il diagramma classi viene mantenuto sincronizzato con le modifiche apportate alle entità nel codice.

> [!NOTE]
> Se il progetto contiene un diagramma classi e fa riferimento a un tipo che si trova in un altro progetto, il diagramma classi non visualizza il tipo di riferimento fino a quando non si compila il progetto per quel tipo. Allo stesso modo, il diagramma non visualizza le modifiche apportate al codice dell'entità esterna fino a quando non si ricompila il progetto per l'entità.

## <a name="see-also"></a>Vedere anche

[Progettazione di classi e tipi](designing-classes-and-types.md)  
[Refactoring di classi e tipi](refactoring-classes-and-types.md)  
[Procedura: Personalizzare i diagrammi classi](how-to-customize-class-diagrams.md)  
[Uso di diagrammi classi](working-with-class-diagrams.md)