---
title: Creazione di Web part per SharePoint | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- Microsoft.SharePoint.WebControls.DateTimeControl
- Microsoft.SharePoint.WebControls.CssLink
- Microsoft.SharePoint.WebControls.RssLink
- Microsoft.SharePoint.WebControls.Theme
- Microsoft.SharePoint.WebControls.AspMenu
- Microsoft.SharePoint.WebControls.ListProperty
- Microsoft.SharePoint.WebControls.ProjectProperty
- Microsoft.SharePoint.WebControls.FormsDigest
- Microsoft.SharePoint.WebControls.ScriptLink
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, Web Parts
- Web Parts [SharePoint development in Visual Studio], designing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 52f35f095c91422f8882724074c54ad48edd88f9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="creating-web-parts-for-sharepoint"></a>Creazione di web part per SharePoint
  Utilizzando le web part, è possibile modificare il contenuto, l'aspetto e il comportamento delle pagine di un sito di SharePoint utilizzando un browser. Web part sono controlli sul lato server che eseguono all'interno di una pagina web part: sono relative ai blocchi predefiniti di pagine visualizzate in un sito di SharePoint. Vedere [blocco predefinito: Web part](http://go.microsoft.com/fwlink/?LinkID=182097).  
  
 È possibile creare e quindi eseguire il debug di web part in un sito di SharePoint utilizzando i modelli di Visual Studio.  
  
## <a name="creating-a-web-part-in-visual-studio"></a>Creazione di una Web Part in Visual Studio  
 Creare una web part aggiungendo un **Web Part** elemento a qualsiasi progetto SharePoint. È possibile utilizzare un **Web Part** elemento in una soluzione creata mediante sandbox o una soluzione farm.  
  
 Se si desidera progettare visivamente una web part tramite una finestra di progettazione, creare un **Web Part visiva** di progetto o aggiungere **Web Part visiva** elemento a qualsiasi progetto SharePoint. È possibile utilizzare un **Web Part visiva** articolo in solo una soluzione farm.  
  
### <a name="web-part-item"></a>Elemento Web Part  
 Oggetto **Web Part** elemento fornisce i file che è possibile utilizzare per progettare una web part per un sito di SharePoint. Quando si aggiunge un **Web Part** item, Visual Studio crea una cartella nel progetto e quindi vengono aggiunti alcuni file nella cartella. La tabella seguente descrive ciascun file.  
  
|File|Descrizione|  
|----------|-----------------|  
|Elements|Contiene informazioni che il file di definizione di funzionalità del progetto utilizzato per distribuire la web part.|  
|file con estensione WebPart|Vengono fornite informazioni necessarie per visualizzare la web part in una raccolta web part per SharePoint.|  
|File di codice|Contiene metodi che aggiungono controlli alla web part e di generare il contenuto personalizzato all'interno della web part.|  
  
 Per ulteriori informazioni, vedere [procedura: creare una Web Part di SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md).  
  
### <a name="visual-web-part-item"></a>Elemento Web Part visiva  
 Una web part visiva è una web part creata utilizzando la finestra di progettazione di Visual Web Developer in Visual Studio. Una web part visiva funziona esattamente come qualsiasi altra web part. Per aggiungere controlli, ad esempio i pulsanti e caselle di testo, a una web part, aggiungere codice in un file XML. Tuttavia, aggiungere controlli a una web part visiva trascinando o copiando li nella web part di Visual Studio **della casella degli strumenti**. La finestra di progettazione genera quindi il codice necessario nel file XML. Vedere [procedura: creare una Web Part di SharePoint tramite una finestra di progettazione](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).  
  
## <a name="sharepoint-controls"></a>Controlli di SharePoint  
 Visual Studio fornisce alcuni controlli per la creazione di pagine di SharePoint, ad esempio le pagine dell'applicazione. Questi controlli vengono visualizzati di **della casella degli strumenti** in **controlli SharePoint**. La funzionalità per questi controlli deriva il [Microsoft.SharePoint.WebControls](http://go.microsoft.com/fwlink/?LinkId=235315) spazio dei nomi, che contiene i controlli server ASP.NET che vengono utilizzati nelle pagine di siti ed elenchi SharePoint.  
  
|Nome controllo|Descrizione|  
|------------------|-----------------|  
|[AspMenu](http://go.microsoft.com/fwlink/?LinkId=235307)|Inserisce un menu ASP. Per ulteriori informazioni, vedere [Cenni preliminari sul controllo Menu](http://go.microsoft.com/fwlink/?LinkId=235316).|  
|[CssLink](http://go.microsoft.com/fwlink/?LinkId=235308)|Inserisce un **collegamento** elemento nella pagina aspx e si applica uno o più fogli di stile esterni definiti da **CssRegistration**.|  
|[DateTimeControl](http://go.microsoft.com/fwlink/?LinkId=235306)|Inserisce un controllo di data/ora nella pagina aspx.|  
|[FormDigest](http://go.microsoft.com/fwlink/?LinkId=235309)|Inserisce una convalida di sicurezza nella pagina. aspx|  
|[ListProperty](http://go.microsoft.com/fwlink/?LinkId=235310)|Restituisce una proprietà di un elenco specificato.|  
|[ProjectProperty](http://go.microsoft.com/fwlink/?LinkId=235311)|Restituisce una proprietà globale del sito Web corrente.|  
|[RssLink](http://go.microsoft.com/fwlink/?LinkId=235312)|Inserisce un collegamento a un feed in una pagina aspx RSS.|  
|[ScriptLink](http://go.microsoft.com/fwlink/?LinkId=235313)|Fornisce proprietà e metodi per la registrazione di risorse, ad esempio gli script, in una pagina in modo che può essere richiesta quando viene eseguito il rendering della pagina.|  
|[Tema](http://go.microsoft.com/fwlink/?LinkId=235314)|Applica un tema per la pagina aspx.|  
  
## <a name="debugging-a-web-part"></a>Debug di una Web Part  
 È possibile eseguire il debug di un progetto di SharePoint che contiene una web part, esattamente come si trattasse del debug di altri progetti di Visual Studio. Quando si avvia il debugger di Visual Studio, Visual Studio apre il sito di SharePoint.  
  
 Per avviare il debug del codice, aggiungere la web part a una pagina web part in SharePoint.  
  
 Per ulteriori informazioni su come eseguire il debug di progetti SharePoint, vedere [risoluzione dei problemi delle soluzioni di SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
## <a name="visual-web-part-limitations"></a>Limitazioni della web part visiva  
 A partire da Visual Studio, è possibile aggiungere una web part visive per soluzioni di SharePoint create mediante sandbox e soluzioni farm. Tuttavia, web part visive presentano le limitazioni seguenti:  
  
-   Web part visive non supportano parametri sostituibili. Per ulteriori informazioni, vedere [parametri sostituibili](../sharepoint/replaceable-parameters.md).  
  
-   Controlli utente o web part visive non può essere trascinata ed eliminata o sono state copiate nella web part visive. Questa azione causerà un errore di compilazione.  
  
-   Web part visive non supportano direttamente i token del server di SharePoint, ad esempio $SPUrl. Per ulteriori informazioni, vedere "Token restrizioni in sandbox Web part visive" nell'argomento [risoluzione dei problemi delle soluzioni di SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
-   Web part visive in una soluzione creata mediante sandbox verifichi l'errore, "la richiesta di esecuzione di codice in modalità sandbox è stata rifiutata perché il servizio Host di codice in modalità sandbox è troppo occupato per gestire la richiesta". Per ulteriori informazioni su questo errore, vedere questo post nel [Blog del Team di SharePoint Developer](http://go.microsoft.com/fwlink/?LinkId=225932).  
  
-   Debug di JavaScript sul lato server non è supportato in Visual Studio, ma è supportato il debug di JavaScript sul lato client.  
  
     Sebbene sia possibile aggiungere inline JavaScript in un file di markup sul lato server, il debug non supportato per i punti di interruzione aggiunti al markup. Per eseguire il debug di JavaScript, fare riferimento a un file JavaScript esterno nel file di markup e quindi impostare i punti di interruzione nel file JavaScript.  
  
-   Debug di codice inline [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] codice deve essere eseguito nel file di codice generato anziché nel file di markup.  
  
-   Web part visive non supportano l'utilizzo del `<@ Assembly Src=` direttiva.  
  
-   Controlli e alcuni web di SharePoint [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] controlli non sono supportati nell'ambiente sandbox di SharePoint. Se si utilizzano controlli non supportati in una web part visiva in una soluzione creata mediante sandbox, l'errore "Il nome tipo o spazio dei nomi 'Tema' non esiste nello spazio dei nomi 'Microsoft.SharePoint.WebControls'".  
  
 Per ulteriori informazioni sulle soluzioni create mediante sandbox, vedere [le differenze tra creata mediante sandbox e soluzioni Farm](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).  
  
## <a name="creating-older-style-sharepoint-based-web-parts"></a>Creazione di precedente stile basato su SharePoint Web part  
 È possibile utilizzare i modelli in Visual Studio per la creazione personalizzata [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] web part per SharePoint. [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] Web part vengono compilate in cima il [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] infrastruttura delle web part e sono il tipo consigliato per i nuovi progetti.  
  
 In alcuni casi, potrebbe essere necessario creare una web part usando lo stile precedente parte web basato su SharePoint. È possibile utilizzare Visual Studio per creare questi tipi di web part, ma Visual Studio non fornisce tutti i modelli che sono progettati specificamente per semplificarne la creazione.  
  
 Per ulteriori informazioni su quando si potrebbe desiderare di creare uno stile precedente parte web basato su SharePoint, vedere [infrastruttura delle Web Part in Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkId=169290). Per ulteriori informazioni su come creare una web part usando lo stile precedente parte web basato su SharePoint, vedere [procedura dettagliata Creazione di una Web Part di SharePoint base](http://go.microsoft.com/fwlink/?LinkId=169288).  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Procedura: Creare una web part di SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)|Viene illustrato come creare una web part per le pagine di SharePoint.|  
|[Procedura: Creare una web part di SharePoint tramite una finestra di progettazione](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)|Viene illustrato come creare una web part per SharePoint utilizzando l'area di progettazione visiva.|  
|[Procedura: Creare un controllo utente per una web part o una pagina applicazione di SharePoint](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Viene illustrato come creare controlli personalizzati riutilizzabili che possono essere utilizzati dalle pagine applicazione e dalle web part eseguite in SharePoint.|  
|[Procedura dettagliata: creazione di una web part per SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)|Viene descritto come progettare una web part per SharePoint.|  
|[Procedura dettagliata: creazione di una web part per SharePoint tramite una finestra di progettazione](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)|Viene descritto come progettare una web part per SharePoint trascinando i controlli a una superficie di progettazione visiva.|  
|[Procedura dettagliata: creazione di una Web part Silverlight che visualizza il servizio OData per SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)|Viene descritto come progettare una web part per SharePoint che ospita un'applicazione Silverlight e visualizza i dati da elenchi SharePoint.|  
  
  