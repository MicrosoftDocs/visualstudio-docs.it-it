---
title: "Procedura: fornire l'automazione per Windows | Documenti Microsoft"
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c37123eeba42630b4b899966f7f4b0dc8c046fe8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
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
 Standard <xref:EnvDTE.Document> oggetto disponibile anche dall'ambiente, anche se un editor può avere una propria implementazione del <xref:EnvDTE.Document> oggetto implementando `IExtensibleObject` interfaccia e la risposta a `GetAutomationObject`.

 Inoltre, un editor può fornire un oggetto di automazione specifico VSPackage, recuperato tramite il <xref:EnvDTE.Document.Object%2A> metodo implementando il `IVsExtensibleObject` o `IExtensibleObject` interfacce. Il [esempi di VSSDK](http://aka.ms/vs2015sdksamples) contribuisce a un oggetto di automazione specifico di documento RTF.

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>