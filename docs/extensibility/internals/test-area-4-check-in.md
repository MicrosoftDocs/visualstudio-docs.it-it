---
title: 'Area test 4: Controllare | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], checking items in
- source control plug-ins, checking items in
ms.assetid: d0329fa8-7a8d-4d30-b67b-6f2a97b75a30
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 698b46c7ccb0a3fb13c799349d36de0cadf80af1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="test-area-4-check-in"></a>Area test 4: Check-In
Questa area di plug-in test di controllo del codice sorgente include gli elementi aggiornati di invio all'archivio delle versioni tramite il **Archivia** comando.  
  
## <a name="command-menu-access"></a>Accedere al Menu comando  
 Nell'esempio [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vengono utilizzati percorsi menu dell'ambiente di sviluppo integrato nei test case.  
  
##### <a name="check-in"></a>Archiviare:  
 **File**, **controllo del codice sorgente**, **Archivia**.  
  
 **File**, **Archivia**.  
  
 Menu di scelta rapida, **Archivia**.  
  
## <a name="common-expected-behavior"></a>Comportamento previsto comune  
  
-   Progetti e file aggiunti a una soluzione o progetto incluso nel controllo del codice sorgente vengono visualizzati di **Archivia** la finestra di dialogo e **archiviazioni in sospeso** finestra.  
  
-   Dopo il check-in, gli elementi aggiunti vengono visualizzati nel controllo del codice sorgente.  
  
-   Dopo il check-in, gli elementi aggiornati sono correttamente con controllo delle versioni nell'archivio.  
  
## <a name="test-cases"></a>Test case  
 Di seguito sono specifici test case per l'area di test di archiviazione.  
  
### <a name="case-4a-modified-items"></a>Caso 4a: elementi modificati  
 Descrive l'utilizzo di controllo nell'azione per aggiornare un file di controllo del codice sorgente che è stato modificato.  
  
|Operazione|Passi di test|Per verificare i risultati previsti|  
|------------|----------------|--------------------------------|  
|Modificare un file di testo che è stato estratto, archiviare solo i file (**Archivia** la finestra di dialogo)|1.  Creare un nuovo progetto con un file di testo.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Estrarre e modificare il file di testo.<br />4.  Check-in tramite la finestra di dialogo Archivia (**File**, **controllo del codice sorgente**, **Archivia**).|Comportamento previsto comune.|  
|Modificare un file di testo che è stato estratto, archiviare solo i file (**archiviazioni in sospeso** finestra)|1.  Creare un nuovo progetto con un file di testo.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Estrarre e modificare il file di testo.<br />4.  Archiviare tramite il **archiviazioni in sospeso** finestra.|Comportamento previsto comune.|  
  
### <a name="case-4b-adding-files"></a>Caso 4b: aggiunta di file  
 Quando si aggiunge un file a un progetto o un elemento a una soluzione, necessario modificare anche il progetto o soluzione. In questo modo il file padre anche estratto e deve essere archiviato per completare l'aggiunta.  
  
|Operazione|Passi di test|Per verificare i risultati previsti|  
|------------|----------------|--------------------------------|  
|Aggiungere un file di testo e archivia i file (**Archivia** la finestra di dialogo)|1.  Creare un nuovo progetto.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Aggiungere un file di testo al progetto.<br />4.  Se richiesto, accettare check-out del progetto.<br />5.  Selezionare la soluzione in **Esplora**.<br />6.  Archivia dal **Archivia** la finestra di dialogo.|Comportamento previsto comune.|  
|Aggiungere un file di testo e archivia i file (**archiviazioni in sospeso** finestra)|1.  Creare un nuovo progetto.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Aggiungere un file di testo al progetto.<br />4.  Se richiesto, accettare check-out del progetto.<br />5.  Controllare nella soluzione da **archiviazioni in sospeso** finestra.|Comportamento previsto comune|  
  
### <a name="case-4c-adding-projects"></a>Caso c 4: aggiunta di progetti  
 Quando si aggiunge un progetto a una soluzione, necessario modificare anche la soluzione. In questo modo il file di soluzione inoltre estratto e deve essere archiviato per completare l'aggiunta.  
  
|Operazione|Passi di test|Per verificare i risultati previsti|  
|------------|----------------|--------------------------------|  
|Aggiungere un progetto a una soluzione vuota nel controllo del codice sorgente (**Archivia** la finestra di dialogo)|1.  Creare una soluzione vuota.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Aggiungere un nuovo progetto.<br />4.  Se richiesto, accettare check-out della soluzione.<br />5.  Archivia dal **Archivia** la finestra di dialogo.|Comportamento previsto comune.|  
|Aggiungere un progetto a una soluzione vuota nel controllo del codice sorgente (**archiviazioni in sospeso** finestra)|1.  Creare una soluzione vuota.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Aggiungere un nuovo progetto.<br />4.  Se richiesto, accettare check-out della soluzione.<br />5.  Controllare nella soluzione da **archiviazioni in sospeso** finestra.|Comportamento previsto comune.|  
  
## <a name="see-also"></a>Vedere anche  
 [Guida per il test dei plug-in del controllo del codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)