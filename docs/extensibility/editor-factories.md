---
title: Factory editor | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - editor factories
ms.assetid: cf4e8164-3546-441d-b465-e8a836ae7216
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 676918b6366837b6ee77cf27bd5fba9fbf608729
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="editor-factories"></a>Factory editor
Una factory editor crea gli oggetti di editor e li inserisce in una cornice di finestra, nota come una visualizzazione fisica. Crea i dati del documento e oggetti di visualizzazione di documenti che sono necessari per creare gli editor e finestre di progettazione. Per creare qualsiasi editor standard e l'editor di componenti di base di Visual Studio, è necessario un factory dell'editor. Facoltativamente è possibile creare un editor personalizzato con una factory dell'editor.  
  
 Si crea una factory editor implementando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfaccia. Nell'esempio seguente viene illustrato come implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> per creare una factory dell'editor:  
  
 [!code-vb[VSSDKEditorFactories#1](../extensibility/codesnippet/VisualBasic/editor-factories_1.vb)]
 [!code-csharp[VSSDKEditorFactories#1](../extensibility/codesnippet/CSharp/editor-factories_1.cs)]  
  
 Un editor viene caricato la prima volta che si apre un tipo di file gestito da tale editor. È possibile scegliere di aprire un editor specifico o l'editor predefinito. Se si seleziona l'editor predefinito, l'ambiente di sviluppo integrato (IDE) determina l'editor corretto per aprire e quindi lo apre. Per ulteriori informazioni, vedere [determinare quale Editor apre un File in un progetto](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="registering-editor-factories"></a>Registrare la factory Editor  
 Prima di poter utilizzare un editor che è stato creato, è innanzitutto necessario registrare le informazioni, incluse le estensioni di file che è possibile gestire.  
  
 Se il pacchetto VSPackage è scritto in codice gestito, è possibile utilizzare il metodo Framework di pacchetto gestito (MPF) <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> per registrare la factory editor dopo aver caricato il pacchetto VSPackage. Se il pacchetto VSPackage è scritto in codice non gestito, quindi è necessario registrare la factory editor utilizzando il <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors> servizio.  
  
### <a name="registering-an-editor-factory-by-using-managed-code"></a>La registrazione usando un Factory dell'Editor di codice gestito  
 È necessario registrare la factory editor il pacchetto VSPackage di `Initialize` metodo. Prima di chiamare `base.Initialize`e quindi chiamare <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> per ogni factory editor  
  
 Nel codice gestito, è necessario annullare la registrazione di un factory dell'editor, perché il pacchetto VSPackage verrà gestito automaticamente. Inoltre, se la factory dell'editor implementa <xref:System.IDisposable>, viene eliminato automaticamente quando è annullata la registrazione.  
  
### <a name="registering-an-editor-factory-by-using-unmanaged-code"></a>Registra una factory editor tramite codice non gestito  
 Nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implementazione per il pacchetto di editor, usare il `QueryService` metodo da chiamare `SVsRegisterEditors`. Questa operazione restituisce un puntatore a <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors>. Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> metodo passando l'implementazione del <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfaccia. È necessario mplementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> in una classe separata.  
  
## <a name="the-editor-factory-registration-process"></a>Il processo di registrazione Factory Editor  
 Il processo seguente si verifica quando l'editor utilizzando la factory dell'editor di caricamento di Visual Studio:  
  
1.  Il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] chiamate di sistema di progetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>.  
  
2.  Questo metodo restituisce la factory editor. Ritardi di Visual Studio durante il caricamento del pacchetto dell'editor, tuttavia, fino a quando l'editor effettivamente necessaria per un sistema di progetto.  
  
3.  Quando l'editor è un sistema di progetto, Visual Studio chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>, un metodo specializzato che restituisce la visualizzazione del documento e il documento, gli oggetti dati.  
  
4.  Se viene chiamato da Visual Studio per il factory editor utilizzando <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> restituire un oggetto dati del documento e un oggetto visualizzazione del documento, Visual Studio crea una finestra del documento, inserisce l'oggetto visualizzazione del documento in essa contenuti, quindi crea una voce nel documento in esecuzione tabella (RDT) per l'oggetto dati del documento.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>   
 [Tabella documenti in esecuzione](../extensibility/internals/running-document-table.md)