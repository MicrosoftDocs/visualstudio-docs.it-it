---
title: Informazioni di riferimento sulle attività MSBuild WPF | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- WPF MSBuild task reference [WPF MSBuild], term/definition table
- build tasks [WPF MSBuild], Microsoft build engine
- build tasks using the Microsoft build engine [WPF MSBuild], compile markup and process resources
- WPF MSBuild task reference [WPF MSBuild]
ms.assetid: 96df0370-e50f-4ffc-9771-b12fb8721143
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 30acdaddc132a40c37bc489b07ae3b7f2843b215
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="wpf-msbuild-task-reference"></a>Informazioni di riferimento sulle attività MSBuild WPF
Il processo di compilazione di Windows Presentation Foundation (WPF) estende Microsoft Build Engine (MSBuild) con un set aggiuntivo di attività di compilazione, tra cui attività di compilazione del markup ed elaborazione di risorse.  
  
## <a name="in-this-section"></a>In questa sezione  
 [FileClassifier](../msbuild/fileclassifier-task.md)  
 Classifica un set di risorse di origine come quelle che verranno incorporate in un assembly. Se una risorsa non è localizzabile, viene incorporata nell'assembly dell'applicazione principale. In caso contrario, viene incorporata in un assembly satellite.  
  
 [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)  
 Genera un assembly se in un progetto almeno una pagina [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] fa riferimento a un tipo dichiarato localmente nel progetto. L'assembly generato viene rimosso dopo il completamento del processo di compilazione o in caso di esito negativo del processo.  
  
 [GetWinFXPath](../msbuild/getwinfxpath-task.md)  
 Restituisce la directory del runtime [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)] corrente.  
  
 [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)  
 Converte i file di progetto [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] non localizzabili in formato binario compilato.  
  
 [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)  
 Esegue la compilazione del markup del secondo passaggio sui file [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] che fanno riferimento ai tipi nello stesso progetto.  
  
 [MergeLocalizationDirectives](../msbuild/mergelocalizationdirectives-task.md)  
 Unisce i commenti e gli attributi di localizzazione di uno o più file in formato binario [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] in un singolo file per l'intero assembly.  
  
 [ResourcesGenerator](../msbuild/resourcesgenerator-task.md)  
 Incorpora una o più risorse (jpg, ico, bmp, [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] in formato binario e altri tipi di estensione) in un file con estensione resources.  
  
 [UidManager](../msbuild/uidmanager-task.md)  
 Controlla, aggiorna o rimuove gli identificatori univoci (UID) per localizzare tutti gli elementi [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] inclusi nei file [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] di origine.  
  
 [UpdateManifestForBrowserApplication](../msbuild/updatemanifestforbrowserapplication-task.md)  
 Aggiunge l'elemento **\<hostInBrowser />** al manifesto dell'applicazione (*nomeprogetto*.exe.manifest) quando viene compilato un progetto [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [MSBuild](../msbuild/msbuild.md)