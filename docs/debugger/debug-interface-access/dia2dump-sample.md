---
title: Esempio Dia2dump | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- sample applications [DIA SDK]
- Dia2dump sample [DIA SDK]
ms.assetid: 492c0893-7043-452f-a020-890a47230d20
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5559d1ac2a03eaeb1dca57531cd2f19831851d3b
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="dia2dump-sample"></a>Esempio Dia2dump
L'esempio Dia2dump viene installato con Visual Studio e contiene il database di origine dia2dump.cpp. Il file eseguibile compilato viene eseguito dalla riga di comando e visualizza il contenuto di un file di database (con estensione pdb) intero programma.  
  
### <a name="to-install-the-sample"></a>Per installare l'esempio  
  
1.  Verificare che il sistema soddisfi tutti i requisiti di installazione descritti nella pagina Inizio installazione di Visual Studio.  
  
2.  Installazione di Visual Studio e seguire tutte le istruzioni di installazione e configurazione per gli esempi inclusi.  
  
#### <a name="to-build-the-sample"></a>Per compilare l'esempio  
  
1.  Aprire il file Dia2dump.sln in Visual Studio. (Se necessario, di Visual Studio prima di aggiornare il progetto Dia2dump.)  
  
2.  Nelle pagine delle proprietà di progetto, nelle **C/C++** &#124; **generali** &#124; **directory di inclusione aggiuntive** proprietà, specificare il `..\DIA SDK\include` directory. In questo modo si garantisce che il compilatore riesca a trovare il file dia2.h.  
  
3.  Nel **compilare** menu, fare clic su **Ricompila soluzione**.  
  
4.  Chiudere Visual Studio.  
  
#### <a name="to-run-the-sample"></a>Per eseguire l'esempio  
  
1.  Aprire un prompt dei comandi e digitare quanto segue:  
  
    ```  
    dia2dump filename  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Origine Dia2dump.cpp](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)   
 [Conversione, migrazione e aggiornamento dei progetti di Visual Studio](../../porting/port-migrate-and-upgrade-visual-studio-projects.md)