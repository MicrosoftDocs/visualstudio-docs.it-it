---
title: Sicurezza dei modelli di testo | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- text templates, security
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 5c6b8d64e02562887b2bc438943fdfe7be3b2e1c
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="security-of-text-templates"></a>Sicurezza dei modelli di testo
Modelli di testo sono i seguenti problemi di protezione:  
  
-   Modelli di testo sono vulnerabili a inserimenti di codice arbitrario.  
  
-   Se il meccanismo utilizzato dall'host per trovare un processore di direttiva non è protetto, è possibile eseguire un processore di direttiva dannoso.  
  
## <a name="arbitrary-code"></a>Codice arbitrario  
 Quando si scrive un modello, è possibile inserire qualsiasi codice all'interno di \<# # > tag. In questo modo il codice non autorizzato per l'esecuzione da all'interno di un modello di testo.  
  
 Assicurarsi di ottenere modelli da origini attendibili. Assicurarsi di avvertire gli utenti finali dell'applicazione non eseguire modelli che non provengono da origini attendibili.  
  
## <a name="malicious-directive-processor"></a>Processore di direttiva dannoso  
 Il motore del modello di testo interagisce con un host di trasformazione e uno o più processori di direttive per trasformare il testo del modello in un file di output. Per ulteriori informazioni, vedere [il processo di trasformazione di modello di testo](../modeling/the-text-template-transformation-process.md).  
  
 Se il meccanismo utilizzato dall'host per trovare un processore di direttiva non è protetto, viene eseguito il rischio di eseguire un processore di direttiva dannoso. Il processore di direttiva dannoso potrebbe fornire codice che viene eseguito in `FullTrust` modalità quando viene eseguito il modello. Se si crea un host di trasformazione del modello testo personalizzato, è necessario utilizzare un meccanismo protetto, ad esempio il Registro di sistema per il motore per individuare i processori di direttiva.