---
title: Fornire la struttura di supporto in un servizio di linguaggio | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], outlining support
- language services, supporting outlining
- outlining, supporting
ms.assetid: df759e89-8193-418c-8038-6626304d387b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6467a1e3386daedc4a67aa420c06cf01187b8d22
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>Procedura: fornire supporto esteso di struttura in un servizio di linguaggio Legacy
Sono disponibili due opzioni per l'estensione del supporto della struttura per il linguaggio oltre, supportando il **Comprimi alle definizioni** comando. È possibile aggiungere aree della struttura di controllo editor e aree della struttura di gestito dal client.  
  
## <a name="adding-editor-controlled-outline-regions"></a>Aggiunta di aree della struttura controllata Editor  
 Utilizzare questo approccio per creare un'area della struttura e quindi consentire all'editor di gestione che indica se l'area è espanso, compresso e così via. Le due opzioni per fornire supporto di struttura, questa opzione è meno affidabili. Per questa opzione, si crea una nuova area della struttura in un intervallo specificato di testo tramite <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>. Dopo la creazione di quest'area, il comportamento viene controllato dall'editor. Utilizzare la procedura seguente per implementare aree della struttura controllata editor.  
  
#### <a name="to-implement-an-editor-controlled-outline-region"></a>Per implementare un'area della struttura controllata editor  
  
1.  Chiamare `QueryService` per <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>  
  
     Restituisce un puntatore a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.  
  
2.  Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, passando un puntatore per un buffer di testo specificato. Restituisce un puntatore per il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> oggetto per il buffer.  
  
3.  Chiamare <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> su <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> per un puntatore a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>.  
  
4.  Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> per aggiungere uno o più nuove aree di struttura alla volta.  
  
     Questo metodo consente di specificare l'intervallo di testo in una struttura, se esistente aree della struttura vengono rimossi o mantenute e indica se l'area della struttura è espanso o compresso per impostazione predefinita.  
  
## <a name="adding-client-controlled-outline-regions"></a>Aggiunta di aree della struttura di controllo Client  
 Utilizzare questo approccio alla struttura implementare gestito dal client (o smart) simile a quella utilizzata per la [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] servizi di linguaggio. Un servizio di linguaggio che gestisce la propria struttura consente di monitorare il contenuto del buffer di testo per eliminare aree della struttura precedente quando essi non è più valido e creare nuove aree della struttura in base alle esigenze.  
  
#### <a name="to-implement-a-client-controlled-outline-region"></a>Per implementare un'area della struttura di controllo client  
  
1.  Chiamare `QueryService` per <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>. Restituisce un puntatore a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.  
  
2.  Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, passando un puntatore per un buffer di testo specificato. Determina se una sessione di testo nascosto già esiste per il buffer.  
  
3.  Se esiste già una sessione di testo, quindi non è necessario creare uno e un puntatore a un esistente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> viene restituito l'oggetto. Utilizzare l'indicatore di misura per l'enumerazione e la creazione di aree della struttura. In caso contrario, chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> per creare una sessione di testo nascosto per il buffer. Un puntatore al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> viene restituito l'oggetto.  
  
    > [!NOTE]
    >  Quando si chiama <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>, è possibile specificare un client di testo nascosto (vale a dire un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> oggetto). Il client invia una notifica quando un testo nascosto o area della struttura è espanso o compresso dall'utente.  
  
4.  Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> struttura) parametro: specificare un valore di <xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE> nel `iType` appartenente il <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struttura per indicare che si sta creando un'area della struttura, piuttosto che in un'area nascosta. Specificare se l'area è gestito dal client o editor controllate nel `dwBehavior` appartenente il <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struttura. L'implementazione di struttura smart può contenere una combinazione di aree della struttura dell'editor e gestito dal client. Specificare il testo dell'intestazione visualizzato quando l'area della struttura viene compresso, ad esempio "...", nel `pszBanner` appartenente il <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struttura. Testo dell'intestazione dell'editor predefinito per un'area nascosta è "…".