---
title: Elemento RequiredPlatformVersion (modelli di Visual Studio) | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 35a8dc6fa57dbe88ce1e30e9be58105f28fe5641
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="requiredplatformversion-element-visual-studio-templates"></a>Elemento RequiredPlatformVersion (modelli di Visual Studio)
Specifica la versione minima del sistema operativo che richiede il modello di progetto per funzionare correttamente. Questo elemento viene usato per i modelli di progetto che crea [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] app.  
  
 Il `RequiredPlatformVersion` valore viene confrontato direttamente con la versione del sistema operativo. Se il `RequiredPlatformVersion` è superiore alla versione del sistema operativo, il modello non viene visualizzato nel **nuovo progetto** la finestra di dialogo. Per specificare un modello per [!INCLUDE[win8](../debugger/includes/win8_md.md)] o versione successiva, impostare `RequiredPlatformVersion` a 6.2.0. Per specificare un modello per [!INCLUDE[win81](../debugger/includes/win81_md.md)] o versione successiva, impostare RequiredPlatformVersion a 6.3.0.  
  
 Modelli che specificano `RequiredPlatformVersion`= 8 sono compatibili con il cliente precedente [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] modelli.  
  
 VSTemplate  
TemplateData  
..... TargetPlatformName  
RequiredPlatformVersion  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
<RequiredPlatformVersion> OperatingSystem </RequiredPlatformVersion>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nessuno.  
  
### <a name="attributes"></a>Attributi  
 Nessuno.  
  
### <a name="child-elements"></a>Elementi figlio  
 Nessuno.  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[TemplatePlatformName](../extensibility/templatedata-element-visual-studio-templates.md)|Specifica la piattaforma a cui è destinato il modello di progetto.|  
  
## <a name="text-value"></a>Valore di testo  
 È necessario specificare un valore di testo.  
  
## <a name="remarks"></a>Note  
 Tale testo specifica la versione minima del sistema operativo richiesta dal modello.  
  
## <a name="example"></a>Esempio  
 Questo esempio specifica che il modello di progetto è destinato a [!INCLUDE[win8](../debugger/includes/win8_md.md)] o versioni successive.  
  
```xml  
<VSTemplate Type="Project" Version="3.0.0"    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <TargetPlatformName>Windows</TargetPlatformName>  
            <RequiredPlatformVersion>6.3.0</RequiredPlatformVersion>  
  
    </TemplateData>  
    <TemplateContent>  
  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento TargetPlatformName (modelli di Visual Studio)](../extensibility/targetplatformname-element-visual-studio-templates.md)   
 [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)   
 [Riferimenti sullo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)