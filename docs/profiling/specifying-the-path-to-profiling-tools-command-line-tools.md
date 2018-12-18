---
title: Specifica del percorso degli strumenti da riga di comando degli strumenti di profilatura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8e25d5052cbc70e4a45040f8ebadb8cb36daa053
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
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