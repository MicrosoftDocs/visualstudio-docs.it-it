---
title: Interfacce del Debugger dello Script ActiveX | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- Active Script Debugger interfaces
- activdbg.h
ms.assetid: bf4750b1-4e58-442b-ab56-254e640de61d
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d4a3d17a8ff43bb3bd18641c2298f5436f40d925
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="active-script-debugger-interfaces"></a>Interfacce del debugger dello script ActiveX
I file di intestazione activdbg.h e activdbg100.h forniscono le interfacce, le enumerazioni e le strutture elencate in questa sezione. Vengono utilizzati per il debug dello script.  
  
> [!NOTE]
>  Le interfacce `IJSDebug*` e l'interfaccia `IEnumJsStackFrames` sono state rilasciate inizialmente con Internet Explorer 11 per il debug del codice nativo tramite script. Il file di intestazione per queste interfacce è jscript9diag.h.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 Le seguenti interfacce consentono il debug indipendente dalla lingua e dall'host:  
  
-   [Costanti, enumerazioni e strutture del debugger di script ActiveX](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)  
  
-   [Interfaccia IActiveScriptDebug](../../winscript/reference/iactivescriptdebug-interface.md)  
  
-   [Interfaccia IActiveScriptErrorDebug](../../winscript/reference/iactivescripterrordebug-interface.md)  
  
-   [Interfaccia IActiveScriptErrorDebug110](../../winscript/reference/iactivescripterrordebug110-interface.md)  
  
-   [Interfaccia IActiveScriptSiteDebug](../../winscript/reference/iactivescriptsitedebug-interface.md)  
  
-   [Interfaccia IActiveScriptSiteDebug32](../../winscript/reference/iactivescriptsitedebug32-interface.md)  
  
-   [Interfaccia IActiveScriptSiteDebugEx](../../winscript/reference/iactivescriptsitedebugex-interface.md)  
  
-   [Interfaccia IActiveScriptWinRTErrorDebug](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)  
  
-   [Interfaccia IApplicationDebugger](../../winscript/reference/iapplicationdebugger-interface.md)  
  
-   [Interfaccia IApplicationDebuggerUI](../../winscript/reference/iapplicationdebuggerui-interface.md)  
  
-   [Interfaccia IDebugApplication](../../winscript/reference/idebugapplication-interface.md)  
  
-   [Interfaccia IDebugApplication110](../../winscript/reference/idebugapplication110-interface.md)  
  
-   [Interfaccia IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md)  
  
-   [Interfaccia IDebugApplicationNode100](../../winscript/reference/idebugapplicationnode100-interface.md)  
  
-   [Interfaccia IDebugApplicationNodeEvents](../../winscript/reference/idebugapplicationnodeevents-interface.md)  
  
-   [Interfaccia IDebugApplicationThread](../../winscript/reference/idebugapplicationthread-interface.md)  
  
-   [Interfaccia IDebugApplicationThread110](../../winscript/reference/idebugapplicationthread110-interface.md)  
  
-   [Interfaccia IDebugApplicationThreadEvents110](../../winscript/reference/idebugapplicationthreadevents110-interface.md)  
  
-   [Interfaccia IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md)  
  
-   [Interfaccia IDebugAsyncOperationCallBack](../../winscript/reference/idebugasyncoperationcallback-interface.md)  
  
-   [Interfaccia IDebugCodeContext](../../winscript/reference/idebugcodecontext-interface.md)  
  
-   [Interfaccia IDebugCookie](../../winscript/reference/idebugcookie-interface.md)  
  
-   [Interfaccia IDebugDocument](../../winscript/reference/idebugdocument-interface.md)  
  
-   [Interfaccia IDebugDocumentContext](../../winscript/reference/idebugdocumentcontext-interface.md)  
  
-   [Interfaccia IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)  
  
-   [Interfaccia IDebugDocumentHost](../../winscript/reference/idebugdocumenthost-interface.md)  
  
-   [Interfaccia IDebugDocumentInfo](../../winscript/reference/idebugdocumentinfo-interface.md)  
  
-   [Interfaccia IDebugDocumentProvider](../../winscript/reference/idebugdocumentprovider-interface.md)  
  
-   [Interfaccia IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)  
  
-   [Interfaccia IDebugDocumentTextAuthor](../../winscript/reference/idebugdocumenttextauthor-interface.md)  
  
-   [Interfaccia IDebugDocumentTextEvents](../../winscript/reference/idebugdocumenttextevents-interface.md)  
  
-   [Interfaccia IDebugDocumentTextExternalAuthor](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)  
  
-   [Interfaccia IDebugExpression](../../winscript/reference/idebugexpression-interface.md)  
  
-   [Interfaccia IDebugExpressionCallBack](../../winscript/reference/idebugexpressioncallback-interface.md)  
  
-   [Interfaccia IDebugExpressionContext](../../winscript/reference/idebugexpressioncontext-interface.md)  
  
