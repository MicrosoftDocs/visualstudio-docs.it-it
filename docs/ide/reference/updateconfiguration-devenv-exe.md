---
title: -Updateconfiguration (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- /updateconfiguration Devenv switch
- Devenv, /updateconfiguration switch
- updateconfiguration Devenv switch
ms.assetid: 9a1084cc-8b68-4ccc-aaea-f95939164338
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 0ec3bfc47829bce2fe5ad836c970cb28f8a1294e
ms.sourcegitcommit: d16c6812b114a8672a58ce78e6988b967498c747
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/02/2018
---
# <a name="updateconfiguration-devenvexe"></a>/Updateconfiguration (devenv.exe)
Notifica a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] che è necessario unire i pacchetti di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nel sistema e controllare se vi sono modifiche della cache MEF.  
  
## <a name="syntax"></a>Sintassi  
  
```  
devenv /updateconfiguration  
```  
  
## <a name="remarks"></a>Note  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] esegue questo comando automaticamente quando si installa un pacchetto VSIX. È consigliabile eseguire `devenv.exe /updateconfiguration` dopo l'applicazione di patch ai file in modo che [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aggiorni la cache MEF. Ciò consente di valutare se la correzione è adeguata.  
  
## <a name="example"></a>Esempio  
 La riga di comando seguente indica a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di unire i pacchetti di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nel sistema e di controllare se vi sono modifiche della cache MEF.  
  
```  
Devenv.exe /updateconfiguration  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Personalizzare l'IDE di Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)   
 [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)