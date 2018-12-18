---
title: Selezione oggetti di contesto | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 04ccc4a57ac7af144c134761119433b7533e9bec
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="selection-context-objects"></a>Selezione oggetti di contesto
Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE) usa un oggetto di contesto di selezione globale per determinare cosa deve essere visualizzata nell'IDE. Tutte le finestre nell'IDE possono avere un proprio oggetto di contesto di selezione inserito nel contesto di selezione globale. L'IDE aggiorna il contesto di selezione globale con i valori da una finestra quando tale finestra ha lo stato attivo. Per ulteriori informazioni, vedere [Feedback all'utente](../../extensibility/internals/feedback-to-the-user.md).  
  
 Ogni sito nell'IDE o cornice della finestra dispone di un servizio chiamato <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>. L'oggetto creato dal pacchetto VSPackage che viene posizionato nella cornice della finestra che è necessario chiamare il `QueryService` metodo per ottenere un puntatore al <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> interfaccia.  
  
 Finestre cornice consente di mantenere le parti delle informazioni sul contesto di selezione da viene propagata al contesto di selezione globale quando vengono avviate. Questa possibilità è utile per le finestre degli strumenti che potrebbero essere necessario iniziare con una selezione vuota.  
  
 Modifica gli eventi trigger di contesto globale selezione che è possono monitorare i pacchetti VSPackage. I VSPackage possono eseguire le attività seguenti implementando `IVsTrackSelectionEx` e <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> interfacce:  
  
-   Aggiornare il file attualmente attivo in una gerarchia.  
  
-   Monitorare le modifiche apportate a determinati tipi di elementi. Ad esempio, se il pacchetto VSPackage Usa una speciale **proprietà** finestra, è possibile monitorare le modifiche in attivo **proprietà** finestra e riavviare tuo quando necessario.  
  
 La sequenza seguente viene illustrato il corso tipico di traccia della selezione.  
  
1.  L'IDE recupera il contesto di selezione dalla finestra appena aperta e lo inserisce nel contesto di selezione globale. Se il contesto della selezione utilizza HIERARCHY_DONTPROPAGATE o SELCONTAINER_DONTPROPAGATE, tali informazioni non vengono propagate al contesto globale. Per ulteriori informazioni, vedere [Feedback all'utente](../../extensibility/internals/feedback-to-the-user.md).  
  
2.  Eventi di notifica vengono trasmessi a qualsiasi VSPackage che li richiesto.  
  
3.  Il pacchetto VSPackage agisce sugli eventi che riceve eseguendo attività quali l'aggiornamento di una gerarchia, la riattivazione di uno strumento o altre operazioni.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>   
 [Gerarchie in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Selezione e la valuta nell'IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Tipi di progetto](../../extensibility/internals/project-types.md)