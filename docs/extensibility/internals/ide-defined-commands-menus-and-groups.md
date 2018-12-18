---
title: Definita dall'IDE comandi, menu e gruppi | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b65266ad3367df5cebeabc251bc8bceb6cda7075
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="ide-defined-commands-menus-and-groups"></a>Gruppi di menu e comandi definiti dall'IDE
Molti menu, comandi e i gruppi di comandi sono già definiti per l'utilizzo da parte di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Questi comandi sono disponibili per l'utilizzo anche quando si estende [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="finding-environment-defined-commands"></a>Ricerca di comandi definiti dall'ambiente  
 I comandi di ambiente sono definiti in un set di file con estensione vsct quattro:  
  
-   SharedCmdDef.vsct  
  
-   SharedCmdPlace.vsct  
  
-   ShellCmdDef.vsct  
  
-   ShellCmdPlace.vsct  
  
 Questi file si trovano  *\<il percorso di installazione di Visual Studio SDK >*\VisualStudioIntegration\Common\Inc\\. Questi file forniscono le definizioni e i GUID dei gruppi che è possibile utilizzare nel file di configurazione (con estensione vsct) nella tabella di comando di un VSPackage come contenitori per i menu, gruppi e i comandi e menu.  
  
## <a name="in-this-section"></a>In questa sezione  
 [GUID e ID dei menu di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)  
 Fornisce i valori GUID e ID di menu nella barra dei menu di Visual Studio e dei gruppi che contengono.  
  
 [GUID e ID delle barre degli strumenti di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)  
 Fornisce i valori GUID e ID di barre degli strumenti nell'IDE di Visual Studio e dei gruppi che contengono.  
  
 [GUID e ID dei comandi di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)  
 Fornisce i valori GUID e ID di comandi definiti dall'IDE di Visual Studio.  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Command Table (. File Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Comandi definiti dall'IDE per l'estensione di sistemi di progetto](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)   
 [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)