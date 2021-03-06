---
title: Anatomia di un pacchetto VSIX | Microsoft Docs
description: Informazioni sul contenuto di un pacchetto VSIX in Visual Studio, un file che contiene una o più estensioni di Visual Studio e un file manifesto dei metadati.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 67b3775509e330ad55a2531a9e42a7cca93c50a6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097500"
---
# <a name="anatomy-of-a-vsix-package"></a>Anatomia di un pacchetto VSIX
Un pacchetto VSIX è un file con estensione *VSIX* che contiene una o più estensioni di Visual Studio, insieme ai metadati usati da Visual Studio per classificare e installare le estensioni. I metadati sono contenuti nel manifesto VSIX e nel file *[Content_Types]. XML* . Un pacchetto VSIX può anche contenere uno o più file con *estensione vsixlangpack* per fornire il testo di installazione localizzato e può contenere pacchetti VSIX aggiuntivi per installare le dipendenze.

 Il formato del pacchetto VSIX segue lo standard OPC (Open Packaging Conventions). Il pacchetto contiene i file binari e i file di supporto, insieme a un file di *[Content_Types]. XML* e a un file manifesto con *estensione VSIX* . Un pacchetto VSIX può contenere l'output di più progetti o anche più pacchetti con manifesti propri.

> [!NOTE]
> I nomi dei file inclusi nei pacchetti VSIX non devono includere spazi, né caratteri riservati in Uniform Resource Identifier (URI), come definito in [ \[ rfc2396 \] ](https://www.rfc-editor.org/rfc/rfc2396.txt).

## <a name="the-vsix-manifest"></a>Manifesto VSIX
 Il manifesto VSIX contiene informazioni sull'estensione da installare e segue lo schema VSX. Per altre informazioni, vedere [riferimento allo schema di estensione VSIX 1,0](/previous-versions/dd393700(v=vs.110)). Per un esempio di manifesto VSIX, vedere [elemento PackageManifest (elemento radice, schema VSX)](/previous-versions/dd393754(v=vs.110)).

 Il manifesto VSIX deve essere denominato `extension.vsixmanifest` quando è incluso in un file ^. vsix *.

## <a name="the-content"></a>Il contenuto
 Un pacchetto VSIX può contenere modelli, elementi della casella degli strumenti, pacchetti VSPackage o qualsiasi altro tipo di estensione supportato da Visual Studio.

## <a name="language-packs"></a>Language Pack
 Un pacchetto VSIX può contenere una o più file con *estensione vsixlangpack* per fornire il testo localizzato durante l'installazione. Per ulteriori informazioni, vedere la pagina relativa alla [localizzazione dei pacchetti VSIX](../extensibility/localizing-vsix-packages.md).

## <a name="dependencies-and-references"></a>Dipendenze e riferimenti
 Un pacchetto VSIX può contenere altri pacchetti VSIX come riferimenti. Ognuno di questi altri pacchetti deve includere il proprio manifesto VSIX.

 Se un utente tenta di installare un'estensione con dipendenze, il programma di installazione verifica che gli assembly necessari siano installati nel sistema utente. Se gli assembly richiesti non vengono trovati, **Extensions e Updates** Visualizza un elenco degli assembly mancanti.

 Se il manifesto dell'estensione include uno o più elementi di [riferimento](/previous-versions/visualstudio/visual-studio-2010/dd393687(v=vs.100)) , le **estensioni e gli aggiornamenti** confrontano il manifesto di ogni riferimento alle estensioni installate nel sistema e installano l'estensione a cui si fa riferimento, se non è già installato. Se è installata una versione precedente di un'estensione a cui si fa riferimento, la versione più recente lo sostituisce.

 Se un progetto in una soluzione multiprogetto include un riferimento a un altro progetto nella stessa soluzione, il pacchetto VSIX include le dipendenze del progetto. È possibile eseguire l'override di questo comportamento selezionando il riferimento per il progetto interno e quindi, nella finestra **Proprietà** , impostando i **gruppi di output inclusi nella proprietà VSIX** su `BuiltProjectOutputGroup` .

 Per includere dll satellite da assembly a cui si fa riferimento nel pacchetto VSIX, aggiungere `SatelliteDllsProjectOutputGroup` ai **gruppi di output inclusi nella proprietà VSIX** .

## <a name="installation-location"></a>Percorso di installazione
 Durante l'installazione, le **estensioni e gli aggiornamenti** cercano il contenuto del pacchetto VSIX in una cartella in *%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions*.

 Per impostazione predefinita, l'installazione viene applicata solo all'utente corrente, perché *% LocalAppData%* è una directory specifica dell'utente. Tuttavia, se si imposta l'elemento [ALLUSERS](/previous-versions/ee191547(v=vs.110)) del manifesto su `True` , l'estensione verrà installata in <em>. \\ </em> VisualStudioInstallationFolder<em>\Common7\IDE\Extensions</em> e sarà disponibile per tutti gli utenti del computer.

## <a name="content_typesxml"></a>[Content_Types]. XML
 Il file *[Content_Types]. XML* identifica i tipi di file nel file con *estensione VSIX* espanso. Visual Studio usa questo file durante l'installazione del pacchetto, ma non installa il file stesso. Per ulteriori informazioni su questo file, vedere [la struttura del file [Content_Types]. XML](the-structure-of-the-content-types-dot-xml-file.md).

 Un file *[Content_Types]. XML* è richiesto dallo standard Open Packaging Conventions (OPC). Per ulteriori informazioni su OPC, vedere [OPC: un nuovo standard per](/archive/blogs/msdnmagazine/opc-a-new-standard-for-packaging-your-data) la creazione di pacchetti di dati nel sito Web MSDN.