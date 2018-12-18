---
title: Informazioni sullo sviluppo per dispositivi mobili con Xamarin | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2018
ms.topic: conceptual
ms.assetid: e970d936-1df4-4c0c-96e3-ef6191295882
ms.technology: vs-ide-mobile
author: ghogen
ms.author: ghogen
manager: douge
ms.workload:
- xamarin
ms.openlocfilehash: 9a174c8712f4ca9151fc30ddd357f53cec2891cf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="learn-about-mobile-development-with-xamarin"></a>Altre informazioni sullo sviluppo per dispositivi mobili con Xamarin

Questo articolo elenca diversi articoli di panoramica che possono essere d'aiuto per comprendere come sviluppare app per dispositivi mobili multipiattaforma con Xamarin. Se Visual Studio e Xamarin non sono ancora stati installati, avviare innanzitutto il processo [Configurazione e installazione](../cross-platform/setup-and-install.md) , quindi tornare qui per consultare queste risorse mentre i programmi di installazione sono in esecuzione.  
  
> [!NOTE]
> Se non diversamente specificato, inizialmente è consigliabile leggere solo le pagine a cui questo articolo è collegato direttamente, evitando le pagine secondarie. Se il processo di installazione è ancora in esecuzione dopo aver completato questo elenco, è possibile tornare indietro ed esplorare argomenti aggiuntivi.  
>   
> È anche possibile leggere gli argomenti contrassegnati come "Concetti di base" e tornare agli argomenti "Approfondimento" più avanti.  
  
## <a name="essentials-introduction-to-xamarin"></a>Concetti di base: Introduzione a Xamarin  

*10-20 minuti*  
  
