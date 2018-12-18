---
title: Visual Studio e Xamarin | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-mobile
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1da4064f-af69-472c-8f31-98484be5f790
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- xamarin
ms.openlocfilehash: e550d7f6220d4d555d8427bcb1c2a3e814a4f5c3
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="visual-studio-and-xamarin"></a>Visual Studio e Xamarin
Xamarin è una piattaforma per lo sviluppo di app per dispositivi mobili per la creazione di app iOS, Android e Windows native da una codebase C#/.NET comune, che consente di ottenere un riutilizzo del codice tra le piattaforme dal 75% a quasi il 100%. Le app scritte con Xamarin e C# hanno accesso completo alle API della piattaforma sottostante, oltre alla possibilità di creare interfacce utente native ed eseguire la compilazione in pacchetti specifici della piattaforma, rendendo minimo l'impatto sulle prestazioni in fase di runtime. Nota: Xamarin supporta anche F#, ma nella presente documentazione verrà illustrato solo C#. Visual Basic non è attualmente supportato.  
  
 Meglio ancora, gli sviluppatori che hanno familiarità con C#, .NET e Visual Studio potranno trarre vantaggio dalla stessa potenza e produttività quando lavorano con Xamarin per le app per dispositivi mobili, incluso il debug remoto nei dispositivi Android, iOS e Windows, senza dover apprendere linguaggi di codifica nativi come Objective-C o Java. Non sorprende quindi che molte applicazioni ad alte prestazioni con interfacce utente accattivanti, come NASCAR, Aviva e MixRadio, siano state create usando Xamarin.  
  
 Questa documentazione consente di valutare tutte le funzionalità di **Visual Studio con Xamarin** per lo sviluppo di queste esperienze.  
  
-   Iniziare con [Configurazione e installazione](../cross-platform/setup-and-install.md), un processo che richiederà del tempo (in genere 2-4 ore a seconda della velocità di connessione a Internet, dei componenti già installati e delle opzioni selezionate).  
  
-   Mentre sono in esecuzione i programmi di installazione, è possibile consultare la pagina [Informazioni sullo sviluppo per dispositivi mobili con Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md) per indicazioni sulle caratteristiche di Xamarin, un confronto tra Xamarin.Forms e l'interfaccia utente nativa e così via.  
  
-   Una volta completata l'installazione, [verificare l'ambiente Xamarin](../cross-platform/verify-your-xamarin-environment.md).  
  
-   Per concludere, consultare l'esercitazione [Nozioni di base sulla compilazione di app con Xamarin.Forms in Visual Studio](../cross-platform/learn-app-building-basics-with-xamarin-forms-in-visual-studio.md).  
  
 È possibile usare tutte le funzionalità di Xamarin tramite [qualsiasi edizione di Visual Studio 2015](https://www.visualstudio.com/vs-2015-product-editions) (Community, Professional ed Enterprise). Tenere inoltre presente che a partire dal 31 marzo 2016, Xamarin è incluso in tutte le edizioni di Visual Studio 2015 e non richiede più una licenza distinta. Per Visual Studio 2013, è possibile installare Xamarin separatamente, come descritto nell'argomento [Configurazione e installazione](../cross-platform/setup-and-install.md).  
  
> [!NOTE]
>  Queste istruzioni descrivono la configurazione del computer più semplice e diretta per gli sviluppatori che hanno familiarità con Windows e Visual Studio. Con questa configurazione, l'esperienza di sviluppo complessiva viene semplificata poiché è sufficiente interagire con il Mac per l'uso del simulatore iOS e del dispositivo con tethering. Se invece si ha familiarità con l'ambiente Mac, è consigliabile eseguire Visual Studio in Parallels/VMWare oppure usare Xamarin Studio Community. Per istruzioni, vedere [Configurazione, installazione e verifiche per gli utenti Mac](../cross-platform/setup-install-and-verifications-for-mac-users.md).  
  
> [!NOTE]
>  Se si vuole una soluzione di sviluppo multipiattaforma basata su HTML e CSS, è disponibile Strumenti di Visual Studio per Apache Cordova, come descritto in [Sviluppo multipiattaforma in Visual Studio](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#HTML).