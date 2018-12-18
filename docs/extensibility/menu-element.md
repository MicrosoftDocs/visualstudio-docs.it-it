---
title: Elemento menu | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, Menus
- Menus element (VSCT XML schema)
ms.assetid: ce0560f3-b4c9-4ab2-a99c-d4e10f37b9e0
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 58b948e7ec420442eae839cd4eeefbccbe6b509d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="menu-element"></a>Elemento di menu
Definisce una voce di menu. Questi sono i sei tipi di menu: ToolWindowToolbar, Menu, MenuController, MenuControllerLatched, sulla barra degli strumenti e contesto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<Menu guid="guidMyCommandSet" id="MyCommand" priority="0x100" type="button">  
  <Parent>... </Parent>  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</Menu>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|guid|Obbligatorio. GUID dell'identificatore di comando/ID GUID.|  
|ID|Obbligatorio. ID dell'identificatore di comando/ID GUID.|  
|priority|Facoltativo. Un valore numerico che specifica la posizione relativa di un menu in un gruppo di menu.|  
|ToolbarPriorityInBand|Facoltativo. Un valore numerico che specifica la posizione relativa di una barra degli strumenti in una banda quando la finestra è ancorata.|  
|tipo|Facoltativo. Valore enumerato che specifica il tipo di elemento.<br /><br /> Se non è presente, il tipo predefinito è Menu.<br /><br /> Contesto<br /> Menu di scelta rapida che viene visualizzato quando un utente fa una finestra. Menu di scelta rapida presenta le caratteristiche seguenti:<br /><br /> -Non usa i campi priorità e il padre quando il menu viene visualizzato come un menu di scelta rapida.<br />-Può essere utilizzato come un sottomenu e anche come un menu di scelta rapida. In questo caso, i campi ID gruppo sia priorità vengono rispettati.<br />-È sempre disponibile.<br /><br /> Menu di scelta rapida viene visualizzato solo quando vengono soddisfatte le condizioni seguenti:<br /><br /> Viene visualizzata la finestra che lo ospita.<br />-Il gestore del mouse nel pacchetto VSPackage rileva un pulsante destro del mouse sulla finestra e quindi chiama un metodo che gestisce il comando.<br />-Il menu di scelta rapida viene visualizzato quando si chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A> (metodo) (l'approccio consigliato) o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> metodo.<br /><br /> Menu<br /> Fornisce un menu a discesa. Un menu a discesa presenta le caratteristiche seguenti:<br /><br /> -Rispetta l'elemento padre nella relativa definizione.<br />-È necessario un gruppo padre o un CommandPlacement a un gruppo.<br />-Può essere un sottomenu in qualsiasi altro tipo di menu.<br />-Viene visualizzata automaticamente ogni volta che viene visualizzato il menu padre.<br />-Non richiede l'implementazione di VSPackage codice affinché venga visualizzato.<br /><br /> MenuController<br /> Fornisce un menu a discesa pulsante di menu combinato, in genere utilizzato nelle barre degli strumenti. Un menu MenuController presenta le caratteristiche seguenti:<br /><br /> -Deve essere contenuta in un altro menu tramite padre o CommandPlacement.<br />-Rispetta l'elemento padre nella relativa definizione.<br />-Può essere qualsiasi tipo di menu padre.<br />-È reso automaticamente disponibile ogni volta che viene visualizzato il menu padre.<br />-Non richiede supporto a livello di codice per rendere il menu visualizzato.<br /><br /> Un comando dal menu di pulsante di menu combinato viene visualizzato sul pulsante di menu. Il comando visualizzato ha una delle seguenti caratteristiche:<br /><br /> -È l'ultimo comando che è stata utilizzata se il comando viene ancora visualizzato e abilitato.<br />-È il primo comando visualizzato.<br /><br /> MenuControllerLatched<br /> Fornisce un pulsante di menu combinato scelta rapida per il quale è possibile specificare un comando come selezione predefinita contrassegnando il comando come impostare un latch.<br /><br /> Un latch è un comando che è contrassegnato come menu selezionato, in genere mediante la visualizzazione di un segno di spunta. Un comando può essere contrassegnato come impostare un latch se dispone di OLECMDF_LATCHED flag impostato su di esso in un'implementazione del `QueryStatus` metodo il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia. Un menu MenuControllerLatched presenta le caratteristiche seguenti:<br /><br /> -Deve essere contenuta in un altro menu tramite un gruppo padre o CommandPlacement.<br />-Rispetta l'elemento padre nella relativa definizione.<br />-Può essere qualsiasi tipo di menu padre.<br />-Viene reso disponibile ogni volta che viene visualizzato il menu padre.<br />-Non richiede supporto a livello di codice per rendere il menu visualizzato.<br /><br /> Un comando dal menu di pulsante di menu combinato viene visualizzato sul pulsante di menu. Il comando visualizzato ha una delle seguenti caratteristiche:<br /><br /> -È il primo comando visualizzato è attivato.<br />-È il primo comando visualizzato.<br /><br /> ToolBar<br /> Fornisce una barra degli strumenti. Una barra degli strumenti ha le caratteristiche seguenti:<br /><br /> -Ignora l'elemento padre nella relativa definizione.<br />-Impossibile stabilire un sottomenu di un gruppo, nemmeno usando CommandPlacement.<br />-Sempre visualizzabile facendo clic su **barre degli strumenti** sul **vista** menu.<br />-Possono essere visualizzati utilizzando un [VisibilityItem](../extensibility/visibilityitem-element.md).<br />-Non richiede il codice per la sua creazione. Per un esempio su come creare una barra degli strumenti, vedere [aggiunta di una barra degli strumenti](../extensibility/adding-a-toolbar.md).<br /><br /> ToolWindowToolbar<br /> Fornisce una barra degli strumenti che è collegato a una finestra degli strumenti specifica, esattamente come una barra degli strumenti è collegato all'ambiente di sviluppo.<br /><br /> -Ignora l'elemento padre nella relativa definizione.<br />-Impossibile stabilire un sottomenu di un gruppo, nemmeno usando CommandPlacement.<br />-Viene visualizzata solo quando viene visualizzata la finestra degli strumenti che ospita la barra degli strumenti e il pacchetto VSPackage aggiunge in modo esplicito la barra degli strumenti per la finestra degli strumenti. Questa operazione viene in genere eseguita quando viene creata la finestra degli strumenti da ottenere la proprietà dell'host della barra degli strumenti (rappresentati dal <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost> interfaccia) dalla cornice della finestra degli strumenti e quindi chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A> metodo.|  
|Condizione|Facoltativo. Vedere [attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|Padre|Facoltativo. L'elemento padre della voce di menu.|  
|CommandFlag|Obbligatorio. Vedere [comando Flag elemento](../extensibility/command-flag-element.md). Come indicato di seguito sono riportati i valori CommandFlag validi per un Menu:<br /><br /> -   **AlwaysCreate**<br />-   **DefaultDocked**<br />-   **DefaultInvisible** -questo flag non influisce sulla visualizzazione delle barre degli strumenti.<br />-   **DontCache**<br />-   **DynamicVisibility** -questo flag non influisce sulla visualizzazione delle barre degli strumenti.<br />-   **IconAndText**<br />-   **NoCustomize**<br />-   **NotInTBList**<br />-   **NoToolbarClose**<br />-   **TestoConsente di modificare**<br />-   **TextIsAnchorCommand**|  
|Stringhe|Obbligatorio. Vedere [stringhe elemento](../extensibility/strings-element.md). L'elemento figlio `ButtonText` elemento deve essere definito.|  
|Annotazione|Commento facoltativo.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento Menus](../extensibility/menus-element.md)|Definisce tutti i menu che implementa un pacchetto VSPackage.|  
  
## <a name="example"></a>Esempio  
  
```  
<Menu guid="cmdGuidWidgetCommands" id="menuIDEditWidget"  
  priority="0x0002" type="Menu">  
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">  
    <CommandFlag>AlwaysCreate</CommandFlag>  
    <Strings>  
      <ButtonText>Edit Widget</ButtonText>  
    </Strings>  
    </Parent>  
</Menu>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [File Visual Studio Command Table (VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)