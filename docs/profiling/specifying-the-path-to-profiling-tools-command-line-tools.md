---
title: Specifica del percorso degli strumenti da riga di comando degli strumenti di profilatura | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b33ee79d51dfcdb3db9021d3613672c44aef8956
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="specifying-the-path-to-profiling-tools-command-line-tools"></a>Specifica del percorso degli strumenti da riga di comando degli strumenti di profilatura
Il percorso degli strumenti da riga di comando di Strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] non è aggiunto alla variabile di ambiente PATH. Nei computer a 32 bit gli strumenti si trovano in un'unica directory. Nei computer a 64 bit sono disponibili versioni a 32 bit e a 64 bit degli strumenti di profilatura.  
  
## <a name="32-bit-computers"></a>Computer a 32 bit  
 Nei computer a 32 bit la directory predefinita per gli strumenti di profilatura è *Unità*\Programmi\Microsoft Visual Studio 11.0\Team Tools\Performance Tools.  
  
## <a name="64-bit-computers"></a>Computer a 64 bit  
 Nei computer a 64 bit specificare il percorso in base alla piattaforma di destinazione dell'applicazione da sottoporre a profilatura.  
  
-   La directory predefinita per gli strumenti di profilatura per applicazioni a 32 bit è la seguente:  
  
     *Unità*\Programmi (x86)\Microsoft Visual Studio 11.0\Team Tools\Performance Tools  
  
-   La directory predefinita per gli strumenti di profilatura per applicazioni a 64 bit è la seguente:  
  
     *Unità*\Programmi (x86)\Microsoft Visual Studio 11.0\Team Tools\Performance Tools\x64