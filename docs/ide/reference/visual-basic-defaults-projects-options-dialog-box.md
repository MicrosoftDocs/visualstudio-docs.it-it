---
title: Impostazioni predefinite di Visual Basic, Progetti, finestra di dialogo Opzioni | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.ToolsOptionsPages.Projects.VBDefaults
helpviewer_keywords:
- Option Explicit statement, setting in the IDE
- Option Compare statement, setting in the IDE
- Option Strict statement, setting in the IDE
ms.assetid: 2465cd9d-18b6-4c4a-b1ea-86dbab23fc79
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 1d71966c83120f235371809c21f1265d615fa5de
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="visual-basic-defaults-projects-options-dialog-box"></a>Impostazioni predefinite di Visual Basic, Progetti, finestra di dialogo Opzioni
Specifica le impostazioni predefinite per le opzioni dei progetti Visual Basic. Alla creazione di un nuovo progetto, le istruzioni specificate per le opzioni verranno aggiunte all'intestazione del progetto nell'editor di codice. Le opzioni si applicano a tutti i progetti Visual Basic.  
  
 Per accedere a questa finestra di dialogo, nel menu **Strumenti** fare clic su **Opzioni**, espandere la cartella **Progetti e soluzioni** e quindi fare clic su **Impostazioni predefinite di Visual Basic**.  
  
 **Option Explicit**  
 Imposta il valore predefinito del compilatore in modo da richiedere le dichiarazioni esplicite delle variabili. Per impostazione predefinita, **Option Explicit** è impostato su **On**. Per altre informazioni, vedere [/optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit).  
  
 **Option Strict**  
 Imposta il valore predefinito del compilatore in modo da richiedere le conversioni esplicite verso un tipo di dati più piccolo e da non consentire l'associazione tardiva. Per impostazione predefinita, **Option Strict** è impostato su **Off**. Per altre informazioni, vedere [/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict).  
  
 **Option Compare**  
 Imposta il valore predefinito del compilatore per il confronto di stringhe: binario (con distinzione tra maiuscole e minuscole) o basato sul testo (senza distinzione tra maiuscole e minuscole). Per impostazione predefinita, **Option Compare** è impostato su **Binary**. Per altre informazioni, vedere [/optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare).  
  
 **Option Infer**  
 Imposta il valore predefinito del compilatore per l'inferenza del tipo di variabile locale. Per impostazione predefinita, **Option Infer** è impostato su **On** per i nuovi progetti e su **Off** per i progetti creati nelle versioni precedenti di Visual Basic dei quali è stata eseguita la migrazione. Per altre informazioni, vedere [/optioninfer](/dotnet/visual-basic/reference/command-line-compiler/optioninfer).  
  
## <a name="see-also"></a>Vedere anche  
 [Solutions and Projects](../../ide/solutions-and-projects-in-visual-studio.md) (Soluzioni e progetti)