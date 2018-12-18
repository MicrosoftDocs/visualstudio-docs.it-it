---
title: Sicurezza per le soluzioni SharePoint | Documenti Microsoft
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
- VB
- CSharp
helpviewer_keywords:
- security [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, security
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 6e9aff74a49f738f4a0ed0df68ffe2e9a5b33525
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="security-for-sharepoint-solutions"></a>Sicurezza per le soluzioni SharePoint
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]include le funzionalità seguenti che consentono di migliorare la sicurezza delle applicazioni di SharePoint.  
  
## <a name="safe-control-entries"></a>Voci di controllo sicure  
 Ogni elemento di progetto SharePoint creato nel [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ha un **voci di controllo sicure** insieme di controlli di proprietà che rappresenta una cassaforte. Il relativo **provvisoria** sottoproprietà consente di specificare i controlli che si ritengano protetto. Per ulteriori informazioni, vedere [che fornisce informazioni sui pacchetti e distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) e [specifica Web part sicure](http://go.microsoft.com/fwlink/?LinkId=177521).  
  
## <a name="allowpartiallytrustedcallers-attribute"></a>Attributo AllowPartiallyTrustedCallers  
 Per impostazione predefinita, solo le applicazioni considerate completamente attendibili dal sistema di sicurezza dall'accesso di codice runtime possono accedere a un assembly di codice gestito condiviso. Contrassegnare un assembly completamente attendibile con l'attributo AllowPartiallyTrustedCallers consente agli assembly parzialmente attendibili per l'accesso.  
  
 L'attributo AllowPartiallyTrustedCallers viene aggiunto a qualsiasi soluzione di SharePoint che non è distribuita in cache assembly globali del sistema ([!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]). Ciò include soluzioni create mediante sandbox o distribuite nella directory Bin dell'applicazione di SharePoint. Per ulteriori informazioni, vedere [modifiche della sicurezza per Microsoft .NET Framework versione 1](http://go.microsoft.com/fwlink/?LinkId=177515) e [distribuzione di Web part in SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177509).  
  
## <a name="safe-against-script-property"></a>Proprietà sicurezza Script  
 *Script injection* è l'inserimento di codice potenzialmente dannoso nei controlli o le pagine Web. Per proteggere i siti di SharePoint 2010 dagli attacchi script injection, è possono che collaboratori visualizzare o modificare le Web part o le relative proprietà per impostazione predefinita. Questo comportamento è controllato da un attributo SafeControl denominato SafeAgainstScript. In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], impostare questo attributo in un elemento di progetto **voci di controllo sicure** sottoproprietà **sicurezza Script**. Per ulteriori informazioni, vedere [che fornisce informazioni sui pacchetti e distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) e [come: contrassegna i controlli come controlli sicuri](../sharepoint/how-to-mark-controls-as-safe-controls.md).  
  
## <a name="vista-and-windows-7-user-account-control"></a>Vista e Windows 7 Account utente  
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)]e [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] incorporare una funzionalità di sicurezza nota come controllo Account utente (UAC). Per sviluppare soluzioni SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] su [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] e [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] sistemi di controllo dell'account utente richiede l'esecuzione di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] come amministratore di sistema. Dal **avviare** menu, aprire il menu di scelta rapida per [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], quindi scegliere **Esegui come amministratore**.  
  
 Per configurare il [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] scelta rapida per sempre Esegui come amministratore, aprire il menu di scelta rapida, scegliere **proprietà**, scegliere il **avanzate** pulsante il **proprietà**la finestra di dialogo e quindi selezionare il **Esegui come amministratore** casella di controllo.  
  
 Per ulteriori informazioni, vedere [comprensione e la configurazione di controllo dell'Account utente in Windows Vista](http://go.microsoft.com/fwlink/?LinkID=156476). e [controllo Account utente di Windows 7](http://go.microsoft.com/fwlink/?LinkId=177523).  
  
## <a name="sharepoint-permissions-considerations"></a>Considerazioni sulle autorizzazioni di SharePoint  
 Per sviluppare soluzioni SharePoint, è necessario disporre di autorizzazioni sufficienti per eseguire il debug delle soluzioni di SharePoint. Prima di poter testare una soluzione di SharePoint, eseguire i passaggi seguenti per assicurarsi di disporre delle autorizzazioni necessarie:  
  
1.  Aggiungere l'account utente come amministratore di sistema.  
  
2.  Aggiungere l'account utente come amministratore di Farm per il server SharePoint.  
  
    1.  In Amministrazione centrale SharePoint 2010, scegliere il **gestire il gruppo di amministratori farm** collegamento.  
  
    2.  Nel **amministratori Farm** pagina, scegliere il **New** opzione di menu  
  
3.  Aggiungere l'account utente per al gruppo WSS_ADMIN_WPG.  
  
## <a name="additional-security-resources"></a>Ulteriori risorse di protezione  
 Per ulteriori informazioni sui problemi di sicurezza, vedere gli argomenti seguenti.  
  
### <a name="visual-studio-security"></a>Sicurezza in Visual Studio  
  
-   [Sicurezza e autorizzazioni utente](http://go.microsoft.com/fwlink/?LinkId=177503)  
  
-   [Protezione nativa e codice di .NET Framework](http://go.microsoft.com/fwlink/?LinkId=177504)  
  
-   [Sicurezza in .NET Framework](http://go.microsoft.com/fwlink/?LinkId=177502)  
  
### <a name="sharepoint-security"></a>Sicurezza di SharePoint  
  
-   [Protezione e amministrazione di SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177501)  
  
-   [Centro risorse di protezione di SharePoint](http://go.microsoft.com/fwlink/?LinkId=177498)  
  
-   [Protezione delle Web part in SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177511)  
  
-   [Miglioramento sicurezza delle applicazioni Web: Minacce e contromisure](http://go.microsoft.com/fwlink/?LinkID=140080)  
  
### <a name="general-security"></a>Sicurezza generale  
  
-   [MSDN Security Development Lifecycle](http://go.microsoft.com/fwlink/?LinkID=147149)  
  
-   [Compilazione di applicazioni ASP.NET sicure: Autenticazione, autorizzazione e comunicazione protetta](http://go.microsoft.com/fwlink/?LinkId=177494)  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo di soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md)  
  
  