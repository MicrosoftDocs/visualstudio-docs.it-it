---
title: Opzioni e le pagine di opzioni | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d85b900779a5df8af077b292b2e2f70b0592e35c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="options-and-options-pages"></a>Opzioni e le pagine di opzioni
Fare clic su **opzioni** sul **strumenti** menu viene aperto il **opzioni** la finestra di dialogo. Le opzioni nella finestra di dialogo vengono definiti collettivamente come pagine Opzioni del menu. Il controllo struttura ad albero nel riquadro di spostamento include le categorie delle opzioni e ogni categoria dispone di pagine Opzioni del menu. Quando si seleziona una pagina, le relative opzioni vengono visualizzati nel riquadro di destra. Queste pagine consentono di modificare i valori delle opzioni che determinano lo stato di un VSPackage.  
  
## <a name="support-for-options-pages"></a>Supporto per le pagine di opzioni  
 La <xref:Microsoft.VisualStudio.Shell.Package> classe offre supporto per la creazione di pagine Opzioni del menu e le categorie di opzioni. La <xref:Microsoft.VisualStudio.Shell.DialogPage> classe implementa una pagina di opzioni.  
  
 L'implementazione predefinita di <xref:Microsoft.VisualStudio.Shell.DialogPage> offre le proprietà pubbliche per un utente in una griglia delle proprietà generica. È possibile personalizzare questo comportamento eseguendo l'override di metodi diversi nella pagina per creare una pagina di opzioni personalizzate con la propria interfaccia utente (UI). Per ulteriori informazioni, vedere [la creazione di una pagina di opzioni](../../extensibility/creating-an-options-page.md).  
  
 Il <xref:Microsoft.VisualStudio.Shell.DialogPage> implementa <xref:Microsoft.VisualStudio.Shell.IProfileManager>, che fornisce la persistenza per le pagine di opzioni e anche per le impostazioni utente. Le implementazioni predefinite del <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> e <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> metodi vengono mantenute le modifiche alle proprietà in una sessione utente del Registro di sistema se la proprietà può essere convertita in e da una stringa.  
  
## <a name="options-page-registry-path"></a>Percorso del Registro di sistema di pagina Opzioni  
 Per impostazione predefinita, il percorso del Registro di sistema di proprietà gestite da una pagina di opzioni viene determinato combinando <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, la parola DialogPage e il nome del tipo della classe della pagina di opzioni. Classe di pagina di opzioni, ad esempio, potrebbe essere definita come segue.  
  
 [!code-csharp[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_1.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_1.vb)]  
  
 Se il <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> è HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, quindi le coppie di nome e il valore di proprietà sono sottochiavi del HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\DialogPage\ Company.OptionsPage.OptionsPageGeneral.  
  
 Il percorso del Registro di sistema della pagina Opzioni viene determinato combinando <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, la parola ToolsOptionsPages e le opzioni di categoria e il nome di pagina. Ad esempio, se la pagina di opzioni personalizzato dispone della categoria, pagine di opzioni personali e <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> è HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, quindi nella pagina Opzioni sono la chiave del Registro di sistema, hkey_local_machine\software\microsoft\. VisualStudio\8.0Exp\ToolsOptionsPages\My opzione Pages\Custom.  
  
## <a name="toolsoptions-page-attributes-and-layout"></a>Gli attributi della pagina di opzioni e il Layout  
 Il <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> attributo determina il raggruppamento delle pagine Opzioni personalizzate in categorie nella struttura ad albero del **opzioni** la finestra di dialogo. Il <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> attributo associa una pagina di opzioni con il pacchetto VSPackage che fornisce l'interfaccia. Si consideri il frammento di codice riportato di seguito.  
  
 [!code-csharp[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_2.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_2.vb)]  
  
 Consente di dichiarare che MyPackage fornisce due pagine di opzioni, OptionsPageGeneral e OptionsPageCustom. Nel **opzioni** la finestra di dialogo, entrambe le opzioni vengono visualizzate nel **My pagine di opzioni** categoria come **generale** e **personalizzata**, rispettivamente.  
  
## <a name="option-attributes-and-layout"></a>Gli attributi di opzione e il Layout  
 L'interfaccia utente (UI) che fornisce la pagina determina l'aspetto delle opzioni in una pagina di opzioni personalizzate. Il layout, l'assegnazione di etichette e la descrizione delle opzioni in una pagina generica di opzioni dipendono dagli attributi seguenti:  
  
-   <xref:System.ComponentModel.CategoryAttribute> Determina la categoria dell'opzione.  
  
-   <xref:System.ComponentModel.DisplayNameAttribute> Determina il nome visualizzato dell'opzione.  
  
-   <xref:System.ComponentModel.DescriptionAttribute> Determina la descrizione dell'opzione.  
  
    > [!NOTE]
    >  Attributi equivalenti, SRCategory, LocDisplayName e SRDescription, utilizzare le risorse stringa per la localizzazione e sono definiti nel [esempio progetto gestito](http://go.microsoft.com/fwlink/?LinkId=122774).  
  
 Si consideri il frammento di codice riportato di seguito.  
  
 [!code-csharp[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_3.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_3.vb)]  
  
 Viene visualizzata nella pagina Opzioni OptionInteger **opzione intero** nel **My Options** categoria. Se l'opzione è selezionata, la descrizione, **l'opzione di numeri interi**, viene visualizzato nella casella Descrizione.  
  
## <a name="accessing-options-pages-from-another-vspackage"></a>L'accesso alle pagine di opzioni da un altro VSPackage  
 Un VSPackage che gestisce una pagina di opzioni a livello di codice accessibile da un altro VSPackage usando il modello di automazione. Nel codice seguente, ad esempio, un VSPackage è registrato come una pagina di opzioni di hosting.  
  
 [!code-csharp[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_4.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_4.vb)]  
  
 Frammento di codice seguente ottiene il valore di OptionInteger da MyOptionPage:  
  
 [!code-csharp[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_5.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_5.vb)]  
  
 Quando il <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> attributo registra una pagina di opzioni, la pagina è registrata con il tasto se AutomationProperties il `SupportsAutomation` argomento dell'attributo è `true`. Automazione esamina questa voce del Registro di sistema per individuare il pacchetto VSPackage associato e automazione quindi accede alla proprietà tramite la pagina di opzioni di hosting, in questo caso, My pagina della griglia.  
  
 Il percorso del Registro di sistema della proprietà di automazione è determinato dalla combinazione <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, la parola AutomationProperties e le opzioni di categoria e il nome di pagina. Ad esempio, se la pagina di opzioni dispone della categoria di categoria personali, il nome My pagina della griglia e <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, quindi la proprietà di automazione con la chiave del Registro di sistema, HKEY_LOCAL_MACHINE\SOFTWARE\ Pagina della griglia di Category\My Microsoft\VisualStudio\8.0Exp\AutomationProperties\My.  
  
> [!NOTE]
>  Il nome canonico, pagina della griglia Category.My personali, è il valore della sottochiave del nome di questa chiave.