---
title: 'IManagedAddin:: | Documenti Microsoft'
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
helpviewer_keywords: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: d6c657698f0d0e3a10871a7276a4eac2617d7874
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
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
  
  