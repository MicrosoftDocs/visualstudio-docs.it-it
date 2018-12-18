---
title: Creazione di controlli utente riutilizzabili per Web part o pagine applicazione | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- user controls [SharePoint development in Visual Studio], creating
- SharePoint development in Visual Studio, user controls
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e76a13174a9ac980644f8f9116c6518fc853028c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="creating-reusable-controls-for-web-parts-or-application-pages"></a>Creazione di controlli utente riutilizzabili per web part o pagine applicazione
  In Visual Studio è possibile creare controlli riutilizzabili personalizzati che possono essere utilizzati dalle pagine applicazione e dalle Web part eseguite in SharePoint. Questi controlli sono denominati controlli utente. Un controllo utente è un tipo di controllo composito che funziona come una pagina Web ASP.NET, è possibile aggiungere controlli server Web esistenti e il markup per un controllo utente e definire proprietà e metodi per il controllo. È quindi possibile incorporarli nelle pagine Web ASP.NET, in cui operano come un'unità.  
  
## <a name="creating-a-user-control"></a>Creazione di un controllo utente  
 Per creare un controllo utente, aggiungere un **controllo utente** per un **progetto SharePoint vuoto**. Per ulteriori informazioni, vedere [procedura: creare un controllo utente per una Web Part o una pagina dell'applicazione SharePoint](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md).  
  
 Quando si aggiunge un **controllo utente** item, Visual Studio crea una cartella nel progetto e quindi vengono aggiunti alcuni file nella cartella. La tabella seguente descrive ciascun file.  
  
|File|Descrizione|  
|----------|-----------------|  
|File di controllo utente|Definisce il controllo utente. Progettazione del controllo utente mediante l'aggiunta di controlli e codice per questo file.|  
|File di codice|Contiene il codice dietro il controllo utente. Aggiungere il codice per gestire gli eventi per questo file.|  
|File di codice della finestra di progettazione|Contiene il codice generato dalla finestra di progettazione e non deve essere modificato direttamente.|  
  
## <a name="designing-the-user-control"></a>Progettazione del controllo utente  
 Progettazione del controllo utente utilizzando la finestra di progettazione di Visual Web Developer in Visual Studio. Questa finestra di progettazione viene visualizzata quando si apre il file di controllo utente nel progetto e scegliere il **progettazione** scheda.  

## <a name="consuming-the-user-control"></a>Utilizzo del controllo utente  
 Controlli utente non vengono visualizzati in SharePoint fino a quando non vengono incluse in una pagina dell'applicazione o una Web Part.  
  
 Per includere un controllo utente in una pagina applicazione, aprire la pagina Web a cui si desidera aggiungere il controllo utente ASP.NET. Passare alla visualizzazione progettazione, quindi selezionare il file di controllo utente personalizzato in Esplora soluzioni e trascinarlo nella pagina. Il controllo utente ASP.NET viene aggiunto alla pagina e la finestra di progettazione crea la direttiva @ Register, che è necessaria per la pagina di riconoscere il controllo utente. È ora possibile lavorare con le proprietà pubbliche e i metodi del controllo.  
  
 Per includere un controllo utente in una Web Part, aggiungere il controllo utente per la Web Part <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> insieme nel file di codice della Web Part. Nell'esempio seguente viene aggiunto un controllo utente per il <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> raccolta di una Web Part.  
  
 [!code-vb[SP_VisualWebPart#5](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1.vb#5)]
 [!code-csharp[SP_VisualWebPart#5](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1.cs#5)]  
  
## <a name="debugging-a-user-control"></a>Debug di un controllo utente  
 Per eseguire il debug di un controllo utente, verificare che il controllo utente è incluso in una pagina dell'applicazione o Web Part nel progetto SharePoint. È quindi possibile eseguire il debug codice nel controllo utente esattamente come si trattasse del debug di codice in qualsiasi progetto di Visual Studio.  
  
 Quando si avvia il debugger di Visual Studio, Visual Studio apre il sito di SharePoint.  
  
 In SharePoint aprire la pagina dell'applicazione che include il controllo utente. Se il controllo utente è incluso in una Web Part, è possibile aggiungere la Web Part a una pagina Web Part in SharePoint.  
  
 Per ulteriori informazioni sul debug di progetti SharePoint, vedere [risoluzione dei problemi delle soluzioni di SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Procedura: Creare un controllo utente per una web part o una pagina applicazione di SharePoint](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Viene illustrato come creare controlli personalizzati riutilizzabili che possono essere utilizzati dalle pagine applicazione e dalle Web part eseguite in SharePoint.|  
  
  