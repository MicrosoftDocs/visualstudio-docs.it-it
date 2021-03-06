---
title: Attività SetEnv | Microsoft Docs
description: Informazioni su come MSBuild usa l'attività SetEnv per impostare o eliminare il valore di una variabile di ambiente specificata.
ms.custom: SEO-VS-2020
ms.date: 11/05/2018
ms.topic: reference
f1_keywords:
- vc.task.setenv
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), tasks
- SetEnv task (MSBuild (C++))
ms.assetid: fd9e4225-68cb-4608-8b27-468b0218c936
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 76fc0d0dafac542ffde8656c643ec01b7ce23a39
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861673"
---
# <a name="setenv-task"></a>Attività SetEnv

Imposta o elimina il valore di una variabile di ambiente specificata.

## <a name="parameters"></a>Parametri

 Nella tabella che segue vengono descritti i parametri dell'attività **SetEnv**.

|Parametro|Descrizione|
|---------------|-----------------|
|**Nome**|Parametro **String** obbligatorio.<br /><br /> Nome di una variabile di ambiente.|
|**OutputEnvironmentVariable**|Parametro di output **stringa** facoltativo.<br /><br /> Contiene il valore assegnato alla variabile di ambiente specificata dal parametro **Name**.|
|**Prefix**|Parametro `Boolean` obbligatorio.<br /><br /> Se `true`, concatena il valore del parametro **Value** prima del valore della variabile di ambiente specificato dal parametro **Name** e quindi assegna il risultato alla variabile di ambiente. Se `false`, assegna solo il valore del parametro **Value** alla variabile di ambiente.|
|**Destinazione**|Parametro **stringa** facoltativo.<br /><br /> Specifica il percorso di archiviazione di una variabile di ambiente. Specificare "Utene" o "Computer".<br /><br /> Per altre informazioni, vedere [Enumerazione EnvironmentVariableTarget](xref:System.EnvironmentVariableTarget).|
|**Valore**|Parametro **stringa** facoltativo.<br /><br /> Valore assegnato alla variabile di ambiente specificata dal parametro **Name**. Se **Value** è vuoto e la variabile esiste, la variabile viene eliminata. Se la variabile non esiste, non si verifica alcun errore anche se non è possibile eseguire l'operazione.<br /><br /> Per altre informazioni, vedere [Metodo Environment::SetEnvironmentVariable](xref:System.Environment.SetEnvironmentVariable%2A).|

## <a name="see-also"></a>Vedi anche

- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
