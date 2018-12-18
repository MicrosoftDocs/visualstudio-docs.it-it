---
title: Comandi definiti dall'IDE per l'estensione di sistemi di progetto | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4941f5d842f311f078594ee9a9deef02219ea05d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="ide-defined-commands-for-extending-project-systems"></a>Comandi definiti dall'IDE per l'estensione di sistemi di progetto
Quando si desidera estendere sistemi di progetto, è possibile utilizzare i comandi e comandi forniti da gruppi di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 Nelle sezioni seguenti vengono elencano gli elementi di comando che risultano particolarmente utili per l'estensione di sistemi di progetto.  
  
## <a name="command-menus"></a>Menu dei comandi  
 Nella tabella seguente viene illustrato i menu dei comandi che sono utili posizioni in cui inserire i comandi di alto livello che richiamano un'estensione di progetto.  
  
|Menu dei comandi|Descrizione|  
|------------------|-----------------|  
|IDM_VS_MENU_PROJECT|Il **progetto** menu di primo livello.|  
|IDM_VS_TOOL_PROJWIN|Il **Esplora** barra degli strumenti.|  
  
## <a name="shortcut-menus"></a>Menu di scelta rapida  
 Nella tabella seguente viene illustrato i menu di scelta rapida che si applicano quando si seleziona un nodo singolo nel **Esplora**, o quando sono presenti più selezioni omogenee nel **Esplora**, ovvero quando tutti i nodi selezionati sono dello stesso tipo.  
  
|Menu di scelta rapida|Descrizione|  
|-------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|Si applica quando è selezionato il nodo del progetto.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|Si applica quando si seleziona un file.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|Si applica quando si seleziona una cartella.|  
|IDM_VS_CTXT_WEBREFFOLDER|Si applica quando si seleziona la cartella riferimenti Web.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|Si applica quando è selezionato il nodo radice di riferimenti denominato "Riferimenti".|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|Si applica quando vengono selezionati nodi di riferimento; tra cui assembly, COM e solo i riferimenti di progetto. Non include riferimenti Web.|  
  
 Nella tabella seguente viene illustrato i menu di scelta rapida che si applicano quando la selezione nella **Esplora** si estende su più gerarchie,  
  
|Menu di scelta rapida|Descrizione|  
|-------------------|-----------------|  
|IDM_VS_CTXT_XPROJ_SLNPROJ|Si applica quando la selezione corrente contiene il nodo della soluzione e i nodi radice del progetto.|  
|IDM_VS_CTXT_XPROJ_SLNITEM|Si applica quando la selezione corrente contiene gli elementi del progetto e del nodo della soluzione.|  
|IDM_VS_CTXT_XPROJ_MULTIPROJ|Si applica quando la selezione corrente è costituito da più radice progetto solo i nodi.|  
|IDM_VS_CTXT_XPROJ_PROJITEM|Si applica quando la selezione corrente contiene una combinazione di nodi del progetto radice e gli elementi di progetto. Inoltre, la selezione può contenere il nodo della soluzione.|  
|IDM_VS_CTXT_XPROJ_MULTIITEM|Si applica quando la selezione corrente contiene elementi di progetto da più progetti nella soluzione, o quando sono selezionati elementi di tipi diversi nello stesso progetto.|  
  
## <a name="command-groups"></a>Gruppi di comandi  
 Nella tabella seguente mostra i gruppi di comandi che è possibile utilizzare quando si estendono progetti e che è possibile accedere tramite il <xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE> menu di scelta rapida.  
  
|Gruppo di comandi|Descrizione|  
|-------------------|-----------------|  
|IDG_VS_CTXT_PROJECT_BUILD|Comandi per la compilazione, ricompilazione e la distribuzione del progetto.|  
|IDG_VS_CTXT_COMPILELINK|Comandi per la compilazione e collegamento del progetto.|  
|IDG_VS_CTXT_PROJECT_CONFIG|Comandi impostare la configurazione di progetto e l'ordine di compilazione.|  
|IDG_VS_CTXT_PROJECT_ADD|Comandi che vengono aggiunte al progetto.|  
|IDG_VS_CTXT_PROJECT_START|Comandi per l'impostazione di progetto di avvio associato con il tasto F5.|  
|IDG_VS_CTXT_PROJECT_SAVE|Comandi per il salvataggio di elementi di progetto.|  
|IDG_VS_CTXT_PROJECT_DEBUG|Comandi per il debug.|  
|IDG_VS_CTXT_PROJECT_SCC|Comandi di controllo del codice sorgente.|  
|IDG_VS_CTXT_PROJECT_TRANSFER|I comandi per tagliare, copiare e incollare le operazioni.|  
|IDG_VS_CTXT_PROJECT_PROPERTIES|I comandi che forniscono accesso al **le proprietà del progetto** la finestra di dialogo.|  
  
## <a name="see-also"></a>Vedere anche  
 [Come VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Confronto tra oggetti MenuCommand e OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)   
 [Creazione di gruppi riutilizzabili di pulsanti](../../extensibility/creating-reusable-groups-of-buttons.md)