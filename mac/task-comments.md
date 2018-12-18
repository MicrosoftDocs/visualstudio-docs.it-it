---
title: "Commenti dell'attività"
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: 973e7b627a7b5c121ff388874577fe59c45529d7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="task-comments"></a>Commenti dell'attività

Quando si scrive codice, è prassi standard commentare esplicitamente il codice incompleto o dubbio o le soluzioni rapide con avvisi. I token di segnale predefiniti offerti da Visual Studio per Mac sono TODO, HACK, FIXME e UNDONE, anche se è possibile definire token personalizzati in **Visual Studio > Preferenze... > Ambiente > Attività**, come illustrato di seguito:

 ![Preferenze dell'elenco attività](media/source-editor-image10.png)

Quando si aggiunge un nuovo commento di attività, includere la parola chiave dell'attività. Ad esempio:

```
//TODO: Finish this for all properties.
```

Visual Studio per Mac attira l'attenzione su questi marcatori evidenziandoli nel riquadro Elenco attività, visualizzato spostandosi su **Visualizza > Riquadri > Attività**:

![Riquadro Elenco attività](media/source-editor-image11.png)