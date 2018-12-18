---
title: Interfaccia IDispatchEx | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDispatchEx interface, about IDispatchEx
- IDispatchEx interface
ms.assetid: 37a3303f-f78e-4b5b-aac8-b836c92819de
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9a100a193f5e3abcb076fb8aaf3d64a0d0c38833
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idispatchex-interface"></a>Interfaccia IDispatchEx
`IDispatchEx`, un'estensione del `IDispatch` supporta funzionalità di interfaccia, appropriati per i linguaggi dinamici, ad esempio linguaggi di scripting. Questa sezione viene descritto il `IDispatchEx` interfaccia stessa, le differenze tra `IDispatch` e `IDispatchEx`e la logica alla base per le estensioni. È previsto che abbiano familiari con i lettori `IDispatch` e di avere a disposizione il `IDispatch` documentazione.  
  
## <a name="remarks"></a>Note  
 `IDispatch`essenzialmente è stato sviluppato per Microsoft Visual Basic. La limitazione principale di `IDispatch` è che presuppone che gli oggetti sono statici. In altre parole, poiché gli oggetti non viene modificata in fase di esecuzione, le informazioni sul tipo possono completamente descriverli in fase di compilazione. I modelli in fase di esecuzione dinamici presenti nei linguaggi di scripting, ad esempio Visual Basic Scripting Edition (VBScript) e [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] e modelli a oggetti, ad esempio HTML dinamico è necessaria un'interfaccia più flessibile.  
  
 `IDispatchEx`è stato sviluppato per fornire tutti i servizi di `IDispatch` nonché alcune estensioni che sono appropriate per le lingue ad associazione tardiva più dinamiche, ad esempio linguaggi di scripting. Le funzionalità aggiuntive di `IDispatchEx` oltre a quelle fornite da `IDispatch` sono:  
  
-   Aggiungere nuovi membri a un oggetto ("expando"), utilizzare `GetDispID` con il `fdexNameEnsure` flag.  
  
-   Eliminare i membri di un oggetto, utilizzare `DeleteMemberByName` o `DeleteMemberByDispID`.  
  
-   Le operazioni di invio tra maiuscole e minuscole, utilizzare `fdexNameCaseSensitive` o `fdexNameCaseInsensitive`.  
  
-   Ricerca di membri con nome implicito, utilizzare `fdexNameImplicit`.  
  
-   Enumerare i DISPID di un oggetto, utilizzare `GetNextDispID`.  
  
-   Mappa da DISPID nel nome dell'elemento, utilizzare `GetMemberName`.  
  
-   Ottenere le proprietà di membri dell'oggetto, utilizzare `GetMemberProperties`.  
  
-   Chiamata del metodo con `this` puntatore, utilizzare `InvokeEx` con DISPATCH_METHOD.  
  
-   Consenti browser che supportano il concetto di spazi dei nomi per ottenere l'elemento padre dello spazio del nome di un oggetto, utilizzare `GetNameSpaceParent`.  
  
 Gli oggetti che supportano `IDispatchEx` potrebbero inoltre supportare `IDispatch` per garantire la compatibilità con le versioni precedenti. La natura dinamica di oggetti che supportano `IDispatchEx` presenta alcune implicazioni per la `IDispatch` interfaccia di tali oggetti. Ad esempio, `IDispatch` supposizione il seguente:  
  
-   Il membro e il parametro DISPID devono rimanere costanti per la durata dell'oggetto. In questo modo un client di ottenere i DISPID una sola volta e memorizzarli nella cache per un uso successivo.  
  
 Poiché `IDispatchEx` consente l'aggiunta e l'eliminazione di membri, il set dei DispId valido non rimane costante. Tuttavia, `IDispatchEx` richiede che il mapping tra nome DISPID e dei membri rimangono costanti. Ciò significa che se un membro viene eliminato:  
  
-   DISPID non può essere riutilizzato fino a quando non viene creato un membro con lo stesso nome.  
  
-   DISPID deve rimanere valido per `GetNextDispID`.  
  
-   DISPID deve essere accettato normalmente da uno qualsiasi del `IDispatch` o `IDispatchEx` metodi, ovvero deve riconoscere il membro come eliminato e restituire un codice di errore appropriato (in genere DISP_E_MEMBERNOTFOUND o S_FALSE).  
  
## <a name="examples"></a>Esempi  
 Questo [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] codice di test () la funzione esegue le operazioni seguenti:  
  
-   Crea un nuovo oggetto chiamando il `Object` costruttore e assegna un puntatore al nuovo oggetto per l'oggetto variabile.  
  
-   Crea un nuovo elemento denominato Elem nell'oggetto e assegna a questo elemento di un puntatore a cat la funzione.  
  
-   Chiama questa funzione. Poiché viene chiamato un metodo, il `this` puntatore fa riferimento all'oggetto obj. La funzione aggiunge un nuovo elemento barra, per l'oggetto.  
  
 Il codice HTML completo è:  
  
```  
<html>  
<body>  
<script type="text/javascript">  
function cat()  
{  
   // Create new element and assign the value 10  
   this.Bar = 10;  
}  
  
function test()  
{  
   // Construct new object  
   Obj = new Object();  
  
   // Create new element and assign function pointer  
   Obj.Elem = cat;  
  
   // Call Elem method ("this" == Obj)  
   Obj.Elem();  
  
   // Obj.Bar now exists  
}  
test();  
</script>  
</body>  
</html>  
```  
  
 Un controllo inserito nella stessa pagina Web sono in grado di ottenere un puntatore di recapito per i motori di script da browser. Il controllo può implementare quindi il test (funzione):  
  
