---
title: L'elemento di inclusione | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- Include
helpviewer_keywords:
- Include element (VSCT XML schema)
- VSCT XML schema elements, Include
ms.assetid: c923dfe6-084a-4105-aec1-f0a3f8399c54
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 189bac6ed410177a615c85abb5be02302030d19b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="include-element"></a>L'elemento di inclusione
L'elemento di inclusione specifica un file che può trovarsi in fornito includere percorso per l'inserimento nel file corrente.  Tutti i simboli e i tipi definiti diventerà parte del risultato compilato.  
  
## <a name="syntax"></a>Sintassi  
  
```csharp  
<Include href="stdidcmd.h" />  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|href|Obbligatorio. Il percorso al file di intestazione:<br /><br /> href="stdidcmd.h"|  
|Condizione|Facoltativo. Vedere [attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|Nessuno.|Nessuno.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Definisce tutti gli elementi che rappresentano i comandi, vale a dire, voci di menu, menu, barre degli strumenti e caselle combinate, che un pacchetto VSPackage fornisce all'IDE.|  
  
## <a name="example"></a>Esempio  
  
```  
<Include href="PackagePlacements.vsct"/>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [File Visual Studio Command Table (VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)