-   [Interfaccia IDebugFormatter](../../winscript/reference/idebugformatter-interface.md)  
  
-   [Interfaccia IDebugHelper](../../winscript/reference/idebughelper-interface.md)  
  
-   [Interfaccia IDebugSessionProvider](../../winscript/reference/idebugsessionprovider-interface.md)  
  
-   [Interfaccia IDebugSessionProviderEx](../../winscript/reference/idebugsessionproviderex-interface.md)  
  
-   [Interfaccia IDebugStackFrame](../../winscript/reference/idebugstackframe-interface.md)  
  
-   [Interfaccia IDebugStackFrameSniffer](../../winscript/reference/idebugstackframesniffer-interface.md)  
  
-   [Interfaccia IDebugStackFrameSnifferEx](../../winscript/reference/idebugstackframesnifferex-interface.md)  
  
-   [Interfaccia IDebugSyncOperation](../../winscript/reference/idebugsyncoperation-interface.md)  
  
-   [Interfaccia IDebugThreadCall](../../winscript/reference/idebugthreadcall-interface.md)  
  
-   [Interfaccia IEnumDebugApplicationNodes](../../winscript/reference/ienumdebugapplicationnodes-interface.md)  
  
-   [Interfaccia IEnumDebugCodeContexts](../../winscript/reference/ienumdebugcodecontexts-interface.md)  
  
-   [Interfaccia IEnumDebugExpressionContexts](../../winscript/reference/ienumdebugexpressioncontexts-interface.md)  
  
-   [Interfaccia IEnumDebugStackFrames](../../winscript/reference/ienumdebugstackframes-interface.md)  
  
-   [Interfaccia IEnumJsStackFrames](../../winscript/reference/ienumjsstackframes-interface.md)  
  
-   [Interfaccia IEnumRemoteDebugApplications](../../winscript/reference/ienumremotedebugapplications-interface.md)  
  
-   [Interfaccia IEnumRemoteDebugApplicationThreads](../../winscript/reference/ienumremotedebugapplicationthreads-interface.md)  
  
-   [Interfaccia IJsDebug](../../winscript/reference/ijsdebug-interface.md)  
  
-   [Interfaccia IJsDebugBreakPoint](../../winscript/reference/ijsdebugbreakpoint-interface.md)  
  
-   [Interfaccia IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)  
  
-   [Interfaccia IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)  
  
-   [Interfaccia IJsDebugProcess](../../winscript/reference/ijsdebugprocess-interface.md)  
  
-   [Interfaccia IJsDebugProperty](../../winscript/reference/ijsdebugproperty-interface.md)  
  
-   [Interfaccia IJsDebugStackWalker](../../winscript/reference/ijsdebugstackwalker-interface.md)  
  
-   [Interfaccia IJsEnumDebugProperty](../../winscript/reference/ijsenumdebugproperty-interface.md)  
  
-   [Interfaccia IMachineDebugManager](../../winscript/reference/imachinedebugmanager-interface.md)  
  
-   [Interfaccia IMachineDebugManagerCookie](../../winscript/reference/imachinedebugmanagercookie-interface.md)  
  
-   [Interfaccia IMachineDebugManagerEvents](../../winscript/reference/imachinedebugmanagerevents-interface.md)  
  
-   [Interfaccia IProcessDebugManager](../../winscript/reference/iprocessdebugmanager-interface.md)  
  
-   [Interfaccia IProvideExpressionContexts](../../winscript/reference/iprovideexpressioncontexts-interface.md)  
  
-   [Interfaccia IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)  
  
-   [Interfaccia IRemoteDebugApplication110](../../winscript/reference/iremotedebugapplication110-interface.md)  
  
-   [Interfaccia IRemoteDebugApplicationEx](../../winscript/reference/iremotedebugapplicationex-interface.md)  
  
-   [Interfaccia IRemoteDebugApplicationEvents](../../winscript/reference/iremotedebugapplicationevents-interface.md)  
  
-   [Interfaccia IRemoteDebugApplicationThread](../../winscript/reference/iremotedebugapplicationthread-interface.md)  
  
-   [Interfaccia IRemoteDebugApplicationThreadEx](../../winscript/reference/iremotedebugapplicationthreadex-interface.md)  
  
-   [Interfaccia ISetNextStatement](../../winscript/reference/isetnextstatement-interface.md)  
  
-   [Interfaccia ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)  
  
-   [Interfaccia IWebAppDiagnosticsSetup](../../winscript/reference/iwebappdiagnosticssetup-interface.md)  
  
-   [Interfaccia IWebAppDiagnosticsObjectInitialization](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md)  
  
 Nella sezione seguente vengono elencate le costanti, le enumerazioni e le strutture utilizzate per il debug:  
  
-   [Costanti, enumerazioni e strutture del debugger di script ActiveX](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica del debug di script ActiveX](../../winscript/active-script-debugging-overview.md)