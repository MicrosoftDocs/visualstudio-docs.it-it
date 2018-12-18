---
title: Metodo GetAutoInsertExtensions | Documenti Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: a53148b0130dd05f3ffc3360a518f9b2b66002e7
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
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
  
  