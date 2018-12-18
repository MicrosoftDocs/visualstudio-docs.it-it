---
title: Visual C++ per lo sviluppo di app per dispositivi mobili multipiattaforma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0bb872d6-981b-4c96-9143-fcec5336bf0d
author: corob-msft
ms.author: corob
manager: douge
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 00f5bcdbdd84de3a33914d3ea90f4eb00c960f1f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="visual-c-for-cross-platform-mobile-development"></a>Visual C++ per Sviluppo app per dispositivi mobili multipiattaforma
È possibile compilare app C++ native per dispositivi iOS, Android e Windows e condividere il codice comune nelle librerie create per iOS, Android e Windows usando Visual C++ per lo sviluppo di app per dispositivi mobili multipiattaforma. Si tratta di un'opzione disponibile in Visual Studio 2015 che consente di installare gli SDK e gli strumenti necessari per lo sviluppo multipiattaforma di librerie condivise e app native. Quando è installata, è possibile usare Visual C++ per creare codice che viene eseguito su dispositivi e piattaforme iOS e Android, oltre a Windows, Windows Phone e Xbox.  
  
 La scrittura di codice per piattaforme multiple può essere frustrante. I linguaggi e gli strumenti di sviluppo primari per iOS, Android e Windows sono diversi a seconda della piattaforma. Comunque, tutte le piattaforme supportano la scrittura di codice in C++. Questo è il denominatore comune che si può usare per consentire il riutilizzo del codice di base su piattaforme diverse. Il codice nativo scritto in C++ può essere più efficiente e meno incline alla decompilazione. Il riutilizzo del codice può assicurare un risparmio di tempo e impegno durante la creazione di app per piattaforme multiple.  
  
 Lo sviluppo con Visual C++ per Sviluppo app per dispositivi mobili multipiattaforma presenta molti vantaggi:  
  
1.  **Installazione semplice.** Il programma di installazione di Visual Studio acquisisce e installa gli strumenti e gli SDK di terze parti necessari per compilare app o librerie per Android e iOS. La configurazione e l'installazione sono semplici e per lo più automatiche.  
  
2.  **Ambiente di compilazione potente e familiare.** Creare creare facilmente progetti e soluzioni multipiattaforma condivisibili con i modelli di Visual Studio. Gestire le proprietà per tutti i progetti usando un'unica interfaccia comune. Modificare tutto il codice nell'editor di Visual Studio e sfruttare la tecnologia IntelliSense multipiattaforma incorporata per il completamento del codice e l'evidenziazione degli errori.  
  
3.  **Esperienza di debug unificata.** Usare gli strumenti di debug di altissimo livello disponibili in Visual Studio per osservare ed eseguire il codice C++ su tutte le piattaforme, tra cui dispositivi ed emulatori Android, simulatori e dispositivi iOS e dispositivi ed emulatori Windows o Windows Phone.  
  
## <a name="get-the-tools"></a>Ottenere gli strumenti  
 Visual C++ per Sviluppo app per dispositivi mobili multipiattaforma è un'opzione installabile inclusa in Visual Studio 2015. Per i prerequisiti e le istruzioni di installazione, vedere [Install Visual C++ for Cross-Platform Mobile Development](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md). Per compilare il codice per iOS, è necessario anche un computer Mac e un account Apple iOS Developer Per altre informazioni, vedere [Install And Configure Tools to Build using iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md).  
  
## <a name="come-up-to-speed"></a>Diventare operativi  
 Se si proviene dallo sviluppo per Android o iOS, sono disponibili ottimi materiali per iniziare. Visual Studio è un ambiente di sviluppo espressivo e potente. Per informazioni su come usarlo, vedere la [Guida introduttiva per sviluppatori Android](/previous-versions/windows/apps/dn275875\(v=win.10\)) o la [Guida introduttiva per sviluppatori iOS](/previous-versions/windows/apps/jj657966\(v=win.10\)). Questi argomenti presentano Visual Studio e illustrano i concetti necessari per sviluppare app multipiattaforma per Windows e Windows Phone. Per iniziare a scrivere la prima app multipiattaforma per iOS e Android, vedere [Build an OpenGL ES Application on Android and iOS](../cross-platform/build-an-opengl-es-application-on-android-and-ios.md).  
  
 Visual C++ per Sviluppo app per dispositivi mobili multipiattaforma include diversi modelli utili per iniziare a lavorare alle app:  
  
