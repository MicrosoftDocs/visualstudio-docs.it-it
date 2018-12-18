---
title: Metodo SetWefProcessId | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9dbd5a9ffb2ff9b3833dc8007fdfafb4b1a35857
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="setwefprocessid-method"></a>Metodo SetWefProcessId
  Fornisce l'identificatore di processo che verrà eseguito il contenuto Web estensioni Framework (WEF).  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT SetWefProcessId(  
    [in] DWORD dwProcessId  
);  
```  
  
#### <a name="parameters"></a>Parametri  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|*cui dwProcessId*|L'identificatore di processo che verrà utilizzato per eseguire il contenuto WEF.|  
  
## <a name="return-value"></a>Valore restituito  
 Valore HRESULT che indica se il metodo è stato completato correttamente.  
  
## <a name="remarks"></a>Note  
 Questo metodo deve essere chiamato dopo aver creato il processo del contenuto WEF ma prima dell'esecuzione di qualsiasi contenuto WEF.  
  
 Se si desidera l'ambiente di sviluppo per collegare un debugger al processo WEF contenuto, l'ambiente è necessario eseguire questa operazione nell'implementazione di questo metodo.  
  
  