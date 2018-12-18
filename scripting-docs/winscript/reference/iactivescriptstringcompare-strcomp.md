---
title: IActiveScriptStringCompare::StrComp | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptStringCompare.StrComp
apilocation: scrobj.dll
helpviewer_keywords: StrComp method, IActiveScriptStringCompare interface
ms.assetid: 124d1281-8037-4766-a2a1-61244ac1f114
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1b92b29f4e40f5e8de567337957aabbcb3c057fd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptstringcomparestrcomp"></a>IActiveScriptStringCompare::StrComp
Definisce il metodo di confronto di stringhe per il motore di script.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT StrComp(  
// The first string:  
    [in] BSTR bszStr1,    
// The second string:   
    [in] BSTR bszStr2,    
// The result of the comparison:  
    [out, retval] LONG* iRet   
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `bszStr1`  
 Prima stringa.  
  
 `bszStr2`  
 Seconda stringa.  
  
 `iRet`  
 Il risultato del confronto. 0 se `bszStr1` e `bszStr2`sono identici, -1 se `bszStr1`  <  `bszStr2`; 1 se `bszStr1`  >  `bszStr2`.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Operazione completata.|  
|`E_INVALIDARG`|Un argomento non è valido.|  
|`E_UNEXPECTED`|La chiamata non era previsto (ad esempio, il motore di script non è ancora caricato o inizializzato).|  
  
## <a name="remarks"></a>Note  
 Questo metodo viene chiamato ogni volta che viene eseguito un confronto tra stringhe.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come eseguire l'overload della funzione di confronto di string. L'overload è consentita quando si utilizza [IActiveScriptProperty::SetProperty](../../winscript/reference/iactivescriptproperty-setproperty.md) impostare SCRIPTPROP_STRINGCOMPAREINSTANCE.  
  
```cpp#  
cpp_quote("// {58562769-ED52-42f7-8403-4963514E1F11}")  
cpp_quote("DEFINE_GUID(IID_IActiveScriptStringCompare, 0x58562769,   
    0xED52, 0x42f7, 0x84, 0x03, 0x49, 0x63, 0x51, 0x4E, 0x1F, 0x11);")  
cpp_quote("")  
  
cpp_quote("#define SCRIPTPROP_INTEGERMODE              0x00003000")  
cpp_quote("#define SCRIPTPROP_STRINGCOMPAREINSTANCE    0x00003001")  
cpp_quote("")  
interface IActiveScriptStringCompare;  
[  
         object,  
         uuid(58562769-ED52-42f7-8403-4963514E1F11),  
         pointer_default(unique)  
]  
interface IActiveScriptStringCompare : IUnknown  
{  
        // StrComp  
        //     bszStr1: first string  
        //     bszStr2: second string  
        //     iRet: 0 if identical, -1 if bszStr1 < bszStr2, 1 if   
        //         bszStr1 > bszStr2  
        //            
        //     Return values:  
        //         S_OK: Success  
        //         E_NOTIMPL: Not implemented  
        //  
        HRESULT StrComp(  
                [in] BSTR bszStr1,  
                [in] BSTR bszStr2,  
                [out, retval] LONG* iRet  
        );  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptStringCompare](../../winscript/reference/iactivescriptstringcompare-interface.md)