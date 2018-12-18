---
title: Configurazione e installazione | Microsoft Docs
ms.custom: 
ms.date: 04/13/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2cfcad00-352c-4161-814c-f5ae32d8ada8
caps.latest.revision: "16"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: xamarin
ms.openlocfilehash: ab7dc9eb430f797f11bcdd641af2a06b2380d9ce
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="setup-and-install"></a>Configurazione e installazione
Per creare app native per iOS, Android e Windows da una codebase C#/.NET comune con Xamarin, è necessario quanto segue:  
  
-   Per l'uso con app Windows e Android: un computer di sviluppo Windows con Visual Studio 2017 o 2015 con Xamarin installato (vedere la nota seguente). È anche possibile usare Visual Studio 2013 seguendo le istruzioni per l'[installazione diretta di Xamarin](https://developer.xamarin.com/guides/cross-platform/getting_started/requirements/#install) (xamarin.com). 
  
-   Per l'uso con app iOS: un Mac con macOS Sierra 10.12 o versione successiva, con Xcode e Xamarin installati.  
  
 È possibile impostare contemporaneamente i computer Windows e Mac. Durante l'esecuzione dei relativi programmi di installazione, è possibile consultare la pagina [Informazioni sullo sviluppo per dispositivi mobili con Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md) per leggere e guardare il materiale di riferimento necessario.  
 
In caso di problemi con Xamarin dopo l'esecuzione della procedura di configurazione e installazione, inserire una domanda in [forums.xamarin.com](http://forums.xamarin.com/).
  
> [!NOTE]
>  A partire dal 31 marzo 2016, Xamarin è completamente incluso in tutte le edizioni di Visual Studio senza costi aggiuntivi e non richiede una licenza distinta. Anche Xamarin Studio Community per Mac è disponibile gratuitamente per studenti, sviluppatori di sistemi operativi e team di piccole dimensioni. Tenere presente che per le installazioni esistenti di Visual Studio che sono configurate con licenze Xamarin precedenti, è necessario aggiornare Xamarin alla versione 4.0.3.214 o successiva. A tale scopo, passare a **Strumenti > Opzioni > Xamarin > Altro**, fare clic sul collegamento **Verifica ora** e scaricare l'aggiornamento 4.0.3.214. Quando si riavvia Visual Studio, passare a **Strumenti > Account Xamarin**. Dovrebbe essere visualizzato lo stato aggiornato.  
  
##  <a name="prereq"></a> Prerequisiti  
  
###  <a name="for-targeting-windows-and-android"></a>Per lo sviluppo per Windows e Android 
  
1.  Consigliato: un computer fisico Windows (non una macchina virtuale) che esegue Windows 8 o versioni successive, per ottenere prestazioni ottimali con l'emulatore Android. È importante tenere presente che è necessario un computer fisico e non una macchina virtuale.  
  
2.  È possibile usare un computer con Windows 7 o versione precedente, nel qual caso si userà Xamarin Player per Android come emulatore. 
    
3. Per entrambe le configurazioni, è sempre possibile eseguire le app direttamente nei dispositivi fisici connessi.  
  
### <a name="for-targeting-ios"></a>Per lo sviluppo per iOS  
  
1.  Un Mac o Mac mini connesso in rete con macOS Sierra che esegue macOS 10.12 o versione successiva (obbligatorio per Xcode 8.3).  
  
2.  Quando si usa Visual Studio in un computer Windows (7 o versione successiva) come ambiente di sviluppo principale, è necessario un Mac in rete solo per compilare ed eseguire il debug di app iOS, collegarsi al simulatore iOS o a dispositivi con tethering e usare la finestra di progettazione dello storyboard in Visual Studio per progettare l'interfaccia utente. Anche i modelli Mac meno recenti sono sufficienti per questo ruolo secondario.  
  
##  <a name="windows"></a> Installazione di Windows (Visual Studio e Xamarin)  
  
> [!TIP]
>  Queste istruzioni si applicano a Visual Studio 2017. Per Visual Studio 2015, vedere [MSDN](setup-and-install.md). Per usare Xamarin con Visual Studio 2013 (con Update 2), seguire le istruzioni per l'[installazione diretta di Xamarin](https://developer.xamarin.com/guides/cross-platform/getting_started/requirements/#install) (xamarin.com).  
  
1.  [Scaricare e avviare il programma di installazione di qualsiasi edizione di Visual Studio 2017](https://www.visualstudio.com/downloads/) (Community, Professional o Enterprise). Visual Studio Community 2017 è l'edizione gratuita. Le edizioni Professional ed Enterprise possono essere usate per un periodo di valutazione di 30 giorni, al termine del quale sarà necessario acquistare una licenza.  
  
    1.  Se si dispone già di Visual Studio 2017 installato, eseguire il **programma di installazione di Visual Studio** dal menu **Start**.
  
2.  All'interno del programma di installazione fare clic sul pulsante **Altre opzioni** (icona con tre barrette) _accanto ad_ **Avvio** e quindi scegliere **Modifica**:  
  
     ![Scelta dell'opzione Modifica nell'installazione di Visual Studio](../cross-platform/media/cross-plat-xamarin-setup-1a.png "Cross-Plat Xamarin Setup 1")  
  
3.  Selezionare le caselle seguenti:  
  
    1.  **Dispositivi mobili e giochi > Sviluppo di applicazioni per dispositivi mobili con .NET**. In questo modo verranno selezionati automaticamente anche vari strumenti Android in Strumenti comuni e Software Development Kit. Questa opzione eseguirà inoltre l'aggiornamento di eventuali installazioni esistenti di Xamarin.  
  
         ![Selezione dell'opzione Sviluppo di applicazioni per dispositivi mobili in Dispositivi mobili e giochi](../cross-platform/media/cross-plat-xamarin-setup-2a.png "Cross-Plat Xamarin Setup 2")  
  
    2. (Facoltativo) **Windows > Sviluppo di app per la piattaforma UWP (Universal Windows Platform)**. Sono incluse opzioni per l'installazione di immagini di emulatori che richiederanno più tempo per il download. È sempre possibile tornare al programma di installazione di Visual Studio per aggiungerle in un secondo momento. 
  
4.  Fare clic sul pulsante **Modifica** e attendere l'esecuzione del processo. Anche in questo caso, l'operazione richiederà un certo tempo. Nel frattempo è possibile procedere con le istruzioni di installazione del Mac e passare a [Informazioni sullo sviluppo per dispositivi mobili con Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md).  
  
5.  Al termine dell'installazione, avviare Visual Studio e accedere con l'account Microsoft se viene richiesto (si tratta dello stesso account che viene usato per Windows).  
      
6.  Per i test di app Android, usare l'[emulatore di Android SDK](https://developer.xamarin.com/guides/android/deployment,_testing,_and_metrics/debug-on-emulator/android-sdk-emulator/) se non sono disponibili dispositivi fisici. Vedere la nota seguente.  
  
 **Nota sugli emulatori nei computer Windows:** poiché le CPU supportano una sola tecnologia di virtualizzazione alla volta, è consigliabile averne solo una in uso in un computer di sviluppo. Esistono tre tecnologie di virtualizzazione principali: Hyper-V (usato da Visual Studio Emulator for Android e dall'emulatore di Windows Phone), Virtual Box (usato da Genymotion) e Intel HAXM (usato dall'emulatore di Android SDK). A causa di diversi problemi tra Hyper-V e Virtual Box, in un computer specifico è preferibile usare emulatori di un solo tipo. Questo è il motivo per cui in precedenza si è consigliato di usare Hyper-V nei computer Windows 8 e versioni successive e gli emulatori Intel HAXM in Windows 7 e versioni precedenti e per l'esecuzione di Windows in computer Mac.  
  
##  <a name="mac"></a> Installazione di Mac (ID Apple, Xcode e Xamarin)  
  
1.  Se non si ha ancora un ID Apple, è possibile crearne uno gratuitamente all'indirizzo [https://appleid.apple.com](https://appleid.apple.com/). Questo è necessario per l'installazione e la firma in Xcode.  
  
2.  Scaricare e installare Xcode dalla pagina  [https://developer.apple.com/xcode/](https://developer.apple.com/xcode/)e aggiungere l'ID Apple come descritto nell'articolo relativo all' [aggiunta di un account a XCode](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html#//apple_ref/doc/uid/TP40013839-CH40-SW1) (apple.com).  
  
3.  Scaricare e installare Xamarin seguendo le istruzioni nella pagina relativa a [installazione e configurazione di Xamarin.iOS](http://developer.xamarin.com/guides/ios/getting_started/installation/mac/) (xamarin.com).  
  
4.  Dopo aver completato l'installazione di Xamarin sia nei computer Windows che nei computer Mac, seguire le istruzioni in [Connecting to the Mac](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/xamarin-mac-agent/)(Connessione al Mac) (xamarin.com) in modo da poter usare iOS e il Mac da Visual Studio nel computer Windows.  
  
     Si noti che entrambi i computer devono trovarsi nella stessa rete locale.