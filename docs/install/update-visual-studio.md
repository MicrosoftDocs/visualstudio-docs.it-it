---
title: Aggiornare Visual Studio 2017 | Microsoft Docs
description: Informazioni dettagliate su come aggiornare Visual Studio.
ms.date: 12/18/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- update Visual Studio
- change visual studio
- changing Visual Studio
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 8e61def66e68d7f889349d0e7b7337238e220dce
ms.sourcegitcommit: e5bd950df79175a96fe62b3d4b17a3ef536ec4c3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="update-visual-studio-2017-to-the-most-recent-release"></a>Aggiornare Visual Studio 2017 alla versione più recente
Visual Studio viene spesso aggiornato per estenderne le funzionalità e correggere i problemi segnalati dagli utenti. È consigliabile eseguire gli aggiornamenti per essere certi di usare sempre la [versione più recente e ottimizzata di Visual Studio](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes#release-history). Ecco come fare.

>[!IMPORTANT]
>Per installare, aggiornare o modificare Visual Studio, è necessario accedere con un account con autorizzazioni amministrative. Per altre informazioni, vedere [Autorizzazioni utente e Visual Studio](../ide/user-permissions-and-visual-studio.md).

## <a name="update-by-using-the-notifications-hub"></a>Eseguire gli aggiornamenti tramite l'hub Notifiche
1. Quando sono disponibili aggiornamenti, viene visualizzato un flag di notifica in Visual Studio.

  ![Aggiornare Visual Studio 2017 tramite l'hub di notifica](media/notification-flag.png "Flag di notifica aggiornamento in Visual Studio")

  Scegliere il flag di notifica per aprire l'hub **di notifica**.

  ![Aggiornare Visual Studio 2017 tramite l'hub Notifiche](media/notifications-hub.png "Hub Notifiche in Visual Studio")

2. Scegliere **"Visual Studio Update" è disponibile**. Verrà aperta la finestra di dialogo **Estensioni e aggiornamenti**.

  ![Aggiornare Visual Studio 2017 tramite l'hub Notifiche](media/notifications-hub-select.png "Hub Notifiche in Visual Studio")

3. Nella finestra di dialogo **Estensioni e aggiornamenti** scegliere il pulsante **Aggiorna**.

  ![Aggiornare Visual Studio 2017 tramite l'hub Notifiche](media/notifications-extensions-and-updates.png "Finestra di dialogo Estensioni e aggiornamenti in Visual Studio")

### <a name="more-about-visual-studio-notifications"></a>Altre informazioni sulle notifiche di Visual Studio

Visual Studio invia una notifica all'utente quando è disponibile un aggiornamento di Visual Studio stesso o di uno o più componenti, nonché quando si verificano eventi specifici nell'ambiente di Visual Studio.

* Se il flag di notifica è giallo, un aggiornamento del prodotto Visual Studio è disponibile per l'installazione.
* Se il flag di notifica è rosso, la licenza presenta un problema.
* Se il flag di notifica è nero, sono presenti messaggi informativi o facoltativi.

Scegliere il flag di notifica per aprire l'hub di **notifica** e quindi scegliere le notifiche su cui si vuole agire. In alternativa, è possibile scegliere di ignorare o eliminare una notifica.

 ![Visualizzare un messaggio informativo o facoltativo nell'hub di notifica](media/notification-flag-optional.png "Flag di notifica di messaggi informativi o facoltativi in Visual Studio")

Se si sceglie di ignorare una notifica, questa non viene più visualizzata da Visual Studio. Se si vuole reimpostare l'elenco delle notifiche ignorate, fare clic sul pulsante **Impostazioni** nell'hub di notifica.

   ![Scegliere il pulsante Impostazioni nell'hub di notifica per visualizzare le opzioni di notifica](media/vs-notifications-hub-settings-button.png "Scegliere il pulsante Impostazioni nell'hub di notifica per visualizzare le opzioni di notifica")

## <a name="update-by-using-the-visual-studio-installer"></a>Eseguire gli aggiornamenti tramite il programma di installazione di Visual Studio
1.  Aprire il programma di installazione. Prima di continuare, potrebbe essere necessario aggiornare il programma di installazione. In tal caso, verrà richiesto di effettuare questa operazione.
 >[!NOTE]
 > In un computer che esegue Windows 10, il programma di installazione si trova sotto la lettera **V** come il **Programma di installazione di Visual Studio** o sotto la lettera **M** come il **Programma di installazione di Microsoft Visual Studio**.

2.  Nella pagina **Prodotto** del programma di installazione cercare l'edizione di Visual Studio installata.

3.  Se è disponibile un aggiornamento, verrà visualizzato un pulsante **Aggiorna**. La verifica della disponibilità di un aggiornamento potrebbe richiedere alcuni secondi.

  Scegliere il pulsante **Aggiorna** per installare gli aggiornamenti.

     ![Aggiornare Visual Studio 2017 tramite il programma di installazione di Visual Studio](media/update-visual-studio.png "Aggiornare Visual Studio 2017 tramite il programma di installazione di Visual Studio")

## <a name="get-support"></a>Supporto
Non sempre tutto funziona correttamente. Se l'installazione di Visual Studio non riesce, vedere la pagina [Risoluzione degli errori di installazione e aggiornamento di Visual Studio 2017](troubleshooting-installation-issues.md). Se nessuna delle procedure di risoluzione dei problemi risulta utile, contattare Microsoft tramite chat in tempo reale per richiedere assistenza per l'installazione (solo in lingua inglese). Per informazioni dettagliate, vedere la [pagina del supporto di Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Ecco alcune altre opzioni di supporto:
* È possibile segnalare i problemi del prodotto a Microsoft tramite lo strumento [Segnala un problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md) che viene visualizzato sia nel programma di installazione di Visual Studio che nell'IDE di Visual Studio.
* È possibile condividere un suggerimento per il prodotto con Microsoft in [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* È possibile visualizzare lo stato dei problemi del prodotto nella [community degli sviluppatori di Visual Studio](https://developercommunity.visualstudio.com/), dove è possibile creare domande e trovare risposte.
* È anche possibile comunicare con gli sviluppatori Microsoft e altri sviluppatori di Visual Studio partecipando alla [conversazione dedicata a Visual Studio nella community di Gitter](https://gitter.im/Microsoft/VisualStudio).  Per questa opzione è necessario un account [GitHub](https://github.com/).

## <a name="see-also"></a>Vedere anche
* [Installare Visual Studio 2017](install-visual-studio.md)
* [Modificare Visual Studio 2017](modify-visual-studio.md)
* [Disinstallare Visual Studio 2017](uninstall-visual-studio.md)
* [Guida dell'amministratore di Visual Studio](visual-studio-administrator-guide.md)
