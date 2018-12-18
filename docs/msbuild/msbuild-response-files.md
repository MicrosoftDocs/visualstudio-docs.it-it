---
title: File di risposta MSBuild | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- response files, MSBuild
- MSBuild, response files
- MSBuild, .rsp files
- .rsp files
ms.assetid: 9f53987b-20ee-470a-ab62-fce997bb5e15
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 7520a9f51f0d9420039728a75e84d4ed16583738
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="msbuild-response-files"></a>File di risposta MSBuild
I file di risposta (RSP) sono file di testo che contengono opzioni della riga di comando di MSBuild.exe. Ogni opzione può essere su una riga separata oppure tutte le opzioni possono essere sulla stessa riga. Le righe di commento sono precedute da un simbolo **#**. L'opzione **@** viene usata per passare un altro file di risposta a MSBuild.exe.  
  
 Il file di risposta automatica è un file RSP speciale che MSBuild.exe usa automaticamente quando si compila un progetto. Questo file, MSBuild.rsp, deve essere nella stessa directory di MSBuild.exe, in caso contrario non viene rilevato. È possibile modificare questo file per specificare opzioni predefinite della riga di comando per MSBuild.exe. Ad esempio, se si usa lo stesso logger ogni volta che si compila un progetto, è possibile aggiungere l'opzione **/logger** a MSBuild.rsp e MSBuild.exe userà il logger ogni volta che viene compilato un progetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni di riferimento su MSBuild](../msbuild/msbuild-reference.md)   
 [Riferimenti alla riga di comando](../msbuild/msbuild-command-line-reference.md)