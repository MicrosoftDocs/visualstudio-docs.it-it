---
title: L'istanza sperimentale | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c80c071866e46528fe7edd287e082df3af166973
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="the-experimental-instance"></a>L'istanza sperimentale
Per proteggere l'ambiente di sviluppo di Visual Studio da applicazioni non verificate che è possibile modificarlo, Visual Studio SDK fornisce uno spazio sperimentale che è possibile utilizzare per provare. Sviluppare nuove applicazioni con Visual Studio come di consueto, ma vengono eseguiti utilizzando l'istanza sperimentale.  
  
 Ogni applicazione che dispone di un pacchetto VSIX avvia l'istanza sperimentale di Visual Studio in modalità di debug.  
  
 Se si desidera avviare l'istanza sperimentale di Visual Studio all'esterno di una soluzione specifica, eseguire il comando seguente nella finestra di comando:  
  
 "*\<Il percorso di installazione di visual studio >*\Common7\IDE\devenv.exe" RootSuffix Exp  
  
> [!NOTE]
>  L'istanza sperimentale viene scritto nel Registro di sistema sotto il `<version number>Exp` e `<version number>Exp_Config` nodi. Ad esempio l'area del Registro di sistema sperimentale di Visual Studio 2015 è  
>   
>  `HKCU\Software\Microsoft\VisualStudio\14.0Exp` e `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`  
  
 È consigliabile eseguire l'estensione nell'istanza sperimentale durante lo sviluppo. Quando si distribuisce l'estensione, viene eseguito nell'istanza di sviluppo. Per ulteriori informazioni sulla registrazione delle applicazioni, vedere [registrazione VSPackage](../extensibility/internals/registering-vspackages.md).