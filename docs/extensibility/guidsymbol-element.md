---
title: Elemento GuidSymbol | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d5089d87156bd5eb191176fe73ab19a01d497b90
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="guidsymbol-element"></a>Elemento GuidSymbol
Il `GuidSymbol` elemento contiene il GUID della coppia GUID: ID che rappresenta un menu, gruppo o comando. L'ID proviene da un `IDSymbol` elemento il `GuidSymbol` elemento. Il `GuidSymbol` elemento ha un `name` attributo che fornisce un nome descrittivo per il GUID, contenute nel `value` attributo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<GuidSymbol name="guidMyCommandSet" value="{xxxxxxxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx}">  
  <IDSymbol>... </IDSymbol>  
  <IDSymbol>... </IDSymbol>  
</GuidSymbol>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|name|Obbligatorio. Nome del simbolo GUID.|  
|predefinito|Obbligatorio. GUID del simbolo GUID.|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento IDSymbol](../extensibility/idsymbol-element.md)|Contiene l'ID della coppia GUID: ID che rappresenta un menu, gruppo o comando.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento Symbols](../extensibility/symbols-element.md)|Gruppi `GuidSymbol` elementi in un file con estensione vsct.|  
  
## <a name="remarks"></a>Note  
 In genere, un file con estensione vsct include tre `GuidSymbol` elementi relativo `Symbols` sezione, uno per il pacchetto stesso, uno per il set di comandi (la raccolta di menu, gruppi e i comandi che rende disponibile il pacchetto) e uno per le mappe di bit che forniscono icone per i pulsanti e altri componenti visivi. Ogni `IDSymbol` elemento in un determinato `GuidSymbol` elemento deve essere univoco `value`. Tuttavia, `IDSymbol` gli elementi che hanno valori identici possono esistere in un pacchetto come hanno elementi padre diversi.  
  
## <a name="see-also"></a>Vedere anche  
 [File Visual Studio Command Table (VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)