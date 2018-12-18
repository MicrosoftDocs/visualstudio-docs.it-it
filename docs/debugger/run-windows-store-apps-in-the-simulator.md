---
title: Eseguire App UWP nel simulatore | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 81b69bf8-ec87-4bb6-9ad4-1fa7b7802d16
caps.latest.revision: "42"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: 40cdfaf430483d68744e4ec9535c2546e75d4470
ms.sourcegitcommit: 5d43e9590e2246084670b79269cc9d99124bb3df
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2018
---
# <a name="run-uwp-apps-in-the-simulator"></a>Eseguire App UWP nel simulatore
Il simulatore di Visual Studio per App UWP è un'applicazione desktop che simula un'app UWP. In genere, è possibile eseguire il debug sul computer locale, un dispositivo collegato o un computer remoto. Tuttavia, in alcuni scenari, si consiglia di utilizzare il simulatore di Visual Studio per emulare dello schermo fisico di diverse dimensioni e la risoluzione. È anche possibile simulare i comuni eventi di tocco e rotazione e le proprietà di connessione di rete.
  
 Il simulatore offre un ambiente in cui è possibile progettare, sviluppare, eseguire il debug e testare le app UWP. Tuttavia, prima di pubblicare l'app in Microsoft Store, è necessario testare l'app in un dispositivo reale.  
  
 Il simulatore di Visual Studio per App UWP non eseguito in un ambiente isolato nel computer locale. Di conseguenza, gli errori che si verificano nel simulatore, ad esempio un errore irreversibile a livello di sistema, può influenzare l'intero computer.  
  
> [!IMPORTANT]
>  Il simulatore di Visual Studio 2015 non include il pulsante Georilevazione perché il simulatore di Windows 10 non prevede la simulazione di georilevazione.
  
