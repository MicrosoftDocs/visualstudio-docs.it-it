---
title: 'Esercitazione 3: creare un gioco di abbinamenti | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-acquisition
ms.topic: conceptual
ms.assetid: 525815c8-2845-45e8-be96-100d1f144725
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c3d0e538304e2d9c3fb5ca71747fd1ed2ab2a5fa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="tutorial-3-create-a-matching-game"></a>Esercitazione 3: Creare un gioco di abbinamenti
In questa esercitazione si compila un gioco delle coppie, in cui il giocatore deve riuscire ad accoppiare icone nascoste. Vengono illustrate le seguenti procedure:  
  
-   Archiviare oggetti, ad esempio icone, in un oggetto `List`.  
  
-   Utilizzare un ciclo `foreach` in Visual C# o un ciclo `For Each` in Visual Basic per scorrere gli elementi di un elenco.  
  
-   Tenere traccia dello stato di un form utilizzando variabili di riferimento.  
  
-   Compilare un gestore eventi per rispondere a eventi utilizzabili con più oggetti.  
  
-   Creare un timer con conto alla rovescia e quindi generare un evento subito dopo l'avvio.  
  
 Al termine di questa esercitazione, il programma sarà simile all'immagine che segue.  
  
 ![Gioco creato in questa esercitazione](../ide/media/express_finishedgame.png "Express_FinishedGame")  
Gioco che si creerà in questa esercitazione  
  
 Per scaricare una versione completa dell'esempio, vedere [Complete Matching Game tutorial sample](http://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba) (Esempio di esercitazione: un gioco delle coppie completo).  
  
> [!NOTE]
>  In questa esercitazione sono trattati sia Visual C# sia Visual Basic; concentrarsi sulle informazioni specifiche del linguaggio di programmazione in uso.  
  
 In caso di blocchi improvvisi o dubbi a livello di programmazione, provare a pubblicare una domanda in uno dei forum MSDN. Vedere il [forum di Visual Basic](http://social.msdn.microsoft.com/Forums/home?forum=vbgeneral) e il [forum di Visual C#](http://social.msdn.microsoft.com/Forums/home?forum=csharpgeneral). Sono inoltre disponibili utilissime risorse di formazione video gratuite. Per altre informazioni sulla programmazione in Visual Basic, vedere [Visual Basic Fundamentals: Development for Absolute Beginners](http://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners) (Nozioni fondamentali di Visual Basic: sviluppo per principianti assoluti). Per altre informazioni sulla programmazione in Visual C#, vedere [C# Fundamentals: Development for Absolute Beginners](http://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners) (Nozioni fondamentali di C#: sviluppo per principianti assoluti).  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Passaggio 1: creare un progetto e aggiungere una tabella al form](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)|Per iniziare, creare il progetto e aggiungere un controllo `TableLayoutPanel` per mantenere allineati i controlli.|  
|[Passaggio 2: aggiungere un oggetto casuale e un elenco di icone](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)|Aggiungere un oggetto `Random` e un oggetto `List` per creare un elenco di icone.|  
|[Passaggio 3: assegnare un'icona casuale a ogni etichetta](../ide/step-3-assign-a-random-icon-to-each-label.md)|Assegnare le icone in modo casuale ai controlli `Label`, in modo che ogni gioco sia diverso.|  
|[Passaggio 4: aggiungere un gestore di eventi Click a ogni etichetta](../ide/step-4-add-a-click-event-handler-to-each-label.md)|Aggiungere un gestore degli eventi Click che modifica il colore dell'etichetta sulla quale viene fatto clic.|  
|[Passaggio 5: aggiungere riferimenti alle etichette](../ide/step-5-add-label-references.md)|Aggiungere variabili di riferimento per tenere traccia delle etichette sulle quali viene fatto clic.|  
|[Passaggio 6: aggiungere un timer](../ide/step-6-add-a-timer.md)|Aggiungere un timer al form per tenere traccia del tempo trascorso durante il gioco.|  
|[Passaggio 7: mantenere le coppie visibili](../ide/step-7-keep-pairs-visible.md)|Mantenere le coppie di icone visibili se viene selezionata una coppia corrispondente.|  
|[Passaggio 8: aggiungere un metodo per verificare se il giocatore ha vinto](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)|Aggiungere un metodo `CheckForWinner()` per verificare se il giocatore ha vinto.|  
|[Passaggio 9: provare altre funzionalità](../ide/step-9-try-other-features.md)|Provare altre funzionalità, ad esempio modificare le icone e i colori oppure aggiungere una griglia e i suoni. Provare a ingrandire lo schema e a regolare il timer.|