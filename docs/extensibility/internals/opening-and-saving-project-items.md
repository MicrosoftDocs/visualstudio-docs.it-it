---
title: Apertura e salvataggio di elementi di progetto | Microsoft Docs
description: Informazioni sui diversi approcci per l'apertura e il salvataggio di file per il nuovo tipo di progetto nell'IDE di Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], file persistence
- files [Visual Studio], opening and saving
- editors [Visual Studio SDK], file persistence
ms.assetid: f71898ad-335f-4c43-a177-4da87078afd1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6ff3c76294ce99fa5eeb7bf311307e54f5d0e6cc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063071"
---
# <a name="opening-and-saving-project-items"></a>Apertura e salvataggio di elementi di progetto
Quando si aggiunge un nuovo tipo di progetto, è necessario gestire l'apertura e il salvataggio dei file di progetti nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Integrated Development Environment (IDE). Negli argomenti seguenti vengono illustrati i diversi approcci per l'apertura e il salvataggio di file.

## <a name="in-this-section"></a>Contenuto della sezione
- [Visualizzazione di file tramite il comando Apri file](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)

 Fornisce una descrizione dettagliata del modo in cui l'IDE gestisce il comando **Apri file** e il ruolo dei progetti in risposta a questo comando.

- [Visualizzazione di file tramite il comando Apri con](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)

 Fornisce una spiegazione dettagliata del modo in cui l'IDE gestisce il comando **Apri con** , richiedendo l'apertura di un file che ha una scelta di editor standard.

- [Procedura: Aprire gli editor specifici del progetto](../../extensibility/how-to-open-project-specific-editors.md)

 Vengono fornite istruzioni dettagliate per specificare che i file di un determinato tipo nel progetto devono essere aperti tramite un editor specifico del progetto.

- [Procedura: Aprire gli editor standard](../../extensibility/how-to-open-standard-editors.md)

 Fornisce istruzioni dettagliate per specificare come abilitare l'IDE per l'apertura di un editor standard per i file nel tipo di progetto.

- [Procedura: Aprire gli editor per i documenti aperti](../../extensibility/how-to-open-editors-for-open-documents.md)

 Vengono fornite istruzioni dettagliate per l'apertura di un editor specifico del progetto per un file aperto.

- [Salvataggio di un documento standard](../../extensibility/internals/saving-a-standard-document.md)

 Fornisce una spiegazione dettagliata del modo in cui l'IDE gestisce i comandi **Salva**, **Salva con nome** e **Salva tutti** per un documento aperto in un editor standard.

- [Salvataggio di un documento personalizzato](../../extensibility/internals/saving-a-custom-document.md)

 Fornisce un diagramma e una spiegazione dettagliata del modo in cui l'IDE gestisce i comandi **Salva**, **Salva con nome** e **Salva tutti** i documenti aperti in un editor personalizzato.

- [Scelta dell'editor da usare per aprire un file in un progetto](../../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)

 Viene illustrato il processo che l'IDE segue per selezionare l'editor o la finestra di progettazione appropriata per un file.

## <a name="related-sections"></a>Sezioni correlate
- [Creazione di finestre di progettazione ed editor personalizzati](../../extensibility/creating-custom-editors-and-designers.md)

 Elenca i quattro tipi di editor che l'IDE può ospitare e fornisce le descrizioni di ogni editor.

- [Project Types](../../extensibility/internals/project-types.md) (Tipi di progetto)

 Viene illustrato come i progetti controllano la modalità di compilazione e compilazione del codice, la modalità di apertura degli editor e la formattazione degli elementi del progetto.
