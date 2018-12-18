---
title: 'Errore: Impossibile connettersi alla macchina &lt;nome&gt;. Impossibile trovare il computer sulla rete. | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vs.debug.remote.dcom_disabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords: DCOM, unable to connect error
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e8b7ef99717f0a68fbd17245958840c89cdf8544
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="error-unable-to-connect-to-the-machine-ltnamegt-the-machine-cannot-be-found-on-the-network"></a>Errore: Impossibile connettersi alla macchina &lt;nome&gt;. Impossibile trovare il computer sulla rete.
Questo messaggio di errore viene visualizzato quando si verifica una delle seguenti condizioni:  
  
-   La connessione stabilita al computer remoto è stata interrotta.  
  
-   L'account utente utilizzato per la connessione al computer remoto è stato disabilitato.  
  
-   La password utilizzata per la connessione al computer remoto è scaduta.  
  
### <a name="to-resolve-this-behavior"></a>Per risolvere questo comportamento  
  
-   Assicurarsi che il computer locale e il computer remoto si trovino nella stessa rete. A tale scopo, utilizzare Esplora risorse o Esplora file per tentare di accedere al computer remoto.  
  
     - e -  
  
-   Assicurarsi che l'account utente utilizzato per la connessione al computer remoto sia attivato.  
  
     - e -  
  
-   Assicurarsi che la password utilizzata per la connessione al computer remoto sia valida e non scaduta.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug remoto](../debugger/remote-debugging.md)   
 [Impostazioni di debug e preparazione](../debugger/debugger-settings-and-preparation.md)