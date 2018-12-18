---
title: "Passaggio 9: Provare altre funzionalità | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b0c5c80-e5a6-4f69-a4a4-0e89a82d4de0
caps.latest.revision: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 198ce949913dc7d35052e50c4bd13a559e8336e5
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2018
---
# <a name="step-9-try-other-features"></a>Passaggio 9: provare altre funzionalità
Per acquisire maggiore dimestichezza, provare a modificare icone e colori oppure aggiungere un timer di gioco o suoni. Per rendere più impegnativo il gioco, provare a ingrandire la lavagna e a regolare il timer.  
  
 Per scaricare una versione completa dell'esempio, vedere [Complete Matching Game tutorial sample](http://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba) (Esempio di esercitazione: un gioco delle coppie completo).  
  
### <a name="to-try-other-features"></a>Per provare altre funzionalità  
  
-   Sostituire le icone e i colori con altri a piacere.  
  
    > [!TIP]
    >  Osservare la proprietà [ForeColor](http://msdn.microsoft.com/library/system.windows.forms.control.forecolor.aspx) dell'etichetta.  
  
-   Aggiungere un timer di gioco per tenere traccia del tempo necessario a un giocatore per vincere.  
  
    > [!TIP]
    >  A tale scopo, è possibile aggiungere un'etichetta per visualizzare il tempo trascorso nel form al di sopra di TableLayoutPanel e aggiungerne un'altra nel form per tenere traccia del tempo. Utilizzare il codice per avviare il timer quando il giocatore inizia la partita e interromperlo dopo che avrà accoppiato le ultime due icone.  
  
-   Aggiungere un suono quando il giocatore trova una coppia, un altro suono quando il giocatore scopre due icone che non corrispondono e un terzo suono quando le icone vengono nuovamente nascoste dal programma.  
  
    > [!TIP]
    >  Per riprodurre suoni, è possibile utilizzare lo spazio dei nomi System.media. Per altre informazioni, vedere [Play Sounds in Windows Forms App (C# )](http://youtu.be/qOh4ooHg1UU) (Riprodurre suoni in app di Windows Form - C# ) o [How To Play Audio In Visual Basic](http://youtu.be/-4oPDeQrtMs) (Come riprodurre suoni in Visual Basic).  
  
-   Rendere più difficile il gioco ingrandendo la lavagna.  
  
    > [!TIP]
    >  Non sarà sufficiente aggiungere righe e colonne in TableLayoutPanel: sarà necessario considerare anche il numero di icone da creare.  
  
-   Rendere più impegnativo il gioco nascondendo la prima icona se il giocatore è troppo lento a rispondere e non sceglie la seconda icona prima di un determinato periodo di tempo.  
  
### <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione  
  
-   In caso di blocchi improvvisi o dubbi a livello di programmazione, provare a pubblicare una domanda in uno dei forum MSDN. Vedere il [forum di Visual Basic](http://social.msdn.microsoft.com/Forums/home?forum=vbgeneral) e il [forum di Visual C#](http://social.msdn.microsoft.com/Forums/home?forum=csharpgeneral).  
  
-   Sono disponibili utilissime risorse di formazione video gratuite. Per altre informazioni sulla programmazione in Visual Basic, vedere [Visual Basic Fundamentals: Development for Absolute Beginners](http://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners) (Nozioni fondamentali di Visual Basic: sviluppo per principianti assoluti). Per altre informazioni sulla programmazione in Visual C#, vedere [C# Fundamentals: Development for Absolute Beginners](http://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners) (Nozioni fondamentali di C#: sviluppo per principianti assoluti).  
  
-   Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 8: Aggiungere un metodo per verificare se il giocatore ha vinto](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).