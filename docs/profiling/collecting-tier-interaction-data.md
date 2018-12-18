---
title: Raccolta di dati di interazione tra livelli | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.performance.property.tierinteraction
helpviewer_keywords:
- Profiling Tools,ADO.NET profiling
- tier interaction profiling method
- Profiling Tools,tier-interaction method
- ADO.NET performance profiling
ms.assetid: 47a944c2-3098-497c-8fc7-e1f43d750bbc
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c12d279541e60353a9e6e4354a16870713498b66
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="collecting-tier-interaction-data"></a>Raccolta di dati di interazione tra livelli
La profilatura delle interazioni tra livelli offre informazioni aggiuntive sui tempi di esecuzione delle funzioni di applicazioni multilivello che comunicano con i database tramite i servizi ADO.NET. I dati vengono raccolti solo per le chiamate di funzione sincrone.  
  
 **Versioni di Visual Studio**  
  
 I dati di profilatura dell'interazione tra livelli possono essere raccolti tramite Visual Studio Ultimate, Visual Studio Premium o Visual Studio Professional. Tuttavia, i dati di profilatura dell'interazione tra livelli possono essere visualizzati solo in VS Ultimate e VS Premium.  
  
 **Windows 8 e Windows Server 2012**  
  
 Per raccogliere dati di interazione tra livelli nelle applicazioni desktop di Windows 8 e nelle applicazioni Windows Server 2012, è necessario utilizzare il metodo di strumentazione. Non è possibile raccogliere dati di interazione tra livelli per le app UWP. Vedere [Performance Tools on Windows 8 and Windows Server 2012 applications](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md) (Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012). È possibile includere i dati di interazione tra livelli in tutti i metodi di profilatura su un'altra versione di Windows supportata.  
  
 **Creazione guidata sessione di prestazioni**  
  
 A causa di un bug nella Creazione guidata sessione di prestazioni, è necessario aggiungere l'opzione di raccolta dati di interazione tra livelli ad un'esecuzione di profilatura da Esplora prestazioni. È inoltre necessario aggiungere il progetto, il file eseguibile o il sito Web al nodo di destinazione di Esplora prestazioni.  
  
### <a name="to-add-tier-interaction-data-to-a-profiling-run-by-using-the-performance-session-property-pages"></a>Per aggiungere dati di interazione tra livelli all'esecuzione della profilatura tramite le pagine delle proprietà della sessione di prestazioni  
  
1.  In Esplora prestazioni scegliere **Proprietà** dal menu contestuale.  
  
2.  Selezionare la pagina **Interazioni tra livelli** e quindi selezionare la casella di controllo **Abilita profilatura interazione tra livelli**.  
  
3.  In Esplora prestazioni selezionare il nodo **Destinazioni** e quindi specificare il progetto, il file eseguibile o il sito Web che si vuole sottoporre a profilatura.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione Interazioni tra livelli](../profiling/tier-interactions-view.md)