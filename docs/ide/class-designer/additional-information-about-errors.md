---
title: Informazioni aggiuntive sugli errori di Progettazione classi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.CPlusPlusViewInDiagramNoTypeFound
- vs.classdesigner.CPlusPlusNoTypeFound
- vs.classdesigner.CannotShowBaseType
- vs.classdesigner.MatchOrphanTypesAtLoad
- vs.classdesigner.CannotShowType
- vs.classdesigner.AssociationTypeNotFoundError
- vs.classdesigner.ViewInDiagramNoTypesFound
- vs.classdesigner.CannotImplementInterface
- vs.classdesigner.CannotShowImplementedInterface
- vs.classdesigner.ViewInDiagramUnparsableTypeFound
- vs.classdesigner.AssociationTypeNotFound
- vs.classdesigner.CPlusPlusTypeCannotBeAdded
helpviewer_keywords:
- errors, class diagrams
- errors, Class Designer
- error messages, Class Designer
- Class Designer [Visual Studio], errors
- error messages, class diagrams
- class diagrams, errors
ms.assetid: 79d70e70-704c-4255-ab68-c10d6949470e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8cd6223786db06506c1fa4ac9b6bd3118eb5e3d7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="additional-information-about-class-designer-errors"></a>Informazioni aggiuntive sugli errori di Progettazione classi
Progettazione classi non tiene traccia del percorso dei file di origine. Di conseguenza, se si modifica la struttura del progetto o si spostano i file di origine in un progetto, Progettazione classi può perdere traccia del tipo, soprattutto del tipo di origine di un typedef, delle classi di base o dei tipi di associazione. Si potrebbe ricevere un errore, ad esempio **Progettazione classi: impossibile visualizzare il tipo**. In tal caso, trascinare di nuovo il codice sorgente modificato o riposizionato nel diagramma classi per visualizzarlo nuovamente.  
  
Nelle risorse seguenti è possibile trovare assistenza per altri errori e avvisi:  
  
[Uso del codice di Visual C++](working-with-visual-cpp-code.md)  
Include informazioni sulla risoluzione dei problemi relativi alla visualizzazione di C++ in un diagramma classi.  
  
[Forum su Progettazione classi di Visual Studio](http://go.microsoft.com/fwlink/?LinkId=160754)  
Forum dedicato a domande su Progettazione classi.  
  
## <a name="see-also"></a>Vedere anche
[Progettazione e visualizzazione di classi e tipi](designing-and-viewing-classes-and-types.md)