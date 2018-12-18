---
title: Opzioni utente della soluzione (. File suo) | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0b96e3ad2ec29402dddc7354df46293b99bac3ec
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="solution-user-options-suo-file"></a>Opzioni utente della soluzione (. File suo)
Il file (suo Solution) di opzioni utente della soluzione contiene le opzioni di soluzione per utente. Questo file non deve essere archiviato nel controllo del codice sorgente.  
  
 Il file (suo Solution) di opzioni utente della soluzione è un'archiviazione strutturata o composta, i file archiviati in un formato binario. Salvare le informazioni utente in flussi con il nome del flusso è la chiave che verrà utilizzata per identificare le informazioni nel file con estensione suo. Il file di opzioni utente soluzione viene utilizzato per archiviare le impostazioni delle preferenze utente e viene creato automaticamente quando Visual Studio salva una soluzione.  
  
 Quando l'ambiente si apre un file con estensione suo, enumera tutti i pacchetti VSPackage attualmente caricati. Se un pacchetto VSPackage implementa il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> interfaccia, quindi l'ambiente chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> metodo nel pacchetto VSPackage viene richiesto di caricare tutti i dati dal file con estensione suo.  
  
 È responsabilità del VSPackage sapere cosa streaming potrebbe essere scritta nel file suo. Per ogni flusso che è stato scritto, il pacchetto VSPackage chiama nuovamente all'ambiente tramite <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> per caricare un flusso specifico identificato dalla chiave, ovvero il nome del flusso. L'ambiente quindi richiama il pacchetto VSPackage per leggere tale flusso specifico passando il nome del flusso e un `IStream` puntatore per il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> metodo.  
  
 A questo punto, in cui viene effettuata un'altra chiamata a `LoadUserOptions` per verificare se esiste un'altra sezione del file con estensione suo che deve essere letta. Questo processo continua fino a quando tutti i flussi di dati nel file con estensione suo sono stati letti ed elaborati dall'ambiente di.  
  
 Quando la soluzione viene salvata o chiuso, l'ambiente chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> metodo con un puntatore al <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> metodo. Un `IStream` contenente le informazioni da salvare binarie viene passato per il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> metodo, che quindi scrive le informazioni per il file con estensione suo e chiama il `SaveUserOptions` metodo per verificare se esiste un altro flusso di informazioni da scrivere il suo file.  
  
 Questi due metodi, `SaveUserOptions` e `WriteUserOptions`, vengono chiamati in modo ricorsivo per ogni flusso di informazioni da salvare nel file con estensione suo, passando il puntatore a `IVsSolutionPersistence`. Vengono richiamate in modo ricorsivo per consentire la scrittura di più flussi per il file con estensione suo. In tal modo, le informazioni utente vengono rese persistenti con la soluzione ed sono sicuramente presente alla successiva apertura della soluzione.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 [Soluzioni](../../extensibility/internals/solutions.md)