---
title: Filtro delle visualizzazioni dei rapporti di prestazioni | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, Profiler Report view filter
- Profiler Report View filter, profiling tools
ms.assetid: 35f89d86-4683-4db1-aa0c-ae0ce65fa524
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6bd2b335635f4fc83eb4b0857f9b5d785eb9dccc
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="performance-report-view-filter"></a>Filtro delle visualizzazioni dei rapporti di prestazioni
La finestra del filtro delle visualizzazioni dei rapporti del profiler si trova nella parte superiore della finestra Rapporto di prestazioni. Se non è visibile, fare clic sul pulsante **Mostra filtro**.  
  
 È possibile modificare ogni clausola filtro per perfezionare i risultati. Nel generatore di filtri sono disponibili le colonne seguenti.  
  
|Elemento del filtro|Descrizione|  
|-----------------|-----------------|  
|E/O|Scegliere **And** se questa clausola e la successiva devono essere entrambe vere (true) per restituire un risultato. Scegliere **Or** se questa clausola o la successiva può essere vera (true) per restituire un risultato.|  
|Campo|Selezionare il campo da usare nella clausola filtro dall'elenco dei campi dati disponibili nel file di rapporto corrente.|  
|Operatore|Scegliere l'operatore che specifica la relazione da impostare tra il campo e il valore.<br /><br /> =    Uguale a<br /><br /> <>  Non uguale a<br /><br /> <    Minore di<br /><br /> >    Maggiore di<br /><br /> <=  Minore o uguale a<br /><br /> >=  Maggiore o uguale a|  
|Valore|Selezionare o immettere il valore da cercare. Per alcuni campi è presente l'elenco dei valori disponibili.|  
  
 È possibile aggiungere clausole filtro fino a ottenere risultati ottimali. Fare clic su **Esegui filtro** per applicare il filtro al file di dati.  
  
 Dalla visualizzazione del rapporto **Contrassegni** è possibile generare clausole filtro per limitare i dati da includere nelle visualizzazioni dei rapporti ai dati raccolti tra due contrassegni. Selezionare i contrassegni da usare come inizio e fine dei dati per il rapporto, quindi fare clic con il pulsante destro del mouse e selezionare **Aggiungi filtro in contrassegni** o **Aggiungi filtro in timestamp**. Entrambi i filtri limitano i dati nel file di dati corrente allo stesso intervallo. L'opzione **Aggiungi filtro in contrassegni** può essere applicata ad altri file con estensione vsp.  
  
 Per salvare il filtro, fare clic su **Esporta filtro** nella barra degli strumenti di Rapporto di prestazioni e quindi specificare un percorso e un nome file per il file con estensione vspf. Per caricare un filtro salvato in precedenza, fare clic su **Importa filtro** e individuare il file del filtro salvato. I file di filtro possono essere usati anche per filtrare file di dati nei computer in cui sono installati gli strumenti di profilatura autonomi. Per altre informazioni, vedere [VSPerfReport](../profiling/vsperfreport.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Analisi dei dati degli strumenti per le prestazioni](../profiling/analyzing-performance-tools-data.md)   
 [VSPerfReport](../profiling/vsperfreport.md)