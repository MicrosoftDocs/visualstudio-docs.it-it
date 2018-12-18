---
title: Attività VCMessage | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- vc.task.vcmessage
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- VCMessage task (MSBuild (Visual C++))
- MSBuild (Visual C++), VCMessage task
ms.assetid: 956675fd-05dc-40b4-856f-616145103498
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aa8ef67a4fa19bd715e73e50fcc268aee7a4df5d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="vcmessage-task"></a>Attività VCMessage
Registra gli avvisi e i messaggi di errore durante una compilazione.  
  
## <a name="remarks"></a>Note  
 Questa attività consente di implementare MSBuild per Visual C++ e non deve essere chiamata dall'utente. Per altre informazioni, vedere <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività **VCMessage**.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|**Argomenti**|Parametro **String** facoltativo.<br /><br /> Elenco delimitato da punto e virgola dei messaggi da visualizzare.|  
|**Codice**|Parametro **String** obbligatorio.<br /><br /> Un numero di errore che qualifica il messaggio.|  
|**Type**|Parametro **String** facoltativo.<br /><br /> Specifica il tipo di messaggio da generare. Specifica `"Warning"` per generare un messaggio di avviso o `"Error"` per generare un messaggio di errore.|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti alle attività](../msbuild/msbuild-task-reference.md)