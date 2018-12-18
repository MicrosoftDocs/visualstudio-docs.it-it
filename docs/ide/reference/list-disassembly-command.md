---
title: Comando Elenca disassembly | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: debug.listdisassembly
helpviewer_keywords:
- Debug.ListDisassembly command
- list disassembly command
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c6a704ac783f4efc300de26c2a5e987f82fc2e9c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="list-disassembly-command"></a>Comando Elenca disassembly
Avvia il processo di debug e consente di specificare come devono essere gestiti gli errori.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Debug.ListDisassembly [/count:number] [/endaddress:expression]  
[/codebytes:yes|no] [/source:yes|no] [/symbolnames:yes|no]  
[/linenumbers:yes|no]  
```  
  
## <a name="switches"></a>Opzioni  
 Ogni opzione può essere richiamata usando la forma completa o una forma breve.  
  
 /count: `number` [or] /c: `number` [or] /length: `number` [or] /l: `number`  
 Facoltativo. Numero di istruzioni da visualizzare. Il valore predefinito è 8.  
  
 /endaddress: `expression` [or] /e: `expression`  
 Facoltativo. Indirizzo in corrispondenza del quale interrompere il disassembly.  
  
 /codebytes:`yes`&#124;`no` [or] /bytes:`yes`&#124;`no` [or] /b:`yes`&#124;`no`  
 Facoltativo. Indica se visualizzare i byte di codice. Il valore predefinito è `no`.  
  
 /source:`yes`&#124;`no` [or] /s:`yes`&#124;`no`  
 Facoltativo. Indica se visualizzare il codice sorgente. Il valore predefinito è `no`.  
  
 /symbolnames:`yes`&#124;`no` [or] /names:`yes`&#124;`no` [or] /n:`yes`&#124;`no`  
 Facoltativo. Indica se visualizzare i nomi dei simboli. Il valore predefinito è `yes`.  
  
 [/linenumbers:`yes`&#124;`no`]  
 Facoltativo. Abilita la visualizzazione dei numeri di riga associati al codice sorgente. L'opzione /source deve avere un valore di `yes` per usare l'opzione /linenumbers.  
  
## <a name="example"></a>Esempio  
  
```  
>Debug.ListDisassembly  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Comando Elenca stack di chiamate](../../ide/reference/list-call-stack-command.md)   
 [Comando Elenca thread](../../ide/reference/list-threads-command.md)   
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)  (Comandi di Visual Studio)  
 [Command Window](../../ide/reference/command-window.md)  (Finestra di comando)  
 [Find/Command Box](../../ide/find-command-box.md)  (Casella Trova/Comando)  
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)