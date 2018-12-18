---
title: Introduzione (Debug Interface Access SDK) | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- .dbg files
- DBG files
ms.assetid: cb3d040a-2846-40d7-bdbc-8a5beb5dd2f6
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d37843917be3a2668e9a2887f046eaee00600dc8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-debug-interface-access-sdk"></a>Introduzione (Debug Interface Access SDK)
Il Debug Interface Access (DIA) SDK fornisce un esempio che illustra come usare l'API di DIA e la documentazione di istruzioni. Utilizzare le interfacce e metodi in DIA SDK per sviluppare applicazioni personalizzate che aprire i file con estensione pdb e DBG e ricerca di contenuto per i simboli, i valori, gli attributi, gli indirizzi e altre informazioni di debug. Questo SDK fornisce inoltre le tabelle di riferimento per le proprietà associate ai simboli presenti nelle applicazioni C++.  
  
 Per utilizzare al meglio il DIA SDK, è necessario avere familiarità con gli elementi seguenti:  
  
-   Linguaggio di programmazione C++  
  
-   Programmazione COM  
  
-   Ambiente Visual Studio sviluppo integrato (IDE) per la compilazione degli esempi di  
  
 Il DIA SDK viene normalmente installato con Visual Studio e il percorso predefinito è *[unità]*\Programmi\Microsoft 9.0\DIA di Visual Studio SDK. Come parte dell'installazione, il MSDIA90, che implementa il DIA SDK, viene registrato automaticamente in modo che tutto ciò che è necessario eseguire per poterlo utilizzare includono `dia2.h` nel programma e collegamento a `diaguids.lib`.  
  
 Intestazione: include\dia2.h  
  
 Libreria: lib\diaguids.lib  
  
 DLL: bin\msdia80.dll  
  
 IDL: idl\dia2.idl  
  
## <a name="in-this-section"></a>In questa sezione  
 [Panoramica](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)  
 Esamina l'architettura di base di DIA.  
  
 [Esecuzione di query nel file PDB](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 Vengono fornite istruzioni dettagliate su come utilizzare l'API di DIA per eseguire query di un file con estensione pdb.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug Interface Access SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)