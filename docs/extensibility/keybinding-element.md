---
title: Tasto di scelta rapida elemento | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 226a5913cbaa151689a886dc88986f7de8cc29f6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="keybinding-element"></a>Tasto di scelta rapida elemento
L'elemento KeyBinding specifica tasti di scelta rapida per i comandi.  
  
 I comandi possono avere una o due tasti di scelta rapida associati. È di un esempio di una singola combinazione di tasti CTRL + S per il **salvare** comando. Tasti di scelta rapida doppi richiedono due combinazioni di tasti successive per attivare un comando. Un esempio di un'associazione duale di chiavi è CTRL + K, CTRL + K per impostare un segnalibro.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|guid|Obbligatorio.|  
|ID|Obbligatorio.|  
|editor|Obbligatorio. L'editor GUID indica il contesto di modifica per il quale sarà attivo il tasto di scelta rapida. Il valore di ambito di associazione globale è "guidVSStd97".|  
|key1|Obbligatorio. I valori validi includono tutti possibile digitare caratteri alfanumerici e i valori esadecimali a due cifre preceduti da 0x e [VK_constants](https://msdn.microsoft.com/en-us/library/windows/desktop/dd375731.aspx).|  
|MOD1|Facoltativo. Qualsiasi combinazione di MAIUSC separate da spazio CTRL e ALT.|  
|key2|Facoltativo. I valori validi includono tutti possibile digitare caratteri alfanumerici e i valori esadecimali a due cifre preceduti da 0x e [VK_constants](https://msdn.microsoft.com/en-us/library/windows/desktop/dd375731.aspx).|  
|MOD2|Facoltativo. Qualsiasi combinazione di MAIUSC separate da spazio CTRL e ALT.|  
|emulatore|Facoltativo.|  
|Condizione|Facoltativo. Vedere [attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|Padre||  
|Annotazione||  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento KeyBindings](../extensibility/keybindings-element.md)|Gli elementi KeyBinding di gruppi e altri raggruppamenti di tasti di scelta rapida.|  
  
## <a name="example"></a>Esempio  
  
```  
<KeyBindings>  
  <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget"   
    editor="guidWidgetEditor" key1="VK_F5"/>  
  <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget"   
    editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/>  
</KeyBindings>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Tasti di scelta rapida elemento](../extensibility/keybindings-element.md)   
 [File Visual Studio Command Table (VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
