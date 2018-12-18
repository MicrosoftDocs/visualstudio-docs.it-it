---
title: -Log (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8fa0fa90e904d4fb7f3e6820ce997a6a93e738f9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)
Registra tutte le attività nel file di log per la risoluzione dei problemi. Il file verrà visualizzato dopo aver chiamato `devenv /log` almeno una volta. Per impostazione predefinita, il file di log è:  
  
 *%APPDATA%* \Microsoft\VisualStudio\\*Versione*\ActivityLog.xml  
  
 dove *Versione* indica la versione di Visual Studio. È tuttavia possibile specificare un percorso e un nome di file diversi.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Devenv /log Path\NameOfLogFile  
```  
  
## <a name="remarks"></a>Note  
 Questa opzione deve apparire alla fine della riga di comando, dopo tutte le altre opzioni.  
  
 Il log viene scritto per tutte le istanze di Visual Studio richiamate con l'opzione /log. Non vengono registrate le istanze di Visual Studio richiamate senza l'opzione /log.  
  
## <a name="see-also"></a>Vedere anche  
 [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)