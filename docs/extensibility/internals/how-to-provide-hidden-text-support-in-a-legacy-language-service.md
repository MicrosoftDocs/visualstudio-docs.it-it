---
title: 'Procedura: fornire supporto di testo nascosto in un servizio di linguaggio Legacy | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hidden text, supporting
- editors [Visual Studio SDK], hidden text
- language services, implementing hidden text regions
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 664ab99af45e8c449247c5515184293ecb1a469f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>Procedura: fornire supporto di testo nascosto in un servizio di linguaggio Legacy
È possibile creare aree di testo nascosto oltre alle aree della struttura. Le aree di testo nascosto possono essere gestito dal client o controllati editor e vengono utilizzati per nascondere completamente un'area di testo. Nell'editor vengono visualizzate in un'area nascosta come linee orizzontali. Un esempio di questa è la visualizzazione solo Script nell'editor HTML.  
  
## <a name="procedure"></a>Routine  
  
#### <a name="to-implement-a-hidden-text-region"></a>Per implementare un'area di testo nascosto  
  
1.  Chiamare `QueryService` per <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>.  
  
     Restituisce un puntatore a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.  
  
2.  Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, passando un puntatore per un buffer di testo specificato. Determina se una sessione di testo nascosto già esiste per il buffer.  
  
3.  Se ne esiste già, quindi non è necessario creare uno e un puntatore a un esistente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> viene restituito l'oggetto. Utilizzare questo puntatore per enumerare e creare aree del testo nascosto. In caso contrario, chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> per creare una sessione di testo nascosto per il buffer.  
  
     Un puntatore al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> viene restituito l'oggetto.  
  
    > [!NOTE]
    >  Quando si chiama `CreateHiddenTextSession`, è possibile specificare un client di testo nascosto (vale a dire <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>). Il client di testo nascosto notifica quando la struttura o il testo nascosto viene espanso o compresso dall'utente.  
  
4.  Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> per aggiungere uno o più nuovi descrive le aree contemporaneamente, specificando le informazioni seguenti nel `reHidReg` (<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>) parametro:  
  
    1.  Specificare un valore di `hrtConcealed` nel `iType` appartenente il <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struttura per indicare che si sta creando un'area nascosta, anziché un'area della struttura.  
  
        > [!NOTE]
        >  Quando le aree nascosto sono nascosti, l'editor visualizza automaticamente le righe per le aree nascoste per indicare la presenza.  
  
    2.  Specificare se l'area è gestito dal client o editor controllate nel `dwBehavior` i membri del <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struttura. L'implementazione di struttura smart può contenere una combinazione di struttura dell'editor e il client controllati e aree di testo nascosto.