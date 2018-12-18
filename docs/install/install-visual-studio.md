---
title: Installare Visual Studio 2017 | Microsoft Docs
description: Informazioni dettagliate sull'installazione di Visual Studio.
ms.custom: ''
ms.date: 12/04/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vs.about
helpviewer_keywords:
- install Visual Studio
- dev15
- set up Visual Studio
- Visual Studio setup
- Visual Studio installer
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b3f6acdd338b0ae8d23fba338c8564d2bd95ad45
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/03/2018
---
# <a name="install-visual-studio-2017"></a>Installare Visual Studio 2017
In questo articolo viene presentato un nuovo modo per installare Visual Studio! Nella versione più recente è stata semplificata la procedura che consente di selezionare e installare solo le funzionalità necessarie. È anche stato ridotto il footprint minimo di Visual Studio in modo che possa essere installato più rapidamente, limitando l'impatto sul sistema.

Per altre informazioni sulle novità in questa versione, vedere le [note sulla versione](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes) Microsoft.

Tutto pronto? Sarà illustrata una procedura dettagliata.

## <a name="step-1---make-sure-your-computer-is-ready-for-visual-studio"></a>Passaggio 1: Verificare che il computer sia pronto per Visual Studio

Prima di iniziare l'installazione di Visual Studio:

