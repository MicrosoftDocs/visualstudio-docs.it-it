---
title: "Procedura: generare eventi quando l'Editor perde lo stato attivo | Documenti Microsoft"
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - fire events on losing focus
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bbdcf30443bc548fd8d182db301cbc7119d8ceae
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-fire-events-when-the-editor-loses-focus"></a>Procedura: generare eventi quando l'Editor perde lo stato attivo
In alcuni casi è necessario sapere quando un editor perde lo stato attivo sulla cornice finestra. È ad esempio, potrebbe essere necessario estrarre codice da una finestra del codice dopo l'editor non è più incentrata su di esso. La procedura seguente fornisce i passaggi da seguire per ricevere la notifica dell'editor perde lo stato attivo.  
  
### <a name="to-fire-an-event-in-response-to-an-editor-losing-focus"></a>Per generare un evento in risposta a un editor perde lo stato attivo  
  
1.  Monitorare gli eventi di selezione ottenendo un <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> oggetto <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>.  
  
2.  Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A> e fornirlo il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents> oggetto.  
  
3.  Nella chiamata a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A>, cercare `elementid==SEID_WindowFrame`.  
  
4.  Test di `varValueNew` parametro per due scopi:  
  
    1.  Si sta cercando la cornice della finestra.  
  
    2.  Il punto in cui il programma perde la selezione verso la cornice della finestra.