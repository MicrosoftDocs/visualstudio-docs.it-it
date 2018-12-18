---
title: IActiveScriptProperty::SetProperty | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptProperty.SetProperty
apilocation:
- scrobj.dll
helpviewer_keywords:
- SetProperty method, IActiveScriptProperty interface
ms.assetid: 0ba429c5-04a3-4505-bc5f-69c505dfca91
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bc9b5f4c0d02789988bb41f46417651414beed7f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptpropertysetproperty"></a>IActiveScriptProperty::SetProperty
Imposta la proprietà specificata dal parametro.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT SetProperty(  
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
 Valore della proprietà da impostare.  
  
 `pvarIndex`  
 Non usato.  
  
 `pvarValue`  
 Valore della proprietà.  
  
 I valori consentiti per `dwProperty` sono descritti nella tabella seguente.  
  
|Costante|Valore|Significato|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|Forza il motore di script per suddividere in modalità di integer anziché modalità punto a virgola mobile. Il valore predefinito è `False`.|  
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
 Per attivare o disattivare la divisione di interi, richiamare `SetProperty` e convertire un `Boolean` per un `Object`. Per impostazione predefinita, il valore della proprietà è `False`. Se si imposta su `True`, operazioni di divisione restituirà solo numeri interi.  
  
 Per abilitare o disabilitare il confronto di stringa personalizzato, è possibile richiamare `SetProperty` e passare un `Object` valore. L'oggetto che si passa a deve implementare l'interfaccia [interfaccia IActiveScriptStringCompare](../../winscript/reference/iactivescriptstringcompare-interface.md). Il [StrComp](../../winscript/reference/iactivescriptstringcompare-strcomp.md) metodo il [interfaccia IActiveScriptStringCompare](../../winscript/reference/iactivescriptstringcompare-interface.md) interfaccia viene chiamata ogni volta che viene eseguita una funzione di confronto di stringa.  
  
 Per selezionare il set di funzionalità del linguaggio è supportata quando il [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motore di script è inizializzata, richiamare `SetProperty` e passare un valore che corrisponde alla funzionalità del linguaggio impostata per essere abilitata per SCRIPTPROP_INVOKEVERSIONING. Se questa proprietà è impostata su 1 (SCRIPTLANGUAGEVERSION_5_7), le funzionalità del linguaggio disponibili sono identici a quelli visualizzati nella versione 5.7 il [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motore di script. Se è impostato su 2 (SCRIPTLANGUAGEVERSION_5_8), le funzionalità del linguaggio disponibili sono quelli visualizzati nella versione 5.7 Oltre a nuove funzionalità che sono stati aggiunti nella versione 5.8. Per impostazione predefinita, questa proprietà è impostata su 0 (SCRIPTLANGUAGEVERSION_DEFAULT), che equivale a set di funzionalità del linguaggio che è disponibile nella versione 5.7, a meno che l'host supporta un comportamento predefinito diverso. Ad esempio, Internet Explorer 8 opts nel [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] funzionalità del linguaggio che sono supportate dalla versione 5.8 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motore di script per impostazione predefinita, quando la modalità documento predefinito per Internet Explorer 8 è la modalità "Standard di Internet Explorer 8". Cambio di modalità documento di Internet Explorer 8 a standard di Internet Explorer 7 o dalla modalità Reimposta il [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motore di script per supportare solo il set di funzionalità del linguaggio presenti nella versione 5.7 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motore di script.  
  
> [!NOTE]
>  SCRIPTPROP_INVOKEVERSIONING deve essere impostata solo quando il [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motore di script è inizializzato.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come forzare il motore di script per utilizzare la divisione di interi e come consentire l'overload della funzione di confronto.  
  
```c#  
BMLScriptEngine bmlScriptEngine = new BMLScriptEngine();  
IActiveScriptProperty scriptProperties = bmlScriptEngine as   
    IActiveScriptProperty;  
  
// Force the scripting engine to use integer division.  
Boolean enableIntegerDivision = true;  
Object vtIntegerDivInstance = (Object)enableIntegerDivision;  
                scriptProperties.SetProperty(SCRIPTPROP_INTEGERDIVISION,   
    System.IntPtr.Zero, ref vtIntegerDivInstance);  
  
// Allow overloading of the compare function.  
BMLScriptStringCompare bmlScriptStringCompareInstance = new   
    BMLScriptStringCompare();  
Object vtStrCmpInstance = (Object)bmlScriptStringCompareInstance;  
scriptProperties.SetProperty(SCRIPTPROP_STRCOMPINST,   
    System.IntPtr.Zero, ref vtStrCmpInstance);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Definizione della compatibilità del documento](http://msdn.microsoft.com/library/cc288325)   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [Informazioni sulla versione](../../javascript/reference/javascript-version-information.md)