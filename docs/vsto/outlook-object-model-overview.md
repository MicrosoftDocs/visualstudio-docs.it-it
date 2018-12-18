---
title: Cenni preliminari sul modello a oggetti di Outlook | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.OutlookAddin
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], object model overview
- object models [Office development in Visual Studio], Office
- objects [Office development in Visual Studio], Office object models
- object models [Office development in Visual Studio], Outlook
- Office object models
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9dbf629961a72bc1294da4f3abea563476922716
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="outlook-object-model-overview"></a>Panoramica del modello a oggetti di Outlook
  Per sviluppare componenti aggiuntivi VSTO per Microsoft Office Outlook, è possibile interagire con gli oggetti forniti dal modello a oggetti di Outlook. Il modello a oggetti di Outlook fornisce classi e interfacce che rappresentano elementi nell'interfaccia utente. Ad esempio, l'oggetto <xref:Microsoft.Office.Interop.Outlook.Application> rappresenta l'intera applicazione, l'oggetto <xref:Microsoft.Office.Interop.Outlook.MAPIFolder> rappresenta una cartelle che contiene messaggi di posta elettronica o altri elementi e l'oggetto <xref:Microsoft.Office.Interop.Outlook.MailItem> rappresenta un messaggio di posta elettronica.  
  
 Questo argomento fornisce una breve panoramica di alcuni degli oggetti principali del modello a oggetti di Outlook. Per risorse con altre informazioni sull'intero modello a oggetti di Outlook, vedere [Uso della documentazione del modello a oggetti di Outlook](#refdoc).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 ![collegamento alla trasmissione video](../vsto/media/playvideo.gif "collegamento alla trasmissione video") per una dimostrazione video correlata, vedere [procedura ricerca per categorie: usare Outlook per creare un Report di attività personalizzato?](http://go.microsoft.com/fwlink/?LinkID=130315).  
  
## <a name="accessing-objects-in-an-outlook-project"></a>Accesso agli oggetti in un progetto di Outlook  
 Outlook offre numerosi oggetti con cui è possibile interagire. Per usare in modo efficace il modello a oggetti, è necessaria una familiarità con gli oggetti principali seguenti:  
  
-   <xref:Microsoft.Office.Interop.Outlook.Application>  
  
-   <xref:Microsoft.Office.Interop.Outlook.Explorer>  
  
-   <xref:Microsoft.Office.Interop.Outlook.Inspector>  
  
-   <xref:Microsoft.Office.Interop.Outlook.MAPIFolder>  
  
-   <xref:Microsoft.Office.Interop.Outlook.MailItem>  
  
-   <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>  
  
-   <xref:Microsoft.Office.Interop.Outlook.TaskItem>  
  
-   <xref:Microsoft.Office.Interop.Outlook.ContactItem>  
  
### <a name="application-object"></a>Oggetto Application  
 L'oggetto <xref:Microsoft.Office.Interop.Outlook.Application> rappresenta l'applicazione Outlook ed è l'oggetto di livello massimo nel modello a oggetti di Outlook. Alcuni dei membri più importanti di questo oggetto includono i seguenti:  
  
