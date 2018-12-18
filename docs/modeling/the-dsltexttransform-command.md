---
title: Comando DslTextTransform
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: a3605dd3d6cd7615a2afd4dba18bf2f7bed994f4
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="the-dsltexttransform-command"></a>Comando DslTextTransform
DslTextTransform.cmd è uno script che chiama TextTransform.exe e viene eseguito con le opzioni comuni. È possibile utilizzare DslTextTransformation.cmd per una compilazione notturna di automatizzare il [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] progetti. Per ulteriori informazioni, vedere [la generazione di file con l'utilità di TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).

 DslTextTransform.cmd si trova nella directory seguente:

 **\<Percorso di installazione di Visual Studio SDK > \visualstudiointegration\tools\bin.**

 È possibile specificare gli argomenti seguenti come input per DslTextTransform.cmd:

-   La directory di output del progetto di modello di dominio.

-   La directory di output del progetto di definizione della finestra di progettazione.

-   Il percorso del file di modello di testo.

 DslTextTransform.cmd elabora il file di modello di testo specificato con i processori di direttive predefinito e gli assembly. Se si creano i processori di direttiva personalizzati, è possibile creare un file batch che chiama TextTransform.exe. In questo file batch, è possibile specificare gli assembly e i processori di direttiva personalizzati associati.