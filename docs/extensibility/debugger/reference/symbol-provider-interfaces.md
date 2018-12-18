---
title: Interfacce del Provider di simboli | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interfaces, symbol handler
- symbol handler, interfaces
- symbol handler, evaluating variables
ms.assetid: 4201f10e-c9f7-4b38-bb45-40fe0082d5bf
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f2b3ec92ce76a3218c646c51ccb28d99322baf93
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="symbol-provider-interfaces"></a>Interfacce del Provider di simboli
Di seguito sono le interfacce di gestione di simboli per il [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)].  
  
## <a name="discussion"></a>Discussione  
 Queste interfacce vengono utilizzate per valutare le variabili in uno stack di chiamate durante la modalità di interruzione. Vengono implementati solo per i provider di simboli di common language runtime (SP).  
  
|Interfaccia|Implementato da|Descrizione|  
|---------------|--------------------|-----------------|  
|[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)|SP|Rappresenta l'indirizzo di un elemento.|  
|[IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)|SP|Rappresenta l'indirizzo di un elemento, fornendo l'accesso all'ID di processo.|  
|[IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)|SP|Rappresenta un simbolo di matrice o un tipo di matrice.|  
|[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)|SP|Rappresenta un simbolo di classe o un tipo di classe.|  
|[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)|SP|Rappresenta un provider di simboli COM+ con metodi specifici al codice gestito.|  
|[IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)|SP|Rappresenta un provider di simboli COM+ con metodi specifici al codice gestito ed estende il **IDebugComPlusSymbolProvider**.|  
|[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)|SP|Rappresenta un simbolo o un tipo che è un contenitore per altri tipi o i simboli.|  
|[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)|SP|Rappresenta un attributo personalizzato che può essere collegato a un simbolo.|  
|[IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)|SP|Rappresenta una query per gli attributi personalizzati per un tipo o metodo.|  
|[IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)|SP|Fornisce l'accesso agli attributi personalizzati su un simbolo.|  
|[IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)|SP|L'interfaccia di base per qualsiasi tipo che può essere determinato in fase di esecuzione.|  
|[IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)|SP|Rappresenta un campo dinamico per una [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) oggetto.|  
|[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)|SP|Rappresenta un tipo di enumerazione.|  
|[IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)|SP|Estende i tipi di campi disponibili per il supporto dei generics codice gestito.|  
|[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)|SP|La classe base per tutti i campi. rappresenta una descrizione di un tipo o un simbolo.|  
|[IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)|SP|Rappresenta la definizione di un campo per un tipo generico di codice gestito.|  
|[IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)|SP|Rappresenta un'istanza di un campo per un tipo generico di codice gestito.|  
|[IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)|SP|Rappresenta un parametro per un tipo generico di codice gestito.|  
|[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)|SP|Rappresenta un metodo.|  
|[IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)|SP|Rappresenta un modificatore facoltativo di debug.|  
|[IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)|SP|Rappresenta un puntatore.|  
|[IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)|SP|Rappresenta un valore di enumerazione di tipo primitivo da un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfaccia.|  
|[IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)|SP|Rappresenta una proprietà di una classe di codice gestito che è possibile ottenere o impostare.|  
|[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)|SP|Rappresenta un provider di simboli che fornisce tipi e simboli.|  
|[IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)|SP|Rappresenta un provider di simboli con accesso diretto alle interfacce di simbolo di metadati e componenti di base.|  
|[IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)|SP|Rappresenta la possibilità di creare un campo che rappresenta un tipo.|  
|[IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)|SP|Estende il **IDebugTypeFieldBuilder** per essere in grado di creare tipi di matrice.|  
|[IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)|SP|Rappresenta una raccolta di [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) oggetti.|  
|[IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)|SP|Rappresenta una raccolta di [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) oggetti.|  
|[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)|SP|Rappresenta una raccolta di [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) oggetti.|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)