---
title: -ResetSettings (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 52d01cfc3ae6a453330c2dda5da137f449ff5cbd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)
Ripristina le impostazioni predefinite di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e avvia automaticamente l'IDE di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Facoltativamente, reimposta le impostazioni in un file con estensione vssettings specificato.  
  
 Le impostazioni predefinite sono determinate dal profilo selezionato quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] è stato avviato per la prima volta.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Devenv /ResetSettings SettingsFile  
```  
  
## <a name="arguments"></a>Argomenti  
 `SettingsFile`  
 Il percorso completo e il nome del file con estensione vssettings da applicare a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Per ripristinare il profilo Impostazioni generali per lo sviluppo, usare `General`.  
  
## <a name="remarks"></a>Note  
 Se non viene specificato `SettingsFile`, al successivo avvio di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verrà richiesto di selezionare una raccolta predefinita di impostazioni.  
  
## <a name="example"></a>Esempio  
 La riga di comando seguente applica le impostazioni memorizzate nel file `MySettings.vssettings`.  
  
```  
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Personalizzare l'IDE di Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)   
 [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)