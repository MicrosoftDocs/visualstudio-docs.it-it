---
title: Semplificato incorporamento | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], custom - simple view embedding
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 183dc4ad9d7ea1a2f6855be050ad8459a3f801ac
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="simplified-embedding"></a>Semplificato incorporamento
Incorporamento semplificato è abilitato in un editor, quando il relativo oggetto visualizzazione del documento è definito come padre (vale a dire un elemento figlio di apportare) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]e <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interfaccia viene implementata per gestire i comandi della finestra. Editor di incorporamento semplificato non possono ospitare controlli attivi. Nella figura seguente, vengono visualizzati gli oggetti utilizzati per creare un editor con incorporamento semplificato.  
  
 ![Rappresentazione grafica dell'Editor di incorporamento semplificato](../extensibility/media/vssimplifiedembeddingeditor.gif "vsSimplifiedEmbeddingEditor")  
Editor con incorporamento semplificato  
  
> [!NOTE]
>  Degli oggetti in questa illustrazione, solo il `CYourEditorFactory` oggetto è necessario per creare un editor basato su file standard. Se si sta creando un editor personalizzato, non è necessario implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>, poiché l'editor avrà probabilmente un proprio meccanismo di salvataggio permanente privato. Per gli editor a non-custom, tuttavia, è necessario farlo.  
  
 Sono contenute tutte le interfacce implementate per creare un editor con incorporamento semplificato nel `CYourEditorDocument` oggetto. Tuttavia, per supportare più visualizzazioni dei dati del documento, dividere le interfacce in oggetti separati di dati e la visualizzazione, come indicato nella tabella seguente.  
  
|Interfaccia|Percorso dell'interfaccia|Usa|  
|---------------|---------------------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Visualizza|Fornisce una connessione alla finestra padre.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Visualizza|Gestisce i comandi.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Visualizza|Consente gli aggiornamenti della barra di stato.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Visualizza|Abilita **della casella degli strumenti** elementi.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Dati|Invia notifiche quando le modifiche al file.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Dati|Abilita la funzionalità Salva con nome per un tipo di file.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|Dati|Abilita il salvataggio permanente di un documento.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Dati|Consente l'eliminazione di eventi di modifica di file, ad esempio l'attivazione di ricaricamento.|