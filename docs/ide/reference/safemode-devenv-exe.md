---
title: -SafeMode (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1c8748a6dadaee41a5e615742715a92240b74ab8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
Avvia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] in modalità sicura caricando soltanto l'ambiente e i servizi predefiniti.  
  
## <a name="syntax"></a>Sintassi  
  
```  
devenv /SafeMode   
```  
  
## <a name="remarks"></a>Note  
 Questa opzione impedisce il caricamento di tutti i pacchetti VSPackage di terze parti all'avvio di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] assicurando un'esecuzione stabile.  
  
## <a name="description"></a>Descrizione  
 Nell'esempio seguente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] viene avviato in modalità sicura.  
  
## <a name="code"></a>Codice  
  
```  
Devenv.exe /SafeMode  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)