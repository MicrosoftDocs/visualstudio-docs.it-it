---
title: Sincronizzare le modifiche tra XCode e Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c71a4d7c-120e-4559-a114-3a99c4b860a9
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: xamarin
ms.openlocfilehash: 6913ffc5f2a0515b2682036b46ec8c164e9f877b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="sync-changes-between-xcode-and-visual-studio"></a>Sincronizzare le modifiche tra XCode e Visual Studio
Il componente Microsoft Visual C++ per lo sviluppo di app per dispositivi mobili include funzionalità remote per la sincronizzazione del lavoro tra PC e Mac. Quando Visual Studio e i computer Mac vengono associati, sono disponibili nuove opzioni per i progetti di applicazioni iOS in Visual Studio che è possibile usare per aprire il progetto in XCode, spostare il codice tra XCode e Visual Studio e pulire la directory temporanea del progetto XCode.  
  
 Per usare le opzioni Computer remoto, il progetto deve essere un progetto di applicazione iOS e Visual Studio deve essere associato al Mac. Per informazioni sui prerequisiti e istruzioni su come eseguire l'associazione di un Mac, vedere [Installare e configurare gli strumenti per la compilazione con iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md).  
  
## <a name="the-remote-machine-menu"></a>Menu Computer remoto  
 In **Esplora soluzioni** fare clic con il pulsante destro del mouse su un progetto di applicazione iOS per visualizzare il menu di scelta rapida. Selezionare **Computer remoto** per visualizzare le opzioni remote disponibili.  
  
 ![Voce di menu Computer remoto in Esplora soluzioni](../cross-platform/media/cppmdd_u2_remotemachine_menu.jpg "CPPMDD_U2_RemoteMachine_Menu")  
  
 Questi comandi consentono di aprire il progetto in XCode, spostare le modifiche locali o l'intero progetto tra Visual Studio e XCode e pulire i file temporanei nel computer remoto.  
  
### <a name="open-in-xcode"></a>Apri in Xcode  
 Per aprire il progetto in XCode da Visual Studio, scegliere il sottomenu **Computer remoto**, quindi scegliere **Apri in Xcode** per aprire il progetto selezionato nel computer remoto associato. Viene usato il server vcremote per aprire XCode nel Mac e passare a una directory temporanea creata nel Mac che contiene una copia del progetto. Verrà visualizzata una finestra di dialogo di Visual Studio che mostra la directory temporanea usata per il progetto. Le azioni eseguite nel computer remoto sono anche indicate nella finestra **Output** di Visual Studio. Per visualizzarle, può essere necessario selezionare **Computer remoto Visual C++** nell'elenco a discesa **Mostra output di**, disponibile nella parte superiore della finestra **Output**.  
  
 ![Azioni nel computer remoto visualizzate nella finestra Output.](../cross-platform/media/cppmdd_u2_remotemachine_output.png "CPPMDD_U2_RemoteMachine_Output")  
  
 Nel Mac è possibile usare tutti gli strumenti di XCode per modificare il codice, le risorse, gli storyboard e le azioni. In Visual Studio, il progetto di applicazione iOS è contrassegnato come "Aperto in XCode" per indicare che potrebbero essere apportate modifiche nel computer remoto. Dopo aver completato le modifiche, è possibile usare i comandi Pull da computer remoto o Pull incrementale da computer remoto per copiare nuovamente le modifiche nel progetto di Visual Studio.  
  
### <a name="push-to-remote-and-incremental-push-to-remote"></a>Push in computer remoto e Push incrementale in computer remoto  
 Se sono state apportate modifiche al progetto di applicazione iOS in Visual Studio, è possibile usare i comandi Push in computer remoto e Push incrementale in computer remoto per spostare i file di progetto modificati nel computer remoto associato. Il comando Push in computer remoto copia tutti i file di progetto nel computer remoto. Il comando Push incrementale in computer remoto copia solo i file modificati nel computer remoto. Per i progetti di grandi dimensioni con piccole modifiche, il comando incrementale consente di risparmiare tempo e larghezza di banda.  
  
 Per copiare i file di progetto nel Mac, nella finestra **Esplora soluzioni** di Visual Studio fare clic sul progetto di applicazione iOS per aprire il menu di scelta rapida. Selezionare **Computer remoto**, quindi scegliere **Push in computer remoto** o **Push incrementale in computer remoto** per copiare i file di progetto da Visual Studio nel Mac.  
  
### <a name="pull-from-remote-and-incremental-pull-from-remote"></a>Pull da computer remoto e Pull incrementale da computer remoto  
 Dopo aver apportato modifiche al progetto in XCode, spostare nuovamente le modifiche in Visual Studio per mantenere sincronizzati i progetti.  
  
 Per copiare i file di progetto dal Mac, nella finestra **Esplora soluzioni** di Visual Studio fare clic sul progetto di applicazione iOS per aprire il menu di scelta rapida. Selezionare **Computer remoto**, quindi scegliere **Pull da computer remoto** o **Pull incrementale da computer remoto** per copiare i file di progetto dal Mac in Visual Studio.  
  
### <a name="clean-remote"></a>Pulisci computer remoto  
 È possibile usare il comando Pulisci computer remoto per eliminare i file nella directory temporanea del progetto nel computer remoto. Il contenuto della directory, inclusi eventuali file di origine o prodotti di compilazione, viene rimosso dal Mac. Prima di usare il comando Pulisci computer remoto, assicurarsi di avere sincronizzato le modifiche da mantenere in Visual Studio tramite il comando Pull da computer remoto o Pull incrementale da computer remoto.  
  
 Per pulire la directory temporanea del progetto nel computer remoto, nella finestra **Esplora soluzioni** di Visual Studio fare clic sul progetto di applicazione iOS per aprire il menu di scelta rapida. Selezionare **Computer remoto** quindi scegliere **Pulisci computer remoto** per rimuovere i file della directory del progetto dal Mac.