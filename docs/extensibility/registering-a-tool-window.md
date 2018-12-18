---
title: Registrazione di una finestra degli strumenti | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering managed
- tool windows, registering
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 637f0635a4f1e04df7495ab00b4e79b59d97ee1b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="registering-a-tool-window"></a>Registrazione di una finestra degli strumenti
È possibile registrare le finestre degli strumenti utilizzando <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> e  <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute>  
  
## <a name="example"></a>Esempio  
  
```csharp  
  
[ProvideToolWindow(typeof(PersistedWindowPane), Style = MsVsShell.VsDockStyle.Tabbed, Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]
[ProvideToolWindow(typeof(DynamicWindowPane), PositionX=250, PositionY=250, Width=160, Height=180, Transient=true)]
[ProvideToolWindowVisibility(typeof(DynamicWindowPane), /*UICONTEXT_SolutionExists*/"f1536ef8-92ec-443c-9ed7-fdadf150da82")]  
[ProvideMenuResource(1000, 1)]  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("01069CDD-95CE-4620-AC21-DDFF6C57F012")]  
public class PackageToolWindow : Package  
{  
```  
  
 Nel codice precedente, il <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> registra le finestre degli strumenti PersistedWindowPane e DynamicWindowPane con Visual Studio. La finestra degli strumenti persistente è ancorata e schede con **Esplora**, e la finestra dinamica è stata assegnata un inizio di posizione e le dimensioni predefinite. La finestra dinamica è temporanea, che indica che non è stata creata all'avvio. Scrive un valore DontForceCreate nella chiave ToolWindows nel Registro di sistema. Per ulteriori informazioni, vedere [finestra strumento di configurazione](../extensibility/tool-window-display-configuration.md).
