---
title: Installare Visual Studio per Mac | Microsoft Docs
description: Istruzioni su come installare Visual Studio per Mac e i componenti aggiuntivi necessari per lo sviluppo multipiattaforma.
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.openlocfilehash: 5de4760b001e82a0c95c593c1308746946b2c630
ms.sourcegitcommit: 65f85389047c5a1938b6d5243ccba8d4f14362ba
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2018
---
# <a name="setup-and-install-visual-studio-for-mac"></a>Configurare e installare Visual Studio per Mac

## <a name="setup"></a>Configurazione

Per iniziare a sviluppare app native multipiattaforma quando si scarica Visual Studio per Mac, è necessario eseguire alcune operazioni di installazione e configurazione di preparazione.

Per l'uso di iOS in Visual Studio è necessario quanto segue:

* Mac con macOS Sierra 10.12 o versione successiva
* Xcode 8.3 o versione successiva. È in genere consigliabile usare la versione stabile più recente.
* ID Apple. Se non si ha ancora un ID Apple, è possibile crearne uno nuovo all'indirizzo https://appleid.apple.com. L'ID Apple è necessario per installare Xcode e accedervi.

## <a name="install"></a>Installazione di

1. Scaricare Visual Studio per Mac da [https://www.visualstudio.com/](https://www.visualstudio.com/)

2. Una volta scaricato il pacchetto di installazione, fare clic sul file **VisualStudioInstaller.dmg** per montare il programma di installazione e quindi eseguirlo facendo doppio clic sul logo, come illustrato nell'immagine seguente:

  ![Finestra di dialogo del programma di installazione](media/installer-image1.png)

3. Potrebbe venire visualizzata una finestra di dialogo di avviso simile a quella dell'immagine seguente. In questo caso, fare clic su **Apri**:

  ![Finestra di dialogo di avviso](media/installer-image2.png)

4. Il programma di installazione controlla il sistema per verificare quali componenti devono essere installati o aggiornati:

  ![Valutazione del sistema](media/installer-image3.png)

5. Verrà quindi visualizzata una finestra di dialogo di avviso che chiede di accettare le condizioni di licenza e privacy. Fare clic su **Continua** per accettare le condizioni:

  ![Finestra di dialogo relativa alla licenza](media/installer-image4.png)

6. Il programma di installazione visualizza un elenco dei componenti necessari che non sono presenti e che devono essere scaricati e installati. Selezionare i prodotti da scaricare:

  ![Selezionare gli elementi](media/installer-image5.png)

  Se non si desidera installare tutte le piattaforme, usare la guida seguente per decidere quali piattaforme installare:

  * **App con Xamarin**:
      - Xamarin.Forms - Selezionare le piattaforme **Android** e **iOS**.
      - Solo iOS - Selezionare la piattaforma **iOS** (si noti che sarà necessario installare [**Xcode**](https://developer.apple.com/xcode/)).
      - Solo Android - Selezionare la piattaforma **Android** (si noti che è necessario selezionare anche le dipendenze rilevanti).
      - Solo Mac - Selezionare la piattaforma **macOS** (si noti che sarà necessario installare [**Xcode**](https://developer.apple.com/xcode/)).
      - App Xamarin completamente multipiattaforma - Selezionare le piattaforme **Android**, **iOS** e **macOS**.
  * **Applicazioni .NET Core** - Selezionare la piattaforma **.NET Core**.
  * **Applicazioni Web ASP.NET Core** - Selezionare la piattaforma **.NET Core**.
  * **Sviluppo di giochi Unity multipiattaforma** - Non è necessario installare alcuna piattaforma aggiuntiva oltre a Visual Studio per Mac. Fare riferimento alla [guida all'installazione di Unity](~/setup-vsmac-tools-unity.md) per altre informazioni sull'installazione dell'estensione di Unity.

  Questa schermata di installazione mostra la versione e le dimensioni di ogni singolo componente. È possibile fare clic su ogni componente per visualizzare un elenco delle relative dipendenze (per Android), visualizzare altri pacchetti scaricati (per .NET Core) o visualizzare le applicazioni aggiuntive necessarie (per iOS e macOS):

  ![Dipendenze aggiuntive di Android](media/installer-image6.png)

7. Una volta selezionate le opzioni desiderate, fare clic su **Installa e aggiorna** per avviare il processo di installazione.

8. Il programma di installazione avvia il processo di download e installazione degli elementi selezionati:

  ![Avvio dell'installazione](media/installer-image7.png)

  ![Download di Xamarin.Mac](media/installer-image8.png)

  ![Completamento dell'installazione](media/installer-image9.png)

9. Potrebbe essere necessario elevare le autorizzazioni necessarie per i singoli componenti richiesti per il completamento dell'installazione. Immettere le credenziali di amministratore in questa posizione per continuare il processo di installazione:

  ![Immettere le autorizzazioni per continuare l'installazione](media/installer-image10.png)

10. Una volta completata l'installazione, è possibile iniziare a sviluppare app in Visual Studio premendo **Avvia**:

  ![Aprire Visual Studio](media/installer-image11.png)

> [!NOTE]
Se si sceglie di non installare una piattaforma o uno strumento durante l'installazione originale (deselezionandolo nel passaggio 6), è necessario eseguire di nuovo il [programma di installazione](https://www.visualstudio.com/vs/) se si vuole aggiungere i componenti in un secondo momento.


## <a name="install-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Installare Visual Studio per Mac protetto da un firewall o un server proxy

Per installare Visual Studio per Mac protetto da un firewall, determinati endpoint devono essere resi accessibili per consentire i download degli strumenti e degli aggiornamenti necessari per il software.

Configurare la rete per consentire l'accesso alle posizioni seguenti:

* [Endpoint di Visual Studio](/visualstudio/install/install-visual-studio-behind-a-firewall-or-proxy-server)

## <a name="next-steps"></a>Passaggi successivi

L'installazione di Visual Studio per Mac consente di iniziare a scrivere codice per le app. Le guide seguenti vengono fornite per eseguire i passaggi successivi di scrittura e distribuzione dei progetti.

### <a name="ios"></a>iOS

1. [Hello, iOS](https://developer.xamarin.com/guides/ios/getting_started/hello,_iOS/)
2. [Provisioning di dispositivi](https://developer.xamarin.com/guides/ios/getting_started/installation/device_provisioning) (per eseguire l'applicazione nel dispositivo).


### <a name="android"></a>Android

1. [Using the Xamarin Android SDK Manager](https://developer.xamarin.com/guides/android/getting_started/installation/android-sdk/?ide=xs) (Uso di Xamarin Android SDK Manager)
2. [Android SDK Emulator](https://developer.xamarin.com/guides/android/getting_started/installation/android-emulator/) (Emulatore di Android SDK)
4. [Set Up Device for Development](https://developer.xamarin.com/guides/android/getting_started/installation/set_up_device_for_development/) (Configurare il dispositivo per lo sviluppo)

### <a name="net-core-apps-aspnet-core-web-apps-unity-game-development"></a>app .NET core, app Web ASP.NET Core, sviluppo di giochi Unity

Per altri carichi di lavoro, vedere la pagina [Carichi di lavoro](~/workloads.md).