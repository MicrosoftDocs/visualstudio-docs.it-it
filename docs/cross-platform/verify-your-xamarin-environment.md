---
title: Verificare l'ambiente Xamarin | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2018
ms.topic: conceptual
ms.assetid: fd39882e-06d1-4b39-80d2-4d07b6e4f8f5
ms.technology: vs-ide-mobile
author: charlespetzold
ms.author: chape
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: 862af0d8912811aee8e0110b48fa8cc3e8f1c06b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="verify-your-xamarin-environment"></a>Verificare l'ambiente Xamarin

Al termine dei programmi di installazione (vedere [Setup and install](../cross-platform/setup-and-install.md)), dedicare alcuni minuti per verificare che tutto sia pronto per le attività di sviluppo con Xamarin.  
  
 Dopo aver completato la verifica dell'installazione, provare una o entrambe le procedure dettagliate seguenti:  
  
-   [Nozioni di base sulla compilazione di app con Xamarin.Forms in Visual Studio](../cross-platform/learn-app-building-basics-with-xamarin-forms-in-visual-studio.md) per compilare un'applicazione Xamarin.Forms.
  
-   [Creare app con interfaccia utente nativa con Xamarin in Visual Studio](../cross-platform/build-apps-with-native-ui-using-xamarin-in-visual-studio.md) per usare le interfacce utente native in ciascuna piattaforma ma condividere parte del codice in una libreria .NET Standard.
  
## <a name="all-platforms"></a>Tutte le piattaforme 
 
In Visual Studio selezionare prima **Strumenti > Estensioni e aggiornamenti** e controllare se sia necessario aggiornare uno o più componenti di Xamarin.  
  
Creare quindi una nuova soluzione Xamarin.Forms in Visual Studio usando **File > Nuovo progetto**. Nella finestra di dialogo espandere **Visual C# > Multipiattaforma**, selezionare **App per dispositivi mobili (Xamarin.Forms)** e fare clic su OK. Nella finestra di dialogo che segue, selezionare **App vuota**. In **Strategia di condivisione codice** selezionare **.NET Standard**. Fare clic su OK.

Queste azioni creano una soluzione con quattro progetti: un progetto di libreria .NET Standard 2.0 condiviso e progetti di applicazioni per Android e iOS, nonché per la piattaforma UWP (Universal Windows Platform):  
  
![Risultati della creazione di un nuovo progetto dal modello App vuota di Xamarin.Forms](../cross-platform/media/crossplat-xamarin-verify-1.png "CrossPlat Xamarin Verify 1")  
   
## <a name="android"></a>Android  
  
1. Verificare che sia installata la versione più recente di Android SDK Tools. A tale scopo, passare a **Strumenti > Android > Android SDK Manager**. Installare le versioni più recenti di Android SDK Tools, degli strumenti della piattaforma Android SDK e degli strumenti di compilazione di Android SDK. Non è necessario installare sempre il livello API Android più recente. Il livello API necessario dipende dal livello della piattaforma che si vuole usare come destinazione. In genere, con la piattaforma Xamarin viene installato anche il livello della piattaforma Android richiesto.  
  
