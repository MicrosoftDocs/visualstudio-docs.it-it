---
title: Proprietà dei progetti Clang (Android C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 663140ea-a568-472b-a79a-dfea8818e06a
author: corob
ms.author: mblome
manager: douge
f1_keywords:
- VC.Project.VCClangCompilerTool.AdditionalIncludeDirectories
- VC.Project.VCClangCompilerTool.DebugInformationFormat
- VC.Project.VCClangCompilerTool.ObjectFile
- VC.Project.VCClangCompilerTool.WarningLevel
- VC.Project.VCClangCompilerTool.WarnAsError
- VC.Project.VCClangCompilerTool.Verbose
- VC.Project.VCClangCompilerTool.Optimization
- VC.Project.VCClangCompilerTool.StrictAliasing
- VC.Project.VCClangCompilerTool.OmitFramePointers
- VC.Project.VCClangCompilerTool.ExceptionHandling
- VC.Project.VCClangCompilerTool.EnableFunctionLevelLinking
- VC.Project.VCClangCompilerTool.DataLevelLinking
- VC.Project.VCClangCompilerTool.DataLevelLinking
- VC.Project.VCClangCompilerTool.FloatABI
- VC.Project.VCClangCompilerTool.BufferSecurityCheck
- VC.Project.VCClangCompilerTool.PIC
- VC.Project.VCClangCompilerTool.UseShortEnums
- VC.Project.VCClangCompilerTool.RuntimeTypeInfo
- VC.Project.VCClangCompilerTool.CLanguageStandard
- VC.Project.VCClangCompilerTool.CppLanguageStandard
- VC.Project.VCClangCompilerTool.PreprocessorDefinitions
- VC.Project.VCClangCompilerTool.UndefinePreprocessorDefinitions
- VC.Project.VCClangCompilerTool.UndefineAllPreprocessorDefinitions
- VC.Project.VCClangCompilerTool.ShowIncludes
- VC.Project.VCClangCompilerTool.PrecompiledHeader
- VC.Project.VCClangCompilerTool.PrecompiledHeaderFile
- VC.Project.VCClangCompilerTool.PrecompiledHeaderOutputFileDirectory
- VC.Project.VCClangCompilerTool.PrecompiledHeaderCompileAs
- VC.Project.VCClangCompilerTool.CompileAs
- VC.Project.VCClangCompilerTool.ForcedIncludeFiles
- VC.Project.VCClangCompilerTool.MultiProcessorCompilation
- vc.project.AdditionalOptionsPage
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 8a1fd92a41f145e097615bea4434ea80fd592416
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="clang-project-properties-android-c"></a>Proprietà dei progetti Clang (Android C++)

Proprietà | Descrizione | Scelte
--- | ---| ---
Directory di inclusione aggiuntive | Specifica una o più directory da aggiungere al percorso di inclusione. Usare il punto e virgola (;) come delimitatore per più percorsi. (-I[path]).
Formato informazioni di debug | Specifica il tipo di informazioni di debug generate dal compilatore. | **Nessuno**: non produce informazioni di debug, quindi la compilazione può risultare più veloce.<br>**Informazioni di debug complete (DWARF2)**: genera informazioni di debug DWARF2.<br>**Informazioni su numero di riga**: genera solo le informazioni sul numero riga.<br>
Nome file oggetto | Consente di specificare un nome usato per eseguire l'override del nome del file oggetto predefinito. Può essere un nome di file o di directory. (/Fo[name]).
Livello avvisi | Specifica il grado di severità del controllo effettuato dal compilatore per trovare gli errori del codice.  È possibile contrassegnare altre opzioni direttamente da Opzioni aggiuntive. (/w, /Weverything). | **Disattiva tutti gli avvisi**: disabilita tutti gli avvisi del compilatore.<br>**Abilita tutti gli avvisi**: abilita tutti gli avvisi, inclusi quelli disabilitati per impostazione predefinita.<br>
Considera gli avvisi come errori | Considera tutti gli avvisi del compilatore come errori. Per un nuovo progetto, potrebbe essere preferibile usare /WX in tutte le compilazioni. La risoluzione degli avvisi garantirà il minor numero possibile di errori del codice di difficile individuazione.
Abilita modalità dettagliata | Visualizza i comandi da eseguire e usa l'output dettagliato.
Ottimizzazione | Specifica il livello di ottimizzazione per l'applicazione. | **Personalizzato**: consente di personalizzare l'ottimizzazione.<br>**Disabilitato**: disabilita l'ottimizzazione.<br>**Riduci dimensione**: ottimizza in base alla dimensione.<br>**Ottimizza velocità**: ottimizza in base alla velocità.<br>**Ottimizzazione completa**: ottimizzazioni onerose.<br>
Aliasing restrittivo | Presuppone le regole di aliasing più restrittive.  Un oggetto di un certo tipo non potrà mai risiedere nello stesso indirizzo di un oggetto di un tipo diverso.
Ometti puntatore ai frame | Disabilita la creazione di puntatori ai frame nello stack di chiamate.
Abilita eccezioni C++ | Specifica il modello di gestione delle eccezioni che deve essere usato dal compilatore. | **No**: disabilita la gestione delle eccezioni.<br>**Sì**: abilita la gestione delle eccezioni.<br>**Rimuovi tabelle**: genera gli eventuali dati statici necessari senza influire sul codice generato.<br>
Abilita collegamento a livello di funzione | Consente al compilatore di assemblare le singole funzioni sotto forma di funzioni incluse nel pacchetto (COMDAT). Impostazione necessaria per le operazioni di modifica e continuazione.     (ffunction-sections).
Abilita collegamento a livello di dati | Consente alle ottimizzazioni del linker di rimuovere i dati non usati creando ogni elemento dati in una sezione distinta.
Abilita SIMD avanzato (Neon) | Abilita la generazione di codice per hardware per operazioni con virgola mobile NEON. Si applica solo per l'architettura ARM.
ABI a virgola mobile | Opzione da selezionare per scegliere l'ABI a virgola mobile. | **Soft**: con "Soft" il compilatore genera output contenente chiamate di libreria per operazioni a virgola mobile.<br>**SoftFP**: con "SoftFP" è consentita la generazione di codice con istruzioni a virgola mobile hardware, ma vengono comunque usate le convenzioni di chiamata soft-float.<br>**Hard**: con "Hard" è consentita la generazione di istruzioni a virgola mobile e vengono usate convenzioni di chiamata specifiche di FPU.<br>
Controllo di sicurezza | Il controllo di sicurezza facilita il rilevamento di sovraccarichi del buffer di stack, un attacco comunemente tentato alla sicurezza di un programma. (fstack-protector). | **Disabilita controllo di sicurezza**: consente di disabilitare il controllo di sicurezza.<br>**Abilita controllo di sicurezza**: consente di abilitare il controllo di sicurezza. (fstack-protector)<br>
Codice indipendente dalla posizione | Genera codice indipendente dalla posizione per l'uso in una libreria condivisa.
Usa enum brevi | Il tipo enum usa solo il numero di byte richiesti dall'insieme di possibili valori di input.
Abilita informazioni sui tipi in fase di esecuzione | Aggiunge codice per il controllo dei tipi di oggetto C++ in fase di esecuzione (informazioni sui tipi in fase di esecuzione).     (frtti, fno-rtti)
Standard del linguaggio C | Determina lo standard del linguaggio C. | **Default**<br>**C89**: standard del linguaggio C89.<br>**C99**: standard del linguaggio C99.<br>**C11**: standard del linguaggio C11.<br>**C99 (dialetto GNU)**: standard del linguaggio C99 (dialetto GNU).<br>**C11 (dialetto GNU)**: standard del linguaggio C11 (dialetto GNU).<br>
Standard del linguaggio C++ | Determina lo standard del linguaggio C++. | **Default**<br>**C++03**: standard del linguaggio C++03.<br>**C++11**: standard del linguaggio C++11.<br>**C++14**: standard del linguaggio C++14.<br>**C++03 (dialetto GNU)**: standard del linguaggio C++03 (dialetto GNU).<br>**C++11 (dialetto GNU)**: standard del linguaggio C++11 (dialetto GNU).<br>**C++14 (dialetto GNU)**: standard del linguaggio C++14 (dialetto GNU).<br>
Definizioni del preprocessore | Definisce i simboli di pre-elaborazione per il file di origine. (-D)
Rimuovi definizioni per il preprocessore | Rimuove una o più definizioni per il preprocessore.  (-U [macro])
Rimuovi tutte le definizioni per il preprocessore | Rimuove tutti i valori precedentemente definiti per il preprocessore.  (-undef)
Mostra inclusioni | Indica al compilatore di generare un elenco dei file di inclusione.  (-H)
Intestazione precompilata | Crea/Usa intestazione precompilata: abilita la creazione o l'uso di un'intestazione precompilata durante la compilazione. | **Usa**: usa un'intestazione precompilata.<br>**Senza intestazioni precompilate**: non usa le intestazioni precompilate.<br>
File di intestazione precompilato | Specifica un nome di file di intestazione da usare come file di intestazione precompilato. Questo file verrà aggiunto anche a "File di inclusione imposti" durante la compilazione
Directory del file di output intestazione precompilata | Specifica la directory per l'intestazione precompilato generato. Questa directory verrà aggiunta anche a "Directory di inclusione aggiuntive" durante la compilazione
Compila intestazione precompilata come | Consente di selezionare il linguaggio di compilazione per il file di intestazione precompilato (-x c-header, -x c++-header). | **Compila come codice C**: consente di compilare come codice C.<br>**Compila come codice C++**: consente di compilare come codice C++.<br>
Compila come | Specifica il linguaggio di compilazione per i file con estensione c e cpp.  Il valore predefinito verrà rilevato in base all'estensione c o cpp. (-x c, -x c++) | **Predefinita**: impostazione predefinita.<br>**Compila come codice C**: consente di compilare come codice C.<br>**Compila come codice C++**: consente di compilare come codice C++.<br>
File di inclusione forzati | Uno o più file di inclusione il cui uso è forzato.     (-include [name])
Compilazione a più processori | Compilazione a più processori.
Opzioni aggiuntive | Opzioni aggiuntive.
