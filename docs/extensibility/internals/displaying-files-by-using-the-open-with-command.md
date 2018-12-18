---
title: Visualizzazione di file tramite l'apertura con il comando | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project types, supporting Open With command
- Open With command
- persistence, supporting Open With command
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a1631632a2ceb66380d1d0c41e54b5a4244a31a3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="displaying-files-by-using-the-open-with-command"></a>Visualizzazione di file tramite l'apertura con il comando
Un progetto può richiedere l'IDE per visualizzare il **Apri con** la finestra di dialogo. La richiesta richiede all'utente di aprire un file con una selezione di editor standard. I passaggi seguenti descrivono il processo.  
  
1.  Le chiamate di progetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>, specificando il valore OSE_UseOpenWithDialog per il `OSEOpenDocEditor` parametro.  
  
2.  In base all'estensione di file del documento, l'IDE determina quale editor elencati, è possibile del Registro di sistema aprire il documento specificato e visualizza tali informazioni nel **Apri con** la finestra di dialogo.  
  
    > [!NOTE]
    >  I progetti che dispongono di un editor di tipo intrinseco che deve essere incluso nel **Apri con** la finestra di dialogo è necessario registrare un factory dell'editor per ogni tali editor. Solo insieme a un particolare tipo di progetto, in cui viene applicata l'implementazione delle funzioni intrinseche editor il <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metodo. L'IDE presenta una factory editor incorporato per l'editor di testo di base e l'editor binario. L'IDE crea inoltre un'istanza di una factory editor per conto di ogni associazione di file Windows registrati. Un esempio di un file di questo tipo è Microsoft Word.  
  
3.  Non appena l'utente seleziona un elemento di **Apri con** la finestra di dialogo, quindi l'IDE apre il documento chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> (metodo). Per ulteriori informazioni, vedere [procedura: aprire gli editor Standard](../../extensibility/how-to-open-standard-editors.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Visualizzazione di file utilizzando il comando Apri File](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)   
 [Procedura: Aprire gli editor standard](../../extensibility/how-to-open-standard-editors.md)