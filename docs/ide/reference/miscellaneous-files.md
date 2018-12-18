---
title: File esterni | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.newfile
- VS.OpenWith
- MiscellaneousFilesProject
helpviewer_keywords:
- solutions, miscellaneous files
- builds [Visual Studio], miscellaneous files
- standalone files
- Solution Explorer, miscellaneous files
- Miscellaneous Files folder
- files [Visual Studio], outside of containers
- files [Visual Studio], Miscellaneous Files folder
ms.assetid: 5b96640b-8efe-48a4-8d0a-1ae3f9587e44
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8e020e1cc38898f830537afc2346fd20711cd587
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="miscellaneous-files"></a>File esterni
È consigliabile usare gli editor [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per lavorare in modo indipendente sui file di un progetto o di una soluzione. Mentre si ha una soluzione aperta, è possibile aprire e modificare i file senza aggiungerli a una soluzione o a un progetto. I file che si intende usare in modo indipendente dai contenitori sono chiamati file esterni. I file esterni sono esterni a soluzioni e progetti, non sono inclusi nelle compilazioni e non possono essere inclusi in una soluzione sotto il controllo del codice sorgente.  
  
 L'apertura dei file in modo indipendente dal contenitore è utile per diversi motivi. Si potrebbe voler visualizzare un file durante lo sviluppo di una soluzione basata su un progetto ma che non è parte integrante dello sviluppo della soluzione. Tra gli esempi comuni vi sono note o istruzioni di sviluppo, lo schema del database e segmenti di codice. L'utente potrebbe anche voler creare un file autonomo.  
  
 ![Progetti di soluzioni](../../ide/reference/media/projects_solutions_misc.gif "Projects_Solutions_Misc")  
  
 Esplora soluzioni può visualizzare una cartella File esterni per i file se sono abilitate le opzioni per la cartella. È possibile impostare le opzioni da [Documenti, Ambiente, finestra di dialogo Opzioni](../../ide/reference/documents-environment-options-dialog-box.md). Dopo la chiusura di un file esterno, esso non è associato ad alcuna soluzione o progetto particolare a meno che non sia stata abilitata un'opzione a tale scopo.  
  
 La cartella File esterni rappresenta i file come collegamenti. Sebbene questa cartella non sia parte di una soluzione, quando si apre una soluzione alcuni o tutti i file esterni che sono stati aperti quando la soluzione è stata chiusa l'ultima volta vengono aperti nuovamente, in base alle impostazioni per la cartella.  
  
> [!NOTE]
>  Alcuni dei file che non vengono visualizzati nella cartella File esterni sono file che non possono essere modificati all'interno dell'IDE, ad esempio file con estensione zip e doc. L'IDE non rileverà i file che possono essere modificati solo tramite un editor esterno.  
  
## <a name="commands-available-in-the-ide"></a>Comandi disponibili nell'IDE  
 I menu, le barre degli strumenti e i comandi in essi contenuti cambiano a seconda del formato del file aperto. Quando si apre un file di testo, ad esempio, si apre la barra degli strumenti dell'editor di testo e sono disponibili i relativi comandi. Se in seguito si apre un file XML Schema, viene visualizzata la barra degli strumenti XML Schema. Mentre si modifica l'XML Schema, i comandi della barra degli strumenti dell'editor di testo o la stessa barra degli strumenti non sono disponibili. L'XML Schema è la finestra attiva e di conseguenza ha il contesto della selezione corrente. Quando si passa da un file di progetto a un file esterno non vengono più visualizzati tutti i comandi correlati al progetto ma soltanto quelli direttamente correlati al file esterno.  
  
## <a name="folder-display-options"></a>Opzioni di visualizzazione cartella  
 È possibile impostare le opzioni di visualizzazione della cartella File esterni in modo che la cartella venga visualizzata anche se non è aperto alcun file esterno. Il file della soluzione non gestisce in modo permanente un elenco di file esterni. Usa una funzionalità facoltativa che consente di ricordare l'elenco dei file usati di recente (MRU) per ogni utente.  
  
## <a name="see-also"></a>Vedere anche  
 [Solutions and Projects](../../ide/solutions-and-projects-in-visual-studio.md)  (Soluzioni e progetti)  
 [Documents, Environment, Options Dialog Box](../../ide/reference/documents-environment-options-dialog-box.md) (Documenti, Ambiente, finestra di dialogo Opzioni)