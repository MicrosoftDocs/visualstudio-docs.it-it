---
title: L'accesso ai dati locali e remoti in applicazioni ClickOnce | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, data
- data access, ClickOnce applications
ms.assetid: be5cbe12-6cb6-49c9-aa59-a1624e1eef3d
caps.latest.revision: "21"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: d22180b0e48a875eaef3ab9e3b8ceac35b1fa6ef
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="accessing-local-and-remote-data-in-clickonce-applications"></a>Accesso a dati locali e remoti in applicazioni ClickOnce
La maggior parte delle applicazioni usa o produce dati. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] offre diverse opzioni per la lettura e la scrittura di dati, in locale e in remoto.  
  
## <a name="local-data"></a>Dati locali  
 Con [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], è possibile caricare e archiviare i dati in locale usando uno dei seguenti metodi:  
  
-   Directory dei dati di[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]   
  
-   Spazio di memorizzazione isolato  
  
-   Altri file locali  
  
### <a name="clickonce-data-directory"></a>Directory dei dati di ClickOnce  
 Ogni applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] installata in un computer locale ha una directory dei dati, archiviata nella cartella dell'utente Documents and Settings. Tutti i file inclusi in un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] e contrassegnati come file "data" vengono copiati in questa directory quando viene installata un'applicazione. I file di dati possono essere di qualsiasi tipo. Quelli usati più frequentemente sono i file di testo, i file XML e i file di database, ad esempio i file mdb di Microsoft Access.  
  
 La directory dei dati è destinata a dati gestiti dall'applicazione, ossia dati archiviati e gestiti in modo esplicito dall'applicazione. Tutti i file statici senza dipendenze non contrassegnati come "data" nel manifesto dell'applicazione risiedono invece nella directory delle applicazioni. In questa directory si trovano i file eseguibili dell'applicazione (exe) e gli assembly.  
  
> [!NOTE]
>  Quando un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] viene disinstallata, viene rimossa anche la directory dei dati. Non utilizzare mai la Directory dei dati per archiviare dati end-user-gestito, ad esempio i documenti.  
  
