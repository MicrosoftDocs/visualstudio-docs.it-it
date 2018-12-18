---
title: L'installazione di Visual Studio SDK | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 8a5a4721eea178e4a9ab5766760ccf1405589684
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="installing-the-visual-studio-sdk"></a>L'installazione di Visual Studio SDK
Visual Studio SDK è una funzionalità facoltativa di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento.  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Installazione di Visual Studio SDK come parte di un'installazione di Visual Studio  
 Se si desidera includere il SDK nell'installazione di Visual Studio, è necessario installare il **lo sviluppo di estensioni di Visual Studio** carico di lavoro in **altri set di strumenti**. Verrà installato Visual Studio SDK, nonché i prerequisiti necessari. È possibile ottimizzare ulteriormente l'installazione, selezionare o visualizzare componenti deselezionando la casella di riepilogo. 
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>Installazione di Visual Studio SDK dopo l'installazione di Visual Studio  
 Se si decide di installare Visual Studio SDK dopo aver completato l'installazione di Visual Studio, eseguire nuovamente il programma di installazione di Visual Studio e selezionare il **lo sviluppo di estensioni di Visual Studio** carico di lavoro.  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>L'installazione da una soluzione di Visual Studio SDK  
 Se si apre una soluzione con un progetto di estensibilità senza prima aver installato Visual Studio SDK, verrà richiesto da una barra informazioni evidenziato sopra Esplora soluzioni. Dovrebbe essere simile al seguente:  
  
 ![SolutionExplorerInstall](../extensibility/media/solutionexplorerinstall.png "SolutionExplorerInstall")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>L'installazione di Visual Studio SDK dalla riga di comando  
Come con qualsiasi carico di lavoro di Visual Studio o nel componente, è possibile installare anche l'elemento dalla riga di comando. Vedere [utilizzare i parametri della riga di comando per installare Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) per informazioni dettagliate sulle opzioni della riga di comando appropriato e come determinare gli identificatori del carico di lavoro o un componente.
  
 Si noti che è necessario utilizzare il programma di installazione di Visual Studio corrisponde alla versione installata di Visual Studio. Ad esempio, se è installato nel computer Visual Studio Enterprise, è necessario eseguire il programma di installazione di Visual Studio Enterprise (vs_enterprise.exe).