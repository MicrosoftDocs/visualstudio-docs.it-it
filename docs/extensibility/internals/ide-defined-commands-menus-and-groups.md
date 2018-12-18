---
title: Definita dall'IDE comandi, menu e gruppi | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
caps.latest.revision: "27"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 34e0e95475457e2a5f206ad4ecb0d7e42e2bb9ea
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
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