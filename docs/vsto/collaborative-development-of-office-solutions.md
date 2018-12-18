---
title: Sviluppo collaborativo di soluzioni Office | Documenti Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], collaborative development
- Office development in Visual Studio, collaboration
- source control [Office development in Visual Studio]
- collaborative development [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 3b69eccc3f6c140c44bff3b2d3d24e33914cae84
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="collaborative-development-of-office-solutions"></a>Sviluppo collaborativo di soluzioni Office
  Più sviluppatori possono lavorare su un progetto di Office nello stesso modo in cui collaborano in altri progetti di Visual Studio. Visual Studio rileva correttamente l'installazione di Microsoft Office in ogni computer, anche se Office è installata in posizioni diverse. Tuttavia, esistono alcune importanti considerazioni da tenere presenti.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="debug-properties-are-not-shared"></a>Eseguire il debug delle proprietà non vengono condivise  
 Le proprietà del debug non sono condivise tra più utenti sotto il controllo del codice sorgente. Progetti Visual Basic e Visual c# archiviano le proprietà di debug in un file specifico dell'utente (*ProjectName*. vbproj o *ProjectName*. csproj), e questo file è incluso nel controllo del codice sorgente. Se più di una persona sta eseguendo il debug, è necessario che ciascuna immetta manualmente le proprietà di debug.  
  
 Se il progetto si trova in una condivisione di rete anziché nel controllo del codice sorgente, è necessario eseguire alcuni passaggi aggiuntivi per consentire agli sviluppatori di aprire la soluzione e assembly di test.  
  
## <a name="source-control-requires-checking-out-all-files"></a>Richiede l'estrazione di tutti i file di controllo del codice sorgente  
 Se si utilizza controllo del codice sorgente per i progetti, è necessario estrarre tutti i file in un file di codice in **Esplora** (ad esempio i file di codice ThisAddIn, ThisWorkbook o ThisDocument) ogni volta che si modifica il file di codice, anche il file che sono nascosti per impostazione predefinita. Se si estrae solo il file di codice di primo livello, le modifiche potrebbero andare perse.  
  
 Dopo aver apportato le modifiche, archiviare che tutti i file nuovamente. Per ulteriori informazioni sui file di codice nascosto nei progetti, vedere [progetti di Office in ambiente Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## <a name="security-for-informal-collaboration-on-a-network"></a>Sicurezza per la collaborazione informale in una rete  
 Per tutte le soluzioni a livello di documento in un percorso di rete (ad esempio \\ \\ *Servername*\\*Sharename*), il percorso completo deve essere aggiunto a elenco delle cartelle attendibili nell'applicazione Microsoft Office che sta utilizzando. Selezionare l'opzione per includere le sottodirectory nella cartella principale, o, in particolare, aggiungere debug e compilare cartelle all'elenco delle cartelle attendibili. Per ulteriori informazioni su come eseguire questa operazione, vedere [concessione dell'attendibilità ai documenti](../vsto/granting-trust-to-documents.md).  
  
 I certificati temporanei che vengono generati automaticamente in fase di compilazione non sono protetti da password. I certificati contengono il nome di account di accesso dello sviluppatore e altre informazioni personali. Se si distribuiscono le personalizzazioni firmate da certificati temporanei, altre potrebbe essere in grado di accedere a queste informazioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza delle soluzioni Office](../vsto/securing-office-solutions.md)   
 [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)   
 [Compilazione di soluzioni Office](../vsto/building-office-solutions.md)  
  
  