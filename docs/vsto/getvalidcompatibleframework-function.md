---
title: Funzione GetValidCompatibleFramework | Documenti Microsoft
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
ms.openlocfilehash: b28587b44dd98630538bc8d6d04c5bc6049e3ca9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="getvalidcompatibleframework-function"></a>Funzione GetValidCompatibleFramework
  Questa API supporta l'infrastruttura Office e non può essere utilizzato direttamente dal codice.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT WINAPI GetValidCompatibleFramework(  
    LPCWSTR lpwszCompatibleFrameworksXML,  
    BSTR* pbstrValidFrameworkTag  
);  
```  
  
#### <a name="parameters"></a>Parametri  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|*lpwszCompatibleFrameworksXML*|Non usare.|  
|*pbstrValidFrameworkTag*|Non usare.|  
  
## <a name="return-value"></a>Valore restituito  
 Se la funzione ha esito positivo, restituisce **S_OK**. Se la funzione ha esito negativo, restituisce un codice di errore.  
  
  