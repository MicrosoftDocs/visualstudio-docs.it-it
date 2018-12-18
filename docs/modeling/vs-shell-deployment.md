---
title: Distribuzione di Visual Studio Shell | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: eb5446c8c3090624f327c234a1b518dc1928b6c9
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="vs-shell-deployment"></a>Distribuzione della shell di Visual Studio

Una shell isolata consente di determinare quali Visual Studio funzionalità necessarie interagire con il linguaggio specifico di dominio e l'aspetto di tale soluzione. Per ulteriori informazioni sulla shell di Visual Studio isolated, vedere [personalizzazione Shell isolata](../extensibility/customizing-the-isolated-shell.md).

## <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>Per impostare una Shell di Visual Studio come destinazione di distribuzione
  
1.  Nel **DslPackage** progetto, aprire **source.extension.tt**.  
  
2.  In `<SupportedProducts>` inserire:  
  
    ```  
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>  
    ```  
  
     Sostituire *MyIsolatedShell* con il nome del pacchetto di shell isolata.