---
title: Distribuzione della shell di Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 816997f971e90ddd27f8e24cdc1857559e04ff70
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
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