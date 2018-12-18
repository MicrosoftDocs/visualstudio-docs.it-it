---
title: Elemento CustomParameter (modelli di Visual Studio) | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameter
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: 743c4489-74ac-403a-bbaa-eed7d785a3ac
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 154586701386f5f8f56c128920e12ca3147deb6b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="customparameter-element-visual-studio-templates"></a>Elemento CustomParameter (modelli di Visual Studio)
Contiene un nome del parametro personalizzato e il valore da utilizzare quando viene creato un progetto o un elemento del modello.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<CustomParameter Name="name" Value="value">  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Name`|Obbligatorio. Nome del parametro. Il formato dei parametri è $*nome*$.|  
|`Value`|Obbligatorio. Il valore di sostituzione per il parametro.|  
  
### <a name="child-elements"></a>Elementi figlio  
 Nessuno.  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Raggruppa i parametri personalizzati che devono essere passati per la creazione guidata modello quando la procedura guidata effettua le sostituzioni di parametro.|  
  
## <a name="remarks"></a>Note  
 Quando un modello contiene `CustomParameter` elementi, ogni istanza di `Name` attributo viene sostituito con il `Value` attributo nei file di progetto o un elemento creati.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come utilizzare diversi parametri personalizzati in un modello. Quando viene creato un progetto o un elemento da un modello con i seguenti parametri personalizzati, tutte le istanze di `$color1$` e `$color2$` nel modello di file verranno sostituiti con `Red` e `Blue`, rispettivamente.  
  
```  
<CustomParameters>  
    <CustomParameter Name="$color1$" Value="Red"/>  
    <CustomParameter Name="$color2$" Value="Blue "/>  
</CustomParameters>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento CustomParameters (modelli di Visual Studio)](../extensibility/customparameters-element-visual-studio-templates.md)   
 [Parametri di modello](../ide/template-parameters.md)   
 [Riferimenti sullo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)