---
title: Attivazione sul posto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - in-place view activation
ms.assetid: 7d316945-06e0-4d8e-ba3a-0ef96fc75399
caps.latest.revision: 26
manager: jillfra
ms.openlocfilehash: 192274d087731f68cb7e01c1da20e80cbfef0360
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "64802931"
---
# <a name="in-place-activation"></a>Attivazione sul posto
Se la visualizzazione dell'editor ospita controlli ActiveX o altri controlli attivi, è necessario implementare la visualizzazione come controllo ActiveX o come oggetto dati del documento attivo usando il modello di attivazione sul posto.  
  
## <a name="support-for-menus-toolbars-and-commands"></a>Supporto per menu, barre degli strumenti e comandi  
 Visual Studio consente alla visualizzazione dell'editor di usare i menu e le barre degli strumenti dell'IDE. Queste estensioni sono dette *componenti OLE sul posto*. Per altre informazioni, vedere <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> e <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager>.  
  
 Se si implementa un controllo ActiveX, è possibile ospitare altri oggetti incorporati. Se si implementa un oggetto dati del documento, la cornice della finestra vincola la possibilità di usare i controlli ActiveX.  
  
> [!NOTE]
> Le interfacce <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> e <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocumentView> consentono una separazione di dati e visualizzazione. Tuttavia, Visual Studio non supporta questa funzionalità e queste interfacce vengono usate solo per rappresentare l'oggetto visualizzazione del documento.  
  
 Gli editor che usano il servizio <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> possono fornire l'integrazione di menu, barre degli strumenti e comandi chiamando i metodi dell'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> che il servizio <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> implementa. Gli editor possono anche offrire altre funzionalità di Visual Studio, come la traccia della selezione e la gestione dell'annullamento. Per ulteriori informazioni, vedere [creazione di editor e finestre di progettazione personalizzati](../extensibility/creating-custom-editors-and-designers.md).  
  
## <a name="objects-and-interfaces-used"></a>Interfacce e oggetti usati  
 Gli oggetti usati per creare l'attivazione sul posto sono illustrati nella figura seguente.  
  
 ![Editor di attivazione di&#45;Place](../misc/media/vsinplaceactivationeditor.gif "vsInPlaceActivationEditor")  
Editor di attivazione sul posto  
  
> [!NOTE]
> Tra gli oggetti di questa figura, solo l'oggetto `CYourEditorFactory` è necessario per creare un editor standard. Se si crea un editor personalizzato, non è necessario implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> perché l'editor avrà probabilmente un proprio meccanismo di salvataggio permanente privato. Per ulteriori informazioni, vedere [creazione di editor e finestre di progettazione personalizzati](../extensibility/creating-custom-editors-and-designers.md).  
  
 Tutte le interfacce implementate per creare un editor di attivazione sul posto sono visualizzate nel singolo oggetto `CYourEditorDocument` , ma questa configurazione supporta solo una singola visualizzazione dei dati del documento. Per altre informazioni sul supporto di più visualizzazioni dei dati del documento, vedere [Supporting Multiple Document Views](../extensibility/supporting-multiple-document-views.md).  
  
|Interfaccia|Tipo di oggetto|Uso|  
|---------------|--------------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>|Visualizzazione|Consente agli oggetti VSPackage sul posto di funzionare come componenti completamente integrati dell'IDE usando il servizio <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> . Questo servizio integra menu, barre degli strumenti e comandi dell'oggetto nell'IDE e invia notifiche delle modifiche di stato.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>|Visualizzazione|Mezzo principale attraverso cui un oggetto incorporato fornisce funzionalità di base al relativo contenitore e comunica con esso.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>|Visualizzazione|Gestisce l'attivazione e la disattivazione degli oggetti sul posto e determina la quantità dell'oggetto sul posto che deve essere visibile.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceObject>|Visualizzazione|Fornisce un canale diretto di comunicazione tra un oggetto sul posto, la finestra cornice più esterna dell'applicazione associata e la finestra del documento nell'applicazione che contiene l'oggetto incorporato.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument>|Visualizzazione|Implementa un oggetto ActiveX. Si noti che i metodi di <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> e `T:Microsoft.VisualStudio.OLE.Interop.IOleDocumentView` che separano i dati del documento e la visualizzazione non sono usati nell'IDE.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Visualizzazione/Dati|Consente all'oggetto dati del documento o all'oggetto visualizzazione del documento, o a entrambi, di partecipare alla gestione dei comandi.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Visualizzazione|Consente gli aggiornamenti della barra di stato.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Visualizzazione|Consente l'aggiunta di elementi alla casella degli strumenti.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Dati|Invia una notifica delle modifiche al file. Questa interfaccia è facoltativa.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Dati|Consente di abilitare la funzionalità Salva con nome per un tipo di file.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Dati|Abilita il salvataggio permanente di un documento. Per i file di sola lettura, chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SetDocDataReadOnly%2A> per fornire l'icona a forma di lucchetto che indica i file di sola lettura.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Dati|Determina se le modifiche ai dati del documento devono essere ignorate.|