---
title: Modelli di supporto di siti Web | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: we site projects, templates
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b17674b8cd5058ec20db4c483b2c3508aa275b29
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="web-site-support-templates"></a>Modelli di supporto di siti Web
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]I modelli di progetto e di elemento di siti Web forniscono stub riutilizzabili e personalizzabili sito progetto e di elemento che consente di accelerare il processo di sviluppo, eliminando la necessità di creare nuovi progetti di sito Web e gli elementi da zero. Per ulteriori informazioni su [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] modelli, vedere [creazione Project and Item Templates](../../ide/creating-project-and-item-templates.md).  
  
## <a name="project-template-folder"></a>Cartella modelli di progetto  
 Modelli di modello di progetto Web sono in genere installati in [*percorso di installazione di Visual Studio*] \Common7\IDE\ProjectTemplates\Web\\, ciascuno in una sottocartella denominata in base al linguaggio di programmazione web.  
  
## <a name="project-file"></a>File di progetto  
 Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE) richiede un'estensione di file di progetto come un modo per eseguire il mapping di un modello per il tipo di progetto corretti. Progetti Web non dispone di un file di progetto, a tale scopo è registrato il webproj estensione file di progetto fittizio.  
  
 Facoltativamente, aggiungere al modello per consentire al sistema di progetto Web di impostare la lingua predefinita in una stringa del nome di lingua di **Aggiungi nuovo elemento** la finestra di dialogo per gli elementi in base al modello. La stringa deve essere la prima riga del file e deve corrispondere al nome registrato in AddItemLanguageName nella registrazione motore Intellisense sia il nome registrato nel progetto Subtype(VsTemplate). Per ulteriori informazioni, vedere [sito Web supporto attributi](../../extensibility/internals/web-site-support-attributes.md).  
  
 Se la stringa non è presente, il sistema del progetto Web tenterà di determinare la lingua predefinita in base alle estensioni di attributi e i file del linguaggio delle pagine aggiunte al progetto Web per il modello di progetto.  
  
## <a name="project-templates"></a>Modelli di progetto  
 Modelli di progetto di sito Web vengono utilizzati per creare nuovi siti Web in risposta al **nuovo sito Web** comando il **File** menu. Attualmente sono supportati tre tipi di progetto di sito Web:  
  
-   Progetti di sito Web vuoto  
  
-   Progetti di siti Web  
  
-   Progetti di servizi Web  
  
### <a name="empty-web-site-projects"></a>Progetti di sito Web vuoto  
 Questi file creano un nuovo sito Web vuoto in risposta al **sito Web vuoto** comando, è disponibile dopo aver scelto **nuovo sito Web** sul **File** menu:  
  
-   EmptyWeb.vstemplate  
  
     Il file di modello che descrive la creazione del nuovo sito Web vuoto.  
  
-   EmptyWeb.webproj  
  
     Questo file è un elemento del sistema del modello di progetto. Il riferimento al file di progetto nel file EmptyWeb.vstemplate soddisfa.  
  
### <a name="web-site-projects"></a>Progetti di siti Web  
 Questi file creano un nuovo sito Web in risposta al **sito Web ASP.NET** comando, è disponibile dopo aver scelto **nuovo sito Web** sul **File** menu:  
  
-   Default.aspx  
  
     Home page predefinita per il nuovo sito Web. L'attributo di linguaggio specifica language il codebehind e l'attributo CodeFile specifica il file dipendenti contenente codice il codebehind associato a questa pagina.  
  
-   Default.aspx. *estensione*  
  
     Il file dipendente che contiene il codice sottostante per la home page predefinita. Lingua il codebehind determina il *estensione* di questo file.  
  
-   web.config  
  
     File di configurazione web.site principale.  
  
-   WebApplication.vstemplate  
  
     Il file di modello che determina il contenuto di Esplora il sito Web e forza la creazione della cartella App_Data.  
  
-   WebApplication.webproj  
  
     Questo file è un elemento del sistema del modello di progetto. Il riferimento al file di progetto nel file WebApplication.vstemplate soddisfa.  
  
### <a name="web-service-projects"></a>Progetti di servizi Web  
 Questi file creano un nuovo sito Web in risposta al **servizio Web ASP.NET** comando disponibile dopo aver scelto **nuovo sito Web** sul **File** menu:  
  
-   Asmx  
  
     La pagina HTML per il nuovo servizio Web. L'attributo di linguaggio specifica language il codebehind e l'attributo CodeBehind specifica il file dipendenti contenente codice il codebehind associato a questo servizio.  
  
-   Servizio. *estensione*  
  
     Il file dipendente che implementa la classe del servizio. Lingua il codebehind determina il *estensione* di questo file.  
  
-   web.config  
  
-   File di configurazione web.site principale.  
  
