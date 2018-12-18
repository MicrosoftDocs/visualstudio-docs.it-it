---
title: Sviluppare app per la piattaforma UWP (Universal Windows Platform) | Microsoft Docs
ms.custom: 
ms.date: 10/24/2017
ms.reviewer: 
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eac59cb6-f12e-4a77-9953-6d62b164a643
caps.latest.revision: "48"
author: stevehoag
ms.author: shoag
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: a696a0b827cc8fe367390efbba01c2a18ff178bb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="develop-apps-for-the-universal-windows-platform-uwp"></a>Sviluppare app per la piattaforma UWP (Universal Windows Platform)
Con la piattaforma UWP (Universal Windows Platform) e uno dei nostri core Windows, è possibile eseguire la stessa app su qualsiasi dispositivo Windows 10, dai telefoni ai desktop. È possibile creare queste app di Windows universale usando Visual Studio e gli strumenti di sviluppo di app di Windows universale.  
  
 ![Piattaforma UWP](../cross-platform/media/uwp_coreextensions.png "UWP_CoreExtensions")  
  
 È possibile eseguire le app su telefoni Windows 10, computer desktop Windows 10 o Xbox. Il pacchetto di app non cambia. Con l'introduzione del singolo core unificato Windows 10, un unico pacchetto di app può essere eseguito su tutte le piattaforme. Diverse piattaforme hanno SDK di estensione che è possibile aggiungere all'app per sfruttare i comportamenti specifici di piattaforma. Ad esempio, un SDK di estensione per dispositivi mobili gestisce la pressione del pulsante Indietro su un telefono Windows. Se si fa riferimento a un SDK di estensione nel progetto, è sufficiente aggiungere i controlli di runtime per verificare se tale SDK sia disponibile nella piattaforma. In questo modo è possibile avere lo stesso pacchetto di app per ogni piattaforma.  
  
 **Che cos'è il core Windows?**  
  
 Per la prima volta, è stato eseguito il refactoring di Windows per avere a disposizione un core comune a tutte le piattaforme Windows 10. Esiste una sola origine comune, un unico kernel di Windows comune, un unico stack I/O di file e un solo modello di applicazione. Per l'interfaccia utente, esiste un unico framework dell'interfaccia utente XAML e un unico framework dell'interfaccia utente HTML. L'esecuzione delle app su diversi dispositivi Windows 10 è stata semplificata per consentire di concentrarsi sulla creazione di app eccezionali.  
  
 **Che cos'è esattamente la piattaforma UWP (Universal Windows Platform)?**  
  
La piattaforma UWP (Universal Windows Platform) è semplicemente una raccolta di contratti e versioni che consente di scegliere la destinazione in cui eseguire l'app. La destinazione non è più un sistema operativo, ma una o più famiglie di dispositivi. Per altre informazioni, vedere [Introduzione alla piattaforma UWP (Universal Windows Platform)](/windows/uwp/get-started/universal-application-platform-guide).  
  
## <a name="requirements"></a>Requisiti  
 Gli strumenti di sviluppo di UWP (Universal Windows Platform) sono dotati di emulatori che consentono di visualizzare l'aspetto dell'app in dispositivi diversi. Per usare gli emulatori, è necessario installare questo software in un computer fisico in cui sia in esecuzione Windows 8.1 (x64) Professional o versioni successive e dotato di un processore che supporti Client Hyper-V e Second Level Address Translation (SLAT). Non è possibile eseguire gli emulatori quando Visual Studio è installato in una macchina virtuale.  
  
 Elenco del software necessario:  
  
-   [Windows 10](http://windows.microsoft.com/windows/downloads). Visual Studio 2017 supporta lo sviluppo UWP solo in Windows 10. Per altre informazioni, vedere [Selezione della piattaforma](https://www.visualstudio.com/productinfo/vs2017-compatibility-vs) e [Requisiti di sistema](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs) di Visual Studio.   
  
-   [Visual Studio](https://www.visualstudio.com/downloads/). Sarà anche necessario il carico di lavoro di sviluppo della piattaforma UWP (Universal Windows Platform).  

     ![Carico di lavoro UWP (Universal Windows Platform)](media/uwp_workload.png)
  
Dopo aver installato il software, è necessario abilitare il dispositivo Windows 10 per lo sviluppo. Vedere [Abilitare il dispositivo per lo sviluppo](/windows/uwp/get-started/enable-your-device-for-development). Non è più necessaria una licenza per sviluppatori per ogni dispositivo Windows 10.  
    
## <a name="universal-windows-apps"></a>App di Windows universale  
Scegliere il linguaggio di sviluppo preferito tra C#, Visual Basic, C++ o JavaScript per creare un'app della piattaforma UWP per dispositivi Windows 10. Vedere [Creare la prima app](/windows/uwp/get-started/your-first-app) o guardare il video [Tools for Windows 10 Overview](http://channel9.msdn.com/Series/ConnectOn-Demand/229) (Panoramica degli strumenti per Windows 10).
  
Se si hanno app di Windows Store 8.1 o Windows Phone 8.1 oppure app di Windows universale create con Visual Studio 2015, sarà necessario trasferire tali app per usare la versione più recente della piattaforma UWP (Universal Windows Platform). Vedere [Passare da Windows Runtime 8.x a UWP](/windows/uwp/porting/w8x-to-uwp-root).
  
Dopo aver creato l'app di Windows universale, è necessario creare un pacchetto dell'app per installarla in un dispositivo Windows 10 o inviarla a Windows Store. Vedere [Creazione di pacchetti delle app](/windows/uwp/packaging/index).

## <a name="see-also"></a>Vedere anche
[Sviluppo di app per dispositivi mobili multipiattaforma in Visual Studio](../cross-platform/cross-platform-mobile-development-in-visual-studio.md)  
