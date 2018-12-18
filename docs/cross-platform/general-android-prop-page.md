---
title: "Proprietà dei progetti generali (Android C++)| Microsoft Docs"
ms.custom: 
ms.date: 10/23/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-mobile
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 65f4868b-b864-4989-a275-1e51869ef599
author: corob
ms.author: mblome
manager: ghogen
f1_keywords:
- VC.Project.VCConfiguration.OutputDirectory
- VC.Project.VCConfiguration.IntermediateDirectory
- VC.Project.VCConfiguration.TargetName
- VC.Project.VCConfiguration.TargetExt
- VC.Project.VCConfiguration.DeleteExtensionsOnClean
- VC.Project.VCConfiguration.BuildLogFile
- VC.Project.VCConfiguration.PlatformToolset
- VC.Project.VCConfiguration.ConfigurationType
- VC.Project.VCConfiguration.DeleteExtensionsOnClean
- VC.Project.VCConfiguration.UseOfSTL
- VC.Project.VCConfiguration.ThumbMode
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 6ec191d4f5deefd959c4647ae98a1626a0bd1d36
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="general-project-properties-android-c"></a>Proprietà dei progetti generali (Android C++)

Proprietà | Descrizione | Scelte
--- | ---| ---
Directory di output | Specifica un percorso relativo della directory dei file di output. Può includere variabili di ambiente.
Directory intermedia | Specifica un percorso relativo della directory dei file intermedi. Può includere variabili di ambiente.
Target Name | Specifica un nome file che verrà generato dal progetto.
Estensione di destinazione | Specifica un'estensione file che verrà generata dal progetto. (Esempio: estensione exe o dll)
Estensioni da eliminare durante la pulitura | Elenco con valori delimitati da punti e virgola con supporto dei caratteri jolly che indica i file della directory intermedia da eliminare durante la pulitura o la ricompilazione.
File del log di compilazione | Specifica il file del log di compilazione in cui scrivere quando è abilitata la funzione di log di compilazione.
Set di strumenti della piattaforma | Specifica il set di strumenti usato per compilare la configurazione corrente. Se non è impostato, viene usato il set di strumenti predefinito
Tipo di configurazione | Specifica il tipo di output generato da questa configurazione. | **Libreria dinamica (so)**: libreria dinamica (so)<br>**Libreria statica (a)**: libreria statica (a)<br>**Utilità**: utilità<br>**Makefile**: makefile<br>
Livello API di destinazione | Livello dell'API di Android NDK di destinazione di questa configurazione.
Uso di STL | Specifica la libreria standard C++ da usare per questa configurazione. | **Libreria di runtime C++ minima (system)**<br>**Libreria statica di runtime C++ (gabi++_static)**<br>**Libreria condivisa di runtime C++ (gabi++_shared)**<br>**Libreria statica di runtime STLport (stlport_static)**<br>**Libreria condivisa di runtime STLport (stlport_shared)**<br>**Libreria statica STL GNU (gnustl_static)**<br>**Libreria condivisa STL GNU (gnustl_shared)**<br>**Libreria statica libc++ LLVM (c++_static)**<br>**Libreria condivisa libc++ LLVM (c++_shared)**<br>
Modalità Thumb | Generare il codice che viene eseguito per la microarchitettura thumb. Si applica solo per l'architettura ARM. | **Thumb**<br>**Arm**<br>**Disabilitato**<br>
