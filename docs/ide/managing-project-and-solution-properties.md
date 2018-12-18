---
title: "Gestione delle proprietà di progetti e soluzioni | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5315dd07ab0c791cc9a349c08431ceb4a9b5c797
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="managing-project-and-solution-properties"></a>Gestione delle proprietà di progetti e soluzioni

Le proprietà dei progetti governano molti aspetti della compilazione, del debug, del test e della distribuzione. Alcune proprietà sono comuni tra tutti i tipi di progetto e altre sono univoche di piattaforme o linguaggi specifici. Per accedere alle proprietà del progetto, fare clic con il pulsante destro del mouse sul nodo del progetto in Esplora soluzioni e scegliere **Proprietà** oppure digitare "proprietà" nella casella di ricerca **Avvio veloce** nella barra dei menu.

![Menu di scelta rapida Progetto](../ide/media/vs2015_proj_prop_menu.gif "vs2015_proj_prop_menu")

I progetti .NET potrebbero anche avere un nodo di proprietà nell'albero del progetto.

![Nodo Proprietà nell'albero Esplora soluzioni](../ide/media/vs2015_props_se.png "VS2015_Props_SE")

## <a name="project-properties"></a>Proprietà di progetti

Le proprietà del progetto sono organizzate in gruppi e ogni gruppo ha una propria pagina delle proprietà. Le pagine possono essere diverse a seconda del linguaggio e del tipo di progetto.

### <a name="c-visual-basic-and-f-projects"></a>Progetti C#, Visual Basic e F#

Nei progetti C#, Visual Basic e F# le proprietà sono esposte in **Progettazione progetti**. La figura seguente mostra la pagina della proprietà di compilazione per un progetto WPF in C#:

![Progettazione progetti di Visual Studio](../ide/media/vs2015_proppage_build.png "VS2015_PropPage_Build")

Per informazioni su ognuna delle pagine delle proprietà in Progettazione progetti, vedere [Riferimenti alle proprietà di progetto](../ide/reference/project-properties-reference.md).

> [!TIP]
> Le soluzioni, così come gli elementi del progetto, hanno alcune proprietà, che sono accessibili nella [Finestra Proprietà](../ide/reference/properties-window.md), non in **Progettazione progetti**.

### <a name="c-and-javascript-projects"></a>Progetti C++ e JavaScript

I progetti C++ e JavaScript hanno un'interfaccia utente differente per la gestione delle proprietà del progetto. Questa illustrazione mostra la pagina delle proprietà di un progetto C++ (le pagine JavaScript sono simili):

![Proprietà di progetto Visual C&#43;&#43;](../ide/media/vs2015_projprops_cpp.png "VS2015_ProjProps_cpp")

Per informazioni sulle proprietà di progetto C++, vedere [Utilizzo di proprietà di progetto (C++)](/cpp/ide/working-with-project-properties). Per altre informazioni sulle proprietà JavaScript, vedere [Pagine proprietà, JavaScript](../ide/reference/property-pages-javascript.md).

## <a name="solution-properties"></a>Proprietà della soluzione

Per accedere alle proprietà della soluzione, fare clic con il pulsante destro del mouse sul nodo della soluzione in **Esplora soluzioni** e scegliere **Proprietà**. Nella finestra di dialogo è possibile impostare le configurazioni di progetto per le compilazioni di debug o di rilascio, scegliere i progetti che devono essere il progetto di avvio quando viene premuto F5 e impostare le opzioni di analisi del codice.

## <a name="see-also"></a>Vedere anche

[Soluzioni e progetti in Visual Studio](../ide/solutions-and-projects-in-visual-studio.md)
