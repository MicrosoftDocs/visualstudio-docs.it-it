---
title: IDispatchEx::InvokeEx | Documenti Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.InvokeEx
apilocation:
- scrobj.dll
helpviewer_keywords:
- InvokeEx method
ms.assetid: d90783e6-4b89-4423-8a56-a9c8b4b2c813
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6302228b110e2b0a6296190079bf60b3d92980bd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idispatchexinvokeex"></a>IDispatchEx::InvokeEx
Fornisce l'accesso alle proprietà e metodi esposti da un `IDispatchEx` oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT InvokeEx(  
   DISPID id,  
   LCID lcid,  
   WORD wFlags,  
   DISPARAMS *pdp,  
   VARIANT *pVarRes,   
   EXCEPINFO *pei,   
   IServiceProvider *pspCaller   
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `id`  
 Identifica il membro. Usa `GetDispID` o `GetNextDispID` per ottenere l'identificatore di invio.  
  
 `lcid`  
 Contesto di impostazioni locali all'interno del quale devono essere interpretati gli argomenti. Il `lcid` viene passato a `InvokeEx` per consentire all'oggetto interpretare gli argomenti specifici delle impostazioni locali.  
  
 `wFlags`  
 I valori legali per `wFlags` sono:  
  
 DISPATCH_PROPERTYGET &#124; DISPATCH_METHOD &#124; DISPATCH_PROPERTYPUT &#124; DISPATCH_PROPERTYPUTREF &#124; DISPATCH_CONSTRUCT  
  
 Flag che descrivono il contesto del `InvokeEx` chiamare:  
  
|Valore|Significato|  
|-----------|-------------|  
|DISPATCH_METHOD|Il membro viene richiamato un metodo. Se una proprietà ha lo stesso nome, può essere impostato in questo e il flag DISPATCH_PROPERTYGET (definito da `IDispatch`).|  
|DISPATCH_PROPERTYGET|Il membro viene recuperato come un proprietà o un membro dati (definito da `IDispatch`).|  
|DISPATCH_PROPERTYPUT|Il membro viene modificato come un proprietà o un membro dati (definito da `IDispatch`).|  
|DISPATCH_PROPERTYPUTREF|Il membro viene modificato dall'assegnazione di un riferimento anziché un valore. Questo flag è valido solo quando la proprietà accetta un riferimento a un oggetto (definito da `IDispatch`).|  
|DISPATCH_CONSTRUCT|Il membro viene utilizzato come costruttore. (Si tratta di un nuovo valore definito da `IDispatchEx`). I valori legali per `wFlags` sono:<br /><br /> DISPATCH_PROPERTYGET DISPATCH_METHOD DISPATCH_PROPERTYPUT DISPATCH_PROPERTYPUTREF DISPATCH_CONSTRUCT|  
  
 `pdp`  
 Puntatore a una struttura contenente una matrice di argomenti, una matrice di DISPID per argomenti denominati e i conteggi del numero di elementi nelle matrici. Vedere il `IDispatch` documentazione per una descrizione completa della struttura DISPPARAMS.  
  
 `pVarRes`  
 Puntatore alla posizione in cui il risultato viene archiviato o Null se il chiamante prevede che nessun risultato. Questo argomento viene ignorato se DISPATCH_PROPERTYPUT o DISPATCH_PROPERTYPUTREF è specificato.  
  
 `pei`  
 Puntatore a una struttura contenente informazioni sull'eccezione. Se è necessario specificare questa struttura `DISP_E_EXCEPTION` viene restituito. Può essere Null. Vedere il `IDispatch` documentazione per una descrizione completa del `EXCEPINFO` struttura.  
  
 `pspCaller`  
 Puntatore a un oggetto provider di servizi fornito dal chiamante, che consente all'oggetto ottenere servizi da parte del chiamante. Può essere Null.  
  
 `IDispatchEx::InvokeEx`fornisce le stesse funzionalità di `IDispatch::Invoke` e aggiunge alcune estensioni:  
  
|||  
|-|-|  
|DISPATCH_CONSTRUCT|Indica che l'elemento viene utilizzato come un costruttore.|  
|`pspCaller`|Il `pspCaller` consente l'accesso agli oggetti per i servizi forniti dal chiamante. Servizi specifici possono essere gestiti dal chiamante se stesso o delegati ai chiamanti ulteriormente la catena di chiamate. Ad esempio, se un motore di script all'interno di un browser effettua un `InvokeEx` chiamata a un oggetto esterno, l'oggetto è possibile seguire il `pspCaller` catena per ottenere servizi dal motore di script o browser. (Si noti che la catena di chiamate non è quella della catena di creazione, noto anche come catena di contenitore o la catena di sito. La catena di creazione potrebbe essere disponibile tramite un altro meccanismo, ad esempio `IObjectWithSite`.)|  
|Puntatore `this`|Quando è impostata DISPATCH_METHOD `wFlags`, potrebbe esserci un parametro"denominato" per il valore "this". DISPID sarà DISPID_THIS e deve essere il primo parametro denominato.|  
  
 Inutilizzata `riid` parametro `IDispatch::Invoke` è stato rimosso.  
  
 Il `puArgArr` parametro `IDispatch::Invoke` è stato rimosso.  
  
 Vedere il `IDispatch::Invoke` documentazione per gli esempi seguenti:  
  
 "Chiama un metodo senza argomenti"  
  
 "Ottenere e impostare le proprietà"  
  
 "Passaggio di parametri"  
  
 "Le proprietà indicizzate"  
  
 "La generazione di eccezioni durante Invoke"  
  
 "Restituzione di errori"  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|||  
|-|-|  
|`S_OK`|Operazione completata.|  
|DISP_E_BADPARAMCOUNT|Il numero di elementi forniti per DISPPARAMS è diverso dal numero di argomenti accettati dal metodo o proprietà.|  
|DISP_E_BADVARTYPE|Uno degli argomenti in `rgvarg` non è un tipo variant valido.|  
|DISP_E_EXCEPTION|L'applicazione deve generare un'eccezione. In questo caso, la struttura passato `pei` deve essere compilato.|  
|DISP_E_MEMBERNOTFOUND|Il membro richiesto non esiste, la chiamata a o `InvokeEx` ha tentato di impostare il valore di una proprietà di sola lettura.|  
|DISP_E_NONAMEDARGS|Questa implementazione di `IDispatch` non supporta argomenti denominati.|  
|DISP_E_OVERFLOW|Uno degli argomenti in `rgvarg` non può essere assegnato forzatamente al tipo specificato.|  
|DISP_E_PARAMNOTFOUND|Uno dei parametri DISPID non corrisponde a un parametro del metodo.|  
|DISP_E_TYPEMISMATCH|Uno o più argomenti non possono essere forzati.|  
|DISP_E_UNKNOWNLCID|Il membro richiamato LCID LCID, e l'identificatore LCID non è riconosciuto. Se l'identificatore LCID non è necessario interpretare gli argomenti, questo errore non deve essere restituito.|  
|DISP_E_PARAMNOTOPTIONAL|È stato omesso un parametro obbligatorio.|  
  
## <a name="example"></a>Esempio  
  
```  
VARIANT var;  
   BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;  
   DISPPARAMS dispparamsNoArgs = {NULL, NULL, 0, 0};  
  
   // Assign to pdex and bstrName  
   if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)))  
   {  
      pdex->InvokeEx(dispid, LOCALE_USER_DEFAULT,  
         DISPATCH_PROPERTYGET, &dispparamsNoArgs,   
         &var, NULL, NULL);  
   }  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDispatchEx](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)