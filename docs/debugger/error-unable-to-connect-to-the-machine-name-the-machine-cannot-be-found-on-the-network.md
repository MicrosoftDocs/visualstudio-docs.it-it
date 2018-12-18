---
title: 'Errore: Impossibile connettersi alla macchina &lt;nome&gt;. Impossibile trovare il computer sulla rete. | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.remote.dcom_disabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- DCOM, unable to connect error
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3e0654148823d40277bdd9c6b6d8ec5b881fdb80
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
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