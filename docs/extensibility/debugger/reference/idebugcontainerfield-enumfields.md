---
title: IDebugContainerField::EnumFields | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugContainerField::EnumFields
helpviewer_keywords: IDebugContainerField::EnumFields method
ms.assetid: 9e5e681b-ad49-4c62-bd95-4afa11d61a57
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a262d2f4aa90bc9ae638fb6cfbfe8af605f2446a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcontainerfieldenumfields"></a>IDebugContainerField::EnumFields
Crea un enumeratore per i campi del contenitore.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT EnumFields(   
   FIELD_KIND         dwKindFilter,  
   FIELD_MODIFIERS    dwModifiersFilter,  
   LPCOLESTR          pszNameFilter,  
   NAME_MATCH         nameMatch,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumFields(  
   enum_ FIELD_KIND      dwKindFilter,   
   enum_ FIELD_MODIFIERS dwModifiersFilter,   
   string                pszNameFilter,   
   NAME_MATCH            nameMatch,   
   out IEnumDebugFields  ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwKindFilter`  
 [in] Una combinazione di [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) le costanti che selezionano i campi da enumerare. Tipi di campo è possono descrivere i tipi di archiviazione, ad esempio classe o informazioni primitive o specifiche, ad esempio locale, parametro o puntatore "this".  
  
 `dwModifiersFilter`  
 [in] Una combinazione di [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) le costanti che selezionano i campi da enumerare. Modificatori di campo possono essere le autorizzazioni di accesso, ad esempio informazioni sull'archiviazione, ad esempio finale, statico o virtuale pubblico o privato.  
  
 `pszNameFilter`  
 [in] Il nome del campo da enumerare. Può trattarsi di un valore null se tutti i campi devono essere restituiti.  
  
 `nameMatch`  
 [in] Un valore di [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) enumerazione che controlla se la ricerca sia tra maiuscole e minuscole.  
  
 `ppEnum`  
 [out] Restituisce un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) oggetto che rappresenta l'elenco dei campi. Restituisce un valore null se non sono presenti campi.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK o S_FALSE se non sono presenti campi. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il `dwKindFilter`, `dwModifiersFilter`, e `pszNameFilter` i parametri possono essere combinati, ad esempio, per selezionare tutti i metodi pubblici virtuali denominati "MyMethod".  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)   
 [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)