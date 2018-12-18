---
title: Creazione di pagine delle opzioni | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
caps.latest.revision: "29"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ae8540a2f372abacd8eda6e63cd868edbb050392
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="creating-options-pages"></a>Creazione di pagine Opzioni
Nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] framework di pacchetto gestito, le classi derivate da <xref:Microsoft.VisualStudio.Shell.DialogPage> estendere il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE tramite l'aggiunta di **opzioni** pagine sotto il **strumenti** menu.  
  
 Oggetto che implementa un determinato **scelta degli strumenti** pagina è associata a VSPackage specifici per il <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> oggetto.  
  
 Poiché l'ambiente di un'istanza dell'oggetto che implementa un particolare **opzioni del menu Strumenti** pagina quando viene visualizzata la pagina specifica dall'IDE:  
  
-   Oggetto **l'opzione strumenti** pagina deve essere implementata nel proprio oggetto e non sull'oggetto che implementa un pacchetto VSPackage.  
  
-   Un oggetto non può implementare più **opzioni del menu Strumenti** pagine.  
  
## <a name="registering-as-a-tools-options-page-provider"></a>La registrazione come Provider di pagina di opzioni di strumenti  
 Configurazione utente VSPackage supporto tramite **opzioni del menu Strumenti** pagine indica gli oggetti che li fornisce **opzioni del menu Strumenti** pagine applicando le istanze di <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> applicato per la <xref:Microsoft.VisualStudio.Shell.Package>implementazione.  
  
 Deve esistere una sola istanza di <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> per ogni <xref:Microsoft.VisualStudio.Shell.DialogPage>-derivato tipo che implementa un **opzioni del menu Strumenti** pagina.  
  
 Ogni istanza di <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> utilizza il tipo che implementa il **opzioni del menu Strumenti** pagina, le stringhe che contengono la categoria e sottocategoria, utilizzato per identificare un **opzioni del menu Strumenti** pagina e delle risorse informazioni per registrare il tipo come fornire un **opzioni del menu Strumenti** pagina.  
  
## <a name="persisting-tools-options-page-state"></a>Salvare in modo permanente lo stato della pagina di opzioni strumenti  
 Se un **opzioni del menu Strumenti** implementazione della pagina è registrato con il supporto di automazione abilitato, l'IDE mantiene lo stato della pagina insieme a tutti gli altri **opzioni del menu Strumenti** pagine.  
  
 Un pacchetto VSPackage può gestire il proprio persistenza tramite <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>. Deve essere utilizzato solo uno o l'altro metodo di persistenza.  
  
## <a name="implementing-dialogpage-class"></a>Classe di implementazione DialogPage  
 Oggetto che fornisce un'implementazione di VSPackage un <xref:Microsoft.VisualStudio.Shell.DialogPage>-tipo derivato può sfruttare le funzionalità ereditate seguenti:  
  
-   Una finestra dell'interfaccia utente predefinito.  
  
-   Oggetto predefinito disponibile il meccanismo di persistenza se <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> viene applicato alla classe, o se il <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> è impostata su `true` per il <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> applicato alla classe.  
  
-   Supporto di automazione.  
  
 Il requisito minimo per un oggetto che implementa un **opzioni del menu Strumenti** pagina <xref:Microsoft.VisualStudio.Shell.DialogPage> è l'aggiunta di proprietà pubbliche.  
  
 Se la classe registrata correttamente come un **opzioni del menu Strumenti** pagina provider, quindi le proprietà pubbliche sono disponibili nel **opzioni** sezione il **strumenti** menu sotto forma di un griglia delle proprietà.  
  
 Tutte queste funzionalità predefinito possono essere sottoposto a override. Ad esempio, per creare un utente più sofisticato interfaccia richiede solo l'override l'implementazione predefinita di <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>.  
  
## <a name="example"></a>Esempio  
 Quello che segue è un'implementazione semplice "hello world" di una pagina di opzioni. Aggiungere il codice seguente a un progetto predefinito creato dal modello di pacchetto di Visual Studio con il **comando di Menu** opzione selezionata in modo adeguato illustrerà funzionalità della pagina opzione.  
  
### <a name="description"></a>Descrizione  
 La classe seguente definisce una pagina di opzioni minimo "hello world". All'apertura, l'utente può impostare pubblico `HelloWorld` proprietà in una griglia delle proprietà.  
  
### <a name="code"></a>Codice  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_1.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_1.vb)]  
  
### <a name="description"></a>Descrizione  
 Applicando l'attributo seguente alla classe del pacchetto rende disponibili le opzioni di pagina quando viene caricato il pacchetto. I numeri sono arbitrari ID di risorsa per la categoria e la pagina e il valore booleano alla fine specifica se la pagina supporta l'automazione.  
  
### <a name="code"></a>Codice  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_2.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_2.vb)]  
  
### <a name="description"></a>Descrizione  
 Il seguente gestore eventi visualizza un risultato in base al valore della proprietà impostata nella pagina delle opzioni. Usa il <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> metodo con il risultato in modo esplicito il cast nel tipo di pagina opzione personalizzata per accedere alle proprietà esposte dalla pagina.  
  
 Nel caso di un progetto generato dal modello di pacchetto, chiamare questa funzione dal `MenuItemCallback` funzione di collegarlo al comando predefinito aggiunto per il **strumenti** menu.  
  
### <a name="code"></a>Codice  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_3.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_3.vb)]  
  
## <a name="see-also"></a>Vedere anche  
 [Opzioni e impostazioni utente estensione](../../extensibility/extending-user-settings-and-options.md)   
 [Supporto dell'automazione per le pagine di opzioni](../../extensibility/internals/automation-support-for-options-pages.md)