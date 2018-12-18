---
title: Distribuzione di applicazioni ClickOnce per il test e i server di produzione senza riapposizione della firma | Documenti Microsoft
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
- ClickOnce applications, deploying without resigning
- ClickOnce deployment, without resigning
- application updates, ClickOnce
- update location [ClickOnce]
- deploymentProvider tag
- manifests [ClickOnce]
ms.assetid: 1218a98d-1ad5-4eef-95dd-0e0b3c44168c
caps.latest.revision: "10"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: ec7265f91d5c202d5885b7f1994aa6f037d6d2ab
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="deploying-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Distribuzione di applicazioni ClickOnce per i server di test e di produzione senza riapposizione della firma
Questo argomento illustra una nuova funzionalità introdotta in .NET Framework versione 3.5 che consente la distribuzione di applicazioni ClickOnce da più posizioni di rete senza riapposizione della firma o la modifica di ClickOnce manifesti ClickOnce.  
  
> [!NOTE]
>  Riapposizione della firma è ancora il metodo preferito per la distribuzione di nuove versioni delle applicazioni. Quando possibile, utilizzare questo metodo. Per altre informazioni, vedere [Mage.exe (Strumento per la generazione e la modifica di manifesti)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).  
  
 Gli sviluppatori di terze parti e gli ISV possono acconsentire esplicitamente a questa funzionalità, rendendo più semplice per aggiornare le proprie applicazioni dei clienti. Questa funzionalità può essere utilizzata nelle situazioni seguenti:  
  
-   Quando si aggiorna un'applicazione, non la prima installazione di un'applicazione.  
  
-   Quando si verifica solo una configurazione dell'applicazione in un computer. Ad esempio, se un'applicazione è configurata per puntare a due database diversi, è possibile utilizzare questa funzionalità.  
  
## <a name="excluding-deploymentprovider-from-deployment-manifests"></a>Esclusione di deploymentProvider dai manifesti della distribuzione  
 In .NET Framework 2.0 e .NET Framework 3.0, qualsiasi applicazione ClickOnce che viene installato nel sistema per la disponibilità offline è necessario specificare un `deploymentProvider` nel manifesto di distribuzione. Il `deploymentProvider` è noto anche come percorso di aggiornamento; è il percorso in cui ClickOnce verifica degli aggiornamenti dell'applicazione. Questo requisito, insieme alla necessità per gli autori di firmare le distribuzioni, rende difficile per un'azienda per aggiornare un'applicazione ClickOnce da un fornitore o di terze parti. Inoltre rende più difficile distribuire l'applicazione stessa da più posizioni nella stessa rete.  
  
 Con le modifiche apportate a ClickOnce in .NET Framework 3.5, è possibile per terze parti fornire un'applicazione ClickOnce in un'altra organizzazione, che è quindi possibile distribuire l'applicazione nella propria rete.  
  
 Per sfruttare i vantaggi di questa funzionalità, è necessario escludere gli sviluppatori di applicazioni ClickOnce `deploymentProvider` dai manifesti di distribuzione. Ciò significa che l'esclusione il `-providerUrl` argomento quando si crea la distribuzione di manifesti con Mage.exe o assicurandosi che il **avviare percorso** casella di testo il **manifesto dell'applicazione** scheda viene lasciata vuota se si sono la generazione di manifesti di distribuzione con MageUI.exe.  
  
## <a name="deploymentprovider-and-application-updates"></a>deploymentProvider e gli aggiornamenti dell'applicazione  
 A partire da .NET Framework 3.5, non è necessario specificare un `deploymentProvider` nel manifesto di distribuzione per distribuire un'applicazione ClickOnce per l'utilizzo online e offline. Supporta lo scenario in cui è necessario creare un pacchetto e firmare la distribuzione, ma consente ad altre società distribuire l'applicazione su reti.  
  
 Il punto importante da ricordare è che le applicazioni che escludono una `deploymentProvider` non è possibile modificare il proprio percorso di installazione durante gli aggiornamenti, fino a che forniscono un aggiornamento che include il `deploymentProvider` nuovo tag.  
  
 Di seguito sono riportati due esempi per chiarire questo concetto. Nel primo esempio, si pubblica un'applicazione ClickOnce che non ha alcun `deploymentProvider` tag e si chiede agli utenti di installarla da http://www.adatum.com/MyApplication/. Se si decide che si desidera pubblicare il successivo aggiornamento dell'applicazione da http://subdomain.adatum.com/MyApplication/, non sarà necessario indicare questo nel manifesto di distribuzione che risiede in http://www.adatum.com/MyApplication/ alcun modo. È possibile eseguire una delle seguenti operazioni:  
  
-   Indicare agli utenti di disinstallare la versione precedente e installare la nuova versione dalla nuova posizione.  
  
-   Includere un aggiornamento in http://www.adatum.com/MyApplication/ che include un `deploymentProvider` che punta a http://www.adatum.com/MyApplication/. Quindi, rilasciare un altro aggiornamento in un secondo momento con `deploymentProvider` che punta a http://subdomain.adatum.com/MyApplication/.  
  
 Nel secondo esempio, si pubblica un'applicazione ClickOnce che specifica `deploymentProvider`, e si decide quindi di rimuoverlo. Una volta la nuova versione senza `deploymentProvider` è stata scaricata ai client, non sarà in grado di reindirizzare il percorso utilizzato per gli aggiornamenti fino a quando non si rilascia una versione dell'applicazione che ha `deploymentProvider` ripristinato. Come con il primo esempio `deploymentProvider` inizialmente deve puntare al percorso di aggiornamento corrente, non al nuovo percorso. In questo caso, se si tenta di inserire un `deploymentProvider` che fa riferimento a http://subdomain.adatum.com/MyApplication/, quindi il successivo aggiornamento avrà esito negativo.  
  
## <a name="creating-a-deployment"></a>Creazione di una distribuzione  
 Per istruzioni dettagliate sulla creazione di distribuzioni che possono essere distribuite da diversi percorsi di rete, vedere [procedura dettagliata: distribuzione manuale di un'applicazione ClickOnce che Does non richiedono nuova firma e che mantiene informazioni sulla personalizzazione](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Mage.exe (Strumento per la generazione e la modifica di manifesti)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [MageUI.exe (Strumento per la generazione e la modifica di manifesti, client grafico)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)