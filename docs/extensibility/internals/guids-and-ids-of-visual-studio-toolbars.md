---
title: GUID e ID di barre degli strumenti di Visual Studio | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- visual studio groups
- toolbars
- visual studio toolbar
- id
- toolgar group
- tool window toolbar
- guid
ms.assetid: c9cacd57-9225-450f-a9ac-cbf3168ea844
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: bbb14818cebb35f703ec6f5ade084d96ac383d6a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="guids-and-ids-of-visual-studio-toolbars"></a>GUID e ID di barre degli strumenti di Visual Studio
In questo argomento enumera i valori GUID e ID di barre degli strumenti inclusi in ambiente di sviluppo integrato (IDE) di Visual Studio e dei gruppi che contengono. Questi valori sono definiti nel file con estensione vsct che vengono installati come parte di Visual Studio SDK. Per ulteriori informazioni, vedere [IDE-Defined comandi, menu e gruppi](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).  
  
> [!NOTE]
>  Molte delle barre degli strumenti di Visual Studio non sono definiti da Visual Studio e il relativo GUID e i valori di ID non sono pubblici. Questo argomento elenca solo le barre degli strumenti che sono definiti nel file con estensione vsct Visual Studio SDK.  
  
 Per ulteriori informazioni su come usare gli oggetti IDE che sono definiti nel file vsct, vedere [estensione menu e comandi](../../extensibility/extending-menus-and-commands.md).  
  
 Le barre degli strumenti predefinita fornite dall'IDE di Visual Studio utilizza il GUID `guidSHLMainMenu`, salvo diversa indicazione, utilizzando la sintassi coppia GUID: ID.  
  
## <a name="ide-toolbars"></a>Barre degli strumenti IDE  
 Le barre degli strumenti seguenti sono fornite tramite l'IDE di Visual Studio. Barre degli strumenti possono essere visualizzati selezionandole nel **barre degli strumenti** sottomenu del **strumenti** menu. Barre degli strumenti nelle finestre degli strumenti non sono inclusi in questa sezione.  
  
 Solo i gruppi possono accedere direttamente dalle barre degli strumenti. Per aggiungere un gruppo, impostare il relativo elemento padre per il GUID e l'ID della barra degli strumenti. Per aggiungere un pulsante a una barra degli strumenti, impostare il relativo elemento padre a un gruppo sulla barra degli strumenti.  
  
|ToolBar|Id|  
|-------------|--------|  
|Standard|IDM_VS_TOOL_STANDARD|  
|Compilazione|IDM_VS_TOOL_BUILD|  
|Editor di testo|IDM_VS_TOOL_TEXTEDITOR|  
|Debug|guidVSDebugGroup:IDM_DEBUG_TOOLBAR|  
|Posizione di debug|guidVSDebugGroup:IDM_DEBUG_CONTEXT_TOOLBAR|  
  
### <a name="special-toolbars"></a>Barre degli strumenti speciali  
 Queste barre degli strumenti sono definiti dall'IDE di Visual Studio, ma non contengono gruppi di comandi e funzioni specializzate.  
  
|ToolBar|Id|  
|-------------|--------|  
|Aggiungi comando|IDM_VS_TOOL_ADDCOMMAND|  
|Undefined|IDM_VS_TOOL_UNDEFINED|  
|XML Schema|IDM_VS_TOOL_SCHEMA|  
|Dati XML|IDM_VS_TOOL_DATA|  
  
## <a name="groups-on-the-ide-toolbars"></a>Gruppi di barre degli strumenti IDE  
 Per aggiungere un pulsante a una barra degli strumenti standard, impostare uno dei seguenti gruppi come elemento padre. I gruppi vengono ordinati in base della barra degli strumenti padre.  
  
### <a name="standard-toolbar-groups"></a>Gruppi della barra degli strumenti standard  
  
|nome|Id|  
|----------|--------|  
|Salva/Apri|IDG_VS_TOOLSB_SAVEOPEN|  
|Taglia o copia|IDG_VS_TOOLSB_CUTCOPY|  
|Annullamento/ripristino|IDG_VS_TOOLSB_UNDOREDO|  
|Esegui/compilazione|IDG_VS_TOOLSB_RUNBUILD|  
|Cerca|IDG_VS_TOOLSB_SEARCH|  
|WINDOWS|IDG_VS_TOOLSB_WINDOWS|  
|Nuove finestre|IDG_VS_TOOLSB_NEWWINDOWS|  
|Caricamento/salvataggio|IDG_VS_WINDOWUI_LOADSAVE|  
|misuratore|IDG_VS_TOOLSB_GAUGE|  
  
