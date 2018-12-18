---
title: 'Passaggio 10: scrivere codice per pulsanti aggiuntivi e una casella di controllo | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-acquisition
ms.topic: conceptual
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 13461522bd4e195eec5bc2a681c8c6b1a9def5d0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>Passaggio 10: scrivere codice per pulsanti aggiuntivi e una casella di controllo
Ora si è pronti per completare gli altri quattro metodi. È possibile copiare e incollare questo codice, ma se si desidera ottenere il massimo vantaggio da questa esercitazione, digitare il codice e utilizzare IntelliSense.  
  
 Con questo codice si aggiungono funzionalità ai pulsanti aggiunti in precedenza. Senza questo codice i pulsanti non eseguono alcuna operazione. I pulsanti utilizzano il codice nei relativi eventi `Click` (la casella di controllo utilizza l'evento `CheckChanged`) per eseguire operazioni diverse quando si attivano i controlli. Ad esempio, tramite l'evento `clearButton_Click`, che si attiva quando si sceglie il pulsante **Cancella immagine**, viene cancellata l'immagine corrente impostando la proprietà `Image` su `null` o `nothing`. Ogni evento nel codice include commenti che spiegano l'azione eseguita dal codice.  
  
 ![link to video](../data-tools/media/playvideo.gif "PlayVideo")Per una versione video di questo argomento, vedere [Tutorial 1: Create a Picture Viewer in Visual Basic - Video 5](http://go.microsoft.com/fwlink/?LinkId=205216) (Esercitazione 1: creare un visualizzatore di immagini in Visual Basic - Video 5) o [Tutorial 1: Create a Picture Viewer in C# - Video 5](http://go.microsoft.com/fwlink/?LinkId=205206) (Esercitazione 1: creare un visualizzatore di immagini in C# - Video 5). In questi video viene usata una versione precedente di Visual Studio, pertanto vi sono piccole differenze in alcuni comandi di menu e altri elementi dell'interfaccia utente. Tuttavia, i concetti e le procedure funzionano in modo analogo nella versione corrente di Visual Studio.  
  
> [!NOTE]
>  Come procedura consigliata, commentare sempre il codice. I commenti contengono informazioni destinate a una persona ed è consigliabile aggiungerli per rendere comprensibile il codice. Tutto ciò che si trova su una riga di commento viene ignorato dal programma. In Visual C# si commenta una riga digitando due barre all'inizio (//), mentre in Visual Basic si commenta una riga anteponendovi una virgoletta singola (').  
  
### <a name="to-write-code-for-additional-buttons-and-a-check-box"></a>Per scrivere codice per una casella di controllo e pulsanti aggiuntivi  
  
-   Aggiungere il codice seguente al file di codice Form1 (Form1.cs o Form1.vb). Scegliere la scheda **VB** per visualizzare il codice Visual Basic.  
  
     [!code-vb[VbExpressTutorial1Step9_10#2](../ide/codesnippet/VisualBasic/step-10-write-code-for-additional-buttons-and-a-check-box_1.vb)]
     [!code-csharp[VbExpressTutorial1Step9_10#2](../ide/codesnippet/CSharp/step-10-write-code-for-additional-buttons-and-a-check-box_1.cs)]  
  
### <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione  
  
-   Per andare al passaggio successivo dell'esercitazione, vedere [Passaggio 11: eseguire il programma e provare altre funzionalità](../ide/step-11-run-your-program-and-try-other-features.md).  
  
-   Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 9: rivedere, commentare e testare il codice](../ide/step-9-review-comment-and-test-your-code.md).