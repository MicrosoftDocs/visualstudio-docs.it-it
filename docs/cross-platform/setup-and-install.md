---
title: Installare Xamarin per Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2018
ms.topic: conceptual
ms.assetid: 2cfcad00-352c-4161-814c-f5ae32d8ada8
ms.technology: vs-ide-mobile
author: charlespetzold
ms.author: chape
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: 8ae03dfe4ed2e72015ca1f7d91153d862f44ce40
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="setup-and-install"></a>Configurazione e installazione

Per compilare app native iOS, Android e Windows da una base di codice C#/.NET comune con Xamarin, sono necessari l'hardware e il software seguenti:

-   Per usare app Windows e Android: un computer di sviluppo Windows (non una macchina virtuale) in cui sia installato Visual Studio 2017 e le funzionalità di sviluppo Xamarin.  

-   Per usare app iOS: un computer Mac con macOS Sierra 10.12 o versione successiva, con Xcode e Visual Studio per Mac installati.

Per usare la piattaforma Xamarin non sono necessarie licenze a parte.
 
È possibile impostare contemporaneamente i computer Windows e Mac. Durante l'esecuzione dei relativi programmi di installazione, è possibile consultare la pagina [Informazioni sullo sviluppo per dispositivi mobili con Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md) per leggere e guardare il materiale di riferimento necessario.

Se si verificano problemi con l'uso della piattaforma Xamarin dopo aver eseguito la procedura di configurazione e installazione, inserire una domanda in [forums.xamarin.com](http://forums.xamarin.com/).

<a name="prereq" /> 

## <a name="pre-requisites"></a>Prerequisiti

###  <a name="for-targeting-windows-and-android"></a>Per lo sviluppo per Windows e Android

Vedere [Requisiti di sistema per la famiglia di prodotti Visual Studio 2017](https://www.visualstudio.com/productinfo/vs2017-system-requirements-vs) per informazioni dettagliate sui prerequisiti per l'installazione di Visual Studio 2017.

Installare Visual 2017 in un computer Windows fisico (non in una macchina virtuale) che esegue Windows 10 e in cui siano installati tutti gli aggiornamenti. 

### <a name="for-targeting-ios"></a>Per lo sviluppo per iOS

Per lo sviluppo di emulatori e dispositivi iOS da un computer Windows, è necessario anche un Mac o Mac mini connesso in rete con macOS 10.12 o versione successiva e Xcode 8.3. Vedere [Configurare e installare Visual Studio per Mac](/visualstudio/mac/installation.md) per altre informazioni dettagliate sui requisiti.

<a name="windows" /> 

##  <a name="windows-setup-visual-studio-and-xamarin"></a>Installazione di Windows (Visual Studio e Xamarin)

Se Visual Studio 2017 non è stato ancora installato, attenersi alla procedura seguente:

1.  [Scaricare e avviare il programma di installazione di qualsiasi edizione di Visual Studio 2017](https://www.visualstudio.com/downloads/) (Community, Professional o Enterprise). Visual Studio 2017 Community Edition è l'edizione gratuita. Le edizioni Professional ed Enterprise sono disponibili per un periodo di valutazione di 30 giorni dopo il quale è necessaria una licenza.

2.  Quando si apre la finestra di dialogo **Installazione**, selezionare le caselle seguenti:    

    - **Dispositivi mobili e giochi > Sviluppo di applicazioni per dispositivi mobili con .NET**. Questa opzione consente di selezionare automaticamente anche vari strumenti Android e Software Development Kit. 

        ![Selezione dell'opzione Sviluppo di applicazioni per dispositivi mobili in Dispositivi mobili e giochi](../cross-platform/media/cross-plat-xamarin-setup-2a.png "Cross-Plat Xamarin Setup 2")

    - (Facoltativo) **Windows > Sviluppo di app per la piattaforma UWP (Universal Windows Platform)**. 

Se Visual Studio 2017 è già installato, ma non è stata ancora installata la piattaforma Xamarin, attenersi alla procedura seguente:

1. Eseguire il **programma di installazione di Visual Studio** dal menu **Start**.

2.  Nel programma di installazione fare clic sul pulsante **Altro** e scegliere **Modifica**:

    ![Scelta dell'opzione Modifica nell'installazione di Visual Studio](../cross-platform/media/cross-plat-xamarin-setup-1a.png "Cross-Plat Xamarin Setup 1")

3.  Quando si apre la finestra di dialogo **Installazione**, selezionare **Dispositivi mobili e giochi > Sviluppo di applicazioni per dispositivi mobili con .NET** e facoltativamente **Windows > Sviluppo di app per la piattaforma UWP (Universal Windows Platform)**. L'opzione **Sviluppo di applicazioni per dispositivi mobili con .NET** eseguirà anche l'aggiornamento di eventuali installazioni Xamarin esistenti.

Durante l'installazione, è possibile procedere con le istruzioni di installazione Mac e passare a [Informazioni sullo sviluppo per dispositivi mobili con Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md).

5.  Al termine dell'installazione, avviare Visual Studio e accedere con l'account Microsoft se viene richiesto. Si tratta dello stesso account che viene usato per Windows.

6.  Per eseguire il test di app Android, usare l'[emulatore di Android SDK](/xamarin/android/get-started/installation/android-emulator/) se non è disponibile un dispositivo fisico. 

<a name="mac" />

##  <a name="mac-setup-apple-id-xcode-and-xamarin"></a>Installazione di Mac (ID Apple, Xcode e Xamarin)

1.  Se non si ha ancora un ID Apple, è possibile crearne uno gratuitamente all'indirizzo [https://appleid.apple.com](https://appleid.apple.com/). L'ID Apple è necessario per l'installazione e l'accesso a Xcode.

2.  Scaricare e installare Xcode da [https://developer.apple.com/xcode/](https://developer.apple.com/xcode/) e aggiungere l'ID Apple come descritto in [Adding Your Account to XCode](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html#//apple_ref/doc/uid/TP40013839-CH40-SW1) (Aggiunta dell'account a XCode) nel sito apple.com.

3.  Scaricare e installare Visual Studio per Mac seguendo le istruzioni riportate in [Configurare e installare Visual Studio per Mac](/visualstudio/mac/installation.md).

4.  Dopo aver completato l'installazione di Xamarin sia nei computer Windows che nei computer Mac, seguire le istruzioni riportate in [Connessione al Mac](/xamarin/ios/get-started/installation/windows/connecting-to-mac/) in modo da poter usare iOS e il Mac da Visual Studio nel computer Windows.

Entrambi i computer devono trovarsi nella stessa rete locale.