### <a name="build-toolbar-groups"></a>Creazione di gruppi della barra degli strumenti  
  
|nome|Id|  
|----------|--------|  
|Barra di compilazione|IDG_VS_BUILDBAR|  
|Annulla|IDG_VS_BUILD_CANCEL|  
  
### <a name="text-editor-toolbar-groups"></a>Gruppi della barra degli strumenti Editor di testo  
  
|nome|Id|  
|----------|--------|  
|Completamento|IDM_VS_TOOL_TEXTEDITOR|  
|Indent|IDG_VS_EDITTOOLBAR_INDENT|  
|Commento|IDG_VS_EDITTOOLBAR_COMMENT|  
|Segnalibri|IDG_VS_EDITTOOLBAR_TEMPBOOKMARKS|  
  
### <a name="debug-toolbar-groups"></a>Gruppi della barra degli strumenti di debug  
  
|nome|Id|  
|----------|--------|  
|Esecuzione|IDM_DEBUG_TOOLBAR|  
|Esecuzione di istruzioni|IDG_DEBUG_TOOLBAR_STEPPING|  
|Espressioni di controllo|IDG_DEBUG_TOOLBAR_WATCH|  
|WINDOWS|IDG_DEBUG_TOOLBAR_WINDOWS|  
  
### <a name="debug-location-toolbar-groups"></a>Gruppi della barra degli strumenti posizione di debug  
  
|nome|Id|  
|----------|--------|  
|Posizione di debug|IDG_DEBUG_CONTEXT_TOOLBAR|  
  
## <a name="tool-window-toolbars"></a>Barre degli strumenti finestra dello strumento  
 Barre degli strumenti possono essere visualizzati direttamente nell'IDE o nelle finestre degli strumenti quali **Esplora**. Poiché le finestre degli strumenti non sono definite nel file vsct, barre degli strumenti finestra di strumento non è definito gli elementi padre. Al contrario, vengono inseriti nel codice. Nella tabella seguente mostra le barre degli strumenti visualizzati nelle finestre degli strumenti nell'IDE e contengono i gruppi di comando.  
  
> [!NOTE]
>  Barre degli strumenti e i gruppi di utilizzano il GUID `guidSHLMainMenu`, salvo diversa indicazione, utilizzando la sintassi coppia GUID: ID. Se viene specificato un GUID per una barra degli strumenti, si applica anche ai gruppi che derivano da tale barra degli strumenti.  
  
