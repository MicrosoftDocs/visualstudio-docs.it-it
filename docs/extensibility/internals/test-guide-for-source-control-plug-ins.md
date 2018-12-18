---
title: Guida per i Plug-in del controllo origine test | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- plug-ins, source control
- source control [Visual Studio SDK], testing plug-ins
- tests, source control plug-ins
- testing, source control plug-ins
- source control plug-ins, test guide
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
caps.latest.revision: "26"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0fdab6cb0b259fe169a9ebd43c92158a5ce20d4b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="test-guide-for-source-control-plug-ins"></a>Guida per i test per i Plug-in del controllo codice sorgente
In questa sezione vengono fornite indicazioni per il test di controllo del codice sorgente plug-in con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Viene fornita una panoramica completa delle aree più comuni di test, nonché alcune delle aree più complesse che possono causare problemi. Questa panoramica non intende essere un elenco completo dei test case.  
  
> [!NOTE]
>  Alcune correzioni di bug e miglioramenti per la versione più recente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE può rivelare problemi esistenti origine plug-in del controllo che sono stati precedentemente non rilevato durante l'utilizzo di versioni precedenti di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. È consigliabile testare il controllo del codice sorgente esistente plug-in per le aree enumerate in questa sezione, anche se non sono state apportate modifiche al plug-in dalla versione precedente di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="common-preparation"></a>Preparazione comune  
 Un computer con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e il controllo del codice sorgente destinazione plug-in installato, è necessario. Per alcuni di apertura dal controllo del codice sorgente test, è possibile utilizzare un secondo computer configurato in modo analogo.  
  
## <a name="definition-of-terms"></a>Definizione dei termini  
 Ai fini di questa guida per i test, utilizzare le definizioni di termini seguenti:  
  
 Progetto client  
 Qualsiasi progetto di tipo disponibile in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] che supporta l'integrazione del controllo codice sorgente (ad esempio, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], o [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]).  
  
 Progetto Web  
 Sono disponibili quattro tipi di progetti Web: File System, IIS locale, siti remoti e FTP.  
  
-   File System progetti vengono creati in un percorso locale, ma non richiedono Internet Information Services (IIS) sia installato in quanto sono accessibili internamente tramite un percorso UNC e può essere inserite sotto il controllo del codice sorgente all'interno dell'IDE, analogamente a progetti client.  
  
-   Progetti IIS locali funzionano con IIS è installato nello stesso computer e si accede con un URL che punta al computer locale.  
  
-   Progetti di siti remoti vengono creati anche in un servizio di IIS, ma vengono inseriti nel controllo del codice sorgente nel computer server IIS e non da all'interno di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
-   Progetti FTP si accede tramite un server FTP remoto ma non può essere inseriti nel controllo del codice sorgente.  
  
 Integrazione di  
 Un altro termine per la soluzione o progetto incluso nel controllo del codice sorgente.  
  
 Archivio versioni  
 Il database di controllo di origine che si accede tramite l'API plug-in controllo di origine.  
  
## <a name="test-areas-covered-in-this-section"></a>Test delle aree trattate in questa sezione  
  
-   [Area di test 1: Aggiungere a / Apri dal controllo del codice sorgente](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)  
  
    -   Caso 1a: Aggiungi soluzione al controllo del codice sorgente  
  
    -   Caso 1b: aprire soluzioni dal controllo del codice sorgente  
  
    -   Caso c 1: aggiungere una soluzione dal controllo del codice sorgente  
  
-   [Area di test 2: Recuperare elementi dal controllo del codice sorgente](../../extensibility/internals/test-area-2-get-from-source-control.md)  
  
-   [Area test 3: Estrarre / Annulla estrazione](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)  
  
    -   Caso 3: Estrarre / Annulla estrazione  
  
    -   Caso 3: Check-Out  
  
    -   Caso 3b: disconnesso estrazione  
  
    -   Caso 3c: Query o modifica Query salvare (QEQS)  
  
    -   Caso 3d: Estrazione invisibile all'utente  
  
    -   Caso 3e: Annulla estrazione  
  
-   [Area di test 4: Archiviare](../../extensibility/internals/test-area-4-check-in.md)  
  
    -   Caso 4a: elementi modificati  
  
    -   Caso 4b: aggiunta di file  
  
    -   Caso c 4: aggiunta di progetti  
  
-   [Area di test 5: Modificare il controllo del codice sorgente](../../extensibility/internals/test-area-5-change-source-control.md)  
  
    -   Caso 5a: associazione  
  
    -   Caso 5b: separare  
  
    -   Caso 5C: Rebind  
  
-   [Area di test 6: Eliminare](../../extensibility/internals/test-area-6-delete.md)  
  
-   [Area di test 7: Condividere](../../extensibility/internals/test-area-7-share.md)  
  
-   [Area di test 8: Cambio di plug-in](../../extensibility/internals/test-area-8-plug-in-switching.md)  
  
    -   Caso 8a: delle modifiche automatico  
  
    -   Caso 8 b: modifica basati su una soluzione  
  
## <a name="see-also"></a>Vedere anche  
 [Plug-in del controllo del codice sorgente](../../extensibility/source-control-plug-ins.md)