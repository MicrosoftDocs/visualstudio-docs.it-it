---
title: Enumeratore dei messaggi | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bc945908ac61a0eaa4df49c76725b2291686eac3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="message-enumerator"></a>Enumeratore di messaggio
I flag seguenti vengono utilizzati per il `TEXTOUTPROC` funzione, che è una funzione di callback nell'IDE sono disponibili quando si chiama il [SccOpenProject](../extensibility/sccopenproject-function.md) (vedere [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) per informazioni dettagliate su callback funzione).  
  
 Se l'IDE viene richiesto di annullare il processo, è possibile ottenere uno dei messaggi di annullamento. In questo caso, il controllo origine plug-in utilizza `SCC_MSG_STARTCANCEL` per porre l'IDE per visualizzare il **Annulla** pulsante. Successivamente, è possibile inviare qualsiasi set di messaggi normali. Se uno di questi restituisce `SCC_MSG_RTN_CANCEL`, quindi il plug-in viene chiuso l'operazione e restituisce. Il plug-in anche esegue il polling `SCC_MSG_DOCANCEL` periodicamente per determinare se l'utente ha annullato l'operazione. Quando vengono eseguite tutte le operazioni o se l'utente ha annullato, il plug-in Invia `SCC_MSG_STOPCANCEL`. Il `SCC_MSG_INFO`, SCC_MSG_WARNING, e i tipi SCC_MSG_ERROR vengono utilizzati per i messaggi che viene visualizzati nell'elenco dei messaggi di scorrimento. `SCC_MSG_STATUS` è un tipo speciale che indica che il testo deve presentarsi in una barra di stato o l'area di visualizzazione temporaneo. Se non si desidera in modo permanente nell'elenco.  
  
## <a name="syntax"></a>Sintassi  
  
```  
enum {   
   SCC_MSG_RTN_CANCEL = -1,   
   SCC_MSG_RTN_OK = 0,   
   SCC_MSG_INFO = 1   
   SCC_MSG_WARNING,   
   SCC_MSG_ERROR,   
   SCC_MSG_STATUS,   
   SCC_MSG_DOCANCEL,   
   SCC_MSG_STARTCANCEL,   
   SCC_MSG_STOPCANCEL   
};  
```  
  
## <a name="members"></a>Membri  
 SCC_MSG_RTN_CANCEL  
 Restituito dal callback per indicare l'annullamento.  
  
 SCC_MSG_RTN_OK  
 Restituito dal callback di continuare.  
  
 SCC_MSG_INFO  
 Messaggio è puramente informativo.  
  
 SCC_MSG_WARNING  
 Messaggio è un avviso.  
  
 SCC_MSG_ERROR  
 Messaggio indica un errore.  
  
 SCC_MSG_STATUS  
 Messaggio è destinato a barra di stato.  
  
 SCC_MSG_DOCANCEL  
 Nessun testo. Restituisce IDE `SCC_MSG_RTN_OK` o `SCC_MSG_RTN_CANCEL`.  
  
 SCC_MSG_STARTCANCEL  
 Avvia un ciclo di annullamento.  
  
 SCC_MSG_STOPCANCEL  
 Arresta il ciclo di annullamento.  
  
## <a name="see-also"></a>Vedere anche  
 [Plug-in del controllo codice sorgente](../extensibility/source-control-plug-ins.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)