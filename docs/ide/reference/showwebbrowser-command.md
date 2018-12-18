---
title: Comando ShowWebBrowser| Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: view.showwebbrowser
helpviewer_keywords:
- ShowWebBrowser command
- View.ShowWebBrowser command
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 122a5029c5518d7a4778c4d4732f7ebac9b23683
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="showwebbrowser-command"></a>Comando ShowWebBrowser
Visualizza l'URL specificato in una finestra del Web browser all'interno o all'esterno dell'ambiente di sviluppo integrato (IDE).  
  
## <a name="syntax"></a>Sintassi  
  
```  
View.ShowWebBrowser URL [/new][/ext]  
```  
  
## <a name="arguments"></a>Argomenti  
 `URL`  
 Obbligatorio. URL (Uniform Resource Locator) per il sito Web.  
  
## <a name="switches"></a>Opzioni  
 /new  
 Facoltativo. Specifica che la pagina venga visualizzata in una nuova istanza del Web browser.  
  
 /ext  
 Facoltativo. Specifica che la pagina venga visualizzata nel Web browser predefinito all'esterno dell'IDE.  
  
## <a name="remarks"></a>Note  
 L'alias per il comando **ShowWebBrowser** è **navigate** o **nav**.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente illustra la home page di MSDN Online in un Web browser all'esterno dell'IDE. Se è già aperta un'istanza del Web browser, viene usata; in caso contrario, viene avviata una nuova istanza.  
  
```  
>View.ShowWebBrowser http://msdn.microsoft.com /ext  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)  (Comandi di Visual Studio)  
 [Command Window](../../ide/reference/command-window.md)  (Finestra di comando)  
 [Find/Command Box](../../ide/find-command-box.md)  (Casella Trova/Comando)  
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)