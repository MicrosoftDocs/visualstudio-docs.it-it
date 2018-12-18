---
title: GUID e ID dei menu di Visual Studio | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- visual studio menus
- visual studio groups
- id
- existing menus
- guid
- menus
ms.assetid: 84639d86-dd21-4b35-9988-6bb654162488
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 69ad8f62931b628582c73a3e370a86611795caa6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="guids-and-ids-of-visual-studio-menus"></a>GUID e ID dei menu di Visual Studio
In questo argomento enumera i valori GUID e ID dei menu e gruppi nella barra dei menu di Visual Studio. Questi valori sono definiti nel file con estensione vsct che vengono installati come parte di Visual Studio SDK. Per ulteriori informazioni, vedere [IDE-Defined comandi, menu e gruppi](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).  
  
 Per ulteriori informazioni sulle modalità gestire gli oggetti di sviluppo integrato (IDE) di ambiente che sono definiti nel file vsct, vedere [estensione menu e comandi](../../extensibility/extending-menus-and-commands.md).  
  
 I menu e gruppi nella barra dei menu di Visual Studio utilizzano il GUID `guidSHLMainMenu`. Il menu se stesso con un ID `IDM_VS_TOOL_MAINMENU`.  
  
## <a name="groups-on-the-visual-studio-menu-bar"></a>Gruppi nella barra dei Menu di Visual Studio  
 Per aggiungere un menu alla barra dei menu, impostare uno di questi gruppi come elemento padre.  
  
|Gruppo|Id|  
|-----------|--------|  
|Visualizzazione/Modifica/file|IDG_VS_MM_FILEEDITVIEW|  
|Refactoring|IDG_VS_MM_REFACTORING:|  
|Progetto|IDG_VS_MM_PROJECT|  
|Compilazione|IDG_VS_MM_BUILDDEBUGRUN|  
|Formato/Tools|IDG_VS_MM_TOOLSADDINS|  
|Finestra Guida/la/Community|IDG_VS_MM_WINDOWHELP|  
|Componenti aggiuntivi|IDG_VS_MM_MACROS|  
|FullScreenBar|IDG_VS_MM_FULLSCREENBAR|  
  
## <a name="menus-on-the-visual-studio-menu-bar"></a>Menu nella barra dei Menu di Visual Studio  
 Per aggiungere un gruppo a un menu di Visual Studio esistente, impostare uno dei seguenti menu del padre. Sottomenu non sono inclusi in questo elenco.  
  
|Menu|Id|  
|----------|--------|  
|File|IDM_VS_MENU_FILE|  
|Edit|IDM_VS_MENU_EDIT|  
|Visualizza|IDM_VS_MENU_VIEW|  
|Refactoring|IDM_VS_MENU_REFACTORING|  
|Progetto|IDM_VS_MENU_PROJECT|  
|Compilazione|IDM_VS_MENU_BUILD|  
|Formato|IDM_VS_MENU_FORMAT|  
|Strumenti|IDM_VS_MENU_TOOLS|  
|Window|IDM_VS_MENU_WINDOW|  
|Componenti aggiuntivi|IDM_VS_MENU_ADDINS|  
|Community|IDM_VS_MENU_COMMUNITY|  
|?|IDM_VS_MENU_HELP|  
  
## <a name="groups-on-visual-studio-menus"></a>Gruppi nel menu di Visual Studio  
 Gli elenchi seguenti mostrano i gruppi che derivano direttamente da menu nella barra dei menu di Visual Studio. Il modo più rapido per aggiungere un comando a un menu di Visual Studio è impostato uno di questi gruppi come elemento padre. Gruppi che discendono dagli sottomenu non vengono visualizzati in questa sezione.  
  
### <a name="file-menu-groups"></a>Gruppi di Menu file  
  
|Gruppo|Id|  
|-----------|--------|  
|Nuovo/Apri|IDG_VS_FILE_FILE|  
|Aggiunta|IDG_VS_FILE_ADD|  
|Soluzione|IDG_VS_FILE_SOLUTION|  
|Varie|IDG_VS_FILE_MISC|  
|Salva|IDG_VS_FILE_SAVE|  
|Rinomina|IDG_VS_FILE_RENAME|  
|Browser|IDG_VS_FILE_BROWSER|  
|Print|IDG_VS_FILE_PRINT|  
|Utilizzati più di recente|IDG_VS_FILE_MRU|  
|Move|IDG_VS_FILE_MOVE|  
|Esci|IDG_VS_FILE_EXIT|  
  
### <a name="edit-menu-groups"></a>Modificare i gruppi di Menu  
  
