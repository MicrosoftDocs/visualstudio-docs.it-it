---
title: Enumerazione SCRIPTUICITEM | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: fbf01f1b-5d7f-4d92-8d10-3da65e352d93
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6620553bce810abcf1a51ac8592061ef017dd9bf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="scriptuicitem-enumeration"></a>Enumerazione SCRIPTUICITEM
Rappresenta il tipo di elemento dell'interfaccia utente. Utilizzato nel [metodo iactivescriptsiteuicontrol:: Getuibehavior](../../winscript/reference/iactivescriptsiteuicontrol-getuibehavior-method.md).  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
typedef enum tagSCRIPTUICITEM {     SCRIPTUICITEM_INPUTBOX = 1,     SCRIPTUICITEM_MSGBOX = 2,     } SCRIPTUICITEM;   
```  
  
## <a name="enumeration-values"></a>Valori di enumerazione  
  
|||  
|-|-|  
|SCRIPTUICITEM_INPUTBOX|Un controllo di input.|  
|SCRIPTUICITEM_MSGBOX|Una finestra di messaggio.|