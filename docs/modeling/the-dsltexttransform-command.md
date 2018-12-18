---
title: Comando DslTextTransform | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, commands
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 24a3f292633b915678bad232a4a671c7906e15cb
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="the-dsltexttransform-command"></a>Comando DslTextTransform
DslTextTransform.cmd è uno script che chiama TextTransform.exe e viene eseguito con le opzioni comuni. È possibile utilizzare DslTextTransformation.cmd per una compilazione notturna di automatizzare il [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] progetti. Per ulteriori informazioni, vedere [la generazione di file con l'utilità di TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).  
  
 DslTextTransform.cmd si trova nella directory seguente:  
  
 **\<Il percorso di installazione di Visual Studio SDK > \visualstudiointegration\tools\bin.**  
  
 È possibile specificare gli argomenti seguenti come input per DslTextTransform.cmd:  
  
-   La directory di output del progetto di modello di dominio.  
  
-   La directory di output del progetto di definizione della finestra di progettazione.  
  
-   Il percorso del file di modello di testo.  
  
 DslTextTransform.cmd elabora il file di modello di testo specificato con i processori di direttive predefinito e gli assembly. Se si creano i processori di direttiva personalizzati, è possibile creare un file batch che chiama TextTransform.exe. In questo file batch, è possibile specificare gli assembly e i processori di direttiva personalizzati associati.