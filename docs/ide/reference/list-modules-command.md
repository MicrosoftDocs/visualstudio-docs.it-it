---
title: Comando Elenca moduli | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- debug.listmodules
helpviewer_keywords:
- Debug.ListModules command
- ListModules command
- list modules command
ms.assetid: 3cb73774-6ac0-43b2-b781-75ed47175bfd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 621d2956807d415d1ed03799e1ef332404429603
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="list-modules-command"></a>Comando Elenca moduli
Elenca i moduli disponibili per il processo corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Debug.ListModules [/Address:yes|no] [/Name:yes|no] [/Order:yes|no]  
[/Path:yes|no] [/Process:yes|no] [/SymbolFile:yes|no]  
[/SymbolStatus:yes|no] [/Timestamp:yes|no] [/Version:yes|no]  
```  
  
#### <a name="parameters"></a>Parametri  
 /Address:`yes|no`  
 Facoltativo. Specifica se visualizzare gli indirizzi di memoria dei moduli. Il valore predefinito è `yes`.  
  
 /Name:`yes|no`  
 Facoltativo. Specifica se visualizzare i nomi dei moduli. Il valore predefinito è `yes`.  
  
 /Order:`yes|no`  
 Facoltativo. Specifica se visualizzare l'ordine dei moduli. Il valore predefinito è `no`.  
  
 /Path:`yes|no`  
 Facoltativo. Specifica se visualizzare i percorsi dei moduli. Il valore predefinito è `yes`.  
  
 /Process:`yes|no`  
 Facoltativo. Specifica se visualizzare i processi dei moduli. Il valore predefinito è `no`.  
  
 /SymbolFile:`yes|no`  
 Facoltativo. Specifica se visualizzare i file dei simboli dei moduli. Il valore predefinito è `no`.  
  
 /SymbolStatus:`yes|no`  
 Facoltativo. Specifica se visualizzare lo stato dei simboli dei moduli. Il valore predefinito è `yes`.  
  
 /Timestamp:`yes|no`  
 Facoltativo. Specifica se visualizzare il timestamp dei moduli. Il valore predefinito è `no`.  
  
 /Version:`yes|no`  
 Facoltativo. Specifica se visualizzare le versioni dei moduli. Il valore predefinito è `no`.  
  
## <a name="remarks"></a>Note  
  
## <a name="example"></a>Esempio  
 In questo esempio vengono elencati i nomi dei moduli, gli indirizzi e i timestamp per il processo corrente.  
  
```  
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)  (Comandi di Visual Studio)  
 [Command Window](../../ide/reference/command-window.md)  (Finestra di comando)  
 [Procedura: Usare la finestra Moduli](../../debugger/how-to-use-the-modules-window.md)