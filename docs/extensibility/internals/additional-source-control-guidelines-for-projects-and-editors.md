---
title: Linee guida sul controllo del codice sorgente per progetti ed editor
description: Informazioni sulle linee guida che i progetti e gli editor devono rispettare per supportare il controllo del codice sorgente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], guidelines for projects and editors
ms.assetid: 2483cce5-321c-4d3c-9c5c-ee8385263f74
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2509f2f6f9da91c3df60d6b041d5ebb6bdd367b6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079007"
---
# <a name="additional-source-control-guidelines-for-projects-and-editors"></a>Linee guida aggiuntive sul controllo del codice sorgente per progetti ed editor
Esistono diverse linee guida che i progetti e gli editor devono rispettare per supportare il controllo del codice sorgente.

## <a name="guidelines"></a>Indicazioni
 Il progetto o l'editor deve anche eseguire le operazioni seguenti per supportare il controllo del codice sorgente:

|Area|Project|Editor|Dettagli|
|----------|-------------|------------|-------------|
|Copie private dei file|X||L'ambiente supporta copie private dei file. Ovvero ogni persona integrata nel progetto ha una propria copia privata dei file presenti in tale progetto.|
|Persistenza ANSI/Unicode|X|X|Se si scrive il codice di persistenza, salvare in modo permanente i file nel modulo ANSI perché la maggior parte dei programmi di controllo del codice sorgente non supporta attualmente Unicode.|
|Enumera file|X||Il progetto deve contenere un elenco specifico di tutti i file al suo interno e deve essere in grado di enumerare l'elenco di file utilizzando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (VSH_PROPID_First_Child/Next_Sibling). Il progetto deve inoltre esporre i nomi degli elementi tramite la relativa <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A> implementazione e supportare la ricerca del nome (inclusi i file speciali) tramite la relativa <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> implementazione.|
|Formato testo|X|X|Quando possibile, i file devono essere in formato testo per supportare l'Unione di versioni diverse. I file non in formato testo non possono essere Uniti con altre versioni del file in un secondo momento. Il formato di testo preferito è XML.|
|Basato su riferimenti|X||I progetti basati su riferimenti sono prontamente supportati nel controllo del codice sorgente. Tuttavia, i progetti basati su directory sono supportati anche dal controllo del codice sorgente purché il progetto possa produrre un elenco di file su richiesta, indipendentemente dal fatto che tali file esistano sul disco. Quando si apre un progetto dal controllo del codice sorgente, il file di progetto viene disattivato prima di uno dei relativi file.|
|Mantieni oggetti e proprietà in ordine stimabile|X|X|Rendere permanente i file in un ordine prevedibile, ad esempio ordine alfabetico, per facilitare l'Unione.|
|Ricarica|X|X|Quando un file viene modificato sul disco, l'editor deve essere in grado di ricaricarlo. Quando si partecipa al controllo del codice sorgente, l'ambiente consente di ricaricare i dati chiamando l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> implementazione. Il caso di ricaricamento più difficile è quando si verifica un'estrazione quando si chiama IVsQueryEditQuerySave:: <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> e si stanno elaborando informazioni. Tuttavia, il codice di ricaricamento deve essere in grado di essere eseguito in questa situazione.<br /><br /> L'ambiente ricarica automaticamente i file di progetto. Tuttavia, un progetto deve implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> se presenta Gerarchie annidate per supportare il ricaricamento dei file di progetto annidati.|

## <a name="see-also"></a>Vedi anche
- [Supporto del controllo del codice sorgente](../../extensibility/internals/supporting-source-control.md)
