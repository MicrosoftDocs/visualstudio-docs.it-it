---
title: -Command (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Devenv, /command switch
- /command Devenv switch
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 77fcd3f560644a8f7033872ea7db4bc50acf3359
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="command-devenvexe"></a>/Command (devenv.exe)
Esegue il comando specificato dopo l'avvio dell'ambiente di sviluppo integrato (IDE) di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```  
devenv /command CommandName  
```  
  
## <a name="arguments"></a>Argomenti  
 `CommandName`  
 Obbligatorio. Nome completo di un comando di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] o del relativo alias, racchiuso tra virgolette doppie. Per altre informazioni sulla sintassi dei comandi e degli alias, vedere [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md).  
  
## <a name="remarks"></a>Note  
 Al completamento dell'avvio, nell'IDE viene eseguito il comando specificato. Se si usa questa opzione, la pagina iniziale di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] non viene visualizzata nell'IDE all'avvio.  
  
 Se un componente aggiuntivo visualizza un comando, è possibile usare questa opzione per avviare il componente aggiuntivo dalla riga di comando. Per altre informazioni, vedere [Procedura: controllare i componenti aggiuntivi tramite Gestione componenti aggiuntivi](http://msdn.microsoft.com/Library/4f60444a-cb48-4cdb-8df4-941f6419aeeb).  
  
## <a name="example"></a>Esempio  
 Questo codice di esempio avvia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ed esegue automaticamente la macro OpenFavoriteFiles.  
  
```  
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Devenv Command Line Switches](../../ide/reference/devenv-command-line-switches.md)  (Opzioni della riga di comando di Devenv)  
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)