---
title: Apertura e salvataggio di elementi di progetto | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], file persistence
- files [Visual Studio], opening and saving
- editors [Visual Studio SDK], file persistence
ms.assetid: f71898ad-335f-4c43-a177-4da87078afd1
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a270811cc13d4b0e9af027ec2b4b5d2032582a3e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="opening-and-saving-project-items"></a>Apertura e salvataggio di elementi di progetto
Quando si aggiunge un nuovo tipo di progetto, è necessario gestire l'apertura e salvataggio dei file in progetti di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE). Gli argomenti seguenti descrivono i diversi approcci per l'apertura e salvataggio di file.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Visualizzazione di file tramite il comando Apri file](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)  
 Fornisce una spiegazione dettagliata della modalità di gestione dell'IDE di **Apri** comando e il ruolo di progetti in risposta a questo comando.  
  
 [Visualizzazione di file tramite il comando Apri con](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)  
 Viene fornita una spiegazione passo passo dettagliata del modo in cui l'IDE gestisce il **Apri con** comando, che richiede l'apertura di un file con alcune scelte di editor standard.  
  
 [Procedura: Aprire gli editor specifici del progetto](../../extensibility/how-to-open-project-specific-editors.md)  
 Vengono fornite istruzioni dettagliate per la specifica che i file di un particolare tipo di progetto devono essere aperto usando un editor specifico del progetto.  
  
 [Procedura: Aprire gli editor standard](../../extensibility/how-to-open-standard-editors.md)  
 Vengono fornite istruzioni dettagliate per la specifica come abilitare l'IDE aprire un editor standard per i file nel tipo di progetto.  
  
 [Procedura: Aprire gli editor per i documenti aperti](../../extensibility/how-to-open-editors-for-open-documents.md)  
 Vengono fornite istruzioni dettagliate per aprire un editor specifico del progetto per un file aperto.  
  
 [Salvataggio di un documento standard](../../extensibility/internals/saving-a-standard-document.md)  
 Fornisce una spiegazione dettagliata di come l'IDE gestisce il **salvare**, **Salva con nome**, e **Salva tutto** comandi per un documento aperto in un editor standard.  
  
 [Salvataggio di un documento personalizzato](../../extensibility/internals/saving-a-custom-document.md)  
 Fornisce un diagramma e una spiegazione dettagliata di come l'IDE gestisce il **salvare**, **Salva con nome**, e **Salva tutto** comandi per i documenti aperti in un editor personalizzato.  
  
 [Scelta dell'editor da usare per aprire un file in un progetto](../../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)  
 Illustra il processo che segue l'IDE per selezionare l'editor appropriato o una finestra di progettazione per un file.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Creazione di finestre di progettazione ed editor personalizzati](../../extensibility/creating-custom-editors-and-designers.md)  
 Elenca i quattro tipi di editor che IDE può ospitare e vengono fornite descrizioni di ogni editor.  
  
 [Tipi di progetto](../../extensibility/internals/project-types.md)  
 Viene descritto come progetti consentono di controllare la modalità di codice viene compilato e compilato, come aprire gli editor e la formattazione di elementi di progetto.