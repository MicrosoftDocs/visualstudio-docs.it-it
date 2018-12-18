---
title: Definire l'elemento | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Define
- Define element (VSCT XML schema)
ms.assetid: 5aee74e3-de41-4dc6-9618-93e158af56dd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 336c0b52e50731ff63fb790a1a1b201b0646caea
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="define-element"></a>Definire l'elemento
Definisce una coppia di nome e il valore di simbolo. Questo simbolo può essere valutato da attributi condizionali. Per ulteriori informazioni, vedere [attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md). Vedere anche il [simboli elemento](../extensibility/symbols-element.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
<Define name="Mode" value="Standard" />  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|name|Obbligatorio. Il nome del simbolo:<br /><br /> nome = "Modalità"|  
|predefinito|Obbligatorio. Il valore del simbolo:<br /><br /> valore = "Standard"|  
|Condizione|Facoltativo. Per ulteriori informazioni, vedere [attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementi figlio  
 Nessuno.  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Definisce tutti gli elementi che rappresentano i comandi che un pacchetto VSPackage fornisce all'ambiente di sviluppo integrato (IDE). Ad esempio, le voci di menu, menu, barre degli strumenti e caselle combinate.|  
  
## <a name="example"></a>Esempio  
  
```  
<Define name="DEMO_UI"/>  
<Define name="MODE" value="Standard"/>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [File Visual Studio Command Table (VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)