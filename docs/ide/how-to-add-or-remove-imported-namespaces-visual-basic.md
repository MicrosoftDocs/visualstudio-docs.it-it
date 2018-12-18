---
title: 'Procedura: Aggiungere o rimuovere spazi dei nomi importati (Visual Basic) | Microsoft Docs'
ms.custom: 
ms.date: 06/21/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adding imported namespaces
- removing imported namespaces
- namespaces [Visual Studio], imported
- imported namespaces [Visual Studio]
- references [Visual Studio], imported namespaces
ms.assetid: 44cebec3-0ea0-47c2-8406-4edeab6a997e
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 015f2efa352b5ff2d8b87e356972270c175d0168
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-or-remove-imported-namespaces-visual-basic"></a>Procedura: aggiungere o rimuovere spazi dei nomi importati (Visual Basic)
L'importazione di uno spazio dei nomi consente di usare nel codice elementi tratti da tale spazio senza doverli qualificare in modo completo. Se, ad esempio, si vuole accedere al metodo `Create` nella classe `System.Messaging.MessageQueue`, è possibile importare lo spazio dei nomi `System.Messaging` e fare riferimento al solo elemento necessario nel codice come `MessageQueue.Create`.  

 Gli spazi dei nomi importati vengono gestiti nella pagina **Riferimenti** di **Creazione progetti**. Le importazioni specificate in questa finestra di dialogo vengono passate direttamente al compilatore (`/imports`) e usate per tutti i file del progetto. L'istruzione `Imports` consente di usare uno spazio dei nomi in un unico file del codice sorgente.  

### <a name="to-add-an-imported-namespace"></a>Per aggiungere uno spazio dei nomi importato  

1.  In **Esplora soluzioni** fare doppio clic sul nodo **Progetto** del progetto.  

2.  Nella scheda **Creazione progetti** fare clic su **Riferimenti**.  

3.  Nell'elenco **Spazi dei nomi importati** selezionare la casella di controllo relativa allo spazio dei nomi da aggiungere.  

    > [!NOTE]
    >  Perché sia possibile importarlo, lo spazio dei nomi deve trovarsi in un componente di riferimento. Se lo spazio dei nomi non è incluso nell'elenco, è necessario aggiungere un riferimento al componente che lo contiene. Per altre informazioni, vedere [Gestione dei riferimenti in un progetto](managing-references-in-a-project.md).  
  
### <a name="to-remove-an-imported-namespace"></a>Per rimuovere uno spazio dei nomi importato  

1.  In **Esplora soluzioni** fare doppio clic sul nodo **Progetto** del progetto.  

2.  Nella scheda **Creazione progetti** fare clic su **Riferimenti**.  

3.  Nell'elenco **Spazi dei nomi importati** deselezionare la casella di controllo per lo spazio dei nomi da rimuovere.  

## <a name="user-imports"></a>Importazioni utente  
 Le importazioni utente consentono di importare una classe specifica all'interno di uno spazio dei nomi anziché l'intero spazio dei nomi. Si supponga, ad esempio, che l'applicazione esegua l'importazione di uno spazio dei nomi `Systems.Diagnostics` ma che l'unica classe di interesse per l'utente all'interno dello spazio dei nomi sia `Debug`. È possibile definire `System.Diagnostics.Debug` come importazione utente e quindi rimuovere l'importazione per `System.Diagnostics`.  

 Se in seguito si decide di importare la classe `EventLog` è possibile specificare `System.Diagnostics.EventLog` come importazione utente e sovrascrivere `System.Diagnostics.Debug` tramite la funzione di aggiornamento.  

#### <a name="to-add-a-user-import"></a>Per aggiungere un'importazione utente  

1.  In **Esplora soluzioni** fare doppio clic sul nodo **Progetto** del progetto.  

2.  Nella scheda **Creazione progetti** fare clic su **Riferimenti**.  

3.  Nella casella di testo sotto l'elenco **Spazi dei nomi importati** immettere il nome completo dello spazio dei nomi da importare, incluso lo spazio dei nomi radice.  

4.  Fare clic sul pulsante **Aggiungi importazione utente** per aggiungere lo spazio dei nomi all'elenco **Spazi dei nomi importati**.  

    > [!NOTE]
    >  Il pulsante **Aggiungi importazione utente** è disabilitato se lo spazio dei nomi corrisponde a uno spazio dei nomi già incluso nell'elenco. Non è infatti possibile aggiungere due volte la stessa importazione.  

#### <a name="to-update-a-user-import"></a>Per aggiornare un'importazione utente  

1.  In **Esplora soluzioni** fare doppio clic sul nodo **Progetto** del progetto.  

2.  Nella scheda **Creazione progetti** fare clic su **Riferimenti**.  

3.  Nell'elenco **Spazi dei nomi importati** selezionare lo spazio dei nomi da modificare.  

4.  Nella casella di testo sotto l'elenco **Spazi dei nomi importati** immettere il nome del nuovo spazio dei nomi.  

5.  Fare clic sul pulsante **Aggiorna importazione utente** per aggiornare lo spazio dei nomi nell'elenco **Spazi dei nomi importati**.  

## <a name="see-also"></a>Vedere anche  
 [Gestione dei riferimenti in un progetto](../ide/managing-references-in-a-project.md)
