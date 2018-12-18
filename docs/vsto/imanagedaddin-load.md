---
title: 'IManagedAddin:: | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords: ''
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 545560c5f02437925c2f93e9c6dc3113e1cddd0b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="imanagedaddinload"></a>IManagedAddin::Load
  Chiamato quando viene caricato un componente aggiuntivo VSTO gestito.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT Load([in] BSTR bstrManifestURL,   
             [in] IDispatch *pdispApplication);  
```  
  
#### <a name="parameters"></a>Parametri  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|*bstrManifestURL*|Percorso completo del manifesto per il componente aggiuntivo VSTO.|  
|*pdispApplication*|Puntatore a IDispatch che rappresenta l'applicazione host che sta caricando il componente aggiuntivo VSTO.|  
  
## <a name="return-value"></a>Valore restituito  
 Valore HRESULT che indica se il metodo è stato completato correttamente.  
  
## <a name="remarks"></a>Note  
 Un manifesto è un file (in genere, un file XML) che fornisce informazioni usate per consentire il caricamento del componente aggiuntivo VSTO. Un manifesto, ad esempio, può specificare il percorso dell'assembly del componente aggiuntivo VSTO e la classe del punto di ingresso per creare un'istanza quando viene caricato il componente aggiuntivo VSTO.  
  
 Il *bstrManifestURL* parametro contiene il valore della `Manifest` voce sotto HKEY_CURRENT_USER\Software\Microsoft\Office\\*\<nome applicazione >*\Addins\\*\<ID componente aggiuntivo >* chiave del Registro di sistema per il componente aggiuntivo VSTO. Per altre informazioni, vedere [IManagedAddin Interface](../vsto/imanagedaddin-interface.md).  
  
 Implementare il metodo [IManagedAddIn::Load](../vsto/imanagedaddin-load.md) per eseguire attività come ad esempio la configurazione del dominio dell'applicazione e dei criteri di sicurezza per il componente aggiuntivo VSTO che viene caricato.  
  
## <a name="see-also"></a>Vedere anche  
 [IManagedAddin Interface](../vsto/imanagedaddin-interface.md)   
 [IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)  
  
  