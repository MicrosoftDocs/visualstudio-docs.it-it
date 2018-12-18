---
title: 'Procedura: modificare il computer di riproduzione della diagnostica grafica | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 1b9aa3ea-29a0-4e21-bc57-936f33537b5c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 143ae65b8d7db584546c250bf5d032450bf220aa
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-change-the-graphics-diagnostics-playback-machine"></a>Procedura: modificare il computer di riproduzione della diagnostica della grafica
È possibile riprodurre le informazioni grafiche tramite il computer locale o tramite un dispositivo o computer remoto.  
  
## <a name="choosing-a-playback-machine"></a>Scelta di un computer di riproduzione  
 Il computer di riproduzione è un computer o dispositivo che viene utilizzato per riprodurre gli eventi di grafica da un log di grafica. In genere, il computer locale è l'opzione più semplice, ma un problema di rendering non è possibile riprodurre in un computer che dispone di hardware diverso o le versioni dei driver di computer in cui è stato acquisito; In questo caso, è possibile scegliere un computer di riproduzione remoto che riproduce meglio il problema e continua a usare il computer di sviluppo per diagnosticarlo.  
  
#### <a name="to-use-the-local-machine-to-play-back-graphics-information"></a>Utilizzare il computer locale per riprodurre le informazioni grafiche  
  
1.  Nella finestra del documento di Log di grafica, scegliere il **computer riproduzione** collegamento. Il **le connessioni Remote Debugger** viene visualizzata la finestra di dialogo.  
  
2.  In **configurazione manuale**nella **indirizzo** proprietà, immettere `localhost`.  
  
3.  Impostare il **modalità di autenticazione** proprietà **Nessuno**.  
  
4.  Scegliere il **selezionare** pulsante.  
  
#### <a name="to-use-a-remote-machine-to-play-back-graphics-information"></a>Per utilizzare un computer remoto per riprodurre le informazioni grafiche  
  
1.  Nella finestra del documento di Log di grafica, scegliere il **computer riproduzione** collegamento. Il **le connessioni Remote Debugger** viene visualizzata la finestra di dialogo.  
  
2.  In **configurazione manuale**nella **indirizzo** proprietà, immettere il nome di dominio Windows o l'indirizzo IP del computer o dispositivo che si desidera utilizzare per riprodurre le informazioni grafiche.  
  
3.  Specificare il tipo di autorizzazione che si desidera utilizzare per proteggere la connessione al computer di riproduzione.  
  
    -   Per l'autenticazione di Windows, impostare il **modalità di autenticazione** proprietà **Windows**.  
  
    -   Per nessuna autenticazione, impostare il **modalità di autenticazione** proprietà **Nessuno**.  
  
4.  Scegliere il **selezionare** pulsante.  
  
> [!NOTE]
>  Il **le connessioni Remote Debugger** la finestra di dialogo può inoltre essere visualizzate le destinazioni di debug remote direttamente connesse al computer di sviluppo o nella stessa subnet. È possibile utilizzare una di queste destinazioni di debug remote come computer di riproduzione della diagnostica della grafica senza configurarlo manualmente. Nel **le connessioni Remote Debugger** finestra di dialogo, selezionare la destinazione desiderata e quindi scegliere il **selezionare** pulsante.  
  
## <a name="see-also"></a>Vedere anche  
 [Documento di log della grafica](graphics-log-document.md)