---
title: Elemento CommandTable | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5f2dd2ebd076d4225adc86e5ba0cdc9af6ca40df
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="commandtable-element"></a>Elemento CommandTable
CommandTable è l'elemento radice del file con estensione vsct. Questo è il file che definisce il layout effettivo e il tipo di comandi che un pacchetto VSPackage fornisce all'IDE. I comandi possono includere voci di menu, menu, barre degli strumenti e caselle combinate. Per altre informazioni, vedere [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema" >  
  <Extern>... </Extern>  
  <Include>... </Include>  
  <Define>... </Define>  
  <Commands>... </Commands>  
  <CommandPlacements>... </CommandPlacements>  
  <VisibilityConstraints>... </VisibilityConstraints>  
  <KeyBindings>... </KeyBindings>  
  <UsedCommands... </UsedCommands>  
  <Symbols>... </Symbols>  
</CommandTable>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|xmlns|Obbligatorio. Spazi dei nomi XML:<br /><br /> xmlns = "http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"<br /><br /> xmlns = "http://www.w3.org/2001/XMLSchema"|  
|language|Facoltativo. L'attributo di linguaggio può essere utilizzato per specificare la lingua predefinita di tutte \<stringhe > elementi della tabella di comando.  Se la lingua non viene specificata, verrà utilizzato il linguaggio del processo corrente:<br /><br /> Language = "en-us"|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento Extern](../extensibility/extern-element.md)|Facoltativo. Contiene le direttive del preprocessore del compilatore.|  
|[Elemento Include](../extensibility/include-element.md)|Facoltativo. Contiene i percorsi di tutti i file da includere con la compilazione.|  
|[Elemento Define](../extensibility/define-element.md)|Facoltativo. Definisce un simbolo dato il nome e valore.|  
|[Elemento Commands](../extensibility/commands-element.md)|Facoltativo. L'elemento padre che definisce tutti i comandi per il pacchetto VSPackage che contiene tutti gli altri elementi.|  
|[Elemento CommandPlacements](../extensibility/commandplacements-element.md)|Facoltativo. Definisce dove sulla barra dei comandi i comandi devono essere inseriti.|  
|[Elemento VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Facoltativo. Determina la visibilità statica di comandi e le barre degli strumenti.|  
|[Elemento KeyBindings](../extensibility/keybindings-element.md)|Facoltativo. Specifica le combinazioni di tasti di scelta rapida, se presente, per i comandi.|  
|[Elemento UsedCommands](../extensibility/usedcommands-element.md)|Facoltativo. Consente a un pacchetto VSPackage se lo si desidera implementare la propria versione della funzionalità originariamente supportate da altri pacchetti VSPackage.|  
|[Elemento Symbols](http://msdn.microsoft.com/en-us/f2ddd0aa-c3dd-439e-834d-28f136a27ffa)|Facoltativo. Contiene tutti i dati dei simboli: GUID, ID e così via, per il compilatore.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|Nessuno||  
  
## <a name="see-also"></a>Vedere anche  
 [File Visual Studio Command Table (VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)