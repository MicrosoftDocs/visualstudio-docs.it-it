---
title: Protezione nelle soluzioni a livello di documento di documenti | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- restricted permissions [Office development in Visual Studio]
- permissions [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio], restricted permissions
- documents [Office development in Visual Studio], restricted permissions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 546a74179b8bdf52541d771809426b5e4aec3e45
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="document-protection-in-document-level-solutions"></a>Sicurezza dei documenti nelle soluzioni a livello di documento
  È possibile utilizzare le funzionalità di protezione di Microsoft Office Word e Microsoft Office Excel nei progetti a livello di documento. Queste funzionalità bloccare gli utenti non autorizzati di apportare modifiche per le parti di un documento protette.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Tramite Excel, è possibile attivare la protezione e disattivare mentre la cartella di lavoro è aperto nella finestra di progettazione. Utilizzo di Word, è possibile attivare la protezione solo all'esterno di finestra di progettazione. In fase di esecuzione, è possibile abilitare o disabilitare la protezione a livello di codice per Word ed Excel.  
  
 Quando la protezione del documento è abilitato in un documento aperto nella finestra di progettazione, tutti i controlli vengono rimossi dal **della casella degli strumenti** o non sono disponibili, e non è possibile trascinare elementi dal **origini dati** finestra per il documento.  
  
## <a name="serverdocument-and-protected-documents"></a>ServerDocument e documenti protetti  
 Se un documento è protetto, la cache dei dati è impossibile accedervi da all'esterno del documento. Non è possibile utilizzare il <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe per recuperare o modificare i dati memorizzati nella cache in un documento protetto o utilizzare altri metodi del <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument> classe.  
  
## <a name="word-document-protection-in-the-designer"></a>Protezione di documenti di Word nella finestra di progettazione  
 Se si aggiunge protezione a un documento di Word o un modello mentre è aperto in Visual Studio, è possibile avviare l'applicazione la protezione nella finestra di progettazione. Il documento è in modalità di progettazione mentre è aperta in Visual Studio e deve essere in esecuzione in modalità prima di poter avviare l'applicazione di protezione.  
  
 Tuttavia, se si crea un progetto che utilizza un documento di Word esistente che è abilitata la protezione, il documento è protetto anche se aperto nella finestra di progettazione. Non è possibile modificare le parti del documento protette, ma è comunque possibile scrivere codice nell'Editor di codice per automatizzare il documento. È anche possibile compilare il progetto se la sicurezza è attivata mentre il documento è aperto in Visual Studio.  
  
 È possibile disattivare la protezione mentre il documento è aperto nella finestra di progettazione in modo che è possibile modificare il documento e compilare il progetto. È possibile disabilitare la protezione per la copia nella finestra di progettazione durante il debug; il documento che viene aperto durante il debug è una copia separata da quella aperta nella finestra di progettazione (la copia di output è archiviata nella directory \bin per Visual Basic e la directory \bin\debug per c#).  
  
 È possibile abilitare la protezione nella copia del documento aperto nella finestra di progettazione, chiudere il progetto in Visual Studio, aprire la copia del documento presente nella directory del progetto e attivare la protezione.  
  
## <a name="enforcing-word-document-protection-on-build"></a>Applicazione di protezione di documenti di Word in fase di compilazione  
 Visual Studio avvia l'applicazione di protezione per i documenti di Word e di modelli durante il processo di compilazione, in modo che la protezione è abilitata all'apertura del documento per il debug. Il documento è protetto con una password vuota.  
  
 La protezione è abilitata durante la compilazione in modo che se il codice nel documento <xref:Microsoft.Office.Tools.Word.Document.Startup> evento che potrebbe generare eccezioni o modificare il comportamento dell'applicazione, questo codice può essere sottoposto a debug in modo corretto. Se si abilita la protezione dopo l'apertura del documento, è Impossibile eseguire il debug o testato il codice di inizializzazione.  
  
## <a name="setting-the-password"></a>Impostazione della Password  
 Visual Studio vengono automaticamente abilita la protezione, ma non fornisce alcuna password per impostazione predefinita. Se si desidera la protezione del documento di una password, è necessario aggiungere prima di distribuire la soluzione. Aggiunta di una password consente agli utenti autorizzati a rimuovere la protezione dal documento. senza una password, non può essere facilmente rimuovere la protezione. Per informazioni dettagliate sull'impostazione di una password, vedere la Guida dell'applicazione di Office specifica.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: a livello di programmazione proteggere documenti e parti di documenti](../vsto/how-to-programmatically-protect-documents-and-parts-of-documents.md)   
 [Procedure dettagliate ed esempi di sviluppo office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Information Rights Management e Cenni preliminari sulle estensioni di codice gestito](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Protezione con password nei documenti di Office](../vsto/password-protection-on-office-documents.md)   
 [Procedura: consentire codice per l'esecuzione sottostante i documenti con autorizzazioni limitate](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)  
  
  