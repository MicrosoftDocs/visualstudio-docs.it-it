---
title: 'Procedura: Profilare codice JavaScript nelle pagine Web | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- JavaScript performance profiling
- Profiling Tools,JavaScript
- web site performance profiling
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7da608523430724e279efc3d5c7c5d5b27564845
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-profile-javascript-code-in-web-pages"></a>Procedura: Profilare codice JavaScript nelle pagine Web

Gli strumenti di profilatura di Visual Studio possono raccogliere dati sulle prestazioni per il codice JavaScript eseguito in un'applicazione Web di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], in una pagina Web arbitraria o in un'applicazione JavaScript usando il metodo di profilatura della strumentazione. Richiede Internet Explorer 8 o versioni successive.

> [!WARNING]
> Per profilare il codice Ja0vaScript nelle app UWP, vedere [Memoria JavaScript](../profiling/javascript-memory.md) 

È possibile usare la procedura guidata di profilatura per creare una sessione di prestazioni. Specificare il metodo di strumentazione, quindi specificare l'opzione di profilatura JavaScript nella pagina Strumentazione della finestra di dialogo delle proprietà per la sessione di prestazioni.

Quando si specifica la profilatura JavaScript, questa viene applicata sia al codice JavaScript eseguito nel browser che al codice [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] eseguito nel server.

- Per un'applicazione Web di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] , la profilatura viene applicata sia al codice JavaScript eseguito nel browser che al codice [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] eseguito nel server.

- Per una pagina Web arbitraria, la profilatura viene applicata al codice JavaScript eseguito nel browser.

## <a name="to-profile-javascript-in-an-aspnet-web-application-project"></a>Per eseguire la profilatura di JavaScript in un progetto dell'applicazione Web ASP.NET

1. Aprire il progetto Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] in Visual Studio.

2. Nel menu **Analizza** fare clic su **Avvia Creazione guidata sessione di prestazioni**.

3. Nella prima pagina della procedura guidata, specificare il metodo di profilatura **Strumentazione** , quindi fare clic su **Avanti**.

4. Nella seconda pagina della procedura guidata, assicurarsi che il progetto corrente sia selezionato nell'elenco delle destinazioni, quindi fare clic su **Avanti**.

5. Nella terza pagina della procedura guidata, selezionare la casella di controllo **Profilo JavaScript** , quindi fare clic su **Avanti**.

6. Nella quarta pagina della procedura guidata, fare clic su **Fine** per avviare l'applicazione Web nel browser.

7. Verificare la funzionalità di cui eseguire la profilatura.

8. Per terminare la sessione di profilatura, chiudere il browser.

### <a name="to-profile-javascript-in-individual-web-pages-or-a-javascript-applications"></a>Per eseguire la profilatura del codice JavaScript in singole pagine Web o in applicazioni JavaScript

1. Aprire Visual Studio.

2. Nel menu **Analizza** fare clic su **Avvia Creazione guidata sessione di prestazioni**.

3. Nella prima pagina della procedura guidata, specificare il metodo di profilatura **Strumentazione** , quindi fare clic su **Avanti**.

4. Nella seconda pagina della procedura guidata, fare clic su un'applicazione ASP.NET o JavaScript, quindi fare clic su **Avanti**.

5. Nella terza pagina della procedura guidata:

    1. Digitare l'URL della pagina nella casella **Specificare l'URL o il percorso che esegue l'applicazione Web** .

    2. Selezionare la casella di controllo **Profilo JavaScript** , quindi fare clic su **Avanti**.

6. Nella quarta pagina della procedura guidata, fare clic su **Fine** per avviare la pagina Web nel browser.

7. Verificare la funzionalità di cui eseguire la profilatura.

8. Per terminare la sessione di profilatura, chiudere il browser.