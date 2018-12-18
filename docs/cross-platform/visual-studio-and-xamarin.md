---
title: Visual Studio e Xamarin | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2018
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 1da4064f-af69-472c-8f31-98484be5f790
author: charlespetzold
ms.author: chape
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: c16898fa94bcdb051b215f3ff89cf4d42cbe7fe7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="visual-studio-and-xamarin"></a>Visual Studio e Xamarin

Xamarin è una piattaforma per lo sviluppo di app per dispositivi mobili per la creazione di app iOS, Android e Windows native da una codebase C#/.NET comune. Le app scritte con Xamarin possono raggiungere dal 75% a quasi il 100% di riutilizzo di codice tra piattaforme diverse. Queste app hanno accesso completo alle API della piattaforma sottostante e possono incorporare interfacce utente native. Vengono compilate in pacchetti specifici per la piattaforma con un impatto ridotto sulle prestazioni di runtime. Nota: Xamarin supporta anche F#, ma nella presente documentazione verrà illustrato solo C#. Visual Basic non è attualmente supportato.  
  
Gli sviluppatori che hanno familiarità con C#, .NET e Visual Studio possono usufruire della stessa potenza e della stessa produttività quando lavorano con Xamarin per app per dispositivi mobili. Tali vantaggi includono il debug remoto in dispositivi Android, iOS e Windows, senza alcuna necessità di apprendere linguaggi di codifica nativi come Objective-C o Java. Non sorprende quindi che molte applicazioni ad alte prestazioni con interfacce utente accattivanti, come NASCAR, Aviva e MixRadio, siano state create usando Xamarin.  
  
Questa documentazione consente di valutare tutta la potenza di **Visual Studio con Xamarin** per lo sviluppo di queste esperienze.  
  
-   Iniziare con [Setup and install](../cross-platform/setup-and-install.md), un processo che richiederà del tempo (in genere 2-4 ore a seconda della velocità di connessione a Internet, dei componenti già installati e delle opzioni selezionate).  
  
-   Mentre sono in esecuzione i programmi di installazione, è possibile consultare la pagina [Informazioni sullo sviluppo per dispositivi mobili con Xamarin](learn-about-mobile-development-with-xamarin.md) per indicazioni sulle caratteristiche di Xamarin, un confronto tra Xamarin.Forms e l'interfaccia utente nativa e così via.  
  
-   Una volta completata l'installazione, [verificare l'ambiente Xamarin](../cross-platform/verify-your-xamarin-environment.md).  
  
-   Per concludere, consultare l'esercitazione [Nozioni di base sulla compilazione di app con Xamarin.Forms in Visual Studio](/learn-app-building-basics-with-xamarin-forms-in-visual-studio.md).  
  
È possibile usare tutte le funzionalità di Xamarin tramite [una qualsiasi edizione di Visual Studio 2017](https://www.visualstudio.com/vs) (Community, Professional o Enterprise). Non è necessaria una licenza separata.  
  
> [!NOTE]
>  Queste istruzioni descrivono la configurazione del computer più semplice e diretta per gli sviluppatori che hanno familiarità con Windows e Visual Studio. Con questa configurazione l'esperienza di sviluppo complessiva viene semplificata, poiché è sufficiente interagire con il Mac per usare il simulatore iOS e i dispositivi con tethering. Se invece si ha familiarità con l'ambiente Mac, è consigliabile eseguire Visual Studio in Parallels o VMware oppure usare Visual Studio per Mac. Per istruzioni, vedere [Configurazione, installazione e verifiche per gli utenti Mac](../cross-platform/setup-install-and-verifications-for-mac-users.md).  
  
> [!NOTE]
>  Se si vuole una soluzione di sviluppo multipiattaforma basata su HTML e CSS, è disponibile Strumenti di Visual Studio per Apache Cordova, come descritto in [Sviluppo multipiattaforma in Visual Studio](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#HTML).