-   WebService.vstemplate  
  
     Il file di modello che determina il contenuto di Esplora il sito Web e forza la creazione delle cartelle App_Data e App_Code. Il servizio. *estensione* file viene copiato nella cartella App_Code.  
  
-   WebService.webproj  
  
     Questo file è un elemento del sistema del modello di progetto. Il riferimento al file di progetto nel file WebService.vstemplate soddisfa.  
  
## <a name="project-item-template-folder"></a>Cartella del modello di elemento di progetto  
 Modelli di modello di elemento di progetto Web sono in genere installati in [*percorso di installazione di Visual Studio*] \Common7\IDE\ItemTemplates\Web\\, ciascuno in una sottocartella denominata in base al relativo linguaggio di programmazione web.  
  
## <a name="project-item-templates"></a>I modelli di progetto  
 I modelli di progetto di sito Web vengono utilizzati per aggiungere nuove pagine Web a un sito Web in risposta al **Aggiungi elemento esistente** comando. Questi tipi di pagine Web sono attualmente supportati:  
  
-   Nuova classe  
  
-   Nuova pagina HTML  
  
-   Nuovo Web Form  
  
-   Pagina master  
  
### <a name="new-class"></a>Nuova classe  
 Questo modello consente di creare un nuovo file di origine che definisce una classe vuota in risposta al **Aggiungi nuova classe** comando.  
  
-   Class. *estensione*  
  
     Il file di origine che implementa la classe vuota. Lingua il codebehind determina il *estensione* di questo file.  
  
-   Class.vstemplate  
  
     Il file di modello che crea il file di origine e determina il relativo contenuto.  
  
### <a name="new-html-page"></a>Nuova pagina HTML  
 Questo modello consente di creare una nuova pagina Web in risposta al **Aggiungi nuova pagina HTML** comando.  
  
-   HtmlPage. htm  
  
     Il contenuto inizio della pagina Web. Questa pagina Web non è in genere alcun file dipendente il codebehind associato. Per creare una pagina intelligente con un file il codebehind associati, utilizzare il modello Web Form.  
  
-   HTMLPage.vstemplate  
  
     Il file di modello che crea la pagina Web e determina il relativo contenuto.  
  
### <a name="new-webform"></a>Nuovo Web Form  
 Questo modello consente di creare una nuova pagina Web smart in risposta al **Aggiungi nuovo Web Form** comando.  
  
 Per creare un file di origine il codebehind dipendenti, selezionare **inserire il codice in file separato**. In caso contrario viene creata con un blocco di script vuoto e non una singola pagina Web \<pagina % % > direttive per collegare un file dipendente.  
  
 Per creare una pagina contenuto per una pagina master selezionata, selezionare **Seleziona pagina master**.  
  
-   WebForm.aspx  
  
     Il contenuto inizio della pagina Web. Questa pagina Web non dispone di alcun file dipendente il codebehind associato.  
  
-   WebForm_cb.aspx  
  
     Il contenuto inizio della pagina Web. Questa pagina Web è un file di dipendenti il codebehind associato.  
  
-   Codebehind. *estensione*  
  
     Il file dipendente che implementa la classe di Web Form. Lingua il codebehind determina il *estensione* di questo file.  
  
-   ContentPage.aspx  
  
     Il contenuto inizio della pagina Web come una pagina di contenuto. Questa pagina Web non dispone di alcun file dipendente il codebehind associato.  
  
-   ContentPage_cb.aspx  
  
     Il contenuto inizio della pagina Web come una pagina di contenuto. Questa pagina Web è un file di dipendenti il codebehind associato.  
  
-   WebForm.vstemplate  
  
     Il file di modello che determina il contenuto della nuova pagina web e i relativi file dipendenti, se presente.  
  
### <a name="new-master-page"></a>Nuova pagina Master  
 Questo modello consente di creare una nuova pagina master in risposta al **Aggiungi pagina Master** comando.  
  
 Per creare un file di origine il codebehind dipendenti, selezionare **inserire il codice in file separato**. In caso contrario viene creata con un blocco di script vuoto e non una singola pagina Web \<pagina % % > direttive per collegare un file dipendente.  
  
-   MasterPage  
  
     Il contenuto inizio della pagina master. Questa pagina master non dispone di alcun file dipendente il codebehind associato.  
  
-   MasterPage_cb.master  
  
     Il contenuto inizio della pagina master. Questa pagina master è un file di dipendenti il codebehind associato.  
  
-   Codebehind. *estensione*  
  
     Il file dipendente che implementa la classe di pagina master. Lingua il codebehind determina il *estensione* di questo file.  
  
-   MasterPage.vstemplate  
  
     Il file di modello che determina il contenuto della nuova pagina master e i relativi file dipendenti, se presente.  
  
## <a name="see-also"></a>Vedere anche  
 [Supporto per siti Web](../../extensibility/internals/web-site-support.md)