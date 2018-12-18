---
title: Elemento extern | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- Extern
helpviewer_keywords:
- VSCT XML schema elements, Extern
- Extern element (VSCT XML schema)
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ea14d985265d02c3e60ee12c8b46deafba2bcd72
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="extern-element"></a>Elemento extern
L'elemento Extern fa riferimento a tutti i file esterni intestazione (h) di tipo merge con il file con estensione vsct in fase di compilazione. I file da unire devono trovarsi nel percorso di inclusione specificato per il compilatore VSCT o a cui fa riferimento un [elemento Include](../extensibility/include-element.md). I file potrebbero essere altri file con estensione vsct o file di intestazione C++.  
  
 Le definizioni nel file di intestazione devono essere nel formato "#define [simbolo] [valore]" il valore può essere un altro simbolo è definito in precedenza. Le definizioni possono essere utilizzate nelle istruzioni condizionali di elementi di comando. Verrà eliminata qualsiasi simbolo non effettivamente utilizzato.  
  
 Elemento CommandTable  
Elemento extern  
  
## <a name="syntax"></a>Sintassi  
  
```  
<Extern href="stdidcmd.h" />  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|href|Obbligatorio. Il percorso al file di intestazione:<br /><br /> href="stdidcmd.h"|  
|Condizione|Facoltativo. Vedere [attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
|language|Facoltativo. La lingua predefinita di tutte [ \<stringhe >](../extensibility/strings-element.md) elementi della tabella di comando:<br /><br /> Language = "en-us"|  
  
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
<?xml version="1.0" encoding="utf-8"?>  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-  
  18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <Extern href="C:\VSCore\vscommon\inc\vsshlids.h"/>  
    ...  
  <Commands package="guidMyPackage">  
</CommandTable>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Command Table (. File Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Come VSPackage aggiungono elementi dell'interfaccia utente](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)