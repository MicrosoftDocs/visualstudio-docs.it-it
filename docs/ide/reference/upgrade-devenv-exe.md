---
title: -Upgrade (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- /upgrade Devenv switch
- Devenv, /upgrade switch
- upgrade Devenv switch
ms.assetid: 3468045c-5cc9-4157-9a9d-622452145d27
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4e765d376276c6e83d7e2bcce2ab46974210d96c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="upgrade-devenvexe"></a>/Upgrade (devenv.exe)
Aggiorna il file della soluzione e tutti i relativi file di progetto oppure il file di progetto specificato ai formati di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] correnti dei file.  
  
## <a name="syntax"></a>Sintassi  
  
```  
devenv SolutionFile | ProjectFile /upgrade  
```  
  
## <a name="arguments"></a>Argomenti  
 `SolutionFile`  
 Obbligatorio se si aggiorna un'intera soluzione e i relativi progetti. Il percorso e il nome di un file di soluzione. È possibile immettere solo il nome del file di soluzione oppure il percorso completo e il nome del file di soluzione. Se non esistono, la cartella o il nome file verranno creati.  
  
 `ProjectFile`  
 Obbligatorio se si esegue l'aggiornamento di un singolo progetto. Il percorso e il nome del file di progetto nella soluzione. È possibile immettere solo il nome del file di progetto oppure il percorso completo e il nome del file di progetto. Se non esistono, la cartella o il nome file verranno creati.  
  
## <a name="remarks"></a>Note  
 I backup vengono creati e copiati automaticamente in una directory denominata Backup creata nella directory corrente.  
  
 Per consentire l'aggiornamento di soluzioni o progetti inclusi nel controllo del codice sorgente è necessario estrarli.  
  
 Se si usa l'opzione `/upgrade`, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] non viene avviato. È possibile visualizzare i risultati dell'aggiornamento nel report di aggiornamento relativo al linguaggio di sviluppo della soluzione o del progetto. Non vengono restituiti messaggi di errore o informazioni sull'utilizzo. Per altre informazioni sull'aggiornamento di progetti in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], vedere [Conversione, migrazione e aggiornamento dei progetti di Visual Studio](../../porting/port-migrate-and-upgrade-visual-studio-projects.md).  
  
## <a name="example"></a>Esempio  
 Questo esempio aggiorna un file di soluzione denominato "MyProject.sln" nella cartella predefinita per le soluzioni di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
```  
devenv "MyProject.sln" /upgrade  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)