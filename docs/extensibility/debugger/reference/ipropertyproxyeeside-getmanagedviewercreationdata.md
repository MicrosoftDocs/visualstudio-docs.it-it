---
title: IPropertyProxyEESide::GetManagedViewerCreationData | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IPropertyProxyEESide::GetManagedViewerCreationData
helpviewer_keywords: IPropertyProxyEESide::GetManagedViewerCreationData
ms.assetid: c4eb4d60-8816-4d52-bc8d-dffd4f066499
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 53964947ac69cb9b4958bff0a8a6fd4ffa0a8afa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ipropertyproxyeesidegetmanagedviewercreationdata"></a>IPropertyProxyEESide::GetManagedViewerCreationData
Recupera informazioni sul Visualizzatore per questo tipo di proprietà per creare un'istanza di tale visualizzatore.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetManagedViewerCreationData(  
   BSTR*                  assemName,  
   IEEDataStorage**       assemBytes,  
   IEEDataStorage**       assemPdb,  
   BSTR*                  className,  
   ASSEMBLYLOCRESOLUTION* alr,  
   BOOL*                  replacementOk  
);  
```  
  
```csharp  
int GetManagedViewerCreationData(  
   out string                     assemName,  
   out IEEDataStorage             assemBytes,  
   out IEEDataStorage             assemPdb,  
   out string                     className,  
   out enum_ASSEMBLYLOCRESOLUTION alr,  
   out int                        replacementOk  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `assemName`  
 [out] Restituisce il nome dell'assembly che contiene questo oggetto.  
  
 `assemBytes`  
 [out] Restituisce un [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) oggetto contenente i byte dell'assembly di questo oggetto (questo è un valore null se nessun byte disponibili).  
  
 `assemPdb`  
 [out] Restituisce un `IEEDataStorage` oggetto contenente il simbolo di archiviazione le informazioni per questo oggetto (questo è un valore null se non è disponibile nessun archivio di simboli).  
  
 `className`  
 [out] Restituisce il nome della classe che contiene questo oggetto.  
  
 `alr`  
 [out] Restituisce un valore di [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md) enumerazione che indica la posizione dell'assembly.  
  
 `replacementOk`  
 [out] Restituisce zero (`TRUE`) se il valore di questo oggetto può essere modificato; zero (`FALSE`) se l'oggetto è di sola lettura.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo viene utilizzato per i visualizzatori di tipo per creare un'istanza di un visualizzatore gestito.  
  
## <a name="see-also"></a>Vedere anche  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)