-   Il metodo [CreateItem](http://msdn.microsoft.com/en-us/771707fb-5f34-473d-9fdf-09a6a7f55ece) , che può essere usato per creare un nuovo elemento, ad esempio un messaggio di posta elettronica, un'attività o un appuntamento.  
  
-   La proprietà <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A> , che permette di accedere alle finestre che mostrano i contenuti di una cartella nell'interfaccia utente di Outlook.  
  
-   La proprietà <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A> , che permette di accedere alle finestre che mostrano i contenuti di un singolo elemento, ad esempio un messaggio di posta elettronica o una convocazione riunione.  
  
 Per ottenere un'istanza del <xref:Microsoft.Office.Interop.Outlook.Application> oggetto, utilizzare il campo di applicazione della `ThisAddIn` classe nel progetto. Per altre informazioni, vedere [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
> [!NOTE]  
>  Per evitare avvisi di sicurezza quando si utilizzano le proprietà e metodi bloccati dalla protezione del modello a oggetti di Outlook, ottenere gli oggetti di Outlook dal campo di applicazione di `ThisAddIn` classe. Per altre informazioni, vedere [Specific Security Considerations for Office Solutions](../vsto/specific-security-considerations-for-office-solutions.md).  
  
### <a name="explorer-object"></a>Oggetto Explorer  
 L'oggetto <xref:Microsoft.Office.Interop.Outlook.Explorer> rappresenta una finestra che mostra i contenuti di una cartella che include elementi quali messaggi di posta elettronica, attività o appuntamenti. L'oggetto <xref:Microsoft.Office.Interop.Outlook.Explorer> include metodi e proprietà che possono essere usati per modificare la finestra ed eventi che vengono generati quando la finestra viene modificata.  
  
 Per ottenere un oggetto <xref:Microsoft.Office.Interop.Outlook.Explorer> , eseguire una delle operazioni seguenti:  
  
-   Usare la proprietà <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A> dell'oggetto <xref:Microsoft.Office.Interop.Outlook.Application> per accedere a tutti gli oggetti <xref:Microsoft.Office.Interop.Outlook.Explorer> in Outlook.  
  
-   Usare il metodo <xref:Microsoft.Office.Interop.Outlook._Application.ActiveExplorer%2A> dell'oggetto <xref:Microsoft.Office.Interop.Outlook.Application> per ottenere l'oggetto <xref:Microsoft.Office.Interop.Outlook.Explorer> che ha attualmente lo stato attivo.  
  
-   Utilizzare il metodo GetExplorer del <xref:Microsoft.Office.Interop.Outlook.MAPIFolder> oggetto per cui ottenere il <xref:Microsoft.Office.Interop.Outlook.Explorer> per la cartella corrente.  
  
### <a name="inspector-object"></a>Oggetto Inspector  
 L'oggetto <xref:Microsoft.Office.Interop.Outlook.Inspector> rappresenta una finestra che mostra un singolo elemento, ad esempio un messaggio di posta elettronica, un'attività o un appuntamento. L'oggetto <xref:Microsoft.Office.Interop.Outlook.Inspector> include metodi e proprietà che possono essere usati per modificare la finestra ed eventi che vengono generati quando la finestra viene modificata.  
  
 Per ottenere un oggetto <xref:Microsoft.Office.Interop.Outlook.Inspector> , eseguire una delle operazioni seguenti:  
  
-   Usare la proprietà <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A> dell'oggetto <xref:Microsoft.Office.Interop.Outlook.Application> per accedere a tutti gli oggetti <xref:Microsoft.Office.Interop.Outlook.Inspector> in Outlook.  
  
-   Usare il metodo <xref:Microsoft.Office.Interop.Outlook._Application.ActiveInspector%2A> dell'oggetto <xref:Microsoft.Office.Interop.Outlook.Application> per ottenere l'oggetto <xref:Microsoft.Office.Interop.Outlook.Inspector> che ha attualmente lo stato attivo.  
  
-   Utilizzare il metodo GetInspector di un elemento specifico, ad esempio un <xref:Microsoft.Office.Interop.Outlook.MailItem> o <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>per recuperare l'oggetto Inspector associato.  
  
### <a name="mapifolder-object"></a>Oggetto MAPIFolder  
 L'oggetto <xref:Microsoft.Office.Interop.Outlook.MAPIFolder> rappresenta una cartella che contiene messaggi di posta elettronica, contatti, attività e altri elementi. Outlook offre 16 oggetti <xref:Microsoft.Office.Interop.Outlook.MAPIFolder> predefiniti.  
  
 Gli oggetti <xref:Microsoft.Office.Interop.Outlook.MAPIFolder> predefiniti vengono definiti dai valori di enumerazione <xref:Microsoft.Office.Interop.Outlook.OlDefaultFolders> . Ad esempio,  
  
 OlDefaultFolders. olFolderInbox corrisponde alla **posta in arrivo** cartelle in Outlook.  
  
 Per un esempio che illustra come accedere a un valore predefinito <xref:Microsoft.Office.Interop.Outlook.MAPIFolder> e creare un nuovo <xref:Microsoft.Office.Interop.Outlook.MAPIFolder>, vedere [come: a livello di programmazione creare cartelle personalizzate](../vsto/how-to-programmatically-create-custom-folder-items.md).  
  
### <a name="mailitem-object"></a>Oggetto MailItem  
 L'oggetto <xref:Microsoft.Office.Interop.Outlook.MailItem> rappresenta un messaggio di posta elettronica. Gli oggetti<xref:Microsoft.Office.Interop.Outlook.MailItem> si trovano in genere nelle cartelle, ad esempio **Posta in arrivo**, **Posta inviata**e **Posta in uscita**. <xref:Microsoft.Office.Interop.Outlook.MailItem> espone proprietà e metodi che possono essere usati per creare e inviare messaggi di posta elettronica.  
  
 Per un esempio che illustra come creare un messaggio di posta elettronica, vedere [procedura: creare a livello di programmazione un elemento di posta elettronica](../vsto/how-to-programmatically-create-an-e-mail-item.md).  
  
### <a name="appointmentitem-object"></a>Oggetto AppointmentItem  
 L'oggetto <xref:Microsoft.Office.Interop.Outlook.AppointmentItem> rappresenta una riunione, un appuntamento singolo o un appuntamento o riunione ricorrente nella cartella **Calendario** . L'oggetto <xref:Microsoft.Office.Interop.Outlook.AppointmentItem> include metodi che eseguono azioni, quali la risposta o l'inoltro di una convocazione riunione, e proprietà che specificano i dettagli della riunione, ad esempio luogo e ora.  
  
 Per un esempio che illustra come creare un appuntamento, vedere [procedura: creare una convocazione riunione](../vsto/how-to-programmatically-create-a-meeting-request.md).  
  
### <a name="taskitem-object"></a>Oggetto TaskItem  
 L'oggetto <xref:Microsoft.Office.Interop.Outlook.TaskItem> rappresenta un'attività da eseguire entro un intervallo di tempo specificato. Gli oggetti<xref:Microsoft.Office.Interop.Outlook.TaskItem> si trovano nella cartella **Attività** .  
  
 Per creare un'attività, usare il metodo [CreateItem](http://msdn.microsoft.com/en-us/771707fb-5f34-473d-9fdf-09a6a7f55ece) dell'ogetto <xref:Microsoft.Office.Interop.Outlook.Application> e passare il valore <xref:Microsoft.Office.Interop.Outlook.OlItemType.olTaskItem> per il parametro.  
  
### <a name="contactitem-object"></a>Oggetto ContactItem  
 L'oggetto <xref:Microsoft.Office.Interop.Outlook.ContactItem>rappresenta un contatto nella cartella **Contatti** . Gli oggetti<xref:Microsoft.Office.Interop.Outlook.ContactItem> contengono diverse informazioni di contatto per le persone rappresentate, ad esempio via e numero civico, indirizzo di posta elettronica e numeri di telefono.  
  
 Per un esempio che illustra come creare un nuovo contatto, vedere [procedura: aggiungere una voce ai contatti di Outlook](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md). Per un esempio che illustra come cercare un contatto esistente, vedere [come: a livello di programmazione cercare un contatto specifico](../vsto/how-to-programmatically-search-for-a-specific-contact.md).  
  
##  <a name="refdoc"></a> Uso della documentazione del modello a oggetti di Outlook  
 Per informazioni complete sul modello a oggetti di Outlook, è possibile usare il riferimento di assembly di interoperabilità primario di Outlook e il riferimento del modello a oggetti VBA.  
  
### <a name="primary-interop-assembly-reference"></a>Riferimento dell'assembly di interoperabilità primario  
 Il riferimento degli assembly di interoperabilità primari di Outlook documenta i tipi disponibili negli assembly di interoperabilità primari per Outlook 2010. Per altre informazioni, vedere la [guida di riferimento per gli assembly di interoperabilità primari di Outlook 2010](http://go.microsoft.com/fwlink/?LinkId=189580).  
  
 Oltre a fornire informazioni per tutti i tipi disponibili negli assembly di interoperabilità primari, questa documentazione fornisce anche informazioni aggiuntive sulla struttura degli assembly di interoperabilità primari ed esempi di codice per attività di automazione comuni di Outlook.  
  
### <a name="vba-object-model-reference"></a>Riferimento del modello a oggetti VBA  
 Nel riferimento del modello a oggetti VBA è illustrato il modello a oggetti di Outlook esposto al codice Visual Basic Applications (VBA). Per altre informazioni, vedere [Riferimento del modello a oggetti di Outlook 2010](http://go.microsoft.com/fwlink/?LinkId=199769).  
  
 Tutti gli oggetti e i membri del riferimento del modello a oggetti VBA corrispondono ai tipi e ai membri dell'assembly di interoperabilità primario di Outlook. Ad esempio, l'oggetto Inspector nel riferimento del modello a oggetti VBA corrisponde al <xref:Microsoft.Office.Interop.Outlook.Inspector> oggetto nell'assembly di interoperabilità primario di Outlook. Sebbene il riferimento del modello a oggetti di VBA fornisca esempi di codice per la maggior parte delle proprietà, dei metodi e degli eventi, è necessario convertire il codice VBA in questo riferimento a Visual Basic o a Visual C# se si vuole usarli in un progetto di componente aggiuntivo VSTO di Outlook creato con Visual Studio.  
  
### <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Uso dei contatti](../vsto/working-with-contact-items.md)|Fornisce argomenti che illustrano come eseguire attività con i contatti.|  
|[Uso degli elementi di posta](../vsto/working-with-mail-items.md)|Fornisce argomenti che illustrano come eseguire attività con gli elementi di posta elettronica.|  
|[Uso delle cartelle](../vsto/working-with-folders.md)|Fornisce argomenti che illustrano come eseguire attività con le cartelle.|  
|[Uso degli elementi di calendario](../vsto/working-with-calendar-items.md)|Fornisce argomenti che illustrano come eseguire attività con gli elementi di calendario.|  
|[Procedura: Determinare l'elemento corrente di Outlook a livello di codice](../vsto/how-to-programmatically-determine-the-current-outlook-item.md)|Illustra come visualizzare il nome della cartella corrente e alcune informazioni sull'elemento selezionato.|  
  