-   Applicazione OpenGLES 2 (Android, iOS, piattaforma UWP)  
  
     Creare una soluzione che include un set di progetti per compilare un'app Android NativeActivity, un'app iOS e un'app di Windows universale, insieme a una libreria di codice C++ condivisa. Queste app usano librerie specifiche della piattaforma create mediante il codice C++ OpenGL ES comune per disegnare lo stesso cubo rotante in ogni app. Quando si installa Visual Studio per usare questo modello, è necessario includere l'opzione Strumenti per lo sviluppo di app di Windows universale.  
  
-   Applicazione NativeActivity (Android)  
  
     Crea un'app C++ OpenGL completa come progetto Android NativeActivity.  
  
-   Applicazione OpenGLES (Android, iOS)  
  
     Creare una soluzione con un set di progetti per compilare un'app Android NativeActivity e un'app per iOS. Queste app usano librerie specifiche della piattaforma create mediante il codice C++ OpenGL ES comune per disegnare lo stesso cubo rotante in ogni app.  
  
-   Libreria condivisa (Android, iOS)  
  
     Crea una soluzione con progetti per creare un file di libreria dinamica Android (con estensione so) e un file di libreria statica iOS (con estensione a) mediante il codice C++ comune in un progetto condiviso.  
  
-   Applicazione di base (Android, Ant)  
  
     Crea un progetto di app Android "Hello, World" che usa solo il codice sorgente Java e il sistema di compilazione Ant.  
  
-   Applicazione di base (Android, Gradle)  
  
     Crea un progetto di app Android "Hello, World" che usa solo il codice sorgente Java e il sistema di compilazione Gradle.  
  
-   Libreria di base (Android, Ant)  
  
     Crea un progetto di libreria Android "Hello, World" che usa solo il codice sorgente Java e il sistema di compilazione Ant.  
  
-   Libreria di base (Android, Gradle)  
  
     Crea un progetto di libreria Android "Hello, World" che usa solo il codice sorgente Java e il sistema di compilazione Gradle.  
  
-   Libreria condivisa dinamica (Android)  
  
     Crea un file di libreria dinamica Android (con estensione so) usando il codice C++.  
  
-   Applicazione OpenGLES 2 (iOS)  
  
     Crea una soluzione con un set di progetti per la compilazione di un'app iOS OpenGL ES 2. L'app usa una libreria di codice C++ OpenGL ES per disegnare il cubo rotante in un'app iOS. Questa app può essere un buon punto di partenza per ottenere informazioni su come importare le librerie C++ nell'app iOS.  
  
-   Libreria statica (Android)  
  
     Crea un progetto per compilare una libreria statica per Android. In un'app per Android è possibile collegare solo una libreria dinamica, ma un numero qualsiasi di librerie statiche.  
  
-   Libreria statica (iOS)  
  
     Crea un progetto per compilare una libreria statica per iOS.  
  
-   Progetto makefile (Android)  
  
     Crea un wrapper di progetto per i propri progetti makefile Android.  
  
## <a name="try-out-sample-code"></a>Provare il codice di esempio  
 Scaricare esempi che illustrano come creare librerie di codice condiviso che è possibile usare in applicazioni iOS, Android e Windows e come creare app NativeActivity per Android. Per un'introduzione, vedere [Cross-Platform Mobile Development Examples](../cross-platform/cross-platform-mobile-development-examples.md).  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
1.  [Install Visual C++ for Cross-Platform Mobile Development](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)  
  
2.  [Installare e configurare gli strumenti per la compilazione con iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md)  
  
3.  [Creare un'app NativeActivity di Android](../cross-platform/create-an-android-native-activity-app.md)  
  
4.  [Build an OpenGL ES Application on Android and iOS](../cross-platform/build-an-opengl-es-application-on-android-and-ios.md)  
  
5.  [Cross-Platform Mobile Development Examples](../cross-platform/cross-platform-mobile-development-examples.md)