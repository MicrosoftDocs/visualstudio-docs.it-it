---
title: IActiveScriptProperty::GetProperty | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptProperty.GetProperty
apilocation: scrobj.dll
helpviewer_keywords: GetProperty method, IActiveScriptProperty interface
ms.assetid: a43383db-b148-4d76-83bd-4f0e899b7cb1
caps.latest.revision: "24"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d55fb2d816931a74827d318e13860b3f97f0fd23
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptpropertygetproperty"></a>IActiveScriptProperty::GetProperty
Ottiene la proprietà specificata dal parametro.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetProperty(  
// The property value:  
    uint dwProperty,    
// Not used:  
    IntPtr pvarIndex,    
// The value of the property:   
    out object pvarValue,    
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwProperty`  
 Il valore della proprietà da ottenere.  
  
 `pvarIndex`  
 Non usato.  
  
 `pvarValue`  
 Valore della proprietà.  
  
 I valori consentiti per `dwProperty` sono descritti nella tabella seguente.  
  
|Costante|Valore|Significato|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|Forza il motore di script per suddividere in modalità di integer anziché modalità punto a virgola mobile.|  
|SCRIPTPROP_STRINGCOMPAREINSTANCE|0x00003001|Consente la funzione di confronto di stringa del motore di scripting da sostituire.|  
|SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION|0x70000002|Segnala al motore di scripting non altri motori di script esistenti per contribuire all'oggetto globale.|  
|SCRIPTPROP_INVOKEVERSIONING|0x00004000|Forza il [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motore di script per selezionare un set di funzionalità del linguaggio è supportata. Il set predefinito di funzionalità del linguaggio supportato dal [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] è equivalente al set di funzionalità del linguaggio che è disponibile nella versione 5.7 di motore di script di [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motore di script.|  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Operazione completata.|  
|`E_INVALIDARG`|Un argomento non è valido.|  
|`E_UNEXPECTED`|La chiamata non era previsto (ad esempio, il motore di script non è ancora caricato o inizializzato).|  
  
## <a name="remarks"></a>Note  
 L'host può utilizzare la proprietà SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION per informare un motore di script non altri motori di script esistenti per contribuire all'oggetto globale. Ad esempio, Internet Explorer è possibile informare il [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motore contenente solo la pagina viene eseguito il rendering [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] script. Pertanto, solo il [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motore è possibile aggiungere nuove proprietà alla finestra oggetto globale e nessun modulo di gestione di Visual Basic Scripting Edition (VBScript) per eseguire la stessa. Il motore possibile ignorare questo flag o usarlo per ottimizzare la gestione dei nuovi membri aggiunti all'oggetto globale.  
  
 L'host può utilizzare la proprietà SCRIPTPROP_INVOKEVERSIONING per selezionare il set di funzionalità del linguaggio per essere supportati quando il [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motore di scripting viene avviato. Se questa proprietà è impostata su 1 (SCRIPTLANGUAGEVERSION_5_7), le funzionalità del linguaggio disponibili sono identici a quelli visualizzati nella versione 5.7 il [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motore di script. Se è impostato su 2 (SCRIPTLANGUAGEVERSION_5_8), le funzionalità del linguaggio disponibili sono quelli visualizzati nella versione 5.7 Oltre a funzionalità che sono stati aggiunti nella versione 5.8. Per impostazione predefinita, questa proprietà è impostata su 0 (SCRIPTLANGUAGEVERSION_DEFAULT), che equivale a set di funzionalità del linguaggio che è disponibile nella versione 5.7, a meno che l'host supporta un comportamento predefinito diverso. Ad esempio, Internet Explorer 8 opts nel [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] le funzionalità del linguaggio è supportate dalla versione 5.8 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motore di script per impostazione predefinita quando la modalità di documento per Internet Explorer 8 è "Standard di Internet Explorer 8".  
  
## <a name="see-also"></a>Vedere anche  
 [Definizione della compatibilità del documento](http://msdn.microsoft.com/library/cc288325)   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [Informazioni sulla versione](../../javascript/reference/javascript-version-information.md)