1. Controllare i [requisiti di sistema](https://www.visualstudio.com/productinfo/vs2017-system-requirements-vs) I requisiti consentono di verificare se il computer supporta Visual Studio 2017.
2. Applicare gli aggiornamenti più recenti di Windows. Tali aggiornamenti consentono di avere la certezza che nel computer siano presenti sia gli aggiornamenti di sicurezza più recenti sia i componenti di sistema necessari per Visual Studio.
3. Riavviare il computer. Il riavvio evita che eventuali installazioni o aggiornamenti in sospeso impediscano l'installazione di Visual Studio.
4. Liberare spazio. Rimuovere le applicazioni e i file non necessari da %SystemDrive% eseguendo, ad esempio, l'app Pulitura disco.

Per domande sull'esecuzione di Visual Studio 2017 side by side con versioni precedenti di Visual Studio, vedere [Compatibilità con le versioni precedenti](https://www.visualstudio.com/productinfo/vs2017-compatibility-vs#compatibility-with-previous-releases).

## <a name="step-2---download-visual-studio"></a>Passaggio 2: Scaricare Visual Studio

Scaricare quindi il file del programma di avvio automatico di Visual Studio. A tale scopo, fare clic sul pulsante seguente, selezionare l'edizione di Visual Studio 2017 desiderata, fare clic su **Salva** e quindi fare clic su **Apri cartella**.

 > [!div class="button"]
 > [Scarica Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)
<br/>

|         |         |
|---------|---------|
|  ![icona della telecamera](media/video-icon.png "Guardare un video")  |    [Guardare un video](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Download-the-Visual-Studio-Installer-GgrESHD6D_3311787171) su come scaricare il file del programma di avvio automatico di Visual Studio e selezionare l'edizione di Visual Studio adatta alle proprie esigenze. |

## <a name="step-3---install-the-visual-studio-installer"></a>Passaggio 3: Installare il programma di installazione di Visual Studio

Eseguire quindi il file del programma di avvio automatico per installare il programma di installazione di Visual Studio. Questo nuovo programma di installazione semplificato include tutto ciò che occorre per installare e personalizzare Visual Studio 2017.

1.  Dalla cartella **Download** fare doppio clic sul file del programma di avvio automatico corrispondente o simile a uno dei file seguenti:

  * **vs_enterprise.exe** per Visual Studio Enterprise
  * **vs_professional.exe** per Visual Studio Professional
  * **vs_community.exe** per Visual Studio Community  <br><br>

  Se si riceve una comunicazione di Controllo dell'account utente, fare clic su **Sì**.

2.  Verrà richiesto di confermare le [Condizioni di licenza](https://www.visualstudio.com/license-terms/) e l'[Informativa sulla privacy](https://go.microsoft.com/fwlink/?LinkID=824704) di Microsoft. Scegliere **Continua**.  

   ![Condizioni di licenza e informativa sulla privacy](media/vs2017-privacy-and-license-terms.PNG "Condizioni di licenza e informativa sulla privacy")

## <a name="step-4---select-workloads"></a>Passaggio 4: Selezionare i carichi di lavoro

Dopo aver installato il programma di installazione, è possibile usarlo per personalizzare l'installazione selezionando i set di funzionalità o carichi di lavoro desiderati. Ecco come fare.

1.  Individuare il carico di lavoro che si vuole installare nella schermata d'**installazione di Visual Studio**.

 ![Selezionare un carico di lavoro dalla finestra di dialogo della configurazione di Visual Studio 2017](../install/media/install-visual-studio-enterprise.png)

     Scegliere ad esempio il carico di lavoro "Sviluppo per desktop .NET". Include l'editor principale predefinito che offre supporto di base per la modifica del codice per oltre 20 linguaggi, la possibilità di aprire e modificare il codice da qualsiasi cartella senza che sia necessario un progetto e il controllo del codice sorgente integrato.  

2.  Dopo aver selezionato il carico di lavoro, fare clic su **Installa**.

    A questo punto si apriranno diverse schermate di stato in cui sarà visualizzato l'avanzamento dell'installazione di Visual Studio.

3.  Dopo aver installato i carichi di lavoro e i componenti nuovi, fare clic su **Avvia**.  

> [!TIP]
>  In qualsiasi momento dopo l'installazione, è possibile installare i carichi di lavoro o i componenti che non sono stati installati inizialmente. Se si ha Visual Studio aperto, passare a **Strumenti** > **Ottieni strumenti e funzionalità** che apre il programma di installazione di Visual Studio. In alternativa, aprire **il programma di installazione di Visual Studio** dal menu Start. Da qui, è possibile selezionare i carichi di lavoro o i componenti che si vogliono installare e fare clic su **Modifica**.  

|         |         |
|---------|---------|
|  ![icona della telecamera](media/video-icon.png "Guardare un video")  |    [Guardare un video](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Install-Workloads-in-Visual-Studio-2017-jHE19HD6D_1611787171) su come installare il programma di installazione di Visual Studio e quindi installare un carico di lavoro. |

## <a name="step-5---select-individual-components-optional"></a>Passaggio 5: Selezionare singoli componenti (facoltativo)

Se non si vuole usare la funzionalità Carichi di lavoro per personalizzare l'installazione di Visual Studio, è possibile scegliere di installare singoli componenti. Per selezionare componenti singoli, fare clic sull'opzione **Singoli componenti** nel programma di installazione di Visual Studio, selezionare i componenti da installare e seguire le istruzioni.

  ![Visual Studio 2017 - Installare singoli componenti](media/vs2017-components.PNG "Installare singoli componenti di Visual Studio")

  |         |         |
  |---------|---------|
  |  ![icona della telecamera](media/video-icon.png "Guardare un video")  |   [Guardare un video](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Install-Components-in-Visual-Studio-2017-ZMfaVID6D_7411787171) su come installare un singolo componente usando il programma di installazione di Visual Studio. |

## <a name="step-6---install-language-packs-optional"></a>Passaggio 6: Installare i Language Pack (facoltativo)

Per impostazione predefinita, alla prima esecuzione il programma di installazione tenta di trovare una corrispondenza con la lingua del sistema operativo. Per installare Visual Studio 2017 nella lingua prescelta, fare clic sull'opzione **Language Pack** dal programma di installazione di Visual Studio e seguire le istruzioni visualizzate.

  ![Visual Studio 2017 - Installare Language Pack](media/vs2017-languages.PNG "Installare Language Pack di Visual Studio")

  |         |         |
  |---------|---------|
  |  ![icona della telecamera](media/video-icon.png "Guardare un video")  |   [Guardare un video](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Install-Language-Packs-in-Visual-Studio-2017-ByT7yID6D_9011787171) su come installare un Language Pack usando il programma di installazione di Visual Studio. |

### <a name="change-the-installer-language-from-the-command-line"></a>Modificare la lingua del programma di installazione dalla riga di comando

Un altro modo per poter modificare la lingua predefinita consiste nell'eseguire il programma di installazione dalla riga di comando. Ad esempio, usare il comando seguente per forzare l'esecuzione in inglese del programma di installazione: `vs_installer.exe --locale en-US`. Il programma di installazione memorizza questa impostazione per l'esecuzione successiva. Il programma di installazione supporta i token delle lingue seguenti: zh-cn, zh-tw, cs-cz, en-us, es-es, fr-fr, de-de, it-it, ja-jp, ko-kr, pl-pl, pt-br, ru-ru e tr-tr.


## <a name="step-7---start-developing"></a>Passaggio 7: Iniziare a sviluppare
1. Al termine dell'installazione di Visual Studio, fare clic sul pulsante **Avvia** per [iniziare a sviluppare con Visual Studio](../ide/get-started-developing-with-visual-studio.md).

2. Fare clic su **File** e quindi su **Nuovo progetto**.

3. Selezionare un tipo di progetto. <br><br>
   Ad esempio, per [compilare un'app C++](../ide/getting-started-with-cpp-in-visual-studio.md), fare clic su **Installati**, espandere **Visual C++** e selezionare il tipo di progetto C++ che si vuole compilare. <br><br>
   Per [compilare un'app C#](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md), fare clic su **Installati**, espandere **Visual C#** e selezionare il tipo di progetto C# che si vuole compilare.

## <a name="get-support"></a>Supporto
Non sempre tutto funziona correttamente. Se l'installazione di Visual Studio non riesce, vedere la pagina [Risoluzione degli errori di installazione e aggiornamento di Visual Studio 2017](troubleshooting-installation-issues.md). Se nessuna delle procedure di risoluzione dei problemi risulta utile, contattare Microsoft tramite chat in tempo reale per richiedere assistenza per l'installazione (solo in lingua inglese). Per informazioni dettagliate, vedere la [pagina del supporto di Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Ecco alcune altre opzioni di supporto:
* È possibile segnalare i problemi del prodotto a Microsoft tramite lo strumento [Segnala un problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md) che viene visualizzato sia nel programma di installazione di Visual Studio che nell'IDE di Visual Studio.
* È possibile condividere un suggerimento per il prodotto con Microsoft in [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* È possibile visualizzare lo stato dei problemi del prodotto nella [community degli sviluppatori di Visual Studio](https://developercommunity.visualstudio.com/), dove è possibile creare domande e trovare risposte.
* È anche possibile comunicare con gli sviluppatori Microsoft e altri sviluppatori di Visual Studio partecipando alla [conversazione dedicata a Visual Studio nella community di Gitter](https://gitter.im/Microsoft/VisualStudio).  Per questa opzione è necessario un account [GitHub](https://github.com/).

## <a name="see-also"></a>Vedere anche
* [Aggiornare Visual Studio 2017](update-visual-studio.md)
* [Modificare Visual Studio 2017](modify-visual-studio.md)
* [Disinstallare Visual Studio 2017](uninstall-visual-studio.md)
* [Creare un'installazione offline di Visual Studio 2017](create-an-offline-installation-of-visual-studio.md)
* [Guida dell'amministratore di Visual Studio 2017](visual-studio-administrator-guide.md)
  * [Usare i parametri della riga di comando per installare Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
* [Installare Build Tools in un contenitore](build-tools-container.md)
