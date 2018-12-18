---
title: -LCID (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language default
- locale IDs, setting for IDE
- Devenv, /LCID switch
- locale IDs
- /l Devenv switch
- LCID devenv switch
- /lcid Devenv switch
ms.assetid: 3a3f4e70-ea66-4351-9d62-acb1dec30e8e
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: bdc04655ccfc8ca5f6c1e45e4378f15221b99f4c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="lcid-devenvexe"></a>/LCID (devenv.exe)
Imposta la lingua predefinita usata per il testo, la valuta e altri valori all'interno dell'ambiente di sviluppo integrato (IDE).  
  
## <a name="syntax"></a>Sintassi  
  
```  
devenv {/LCID|/l} LocaleID  
```  
  
## <a name="arguments"></a>Argomenti  
 `LocaleID`  
 Obbligatorio. LCID (ID impostazioni locali) della lingua specificata.  
  
## <a name="remarks"></a>Note  
 Carica l'IDE e imposta la lingua naturale predefinita per l'ambiente. Questa modifica è persistente tra le sessioni e viene riportata nel riquadro **Impostazioni internazionali** delle opzioni **Ambiente** nella finestra di dialogo **Opzioni** nell'IDE.  
  
 Se la lingua specificata non è disponibile nel sistema dell'utente, l'opzione /LCID viene ignorata.  
  
 Nella tabella seguente vengono elencati gli LCID delle lingue supportate da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
|Linguaggio|LCID|  
|--------------|----------|  
|Cinese (semplificato)|2052|  
|Cinese (tradizionale)|1028|  
|Inglese|1040|  
|Francese|1036|  
|Tedesco|1031|  
|Italiano|1040|  
|Giapponese|1041|  
|Coreano|1042|  
|Spagnolo|3082|  
  
## <a name="example"></a>Esempio  
 In questo esempio viene caricato l'IDE con le stringhe delle risorse in lingua inglese.  
  
```  
devenv /LCID 1033  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Devenv Command Line Switches](../../ide/reference/devenv-command-line-switches.md)  (Opzioni della riga di comando di Devenv)  
 [Impostazioni internazionali, Ambiente, finestra di dialogo Opzioni](../../ide/reference/international-settings-environment-options-dialog-box.md)   
 [Personalizzazione del layout delle finestre](../../ide/customizing-window-layouts-in-visual-studio.md)