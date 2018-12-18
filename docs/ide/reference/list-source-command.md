---
title: Comando Elenca origine | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- Debug.ListSource
helpviewer_keywords:
- Debug.ListSource command
- list source command
- ListSource command
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d21a18a58832918b566e925c7c3898988740a1a7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="list-source-command"></a>Comando Elenca origine
Visualizza le righe del codice sorgente specificate.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Debug.ListSource [/Count:number] [/Current] [/File:filename]  
[/Line:number] [/ShowLineNumbers:yes|no]  
```  
  
## <a name="switches"></a>Opzioni  
 /Count:`number`  
 Facoltativo. Specifica il numero di righe da visualizzare.  
  
 /Current  
 Facoltativo. Visualizza la riga corrente.  
  
 /File:`filename`  
 Facoltativo. Percorso del file da visualizzare. Se non viene specificato alcun nome file, il comando visualizza il codice sorgente per la riga dell'istruzione corrente.  
  
 /Line:`number`  
 Facoltativo. Visualizza un numero di riga specifico.  
  
 /ShowLineNumbers:`yes|no`  
 Facoltativo. Specifica se visualizzare i numeri di riga.  
  
## <a name="remarks"></a>Note  
  
## <a name="example"></a>Esempio  
 In questo esempio viene elencato il codice sorgente dalla riga 4 del file Form1.vb, con i numeri di riga visibili.  
  
```  
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)  (Comandi di Visual Studio)  
 [Command Window](../../ide/reference/command-window.md) (Finestra di comando)