|Gruppo|Id|  
|-----------|--------|  
|Annullamento/ripristino|IDG_VS_EDIT_UNDOREDO|  
|Taglia/Copia/Incolla.|IDG_VS_EDIT_CUTCOPY|  
|Seleziona|IDG_VS_EDIT_SELECT|  
|Istruzione GoTo|IDG_VS_EDIT_GOTO|  
|Find|IDG_VS_EDIT_FIND|  
|Oggetti|IDG_VS_EDIT_OBJECTS|  
|Verbi OLE|IDG_VS_EDIT_OLEVERBS|  
|Finestra di comando|IDG_VS_EDIT_COMMANDWELL|  
  
### <a name="refactor-menu-groups"></a>Effettuare il refactoring di gruppi di Menu  
  
|Gruppo|Id|  
|-----------|--------|  
|Common|IDG_REFACTORING_COMMON|  
|Avanzate|IDG_REFACTORING_ADVANCED|  
  
### <a name="view-menu-groups"></a>Visualizza gruppi di Menu  
  
|Gruppo|Id|  
|-----------|--------|  
|Codice del modulo|IDG_VS_VIEW_FORMCODE|  
|Browser|IDG_VS_VIEW_BROWSER|  
|Definire le visualizzazioni|IDG_VS_VIEW_DEFINEVIEWS|  
|WINDOWS|IDG_VS_VIEW_WINDOWS|  
|Architettura di Windows|IDG_VS_VIEW_ARCH_WINDOWS|  
|Windows dell'organizzazione|IDG_VS_VIEW_ORG_WINDOWS|  
|Browser del codice|IDG_VS_VIEW_CODEBROWSENAV_WINDOWS|  
|Sviluppo Windows|IDG_VS_VIEW_DEV_WINDOWS|  
|Barre degli strumenti|IDG_VS_VIEW_TOOLBARS|  
|Simboli|IDG_VS_VIEW_SYMBOLNAVIGATE|  
|Passare|IDG_VS_VIEW_NAVIGATE|  
|Passare ridotto|IDG_VS_VIEW_SMALLNAVIGATE|  
|Visualizzatore oggetti|IDG_VS_VIEW_OBJBRWSR|  
|Finestra di comando|IDG_VS_VIEW_COMMANDWELL|  
|Pagine delle proprietà|IDG_VS_VIEW_PROPPAGES|  
|Aggiorna|IDG_VS_VIEW_REFRESH|  
  
### <a name="project-menu-groups"></a>Gruppi di Menu progetto  
  
|Gruppo|Id|  
|-----------|--------|  
|Varie aggiungere|IDG_VS_PROJ_MISCADD|  
|Aggiunta|IDG_VS_PROJ_ADD|  
|Cartella|IDG_VS_PROJ_FOLDER|  
|Scarica/ricarica|IDG_VS_PROJ_UNLOADRELOAD|  
|Riferimenti|IDG_VS_PROJ_REFERENCE|  
|Opzioni|IDG_VS_PROJ_OPTIONS|  
|Impostazioni|IDG_VS_PROJ_SETTINGS|  
  
### <a name="build-menu-groups"></a>Creazione di gruppi di Menu  
  
|Gruppo|Id|  
|-----------|--------|  
|Soluzione|IDG_VS_BUILD_SOLUTION|  
|Selection|IDG_VS_BUILD_SELECTION|  
|Ottimizzazione GPO|IDG_VS_PGO_SELECTION|  
|Varie|IDG_VS_BUILD_MISC|  
|Annulla|IDG_VS_BUILD_CANCEL|  
  
### <a name="tools-menu-groups"></a>Gruppi di Menu Strumenti  
  
|Gruppo|Id|  
|-----------|--------|  
|Riga di comando|IDG_VS_TOOLS_CMDLINE|  
|Frammenti di codice|IDG_VS_TOOLS_SNIPPETS|  
|Subset di oggetto|IDG_VS_TOOLS_OBJSUBSET|  
|Opzioni|IDG_VS_TOOLS_OPTIONS|  
|Altri 2|IDG_VS_TOOLS_OTHER2|  
|Strumenti esterni|IDG_VS_TOOLS_EXT_TOOLS|  
|Personalizzazioni esterne|IDG_VS_TOOLS_EXT_CUST|  
  
### <a name="window-menu-groups"></a>Gruppi di Menu finestra  
  
|Gruppo|Id|  
|-----------|--------|  
|Nuovo|IDG_VS_WINDOW_NEW|  
|Dock Chiudi|IDG_VS_DOCKCLOSE|  
|Dock/Nascondi|IDG_VS_DOCKHIDE|  
|Disponi|IDG_VS_WINDOW_ARRANGE|  
|Navigazione|IDG_VS_WINDOW_NAVIGATION|  
|List|IDG_VS_WINDOW_LIST|  
  