2.  Convalidare la compilazione e il debug in un dispositivo o in un emulatore:  
  
    -   Fare clic con il pulsante destro del mouse sul progetto Android in Esplora soluzioni e scegliere **Imposta come progetto di avvio**.  
  
    -   Sulla barra degli strumenti è visualizzata una casella di riepilogo a discesa contenente l'elenco degli emulatori e dei dispositivi Android disponibili. 
    
    I dispositivi Android devono essere abilitati per il debug USB tramite Opzioni per sviluppatori nella pagina Impostazioni del dispositivo. Il dispositivo viene quindi collegato al computer con un cavo USB. 
    
    Sono elencati anche gli emulatori. Selezionare uno dei dispositivi o degli emulatori di Visual Studio:

  ![Selezione di Visual Studio Emulator for Android come destinazione di debug](../cross-platform/media/crossplat-xamarin-verify-3.png "CrossPlat Xamarin Verify 3")  
  
  Per informazioni più dettagliate, vedere [Introducing Visual Studio's Emulator for Android](http://blogs.msdn.com/b/visualstudioalm/archive/2014/11/12/introducing-visual-studio-s-emulator-for-android.aspx) (Introduzione a Visual Studio Emulator for Android) (blog di Visual Studio ALM). In caso di problemi di funzionamento dell'emulatore, vedere [Troubleshooting the Visual Studio Emulator for Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md). È anche possibile creare nuovi profili di dispositivo per l'emulatore selezionando **Strumenti > Android > Gestione emulatori Android**.  
  
3. Premere F5 per compilare e distribuire il programma al dispositivo o all'emulatore Android.
  
## <a name="windows"></a>WINDOWS 
  
1.  Fare clic con il pulsante destro del mouse sul progetto Windows universale in Esplora soluzioni e selezionare **Imposta come progetto di avvio**.  

2.  Nell'elenco a discesa **Piattaforme soluzione** selezionare **x86** o **x64**. Selezionare **Computer locale**.

3.  Premere F5 per distribuire il programma al desktop.
  
## <a name="ios"></a>iOS  
  
1.  Assicurarsi che il Mac sia disponibile in rete e associato a Visual Studio, come descritto in [Connessione al Mac](/xamarin/ios/get-started/installation/windows/connecting-to-mac/).  
  
2.  Fare clic con il pulsante destro del mouse sul progetto iOS in Esplora soluzioni e scegliere **Imposta come progetto di avvio**.  
  
3.  Selezionare la destinazione **iPhoneSimulator** nell'elenco a discesa di compilazione di Visual Studio, come illustrato di seguito, oppure la destinazione **iPhone**, nel caso di un dispositivo con tethering al Mac.   
  
 ![Selezione della destinazione di compilazione di iPhoneSimulator](../cross-platform/media/crossplat-xamarin-verify-5.png "CrossPlat Xamarin Verify 5") 

 Se non è elencato alcun simulatore, avviare Xcode nel Mac, selezionare **Xcode > Preferences** (Preferenze) e fare clic su **Download** (Scarica). Sotto l'intestazione **Components** (Componenti) dovrebbero essere visualizzate le versioni del simulatore disponibili per il download. Altre istruzioni per il debug sono disponibili nella pagina [Debug in iOS](/xamarin/ios/deploy-test/debugging-in-xamarin-ios/?tabs=vsmac#Debugging_on_the_Simulator).
  
4.  Selezionare la destinazione del dispositivo emulatore dall'elenco a discesa di Visual Studio:

 ![Selezione di una destinazione di debug iPhone](../cross-platform/media/crossplat-xamarin-verify-6.png "CrossPlat Xamarin Verify 6")

5. Avviare il debugger premendo F5. Il simulatore viene avviato nel Mac, dove è possibile interagire con l'app mentre viene eseguito il debug in Visual Studio. Se al Mac è connesso un iPhone o un iPad fisico, il dispositivo viene visualizzato nell'elenco ed è possibile selezionarlo. Se nell'elenco non è visualizzato alcun dispositivo o simulatore, controllare la connessione al Mac. Vedere l'articolo collegato nel passaggio 1 sopra descritto o passare a **Strumenti > iOS > Associa a Mac**  
  
6.  Se si verificano problemi di connessione al Mac, leggere [Risoluzione dei problemi di connessione](/xamarin/ios/get-started/installation/windows/connecting-to-mac/troubleshooting/).  
  
7.  Se viene visualizzato l'errore "Non esistono profili di provisioning installati corrispondenti alle chiavi di firma del codice Mac OS X installate", provare i suggerimenti seguenti:  
  
  - Verificare che l'account Id Apple sia aggiunto in Xcode nel Mac come descritto nell'articolo relativo all' [aggiunta dell'account personale a Xcode](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html#//apple_ref/doc/uid/TP40013839-CH40-SW1) (apple.com).  Dopo aver aggiunto l'account, assicurarsi di riavviare sia Visual Studio che Xcode.  
    
  - Nella scheda relativa alla firma del bundle iOS nelle proprietà del progetto iOS verificare che il campo Custom Entitlement sia vuoto per la configurazione di debug attiva.  Nota: è consigliabile provare a rimuovere questa impostazione solo se viene segnalato l'errore precedente.  
  
  ![CrossPlat Xamarin Verify 8](../cross-platform/media/crossplat-xamarin-verify-8.png "CrossPlat Xamarin Verify 8")  
