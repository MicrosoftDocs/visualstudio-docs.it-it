---
title: TargetCLR | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a69edb2730ff89a50dd45252258fc57e7205de3d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="targetclr"></a>TargetCLR
L'opzione **TargetCLR** specifica la versione di Common Language Runtime (CLR) da sottoporre a profilatura quando in un'applicazione è caricata più di una versione di CLR.  
  
 Per impostazione predefinita, gli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] vengono applicati alla prima versione di CLR caricata dall'applicazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
VSPerfCmd.exe {/Launch:AppName | /Attach:PID} /TargetCLR[:ClrVersion] [Options]   
```  
  
#### <a name="parameters"></a>Parametri  
 `ClrVersion`  
 Numero di versione di CLR. Usare il formato di versione **vN.N.NNNNN**.  
  
## <a name="required-options"></a>Opzioni obbligatorie  
 L'opzione **TargetCLR** può essere usata solo con le opzioni **Launch** o **Attach**.  
  
 **Launch:** `AppName`  
 Avvia l'applicazione specificata e avvia la profilatura.  
  
 **Attach:** `PID`  
 Avvia la profilatura del processo specificato.  
  
## <a name="example"></a>Esempio  
 In questo esempio, l'opzione TargetCLR viene usata per assicurarsi che venga sottoposta a profilatura la versione di CLR 4.0.11003.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003  
```