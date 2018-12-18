---
title: Formattazione automatica in un servizio di linguaggio Legacy | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 43d9c59beaddfc6992e7b9e16e0e778be2a6d30f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Formattazione in un servizio di linguaggio Legacy automatica
Con la formattazione automatica, un servizio di linguaggio inserisce automaticamente un frammento di codice quando un utente inizia a digitare un costrutto di codice noti.  
  
## <a name="automatic-formatting-behavior"></a>Comportamento di formattazione automatica  
 Ad esempio, quando si digita `if`, il servizio di linguaggio inserisce automaticamente parentesi graffe corrispondenti o se si preme il tasto INVIO, a livello di rientro appropriato, a seconda che il servizio di linguaggio forza il punto di inserimento in una nuova riga precedente riga apre un nuovo ambito.  
  
 Il filtro del comando utilizzato per il resto del servizio di linguaggio anche utilizzabile per la formattazione automatica. È inoltre possibile evidenziare parentesi graffe corrispondenti chiamando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>.  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo di un servizio di linguaggio legacy](../../extensibility/internals/developing-a-legacy-language-service.md)