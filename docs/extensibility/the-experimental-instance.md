---
title: L'istanza sperimentale | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
caps.latest.revision: "36"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a656baf951e573a5913960b19c1b583797de090f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
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