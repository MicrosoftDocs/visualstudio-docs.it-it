---
title: Elemento combinata | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Combos element (VSCT XML schema)
- VSCT XML schema elements, Combos
ms.assetid: 392e3063-f0a0-4130-9583-23bd2aa3fa36
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9980232a7927bf1ae2df9d5f6329a57a031d3f56
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="combo-element"></a>Elemento combinata
Definisce i comandi che vengono visualizzati in una casella combinata. Esistono quattro tipi di caselle combinate, come indicato di seguito: DropDownCombo, DynamicCombo, IndexCombo e MRUCombo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<combo guid="guidMyCommandSet" id="MyCommand" defaultWidth="20" idCommandList="MyCommandListID" priority="0x102" type="DropDownCombo">  
  <Parent>... </Parent  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</combo>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|guid|Obbligatorio. GUID dell'identificatore di comando/ID GUID.|  
|ID|Obbligatorio. ID dell'identificatore di comando/ID GUID.|  
|defaultWidth|Obbligatorio. Valore intero che specifica una larghezza in pixel della casella combinata.|  
|idCommandList|Obbligatorio. Un ID che viene inviato alla destinazione del comando attivo per recuperare l'elenco di elementi da visualizzare nella casella combinata. L'ID sarà nello stesso ambito GUID del controllo.|  
|priority|Facoltativo. Un valore numerico che specifica la priorità.|  
|tipo|Facoltativo. Valore enumerato che specifica il tipo di pulsante.<br /><br /> Se non è specificato, utilizza pulsante.<br /><br /> DropDownCombo<br /> Il pacchetto VSPackage è responsabile per la compilazione nel contenuto di questa casella combinata. L'utente non è possibile digitare un valore nella casella di testo di questo elenco a discesa.<br /><br /> DynamicCombo<br /> Il pacchetto VSPackage è responsabile per la compilazione nel contenuto di questa casella combinata. L'utente può modificare questo combinata e anche selezionare elementi in essa contenuti.<br /><br /> IndexCombo<br /> Lo stesso come DynamicCombo eccezione del fatto che genera l'indice dell'elemento anziché il testo.<br /><br /> MRUCombo<br /> Compilato tramite l'ambiente di sviluppo integrato (IDE) per conto di VSPackage.  L'utente può modificare in questa casella combinata. Nell'IDE vengono mantenuti fino alle voci di 16 per ogni casella combinata.<br /><br /> Quando l'utente seleziona un elemento nella casella combinata o immette un nuovo valore, l'IDE di notifica a VSPackage appropriato.|  
|Condizione|Facoltativo. Vedere [attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|Padre|Facoltativo. L'elemento padre del pulsante.|  
|CommandFlag|Obbligatorio. Vedere [comando Flag elemento](../extensibility/command-flag-element.md). Come indicato di seguito sono riportati i valori CommandFlag validi per un pulsante.<br /><br /> -CaseSensitive<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> -DynamicVisibility<br /><br /> -Filtro tasti<br /><br /> -IconAndText<br /><br /> -NoAutoComplete<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> -StretchHorizontally|  
|Stringhe|Obbligatorio. Vedere [stringhe elemento](../extensibility/strings-element.md). L'elemento ButtonText figlio deve essere definito.|  
|Annotazione|Commento facoltativo.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento Commands](../extensibility/commands-element.md)|Rappresenta la raccolta di comandi sulla barra degli strumenti di VSPackage.|  
  
## <a name="example"></a>Esempio  
  
```  
<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"  
  defaultWidth="100" idCommandList="cmdidGetInsertOptionsList">  
  <CommandFlag>DynamicVisibility</CommandFlag>  
  <Strings>  
    <ButtonText>Select Insert Options</ButtonText>  
  </Strings>  
</Combo>  
  
<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"  
  priority="0x0500" type="DropDownCombo" defaultWidth="100"  
  idCommandList="cmdidGetInsertOptionsList">  
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">  
  <CommandFlag>DynamicVisibility</CommandFlag>  
  <Strings>  
    <ButtonText>Select Insert Options</ButtonText>  
  </Strings>  
</Combo>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [File Visual Studio Command Table (VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)