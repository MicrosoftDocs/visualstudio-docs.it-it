---
title: Progetto di tipo Essentials | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 899d2758be1561d9b5fbda3280230333cc0ac8a3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="project-type-essentials"></a>Essentials tipo di progetto
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]include diversi tipi di progetto per lingue quali [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] o [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]consente anche di creare i propri tipi di progetto.  
  
 Se si desidera aggiungere comandi personalizzati, editor o finestre degli strumenti di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], è possibile farlo senza creare un nuovo tipo di progetto. Per altre informazioni, vedere i seguenti argomenti:  
  
-   [Comandi, menu e barre degli strumenti](../../extensibility/internals/commands-menus-and-toolbars.md)  
  
-   [Estensioni dell'editor e dei servizi di linguaggio](../../extensibility/editor-and-language-service-extensions.md)  
  
-   [Estensione e personalizzazione delle finestre degli strumenti](../../extensibility/extending-and-customizing-tool-windows.md)  
  
 Analogamente, se si desidera personalizzare il comportamento del metodo [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] tipi di progetto, è possibile eseguire quindi l'uso sottotipi di progetto. Per ulteriori informazioni, vedere [sottotipi di progetto](../../extensibility/internals/project-subtypes.md).  
  
 È necessario creare un nuovo tipo di progetto per i progetti che sono basate su un linguaggio diverso da [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] se si desidera supportare uno o più delle operazioni seguenti:  
  
-   Compilazione  
  
-   Distribuzione  
  
-   Configurazioni multiple  
  
-   Controllo del codice sorgente  
  
-   Debug  
  
-   Elementi di progetto in Esplora soluzioni  
  
-   Il **Apri progetto** o **nuovo progetto** finestre di dialogo  
  
-   Nidificazione di progetto  
  
-   Per ulteriori informazioni sulle funzionalità dei tipi di progetto, vedere gli argomenti seguenti:  
  
-   Tipi di progetto sono oggetti di un VSPackage che implementano il set di interfacce [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prevista. Se si utilizza c# per lo sviluppo di un tipo di progetto, le classi di progetto del Framework di pacchetto gestito implementano le interfacce necessarie per l'utente e consentono di eredita tale implementazione. Per ulteriori informazioni, vedere [utilizzando il Framework di pacchetto gestito per implementare un tipo di progetto (c#)](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md).  
  
-   Per gli sviluppatori di C++, le classi nella libreria HierUtil funzionano in modo simile. Per ulteriori informazioni, vedere [non incluso nella Build: utilizzo di classi di progetto HierUtil7 per implementare un tipo di progetto (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346).  
  
-   Tipi di progetto possono supportare dati diversi dai file del codice sorgente tipico che compila in un assembly .exe o DLL. Ad esempio, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] progetti di database contengono riferimenti a script e query file archiviati su disco e aggiungere comandi a **Esplora** per eseguire gli script e query su un database, ma i progetti non supportano comportamento di compilazione. Per ulteriori informazioni, vedere [di apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md).  
  
-   Un tipo di progetto non è necessario utilizzare i file. Ad esempio, un tipo di progetto potrebbe archiviare tutti i relativi dati in un database. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Fornisce tipi di progetto di controllo completo sulla modalità cui conservare i dati per progetti ed elementi di progetto. Per ulteriori informazioni, vedere [decisioni di progettazione di tipo di progetto](../../extensibility/internals/project-type-design-decisions.md).  
  
-   Tipi di progetto è necessario fornire un *factory del progetto*, che è un oggetto che crea un'istanza del progetto digitare ogni volta che [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] viene informato di aprire o creare un progetto basato su tale tipo di progetto. Per ulteriori informazioni, vedere [la creazione di istanze da utilizzando progetto factory dei progetti](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
-   Tipi di progetto è necessario specificare modelli per progetti ed elementi di progetto. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]utilizza i modelli quando si creano nuovi progetti e aggiungere nuovi elementi a progetti esistenti. Per ulteriori informazioni, vedere [aggiunta di progetto e i modelli di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
-   Tipi di progetto possono supportare più configurazioni, ad esempio Debug e rilascio. Gli utenti possono modificare le configurazioni diverse di un progetto tramite pagine delle proprietà specificate. Per ulteriori informazioni, vedere [la gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuzione dei tipi di progetto](../../extensibility/internals/deploying-project-types.md)