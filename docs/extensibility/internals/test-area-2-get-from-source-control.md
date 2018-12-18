---
title: 'Area di test 2: Ottenere dal controllo del codice sorgente | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, getting items from source control
- source control [Visual Studio SDK], getting items from
ms.assetid: cbd345c5-ca43-4630-b7a4-85564f4e2090
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a9ec7071a1e4ca78bb116c577cdcc77f9798c050
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="test-area-2-get-from-source-control"></a>Area di test 2: Ottenere dal controllo del codice sorgente
Questa area di test descrive i test case per il recupero di elementi dall'archivio delle versioni tramite il comando Get. Questi test case possono essere applicati a entrambi locale e per i progetti Web.  
  
## <a name="command-menu-access"></a>Accedere al Menu comando  
 Nell'esempio [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vengono utilizzati percorsi menu dell'ambiente di sviluppo integrato nei test case.  
  
##### <a name="get-latest-version"></a>Ottenere la versione più recente:  
  
-   **File**, **controllo del codice sorgente**, **Leggi ultima versione**.  
  
-   **File**, **Leggi ultima versione**.  
  
-   Menu di scelta rapida, **Leggi ultima versione**.  
  
-   Get: **File**, **controllo del codice sorgente**, **ottenere**.  
  
## <a name="expected-behavior"></a>Comportamento previsto  
  
##### <a name="get-latest-version"></a>Ottenere la versione più recente:  
 Esegue un recupero invisibile all'utente (senza interfaccia utente) della versione più recente dell'elemento dall'archivio delle versioni.  
  
##### <a name="get"></a>Ottieni:  
 Consente di visualizzare il **ottenere** la finestra di dialogo e consente all'utente di apportare modifiche al set di file che verrà recuperato, nonché modificare le opzioni che influiscono sul modo in cui vengono recuperati i file.  
  
## <a name="test-cases"></a>Test case  
  
|Operazione|Passi di test|Per verificare i risultati previsti|  
|------------|----------------|--------------------------------|  
|Ottenere la versione più recente di un file che non esiste in locale|1.  Creare un progetto.<br />2.  Aggiungere un elemento al progetto.<br />3.  Inserire il progetto nel controllo del codice sorgente.<br />4.  Eliminare la copia locale dell'elemento.<br />5.  Ottenere la versione più recente dell'elemento (Menu di scelta rapida, **Leggi ultima versione**).|File di elemento viene recuperato in locale.|  
|Ottenere un file che non esiste in locale|1.  Creare un progetto.<br />2.  Aggiungere un elemento al progetto.<br />3.  Inserire il progetto nel controllo del codice sorgente.<br />4.  Eliminare la copia locale dell'elemento.<br />5.  Ottenere l'elemento (**File**, **controllo del codice sorgente**, **ottenere** \<elemento >).|File di elemento viene recuperato in locale.|  
|Ottenere un file che è stato estratto in modo esclusivo e modificato localmente|1.  Creare un progetto.<br />2.  Aggiungere un elemento al progetto.<br />3.  Inserire il progetto nel controllo del codice sorgente.<br />4.  Estrae l'elemento del progetto in modo esclusivo.<br />5.  Modificare la copia locale.<br />6.  Ottenere la versione più recente dell'elemento (**File**, **Leggi ultima versione di** \<elemento >). Se questo passaggio ha esito positivo, andare al passaggio successivo.<br />7.  Fare clic su **sostituire** pulsante nella finestra di dialogo di avviso.|**ReResult al passaggio 6**`:`<br /><br /> La finestra di dialogo di avviso indica che il file è estratto.<br /><br /> **ReResult indicato nel passaggio 7:**<br /><br /> Il file locale modificato viene sostituito dalla versione originale dall'archivio versione.<br /><br /> File è di lettura/scrittura.|  
|Ottenere e sostituire i file estratti, condivisa e modificato localmente|1.  Creare un nuovo progetto.<br />2.  Aggiungere un elemento al progetto.<br />3.  Inserire il progetto nel controllo del codice sorgente.<br />4.  Estrarre l'elemento di progetto come condiviso.<br />5.  Modificare la copia locale.<br />6.  Ottenere la versione più recente dell'elemento (**File**, **Leggi ultima versione di** \<elemento >). Se questo passaggio ha esito positivo, andare al passaggio successivo.<br />7.  Fare clic su **sostituire** nella finestra di dialogo di avviso.|**Risultato del passaggio 6:**<br /><br /> La finestra di dialogo di avviso indica che il file è estratto.<br /><br /> **Risultato del passaggio 7:**<br /><br /> Il file locale modificato viene sostituito dalla versione originale dall'archivio versione.<br /><br /> File è di lettura/scrittura.|  
|Ottenere un file che esiste localmente, identica a quella più recente nell'archivio delle versioni|1.  Creare un nuovo progetto.<br />2.  Aggiungere un elemento al progetto.<br />3.  Inserire il progetto nel controllo del codice sorgente.<br />4.  Ottenere l'elemento (**File**, **controllo del codice sorgente**, **ottenere** \<elemento >).|File locale è stato modificato.|  
|Ottenere una soluzione con un unico progetto|1.  Creare una soluzione con un progetto.<br />2.  Inserire la soluzione nel controllo del codice sorgente.<br />3.  Eliminare tutti i file di progetto in locale.<br />4.  La soluzione (**File**, **controllo del codice sorgente**, **ottenere**).|Tutti i file eliminati vengono ripristinati in locale.|  
  
## <a name="see-also"></a>Vedere anche  
 [Guida per il test dei plug-in del controllo del codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)