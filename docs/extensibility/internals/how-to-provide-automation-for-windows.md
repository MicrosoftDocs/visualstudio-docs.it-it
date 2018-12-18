---
title: 'Procedura: fornire l''automazione per Windows | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 17cf60573b6feb9fd317116eec4639dbf88f6089
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-provide-automation-for-windows"></a>Procedura: fornire l'automazione per Windows
È possibile fornire l'automazione per documenti e finestre. Fornisce l'automazione è consigliabile ogni volta che si desidera rendere disponibili gli oggetti di automazione in una finestra e l'ambiente non esiste ancora fornisce un oggetto di automazione pronti all'uso, come invece avviene con un elenco di attività.  
  
## <a name="automation-for-tool-windows"></a>Automazione per le finestre degli strumenti  
 L'ambiente fornisce l'automazione in una finestra degli strumenti restituendo standard <xref:EnvDTE.Window> dell'oggetto come illustrato nella procedura seguente:  
  
#### <a name="to-provide-automation-for-tool-windows"></a>Per consentire l'automazione per le finestre degli strumenti  
  
1.  Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> metodo tramite l'ambiente con <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> come `VSFPROPID` parametro per ottenere il `Window` oggetto.  
  
2.  Quando un chiamante richiede un oggetto di automazione VSPackage specifico per la finestra degli strumenti tramite <xref:EnvDTE.Window.Object%2A>, l'ambiente chiama `QueryInterface` per `IExtensibleObject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, o `IDispatch` interfacce. Entrambi `IExtensibleObject` e `IVsExtensibleObject` forniscono un <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> metodo.  
  
3.  Quando l'ambiente chiama quindi il `GetAutomationObject` passando `NULL`, rispondere passando nuovamente l'oggetto specifico di VSPackage.  
  
4.  Se la chiamata `QueryInterface` per `IExtensibleObject` e `IVsExtensibleObject` ha esito negativo, quindi l'ambiente chiama `QueryInterface` per `IDispatch`.  
  
## <a name="automation-for-document-windows"></a>Automazione per le finestre dei documenti  
 Standard <xref:EnvDTE.Document> oggetto disponibile anche dall'ambiente, anche se un editor può avere una propria implementazione del `T:EnvDTE.Document` oggetto implementando `IExtensibleObject` interfaccia e la risposta a `GetAutomationObject`.  
  
 Inoltre, un editor può fornire un oggetto di automazione specifico VSPackage, recuperato tramite il <xref:EnvDTE.Document.Object%2A> metodo implementando il `IVsExtensibleObject` o `IExtensibleObject` interfacce. Il [esempi di VSSDK](http://aka.ms/vs2015sdksamples) contribuisce a un oggetto di automazione specifico di documento RTF.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>