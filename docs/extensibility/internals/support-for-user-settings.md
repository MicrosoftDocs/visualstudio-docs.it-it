---
title: Supporto per le impostazioni utente | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Custom Settings Points
- user settings [Visual Studio SDK], registering persistence support
- persistence, registering settings
ms.assetid: ad9beac3-4f8d-4093-ad0e-6fb00444a709
caps.latest.revision: "26"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: de3fc9b6edb3b916162a1beb34fb716d5c2adaa4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="support-for-user-settings"></a>Supporto per le impostazioni utente
Un pacchetto VSPackage può definire una o più categorie di impostazioni, che sono gruppi di variabili di stato che vengono mantenute quando un utente sceglie il **Importa/Esporta impostazioni** comando il **strumenti** menu. Per abilitare la persistenza, utilizzare le impostazioni API nel [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].  
  
 Una voce del Registro di sistema cui fa riferimento come un punto di impostazioni personalizzato e un GUID definisce la categoria di impostazioni di un pacchetto VSPackage. Un pacchetto VSPackage può supportare più categorie di impostazioni, ognuno definito da un punto di impostazioni personalizzato.  
  
-   Le implementazioni di impostazioni che si basano sugli assembly di interoperabilità (utilizzando la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> interface) deve creare un punto di impostazioni personalizzato del Registro di sistema oppure utilizzando uno script di registrazione (file con estensione RGS). Per ulteriori informazioni, vedere [la creazione di script di registrazione](/cpp/atl/creating-registrar-scripts).  
  
-   Il codice che utilizza il Framework di pacchetto gestito (MPF) debba creare punti di impostazioni personalizzati collegando un <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> al pacchetto VSPackage per ogni punto di impostazioni personalizzato.  
  
     Se un singolo VSPackage supporta diversi punti di impostazioni personalizzato, ogni punto di impostazioni personalizzato viene implementato da una classe separata e ciascuno viene registrato da un'istanza univoca del <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> classe. Di conseguenza, le impostazioni di un classe di implementazione possono supportare più di una categoria di impostazioni.  
  
## <a name="custom-settings-point-registry-entry-details"></a>Dettagli delle voci del Registro di sistema di punto di impostazioni personalizzate  
 Punti di impostazioni personalizzati vengono creati in una voce del Registro di sistema nel percorso seguente: HKLM\Software\Microsoft\VisualStudio\\*\<versione >*\UserSettings\\`<CSPName>`, dove `<CSPName>` è il nome del punto di impostazioni personalizzato supporta il pacchetto VSPackage e  *\<versione >* è la versione di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], ad esempio 8.0.  
  
> [!NOTE]
>  Il percorso radice dell'HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<versione >* può essere sostituito con un'alternativa radice quando il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE) inizializzato. Per ulteriori informazioni, vedere [opzioni della riga di comando](../../extensibility/command-line-switches-visual-studio-sdk.md).  
  
 Di seguito è illustrata la struttura della voce del Registro di sistema:  
  
 HKLM\Software\Microsoft\VisualStudio\\*\<versione >*\UserSettings\  
  
 `<CSPName`> = '#12345' s  
  
 Pacchetto = '{XXXX XXXXXX XXXX XXXX XXXXXXXXX}'  
  
 Categoria = '{aaaa YYYYYY gg aaaa YYYYYYYYY}'  
  
 ResourcePackage = '{ZZZZZZ ZZZZ ZZZZ ZZZZ ZZZZZZZZZ}'  
  
 AlternateParent = CategoryName  
  
|nome|Tipo|Dati|Descrizione|  
|----------|----------|----------|-----------------|  
|(Predefinito)|REG_SZ|Nome del punto di impostazioni personalizzato|Il nome della chiave, `<CSPName`>, è il nome non localizzato del punto di impostazioni personalizzato.<br /><br /> Per le implementazioni in base a MPF, il nome della chiave viene ottenuto combinando il `categoryName` e `objectName` gli argomenti del <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> costruttore in `categoryName_objectName`.<br /><br /> La chiave può essere vuota o può contenere l'ID di riferimento per la stringa localizzata in una DLL satellite. Questo valore viene ottenuto dal `objectNameResourceID` argomento per il <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> costruttore.|  
|Pacchetto|REG_SZ|GUID|Il GUID del pacchetto VSPackage che implementa il punto di impostazioni personalizzato.<br /><br /> Le implementazioni basata sull'utilizzo di MPF il <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> classe, utilizzare il costruttore `objectType` argomento che contiene il pacchetto VSPackage <xref:System.Type> e reflection per ottenere questo valore.|  
|Category|REG_SZ|GUID|GUID che identifica la categoria di impostazioni.<br /><br /> Per le implementazioni in base alle assembly di interoperabilità, questo valore può essere un scelto arbitrariamente GUID, che il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE passa al <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> metodi. Tutte le implementazioni di questi due metodi è necessario verificare i relativi argomenti di tipo GUID.<br /><br /> Per le implementazioni in base a MPF questo GUID è ottenuto il <xref:System.Type> di classe che implementa il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] meccanismo delle impostazioni.|  
|ResourcePackage|REG_SZ|GUID|Facoltativo.<br /><br /> Percorso satellite DLL contenente localizzata stringhe se non fornisce l'implementazione di VSPackage.<br /><br /> MPF utilizza la reflection per ottenere la risorsa corretta VSPackage, pertanto la <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> classe non viene impostato questo argomento.|  
|AlternateParent|REG_SZ|Nome della cartella sotto la pagina di opzioni del menu Strumenti che contiene il punto di impostazioni personalizzato.|Facoltativo.<br /><br /> È necessario impostare questo valore solo se supporta un'implementazione delle impostazioni **opzioni del menu Strumenti** pagine che utilizzano il meccanismo di persistenza di [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] anziché il meccanismo nel modello di automazione per salvare lo stato.<br /><br /> In questi casi, il valore della chiave AlternateParent è il `topic` sezione la `topic.sub-topic` stringa utilizzata per identificare la particolare **Options** pagina. Ad esempio, per il **Options** pagina `"TextEditor.Basic"` sarebbe il valore di AlternateParent `"TextEditor"`.<br /><br /> Quando <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> il punto di impostazioni personalizzato, viene generato l'errore è identico al nome di categoria.|