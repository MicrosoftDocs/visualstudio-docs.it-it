---
title: Salvataggio delle informazioni sui simboli con i file di dati di prestazioni | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- packsymbols, in profiling tools reports
- profiling tools, packsymbols
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 15a1a6888ca35df54ff6073aefaf686327b4cd8a
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="saving-symbol-information-with-performance-data-files"></a>Salvataggio delle informazioni sui simboli con i file di dati di prestazioni

Se si usa l'IDE di Visual Studio per analizzare i file e si prevede di spostare il file con estensione vsp in un altro computer, è necessario configurare le impostazioni del progetto relative alle prestazioni per salvare o *serializzare* i simboli nel file di rapporto. In questo modo viene incrementata la dimensione di un file di rapporto. La serializzazione dei simboli è necessaria per due motivi:

- Per incorporare i simboli del codice in un rapporto di prestazioni prima che gli assembly di destinazione vadano persi dal relativo percorso di archiviazione temporanea.

- Per conservare i simboli, in modo che il rapporto di prestazioni sia portabile dal computer profilato e restituisca le stesse informazioni se il rapporto viene aperto per l'analisi in un altro computer che potrebbe avere simboli diversi.

È possibile serializzare i simboli dall'IDE di Visual Studio o dalla riga di comando:

- Per serializzare i simboli nell'IDE di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], scegliere **Strumenti** nella barra dei menu e quindi fare clic su **Opzioni**. Nella finestra **Opzioni** selezionare **Strumenti per le prestazioni** e quindi selezionare la casella di controllo **Serializzare automaticamente le informazioni sui simboli**.

- PACKSYMBOLS è l'opzione della riga di comando equivalente per salvare file di rapporto. Per serializzare i simboli, digitare **vsperfreport /summary:all /packsymbols nomefile.vsp**.

## <a name="troubleshooting-symbol-problems"></a>Risoluzione dei problemi relativi ai simboli

Se non si visualizzano i simboli nel codice, sono disponibili alcune soluzioni comuni:

- Eseguire vsperfreport /debugsympath dalla riga di comando per visualizzare un elenco completo dei percorsi in cui i componenti del profiler caricano le informazioni sui simboli e verificare se i file dei simboli usati corrispondono ai file usati dal progetto.

- Assicurarsi di eseguire vsperfreport con il flag /PACKSYMBOLS o di avere selezionato nell'IDE di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] l'opzione di serializzazione delle informazioni sui simboli nelle opzioni generali di Esplora prestazioni.

- Se si raccolgono dati di tipo, aggiungere /SUMMARY:TYPE alla riga di comando vsperfreport.

 Se non è possibile visualizzare i simboli da Windows o da altri programmi Microsoft:

- Assicurarsi di avere impostato il percorso della cache dei simboli di Windows. Effettuare una delle operazioni seguenti per impostare il percorso della cache dei simboli:

  - Impostare l'opzione Debugger->Simboli nell'IDE di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sul percorso corretto.

  - Aggiungere l'opzione -symbolpath alla riga di comando VSPerfReport per includere i simboli.

- Se non sono visibili simboli in [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], assicurarsi di avere configurato correttamente il server dei simboli per il server ASP.

## <a name="repacking-symbols"></a>Ricompressione dei simboli

Per ricomprimere i simboli in un rapporto, usare lo strumento della riga di comando VsPerfReport. Usare le righe di comando seguenti:

VsPerfReport -clearpackedsymbols nomefile.vsp

VsPerfReport -packsymbols -summary:all nomefile.vsp

## <a name="see-also"></a>Vedere anche

[Salvataggio ed esportazione dei dati degli strumenti per le prestazioni](../profiling/saving-and-exporting-performance-tools-data.md)  
[Procedura: Fare riferimento alle informazioni sui simboli di Windows](../profiling/how-to-reference-windows-symbol-information.md)  
[VSPerfReport](../profiling/vsperfreport.md)