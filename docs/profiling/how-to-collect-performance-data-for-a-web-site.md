---
title: 'Procedura: Raccogliere dati sulle prestazioni per un sito Web | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vsperf.url.url
- vsperf.chooseurl
- vs.performance.wizard.asppage
- vsperf.url.ok
- vsperf.url.cancel
helpviewer_keywords:
- Profiling Tools,profiling ASP.NET
- web sites, performance profiling
- ASP.NET, performance profilng
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: db9cefe31201a3b67ba176a56fed58bbe155bcf0
ms.sourcegitcommit: 36ab8429333b31f03992a9fe8fc669db8e09c968
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2018
---
# <a name="how-to-collect-performance-data-for-a-web-site"></a>Procedura: Raccogliere dati sulle prestazioni per un sito Web

Per raccogliere dati sulle prestazioni di un'applicazione Web di **, è possibile usare la** Creazione guidata sessione di prestazioni [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] . È possibile profilare un'applicazione Web aperta in Visual Studio oppure un sito Web di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] presente nel computer locale e non aperto nell'IDE di Visual Studio.

> [!NOTE]
> La **Creazione guidata sessione di prestazioni** consente di aggiungere dati di interazione tra livelli (TIP), dati relativi alle prestazioni di JScript o entrambi ai dati di profilatura raccolti. L'opzione TIP raccoglie dati dai processi sul lato server. L'opzione di profilatura JScript raccoglie dati da script in esecuzione in un sito Web locale o remoto. Nella maggior parte dei casi, è consigliabile scegliere solo una delle opzioni.

 In base alle autorizzazioni di accesso a livello utente che un amministratore ha reso disponibili, un singolo utente può avere o meno le autorizzazioni di sicurezza necessarie per creare una sessione del profiler sul computer che ospita il processo ASP.NET. Gli esempi seguenti illustrano le possibili differenze tra i diversi tipi di utenti:

- Se l'amministratore ha impostato l'avvio del driver e del servizio, è possibile che alcuni utenti abbiano accesso a funzionalità di profilatura avanzate,

- mentre gli utenti di dominio possano accedere soltanto ad esempi di profilatura.

- È possibile anche che alcuni utenti neghino l'accesso alle funzionalità di profilatura a tutti gli altri utenti.

 Per altre informazioni, vedere [Profilatura e sicurezza in Windows Vista](../profiling/profiling-and-windows-vista-security.md) e le opzioni ADMIN in [VSPerfCmd](../profiling/vsperfcmd.md).

## <a name="to-profile-a-web-site-project"></a>Per profilare un progetto di sito Web

1. Aprire il progetto Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] in Visual Studio.

2. Dal menu **Analizza** scegliere **Profiler prestazioni**, **Esplora prestazioni** e quindi selezionare **Avvia**.

3. Nella prima pagina della procedura guidata selezionare un metodo di profilatura e quindi fare clic su **Avanti**. Per altre informazioni sui metodi di profilatura, vedere [Informazioni sui metodi di raccolta delle prestazioni](../profiling/understanding-performance-collection-methods.md). Tenere presente che il metodo di profilatura del visualizzatore di concorrenza non è disponibile per le applicazioni Web.

4. Nell'elenco a discesa **Specificare l'applicazione di destinazione per la profilatura** verificare che il progetto corrente sia selezionato e quindi fare clic su **Avanti**.

5. Nella terza pagina della procedura guidata è possibile scegliere di aggiungere dati di profilatura dell'interazione tra livelli (TIP), dati da JavaScript in esecuzione nelle pagine Web o entrambi.

    - Per raccogliere dati di interazione tra livelli, selezionare la casella di controllo **Abilita profilatura interazione tra livelli** .

    - Per raccogliere dati da JavaScript in esecuzione nelle pagine Web, selezionare la casella di controllo **Profila JavaScript** .

6. Scegliere **Avanti**.

7. Nella quarta pagina della procedura guidata fare clic su **Fine**.

8. Verrà creata una sessione di prestazioni per l'applicazione di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] e il sito Web verrà avviato nel browser. Verificare la funzionalità che si vuole profilare e quindi chiudere il browser.

     Il profiler genera il file di dati e apre la visualizzazione Riepilogo dei dati nella finestra principale di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

## <a name="to-profile-a-web-site-without-opening-a-project-in-visual-studio"></a>Per profilare un sito Web senza aprire un progetto in Visual Studio

1. Aprire Visual Studio.

2. Dal menu **Analizza** scegliere **Profiler prestazioni**, **Esplora prestazioni** e quindi selezionare **Avvia**.

3. Nella prima pagina della procedura guidata selezionare un metodo di profilatura e quindi fare clic su **Avanti**. Per altre informazioni, vedere [Informazioni sui metodi di raccolta delle prestazioni](../profiling/understanding-performance-collection-methods.md).

4. Nella seconda pagina della procedura guidata, selezionare l'opzione **Profilatura di un'applicazione ASP.NET o JavaScript** e quindi fare clic su **Avanti**.

5. Nella terza pagina della procedura guidata digitare l'URL della home page dell'applicazione nella casella **Specificare l'URL o il percorso che esegue l'applicazione Web** e quindi fare clic su **Avanti**.

    - Per un sito Web basato su server (IIS), digitare un URL, ad esempio **http://localhost/MySite/default.aspx**. In questo modo verrà profilata l'applicazione [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] presente nel computer locale nella radice dell'applicazione di MySite e in Internet Explorer verrà aperta la pagina default.aspx del sito per avviare la sessione.

    - Per un sito Web basato su file, digitare un percorso, ad esempio file///**c:\WebSites\MySite\default.aspx**. In questo modo verrà profilata l'applicazione [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] presente in c:\webSites\MySite e in Internet Explorer verrà aperta la pagina http://localhost:nnnn/MySite/default.aspx per avviare la sessione.

    - Per i siti esterni sui quali si vuole raccogliere dati JavaScript, digitare l'URL, ad esempio http://www.contoso.com.

     Per altre informazioni, visualizzare le pagine delle proprietà per un file binario di destinazione [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] .

6. Nella terza pagina della procedura guidata è possibile scegliere di aggiungere dati di profilatura dell'interazione tra livelli (TIP), dati da JavaScript in esecuzione nelle pagine Web o entrambi.

    - Per raccogliere dati di interazione tra livelli, selezionare la casella di controllo **Abilita profilatura interazione tra livelli** .

    - Per raccogliere dati da JavaScript in esecuzione nelle pagine Web, selezionare la casella di controllo **Profila JavaScript** .

7. Scegliere **Avanti**.

8. Nella quarta pagina della procedura guidata fare clic su **Fine**.

9. Verrà creata una sessione di prestazioni per l'applicazione ASP.NET e il sito Web verrà avviato nel browser. Verificare la funzionalità che si vuole profilare e quindi chiudere il browser.

     Il profiler genera il file di dati e apre la visualizzazione Riepilogo dei dati nella finestra principale di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="see-also"></a>Vedere anche

[Panoramiche](../profiling/overviews-performance-tools.md)  
[Configurazione di sessioni di prestazioni](../profiling/configuring-performance-sessions.md)  
[Informazioni sui valori dei dati di strumentazione](../profiling/understanding-instrumentation-data-values.md)  
[Informazioni sui valori dei dati di campionamento](../profiling/understanding-sampling-data-values.md)
