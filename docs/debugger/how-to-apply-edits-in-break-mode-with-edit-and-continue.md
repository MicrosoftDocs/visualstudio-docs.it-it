---
title: 'Procedura: applicare modifiche in modalità di interruzione con modifica e continuazione | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [Visual Basic], applying edits in break mode
- break mode, applying code changes
- Edit and Continue, applying edits in break mode
- editing, break mode
- coding, editing in break mode
- code, editing in break mode
ms.assetid: 1eef7498-6a1f-4fba-8146-510adc6375c9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f031598e0c8f290907e759bcfceac85c1b063f5f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue"></a>Procedura: applicare modifiche in modalità di interruzione con Modifica e continuazione
È possibile usare Modifica e continuazione per modificare il codice in modalità di interruzione e continuare senza interrompere e riavviare l'esecuzione.  
  
Per le limitazioni sull'utilizzo di modifica e continuazione durante il debug, vedere [modifiche al codice supportate (c# e Visual Basic](../debugger/supported-code-changes-csharp.md)]
  
### <a name="to-edit-code-in-break-mode"></a>Per modificare il codice in modalità di interruzione  
  
1.  Attivare la modalità di interruzione in uno dei seguenti modi:  
  
    -   Impostare un punto di interruzione nel codice, quindi scegliere **Avvia debug** dal **Debug** menu e attendere che l'applicazione raggiunga il punto di interruzione.  
  
         oppure  
  
    -   Avviare il debug e quindi selezionare **Interrompi tutto** dal **Debug** menu.  
  
         oppure  
  
    -   Quando si verifica un'eccezione, scegliere **Abilita modifica** sul**eccezioni**.  
  
2.  Apportare le modifiche di codice desiderato e supportato.  
  
     Per ulteriori informazioni, vedere [modifiche al codice supportate (c# e Visual Basic](../debugger/supported-code-changes-csharp.md).  
  
    > [!NOTE]
    >  Se si tenta di apportare una modifica non consentita da Modifica e continuazione, la modifica verrà contrassegnata con una riga ondulata di colore viola e nell'Elenco attività verrà indicata un'attività da eseguire. Per poter proseguire l'esecuzione del codice, è necessario annullare la modifica non valida del codice.  
  
3.  Nel **Debug** menu, fare clic su **continua** per riprendere l'esecuzione.  
  
     Il codice verrà eseguito con le modifiche incorporate nel progetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Modifiche al codice supportate (c# e Visual Basic](../debugger/supported-code-changes-csharp.md)   
 [Modifica e continuazione (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)