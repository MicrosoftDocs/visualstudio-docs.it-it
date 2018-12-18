---
title: Icone di Visualizzazione classi e Visualizzatore oggetti | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- icons, in Object Browser
- signal icons
- Class View tool, symbols
- graphic symbols
- IntelliSense, icons
- icons, IntelliSense
- symbols, Object Browser icons
- Object Browser, icons in Class View
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4893b38ceed7709f6b306b0cb84da47f205c911f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="class-view-and-object-browser-icons"></a>Icone di Visualizzazione classi e Visualizzatore oggetti

In **Visualizzazione classi** e **Visualizzatore oggetti** vengono visualizzate le icone che rappresentano le entità di codice, ad esempio spazi dei nomi, classi, funzioni e variabili. Nella tabella seguente vengono illustrate e descritte le icone.

|Icona|Descrizione|Icona|Descrizione|
|----------|-----------------|----------|-----------------|
|![Simbolo Spazio dei nomi](../ide/media/vxnamespace_icon.gif "vxNamespace_Icon")|Spazio dei nomi|![Simbolo Dichiarazione](../ide/media/vxmethod_icon.gif "vxMethod_Icon")|Metodo o funzione|
|![Icona Classe](../ide/media/vxclass_icon.gif "vxClass_Icon")|Classe|![Simbolo Operatore](../ide/media/vxoperator_icon.gif "vxOperator_Icon")|Operatore|  
|![Simbolo interfaccia cerchio-linea](../ide/media/vxinterface_icon.gif "vxInterface_Icon")|Interfaccia|![Simbolo Proprietà](../ide/media/vxproperty_icon.gif "vxProperty_Icon")|Proprietà|
|![Simbolo Struttura](../ide/media/vxstruct_icon.gif "vxStruct_Icon")|Struttura|![Icona Campo](../ide/media/vxfield_icon.gif "vxField_Icon")|Campo o variabile|  
|![Simbolo Unione](../ide/media/vxunion_icon.gif "vxUnion_Icon")|Unione|![Simbolo Evento](../ide/media/vxevent_icon.gif "vxEvent_Icon")|event|  
|![Simbolo Enumerazione](../ide/media/vxenum_icon.gif "vxEnum_Icon")|Enum|![Icona Costante](../ide/media/vxconstant_icon.gif "vxConstant_Icon")|Costante|  
|![Simbolo Definizione di tipo](../ide/media/vxtypedef_icon.gif "vxTypeDef_Icon")|TypeDef|![Simbolo Elemento di enumerazione](../ide/media/vxenumitem_icon.gif "vxEnumItem_Icon")|Elemento di enumerazione|  
|![Simbolo dei moduli di Visual Studio](../ide/media/vxmodule_icon.gif "vxModule_Icon")|Modulo|![Simbolo Elemento mappa](../ide/media/vxmapitem_icon.gif "vxMapItem_Icon")|Elemento mappa|  
|![Simbolo Metodo di estensione](../ide/media/extensionmethod.gif "ExtensionMethod")|Metodo di estensione|![Simbolo Dichiarazione](../ide/media/vxmethod_icon.gif "vxMethod_Icon")|Dichiarazione esterna|  
|![Simbolo Delegato](../ide/media/vxdelegate_icon.gif "vxDelegate_Icon")|delegato|![Icona di errore per Visualizzazione classi e Visualizzatore oggetti](../ide/media/erroricon.gif "ErrorIcon")|Error|  
|![Simbolo Eccezione](../ide/media/vxexception_icon.gif "vxException_Icon")|Eccezione|![Simbolo Modello](../ide/media/vxtemplate_icon.gif "vxTemplate_Icon")|Modello|  
|![Simbolo Mappa](../ide/media/vxmap_icon.gif "vxMap_Icon")|Mappa|![Simbolo di errore con punto esclamativo](../ide/media/vxerror_icon.gif "vxError_Icon")|Sconosciuto|  
|![Simbolo Inoltro dei tipi](../ide/media/ob_type_forward.gif "ob_type_forward")|Inoltro del tipo|||  

## <a name="signal-icons"></a>Icone di segnalazione

Le icone di segnalazione seguenti si applicano a tutte le icone precedenti e ne indicano l'accessibilità.

|Icona|Descrizione|
|----------|-----------------|  
|\<Nessuna icona di segnalazione>|Pubblico. Accessibile ovunque in questo componente e da qualsiasi componente che vi fa riferimento.|  
|![Simbolo di contrassegno Protetto](../ide/media/vxsignal_icon_key.gif "vxSignal_Icon_Key")|Protetto. Accessibile dalla classe o dal tipo contenitore o da quelli da essi derivati.|  
|![Simbolo di contrassegno Privato](../ide/media/vxsignal_icon_lock.gif "vxSignal_Icon_Lock")|Privato. Accessibile solo nella classe o nel tipo contenitore.|  
|![Simbolo di contrassegno Sealed](../ide/media/vxsignal_icon_envelope.gif "vxSignal_Icon_Envelope")|Contrassegnato come sealed.|  
|![Simbolo di contrassegno Friend&#47;Internal](../ide/media/vxsignal_icon_diamond.gif "vxSignal_Icon_Diamond")|Friend/Internal. Accessibile solo dal progetto.|  
|![Icona di segnalazione freccia](../ide/media/vxsignal_icon_arrow.gif "vxSignal_Icon_Arrow")|Collegamento. Un collegamento all'oggetto.|

> [!NOTE]
> Se il progetto è incluso in un database di controllo del codice sorgente potrebbero essere visualizzate altre icone di segnalazione per indicare lo stato di controllo del codice sorgente, ad esempio se il codice è stato archiviato o estratto.

## <a name="see-also"></a>Vedere anche

[Visualizzazione della struttura del codice](../ide/viewing-the-structure-of-code.md)