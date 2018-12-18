---
title: Elemento VisibilityItem | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VisibilityItem element (VSCT XML schema)
- VSCT XML schema elements, VisibilityItem
ms.assetid: 0932f551-972d-4194-84bb-426e3e4375e4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 85cc2a3d65d5a4763aeca231175201cf55a74b3e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="visibilityitem-element"></a>Elemento VisibilityItem
Il `VisibilityItem` elemento determina la visibilità statica di comandi e le barre degli strumenti. Ogni voce identifica un comando o i menu, nonché un contesto di interfaccia utente del comando associato. Visual Studio rileva i comandi, menu e barre degli strumenti e la visibilità, senza caricare i pacchetti VSPackage che definiscono. L'IDE Usa il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> metodo per determinare se un contesto di comando dell'interfaccia utente è attivo.  
  
 Dopo aver caricato il pacchetto VSPackage, Visual Studio si presuppone la visibilità di comando devono essere determinati dal pacchetto VSPackage anziché `VisibilityItem`. Per determinare la visibilità del comando, è possibile implementare il <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> gestore dell'evento o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> (metodo), a seconda di come è stato implementato il comando.  
  
 Un comando o un menu che contiene un `VisibilityItem` elemento viene visualizzato solo quando il contesto associato è attivo. È possibile associare un singolo comando, menu o sulla barra degli strumenti con uno o più contesti dell'interfaccia utente di comando con l'inclusione di una voce per ogni combinazione di contesto di comando. Se un comando o un menu è associato a più contesti dell'interfaccia utente di comando, quindi il comando o un menu è visibile quando uno dei contesti dell'interfaccia utente del comando associato è attivo.  
  
 Il `VisibilityItem` elemento si applica solo ai comandi, menu e barre degli strumenti, non a gruppi. Un elemento che non dispone di un processo di `VisibilityItem` elemento è visibile ogni volta che il relativo menu padre è attivo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<VisibilityItem  
  guid ="="cmdGuidMyProductCommands"  
  id=="cmdidAddWidget"  
  context="guidNotViewSourceMode"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|guid|Obbligatorio. Il GUID dell'identificatore di comando/ID GUID.|  
|ID|Obbligatorio. ID dell'identificatore di comando/ID GUID.|  
|contesto|Obbligatorio. Il contesto dell'interfaccia utente in cui il comando è visibile.|  
|Condizione|Facoltativo. Vedere [attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementi figlio  
 Nessuno  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Il `VisibilityConstraints` elemento determina la visibilità statica dei gruppi di comandi e le barre degli strumenti.|  
  
## <a name="remarks"></a>Note  
 I contesti dell'interfaccia utente di Visual Studio standard definiti nel *il percorso di installazione di Visual Studio SDK*\VisualStudioIntegration\Common\Inc\vsshlids.h file nonché come il <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids> e <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> classi. Cui è definito un set più completo dei contesti dell'interfaccia utente di <xref:Microsoft.VisualStudio.VSConstants> classe.  
  
## <a name="example"></a>Esempio  
  
```  
<VisibilityConstraints>  
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"  
    context="guidNotViewSourceMode"/>  
</VisibilityConstraints>  
```  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>   
 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>   
 <xref:Microsoft.VisualStudio.VSConstants>   
 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>   
 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>   
 [Elemento VisibilityConstraints](../extensibility/visibilityconstraints-element.md)   
 [File Visual Studio Command Table (VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)