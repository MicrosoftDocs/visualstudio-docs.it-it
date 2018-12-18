---
title: Importa/Esporta impostazioni (comando) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d3faa3d77a0aab8edfbe491b9df655931c2f6ed2
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2018
---
# <a name="import-and-export-settings-command"></a>Importa/Esporta impostazioni (comando)
Consente di importare, esportare o reimpostare le impostazioni di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```  
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]  
```  
  
## <a name="switches"></a>Opzioni  
 /export:`filename`  
 Facoltativo. Esporta le impostazioni correnti nel file specificato.  
  
 /import:`filename`  
 Facoltativo. Importa le impostazioni correnti nel file specificato.  
  
 /reset  
 Facoltativo. Reimposta le impostazioni correnti.  
  
## <a name="remarks"></a>Note

Se si esegue questo comando senza opzioni viene visualizzata l'**Importazione/Esportazione guidata delle impostazioni**. Per altre informazioni, vedere [Sincronizzare le impostazioni](../../ide/synchronized-settings-in-visual-studio.md).

## <a name="example"></a>Esempio

Il comando seguente esporta le impostazioni correnti nel file `MyFile.vssettings`.

```shell
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"
```

## <a name="see-also"></a>Vedere anche

[Personalizzare l'IDE di Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)  
[Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)