|Finestra degli strumenti|ToolBar|Gruppi|  
|-----------------|-------------|------------|  
|Esplora soluzioni|IDM_VS_TOOL_PROJWIN|IDG_VS_PROJ_TOOLBAR1... 5|  
|Esplora server|guid_SE_MenuGroup:IDM_SE_TOOLBAR_SERVEREXPLORER|IDG_SE_TOOLBAR_REFRESH|  
|Proprietà|IDM_VS_TOOL_PROPERTIES|IDG_VS_PROPERTIES_SORT<br /><br /> IDG_VS_PROPERTIES_PAGES|  
|Visualizzazione classi|IDM_VS_TOOL_CLASSVIEW|IDG_VS_CLASSVIEW_FOLDERS<br /><br /> IDG_VS_CLASSVIEW_SEARCH<br /><br /> IDG_VS_CLASSVIEW_SETTINGS|  
|Visualizzazione classi|IDM_VS_TOOL_CLASSVIEW_GO|IDG_VS_CLASSVIEW_SEARCH2|  
|Visualizzatore oggetti|IDM_VS_TOOL_OBJBROWSER|IDG_VS_OBJBROWSER_SUBSETS<br /><br /> IDG_VS_OBJBROWSER_SEARCH<br /><br /> IDG_VS_OBJBROWSER_ADDREFERENCE<br /><br /> IDG_VS_OBJBROWSER_BROWSERSETTINGS|  
|Visualizzatore oggetti|IDM_VS_TOOL_OBJECT_BROWSER_GO|IDG_VS_OBJBROWSER_SEARCH2|  
|Output|IDM_VS_TOOL_OUTPUTWINDOW|IDG_VS_OUTPUTWINDOW_SELECT<br /><br /> IDG_VS_OUTPUTWINDOW_GOTO<br /><br /> IDG_VS_OUTPUTWINDOW_NEXTPREV<br /><br /> IDG_VS_OUTPUTWINDOW_CLEAR<br /><br /> IDG_VS_OUTPUTWINDOW_WORDWRAP|  
|Trova e sostituisci|IDM_VS_TOOL_UNIFIEDFIND|IDG_VS_FINDTAB<br /><br /> IDG_VS_REPLACETAB|  
|Risultati ricerca 1|IDM_VS_TOOL_FINDRESULTS1|IDG_VS_FINDRESULTS1_GOTO<br /><br /> IDG_VS_FINDRESULTS1_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS1_CLEAR<br /><br /> IDG_VS_FINDRESULTS1_STOPFIND|  
|Risultati ricerca 2|IDM_VS_TOOL_FINDRESULTS2|IDG_VS_FINDRESULTS2_GOTO<br /><br /> IDG_VS_FINDRESULTS2_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS2_CLEAR<br /><br /> IDG_VS_FINDRESULTS2_STOPFIND|  
|Frammento di codice|IDM_VS_TOOL_SNIPPETMENUS|IDG_VS_SNIPPET_REPL<br /><br /> IDG_VS_SNIPPET_REF<br /><br /> IDG_VS_SNIPPET_PROP|  
|Segnalibri|IDM_VS_TOOL_BOOKMARKWIND|IDG_VS_BWNEWFOLDER<br /><br /> IDG_VS_BWNEXTBM<br /><br /> IDG_VS_BWNEXTBMF<br /><br /> IDG_VS_BWENABLE<br /><br /> IDG_VS_BWDELETE|  
|Elenco attività|IDM_VS_TOOL_TASKLIST|IDG_VS_TASKLIST_PROVIDERLIST|  
|Attività definite dall'utente|IDM_VS_TOOL_USERTASKS|IDG_VS_TASKLIST_PROVIDERLIST<br /><br /> IDG_VS_USERTASKS_EDIT|  
|Elenco errori|IDM_VS_TOOL_ERRORLIST|IDG_VS_ERRORLIST_ERRORGROUP<br /><br /> IDG_VS_ERRORLIST_WARNINGGROUP<br /><br /> IDG_VS_ERRORLIST_MESSAGEGROUP|  
|Visualizzatore chiamate|IDM_VS_TOOL_CALLBROWSER1... 16|IDG_VS_TOOLBAR_CALLBROWSER1_ACTIONS<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_TYPE<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_CBSETTINGS|  
|Punti di interruzione|guidVSDebugGroup:IDM_BREAKPOINTS_WINDOW_TOOLBAR|IDG_BREAKPOINTS_WINDOW_NEW<br /><br /> IDG_BREAKPOINTS_WINDOW_DELETE<br /><br /> IDG_BREAKPOINTS_WINDOW_ALL<br /><br /> IDG_BREAKPOINTS_WINDOW_VIEW<br /><br /> IDG_BREAKPOINTS_WINDOW_EDIT<br /><br /> IDG_BREAKPOINTS_WINDOW_COLUMNS|  
|Disassembly|guidVSDebugGroup:IDM_DISASM_WINDOW_TOOLBAR|IDG_DISASM_WINDOW_TOOLBAR|  
|Memoria 1-4|guidVSDebugGroup:IDM_MEMORY_WINDOW_TOOLBAR1... 4|IDG_MEMORY_EXPRESSION1... 4<br /><br /> IDG_MEMORY_COLUMNS1... 4|  
|Processi|guidVSDebugGroup:IDM_ATTACHED_PROCS_TOOLBAR|IDG_ATTACHED_PROCS_EXECCNTRL IDG_ATTACHED_PROCS_STEPPING<br /><br /> IDG_ATTACHED_PROCS_EXECCNTRL2<br /><br /> IDG_ATTACHED_PROCS_ATTACH<br /><br /> IDG_ATTACHED_PROCS_COLUMNS|  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiunta di un Controller di Menu per una barra degli strumenti](../../extensibility/adding-a-menu-controller-to-a-toolbar.md)   
 [Aggiunta di una barra degli strumenti a una finestra degli strumenti](../../extensibility/adding-a-toolbar-to-a-tool-window.md)   
 [GUID e ID dei menu di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)