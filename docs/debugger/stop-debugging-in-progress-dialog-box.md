---
title: Arrestare il debug nella finestra di dialogo stato | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.stopnow
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- Stop Debugging in Progress dialog box
ms.assetid: ed7ef49d-e25f-4a4d-9396-9bc7b4143117
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fe7eca0124869a9c636738c8641f5d2e97e63404
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="stop-debugging-in-progress-dialog-box"></a>Terminazione debug in corso (finestra di dialogo)
Questa finestra di dialogo viene visualizzata quando il debugger tenta di interrompere una sessione di debug, ma questa operazione richiede tempo. L'interruzione di una sessione di debug è in genere un'operazione molto veloce e questa finestra di dialogo non viene visualizzata. Talvolta, tuttavia, è necessario più tempo per la disconnessione da tutti i processi in fase di debug. Se l'interruzione della sessione richiede diversi secondi o si verifica un errore di disconnessione, viene visualizzata questa finestra di dialogo. Se ciò avviene di frequente, è possibile che sia presente un problema interno. Può quindi essere opportuno contattare il Servizio Supporto Tecnico Clienti Microsoft.  
  
 È possibile attendere il disconnessione dei processi questa finestra di dialogo scomparsa o usare il **Termina ora** pulsante per forzare l'interruzione immediata.  
  
 **Arresta**  
 Fare clic su questo pulsante per terminare immediatamente la sessione di debug. Utilizzando **Termina ora** termineranno anziché scollegare i processi in corso il debug. Se si esegue il debug di processi di sistema, interruzione di tali processi con **Termina ora** può avere effetti imprevisti e indesiderati.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Disconnessione di programmi](http://msdn.microsoft.com/en-us/f2c756c2-8079-474b-94c2-01c19a141a01)