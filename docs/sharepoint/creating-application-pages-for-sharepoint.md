---
title: Creazione di pagine dell'applicazione per SharePoint | Documenti Microsoft
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
- SharePoint development in Visual Studio, Web pages
- SharePoint development in Visual Studio, content pages
- SharePoint development in Visual Studio, application pages
- application pages [SharePoint development in Visual Studio], developing
- application pages [SharePoint development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 68731e2a0c933f3f48f3a2211a9d17ca21e50242
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="creating-application-pages-for-sharepoint"></a>Creazione di pagine applicazione per SharePoint
  Un *pagina applicazione* è una pagina Web ASP.NET che è progettata per l'uso in un sito Web di SharePoint. Pagine dell'applicazione sono un tipo specializzato di pagina ASP.NET. La differenza principale tra una pagina dell'applicazione e una pagina ASP.NET standard è che una pagina dell'applicazione include contenuto che viene unito con una pagina master di SharePoint. Una pagina master consente di condividere lo stesso aspetto e comportamento delle altre pagine in un sito di pagine dell'applicazione.  
  
 Visual Studio consente di progettare pagine applicazione usando una finestra di progettazione. La finestra di progettazione consente di visualizzare un'area di contenuto per ogni segnaposto di contenuto che è definito in una pagina master. È possibile progettare la pagina dell'applicazione trascinando i controlli a queste aree di contenuto.  
  
## <a name="application-pages"></a>Pagine dell'applicazione  
 Le pagine dell'applicazione sono condivise da tutti i siti sul server, mentre una pagina del sito è a un sito specifico. Per ulteriori informazioni, [tipi di pagine di SharePoint](http://go.microsoft.com/fwlink/?LinkID=211584).  
  
 Per impostazione predefinita, la maggior parte delle pagine visualizzate quando si crea un sito di SharePoint sono pagine del sito. Una pagina del sito può essere aggiunti a una raccolta di pagine di SharePoint. Gli utenti possono personalizzare una pagina del sito mediante strumenti quali SharePoint Designer. Una pagina del sito può ospitare anche le funzionalità, ad esempio Web part dinamiche e aree Web Part.  
  
 Le pagine dell'applicazione non è possibile eseguire queste operazioni. Tuttavia, una pagina dell'applicazione è il tipo di pagina per creare, se si desidera che la pagina per contenere codice personalizzato. Sebbene sia possibile aggiungere codice personalizzato a una pagina del sito, il codice si interrompe quando l'utente Personalizza la pagina mediante strumenti quali SharePoint Designer.  
  
> [!NOTE]  
>  Visual Studio non sono disponibili modelli che consentono di creano pagine del sito per un sito di SharePoint. Per ulteriori informazioni, vedere [tipi di pagine di SharePoint](http://go.microsoft.com/fwlink/?LinkID=211584).  
  
## <a name="creating-an-application-page"></a>Creazione di una pagina dell'applicazione  
 Per creare una pagina applicazione, aggiungere un **pagina applicazione** elemento a un progetto SharePoint. Quando si crea una pagina applicazione, Visual Studio aggiunge le cartelle seguenti al progetto:  
  
|Cartella|Descrizione|  
|------------|-----------------|  
|Layout|Esegue il mapping alla directory virtuale layouts del file system di SharePoint.|  
|Sottocartella di layout|Contiene i file che costituiscono la pagina dell'applicazione. Per impostazione predefinita, questa cartella include lo stesso nome del progetto. È possibile rinominare la cartella in qualsiasi momento. Quando si esegue il progetto, Visual Studio distribuisce questa cartella per la directory virtuale layouts del file system di SharePoint.|  
  
 Visual Studio aggiunge i seguenti file al progetto:  
  
|File|Descrizione|  
|----------|-----------------|  
|File della pagina ASP.NET (aspx)|Contiene il markup XML che definisce la pagina.|  
|File di codice pagina applicazione|Contiene il codice dietro la pagina dell'applicazione. Aggiungere il codice che gestisce gli eventi per questo file.|  
|File di codice della finestra di progettazione di pagina di applicazione|Contiene il codice generato dalla finestra di progettazione. Non modificare direttamente il file.|  
  
## <a name="designing-and-debugging-an-application-page"></a>Progettazione e debug di una pagina dell'applicazione  
 Progettare il contenuto di una pagina dell'applicazione utilizzando la visualizzazione di progettazione in Visual Studio. Questa finestra di progettazione viene visualizzata quando si apre la pagina dell'applicazione nel progetto (facendo doppio clic o aprendo il relativo menu di scelta rapida e scegliendo **aprire**) e quindi scegliere il **progettazione** pulsante nella parte inferiore della l'editor.  
  
> [!NOTE]  
>  È possibile progettare la pagina solo nel **origine** della finestra di progettazione. Il **progettazione** visualizzazione della finestra di progettazione è disabilitata per le pagine dell'applicazione.  
  
 È possibile eseguire il debug di una pagina applicazione esattamente come si trattasse del debug di altri elementi di progetto SharePoint in Visual Studio. Quando si avvia il debugger di Visual Studio, Visual Studio apre il sito di SharePoint.  
  
 Per visualizzare la pagina dell'applicazione, è necessario passare manualmente alla posizione della pagina dell'applicazione (ad esempio: http://*nome_server*/_layouts/*Project_Name*/ApplicationPage1.aspx).  
  
 Per ulteriori informazioni su come eseguire il debug di progetti SharePoint, vedere [risoluzione dei problemi delle soluzioni di SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
## <a name="choosing-a-master-page"></a>Scelta di una pagina Master  
 Per impostazione predefinita, un **pagina applicazione** elemento fa riferimento la pagina principale del sito che si utilizza per il debug del progetto. Pagina denominata v4. master che sarà possibile trovarlo nel **raccolta pagine Master** del sito di SharePoint.  
  
 È possibile modificare in modo esplicito la pagina master viene utilizzata dalla pagina dell'applicazione impostando il `MasterPageFile` attributo dell'applicazione `Page` elemento. (Ad esempio: `MasterPageFile="~/_layouts/applicationv4.master"`). In effetti, è necessario impostare questo attributo se le pagine master dinamiche non sono abilitate nel server SharePoint. Per ulteriori informazioni sulle pagine master in SharePoint, vedere [pagine Master](http://go.microsoft.com/fwlink/?LinkID=169281).  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo per SharePoint Foundation in profondità](http://go.microsoft.com/fwlink/?LinkID=182103)   
 [Panoramica di ASP.NET](/aspnet/overview)   
 [ASP.NET Web Pages](/aspnet/web-pages/index)   
  
  