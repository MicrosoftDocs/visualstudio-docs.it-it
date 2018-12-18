---
title: Casella degli strumenti, Scheda Componenti | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Toolbox, Components tab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 29fd00d6fdf6f973149f57a78eb1145274689a2b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="toolbox-components-tab"></a>Casella degli strumenti, Scheda Componenti

Visualizza i componenti che è possibile aggiungere alle finestre di progettazione di Visual Basic e C#. Oltre ai componenti .NET Framework inclusi in Visual Studio, ad esempio i componenti <xref:System.Messaging.MessageQueue> e <xref:System.Diagnostics.EventLog>, in questa scheda è possibile aggiungere componenti personalizzati o di terze parti.
  
 Per visualizzare questa scheda, scegliere **Casella degli strumenti** dal menu **Visualizza**. Nella **Casella degli strumenti** selezionare la scheda **Componenti**.  
  
 **BackgroundWorker**  
 Crea un'istanza del componente `System.ComponentModel.BackgroundWorker` che può eseguire un'operazione su un thread separato dedicato.  
  
 **DirectoryEntry**  
 Crea un'istanza del componente <xref:System.DirectoryServices.DirectoryEntry> che incapsula un nodo o un oggetto nella gerarchia di Active Directory e può essere usata per interagire con i provider del servizio Active Directory.  
  
 **DirectorySearcher**  
 Crea un'istanza del componente <xref:System.DirectoryServices.DirectorySearcher> che è possibile usare per eseguire query in Active Directory.  
  
 **ErrorProvider**  
 Crea un'istanza del componente `System.Windows.Forms.ErrorProvider` che indica all'utente finale che a un controllo in un form è associato un errore.  
  
 **EventLog**  
 Crea un'istanza del componente <xref:System.Diagnostics.EventLog> che consente di interagire con i log di sistema e i log eventi personalizzati, ad esempio scrivendo eventi e leggendo dati.
  
 **FileSystemWatcher**  
 Crea un'istanza del componente <xref:System.IO.FileSystemWatcher> che consente di monitorare le modifiche apportate a una directory o a un file a cui si ha accesso.
  
 **HelpProvider**  
 Crea un'istanza del componente `System.Windows.Forms.HelpProvider` che offre informazioni della Guida, anche in finestre popup.  
  
 **ImageList**  
 Crea un'istanza del componente `System.Windows.Forms.ImageList` che rende disponibili metodi per la gestione di una raccolta di oggetti `System.Drawing.Image`.  
  
 **MessageQueue**  
 Crea un'istanza del componente <xref:System.Messaging.MessageQueue> che consente di interagire con le code di messaggi, leggendo e scrivendo messaggi nelle code, elaborando transazioni ed eseguendo attività di amministrazione delle code.

 **PerformanceCounter**  
 Crea un'istanza del componente <xref:System.Diagnostics.PerformanceCounter> che consente di interagire con i contatori delle prestazioni di Windows, creando nuove categorie e istanze, leggendo valori dai contatori ed eseguendo calcoli sui dati dei contatori stessi.
  
 **Processo**  
 Crea un'istanza del componente <xref:System.Diagnostics.Process> che consente di arrestare e avviare i processi del sistema, nonché di manipolare i dati associati a questi.
  
 **SerialPort**  
 Crea un'istanza del componente `System.IO.Ports.SerialPort` che rende disponibili le funzioni di I/O sincrono e basato su eventi, l'accesso agli stati di blocco e interruzione, l'accesso alle proprietà del driver seriale.  
  
 **ServiceController**  
 Crea un'istanza del componente <xref:System.ServiceProcess.ServiceController> che consente di manipolare i servizi esistenti, avviandoli e arrestandoli e inviando loro dei comandi.
  
 **Timer**  
 Crea un'istanza del componente <xref:System.Windows.Forms.Timer> che consente di aggiungere funzionalità basate sull'ora alle applicazioni basate su Windows. Per altre informazioni, vedere [Componente Timer](/dotnet/framework/winforms/controls/timer-component-windows-forms).  
  
> [!NOTE]
>  È disponibile anche un componente <xref:System.Timers.Timer> basato su sistema che è possibile aggiungere alla **Casella degli strumenti**. Il componente <xref:System.Timers.Timer> è ottimizzato per le applicazioni server mentre il componente <xref:System.Windows.Forms.Timer> di Windows Forms è più adatto all'uso con Windows Forms.  
  
## <a name="see-also"></a>Vedere anche

[Programmazione con i componenti](http://msdn.microsoft.com/Library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)  
[Procedure dettagliate sulla programmazione dei componenti](http://msdn.microsoft.com/Library/373cacf7-479e-4b05-991c-5cb18824e913)  
[Casella degli strumenti](../../ide/reference/toolbox.md)