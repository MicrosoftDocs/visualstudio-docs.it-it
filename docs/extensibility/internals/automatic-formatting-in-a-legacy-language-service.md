---
title: Formattazione automatica in un servizio di linguaggio Legacy | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e052c62afcf9551cc54373da15071fb3903fe950
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Formattazione in un servizio di linguaggio Legacy automatica
Con la formattazione automatica, un servizio di linguaggio inserisce automaticamente un frammento di codice quando un utente inizia a digitare un costrutto di codice noti.  
  
## <a name="automatic-formatting-behavior"></a>Comportamento di formattazione automatica  
 Ad esempio, quando si digita `if`, il servizio di linguaggio inserisce automaticamente parentesi graffe corrispondenti o se si preme il tasto INVIO, a livello di rientro appropriato, a seconda che il servizio di linguaggio forza il punto di inserimento in una nuova riga precedente riga apre un nuovo ambito.  
  
 Il filtro del comando utilizzato per il resto del servizio di linguaggio anche utilizzabile per la formattazione automatica. È inoltre possibile evidenziare parentesi graffe corrispondenti chiamando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>.  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo di un servizio di linguaggio legacy](../../extensibility/internals/developing-a-legacy-language-service.md)