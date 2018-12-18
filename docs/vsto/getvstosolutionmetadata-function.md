---
title: Funzione GetVstoSolutionMetadata | Documenti Microsoft
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
ms.openlocfilehash: 6c024d97d13c2794dd4fdaee6cfcd53d24c2e668
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="getvstosolutionmetadata-function"></a>Funzione GetVstoSolutionMetadata
  Questa API supporta l'infrastruttura Office e non può essere utilizzato direttamente dal codice.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT WINAPI GetVstoSolutionMetadata(  
    LPCWSTR lpwszSolutionMetadataKey,  
    ISolutionMetadata** ppSolutionInfo  
);  
```  
  
#### <a name="parameters"></a>Parametri  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|*lpwszSolutionMetadataKey*|Non usare.|  
|*ppSolutionInfo*|Non usare.|  
  
## <a name="return-value"></a>Valore restituito  
 Se la funzione ha esito positivo, restituisce **S_OK**. Se la funzione ha esito negativo, restituisce un codice di errore.  
  
  