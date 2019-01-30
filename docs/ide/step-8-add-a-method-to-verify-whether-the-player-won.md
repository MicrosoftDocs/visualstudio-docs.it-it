---
title: 'Passaggio 8: Aggiungere un metodo per verificare se il giocatore ha vinto'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 6e317f6e-ba4c-4306-8924-300b0c2f65c6
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: af467c46899f03422dff654607574f1a5ff14383
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54925382"
---
# <a name="step-8-add-a-method-to-verify-whether-the-player-won"></a>Passaggio 8: Aggiungere un metodo per verificare se il giocatore ha vinto
È stato creato un gioco divertente, ma serve un elemento aggiuntivo per completare l'opera. Il gioco deve terminare quando il giocatore vince, pertanto è necessario aggiungere un metodo `CheckForWinner()` per verificare se il giocatore ha vinto.

## <a name="to-add-a-method-to-verify-whether-the-player-won"></a>Per aggiungere un metodo per verificare se il giocatore ha vinto

1.  Aggiungere un metodo `CheckForWinner()` alla fine del codice, al di sotto del gestore eventi `timer1_Tick()`, come illustrato nel codice seguente.

     [!code-csharp[VbExpressTutorial4Step8#10](../ide/codesnippet/CSharp/step-8-add-a-method-to-verify-whether-the-player-won_1.cs)]
     [!code-vb[VbExpressTutorial4Step8#10](../ide/codesnippet/VisualBasic/step-8-add-a-method-to-verify-whether-the-player-won_1.vb)]

     Il metodo usa un altro ciclo `foreach` in Visual C# o un ciclo `For Each` in Visual Basic per scorrere ogni etichetta in <xref:System.Windows.Forms.TableLayoutPanel>. Utilizza l'operatore di uguaglianza (`==` in Visual C# e `=` in Visual Basic) per controllare il colore dell'icona di ogni etichetta e verificare se corrisponde allo sfondo. Se i colori corrispondono, l'icona resta invisibile e il giocatore non ha accoppiato tutte le icone rimanenti. In tal caso, il programma utilizza un'istruzione `return` per ignorare la parte restante del metodo. Se il ciclo scorre tutte le etichette senza eseguire l'istruzione `return`, significa che tutte le icone nel form sono state accoppiate. Il programma visualizza un oggetto MessageBox con un messaggio di congratulazioni all'utente, quindi chiama il metodo `Close()` del form per terminare il gioco.

2.  Fare quindi in modo che il gestore dell'evento <xref:System.Windows.Forms.Control.Click> dell'etichetta chiami il nuovo metodo `CheckForWinner()`. Accertarsi che il programma verifichi se il giocatore ha vinto immediatamente dopo aver visualizzato la seconda icona scelta dal giocatore. Cercare la riga in cui si è impostato il colore della seconda icona scelta, quindi chiamare il metodo `CheckForWinner()` subito dopo, come illustrato nel codice seguente.

     [!code-csharp[VbExpressTutorial4Step8#11](../ide/codesnippet/CSharp/step-8-add-a-method-to-verify-whether-the-player-won_2.cs)]
     [!code-vb[VbExpressTutorial4Step8#11](../ide/codesnippet/VisualBasic/step-8-add-a-method-to-verify-whether-the-player-won_2.vb)]

3.  Salvare ed eseguire il programma. Giocare e accoppiare tutte le icone. Quando si vince, il programma visualizza un oggetto **MessageBox** con un messaggio di congratulazioni, come illustrato nell'immagine che segue, quindi chiude il riquadro.

     ![Gioco di abbinamenti con MessageBox](../ide/media/express_tut4step8.png)
**Gioco di abbinamenti** con **MessageBox**

## <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione

-   Per procedere al passaggio successivo dell'esercitazione, vedere [Passaggio 9: Provare altre funzionalità](../ide/step-9-try-other-features.md).

-   Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 7: Mantenere le coppie visibili](../ide/step-7-keep-pairs-visible.md).
