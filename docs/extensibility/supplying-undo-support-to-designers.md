---
title: Fornisce supporto per le finestre di progettazione di annullare | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5fc289426c2560e978819efcd8eaf17e56b224a8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="supplying-undo-support-to-designers"></a>Fornisce il supporto di annullamento per le finestre di progettazione
Finestre di progettazione, ad esempio editor, in genere necessario supportare le operazioni di annullamento in modo che gli utenti possono invertire le modifiche apportate di recente quando si modifica un elemento di codice.  
  
 La maggior parte delle finestre di progettazione implementate in Visual Studio dispongono del supporto di annullamento fornito automaticamente dall'ambiente.  
  
 Implementazioni della finestra di progettazione che forniscono il supporto per la funzionalità di annullamento è necessario:  
  
-   Gestione dell'annullamento implementando la classe base astratta <xref:System.ComponentModel.Design.UndoEngine>  
  
-   Persistenza forniture e CodeDOM supporto mediante l'implementazione di <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> e <xref:System.ComponentModel.Design.IComponentChangeService> classi.  
  
 Per ulteriori informazioni sulla scrittura di finestre di progettazione utilizzando [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], vedere [estensione supporto in fase di progettazione](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).  
  
 Il [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] fornisce un'infrastruttura di annullamento predefinito per:  
  
-   Fornendo annullare le implementazioni di gestione tramite il <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> e <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> classi.  
  
-   Fornisce la persistenza e il supporto CodeDOM tramite il valore predefinito <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> e <xref:System.ComponentModel.Design.IComponentChangeService> implementazioni.  
  
## <a name="obtaining-undo-support-automatically"></a>Supporto dell'annullamento automaticamente  
 Creato in qualsiasi finestra di progettazione [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dispone del supporto di rollback automatico e completo se la finestra di progettazione:  
  
-   Si avvalgono di un <xref:System.Windows.Forms.Control> basato su classe per l'interfaccia utente.  
  
-   Oltre alla generazione del codice basato su CodeDOM standard e sistema di analisi per la persistenza e la generazione di codice.  
  
     Per ulteriori informazioni sull'uso di supporto di Visual Studio CodeDOM, vedere [compilazione e la generazione del codice sorgente dinamico](/dotnet/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation)  
  
## <a name="when-to-use-explicit-designer-undo-support"></a>Quando utilizzare il supporto di annullamento della finestra di progettazione esplicite  
 Finestre di progettazione è necessario fornire i propri management annullamento se utilizzano un'interfaccia utente grafica, detta un adattatore di visualizzazione, diverso da quello fornito da <xref:System.Windows.Forms.Control>.  
  
 Un esempio potrebbe essere creazione di un prodotto con un'interfaccia di progettazione grafica basata sul web anziché un [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] basato su interfaccia grafica.  
  
 In questi casi, uno necessario registrare l'adapter di visualizzazione con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] utilizzando <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>e fornire la gestione esplicita di annullamento.  
  
 Finestre di progettazione devono fornire CodeDOM e la persistenza è supportata se non utilizzano il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] il modello di generazione del codice fornito nel <xref:System.CodeDom> spazio dei nomi.  
  
## <a name="undo-support-features-of-the-designer"></a>Annullare la funzionalità di supporto della finestra di progettazione  
 L'ambiente di SDK fornisce le implementazioni predefinite di interfacce necessarie per fornire annullare supporto che può essere usato dalle finestre di progettazione non utilizza <xref:System.Windows.Forms.Control> basato su classi per le relative interfacce utente o il modello standard di persistenza e CodeDOM.  
  
 Il <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> deriva dalla classe di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] <xref:System.ComponentModel.Design.UndoEngine> classe usando un'implementazione della <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> classe per la gestione delle operazioni di annullamento.  
  
 Visual Studio fornisce la funzionalità di rollback della finestra di progettazione seguente:  
  
-   Funzionalità di annullamento collegati tra più finestre di progettazione.  
  
-   Unità figlio all'interno di una finestra di progettazione è possibile interagire con i relativi elementi padre mediante l'implementazione <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> e <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> su <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>.  
  
 L'ambiente di SDK fornisce il supporto CodeDOM e persistenza fornendo:  
  
-   <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> come un implementazioni del <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
 Oggetto <xref:System.ComponentModel.Design.IComponentChangeService> fornito dal [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]' host di progettazione.  
  
## <a name="using-the-environment-sdk-features-to-supply-undo-support"></a>Tramite la funzionalità SDK dell'ambiente per fornire il supporto di annullamento  
 Per ottenere il supporto di annullamento, è necessario un oggetto che implementa una finestra di progettazione:  
  
-   Creare un'istanza e inizializzare un'istanza di <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> classe con un valore valido <xref:System.IServiceProvider> implementazione.  
  
-   Questo <xref:System.IServiceProvider> classe deve fornire i servizi seguenti:  
  
    -   <xref:System.ComponentModel.Design.IDesignerHost>.  
  
    -   <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
         Finestre di progettazione utilizzando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] la serializzazione CodeDOM può scegliere di utilizzare <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> fornito con il [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] come implementazione del <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>.  
  
         In questo caso, il <xref:System.IServiceProvider> classe fornita per il <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> costruttore deve restituire l'oggetto come un'implementazione del <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> classe.  
  
    -   <xref:System.ComponentModel.Design.IComponentChangeService>  
  
         Finestre di progettazione utilizzando il valore predefinito <xref:System.ComponentModel.Design.DesignSurface> fornito dal [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] host di progettazione sono necessariamente avere un'implementazione predefinita del <xref:System.ComponentModel.Design.IComponentChangeService> classe.  
  
 Finestre di progettazione che implementa un <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> meccanismo di annullamento in base tiene automaticamente traccia delle modifiche se:  
  
-   Le modifiche alle proprietà vengono effettuate tramite il <xref:System.ComponentModel.TypeDescriptor> oggetto.  
  
-   <xref:System.ComponentModel.Design.IComponentChangeService> gli eventi vengono generati manualmente quando una modifica annullabile viene eseguito il commit.  
  
-   La modifica nella finestra di progettazione è stata creata all'interno del contesto di un <xref:System.ComponentModel.Design.DesignerTransaction>.  
  
-   La finestra di progettazione sceglie di creare in modo esplicito le unità di annullamento tramite l'unità di annullamento standard fornito da un'implementazione di <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> o l'implementazione di specifiche di Visual Studio <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>, che deriva da <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> e fornisce inoltre un implementazione di entrambi <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> e <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.ComponentModel.Design.UndoEngine>   
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>   
 [Estensione del supporto in fase di progettazione](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)