---
title: Sicurezza dall'accesso di codice per applicazioni ClickOnce | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vb.XBAPProjectPropertiesSecurity.HowTo
- vb.XBAProjectPropertiesSecurity.HowTo
- vb.ProjectPropertiesSecurity.HowTo
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], security
- ClickOnce applications, caspol
- security [ClickOnce], WPF browser-hosted applications
- security [ClickOnce], ClickOnce applications
- ClickOnce applications, code access security policies
- security, ClickOnce
ms.assetid: 04b104d0-0bd3-4ccb-b164-1de92d234487
caps.latest.revision: "31"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: e4897ad027354ef54a77fdad3488d2e623264741
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="code-access-security-for-clickonce-applications"></a>Sicurezza dall'accesso di codice per applicazioni ClickOnce
Le applicazioni ClickOnce sono basate sul Framework .NET e sono soggette a vincoli di sicurezza per l'accesso al codice. Per poter scrivere correttamente le applicazioni ClickOnce è quindi importante comprendere le implicazioni di questo tipo di sicurezza.  
  
 La sicurezza dall’accesso di codice è un meccanismo di .NET Framework che consente di limitare l'accesso del codice alle risorse e alle operazioni protette. È necessario configurare le autorizzazioni per la sicurezza dell'accesso di codice per l'applicazione ClickOnce per usare l'area appropriata per la posizione del programma di installazione delle applicazioni. Nella maggior parte dei casi è possibile scegliere l'area **Internet** per un set di autorizzazioni limitato oppure l'area **Intranet locale** per un set di autorizzazioni più esteso.  
  
## <a name="default-clickonce-code-access-security"></a>Sicurezza dell'accesso di codice ClickOnce predefinita  
 Per impostazione predefinita, l'applicazione ClickOnce riceve autorizzazioni di attendibilità totale quando è installata o eseguita in un computer client.  
  
