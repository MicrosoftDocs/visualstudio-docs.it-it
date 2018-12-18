---
title: Compilare un'applicazione OpenGL ES in Android e iOS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 76a67886-df57-4a81-accb-2e3c2eaf607b
author: corob-msft
ms.author: corob
manager: douge
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 41d1a3a88230ed38d4d9688c2f07cdf099e2464b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="build-an-opengl-es-application-on-android-and-ios"></a>Compilare un'applicazione OpenGL ES in Android e iOS
Quando si installa l'opzione Visual C++ per Sviluppo app per dispositivi mobili multipiattaforma, è possibile creare soluzioni e progetti di Visual Studio per le app iOS e Android che condividono un codice comune. Questo argomento descrive un modello di soluzione che crea un'app iOS semplice e un'app NativeActivity di Android. Le app hanno un codice C++ in comune che usa OpenGL ES per visualizzare lo stesso cubo rotante animato in tutte le piattaforme. OpenGL ES (OpenGL for Embedded Systems o GLES) è un'API grafica 2D e 3D supportata in molti dispositivi mobili.  
  
 [Requisiti](#req)   
 [Creare un nuovo progetto di applicazione OpenGLES](#Create)   
 [Compilare ed eseguire l'app Android](#BuildAndroid)   
 [Compilare ed eseguire l'app iOS](#BuildIOS)   
 [Personalizzare le app](#Customize)  
  
##  <a name="req"></a> Requisiti  
 Prima di creare un'app OpenGL ES per iOS e Android, verificare che tutti i requisiti di sistema siano soddisfatti. È necessario installare l'opzione Visual C++ per Sviluppo app per dispositivi mobili multipiattaforma in Visual Studio 2015. Verificare che gli SDK e gli strumenti di terze parti richiesti siano inclusi nell'installazione e che sia installato Visual Studio Emulator per Android. Per altre informazioni e istruzioni dettagliate, vedere [Install Visual C++ for Cross-Platform Mobile Development](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md). Per compilare e testare l'app iOS, è necessario un computer Mac, configurato in base alle istruzioni di installazione. Per altre informazioni sulla configurazione per lo sviluppo di iOS, vedere [Install And Configure Tools to Build using iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md)  
  
##  <a name="Create"></a> Creare un nuovo progetto di applicazione OpenGLES  
 In questa esercitazione verrà creato un nuovo progetto di applicazione OpenGL ES, quindi verrà compilata ed eseguita l'app predefinita in Visual Studio Emulator per Android. Quindi, l'app per iOS verrà compilata ed eseguita nel simulatore iOS.  
  
#### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto  
  
1.  Aprire Visual Studio. Nella barra dei menu scegliere **File**, **Nuovo**, **Progetto**.  
  
2.  Nella finestra di dialogo **Nuovo progetto** in **Modelli**scegliere **Visual C++**, **Multipiattaforma**, quindi scegliere il modello **Applicazione OpenGLES (Android, iOS)** .  
  
3.  Assegnare all'app un nome come `MyOpenGLESApp`, quindi scegliere **OK**.  
  
     ![Nuovo progetto applicazione OpenGLES](../cross-platform/media/cppmdd_opengles_newproj.PNG "CPPMDD_OpenGLES_NewProj")  
  
     Visual Studio crea la nuova soluzione e apre Esplora soluzioni.  
  
     ![MyOpenGLESApp in Esplora soluzioni](../cross-platform/media/cppmdd_opengles_solexpl.PNG "CPPMDD_OpenGLES_SolExpl")  
  
 La nuova soluzione di applicazione OpenGL ES include tre progetti di libreria e due progetti di applicazione. La cartella Librerie include un progetto di codice condiviso e due progetti specifici per la piattaforma che fanno riferimento al codice condiviso:  
  
-   **MyOpenGLESApp.Android.NativeActivity** contiene i riferimenti e il codice glue che implementa l'app come NativeActivity in Android. L'implementazione dei punti di ingresso dal codice glue si trova in main.cpp, che include il codice condiviso comune in MyOpenGLESApp.Shared. Le intestazioni precompilate sono invece in pch.h. Questo progetto di app NativeActivity viene compilato in un file di libreria condivisa (.so) che viene selezionato dal progetto MyOpenGLESApp.Android.Packaging.  
  
-   **MyOpenGLESApp.iOS.StaticLibrary** crea un file di libreria statica iOS (.a) che contiene il codice condiviso in MyOpenGLESApp.Shared. È collegato all'app creata dal progetto MyOpenGLESApp.iOS.Application.  
  
-   **MyOpenGLESApp.Shared** contiene il codice condiviso multipiattaforma. Usa le macro del preprocessore per la compilazione condizionale del codice specifico per la piattaforma. Il codice condiviso viene selezionato dal riferimento al progetto in MyOpenGLESApp.Android.NativeActivity e MyOpenGLESApp.iOS.StaticLibrary.  
  
 La soluzione contiene due progetti per compilare le app per le piattaforme Android e iOS:  
  
-   **MyOpenGLESApp.Android.Packaging** crea il file APK per la distribuzione in un dispositivo o un emulatore Android. Questo progetto contiene le risorse e il file AndroidManifest.xml in cui sono state impostate le proprietà del manifesto. Contiene inoltre il file build.xml che controlla il processo di compilazione Ant. Per impostazione predefinita, è impostato come progetto di avvio in modo che possa essere distribuito ed eseguito direttamente da Visual Studio.  
  
-   **MyOpenGLESApp.iOS.Application** contiene le risorse e il codice glue Objective-C per creare un'app iOS che collega il codice della libreria statica C++ in MyOpenGLESApp.iOS.StaticLibrary. Questo progetto crea un pacchetto di compilazione che viene trasferito al Mac da Visual Studio e dall'agente remoto. Quando si compila questo progetto, Visual Studio invia i file e i comandi per compilare e distribuire l'app nel Mac.  
  
##  <a name="BuildAndroid"></a> Compilare ed eseguire l'app Android  
 La soluzione creata dal modello imposta l'app Android come progetto predefinito.  È possibile compilare ed eseguire l'app per verificare l'installazione e la configurazione. Per un test iniziale, eseguire l'app in uno dei profili del dispositivo installati da Visual Studio Emulator per Android. Se si preferisce testare l'app in un'altra destinazione, è possibile caricare l'emulatore di destinazione o connettere il dispositivo al computer.  
  
#### <a name="to-build-and-run-the-android-native-activity-app"></a>Per compilare ed eseguire l'app NativeActivity di Android  
  
1.  Se non è ancora selezionato, scegliere **x86** dall'elenco a discesa **Piattaforme soluzione** .  
  
     ![Impostare la piattaforma soluzione su x86](../cross-platform/media/cppmdd_opengles_solutionplat.png "CPPMDD_OpenGLES_SolutionPlat")  
  
     Usare x86 per fare riferimento ad Android Emulator per Windows. Se la destinazione è un dispositivo, scegliere la piattaforma soluzione basata sul processore del dispositivo. Se l'elenco **Piattaforme soluzione** non è visualizzato, scegliere **Piattaforme soluzione** dall'elenco **Aggiungi o rimuovi pulsanti** e quindi scegliere la piattaforma.  
  
2.  In **Esplora soluzioni**aprire il menu di scelta rapida per il progetto MyOpenGLESApp.Android.Packaging, quindi scegliere **Compila**.  
  
     ![Compilare il progetto di pacchetti Android](../cross-platform/media/cppmdd_opengles_andbuild.png "CPPMDD_OpenGLES_AndBuild")  
  
     La finestra di output visualizza l'output del processo di compilazione per la libreria condivisa e l'app di Android.  
  
     ![Output di compilazione per progetti Android](../cross-platform/media/cppmdd_opengles_andoutput.png "CPPMDD_OpenGLES_AndOutput")  
  
3.  Scegliere uno dei profili di VS Emulator Android Phone (x86) come destinazione della distribuzione.  
  
     ![Scegliere la destinazione di distribuzione](../cross-platform/media/cppmdd_opengles_pickemulator.png "CPPMDD_OpenGLES_PickEmulator")  
  
     Se sono installati altri emulatori o è connesso un dispositivo Android, è possibile sceglierli nell'elenco a discesa delle destinazioni della distribuzione. Per eseguire l'app, la piattaforma soluzione compilata deve corrispondere alla piattaforma del dispositivo di destinazione.  
  
4.  Premere F5 per avviare il debug o MAIUSC+F5 per avviare senza eseguire il debug.  
  
     Visual Studio avvia l'emulatore, che richiede alcuni secondi per caricare e distribuire il codice. Ecco come verrà visualizzata l'app in Visual Studio Emulator for Android.  
  
     ![App in esecuzione nell'emulatore per Android](../cross-platform/media/cppmdd_opengles_andemulator.png "CPPMDD_OpenGLES_AndEmulator")  
  
     Una volta avviata l'app, è possibile impostare i punti di interruzione e usare il debugger per eseguire il codice un'istruzione alla volta, esaminare le variabili locali e controllare i valori.  
  
5.  Premere MAIUSC+F5 per arrestare il debug.  
  
     L'emulatore è un processo separato che continua a essere eseguito. È possibile modificare, compilare e distribuire il codice più volte nello stesso emulatore. L'app viene visualizzata nella raccolta di app nell'emulatore e può essere avviata direttamente da questa posizione.  
  
 I progetti della libreria e dell'app NativeActivity di Android generati inseriscono il codice condiviso C++ di una libreria dinamica che include il codice "glue" nell'interfaccia con la piattaforma Android. Ciò significa che il codice dell'app si trova nella libreria e il manifesto, le risorse e le istruzioni di compilazione si trovano nel progetto di creazione del pacchetto. Il codice condiviso viene chiamato da main.cpp nel progetto NativeActivity. Per altre informazioni su come programmare NativeActivity di Android, vedere la pagina dei [concetti](https://developer.android.com/ndk/guides/concepts.html) di Android Developer NDK.  
  
 Visual Studio compila i progetti NativeActivity di Android usando Android NDK, che usa Clang come set di strumenti della piattaforma. Visual Studio esegue il mapping delle proprietà del progetto NativeActivity alle opzioni della riga di comando e alle opzioni usate per compilare, collegare ed eseguire il debug nella piattaforma di destinazione. Per dettagli, aprire la finestra di dialogo **Pagine delle proprietà** per il progetto MyOpenGLESApp.Android.NativeActivity. Per altre informazioni sulle opzioni della riga di comando, vedere [Clang Compiler User's Manual](http://clang.llvm.org/docs/UsersManual.html).  
  
##  <a name="BuildIOS"></a> Compilare ed eseguire l'app iOS  
 Il progetto dell'app iOS viene creato e modificato in Visual Studio, ma deve essere compilato e distribuito da un Mac a causa di restrizioni relative alla licenza. Visual Studio comunica con un agente remoto in esecuzione nel Mac per trasferire i file del progetto ed eseguire i comandi di compilazione, distribuzione e debug. Per compilare l'app iOS, è necessario impostare e configurare il Mac e Visual Studio per la comunicazione. Per istruzioni dettagliate, vedere [Install And Configure Tools to Build using iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Quando l'agente remoto è in esecuzione e Visual Studio è associato al Mac, è possibile compilare ed eseguire l'app iOS per verificare l'installazione e la configurazione.  
  
#### <a name="to-build-and-run-the-ios-app"></a>Per compilare ed eseguire l'app iOS  
  
1.  Verificare che l'agente remoto sia in esecuzione nel Mac e che Visual Studio sia associato all'agente remoto. Per avviare l'agente remoto, aprire una finestra dell'app terminale e immettere `vcremote`. Per altre informazioni, vedere [Configurare l'agente remoto in Visual Studio](../cross-platform/install-and-configure-tools-to-build-using-ios.md#ConfigureVS).  
  
     ![Finestra del terminale Mac che esegue vcremote](../cross-platform/media/cppmdd_common_vcremote.png "CPPMDD_common_vcremote")  
  
2.  Se non è ancora selezionato, scegliere **x86** dall'elenco a discesa **Piattaforme soluzione** .  
  
     ![Impostare la piattaforma soluzione su x86](../cross-platform/media/cppmdd_opengles_solutionplat.png "CPPMDD_OpenGLES_SolutionPlat")  
  
     Usare x86 per fare riferimento al simulatore iOS. Se la destinazione è un dispositivo iOS, scegliere la piattaforma soluzione basata sul processore del dispositivo (di solito, un processore ARM). Se l'elenco **Piattaforme soluzione** non è visualizzato, scegliere **Piattaforme soluzione** dall'elenco **Aggiungi o rimuovi pulsanti** e quindi scegliere la piattaforma.  
  
3.  In Esplora soluzioni aprire il menu di scelta rapida per il progetto MyOpenGLESApp.iOS.Application e scegliere **Compila**.  
  
     ![Compilare il progetto applicazione iOS](../cross-platform/media/cppmdd_opengles_iosbuild.png "CPPMDD_OpenGLES_iOSBuild")  
  
     La finestra di output visualizza l'output del processo di compilazione per la libreria statica e l'app di iOS. Nel Mac la finestra terminale che esegue l'agente remoto mostra il comando e l'attività di trasferimento dei file.  
  
     Nel computer Mac potrebbe essere richiesto di accettare una richiesta di firma del codice. Scegliere Consenti per continuare.  
  
4.  Scegliere **Simulatore iOS** nella barra degli strumenti per eseguire l'app nel simulatore iOS nel Mac. L'avvio del simulatore potrebbe richiedere qualche istante. Per vedere l'output, potrebbe essere necessario portare il simulatore in primo piano nel Mac.  
  
     ![App in esecuzione nel simulatore per iOS](../cross-platform/media/cppmdd_opengles_iossimulator.png "CPPMDD_OpenGLES_iOSSimulator")  
  
     Una volta avviata l'app, è possibile impostare i punti di interruzione e usare il debugger di Visual Studio per esaminare le variabili locali, visualizzare lo stack di chiamate e controllare i valori.  
  
     ![Debugger nel punto di interruzione nell'app iOS](../cross-platform/media/cppmdd_opengles_iosdebug.png "CPPMDD_OpenGLES_iOSDebug")  
  
5.  Premere MAIUSC+F5 per arrestare il debug.  
  
     Il simulatore iOS è un processo separato che continua a essere eseguito nel Mac. È possibile modificare, compilare e distribuire il codice più volte nella stessa istanza del simulatore iOS. È anche possibile eseguire il codice direttamente nel simulatore dopo che è stato distribuito.  
  
 I progetti della libreria e dell'app iOS generati inseriscono il codice C++ in una libreria statica che implementa solo il codice condiviso. La maggior parte del codice dell'applicazione si trova nel progetto di applicazione. Le chiamate al codice della libreria condivisa in questo progetto del modello vengono eseguite nel file GameViewController.m. Per compilare l'app iOS, Visual Studio usa il set di strumenti della piattaforma Xcode, che richiede la comunicazione con un client remoto in esecuzione in un Mac.  
  
 Visual Studio trasferisce i file del progetto e invia i comandi al client remoto per compilare l'app con Xcode. Il client remoto invia a sua volta le informazioni sullo stato della compilazione a Visual Studio. Dopo aver compilato l'app, è possibile usare Visual Studio per inviare i comandi per l'esecuzione e il debug dell'app. Il debugger in Visual Studio controlla l'app in esecuzione nel simulatore iOS sul Mac o su un dispositivo iOS collegato. Visual Studio esegue il mapping delle proprietà del progetto StaticLibrary alle opzioni della riga di comando e alle opzioni usate per compilare, collegare ed eseguire il debug nella piattaforma iOS di destinazione. Per dettagli sull'opzione della riga di comando del compilatore, aprire la pagina **Pagine delle proprietà** per il progetto MyOpenGLESApp.iOS.StaticLibrary.  
  
##  <a name="Customize"></a> Personalizzare le app  
 È possibile modificare il codice condiviso C++ per aggiungere o modificare le funzionalità comuni. È necessario modificare le chiamate al codice condiviso nei progetti MyOpenGLESApp.Android.NativeActivity e MyOpenGLESApp.iOS.Application in modo che corrispondano. È possibile usare le macro del preprocessore per specificare le sezioni specifiche per la piattaforma nel codice comune. La macro del preprocessore `__ANDROID__` è predefinita quando viene eseguita la compilazione per Android. La macro del preprocessore `__APPLE__` è predefinita quando viene eseguita la compilazione per iOS.  
  
 Per visualizzare IntelliSense per una specifica piattaforma del progetto, scegliere il progetto nell'elenco a discesa delle funzionalità di commutazione del contesto nella barra Navigazione nella parte superiore della finestra dell'editor.  
  
 ![Elenco a discesa selezione tipo di contesto del progetto nell'editor](../cross-platform/media/cppmdd_opengles_contextswitcher.png "CPPMDD_OpenGLES_ContextSwitcher")  
  
 I problemi di IntelliSense nel progetto corrente vengono contrassegnati con una riga rossa ondulata. I problemi negli altri progetti vengono contrassegnati con una riga viola ondulata. Per impostazione predefinita, Visual Studio non supporta l'applicazione di colori al codice o IntelliSense per i file Java o Objective-C. Tuttavia, è possibile modificare i file di origine e modificare le risorse per impostare il nome dell'applicazione, l'icona e altri dettagli relativi all'implementazione.