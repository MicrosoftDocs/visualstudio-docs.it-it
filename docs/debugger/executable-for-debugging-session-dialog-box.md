---
title: Eseguibile per la finestra di dialogo di sessione di debug | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.exefordebug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- executable files, specifying when debugging
- DLLs, debugging
- debugger, Executable for Debugging Session dialog box
- Executable for Debugging Session dialog box
ms.assetid: c0ddbe32-b99f-4425-acf1-f48842804f56
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 98cee61b9a43e031daf468555f31349d10023fcc
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="executable-for-debugging-session-dialog-box"></a>finestra di dialogo Eseguibile per la sessione di debug
Questa finestra di dialogo viene visualizzata quando si tenta di eseguire il debug di una DLL per la quale non è stato specificato alcun eseguibile. Visual Studio non è in grado di avviare direttamente una DLL, ma avvierà l'eseguibile specificato. È possibile eseguire il debug della DLL quando viene chiamata dall'eseguibile.  
  
 **Nome del file eseguibile**  
 Immettere il nome e il percorso di un file eseguibile che chiama la DLL sottoposta a debug.  
  
 **Accedere all'URL in cui può essere il progetto (solo ATL Server)**  
 Se si esegue il debug di una DLL di ATL Server, immettere l'URL del progetto.  
  
 Una volta immesse, queste impostazioni sono archiviate nelle Pagine delle proprietà del progetto, pertanto non è necessario immetterle nuovamente per le successive sessioni di debug. Se occorre modificare queste impostazioni, aprire le Pagine delle proprietà e modificare i valori. Per ulteriori informazioni su come specificare un file eseguibile per la sessione di debug, vedere [debug delle DLL](../debugger/how-to-debug-from-a-dll-project.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Debug in Visual Studio](../debugger/index.md)  
 [Tour delle funzionalità del debugger](../debugger/debugger-feature-tour.md)