1.  [App per dispositivi mobili in Visual Studio con Xamarin](https://www.visualstudio.com/xamarin/) (visualstudio.com) fornisce un breve resoconto delle caratteristiche principali di Xamarin.  
  
2.  [Creazione di app per dispositivi mobili multipiattaforma con C# e Visual Studio](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2015-Final-Release-Event/Building-cross-platform-mobile-apps-using-C-and-Visual-Studio-2015) (Channel 9, 15 minuti e 16 secondi) con l'esperto di Xamarin James Montemagno. I primi tre minuti offrono una panoramica di Xamarin, seguita da dimostrazioni di codice.  
  
## <a name="essentials-overview-of-the-visual-studio-and-xamarin-environment"></a>Concetti di base: Panoramica dell'ambiente Visual Studio e Xamarin  

*5-15 minuti*  
  
-   La maggior parte del lavoro verrà eseguita nel computer Windows in cui sono installati Visual Studio e Xamarin. In questo computer verranno direttamente create le app Windows e Android, che saranno quindi eseguite e di cui sarà effettuato il debug nel desktop,nei dispositivi o negli emulatori. È anche possibile compilare, eseguire ed effettuare il debug di app iOS in modalità remota tramite il Mac. Visual Studio nel computer Windows può anche connettersi alla finestra di progettazione dello storyboard e al simulatore iOS.  
  
-   Il Mac in cui sono installati Xcode e Visual Studio per Mac funge da host di compilazione e di firma, nonché da ambiente di runtime per le app iOS. Il computer Windows delega le build iOS a questo Mac. L'applicazione viene eseguita in un simulatore iOS nel Mac o direttamente in un dispositivo con tethering connesso al Mac. È possibile interagire con l'app nel Mac, conducendo l'esperienza di debug in Visual Studio.
  
Queste relazioni sono illustrate di seguito.  
  
![Relazione tra computer di sviluppo Windows e Mac in un ambiente Xamarin](../cross-platform/media/crossplat-xamarin-learn-1.png "CrossPlat Xamarin Learn 1")  

> [!NOTE]
> Windows Phone è illustrato in questo diagramma per motivi di completezza. Quando si usa la piattaforma Xamarin, l'opzione di condivisione del codice consigliata è una libreria .NET Standard 2.0, che non è compatibile con i dispositivi Windows Phone o Windows 10 Mobile. 

Altre informazioni sull'uso delle app iOS sono disponibili in [Introduzione a Xamarin.iOS per Visual Studio](/xamarin/ios/get-started/installation/windows/introduction-to-xamarin-ios-for-visual-studio/).
  
## <a name="essentials-how-projects-are-structured"></a>Concetti di base: Come sono strutturati i progetti  

*10-30 minuti*  
  
1.  [Opzioni di condivisione del codice](/xamarin/cross-platform/app-fundamentals/code-sharing/). Per le nuove applicazioni, è consigliabile condividere codice tramite una libreria .NET Standard. La maggior parte del codice relativo alla logica di business si troverà nella libreria .NET Standard, incluso l'accesso ai database, le chiamate alle API REST e le chiamate ai componenti di Xamarin portatili. Vedere [Approfondimento: componenti di Xamarin](#components) alla fine di questo articolo. Anche il codice dell'interfaccia utente comune scritto con Xamarin.Forms risiede in una libreria .NET Standard.  
  
2.  (Facoltativo) Il [case study relativo a Tasky](/xamarin/cross-platform/app-fundamentals/building-cross-platform-applications/case-study-tasky/) descrive alcune procedure consigliate per la progettazione e la struttura di un'app completa. Descrive ad esempio come strutturare il progetto con codice condiviso che separa il livello dati, il livello di accesso ai dati e il livello business.  
  
## <a name="essentials-native-and-xamarinforms-ui-layers"></a>Concetti di base: Livelli dell'interfaccia utente Xamarin Native e Xamarin.Forms  

*10-40 minuti*  
  
Xamarin offre due metodi per creare app di alto livello: Xamarin Native e Xamarin.Forms.  
  
Con Xamarin Native occorre scrivere codice separato per l'interfaccia utente per ogni piattaforma di destinazione: iOS, Android e Windows.  Con questo approccio è possibile accedere direttamente alle API specifiche della piattaforma e progettare così un'esperienza di interfaccia utente personalizzata per ogni piattaforma.  È anche disponibile l'accesso completo alle finestre di progettazione e ai controlli nativi per ogni piattaforma, per facilitare la creazione dell'interfaccia utente corrispondente.  
  
Xamarin.Forms offre un set di API generalizzato che consente di scrivere un livello di interfaccia utente condiviso per tutte le piattaforme in una libreria .NET Standard.  Xamarin.Forms prevede il rendering in controlli nativi in ciascuna piattaforma di destinazione per offrire un aspetto originale.  Anziché usare una finestra di progettazione, l'interfaccia utente viene creata mediante C# e XAML.  

La maggior parte degli sviluppatori usa Xamarin.Forms. Si tratta del percorso consigliato per gli sviluppatori che devono acquisire familiarità con Xamarin. L'approccio Xamarin Native è più complesso e richiede una conoscenza più dettagliata delle piattaforme di destinazione.
  
Non è necessario decidere in anticipo quale approccio adottare. Le app possono essere implementate usando una combinazione di Xamarin Native e Xamarin.Forms:  
  
-   Usare Xamarin.Forms per creare schermate per uso generico, che offrono un'interfaccia utente e funzionalità simili in tutte le piattaforme, come le schermate di accesso, i moduli di contatto e i risultati di ricerca.  
  
-   Xamarin.Forms consente anche di usare un'ampia gamma di funzionalità di personalizzazione per adattare l'interfaccia utente a ogni piattaforma. L'opzione di personalizzazione più semplice prevede l'API `OnPlatform`. È anche possibile creare visualizzazioni personalizzate, estendere renderer esistenti e creare renderer personalizzati.  
  
-   Se necessario, è possibile usare Xamarin Native per creare schermate che usano funzionalità dell'interfaccia utente esclusive di ogni piattaforma. Un esempio può essere una schermata che usa funzioni native di acquisizione di immagini con una fotocamera e funzioni di modifica delle immagini.  
  
È in genere consigliabile iniziare con una soluzione Xamarin.Forms per configurare la condivisione del codice dell'interfaccia utente tra le piattaforme. Usare quindi le funzionalità di personalizzazione per eseguire modifiche specifiche per ogni piattaforma. Se e quando è necessario creare schermate interamente specifiche della piattaforma, è possibile aggiungerle singolarmente tramite Xamarin Native.  
  
Per altre informazioni:  
  
1.  [Xamarin.Forms](/xamarin/xamarin-forms/) fornisce una breve panoramica e informazioni sui vantaggi e gli svantaggi di Xamarin.Forms rispetto ai livelli dell'interfaccia utente nativa (ovvero Xamarin.iOS e Xamarin.Android).  
  
2.  I primi tre minuti del video di James Montemagno su [Xamarin.Forms: app native iOS, Android e Windows con C# e XAML](https://channel9.msdn.com/events/Visual-Studio/Connect-event-2015/704) (Channel9, 13 minuti e 3 secondi) offrono un'altra panoramica e alcune demo.  
  
3.  (Facoltativo) [Introduzione a Xamarin.Forms](/xamarin/xamarin-forms/get-started/introduction-to-xamarin-forms/)  
  
4.  (Facoltativo) Vedere alcuni esempi di uso di `OnPlatform` per la personalizzazione nella documentazione relativa alla [classe Device](/xamarin/xamarin-forms/platform/device/)
  
5.  (Facoltativo) L'articolo [Cross-Platform - Share UI Code Across Mobile Platforms with Xamarin.Forms](https://msdn.microsoft.com/magazine/dn904669.aspx) (Sviluppo multipiattaforma - Condividere codice di interfaccia utente tra più piattaforme per dispositivi mobili con Xamarin.Forms) di Jason Smith (MSDN Magazine) presenta le diverse opzioni di personalizzazione disponibili in Xamarin.Forms. I dettagli sono disponibili in [Renderer personalizzati](/xamarin/xamarin-forms/app-fundamentals/custom-renderer/).  
  
## <a name="deeper-dive-debugging-with-emulators"></a>Approfondimento: Debug con gli emulatori  

*10-15 minuti*  
  
Per eseguire il debug di app multipiattaforma senza dover usare un dispositivo fisico, saranno necessari gli emulatori descritti qui:  
  
### <a name="microsofts-android-emulator"></a>Emulatore Android di Microsoft 

È consigliabile usare Microsoft [Visual Studio Emulator for Android](~/cross-platform/visual-studio-emulator-for-android.md), installato con Visual Studio.  Il video dedicato a [Visual Studio Emulator for Android](https://channel9.msdn.com/events/Visual-Studio/Connect-event-2015/711) (Channel 9, 5 minuti e 55 secondi) offre una panoramica e una dimostrazione.  
  
### <a name="apples-ios-simulator"></a>Simulatore iOS di Apple

Per altre informazioni, leggere l' [introduzione al simulatore iOS](https://developer.apple.com/library/prerelease/content/documentation/IDEs/Conceptual/iOS_Simulator_Guide/GettingStartedwithiOSSimulator/GettingStartedwithiOSSimulator.html#//apple_ref/doc/uid/TP40012848-CH5-SW1) (apple.com).  
  
### <a name="microsofts-windows-phone-emulator"></a>Emulatore Windows Phone di Microsoft.

Per altre informazioni, leggere [Test with the Microsoft Emulator for Windows 10 Mobile](/windows-uwp/windows-apps-src/debug-test-perf/test-with-the-emulator/) (Test con l'emulatore di Microsoft per Windows 10 Mobile).  
  
<a name="components" /> 

## <a name="deeper-dive-xamarin-components"></a>Deeper Dive: Xamarin Components  

*10 minuti*  
  
Numerose funzionalità estese sono disponibili per le app Xamarin mediante i componenti di Xamarin. All'indirizzo [http://components.xamarin.com/](http://components.xamarin.com/) è disponibile per il download il catalogo completo, che include i componenti per controlli aggiuntivi dell'interfaccia utente e per l'autenticazione, oltre a un'ampia gamma di servizi cloud come Microsoft Azure e molto altro ancora.