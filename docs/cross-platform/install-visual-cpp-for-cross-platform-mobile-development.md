---
title: Installare Visual C++ per lo sviluppo di app per dispositivi mobili multipiattaforma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: aaea6b8d-55eb-4427-8185-c050f855c257
author: corob-msft
ms.author: corob
manager: douge
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 64bdc654bc1bcd6721cc29052a9409e00f6afd07
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="install-visual-c-for-cross-platform-mobile-development"></a>Installare Visual C++ per Sviluppo app per dispositivi mobili multipiattaforma
[Visual C++ per Sviluppo app per dispositivi mobili multipiattaforma](http://go.microsoft.com/fwlink/p/?LinkId=536383) è un componente installabile di Visual Studio 2015. Include modelli multipiattaforma di Visual Studio e installa gli SDK e gli strumenti multipiattaforma per iniziare rapidamente, senza doverli individuare, scaricare e configurare manualmente. Con questi strumenti di Visual Studio è possibile creare, modificare, eseguire il debug e testare facilmente i progetti multipiattaforma. Questo argomento descrive come installare gli strumenti e il software di terze parti necessari per sviluppare app multipiattaforma mediante Visual Studio. Per una panoramica del componente, vedere [Visual C++ per dispositivi mobili multipiattaforma](http://go.microsoft.com/fwlink/p/?LinkId=536387)  
  
 [Requisiti](#Requirements)   
 [Ottenere gli strumenti](#GetTheTools)   
 [Installare gli strumenti](#InstallTheTools)   
 [Install tools for iOS](#InstallForiOS)   
 [Installare o aggiornare manualmente le dipendenze](#ThirdParty)  
  
##  <a name="Requirements"></a> Requisiti  
  
-   Per i requisiti di installazione, vedere [Requisiti di sistema di Visual Studio 2015](https://www.visualstudio.com/visual-studio-2015-system-requirements-vs).  
  
    > [!IMPORTANT]
    >  Se si usa Windows 7 o Windows Server 2008 R2, è possibile sviluppare codice per applicazioni di Windows classiche, librerie e app Android NativeActivity, nonché librerie di codice e app per iOS, ma non app di Windows Store o di Windows universale.  
  
 Per compilare le app per specifiche piattaforme del dispositivo sono necessari alcuni requisiti aggiuntivi:  
  
-   Gli emulatori Windows Phone e l'emulatore di Microsoft Visual Studio per Android richiedono un computer in grado di eseguire Hyper-V. Per poter installare ed eseguire gli emulatori, è prima necessario abilitare la funzionalità Hyper-V in Windows. Per altre informazioni, vedere i [requisiti di sistema](http://msdn.microsoft.com/en-us/4d5bb438-231a-4cd2-84b7-e9660b0e3baf) dell'emulatore.  
  
-   Gli emulatori Android x86 inclusi in Android SDK offrono i risultati migliori nei computer in grado di eseguire il driver HAXM Intel. A questo scopo è necessario un processore Intel x64 con supporto di VT-x e della funzionalità del bit di disattivazione dell'esecuzione (XD, Execute Disable Bit). Per altre informazioni, vedere le [istruzioni di installazione per Intel® Hardware Accelerated Execution Manager - Microsoft Windows](http://go.microsoft.com/fwlink/p/?LinkId=536385).  
  
-   La compilazione di codice per iOS richiede un ID Apple, un account iOS Developer Program e un computer Mac in grado di eseguire [Xcode 6](http://go.microsoft.com/fwlink/p/?LinkId=536387) o versioni successive su OS X Mavericks o versioni successive. Per una procedura di installazione semplice, vedere [Install tools for iOS](#InstallForiOS).  
  
##  <a name="GetTheTools"></a> Ottenere gli strumenti  
 Visual C++ per lo sviluppo di app per dispositivi mobili multipiattaforma è un componente installabile incluso nelle edizioni Community, Professional ed Enterprise di Visual Studio. Per ottenere Visual Studio, passare alla pagina [Download di Visual Studio 2015](http://go.microsoft.com/fwlink/p/?linkid=517106) e scaricare Visual Studio 2015 con Update 2 RC o versioni successive.  
  
##  <a name="InstallTheTools"></a> Installare gli strumenti  
 Il programma di installazione per Visual Studio 2015 include un'opzione per installare Visual C++ per Sviluppo app per dispositivi mobili multipiattaforma. Vengono installati gli strumenti, i modelli e i componenti del linguaggio C++ richiesti per Visual Studio, i set di strumenti GCC e Clang necessari per le compilazioni e il debug di Android e i componenti per comunicare con un Mac per lo sviluppo iOS. Vengono anche installati tutti gli strumenti e gli SDK di terze parti necessari per supportare lo sviluppo di app per iOS e Android. Molti di questi strumenti di terze parti sono software open source necessari per il supporto della piattaforma Android.  
  
-   Android Native Development Kit (NDK) è richiesto per compilare codice C++ per la piattaforma Android.  
  
-   Android SDK, Apache Ant e Java SE Development Kit sono richiesti per il processo di compilazione Android.  
  
-   Microsoft Visual Studio Emulator for Android è un emulatore facoltativo ad alte prestazioni utile per il test e il debug del codice.  
  
#### <a name="to-install-visual-c-for-cross-platform-mobile-development-and-the-third-party-tools"></a>Per installare Visual C++ per lo sviluppo di app per dispositivi mobili multipiattaforma e gli strumenti di terze parti  
  
1.  Eseguire il programma di installazione di Visual Studio 2015 scaricato mediante il collegamento in [Ottenere gli strumenti](#GetTheTools). Per installare i componenti facoltativi, scegliere **Personalizzata** come tipo di installazione. Scegliere **Avanti** per selezionare i componenti facoltativi da installare.  
  
2.  In Selezione funzionalità espandere **Sviluppo di app per dispositivi mobili multipiattaforma** e selezionare **Sviluppo di app per dispositivi mobili in Visual C++**.  
  
     ![Selezionare Sviluppo di app per dispositivi mobili in Visual C&#43;&#43;](../cross-platform/media/cppmdd_install_vcmdd.png "CPPMDD_Install_VCMDD")  
  
     Per impostazione predefinita, quando si seleziona **Sviluppo di app per dispositivi mobili in Visual C++**, l'opzione **Linguaggi di programmazione** viene impostata per installare **Visual C++** e le opzioni **Strumenti comuni e Software Development Kit** vengono impostate per installare i componenti di terze parti richiesti. Se necessario, è possibile scegliere componenti aggiuntivi. Per impostazione predefinita, è selezionato anche **Microsoft Visual Studio Emulator for Android**. I componenti già installati risultano inattivi nell'elenco.  
  
     Per compilare app di Windows universale e condividere codice tra tali app e i progetti iOS e Android, in **Selezione funzionalità** espandere **Sviluppo per Windows e Web** e selezionare **Strumenti per lo sviluppo di app di Windows universale**. Se non si prevede di sviluppare app di Windows universale, è possibile ignorare questa opzione.  
  
     Scegliere **Avanti** per continuare.  
  
3.  I componenti di terze parti hanno condizioni di licenza proprie. Per visualizzare le condizioni di licenza, scegliere il collegamento **Condizioni di licenza** accanto a ogni componente. Scegliere **Installa** per aggiungere i componenti e installare Visual Studio e Visual C++ per lo sviluppo di app per dispositivi mobili multipiattaforma.  
  
4.  Al termine dell'installazione, chiudere il programma di installazione e riavviare il computer. Alcune azioni di installazione per i componenti di terze parti non hanno effetto finché il computer non viene riavviato.  
  
    > [!IMPORTANT]
    >  Il riavvio è necessario per assicurare la corretta installazione di tutti i componenti.  
  
     Se non è possibile installare il componente Microsoft Visual Studio Emulator for Android, Hyper-V potrebbe non essere abilitato nel computer. Usare l'app **Attivazione o disattivazione delle funzionalità Windows** del Pannello di controllo per abilitare Hyper-V e quindi eseguire nuovamente il programma di installazione di Visual Studio.  
  
    > [!NOTE]
    >  Se il computer o la versione di Windows in uso non supporta Hyper-V, non è possibile usare il componente Microsoft Visual Studio Emulator for Android. L'edizione Home di Windows non include il supporto per Hyper-V.  
  
5.  Aprire Visual Studio. Se è la prima volta che si esegue Visual Studio, la configurazione e l'accesso possono richiedere tempo. Quando Visual Studio è pronto, nel menu **Strumenti** selezionare **Estensioni e aggiornamenti**, quindi **Aggiornamenti**. Se sono disponibili aggiornamenti di Visual Studio per Visual C++ per Sviluppo app per dispositivi mobili multipiattaforma o per Microsoft Visual Studio Emulator for Android, è necessario installarli.  
  
##  <a name="InstallForiOS"></a> Install tools for iOS  
 È possibile usare Visual C++ per Sviluppo app per dispositivi mobili multipiattaforma per modificare, eseguire il debug e distribuire codice iOS al simulatore iOS o a un dispositivo iOS ma, a causa di restrizioni di licenza, il codice deve essere compilato in remoto su Mac. Per compilare ed eseguire le app iOS usando Visual Studio, è necessario installare e configurare l'agente remoto sul Mac. Per istruzioni dettagliate sull'installazione, prerequisiti e le opzioni di configurazione, vedere [Install And Configure Tools to Build using iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Se non si compila per iOS, è possibile ignorare questo passaggio.  
  
##  <a name="ThirdParty"></a> Installare o aggiornare manualmente le dipendenze  
 Se si decide di non installare una o più dipendenze di terze parti con il programma di installazione di Visual Studio quando si installa l'opzione Sviluppo di app per dispositivi mobili in Visual C++, è possibile installarle in un secondo momento usando la procedura descritta in [Install the tools](#InstallTheTools). Possono anche essere installate a aggiornate in modo indipendente da Visual Studio.  
  
> [!CAUTION]
>  È possibile installare le dipendenze in qualsiasi ordine, ad eccezione di Java. È necessario installare e configurare il JDK prima di installare Android SDK.  
  
 Leggere le seguenti informazioni e usare questi collegamenti per installare manualmente le dipendenze.  
  
-   [Java SE Development Kit](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)  
  
     Per impostazione predefinita, il programma di installazione inserisce gli strumenti Java in C:\Programmi (x86)\Java.  
  
-   [Android SDK](https://developer.android.com/sdk/index.html#Other)  
  
     Durante l'installazione, aggiornare le API come consigliato. Verificare che sia installato almeno l'SDK per Android 5.0 Lollipop (API livello 21). Per impostazione predefinita, il programma di installazione inserisce Android SDK in C:\Programmi (x86)\Android\android-sdk.  
  
     È possibile eseguire di nuovo l'app SDK Manager nella directory Android SDK per aggiornare l'SDK e installare strumenti facoltativi e livelli API aggiuntivi. L'installazione degli aggiornamenti potrebbe non riuscire se non si usa **Esegui come amministratore** per eseguire l'app SDK Manager. In caso di problemi durante la compilazione di un'app Android, in SDK Manager verificare la disponibilità di aggiornamenti per gli SDK installati.  
  
     Per usare alcuni degli emulatori Android forniti con Android SDK, è necessario installare i driver HAXM Intel facoltativi. Può essere necessario rimuovere la funzionalità Hyper-V da Windows per installare correttamente i driver HAXM di Intel. È necessario ripristinare la funzionalità Hyper-V per usare gli emulatori Windows Phone e l'emulatore di Visual Studio per Android.  
  
-   [Android NDK](https://developer.android.com/tools/sdk/ndk/index.html)  
  
     Per impostazione predefinita, il programma di installazione inserisce Android NDK in C:\ProgramData\Microsoft\AndroidNDK. È possibile scaricare e installare di nuovo Android NDK per aggiornare l'installazione.  
  
-   [Apache Ant](http://ant.apache.org/bindownload.cgi)  
  
     Per impostazione predefinita, il programma di installazione inserisce Apache Ant in C:\Programmi (x86)\Microsoft Visual Studio 14.0\Apps.  
  
-   [Microsoft Visual Studio Emulator for Android](http://go.microsoft.com/fwlink/p/?LinkId=536390)  
  
     È possibile installare e aggiornare Microsoft Visual Studio Emulator for Android da Visual Studio Gallery.  
  
 Nella maggior parte dei casi, Visual Studio è in grado di rilevare le configurazioni per il software di terze parti installato e mantiene i percorsi di installazione in variabili di ambiente interne. È possibile eseguire l'override dei percorsi predefiniti di questi strumenti di sviluppo multipiattaforma nell'IDE di Visual Studio.  
  
#### <a name="to-set-the-paths-for-third-party-tools"></a>Per impostare i percorsi per gli strumenti di terze parti  
  
1.  Sulla barra dei menu di Visual Studio scegliere **Strumenti**, quindi **Opzioni**.  
  
2.  Nella finestra di dialogo **Opzioni** espandere **Multipiattaforma**, **C++** e selezionare **Android**.  
  
     ![Opzioni di percorso dello strumento Android](../cross-platform/media/cppmdd_options_android.PNG "CPPMDD_Options_Android")  
  
3.  Per modificare il percorso usato da uno strumento, selezionare la casella di controllo accanto al percorso e modificare il percorso della cartella nella casella di testo. È anche possibile usare il pulsante Sfoglia (**...**) per aprire una finestra di dialogo **Selezionare il percorso** in cui scegliere la cartella.  
  
4.  Scegliere **OK** per salvare i percorsi personalizzati delle cartelle degli strumenti.  
  
## <a name="see-also"></a>Vedere anche  
 [Installare e configurare gli strumenti per la compilazione con iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md)   
 [Visual C++ per dispositivi mobili multipiattaforma](https://www.visualstudio.com/explore/cplusplus-mdd-vs.aspx)