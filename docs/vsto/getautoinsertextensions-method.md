---
title: Metodo GetAutoInsertExtensions | Documenti Microsoft
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
ms.openlocfilehash: 67f6bfcb0ee38acf9abb604f28fa95eeaa605fde
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="getautoinsertextensions-method"></a>Metodo GetAutoInsertExtensions
  Ottiene informazioni sulle App per Office che devono essere inseriti automaticamente durante il debug.  
  
 Questo metodo è riservato per utilizzi futuri.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetAutoInsertExtensions(  
    [out, retval] SAFEARRAY(BSTR)* psaExtensionNames  
);  
```  
  
#### <a name="parameters"></a>Parametri  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|*psaExtensionNames*|I nomi di estensione delle App per Office.|  
  
## <a name="return-value"></a>Valore restituito  
 Valore HRESULT che indica se il metodo è stato completato correttamente.  
  
## <a name="remarks"></a>Note  
 Ogni app per Office deve essere inserito viene restituito come un'estensione di applicazione di Office, che corrisponde a un valore in HKEY_CURRENT_USER\Software\Microsoft\Office\WEF\Developer. L'host deve cercare questi valori nel Registro di sistema e quindi inserire automaticamente le estensioni.  
  
  