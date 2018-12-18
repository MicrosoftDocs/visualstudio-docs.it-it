---
title: Proprietà dei linker Clang (Android C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 66e88848-116c-4eb0-bc57-183394d35b57
author: corob
ms.author: mblome
manager: douge
f1_keywords:
- VC.Project.VCLinkerTool.OutputFile
- VC.Project.VCLinkerTool.ShowProgress
- VC.Project.VCLinkerTool.Version
- VC.Project.VCLinkerTool.VerboseOutput
- VC.Project.VCLinkerTool.IncrementalLink
- VC.Project.VCLinkerTool.SharedLibrarySearchPath
- VC.Project.VCLinkerTool.AdditionalLibraryDirectories
- VC.Project.VCLinkerTool.UnresolvedReferences
- VC.Project.VCLinkerTool.OptimizeForMemory
- VC.Project.VCLinkerTool.IgnoreDefaultLibraryNames
- VC.Project.VCLinkerTool.ForceSymbolReferences
- VC.Project.VCLinkerTool.ForceFileOutput
- VC.Project.VCLinkerTool.OmitDebuggerSymbolInformation
- VC.Project.VCLinkerTool.GenerateMapFile
- VC.Project.VCLinkerTool.Relocation
- VC.Project.VCLinkerTool.FunctionBinding
- VC.Project.VCLinkerTool.NoExecStackRequired
- VC.Project.WholeArchive
- VC.Project.AdditionalOptionsPage
- VC.Project.VCLinkerTool.AdditionalDependencies
- VC.Project.VCLinkerTool.LibraryDependencies
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 3611268c17d26328d131eacafb92b1ce55c7d07f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="clang-linker-properties-android-c"></a>Proprietà dei linker Clang (Android C++)

Proprietà | Descrizione | Scelte
--- | ---| ---
File di output | L'opzione sostituisce il nome e il percorso predefiniti del programma creato dal linker. (-o)
Mostra stato | Visualizza i messaggi di stato del linker.
Versione | L'opzione -version indica al linker di inserire un numero di versione nell'intestazione dell'eseguibile.
Abilita output dettagliato | L'opzione -verbose indica al linker di visualizzare messaggi dettagliati per il debug.
Abilita collegamento incrementale | L'opzione indica al linker di abilitare il collegamento incrementale.
Percorso di ricerca libreria condivisa | Consente all'utente di popolare il percorso di ricerca della libreria condivisa.
Directory librerie aggiuntive | Consente all'utente di sostituire il percorso della libreria dell'ambiente. (-L cartella).
Segnala riferimenti a simboli non risolti | Se abilitata, questa opzione segnala i riferimenti a simboli non risolti.
Ottimizza in base all'utilizzo della memoria | Ottimizza in base all'utilizzo della memoria leggendo nuovamente, se necessario, le tabelle di simboli.
Ignora librerie predefinite specifiche | Specifica il nome di una o più librerie predefinite da ignorare.
Imponi riferimenti al simbolo | Impone l'inserimento del simbolo nel file di output come simbolo non definito.
Informazioni sui simboli del debugger | Informazioni sui simboli del debugger ottenuti dal file di output. | **Includi tutti**<br>**Ometti i simboli non necessari per la rilocazione**<br>**Ometti solo le informazioni sui simboli del debugger**<br>**Ometti tutte le informazioni sui simboli**<br>
Includi le informazioni sui simboli del debugger nel pacchetto | Rimuove le informazioni sui simboli del debugger prima della creazione del pacchetto.  Per il debug verrà usata una copia del file binario originale.
Nome file di mapping | L'opzione Map indica al linker di creare un file di mapping con il nome specificato dall'utente.
Contrassegna le variabili come di sola lettura dopo la rilocazione | Questa opzione contrassegna le variabili come di sola lettura dopo la rilocazione.
Abilita il binding immediato delle funzioni | Questa opzione contrassegna l'oggetto per il binding immediato delle funzioni.
Richiedi stack eseguibili | Questa opzione contrassegna l'output in modo da non richiedere lo stack degli eseguibili.
Intero archivio | Con Intero archivio viene usato tutto il codice disponibile in origini e dipendenze aggiuntive.
Opzioni aggiuntive | Opzioni aggiuntive.
Dipendenze aggiuntive | Specifica altri elementi da aggiungere alla riga di comando del collegamento.
Dipendenze libreria | Questa opzione consente di specificare librerie aggiuntive da aggiungere alla riga di comando del linker. La libreria aggiuntiva verrà aggiunta alla fine della riga di comando del linker e sarà contraddistinta dal prefisso "lib" e dall'estensione "a".  (-lFILE)