```  
<html>  
<body>  
<script type="text/javascript">  
function cat()  
{  
   // Create new element and assign the value 10  
   this.Bar = 10;  
}  
</script>  
<object id="test" <CLASSID="CLSID:9417DB5D-FA2A-11D0-8CB3-00C04FC2B085">>  
</object>  
</body>  
</html>  
```  
  
 Dal controllo del codice, testare, esegue la stessa operazione come la [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] funzione `test()`. Si noti che queste chiamate di invio vengono eseguite in esecuzione [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] del motore e modificare lo stato del motore di:  
  
-   Ottiene il puntatore di recapito per la funzione cat tramite `GetDispID()`.  
  
-   Ottiene l'oggetto di funzione usando il puntatore di invio `GetDispID()`.  
  
-   Costruisce un oggetto chiamando la funzione di oggetto con `InvokeEx()` e ottiene un puntatore dispatch all'oggetto appena creata.  
  
-   Crea un nuovo elemento, Elem, in cui l'oggetto usando `GetDispID()` con il `fdexNameEnsure` flag.  
  
-   Inserisce il puntatore di invio in gatto in elemento usando `InvokeEx()`.  
  
-   Chiama il puntatore di invio a cat come metodo chiamando `InvokeEx()` e passando il puntatore di spedizione per l'oggetto costruito come il `this` puntatore.  
  
-   Il metodo cat crea un nuovo elemento barra corrente `this` oggetto.  
  
-   Verifica che il nuovo elemento, a barre, è stato creato nell'oggetto costruito con l'enumerazione tramite gli elementi utilizzando `GetNextDispID()`.  
  
 Il codice per il controllo di test:  
  
```  
   BOOL test(IDispatchEx *pdexScript)  
   {  
      HRESULT hr;  
      VARIANT var;  
      DISPID dispid, putid;  
      BOOL retval = FALSE;  
      BSTR bstrName = NULL;  
      IDispatch   *pdispObj = NULL, *pdispCat = NULL;  
      IDispatchEx *pdexObj = NULL;  
      DISPPARAMS dispparams, dispparamsNoArgs = {NULL, NULL, 0, 0};  
  
      // Get dispatch pointer for "cat"  
      bstrName = SysAllocString(OLESTR("cat"));  
         if (bstrName == NULL) goto LDone;  
      hr = pdexScript->GetDispID(bstrName, 0, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
      hr = pdexScript->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_PROPERTYGET, &dispparamsNoArgs,   
         &var, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
      pdispCat = var.pdispVal;  
  
      // Create object by calling "Object" constructor  
      bstrName = SysAllocString(OLESTR("Object"));  
         if (NULL == bstrName) goto LDone;  
      hr = pdexScript->GetDispID(bstrName, 0, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
      hr = pdexScript->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_CONSTRUCT, &dispparamsNoArgs,   
         &var, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
      pdispObj = var.pdispVal;  
      hr = pdispObj->QueryInterface(IID_IDispatchEx, (void **)&pdexObj);  
         if (FAILED(hr)) goto LDone;  
  
      // Create new element in object  
      bstrName = SysAllocString(OLESTR("Elem"));  
         if (NULL == bstrName) goto LDone;  
      hr = pdexObj->GetDispID(bstrName, fdexNameEnsure, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
  
      // Assign "cat" dispatch pointer to element  
      putid = DISPID_PROPERTYPUT;  
      var.vt = VT_DISPATCH;  
      var.pdispVal = pdispCat;  
      dispparams.rgvarg = &var;  
      dispparams.rgdispidNamedArgs = &putid;  
      dispparams.cArgs = 1;  
      dispparams.cNamedArgs = 1;  
      hr = pdexObj->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_PROPERTYPUTREF, &dispparams,  
         NULL, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
  
      // Invoke method with "this" pointer  
      putid = DISPID_THIS;  
      var.vt = VT_DISPATCH;  
      var.pdispVal = pdispObj;  
      dispparams.rgvarg = &var;  
      dispparams.rgdispidNamedArgs = &putid;  
      dispparams.cArgs = 1;  
      dispparams.cNamedArgs = 1;  
      hr = pdexObj->InvokeEx(dispid, LOCALE_USER_DEFAULT,  
         DISPATCH_METHOD, &dispparams,  
            NULL, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
  
      // Confirm that new element "Bar" is in object  
      hr = pdexObj->GetNextDispID(fdexEnumAll, DISPID_STARTENUM, &dispid);  
      while (hr == NOERROR)  
      {  
            hr = pdexObj->GetMemberName(dispid, &bstrName);  
            if (FAILED(hr)) goto LDone;  
            retval = !wcscmp(bstrName, OLESTR("Bar"));  
            SysFreeString(bstrName);  
            bstrName = NULL;  
            if (retval) goto LDone;  
         hr = pdexObj->GetNextDispID(fdexEnumAll, dispid, &dispid);  
      }  
LDone:  
   SysFreeString(bstrName);  
   if (pdispCat != NULL)  
      pdispCat->Release();  
   if (pdispObj != NULL)  
      pdispObj->Release();  
   if (pdexObj != NULL)  
      pdexObj->Release();  
  
   return retval;  
   }  
```  
  
## <a name="methods"></a>Metodi  
 [Metodi IDispatchEx](../../winscript/reference/idispatchex-methods.md)