---
title: Elemento TemplateGroupID (modelli di Visual Studio) | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateGroupID
helpviewer_keywords:
- TemplateGroupID element [Visual Studio Templates]
- <TemplateGroupID> element [Visual Studio Templates]
ms.assetid: bce7b49a-90bc-4691-aff3-a87e209f6d83
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 91631975d48f6e7e13646c428cdd5b5473bbeed2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="templategroupid-element-visual-studio-templates"></a>Elemento TemplateGroupID (modelli di Visual Studio)
Specifica il tipo di progetto in cui verranno visualizzati i modelli di elemento. Questo elemento è significativo quando [ShowByDefault (modelli di Visual Studio)](../extensibility/showbydefault-visual-studio-templates.md) è impostato su `false`. Quando [ShowByDefault (modelli di Visual Studio)](../extensibility/showbydefault-visual-studio-templates.md) è impostato su `true`, un modello di elemento è disponibile in tutti i tipi di progetto.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<TemplateGroupID >  
  
## <a name="syntax"></a>Sintassi  
  
```  
<TemplateGroupID> ... </TemplateGroupID>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
 Nessuno.  
  
### <a name="child-elements"></a>Elementi figlio  
 Nessuno.  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Classifica il modello in base alla categoria e definisce la modalità di visualizzazione nella finestra di dialogo **Nuovo progetto** o **Aggiungi nuovo elemento** .|  
  
## <a name="text-value"></a>Valore di testo  
 È necessario specificare un valore di testo.  
  
 Il testo specifica un identificatore per una categoria di modelli di elemento.  
  
## <a name="remarks"></a>Note  
 `TemplateGroupID` è un elemento.  
  
 Il valore di `TemplateGroupID` elemento viene utilizzato la registrazione del sistema del progetto (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<numero di versione >*\Projects\\) per filtrare i modelli visualizzati nel **Aggiungi nuovo elemento** la finestra di dialogo.  
  
|Valore di Visual C++|Significato|  
|------------------------|-------------|  
|VC-Native|Usato nei progetti nativi. È anche il valore predefinito se non è possibile determinare un tipo di progetto.|  
|VC-Managed|Usato per i progetti (/clr) gestiti|  
|VC-Windows|Usato per tutti i progetti per la piattaforma Windows (nativi/gestiti/Store)|  
|WinRT-Native-UAP|Usato per i progetti Store di Windows 10|  
|CodeSharing-Native|Usato per i progetti di elementi condivisi|  
|WinRT-Native-6.3|Usato per i progetti Store di Windows 8.1|  
|WinRT-Native-Phone-6.3|Usato per i progetti Windows Phone 8.1|  
|WinRT-Nativo|Usato per i progetti Store di Windows 8.0|  
|VC-Android|Usato per i progetti Android|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)