#### <a name="marking-data-files-in-a-clickonce-distribution"></a>Contrassegno dei file di dati in una distribuzione ClickOnce  
 Per inserire un file esistente nella directory dei dati, è necessario contrassegnarlo come file di dati nel file manifesto dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Per altre informazioni, vedere [How to: Include a Data File in a ClickOnce Application](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
#### <a name="reading-from-and-writing-to-the-data-directory"></a>Lettura e scrittura nella directory dei dati  
 Per la lettura dalla directory dei dati, l'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] deve richiedere le autorizzazioni di lettura. Analogamente, per la scrittura nella directory sono necessarie le autorizzazioni di scrittura. L'applicazione ottiene automaticamente queste autorizzazioni se è configurata per l'esecuzione con attendibilità totale. Per ulteriori informazioni sull'elevazione delle autorizzazioni per l'applicazione mediante l'elevazione delle autorizzazioni o distribuzione di applicazioni attendibili, vedere [protezione delle applicazioni ClickOnce](../deployment/securing-clickonce-applications.md).  
  
> [!NOTE]
>  Se l'organizzazione non usa la distribuzione di applicazioni attendibili e ha disattivato l'elevazione delle autorizzazioni, l'asserzione delle autorizzazioni non riesce.  
  
 Una volta ottenute queste autorizzazioni, l'applicazione può accedere alla directory dei dati usando le chiamate al metodo nelle classi contenute in <xref:System.IO>. È possibile ottenere il percorso della directory dei dati all'interno di un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] di Windows Form usando la proprietà <xref:System.Deployment.Application.ApplicationDeployment.DataDirectory%2A> definita nella proprietà <xref:System.Deployment.Application.ApplicationDeployment.CurrentDeployment%2A> di <xref:System.Deployment.Application.ApplicationDeployment>. È il modo consigliato più appropriato per l'accesso ai dati. Il seguente esempio di codice mostra la procedura per un file di testo denominato CSV.txt incluso nella distribuzione come file di dati.  
  
 [!code-csharp[ClickOnce.OpenDataFile#1](../deployment/codesnippet/CSharp/accessing-local-and-remote-data-in-clickonce-applications_1.cs)]
 [!code-vb[ClickOnce.OpenDataFile#1](../deployment/codesnippet/VisualBasic/accessing-local-and-remote-data-in-clickonce-applications_1.vb)]  
  
 Per altre informazioni su come contrassegnare i file nella distribuzione come file di dati, vedere [How to: Include a Data File in a ClickOnce Application](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
 È anche possibile ottenere il percorso della directory dei dati usando le variabili rilevanti nella classe <xref:System.Windows.Forms.Application> , ad esempio <xref:System.Windows.Forms.Application.LocalUserAppDataPath%2A>.  
  
 La manipolazione di altri tipi di file potrebbe richiedere autorizzazioni aggiuntive. Ad esempio, per usare un file di database di Access (mdb), l'applicazione deve asserire l'attendibilità totale per usare le classi <xref:System.Data> rilevanti.  
  
#### <a name="data-directory-and-application-versions"></a>Directory dei dati e versioni dell'applicazione  
 Ogni versione dell'applicazione ha la propria directory dei dati, isolata rispetto alle altre versioni. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] crea questa directory indipendentemente dai file di dati inclusi nella distribuzione in modo che l'applicazione disponga di un percorso in cui creare i nuovi file di dati in fase di esecuzione. Quando viene installata una nuova versione di un'applicazione, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] copia tutti i file di dati esistenti dalla directory dei dati della versione precedente alla directory dei dati della nuova versione, indipendentemente dal fatto che i file fossero inclusi nella distribuzione originale o siano stati creati dall'applicazione.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sostituisce la versione precedente del file con la versione più recente del server se il valore hash di un file di dati nella versione precedente dell'applicazione è diverso da quello nella nuova versione. Inoltre, se la versione precedente dell'applicazione ha creato un nuovo file con lo stesso nome del file incluso nella distribuzione della nuova versione, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sovrascrive il file della versione precedente con il nuovo file. In entrambi i casi, i file precedenti verranno inclusi in una sottodirectory all'interno della directory dei dati denominata `.pre`, in modo che l'applicazione possa ancora accedere ai dati precedenti per scopi di migrazione.  
  
 Per una migrazione dei dati più specifica, è possibile usare l'API di distribuzione di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] per eseguire una migrazione personalizzata dalla directory dei precedente a quella nuova. Sarà necessario verificare la disponibilità di un download usando <xref:System.Deployment.Application.ApplicationDeployment.IsFirstRun%2A>, scaricare l'aggiornamento con <xref:System.Deployment.Application.ApplicationDeployment.Update%2A> o <xref:System.Deployment.Application.ApplicationDeployment.UpdateAsync%2A>ed eseguire il processo di migrazione dei dati personalizzato autonomamente dopo il completamento dell'aggiornamento.  
  
### <a name="isolated-storage"></a>Spazio di memorizzazione isolato  
 Lo spazio di memorizzazione isolato fornisce un'API per creare e accedere ai file usando una semplice API. Il percorso effettivo dei file archiviati è nascosto sia allo sviluppatore che all'utente.  
  
 Lo spazio di memorizzazione isolato funziona in tutte le versioni di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Lo spazio di memorizzazione isolato funziona anche in applicazioni parzialmente attendibili senza necessità di autorizzazioni aggiuntive. Usare lo spazio di memorizzazione isolato se l'applicazione deve essere eseguita con attendibilità parziale, ma deve gestire dati specifici dell'applicazione.  
  
 Per altre informazioni, vedere [Spazio di memorizzazione isolato](/dotnet/standard/io/isolated-storage).  
  
### <a name="other-local-files"></a>Altri file locali  
 Se l'applicazione deve usare o salvare dati dell'utente finale come report, immagini, musica e così via, l'applicazione richiederà che <xref:System.Security.Permissions.FileIOPermission> sia in grado di leggere e scrivere i dati nel file system locale.  
  
## <a name="remote-data"></a>Dati remoti  
 A un certo punto, l'applicazione dovrà probabilmente recuperare informazioni da un sito Web remoto, ad esempio dati del cliente o informazioni di mercato. Questa sezione descrive le tecniche più comuni per il recupero dei dati remoti.  
  
### <a name="accessing-files-by-using-http"></a>Accesso ai file con HTTP  
 È possibile accedere ai dati da un server Web usando la classe <xref:System.Net.WebClient> o <xref:System.Net.HttpWebRequest> nello spazio dei nomi <xref:System.Net> . I dati possono essere file statici o applicazioni [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] che restituiscono testo non elaborato o dati XML. Se i dati sono in formato XML, il modo più veloce per recuperarli prevede l'uso della classe <xref:System.Xml.XmlDocument> , il cui metodo <xref:System.Xml.XmlDocument.Load%2A> acquisisce un URL come argomento. Per un esempio, vedere [Reading an XML Document into the DOM](/dotnet/standard/data/xml/reading-an-xml-document-into-the-dom).  
  
 È necessario tenere presenti i problemi legati alla sicurezza quando l'applicazione accede ai dati remoti tramite HTTP. Per impostazione predefinita, l'accesso dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] alle risorse di rete può essere limitato, a seconda di come è stata distribuita l'applicazione. Queste restrizioni vengono applicate per evitare che programmi dannosi accedano ai dati remoti riservati o che usino il computer di un utente per attaccare gli altri computer della rete.  
  
 La tabella seguente elenca le strategie di distribuzione che è possibile usare e le relative autorizzazioni Web predefinite.  
  
|Tipo di distribuzione|Autorizzazioni di rete predefinite|  
|---------------------|---------------------------------|  
|Installazione Web|Può accedere solo al server Web da cui è stata installata l'applicazione|  
|Installazione da condivisione file|Non può accedere a tutti i server Web|  
|Installazione da CD-ROM|Può accedere a qualsiasi server Web|  
  
 Se l'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] non riesce ad accedere a un server Web a causa di restrizioni di sicurezza, l'applicazione deve asserire <xref:System.Net.WebPermission> per il sito Web specificato. Per ulteriori informazioni su come aumentare le autorizzazioni di sicurezza per un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione, vedere [protezione delle applicazioni ClickOnce](../deployment/securing-clickonce-applications.md).  
  
### <a name="accessing-data-through-an-xml-web-service"></a>Accesso ai dati mediante un servizio Web XML  
 Se si espongono i dati sotto forma di servizio Web XML, è possibile accedervi usando un proxy del servizio Web XML. Il proxy è una classe [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] creata usando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Le operazioni del servizio Web XML, ad esempio il recupero dei clienti, l'emissione di ordini e così via, vengono esposte come metodi nel proxy. I servizi Web risultano più semplici da usare rispetto al testo non elaborato o ai file XML.  
  
 Se il servizio Web XML funziona tramite HTTP, sarà associato alle stesse restrizioni di sicurezza delle classi <xref:System.Net.WebClient> e <xref:System.Net.HttpWebRequest> .  
  
### <a name="accessing-a-database-directly"></a>Accesso diretto al database  
 È possibile usare le classi nello spazio dei nomi <xref:System.Data> per stabilire connessioni dirette a un server di database come SQL Server in rete, ma è necessario tenere presente i problemi legati alla sicurezza. A differenza delle richieste HTTP, le richieste di connessione di database sono sempre vietate in caso di attendibilità parziale. Queste autorizzazioni sono disponibili per impostazione predefinita solo se l'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] viene installata da un CD-ROM. In questo modo, l'applicazione ottiene l'attendibilità totale. Per abilitare l'accesso a uno specifico database di SQL Server, l'applicazione deve richiedere <xref:System.Data.SqlClient.SqlClientPermission> a tale database. Per abilitare l'accesso a un database diverso da SQL Server, deve richiedere <xref:System.Data.OleDb.OleDbPermission>.  
  
 Nella maggior parte dei casi, l'accesso al database non è diretto, ma avviene mediante un'applicazione del server Web scritta in [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] o un servizio Web XML. Questo tipo di accesso al database rappresenta in genere il metodo migliore se l'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] viene distribuita da un server Web. È possibile accedere al server con un'attendibilità parziale senza elevare le autorizzazioni dell'applicazione.  
  
## <a name="see-also"></a>Vedere anche  
 [How to: Include a Data File in a ClickOnce Application](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md)