---
title: Attività SetEnv | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vc.task.setenv
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), tasks
- SetEnv task (MSBuild (Visual C++))
ms.assetid: fd9e4225-68cb-4608-8b27-468b0218c936
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ccd67a4bf70e05f0661277db05430615afbcfdad
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47531453"
---
# <a name="setenv-task"></a>Attività SetEnv
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [attività SetEnv](https://docs.microsoft.com/visualstudio/msbuild/setenv-task).  
  
  
Imposta o elimina il valore di una variabile di ambiente specificata.  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività **SetEnv**.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|**Name**|Parametro **String** obbligatorio.<br /><br /> Nome di una variabile di ambiente.|  
|**OutputEnvironmentVariable**|Parametro di output **String** facoltativo.<br /><br /> Contiene il valore assegnato alla variabile di ambiente specificata dal parametro **Name**.|  
|**Prefix**|Parametro `Boolean` obbligatorio.<br /><br /> Se `true`, concatena il valore del parametro **Value** prima del valore della variabile di ambiente specificato dal parametro **Name** e quindi assegna il risultato alla variabile di ambiente. Se `false`, assegna solo il valore del parametro **Value** alla variabile di ambiente.|  
|**Destinazione**|Parametro **String** facoltativo.<br /><br /> Specifica il percorso di archiviazione di una variabile di ambiente. Specificare "`User`" o "`Machine`".<br /><br /> Per altre informazioni, vedere "Enumerazione EnvironmentVariableTarget" sul sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**Valore**|Parametro **String** facoltativo.<br /><br /> Valore assegnato alla variabile di ambiente specificata dal parametro **Name**. Se **Value** è vuoto e la variabile esiste, la variabile viene eliminata. Se la variabile non esiste, non si verifica alcun errore anche se non è possibile eseguire l'operazione.<br /><br /> Per altre informazioni, vedere "Metodo Environment::SetEnvironmentVariable" sul sito Web [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti alle attività](../msbuild/msbuild-task-reference.md)



