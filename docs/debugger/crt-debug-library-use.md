---
title: Utilizzo della libreria di Debug CRT | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.debug.runtime
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /DEBUG linker option [C++]
- crtdbg.h file
- debug library
- MDd compiler option [C++]
- libraries, CRT debug library
- MTd compiler option [C++]
- LDd compiler function [C++]
- /MTd compiler option [C++]
- /MDd compiler option [C++]
- debugging [CRT], CRT debug library
- DEBUG linker option [C++]
- /LDd compiler function [C++]
ms.assetid: 464de16b-4215-4787-9bfa-921aaff9d9f4
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 420dcc98aad4f4ca2ad76d16b7f4c6c7c51d2beb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="crt-debug-library-use"></a>Utilizzo della libreria di debug CRT
La libreria di runtime del linguaggio C offre un ampio supporto per il debug. Per utilizzare una delle librerie di debug CRT, è necessario collegare con [/debug](/cpp/build/reference/debug-generate-debug-info) e compilare con **/MDd**, **/MTd**, o **/LDd**.  
  
## <a name="remarks"></a>Note  
 Le definizioni e le macro principali del debug CRT sono disponibili nel file di intestazione CRTDBG.h.  
  
 Le funzioni in librerie di debug CRT sono compilate con informazioni di debug ([/Z7, /Zd, /Zi, /ZI (formato informazioni di Debug)](/cpp/build/reference/z7-zi-zi-debug-information-format)) e senza ottimizzazione. Alcune funzioni contengono asserzioni per la verifica di parametri ricevuti e viene fornito il codice sorgente. Grazie a questo codice sorgente è possibile eseguire passo passo le funzioni CRT per accertarsi che funzionino correttamente e rilevare eventuali parametri o stati di memoria errati. Parte della tecnologia CRT è proprietaria e non fornisce codice sorgente per la gestione delle eccezioni, la virgola mobile e alcune altre routine.  
  
 Quando si implementa Visual C++, è possibile scegliere di installare il codice sorgente della libreria di runtime del linguaggio C sul disco rigido. Se non si installa il codice sorgente, sarà necessario il CD-ROM per eseguire un passaggio alla volta le funzioni CRT.  
  
 Per ulteriori informazioni sulle varie librerie di runtime è possibile utilizzare, vedere [C Run-Time Libraries](/cpp/c-runtime-library/crt-library-features).  
  
## <a name="see-also"></a>Vedere anche  
 [Tecniche di debug CRT](../debugger/crt-debugging-techniques.md)   
 [/MD, /MT, /LD (utilizzo della libreria Run-Time)](/cpp/build/reference/md-mt-ld-use-run-time-library)