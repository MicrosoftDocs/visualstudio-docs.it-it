---
title: Disinstallazione di Visual Studio per Mac | Microsoft Docs
description: Istruzioni per la disinstallazione di Visual Studio per Mac e degli strumenti correlati.
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 4EB95F75-BC2E-4982-9564-2975805712D8
ms.openlocfilehash: 193856ca96395db9a5b3bd494a5b8f1f7331f702
ms.sourcegitcommit: 238cd48787391aa0ed1eb684f3f04e80f7958705
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/12/2018
---
# <a name="uninstalling-visual-studio-for-mac"></a>Disinstallazione di Visual Studio per Mac

Vi sono diversi prodotti Xamarin che consentono lo sviluppo di applicazioni multipiattaforma, incluse app autonome come Visual Studio per Mac.

Questa guida può essere usata per disinstallare singolarmente ogni prodotto spostandosi sulla sezione relativa. Seguendo questa guida è possibile disinstallare l'intero set di strumenti di Xamarin.

Se precedentemente nel computer era installato Xamarin Studio, può essere necessario seguire anche le istruzioni della guida di [disinstallazione](https://developer.xamarin.com/guides/cross-platform/getting_started/installation/uninstalling_xamarin/) in developer.xamarin.com, oltre alla procedura seguente.

## <a name="uninstall-script"></a>Script di disinstallazione

È possibile disinstallare contemporaneamente Visual Studio e i relativi componenti associati usando lo [script di disinstallazione](https://raw.githubusercontent.com/MicrosoftDocs/visualstudio-docs/master/mac/resources/uninstall-vsmac.sh).

Questo script di disinstallazione contiene la maggior parte dei comandi che si trovano nell'articolo. Due elementi principali sono stati omessi dallo script, a causa di possibili dipendenze esterne:

- **Disinstallazione di Mono**
- **Disinstallazione di Android AVD**

Per eseguire lo script, seguire questa procedura:

1. Fare clic con il pulsante destro del mouse sullo script e scegliere **Salva con nome** per salvare il file sul Mac.
2. Aprire Terminal e modificare la directory di lavoro in cui lo script è stato scaricato:

    ```bash
    $ cd /location/of/file
    ```
3. Rendere eseguibile lo script ed eseguirlo con **sudo**:

    ```bash
    $ chmod +x ./uninstall-vsmac.sh
    $ sudo ./uninstall-vsmac.sh
    ```
4. Infine, eliminare lo script di disinstallazione.

## <a name="uninstall-visual-studio-for-mac"></a>Disinstallare Visual Studio per Mac

Il primo passaggio nella disinstallazione di Visual Studio da un Mac consiste nell'individuare **Visual Studio.app** nella directory **/Applicazioni** e trascinarla nel **Cestino**. In alternativa, fare clic con il pulsante destro del mouse e scegliere **Sposta nel cestino** come illustrato nella figura seguente:

![Spostare l'applicazione Visual Studio nel cestino](media/uninstall-image1.png)

L'eliminazione di questo bundle dell'app causa la rimozione di Visual Studio per Mac, anche se possono rimanere nel file system altri file correlati con Xamarin.

Per rimuovere tutte le tracce di Visual Studio per Mac, occorre eseguire i comandi seguenti in Terminal:

```bash
sudo rm -rf "/Applications/Visual Studio.app"
rm -rf ~/Library/Caches/VisualStudio
rm -rf ~/Library/Preferences/VisualStudio
rm -rf ~/Library/Preferences/Visual\ Studio
rm -rf ~/Library/Logs/VisualStudio
rm -rf ~/Library/VisualStudio
rm -rf ~/Library/Preferences/Xamarin/
rm -rf ~/Library/Developer/Xamarin
rm -rf ~/Library/Application\ Support/VisualStudio
rm -rf ~/Library/Application\ Support/VisualStudio/7.0/LocalInstall/Addins/
```

## <a name="uninstall-mono-sdk-mdk"></a>Disinstallare Mono SDK (MDK)

Mono è un'implementazione open source di Microsoft .NET Framework ed è usato da tutti i prodotti Xamarin (Xamarin.iOS, Xamarin.Android e Xamarin.Mac) per consentire lo sviluppo per queste piattaforme in C#.

> [!WARNING]
> Vi sono altre applicazioni al di fuori di Visual Studio per Mac che usano Mono, ad esempio Unity.
> Prima di disinstallare Mono, assicurarsi che non vi siano altre dipendenze.

Per rimuovere Mono Framework da un computer, eseguire i comandi in Terminal:

```bash
sudo rm -rf /Library/Frameworks/Mono.framework
sudo pkgutil --forget com.xamarin.mono-MDK.pkg
sudo rm -rf /etc/paths.d/mono-commands
```

## <a name="uninstall-xamarinandroid"></a>Disinstallare Xamarin.Android

Per l'installazione e l'uso di Xamarin.Android sono richiesti diversi elementi, ad esempio Android SDK e Java SDK.

Usare i comandi seguenti per rimuovere Xamarin.Android:

```bash
sudo rm -rf /Developer/MonoDroid
rm -rf ~/Library/MonoAndroid
sudo pkgutil --forget com.xamarin.android.pkg
sudo rm -rf /Library/Frameworks/Xamarin.Android.framework
```

### <a name="uninstall-android-sdk-and-java-sdk"></a>Disinstallare Android SDK e Java SDK

Android SDK è richiesto per lo sviluppo di applicazioni Android. Per rimuovere completamente tutte le parti di Android SDK, individuare il file in **~/Library/Developer/Xamarin/** e spostarlo nel **Cestino**.

Non è necessario disinstallare Java SDK (JDK) poiché è già inserito nel pacchetto come parte di Mac OS X / macOS.

### <a name="uninstall-android-avd"></a>Disinstallare Android AVD

> [!WARNING]
> Vi sono altre applicazioni al di fuori di Visual Studio per Mac che usano Android AVD e questi componenti di Android aggiuntivi, quali Android Studio.
> La rimozione di questa directory può causare l'interruzione di progetti in Android Studio. 

Per rimuovere tutti gli Android AVD e i componenti di Android aggiuntivi, usare il comando seguente:

```bash
rm -rf ~/.android
```

Per rimuovere solo gli Android AVD, usare il comando seguente:

```bash
rm -rf ~/.android/avd
```

 

## <a name="uninstall-xamarinios"></a>Disinstallare Xamarin.iOS

Xamarin.iOS consente di sviluppare applicazioni iOS usando C# o F# con Visual Studio per Mac.

Usare i comandi seguenti in Terminal per rimuovere tutti i file Xamarin.iOS da un file system:

```bash
rm -rf ~/Library/MonoTouch
sudo rm -rf /Library/Frameworks/Xamarin.iOS.framework
sudo rm -rf /Developer/MonoTouch
sudo pkgutil --forget com.xamarin.monotouch.pkg
sudo pkgutil --forget com.xamarin.xamarin-ios-build-host.pkg
sudo pkgutil --forget com.xamarin.xamarin.ios.pkg
```

## <a name="uninstall-xamarinmac"></a>Disinstallare Xamarin.Mac

È possibile rimuovere dal computer Xamarin.Mac usando i due comandi seguenti per eliminare rispettivamente il prodotto e la licenza dal Mac:

```bash
sudo rm -rf /Library/Frameworks/Xamarin.Mac.framework
rm -rf ~/Library/Xamarin.Mac
```

## <a name="uninstall-workbooks-and-inspector"></a>Disinstallare Workbooks e Inspector

A partire dalla versione 1.2.2, Xamarin Workbooks e Inspector possono essere disinstallati da un terminal eseguendo:

```bash
sudo /Library/Frameworks/Xamarin.Interactive.framework/Versions/Current/uninstall
```

Per le versioni precedenti, è necessario rimuovere manualmente gli artefatti seguenti:

* Eliminare l'app Workbooks all'indirizzo `"/Applications/Xamarin Workbooks.app"`
* Eliminare l'app Inspector `"Applications/Xamarin Inspector.app"`
* Eliminare i componenti aggiuntivi: `"~/Library/Application Support/XamarinStudio-6.0/LocalInstall/Addins/Xamarin.Interactive"` e `"~/Library/Application Support/XamarinStudio-6.0/LocalInstall/Addins/Xamarin.Inspector"`
* Eliminare Inspector e i file di supporto qui: `/Library/Frameworks/Xamarin.Interactive.framework` e `/Library/Frameworks/Xamarin.Inspector.framework`

# <a name="uninstall-the-xamarin-profiler"></a>Disinstallare Xamarin Profiler

```bash
sudo rm -rf "/Applications/Xamarin Profiler.app"
```

## <a name="uninstall-the-visual-studio-installer"></a>Disinstallare il Programma di installazione di Visual Studio

Usare i comandi seguenti per rimuovere tutte le tracce di Xamarin Universal Installer:

```bash
rm -rf ~/Library/Caches/XamarinInstaller/
rm -rf ~/Library/Caches/VisualStudioInstaller/
rm -rf ~/Library/Logs/XamarinInstaller/
rm -rf ~/Library/Logs/VisualStudioInstaller/
rm -rf ~/Library/Preferences/Xamarin/
rm -rf "~/Library/Preferences/Visual Studio/"
```
