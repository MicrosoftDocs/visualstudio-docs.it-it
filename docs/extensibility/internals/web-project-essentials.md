---
title: Web Essentials progetto | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: web projects, essentials
ms.assetid: ca2f4e43-322c-4431-8680-52da846940bc
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ac781256ee78becf3b0cfdffbbec6f0c6bc30225
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="web-project-essentials"></a>Essentials progetto Web
Progetti Web creano applicazioni Web. È possibile utilizzare un progetto Web per creare un'applicazione Web che include pagine Web smart. Una pagina Web smart ha codice lato server che esegue il rendering della pagina Web richiesta.  
  
 Utilizzo di linguaggi di programmazione tradizionali, ad esempio [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] o [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], è possibile creare pagine Web intelligente per raccogliere e l'elaborazione delle informazioni da un utente, archiviarlo in un database e così via.  
  
-   Il modello code-behind Associa file di codice sorgente dipendente a pagine Web con il file estensione aspx o asmx. Ad esempio, in Hello potrebbe essere il hello.aspx.cs di file di codice sorgente dipendente.  
  
-   Il codice sul lato server associato a una pagina Web intelligente viene compilato in un file eseguibile che si trova nella cartella /bin del sito Web.  
  
-   File di codice di origine aggiuntivi, ad esempio, classi helper che non sono associati a una pagina Web specifica, si trovano nella cartella /App_Code sito Web.  
  
    -   Un progetto di sito Web (WSP) genera un file eseguibile per ogni pagina Web smart. File eseguibile aggiuntivi vengono generati da qualsiasi file di codice sorgente nella cartella /App_Code.  
  
    -   Un progetto di applicazione Web (WAP) produce un unico file eseguibile che combina il codice per tutte le pagine Web smart, nonché tutti i file di origine nella cartella /App_Code.  
  
-   Trova il file di soluzione per un progetto Web separatamente dal sito Web stesso. Per impostazione predefinita, i file di soluzione si trovano in \Documents and Settings\\*AccountUtente*documenti \My\\*\<Visual Studio # # # >*\Projects\\ *YourWebSite*.  
  
    > [!NOTE]
    >  Se si desidera mantenere il file della soluzione con il sito Web, è sufficiente spostare non esiste e riaprirlo.  
  
-   Se si apre un sito Web che non dispone di alcun file di soluzione in Visual Studio, che viene generato automaticamente un nuovo file di soluzione.  
  
-   Progetti Web non sono disponibili file di progetto. Informazioni di progetto vengono archiviate nel file di soluzione, il file Web. config e così via.  
  
-   Aggiunta automatica di proprietà globali per un progetto Web crea un file di archiviazione nella cartella della soluzione del progetto Web.  
  
-   Una pagina Web smart può essere associata a un linguaggio di programmazione sul lato server tramite la direttiva di pagina o \<script runat = "server" > tag.  
  
-   Inoltre, le pagine Web può avere qualsiasi numero di blocchi di script sul lato client scritto in qualsiasi linguaggio di scripting.  
  
-   Viene implementato un sistema di progetto di sito Web tramite l'aggiunta di modelli di progetto e di elemento e la registrazione per il [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] progetto.  
  
-   Un sistema WAP viene implementato come un sottotipo di progetto, denominato anche una versione del progetto. Il [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] progetto è versione per il sottotipo WAP per creare il sistema WAP. Per ulteriori informazioni su sottotipi di progetto, vedere [sottotipi di progetto](../../extensibility/internals/project-subtypes.md).  
  
-   Una pagina Web smart combina HTML con un linguaggio di programmazione sul lato server. La lingua del server viene chiamata il linguaggio indipendente. Per supportare una lingua indipendente, è necessario che il sistema del progetto Web di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> famiglia di interfacce.  
  
    -   Per supportare la lingua contenuta in un editor, il servizio di linguaggio HTML deve rinviare la visualizzazione di codice lingua indipendente a un servizio di linguaggio indipendente.  
  
    -   Marcatori di errore (smettono) è necessario creare sempre nel buffer principale dell'editor di codice.  
  
## <a name="see-also"></a>Vedere anche  
 [Progetti Web](../../extensibility/internals/web-projects.md)