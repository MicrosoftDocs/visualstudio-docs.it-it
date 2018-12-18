---
title: Debug remoto in Visual Studio | Documenti Microsoft
ms.custom: remotedebugging
ms.date: 08/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: hero-article
f1_keywords: vs.debug.remote.overview
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords: remote debugging, setup
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
caps.latest.revision: "65"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 21867feae0d313c3ac5f93e51cf85ebe14bbba0b
ms.sourcegitcommit: 65f85389047c5a1938b6d5243ccba8d4f14362ba
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2018
---
# <a name="remote-debugging"></a>Remote Debugging
È possibile eseguire il debug di un'applicazione Visual Studio che è stata distribuita in un computer diverso. A questo scopo si usa Visual Studio Remote Debugger.

Per istruzioni dettagliate sul debug remoto, vedere gli argomenti.

|Scenario|Collegamento|
|-|-|-|
|Servizio app di Azure|[Snapshot Debugger](../debugger/debug-live-azure-applications.md) o [remoto di eseguire il debug ASP.NET in Azure](../debugger/remote-debugging-azure.md)|
|Macchina virtuale Azure|[Eseguire il debug remoto di ASP.NET in Azure](../debugger/remote-debugging-azure.md)|
|Azure Service Fabric|[Debug di un'applicazione Azure Service Fabric](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)|
|ASP.NET|[Eseguire il debug remoto ASP.NET Core](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md) o [ASP.NET di eseguire il Debug remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|In c# o Visual Basic|[Eseguire il debug remoto di un progetto C# o Visual Basic](../debugger/remote-debugging-csharp.md)|
|C++|[Eseguire il debug remoto di un progetto C++](../debugger/remote-debugging-cpp.md)|
|App di Windows universale (UWP)|[Eseguire App UWP in un computer remoto](../debugger/run-windows-store-apps-on-a-remote-machine.md) o [eseguire il Debug di un pacchetto dell'app installata](../debugger/debug-installed-app-package.md)|

Se sufficiente desidera scaricare e installare il debugger remoto e non necessario istruzioni aggiuntive per lo scenario, seguire i passaggi descritti in questo articolo.
  
## <a name="download-and-install-the-remote-tools"></a>Scaricare e installare remote tools  

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="fileshare_msvsmon"></a>(Facoltativo) Per eseguire il debugger remoto da una condivisione file

È possibile trovare il debugger remoto (**msvsmon.exe**) in un computer con Visual Studio Community, Professional o Enterprise già installato. Per alcuni scenari, il modo più semplice per configurare il debug remoto consiste nell'eseguire il debugger remoto (msvsmon.exe) da una condivisione file. Per le limitazioni di utilizzo, vedere pagina della Guida del debugger remoto (**Guida > utilizzo** nel debugger remoto).

1. Trovare **msvsmon.exe** nella directory corrispondente alla versione di Visual Studio. Per Visual Studio Enterprise 2017:

      **Programma file (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe**
      
      **Programma file (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe**

2. Condivisione di **Debugger remoto** cartella nel computer di Visual Studio.

3. Nel computer remoto, eseguire **msvsmon.exe**. Seguire il [istruzioni di installazione](#bkmk_setup).

> [!TIP] 
> Per l'installazione dalla riga di comando e di riferimento della riga di comando, vedere la pagina della Guida per **msvsmon.exe** digitando ``msvsmon.exe /?`` nella riga di comando nel computer con installato Visual Studio (o passare a **Guida > utilizzo**nel debugger remoto).
  
## <a name="requirements_msvsmon"></a> Requisiti

[!INCLUDE [remote-debugger-requirements](../debugger/includes/remote-debugger-requirements.md)]
  
## <a name="set-up-the-remote-debugger"></a>Configurare il debugger remoto  

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

### <a name="configure_msvsmon"></a>Configurare il debugger remoto  
È possibile modificare alcuni aspetti della configurazione del debugger remoto dopo che è stata avviata per la prima volta.
  
-   Se è necessario aggiungere le autorizzazioni per altri utenti per connettersi al debugger remoto, scegliere **strumenti > autorizzazioni**. È necessario avere privilegi di amministratore per concedere o negare autorizzazioni.

     > [!IMPORTANT] 
     > È possibile eseguire il debugger remoto con un account utente diverso dall'account utente in uso nel computer di Visual Studio, ma è necessario aggiungere l'account utente diverso alle autorizzazioni del debugger remoto. 

     In alternativa, è possibile avviare il debugger remoto dalla riga di comando con il **/Allow \<nome utente >** parametro: **msvsmon /Allow \< username@computer>**.
  
-   Se è necessario modificare la modalità di autenticazione o il numero di porta oppure specificare un valore di timeout per remote tools: scegliere **strumenti > Opzioni**.  
  
     Per un elenco dei numeri di porta utilizzati per impostazione predefinita, vedere [assegnazioni di porta del Debugger remoto](../debugger/remote-debugger-port-assignments.md).  
  
     > [!WARNING]
     >  È possibile scegliere di eseguire Remote Tools in modalità Nessuna autenticazione che, tuttavia, è fortemente sconsigliata perché priva di qualsiasi sicurezza di rete. Scegliere la modalità Nessuna autenticazione solo se si ha la certezza che la rete non è soggetta a rischi derivanti da traffico ostile o dannoso.

##  <a name="bkmk_configureService"></a>(Facoltativo) Configurare il debugger remoto come servizio
Per il debug in ASP.NET e altri ambienti server, è necessario eseguire il debugger remoto come amministratore o, se si desidera sempre in esecuzione, eseguire il debugger remoto come servizio.
  
 Se si desidera configurare il debugger remoto come servizio, seguire questi passaggi.  
  
1.  Trovare la **Configurazione guidata del debugger remoto** (rdbgwiz.exe). Si tratta di un'applicazione separata dal debugger remoto. È disponibile solo quando si installa Remote Tools e non è inclusa nell'installazione di Visual Studio.  
  
2.  Avviare la configurazione guidata. Quando viene visualizzata la prima pagina, fare clic su **Avanti**.  
  
3.  Selezionare la casella di controllo **Esegui Visual Studio 2015 Remote Debugger come servizio** .  
  
4.  Aggiungere il nome dell'account utente e la password.  
  
     Potrebbe essere necessario aggiungere il **accedere come servizio** diritto utente di questo account (trovare **criteri di sicurezza locali** (secpol.msc) nei **avviare** pagina o nella finestra (o tipo  **secpol** un prompt dei comandi). Quando viene visualizzata la finestra, fare doppio clic su **Assegnazione diritti utente**e trovare **Accedi come servizio** nel riquadro di destra. Fare doppio clic. Aggiungere l'account utente per il **proprietà** finestra e fare clic su **OK**). Scegliere **Avanti**.  
  
5.  Selezionare il tipo di rete con cui si vuole che Remote Tools comunichi. Almeno un tipo di rete deve essere selezionato. Se i computer sono connessi tramite un dominio, è necessario scegliere il primo elemento. Se i computer sono connessi tramite un gruppo di lavoro o un gruppo home, è necessario scegliere il secondo o il terzo elemento. Scegliere **Avanti**.  
  
6.  Se è possibile avviare il servizio, viene visualizzato il messaggio **Configurazione guidata di Visual Studio Remote Debugger completata**. Se non è possibile avviare il servizio, viene visualizzato il messaggio **Impossibile completare la Configurazione guidata di Visual Studio Remote Debugger**. La pagina offre anche alcuni suggerimenti da seguire per l'avvio del servizio.  
  
7.  Scegliere **Fine**.  
  
 A questo punto il debugger remoto è in esecuzione come servizio. È possibile verificare questa passando a **Pannello di controllo > servizi** e cercando **Visual Studio 2015 Remote Debugger**.  
  
 È possibile arrestare e avviare il servizio debugger remoto da **Pannello di controllo > servizi**.

## <a name="set-up-debugging-with-remote-symbols"></a>Configurare il debug con simboli remoti 

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]
  
## <a name="see-also"></a>Vedere anche  
 [Debugger Feature Tour](../debugger/debugger-feature-tour.md)  (Tour delle funzionalità del debugger)  
 [Configurare Windows Firewall per debug remoto](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Assegnazioni di porta del Debugger remoto](../debugger/remote-debugger-port-assignments.md)   
 [Il debug di ASP.NET Core in un Computer remoto con IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)  
 [Errori e risoluzione dei problemi relativi al debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)
