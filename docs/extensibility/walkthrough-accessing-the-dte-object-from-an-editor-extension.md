---
title: "Procedura dettagliata: Accesso all'oggetto DTE di un'estensione di Editor | Documenti Microsoft"
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b888136f51e7893c6ad44ab888d8079ee92d8edf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-accessing-the-dte-object-from-an-editor-extension"></a>Procedura dettagliata: Accesso all'oggetto DTE di un'estensione di Editor
Nei pacchetti VSPackage, è possibile ottenere l'oggetto DTE chiamando il <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> (metodo) con il tipo dell'oggetto DTE. Nelle estensioni di Managed Extensibility Framework (MEF), è possibile importare <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> e quindi chiamare il <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> metodo con un tipo di <xref:EnvDTE.DTE>.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per ulteriori informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="getting-the-dte-object"></a>Ottenere l'oggetto DTE  
  
#### <a name="to-get-the-dte-object-from-the-serviceprovider"></a>Per ottenere l'oggetto DTE da ServiceProvider  
  
1.  Creare un progetto VSIX c# denominato `DTETest`. Aggiungere un modello di elemento di classificatore Editor e denominarla `DTETest`. Per ulteriori informazioni, vedere [creazione di un'estensione con un modello di elemento Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
2.  Aggiungere i seguenti riferimenti all'assembly al progetto:  
  
    -   EnvDTE  
  
    -   EnvDTE80  
  
    -   Microsoft.VisualStudio.Shell.Immutable.10.0  
  
3.  Passare al file DTETest.cs e aggiungere le seguenti `using` direttive:  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    using Microsoft.VisualStudio.Shell;  
  
    ```  
  
4.  Nel `GetDTEProvider` classe, importare un <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.  
  
    ```csharp  
    [Import]  
    internal SVsServiceProvider ServiceProvider = null;  
  
    ```  
  
5.  Nel metodo `GetClassifier()` aggiungere il codice seguente:  
  
    ```csharp  
    DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));  
  
    ```  
  
6.  Se è necessario utilizzare il <xref:EnvDTE80.DTE2> interfaccia, è possibile eseguire il cast ad esso l'oggetto DTE.  
  
## <a name="see-also"></a>Vedere anche  
 [Punti di estensione dei servizi di linguaggio e dell'editor](../extensibility/language-service-and-editor-extension-points.md)