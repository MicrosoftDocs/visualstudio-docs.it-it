---
title: Commenti dell'attività
description: ''
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: c119af47cc3b592033a68b0ec543afa86140c77a
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="task-comments"></a>Commenti dell'attività

Quando si scrive codice, è prassi standard commentare esplicitamente il codice incompleto o dubbio o le soluzioni rapide con avvisi. I token di segnalazione predefiniti forniti da Visual Studio per Mac sono TODO, HACK, FIXME e UNDONE. È possibile definire token personalizzati in **Visual Studio > Preferenze > Ambiente > Attività**, come illustrato nell'immagine seguente:

 ![Preferenze dell'elenco attività](media/source-editor-image10.png)

Quando si aggiunge un nuovo commento di attività, includere la parola chiave dell'attività. Ad esempio:

```
//TODO: Finish this for all properties.
```

Visual Studio per Mac attira l'attenzione su questi marcatori evidenziandoli nel riquadro Elenco attività, visualizzato spostandosi su **Visualizza > Riquadri > Attività**:

![Riquadro Elenco attività](media/source-editor-image11.png)