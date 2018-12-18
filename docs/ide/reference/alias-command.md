---
title: Comando Alias | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- tools.alias
helpviewer_keywords:
- aliases, Visual Studio commands
- commands, aliases
- Tools.Alias command
- command aliases
- alias command
ms.assetid: bdf857df-b5d5-450f-8c10-a6fd4dccc130
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 02378b6e980dc4590bdc8901f67ca160bbffe157
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="alias-command"></a>Comando Alias
Crea un nuovo alias per un comando completo, un comando completo con i relativi argomenti o un altro alias.  
  
> [!TIP]
>  Digitando `>alias` senza alcun argomento verrà visualizzato l'elenco corrente di alias e le relative definizioni.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Tools.Alias [/delete] [/reset] [aliasname] [aliasstring]  
```  
  
## <a name="arguments"></a>Argomenti  
 `aliasname`  
 Facoltativo. Nome del nuovo alias. Se per `aliasname` non viene specificato alcun valore, verrà visualizzato un elenco degli alias correnti e le relative definizioni.  
  
 `aliasstring`  
 Facoltativo. Nome del comando completo o alias esistente e i parametri da creare come alias. Se per `aliasstring` non viene specificato alcun valore, verranno visualizzati il nome di alias e la stringa di alias per l'alias specificato.  
  
## <a name="switches"></a>Opzioni  
 /delete o /del o /d  
 Facoltativo. Elimina l'alias specificato rimuovendolo dal completamento automatico.  
  
 /reset  
 Facoltativo. Ripristina le impostazioni originali dell'elenco di alias predefiniti, ovvero ripristina tutti gli alias predefiniti e rimuove tutti gli alias definiti dall'utente.  
  
## <a name="remarks"></a>Note  
 Poiché rappresentano i comandi, gli alias devono essere posizionati all'inizio della riga di comando.  
  
 Quando si esegue questo comando, le opzioni devono essere incluse subito dopo il comando, non dopo gli alias. In caso contrario, l'opzione verrà considerata parte della stringa di alias.  
  
 L'opzione `/reset` chiede una conferma prima del ripristino degli alias. Non esiste una forma breve di `/reset`.  
  
## <a name="examples"></a>Esempi  
 In questo esempio viene creato un nuovo alias, `upper`, per il comando completo Edit.MakeUpperCase.  
  
```  
>Tools.Alias upper Edit.MakeUpperCase  
```  
  
 In questo esempio l'alias `upper` viene eliminato.  
  
```  
>Tools.alias /delete upper  
```  
  
 In questo esempio viene visualizzato un elenco di tutti gli alias correnti e le relative definizioni.  
  
```  
>Tools.Alias  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)  (Comandi di Visual Studio)  
 [Command Window](../../ide/reference/command-window.md)  (Finestra di comando)  
 [Find/Command Box](../../ide/find-command-box.md)  (Casella Trova/Comando)  
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)