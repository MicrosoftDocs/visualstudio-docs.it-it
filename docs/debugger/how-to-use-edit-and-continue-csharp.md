---
title: 'Procedura: utilizzare Modifica e continuazione (c#) | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], about Edit and Continue
ms.assetid: 40e136d8-a08c-43bd-b313-fb821c55eb3c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: a1f073d401ddc1a99e365245f2a8c1b66b13fb8a
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-use-edit-and-continue-c"></a>Procedura: utilizzare Modifica e continuazione (C#)
La funzionalità Modifica e continuazione per C# consente di apportare modifiche al codice in modalità di interruzione durante il debug. Le modifiche possono essere applicate senza terminare e riavviare la sessione di debug.  
  
 Modifica e continuazione viene richiamata automaticamente quando si apportano modifiche in modalità di interruzione, quindi si sceglie un'esecuzione del debugger del comando, ad esempio **continua**, **passaggio**, o **Imposta istruzione successiva**, oppure si valuta una funzione in una finestra del debugger.  
  
> [!NOTE]
>  Modifica e continuazione non è supportata durante il debug di ottimizzazione di codice, codice misto nativo/gestito o codice di SQL Server common language runtime (CLR) integrazione. Per informazioni sugli altri scenari non supportati, vedere [modifiche al codice supportate (c# e Visual Basic)](../debugger/supported-code-changes-csharp.md). Se si tenta di applicare modifiche al codice in uno di questi scenari, il debugger visualizza una finestra di dialogo in cui viene indicato che modifica e continuazione non è supportata.  
  
### <a name="to-invoke-edit-and-continue-automatically"></a>Per richiamare modifica e continuazione automaticamente  
  
1.  In modalità di interruzione, apportare una modifica al codice sorgente.  
  
2.  Dal **Debug** menu, fare clic su **continua**, **passaggio**, o **Imposta istruzione successiva** o valutare una funzione in una finestra del debugger.  
  
     Il nuovo codice viene compilato e il debug continua con il nuovo codice. Alcune modifiche non sono supportate in modifica e continuazione. Per ulteriori informazioni, vedere [modifiche al codice supportate (c# e Visual Basic)](../debugger/supported-code-changes-csharp.md).  
  
### <a name="to-enabledisable-edit-and-continue"></a>Per abilitare o disabilitare Modifica e continuazione  
  
1.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
2.  Nel **opzioni** finestra di dialogo espandere il **debug** nodo e selezionare **modifica e continuazione**.  
  
3.  Nel **opzioni** la finestra di dialogo **modifica e continuazione** pagina, selezionare o deselezionare il **Abilita modifica e continuazione** casella di controllo.  
  
     L'impostazione diventa effettiva quando si riavvia la sessione di debug.  
  
## <a name="see-also"></a>Vedere anche  
 [Modifica e continuazione (Visual c#)](../debugger/edit-and-continue-visual-csharp.md)   
 [Modifiche al codice supportate (c# e Visual Basic)](../debugger/supported-code-changes-csharp.md)   