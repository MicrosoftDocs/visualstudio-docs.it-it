---
title: Anatomia di un pacchetto VSIX | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e728fbe2a9e430224a3da822cbcae45745eeb29e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="anatomy-of-a-vsix-package"></a>Anatomia di un pacchetto VSIX
Un pacchetto VSIX è un file con estensione VSIX che contiene uno o più estensioni di Visual Studio, insieme a Visual Studio Usa per classificare e installare le estensioni dei metadati. I metadati contenuti nel manifesto VSIX e il file [Content_Types] XML. Un pacchetto VSIX può anche contenere uno o più file vsixlangpack per fornire il testo di programma di installazione localizzato e può contenere pacchetti VSIX aggiuntivi per installare le dipendenze.  
  
 Formato di pacchetto VSIX conforme allo standard Open Packaging Conventions (OPC). Il pacchetto contiene i file binari e i file di supporto, insieme a un file [Content_Types] XML e un'estensione VSIX file manifesto. Un pacchetto VSIX può contenere l'output di più progetti, o anche più pacchetti che contengono i propri manifesti.  
  
> [!NOTE]
>  I nomi dei file inclusi nei pacchetti VSIX non devono includere spazi, né caratteri riservati in identificatori URI (Uniform Resource), come definito in [ \[RFC2396\]](http://go.microsoft.com/fwlink/?LinkId=90339).  
  
## <a name="the-vsix-manifest"></a>Il manifesto VSIX  
 Il manifesto VSIX contiene informazioni sull'installazione di estensione e segue lo Schema VSX. Per ulteriori informazioni, vedere [riferimento 1.0 dello Schema di estensione VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b). Per un esempio di manifesto VSIX, vedere [elemento PackageManifest (elemento radice, Schema VSX)](http://msdn.microsoft.com/en-us/f8ae42ba-775a-4d2b-976a-f556e147f187).  
  
 Il manifesto VSIX deve essere denominato `extension.vsixmanifest` quando è incluso in un file con estensione VSIX.  
  
## <a name="the-content"></a>Il contenuto  
 Modelli, gli elementi della casella degli strumenti, i pacchetti VSPackage o qualsiasi altro tipo di estensione supportata da Visual Studio, può contenere un pacchetto VSIX.  
  
## <a name="language-packs"></a>Language Pack  
 Un pacchetto VSIX può contenere uno o più file vsixlangpack per fornire il testo localizzato durante l'installazione. Per ulteriori informazioni, vedere [localizzazione pacchetti VSIX](../extensibility/localizing-vsix-packages.md).  
  
## <a name="dependencies-and-references"></a>Dipendenze e riferimenti  
 Un pacchetto VSIX può contenere altri pacchetti VSIX come riferimenti. Ognuno di questi altri pacchetti deve includere un manifesto VSIX proprio.  
  
 Se un utente tenta di installare un'estensione con dipendenze, il programma di installazione verifica che gli assembly necessari siano installati nel sistema dell'utente. Se non sono possibile trovare gli assembly necessari **estensioni e aggiornamenti** Visualizza un elenco di assembly mancanti.  
  
 Se il manifesto dell'estensione include uno o più [riferimento](http://msdn.microsoft.com/en-us/32c52934-e81e-4b53-8cb6-4df45ef7bfa8) elementi **estensioni e aggiornamenti** confronta il manifesto di ogni riferimento a estensioni installate nel sistema e installa il estensione di riferimento, se non è già installato. Se è installata una versione precedente di un'estensione di cui viene fatto riferimento, la versione più recente lo sostituisce.  
  
 Se un progetto in una soluzione multiprogetto include un riferimento a un altro progetto nella stessa soluzione, il pacchetto VSIX include le dipendenze del progetto. È possibile eseguire l'override di questo comportamento facendo clic sul riferimento per il progetto interno, quindi il **proprietà** finestra, l'impostazione di **Output gruppi inclusi in VSIX** proprietà `BuiltProjectOutputGroup`.  
  
 Per includere le DLL satellite da assembly di riferimento nel pacchetto VSIX, aggiungere `SatelliteDllsProjectOutputGroup` per il **Output gruppi inclusi in VSIX** proprietà.  
  
## <a name="installation-location"></a>Percorso di installazione  
 Durante l'installazione, **estensioni e aggiornamenti** Cerca il contenuto del pacchetto VSIX in una cartella in % LocalAppData%\Microsoft\VisualStudio\14.0\Extensions.  
  
 Per impostazione predefinita, l'installazione si applica solo all'utente corrente, in quanto % LocalAppData % è una directory specifiche dell'utente. Tuttavia, se si imposta la [AllUsers](http://msdn.microsoft.com/en-us/ac817f50-3276-4ddb-b467-8bbb1432455b) elemento del manifesto per `True`, verrà installata l'estensione in... \\ *VisualStudioInstallationFolder*\Common7\IDE\Extensions e sarà disponibile a tutti gli utenti del computer.  
  
## <a name="contenttypesxml"></a>[Content_Types] XML  
 Il file [Content_Types] XML identifica i tipi di file nel file. VSIX espanso. Visual Studio utilizza questo file durante l'installazione del pacchetto, ma non viene installato il file stesso. Per ulteriori informazioni su questo file, vedere [della struttura del File [Content_types]. XML](the-structure-of-the-content-types-dot-xml-file.md).  
  
 Un file [Content_Types] XML è necessario per la standard Open Packaging Conventions (OPC). Per ulteriori informazioni su OPC, vedere [OPC: un nuovo Standard per la creazione di pacchetti di dati](http://go.microsoft.com/fwlink/?LinkID=148207) nel sito Web MSDN.