-   Un'applicazione con autorizzazioni di attendibilità totale ha un accesso illimitato alle risorse, ad esempio al file system e al registro. L'applicazione (e il sistema dell'utente finale) diventa però potenzialmente vulnerabile e potrebbe essere sfruttata da codice dannoso.  
  
-   Quando un'applicazione richiede autorizzazioni di attendibilità totale, è possibile che all'utente finale sia richiesto di concedere le autorizzazioni all'applicazione. Ciò significa che l'applicazione non fornisce effettivamente un'esperienza ClickOnce e, potenzialmente, la richiesta potrebbe confondere gli utenti meno esperti.  
  
    > [!NOTE]
    >  Quando si installa un'applicazione da un supporto rimovibile come un CD-ROM, non vengono inviate richieste all'utente. Inoltre, un amministratore di rete può configurare dei criteri di rete in modo che agli utenti non vengano inviate richieste quando installano un'applicazione da un'origine attendibile. Per altre informazioni, vedere [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
 Per limitare le autorizzazioni per un'applicazione ClickOnce, è possibile modificare le autorizzazioni per la sicurezza dell'accesso di codice per l'applicazione in modo da richiedere l'area più appropriata per le autorizzazioni necessarie all'applicazione. Nella maggior parte dei casi è possibile selezionare l'area da cui viene distribuita l'applicazione. Ad esempio, se l'applicazione è di tipo aziendale, è possibile usare l'area **Intranet locale** . Se l'applicazione è di tipo Internet, è possibile usare l'area **Internet** .  
  
## <a name="configuring-security-permissions"></a>Configurazione delle autorizzazioni di sicurezza  
 È sempre necessario configurare l'applicazione ClickOnce per richiedere l'area appropriata per limitare le autorizzazioni per la sicurezza dell'accesso di codice. È possibile configurare le autorizzazioni di sicurezza nella pagina **Sicurezza** di **Creazione progetti**.  
  
 La pagina **Sicurezza** in **Creazione progetti** contiene una casella di controllo **Abilita impostazioni di sicurezza ClickOnce** . Quando questa casella di controllo è selezionata, le richieste di autorizzazioni di sicurezza vengono aggiunte al manifesto della distribuzione per l'applicazione. Al momento dell'installazione all'utente verrà richiesto di concedere le autorizzazioni se le autorizzazioni richieste superano quelle predefinite per l'area da cui viene distribuita l'applicazione. Per altre informazioni, vedere [How to: Enable ClickOnce Security Settings](../deployment/how-to-enable-clickonce-security-settings.md).  
  
 Alle applicazioni distribuite da posizioni diverse vengono concessi livelli diversi di autorizzazioni senza richiesta di conferma. Ad esempio, se un'applicazione viene distribuita da Internet, riceve un set di autorizzazioni molto limitato. Se viene installata da una Intranet locale riceve un maggior numero di autorizzazioni, mentre se viene installata da CD-ROM riceve autorizzazioni di attendibilità totale.  
  
 Come punto di partenza per la configurazione delle autorizzazioni, è possibile selezionare un'area di sicurezza dall'elenco **Area** nella pagina **Sicurezza** . Se l'applicazione potrebbe essere potenzialmente distribuita da più aree, selezionare l'area con il minor numero di autorizzazioni. Per altre informazioni, vedere [How to: Set a Security Zone for a ClickOnce Application](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md).  
  
 Le proprietà che è possibile impostare variano in base al set di autorizzazioni. Non tutti i set di autorizzazioni dispongono di proprietà configurabili. Per altre informazioni sull'elenco completo di autorizzazioni che l'applicazione può richiedere, vedere <xref:System.Security.Permissions>. Per altre informazioni su come impostare le autorizzazioni per una zona personalizzata, vedere [How to: Set Custom Permissions for a ClickOnce Application](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).  
  
## <a name="debugging-an-application-that-has-restricted-permissions"></a>Debug di un'applicazione con autorizzazioni limitate  
 È probabile che uno sviluppatore usi le autorizzazioni di attendibilità totale nel computer di sviluppo. Quindi, quando esegue il debug dell'applicazione, non visualizzerà le stesse eccezioni di sicurezza visualizzate dagli utenti quando eseguono la stessa operazione con autorizzazioni limitate.  
  
 Per rilevare queste eccezioni, è necessario eseguire il debug dell'applicazione con le stesse autorizzazioni dell'utente finale. Il debug con autorizzazioni limitate può essere abilitato nella pagina **Sicurezza** di **Creazione progetti**.  
  
 Quando si esegue il debug di un'applicazione con autorizzazioni limitate, vengono generate eccezioni per ogni richiesta di sicurezza del codice non abilitata nella pagina **Sicurezza** . Viene visualizzato un supporto eccezioni che fornisce suggerimenti su come modificare il codice per evitare l'eccezione.  
  
 Inoltre, quando si scrive codice, la funzionalità IntelliSense nell'editor del codice disabilita tutti i membri non inclusi nelle autorizzazioni di sicurezza configurate.  
  
 Per altre informazioni, vedere [How to: Debug a ClickOnce Application with Restricted Permissions](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md).  
  
## <a name="security-permissions-for-browser-hosted-applications"></a>Autorizzazioni di sicurezza per applicazioni ospitate da browser  
 Visual Studio fornisce i seguenti tipi di progetto per le applicazioni Windows Presentation Foundation (WPF):  
  
-   Applicazione Windows WPF  
  
-   Applicazione Web Browser WPF  
  
-   Libreria di controlli personalizzati WPF  
  
-   Libreria di servizi WPF  
  
 Di questi tipi di progetto, solo le applicazioni Web Browser WPF vengono ospitate in un Web browser e richiedono quindi impostazioni speciali di distribuzione e sicurezza. Le impostazioni di sicurezza predefinite per queste applicazioni sono le seguenti:  
  
-   **Abilita impostazioni di sicurezza ClickOnce**  
  
-   **È un'applicazione parzialmente attendibile**  
  
-   **Area Internet** (con l'autorizzazione predefinita impostata per le applicazioni Web browser WPF selezionata)  
  
 Nella finestra di dialogo **Impostazioni di sicurezza avanzate** la casella di controllo **Esegui debug dell'applicazione con il set di autorizzazioni selezionato** è selezionata e disabilitata. Il debug nell'area, infatti, non può essere disattivato per le applicazioni ospitate da browser.  
  
## <a name="see-also"></a>Vedere anche  
 [Protezione di applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)   
 [How to: Enable ClickOnce Security Settings](../deployment/how-to-enable-clickonce-security-settings.md)  (Procedura: Abilitare le impostazioni di sicurezza ClickOnce)  
 [Procedura: impostare un'area di sicurezza per un'applicazione ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Procedura: impostare le autorizzazioni personalizzate per un'applicazione ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Procedura: eseguire il debug di un'applicazione ClickOnce con autorizzazioni limitate](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Cenni preliminari sulla distribuzione di applicazioni attendibili](../deployment/trusted-application-deployment-overview.md)   
 [Pagina Sicurezza, Creazione progetti](../ide/reference/security-page-project-designer.md)