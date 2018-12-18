---
title: Riferimento allo Schema XML VSCT | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio command table configuration files (VSCT), XML schema
- VSCT XML schema elements
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e8b8b796f4b5740f90a8755bdf158735387eaa90
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="vsct-xml-schema-reference"></a>Riferimento allo Schema XML VSCT
Fornisce una tabella di elementi dello schema di comando del compilatore di tabella, con figlio consentito elementi e attributi per ognuno.  
  
 Un file di configurazione (con estensione vsct) di tabella comandi basati su XML definisce gli elementi di comando che un pacchetto VSPackage fornisce all'ambiente di sviluppo integrato (IDE). Questi elementi includono voci di menu, menu, barre degli strumenti e caselle combinate.  
  
> [!NOTE]
>  Il compilatore VSCT è possibile eseguire un preprocessore sul file con estensione vsct. Poiché si tratta in genere include il preprocessore, che è possibile definire C++ e le macro che hanno la stessa sintassi utilizzata nel file di C++. Nel file vsct vengono forniti esempi di questo file di **nuovo progetto** procedura guidata Crea per un progetto VSPackage.  
  
## <a name="optional-elements"></a>Elementi facoltativi  
 Alcuni elementi VSCT sono facoltativi. Se un `Parent` argomento non viene specificato, verrà implicita Group_Undefined:0. Se un `Icon` argomento non viene specificato, verrà implicita guidOfficeIcon:msotcidNoIcon. Quando viene definito un tasto di scelta rapida, l'emulazione, che non viene utilizzato in genere, è facoltativo.  
  
 Gli elementi di bitmap possono essere incorporati in fase di compilazione specificando il percorso della striscia di bitmap nel `href` argomento. Striscia di bitmap viene copiata durante l'unione anziché estratti dalle risorse della DLL. Quando un `href` argomento viene fornito, il `usedList` argomento diventa facoltativo e vengono considerati tutti gli slot nella striscia di bitmap utilizzata.  
  
 Tutti i valori GUID e ID devono essere definiti utilizzando i nomi simbolici. Questi nomi possono essere definiti nei file di intestazione o in VSCT \<simboli > sezioni. I nomi simbolici devono essere locali, inclusi tramite \<inclusione > elementi, o a cui fa riferimento \<Extern > elementi. Un nome simbolico viene importato da un file di intestazione specificato in un \<Extern > elemento se segue il modello semplice di #define valore di simbolo. Il valore può essere un altro simbolo, purché tale simbolo è stato definito in precedenza. Le definizioni di GUID devono seguire nel formato OLE o C++. I valori di ID possono essere cifre decimali o cifre esadecimali che sono preceduti da 0x, come mostrato nelle righe seguenti:  
  
-   {6D484634-E53D-4a2c-ADCB-55145C9362C8}  
  
-   {0x6d484634, 0xe53d, 0x4a2c, {0xad, 0xcb, 0x55, 0x14, 0x5c, 0x93, 0x62, 0xc8}}  
  
 I commenti XML possono essere utilizzati, ma potrebbero ignorarle strumenti (GUI) di interfaccia utente grafica di andata e ritorno. Il contenuto di \<annotazione > elementi sono garantiti venga mantenuto indipendentemente dal formato.  
  
## <a name="schema-hierarchy"></a>Gerarchia dello schema  
 Un file con estensione vsct ha i seguenti elementi principali.  
  
 [Elemento CommandTable](../extensibility/commandtable-element.md)  
  
 [Elemento Extern](../extensibility/extern-element.md)  
  
 [Elemento Include](../extensibility/include-element.md)  
  
 [Elemento Define](../extensibility/define-element.md)  
  
 [Elemento Commands](../extensibility/commands-element.md)  
  
 [Elemento CommandPlacements](../extensibility/commandplacements-element.md)  
  
 [Elemento VisibilityConstraints](../extensibility/visibilityconstraints-element.md)  
  
 [Elemento KeyBindings](../extensibility/keybindings-element.md)  
  
 [Elemento UsedCommands](../extensibility/usedcommands-element.md)  
  
 [Elemento Parent](../extensibility/parent-element.md)  
  
 [Elemento Icon](../extensibility/icon-element.md)  
  
 [Elemento Strings](../extensibility/strings-element.md)  
  
 [Elemento CommandFlag](../extensibility/command-flag-element.md)  
  
 [Elemento Symbols](../extensibility/symbols-element.md)  
  
 [Attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Come VSPackage aggiungono elementi dell'interfaccia utente](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Routing dei comandi nei pacchetti VSPackage](../extensibility/internals/command-routing-in-vspackages.md)