##  <a name="BKMK_Set_the_simulator_as_the_target"></a> Impostare il simulatore come destinazione  
 Per eseguire l'app UWP nel simulatore, scegli **simulatore** dall'elenco a discesa elenco accanto al **Avvia debug** pulsante del debugger **Standard** barra degli strumenti. Questa opzione è disponibile solo se l'app **minima piattaforma di destinazione. Versione** è minore o uguale al sistema operativo nel computer di sviluppo. 
  
 ![L'esecuzione nel simulatore](../debugger/media/vsrun_f5_simulator.png "VSRUN_F5_Simulator")  
  
##  <a name="BKMK_Choose_an_interaction_mode"></a> Scegliere una modalità di interazione  
 È possibile scegliere le modalità di interazione seguenti  
  
-   ![Pulsante modalità mouse](../debugger/media/simulator_mousemodebtn.png "SIMULATOR_MouseModeBtn") modalità Mouse: imposta la modalità di interazione sui movimenti del mouse. I movimenti del mouse includono clic, doppio clic e trascinamento.  
  
-   ![Pulsante emulazione tocco di avvio](../debugger/media/simulator_starttouchemulationbtn.png "SIMULATOR_StartTouchEmulationBtn") emulazione tocco di avvio: imposta la modalità di interazione sui movimenti tocco di un singolo dito. Gli eventi di un singolo dito includono tocco, trascinamento e scorrimento rapido.  
  
     ![Destinazione di un solo dito sul simulatore](../debugger/media/simulator_onefinger.png "SIMULATOR_OneFinger") l'icona di bersaglio singolo indica la posizione degli eventi nel simulatore. Usa il mouse per posizionare il puntatore.  
  
     ![Destinazione touch un solo dito sul](../debugger/media/simulator_onefingerengaged.png "SIMULATOR_OneFingerEngaged") premere il pulsante sinistro del mouse per attivare la modalità tocco. Ad esempio, fai clic sul pulsante per simulare un tocco o premi e tieni premuto il pulsante mentre trascini o scorri rapidamente.  
  
## <a name="pinch-and-zoom"></a>Zoom indietro/avanti  
 Imposta la modalità di interazione per i movimenti zoom indietro e avanti di due dita.  
  
-   ![Con il dito sul simulatore due](../debugger/media/simulator_twofinger.png "SIMULATOR_TwoFinger")  
  
     La doppia icona di destinazione indica la posizione di due dita sullo schermo del dispositivo.  
  
    -   Sposta il mouse per posizionare le icone sopra l'oggetto sullo schermo del dispositivo.  
  
    -   Ruota la rotellina del mouse avanti o indietro per modificare la distanza simulata delle due dita prima di eseguire il movimento zoom avanti o indietro.  
  
-   -   ![Avvicinare le dita, zoom e rotazioni destinazioni](../debugger/media/simulator_twofingerengaged.png "SIMULATOR_TwoFingerEngaged")  
  
         Premi il pulsante sinistro e ruota la rotellina indietro (verso di te) per fare zoom avanti.  
  
    -   Premi il pulsante sinistro e ruota la rotellina del mouse in avanti (lontano da te) per fare zoom indietro.  
  
## <a name="object-rotation"></a>Rotazione di oggetti  
 Il pulsante **Rotazione emulazione tocco** imposta la modalità di interazione sui movimenti di rotazione usando due dita.  
  
-   -   Sposta il mouse per posizionare le icone sopra l'oggetto sullo schermo del dispositivo.  
  
    -   Ruota la rotellina del mouse avanti o indietro per modificare l'orientamento simulato delle due dita prima di ruotare l'oggetto.  
  
-   -   Premi il pulsante sinistro e ruota la rotellina indietro (verso di te) per ruotare l'oggetto in senso antiorario. Mente ruoti la rotella del mouse, una delle due icone di destinazione ruota intorno all'altra per indicare la dimensione relativa della rotazione.  
  
    -   Premi il pulsante sinistro e ruota la rotellina del mouse avanti (lontano di te) per ruotare l'oggetto in senso orario.  
  
##  <a name="BKMK_Enable_or_disable_Always_on_top_mode"></a> Abilitare o disabilitare la modalità Sempre in primo piano  
 Puoi impostare la finestra del simulatore in modo che sia sempre in primo piano rispetto ad altre finestre. Il pulsante **Attiva/disattiva finestra in primo piano** abilita o disabilita la modalità **Sempre in primo piano** della finestra del simulatore.  
  
##  <a name="BKMK_Change_the_device_orientation"></a> Modificare l'orientamento del dispositivo  
 Puoi modificare l'orientamento verticale e orizzontale del dispositivo ruotando il simulatore di 90 gradi in qualsiasi direzione.  
  
> [!NOTE]
>  Il simulatore non rispetta la proprietà [DisplayProperties.AutoRotationPreferences](http://go.microsoft.com/fwlink/?LinkId=249460) di un progetto. Ad esempio, se il progetto imposta l'orientamento su `Landscape`e quindi ruoti il simulatore sull'orientamento verticale, anche l'immagine visualizzata dal simulatore sarà ruotata e ridimensionata. Verifica queste impostazioni su un dispositivo reale.  
  
> [!NOTE]
>  Se ruoti il simulatore in modo che un suo bordo sia più largo dello schermo su cui viene visualizzato, il simulatore verrà ridimensionato automaticamente alle dimensioni dello schermo. Il simulatore non viene ripristinato alla dimensione originale se lo ruoti di nuovo.  
  
##  <a name="BKMK_Change_the_simulated_screen_size_and_resolution"></a> Modificare le dimensioni e la risoluzione dello schermo simulate  
 Per modificare le dimensioni e la risoluzione dello schermo simulate, scegliere il pulsante **Cambia risoluzione** nella tavolozza e scegliere una nuova dimensione e una nuova risoluzione dall'elenco.  
  
 Le dimensioni e la risoluzione dello schermo sono elencate come *Larghezza schermo in pollici, larghezza in pixel X altezza in pixel*. Come noterai, le dimensioni e la risoluzione dello schermo sono simulate. Le coordinate della posizione nel simulatore vengono convertite nelle coordinate delle dimensioni e della risoluzione del dispositivo selezionato.  
  
> [!NOTE]
>  Puoi salvare le versioni ridimensionate delle immagini bitmap nell'app. Windows caricherà l'immagine corretta per la scala corrente. Per ulteriori informazioni, vedere [Introduzione a progettazione e l'interfaccia utente](/windows/uwp/layout/design-and-ui-intro). Tuttavia, se modifichi la risoluzione del simulatore in modo Windows selezioni un'immagine diversa in base alla risoluzione, dovrai arrestare e riavviare la sessione di debug per visualizzare la nuova immagine.  
  
##  <a name="BKMK_Capture_a_screenshot_of_your_app_for_submission_to_the_Microsoft_Store"></a>Acquisire una schermata dell'app da inviare a Microsoft Store  
 Quando si invia un'app in Microsoft Store, è necessario includere alcune schermate dell'app.  
  
> [!NOTE]
>  La schermata viene salvato con la risoluzione corrente del simulatore. Per modificare la risoluzione, scegli il pulsante **Cambia risoluzione** .  
  
-   Per creare schermate dell'app dal simulatore, scegli il pulsante **Acquisisce la schermata negli Appunti** .  
  
-   Per impostare il percorso in cui si trovano la schermate, scegliere il pulsante **Impostazioni cattura di schermata** e scegliere il percorso dal menu di scelta rapida.  
  
     ![Menu di scelta rapida impostazioni schermata](../debugger/media/simulator_screenshotsettingscntxmnu.png "SIMULATOR_ScreenShotSettingsCntxMnu")  
  
##  <a name="BKMK_Simulate_network_connection_properties"></a> Simulare le proprietà di connessione di rete  
 È possibile consentire agli utenti dell'app per gestire il costo delle connessioni di rete a consumo mantenendo la consapevolezza di connessione dati o costo piano stato modifiche alla rete e consentendo all'app di usare queste informazioni per evitare di dover sostenere costi aggiuntivi per il roaming o il superamento un limite di trasferimento dati specificato. Il [Windows.Networking.Connectivity](/uwp/api/windows.networking.connectivity) API consentono di rispondere a [NetworkStatusChanged](/uwp/api/windows.networking.connectivity.networkinformation) e [TriggerType](/uwp/api/windows.applicationmodel.background.systemtrigger) gli eventi che consentono l'accesso. Vedere [Guida introduttiva: Gestione dei vincoli di costo per le reti a consumo](http://msdn.microsoft.com/library/windows/apps/Hh750310.aspx).  
  
 Per eseguire il debug o il test di codice in grado di riconoscere costo di rete, il simulatore può simulare le proprietà di una rete esposte tramite il [ConnectionProfile](/uwp/api/windows.networking.connectivity.connectionprofile) oggetto restituito da [GetInternetConnectionProfile](/uwp/api/windows.networking.connectivity.networkinformation).
  
 Per simulare le proprietà di rete:  
  
1.  Sulla barra degli strumenti del simulatore scegliere **Modifica proprietà di rete** .  
  
2.  Nella finestra di dialogo **Imposta proprietà di rete** selezionare **Usa proprietà di rete simulate**.  
  
     Deseleziona la casella di controllo per rimuovere la simulazione e tornare alle proprietà di rete dell'interfaccia attualmente connessa.  
  
3.  Immetti un **Nome profilo** per la rete simulata. Si consiglia di utilizzare un nome univoco che è possibile utilizzare per identificare la simulazione nella [ProfileName](/uwp/api/windows.networking.connectivity.connectionprofile) proprietà del [ConnectionProfile](/uwp/api/windows.networking.connectivity.connectionprofile) oggetto.  
  
4.  Selezionare il [NetworkCostType](/uwp/api/windows.networking.connectivity.networkcosttype) valore per il profilo di **tipo costo rete** elenco.  
  
5.  Dal **Flag di stato limite dati** elenco, è possibile impostare il [ApproachingDataLimit](/uwp/api/windows.networking.connectivity.connectioncost) proprietà o [OverDataLimit](/uwp/api/windows.networking.connectivity.connectioncost) proprietà su true, oppure è possibile scegliere  **In limite dati** per impostare entrambi i valori su false.  
  
6.  Dal **stato Roaming** elenco, impostare il [Roaming](/uwp/api/windows.networking.connectivity.connectioncost) proprietà.  
  
7.  Scegliere **imposta proprietà** per simulare le proprietà di rete generando un primo piano [NetworkStatusChanged](/uwp/api/windows.networking.connectivity.networkinformation) evento e uno sfondo [SystemTrigger](/uwp/api/windows.applicationmodel.background.systemtrigger) di tipo  **NetworkStateChange**.  
  
 **Altre informazioni sulla gestione delle connessioni di rete**  
  
 [Guida introduttiva: Gestione dei vincoli di costo per le reti a consumo](http://msdn.microsoft.com/library/windows/apps/Hh750310.aspx)  
  
 [Esempio di informazioni di rete](http://code.msdn.microsoft.com/windowsapps/Network-Information-Sample-63aaa201)  
  
 [Analizzare il consumo di energia](../profiling/analyze-energy-use-in-store-apps.md)  
  
 [Windows.Networking.Connectivity](/uwp/api/windows.networking.connectivity)  
  
 [Come rispondere agli eventi di sistema con attività in background](http://msdn.microsoft.com/en-us/f7c86e86-a7ae-4abb-a923-76b03337a80a)  
  
 [Come attivare eventi di sospensione, ripresa e background nelle app UWP](http://msdn.microsoft.com/library/windows/apps/hh974425.aspx)  
  
##  <a name="BKMK_Navigate_the_simulator_with_the_keyboard"></a> Spostarsi nel simulatore con la tastiera  
 È possibile passare la barra degli strumenti del simulatore premendo **CTRL + ALT + freccia** per spostare lo stato attivo dalla finestra del simulatore alla barra degli strumenti del simulatore. Utilizza **Freccia su** e **Freccia giù** per spostarti tra i pulsanti della barra degli strumenti.  
  
 È possibile arrestare il simulatore premendo **CTRL + ALT + F4**.  
  
## <a name="see-also"></a>Vedere anche  
 [Eseguire app da Visual Studio](../debugger/run-store-apps-from-visual-studio.md)