### <a name="help-menu-groups"></a>Gruppi di Menu della Guida  
  
|Gruppo|Id|  
|-----------|--------|  
|Esempi|IDG_VS_HELP_SAMPLES|  
|Supporto|IDG_VS_HELP_SUPPORT|  
|Informazioni su|IDG_VS_HELP_ABOUT|  
  
## <a name="submenus-of-visual-studio-menus"></a>Sottomenu del menu di Visual Studio  
 Gerarchia riportata di seguito viene mostrato i sottomenu che sono associati i menu nella barra dei menu di Visual Studio. Poiché solo un gruppo può avere un menu del padre, ogni sottomenu deve derivano da un gruppo in un menu, anziché direttamente dal menu. Per ulteriori informazioni sulla relazione tra i menu, gruppi e i sottomenu, vedere [aggiunta di un sottomenu a un Menu](../../extensibility/adding-a-submenu-to-a-menu.md).  
  
> [!NOTE]
>  I nomi dei menu nella barra dei menu di Visual Studio non sono separatamente illustrati in questa gerarchia perché che può essere dedotto dalla convenzione di denominazione per i gruppi nell'IDE, come indicato di seguito: IDG_VS_*nome Menu*_*nomedelgruppo*.  
  
|Gruppo padre|Sottomenu|Gruppi figlio|  
|------------------|-------------|------------------|  
|IDG_VS_FILE_FILE|IDM_VS_CSCD_NEW|IDG_VS_FILE_NEW_CASCADE|  
||IDM_VS_CSCD_OPEN|IDG_VS_FILE_OPENP_CASCADE|  
|||IDG_VS_FILE_OPENF_CASCADE|  
|IDG_VS_FILE_ADD|IDM_VS_CSCD_ADD|IDG_VS_FILE_ADD_PROJECT_NEW|  
|||IDG_VS_FILE_ADD_PROJECT_EXI|  
|IDG_VS_FILE_MRU|IDM_VS_CSCD_FILEMRU|IDG_VS_FILE_FMRU_CASCADE|  
||IDM_VS_CSCD_PROJMRU|IDG_VS_FILE_PMRU_CASCADE|  
|IDG_VS_FILE_MOVE|IDM_VS_CSCD_MOVETOPRJ|IDG_VS_FILE_MOVE_CASCADE|  
|||IDG_VS_FILE_MOVE_PICKER|  
|IDG_VS_VIEW_DEV_WINDOWS|IDM_VS_CSCD_FINDRESULTS|IDG_VS_WNDO_FINDRESULTS|  
||IDM_VS_CSCD_WINDOWS|IDG_VS_VIEW_CALLBROWSER|  
|||IDG_VS_WNDO_OTRWNDWS1... 6|  
|||IDG_VS_WNDO_WINDOWS2|  
|IDG_VS_VIEW_TOOLBARS|IDM_VS_CSCD_COMMANDBARS||  
|IDG_VS_EDIT_GOTO|IDM_VS_EDITOR_FIND_MENU||  
|IDG_VS_EDIT_OBJECTS|IDM_VS_CSCD_MNUDES|IDG_VS_MNUDES_INSERT|  
|||IDG_VS_MNUDES_EDITNAMES|  
||IDM_VS_CSCD_OLEVERBS|IDG_VS_EDIT_OLEVERBS|  
|IDG_VS_BUILD_SELECTION|IDM_VS_CSCD_BUILD|IDG_VS_BUILD_CASCADE|  
|||IDG_VS_BUILD_PROJPICKER|  
||IDM_VS_CSCD_REBUILD|IDG_VS_REBUILD_CASCADE|  
|||IDG_VS_REBUILD_PROJPICKER|  
||IDM_VS_CSCD_PROJONLY|IDG_VS_PROJONLY_CASCADE|  
||IDM_VS_CSCD_CLEAN|IDG_VS_CLEAN_CASCADE|  
|||IDG_VS_CLEAN_PROJPICKER|  
||IDM_VS_CSCD_DEPLOY|IDG_VS_DEPLOY_CASCADE|  
|||IDG_VS_DEPLOY_PROJPICKER|  
|IDG_VS_PGO_SELECTION|IDM_VS_CSCD_PGO_BUILD|IDG_VS_PGO_BUILD_CASCADE_BUILD|  
|||IDG_VS_PGO_BUILD_CASCADE_RUN|  
  
## <a name="see-also"></a>Vedere anche  
 [GUID e ID di barre degli strumenti di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)   
 [GUID e ID dei comandi di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)   
 [File Visual Studio Command Table (VSCT)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)