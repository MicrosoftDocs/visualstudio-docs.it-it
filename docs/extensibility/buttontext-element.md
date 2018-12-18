---
title: Elemento ButtonText | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2fca0fbb22bf51353eeaa64f519face53bfb23c8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="buttontext-element"></a>Elemento ButtonText
Questo campo consente di specificare il testo visualizzato in diversi menu. Per impostazione predefinita, il `ButtonText` elemento compare in un controller di menu. Il `ButtonText` elemento diventa il valore predefinito anche se gli altri campi di testo sono vuoti. Il `ButtonText` elemento non può essere vuoto, anche se sono specificati gli altri campi di testo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<ButtonText>My Command</ButtonText>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
 Nessuno.  
  
### <a name="child-elements"></a>Elementi figlio  
 Nessuno.  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento Strings](../extensibility/strings-element.md)|Raggruppa gli elementi di testo, ad esempio `ButtonText` e `CommandName`.|  
  
## <a name="text-value"></a>Valore di testo  
 Il valore di testo il `ButtonText` elemento fornisce il testo visualizzato per le voci di menu, casella combinata e altri elementi dell'interfaccia utente che contengono testo visibile.  
  
## <a name="see-also"></a>Vedere anche  
 [File Visual Studio Command Table (VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)