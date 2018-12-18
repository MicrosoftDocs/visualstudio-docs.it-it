---
title: Enumeratore dei messaggi | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 6a24db9c50bd298f068c23af0b6bad5755ec252d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="message-enumerator"></a>Enumeratore di messaggio
I flag seguenti vengono utilizzati per il `TEXTOUTPROC` funzione, che è una funzione di callback nell'IDE sono disponibili quando si chiama il [SccOpenProject](../extensibility/sccopenproject-function.md) (vedere [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) per informazioni dettagliate su callback funzione).  
  
 Se l'IDE viene richiesto di annullare il processo, è possibile ottenere uno dei messaggi di annullamento. In questo caso, il controllo origine plug-in utilizza `SCC_MSG_STARTCANCEL` per porre l'IDE per visualizzare il **Annulla** pulsante. Successivamente, è possibile inviare qualsiasi set di messaggi normali. Se uno di questi restituisce `SCC_MSG_RTN_CANCEL`, quindi il plug-in viene chiuso l'operazione e restituisce. Il plug-in anche esegue il polling `SCC_MSG_DOCANCEL` periodicamente per determinare se l'utente ha annullato l'operazione. Quando vengono eseguite tutte le operazioni o se l'utente ha annullato, il plug-in Invia `SCC_MSG_STOPCANCEL`. Il `SCC_MSG_INFO`, SCC_MSG_WARNING, e i tipi SCC_MSG_ERROR vengono utilizzati per i messaggi che viene visualizzati nell'elenco dei messaggi di scorrimento. `SCC_MSG_STATUS`è un tipo speciale che indica che il testo deve visualizzati in una barra di stato o l'area di visualizzazione temporaneo. Se non si desidera in modo permanente nell'elenco.  
  
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