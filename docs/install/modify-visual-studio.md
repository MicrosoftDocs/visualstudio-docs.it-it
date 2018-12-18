---
title: Modificare Visual Studio 2017 | Microsoft Docs
description: Informazioni dettagliate su come modificare Visual Studio.
ms.custom: H1Hack27Feb2017
ms.date: 11/08/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- modify Visual Studio
- change visual studio
- changing Visual Studio
- customize Visual Studio
ms.assetid: 3399ea7b-a291-4a9e-80a1-b861a21afa1d
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8278b138e8cf7a8780ad83d591a823fdb85f2b08
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="modify-visual-studio-2017-by-adding-or-removing-workloads-and-components"></a>Modificare Visual Studio 2017 aggiungendo o rimuovendo carichi di lavoro e componenti
Oltre ad aver semplificato la personalizzazione di Visual Studio in base alle attività da eseguire, è stata semplificata anche la modifica di Visual Studio. Per eseguire questa operazione non è più necessario eseguire una ricerca nel Pannello di controllo, ma è sufficiente avviare il nuovo programma di installazione di Visual Studio ed effettuare le modifiche desiderate.

Ecco come fare.  

## <a name="modify-workloads"></a>Modificare i carichi di lavoro  
 I carichi di lavoro contengono le funzionalità necessarie per il linguaggio di programmazione o piattaforma in uso. Usare i carichi di lavoro per modificare Visual Studio in modo che supporti il lavoro da eseguire quando desiderato.  

>[!IMPORTANT]
>Per installare, aggiornare o modificare Visual Studio, è necessario accedere con un account con autorizzazioni amministrative. Per altre informazioni, vedere [Autorizzazioni utente e Visual Studio](../ide/user-permissions-and-visual-studio.md).

1.  Individuare il programma di installazione di Visual Studio all'interno del computer in uso.  

     Ad esempio, in un computer che esegue l'Aggiornamento dell'anniversario di Windows 10 selezionare **Start** e scorrere fino alla lettera **P** in cui viene visualizzato come **Programma di installazione di Visual Studio**.  

     ![Programma di installazione di Visual Studio](media/vs2017-locate-the-visual-studio-installer.PNG "Individuare il programma di installazione di Microsoft Visual Studio")

     >[!NOTE]
     In alcuni computer il programma di installazione di Visual Studio potrebbe trovarsi sotto la lettera **"M"** come **Microsoft Visual Studio: programma di installazione**.<br/><br/> In alternativa, è possibile trovare il programma di installazione di Visual Studio nel percorso seguente: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

2.  Fare clic o toccare per avviare il programma di installazione e quindi selezionare **Modifica**.  

     ![Avviare o modificare Visual Studio](media/vs2017-modify.PNG "Modificare Visual Studio 2017")  

3.  Nella schermata **Carichi di lavoro** selezionare o deselezionare i carichi di lavoro da installare o disinstallare.  

    ![Finestra di dialogo di installazione di Visual Studio 2017](media/vs2017-modify-workloads.PNG "Scegliere un carico di lavoro in Visual Studio 2017")

4. Fare clic o toccare **Modifica** di nuovo.  

5. Dopo aver installato i carichi di lavoro e i componenti nuovi, fare clic su **Avvia**.

## <a name="modify-individual-components"></a>Modificare i singoli componenti

Se non si intende usare la comoda funzionalità Carichi di lavoro per personalizzare l'installazione di Visual Studio, scegliere l'opzione **Singoli componenti** dal programma di installazione di Visual Studio, selezionare i componenti desiderati e seguire le istruzioni visualizzate.  

## <a name="get-support"></a>Supporto
Non sempre tutto funziona correttamente. Se l'installazione di Visual Studio non riesce, vedere la pagina [Risoluzione degli errori di installazione e aggiornamento di Visual Studio 2017](troubleshooting-installation-issues.md). Se nessuna delle procedure di risoluzione dei problemi risulta utile, contattare Microsoft tramite chat in tempo reale per richiedere assistenza per l'installazione (solo in lingua inglese). Per informazioni dettagliate, vedere la [pagina del supporto di Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Ecco alcune altre opzioni di supporto:
* È possibile segnalare i problemi del prodotto a Microsoft tramite lo strumento [Segnala un problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md) che viene visualizzato sia nel programma di installazione di Visual Studio che nell'IDE di Visual Studio.
* È possibile condividere un suggerimento per il prodotto con Microsoft in [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* È possibile visualizzare lo stato dei problemi del prodotto nella [community degli sviluppatori di Visual Studio](https://developercommunity.visualstudio.com/), dove è possibile creare domande e trovare risposte.
* È anche possibile comunicare con gli sviluppatori Microsoft e altri sviluppatori di Visual Studio partecipando alla [conversazione dedicata a Visual Studio nella community di Gitter](https://gitter.im/Microsoft/VisualStudio).  Per questa opzione è necessario un account [GitHub](https://github.com/).

## <a name="see-also"></a>Vedere anche
* [Installare Visual Studio 2017](install-visual-studio.md)
* [Aggiornare Visual Studio 2017](update-visual-studio.md)
* [Disinstallare Visual Studio 2017](uninstall-visual-studio.md)
