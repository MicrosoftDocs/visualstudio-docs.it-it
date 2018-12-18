---
title: -SafeMode (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 17a8d92075f558e1e00bbba04f2c3ae955056b61
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
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