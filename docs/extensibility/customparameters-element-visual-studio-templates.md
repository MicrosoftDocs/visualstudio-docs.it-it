---
title: Elemento CustomParameters (modelli di Visual Studio) | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameters
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: cf3efc91-1532-4022-bbb8-a18658424fee
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4c09d320b1a9185e79e36d54ff0363219d3dabc6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="customparameters-element-visual-studio-templates"></a>Elemento CustomParameters (modelli di Visual Studio)
Raggruppa i parametri personalizzati che devono essere passati per la creazione guidata modello quando la procedura guidata effettua le sostituzioni di parametro.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<CustomParameters>  
    <CustomParameter/>  
    <CustomParameter/>  
</CustomParameters>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
 Nessuno.  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[CustomParameter](../extensibility/customparameter-element-visual-studio-templates.md)|Elemento facoltativo.<br /><br /> Contiene un nome del parametro personalizzato e il valore da utilizzare quando viene creato un progetto o un elemento del modello. Possono esistere zero o più elementi `CustomParameter` in un elemento `CustomParameters`.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Specifica il contenuto del modello.|  
  
## <a name="remarks"></a>Note  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come utilizzare diversi parametri personalizzati in un modello. Quando viene creato un progetto o un elemento da un modello con i seguenti parametri personalizzati, tutte le istanze di `$color1$` e `$color2$` nel modello di file verranno sostituiti con `Red` e `Blue`, rispettivamente.  
  
```  
<CustomParameters>  
    <CustomParameter Name="$color1$" Value="Red"/>  
    <CustomParameter Name="$color2$" Value="Blue "/>  
</CustomParameters>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento CustomParameter (modelli di Visual Studio)](../extensibility/customparameter-element-visual-studio-templates.md)   
 [Parametri di modello](../ide/template-parameters.md)   
 [Riferimenti sullo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)