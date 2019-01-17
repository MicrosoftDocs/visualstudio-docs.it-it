---
title: Enumerazione SCRIPTUICITEM | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: fbf01f1b-5d7f-4d92-8d10-3da65e352d93
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cf880ed8b0295e841026e884f6cec71a9f52d4ae
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347489"
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