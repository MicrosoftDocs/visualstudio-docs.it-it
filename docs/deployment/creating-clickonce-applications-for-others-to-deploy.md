---
title: Creazione di applicazioni ClickOnce per altri utenti per la distribuzione | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- preserved branding information
- useManifestForTrust element
- customer deployments [ClickOnce]
- multiple ClickOnce deployment and branding
- ClickOnce applications, previous .NET Framework versions
- application manifests [ClickOnce]
- <useManifestForTrust> element
- manifests [ClickOnce]
- trust applications, ClickOnce
- ClickOnce applications, deployed by others
- ClickOnce applications, previous .NET Framework
ms.assetid: d20766c7-4ef3-45ab-8aa0-3f15b61eccaa
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 10f7cf3b6069c80337213283eddd12bdd54e4b7d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="creating-clickonce-applications-for-others-to-deploy"></a>Creazione di applicazioni ClickOnce per la distribuzione da parte di terzi
Non tutti gli sviluppatori che creano distribuzioni ClickOnce prevede di distribuire le applicazioni stesse. Molti di essi solo pacchetto propria applicazione tramite ClickOnce e quindi passare i file a un cliente, ad esempio un'azienda di grandi dimensioni. Il cliente si assume la responsabilità di ospitare l'applicazione nella propria rete. In questo argomento vengono illustrati alcuni problemi relativi a tali distribuzioni nelle versioni di .NET Framework precedenti alla versione 3.5. Viene quindi illustrata una nuova soluzione fornita utilizzando la nuova funzionalità di "Usa manifesto applicazione per l'attendibilità" in .NET Framework 3.5. Vengono infine con strategie consigliate per la creazione di distribuzioni ClickOnce per i clienti che utilizzano ancora versioni precedenti di .NET Framework.  
  
## <a name="issues-involved-in-creating-deployments-for-customers"></a>Problemi relativi alla creazione di distribuzioni per i clienti  
 Alcuni problemi si verificano quando si prevede di fornire una distribuzione a un cliente. Il primo problema riguarda la firma del codice. Per essere distribuita attraverso una rete, il manifesto di distribuzione e manifesto dell'applicazione di una distribuzione di ClickOnce devono essere entrambi firmate con un certificato digitale. Questo genera la domanda se utilizzare il certificato dello sviluppatore o il certificato del cliente per la firma dei manifesti.  
  
 La domanda del certificato da utilizzare è critica, come l'identità dell'applicazione ClickOnce è basato sulla firma digitale del manifesto di distribuzione. Lo sviluppatore firma il manifesto di distribuzione, provocare conflitti se il cliente è un'azienda di grandi dimensioni e più di un reparto della società consente di distribuire una versione personalizzata dell'applicazione.  
  
 Ad esempio Adventure Works dispone di un reparto finanziario e un reparto risorse umane. Entrambi i reparti di licenza di un'applicazione ClickOnce da Microsoft Corporation che genera i report dai dati archiviati in un database SQL. Microsoft fornisce a una versione dell'applicazione personalizzata per i dati di ogni reparto. Se le applicazioni sono firmate con lo stesso certificato Authenticode, un utente che tenta di utilizzare entrambe le applicazioni si verifica un errore, come ClickOnce considera la seconda applicazione identica al primo. In questo caso, il cliente potrebbe subire effetti collaterali imprevisti e indesiderati che includono la perdita di tutti i dati archiviati localmente dall'applicazione.  
  
 Un problema aggiuntivo relativo alla firma del codice è il `deploymentProvider` elemento nel manifesto di distribuzione, che indica di ClickOnce la posizione in cui cercare gli aggiornamenti dell'applicazione. Questo elemento deve essere aggiunto al manifesto di distribuzione prima di firmarlo. Se questo elemento viene aggiunto in seguito, il manifesto di distribuzione deve essere firmato nuovamente.  
  
### <a name="requiring-the-customer-to-sign-the-deployment-manifest"></a>Richiedere il cliente firmare il manifesto di distribuzione  
 Per risolvere questo problema delle distribuzioni non univoco è avere allo sviluppatore di firmare il manifesto dell'applicazione e il cliente firmare il manifesto di distribuzione. Questo approccio funziona, introduce altri problemi. Poiché un certificato Authenticode deve rimanere una risorsa protetta, il cliente non solo di fornire il certificato dello sviluppatore per firmare la distribuzione. Mentre il cliente possa firmare il manifesto di distribuzione se stessi usando gli strumenti disponibili gratuitamente con .NET Framework SDK, tale operazione potrebbe richiedere informazioni più tecniche rispetto al cliente disponibilità o in grado di fornire. In questi casi, lo sviluppatore crea in genere un'applicazione, sito Web o un altro meccanismo tramite cui il cliente può inviare la propria versione dell'applicazione per la firma.  
  
### <a name="the-impact-of-customer-signing-on-clickonce-application-security"></a>L'impatto del cliente di firma per le applicazioni ClickOnce  
 Anche se lo sviluppatore e il cliente accetta che il cliente deve firmare il manifesto dell'applicazione, questa genera altri problemi che racchiudono l'identità dell'applicazione, soprattutto quando si applica a una distribuzione di applicazioni attendibili. (Per ulteriori informazioni su questa funzionalità, vedere [Panoramica della distribuzione di applicazioni attendibili](../deployment/trusted-application-deployment-overview.md).) Si supponga che Adventure Works desidera configurare i computer client in modo che qualsiasi applicazione fornito da Microsoft Corporation viene eseguito con attendibilità totale. Se Adventure Works firma il manifesto di distribuzione, ClickOnce utilizzerà la firma di sicurezza Adventure Work per determinare il livello di attendibilità dell'applicazione.  
  
## <a name="creating-customer-deployments-by-using-application-manifest-for-trust"></a>Creazione di distribuzioni dei clienti con manifesto dell'applicazione per la relazione di Trust  
 ClickOnce in .NET Framework 3.5 contiene una nuova funzionalità che offre agli sviluppatori e ai clienti una nuova soluzione per lo scenario di modalità devono essere firmati i manifesti. Il manifesto dell'applicazione ClickOnce supporta un nuovo elemento denominato `<useManifestForTrust>` che consente agli sviluppatori indicare che la firma digitale del manifesto dell'applicazione è ciò che deve essere utilizzato per prendere decisioni sull'attendibilità. Lo sviluppatore utilizza gli strumenti di creazione di pacchetti di ClickOnce, ad esempio Visual Studio Mage.exe e MageUI.exe, includere l'elemento nel manifesto dell'applicazione, nonché per incorporare il nome del server di pubblicazione sia il nome dell'applicazione nel manifesto.  
  
 Quando si utilizza `<useManifestForTrust>`, il manifesto di distribuzione non deve essere firmato con un certificato Authenticode emesso da un'autorità di certificazione. In alternativa, possono essere firmato con un certificato autofirmato. Un certificato autofirmato generato dal cliente o lo sviluppatore utilizzando strumenti standard di .NET Framework SDK e quindi applicato al manifesto di distribuzione utilizzando gli strumenti di distribuzione ClickOnce standard. Per ulteriori informazioni, vedere [MakeCert](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx).  
  
 Usando un certificato autofirmato per il manifesto di distribuzione presenta molti vantaggi. Eliminando la necessità per il cliente di ottenere o creare il proprio certificato Authenticode, `<useManifestForTrust>` semplifica la distribuzione per il cliente, consentendo allo sviluppatore di mantenere le proprie identità personalizzazione dell'applicazione. Il risultato è un insieme di distribuzioni con segno che sono più sicure e identità di applicazione univoco. In questo modo si evita il potenziale conflitto che può verificarsi dalla distribuzione della stessa applicazione a più clienti.  
  
 Per informazioni dettagliate su come creare una distribuzione di ClickOnce con `<useManifestForTrust>` abilitata, vedere [procedura dettagliata: distribuzione manuale di un'applicazione ClickOnce che Does non richiedono nuova firma e che mantiene informazioni sulla personalizzazione](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md).  
  
### <a name="how-application-manifest-for-trust-works-at-runtime"></a>Manifesto dell'applicazione come per l'attendibilità in fase di esecuzione  
 Per ottenere una migliore comprensione del funzionamento del manifesto dell'applicazione per la relazione di trust in fase di esecuzione, si consideri l'esempio seguente. Un'applicazione ClickOnce destinate a .NET Framework 3.5 è stata creata da Microsoft. Il manifesto dell'applicazione utilizza il `<useManifestForTrust>` elemento e viene firmato da Microsoft. Adventure Works firma il manifesto di distribuzione utilizzando un certificato autofirmato. Adventure Works i client sono configurati per considerare attendibili tutte le applicazioni firmate da Microsoft.  
  
 Quando un utente fa clic su un collegamento al manifesto della distribuzione, ClickOnce installa l'applicazione nei computer dell'utente. Il certificato e sulla distribuzione di identificare in modo univoco l'applicazione ClickOnce nel computer client. Se l'utente tenta di installare di nuovo la stessa applicazione da un percorso diverso, ClickOnce è possibile utilizzare questa identità per stabilire che l'applicazione esiste già nel client.  
  
 Successivamente, ClickOnce esamina il certificato Authenticode che viene utilizzato per firmare il manifesto dell'applicazione, che determina il livello di attendibilità da concedere. Poiché Adventure Works è stato configurato il client per considerare attendibili tutte le applicazioni firmate da Microsoft, l'applicazione ClickOnce viene concessa l'attendibilità totale. Per altre informazioni, vedere [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
## <a name="creating-customer-deployments-for-earlier-versions"></a>Creazione di distribuzioni dei clienti per le versioni precedenti  
 Cosa accade se uno sviluppatore distribuisce le applicazioni ClickOnce per i clienti che utilizzano versioni precedenti di .NET Framework? Le sezioni seguenti riepilogano diverse soluzioni consigliate, con i vantaggi e svantaggi di ognuno.  
  
### <a name="sign-deployments-on-behalf-of-customer"></a>Firmare le distribuzioni per conto cliente  
 Una strategia di distribuzione è per gli sviluppatori creare un meccanismo per firmare le distribuzioni per conto di clienti, tramite la chiave privata del cliente. In questo modo lo sviluppatore non per la gestione delle chiavi private o più pacchetti di distribuzione. Lo sviluppatore fornisce solo la stessa distribuzione per ogni cliente. Spetta al cliente di personalizzarlo con il servizio di firma per il proprio ambiente.  
  
 Uno svantaggio di questo metodo è i tempi e costi necessari per l'implementazione. Mentre tale servizio può essere compilato utilizzando gli strumenti disponibili in .NET Framework SDK, vengono aggiunti più tempo di sviluppo al ciclo di vita del prodotto.  
  
 Come notato in precedenza in questo argomento, un altro svantaggio è che la versione di ciascun cliente dell'applicazione avrà la stessa identità di applicazione, che potrebbe provocare conflitti. Se si tratta di un problema, lo sviluppatore può modificare il campo nome che viene utilizzato quando si genera il manifesto di distribuzione per assegnare un nome univoco a ogni applicazione. Verrà creata un'identità distinta per ogni versione dell'applicazione ed eliminare qualsiasi potenziale conflitto di identità. Questo campo corrisponde alla `-Name` argomento di Mage.exe e al **nome** nel campo di **nome** scheda in MageUI.exe.  
  
 Ad esempio, che lo sviluppatore ha creato un'applicazione denominata Application1. Anziché creare un'unica distribuzione con il campo nome impostato su Application1, lo sviluppatore può creare diverse distribuzioni con una variante di specifiche del cliente per questo nome, ad esempio Application1 ClienteA, Application1-ClienteB e così via.  
  
### <a name="deploy-using-a-setup-package"></a>Distribuire mediante un pacchetto di installazione  
 Una strategia di distribuzione possibili secondo consiste nel generare un progetto Microsoft Setup per eseguire la distribuzione iniziale dell'applicazione ClickOnce. Questo può essere fornito in uno dei diversi formati: in una distribuzione MSI, come un programma di installazione eseguibile (. File EXE) o come file cabinet (CAB) insieme a uno script batch.  
  
 Utilizzando questa tecnica, lo sviluppatore fornisce al cliente una distribuzione che include i file dell'applicazione, il manifesto dell'applicazione e un manifesto di distribuzione che funge da un modello. Il cliente esegue il programma di installazione, che richiede un URL di distribuzione (il server o condivisione percorso da cui gli utenti installeranno l'applicazione ClickOnce file), nonché un certificato digitale. L'applicazione di installazione può anche scegliere per la richiesta di ulteriori opzioni di configurazione di ClickOnce, ad esempio di intervallo di controllo di aggiornamento. Quando queste informazioni vengono raccolte, il programma di installazione potrebbe generare il manifesto di distribuzione reale, firmarlo e pubblicare l'applicazione ClickOnce nel percorso server designato.  
  
 Esistono tre modi che il cliente possa firmare il manifesto di distribuzione in questa situazione:  
  
1.  Il cliente può utilizzare un certificato valido emesso da un'autorità di certificazione (CA).  
  
2.  Una variante di questo approccio, il cliente può scegliere firmare il manifesto di distribuzione con un certificato autofirmato. Lo svantaggio è che ciò comporterà l'applicazione visualizzare le parole "Autore sconosciuto" quando l'utente viene chiesto di installarlo. Tuttavia, il vantaggio è che impedisce ai clienti più piccoli di dover dedicare tempo e denaro richiesto per un certificato emesso da un'autorità di certificazione.  
  
3.  Infine, lo sviluppatore può includere il proprio certificato autofirmato nel pacchetto di installazione. In questo modo i potenziali problemi con l'identità dell'applicazione descritti precedentemente in questo argomento.  
  
 Lo svantaggio di metodo di installazione distribuzione progetto è il tempo e costi necessari per compilare un'applicazione di distribuzione personalizzata.  
  
### <a name="have-customer-generate-deployment-manifest"></a>Cliente generare il manifesto di distribuzione  
 Una terza strategia di distribuzione è passare solo il file dell'applicazione e il manifesto dell'applicazione disattivata al cliente. In questo scenario, il cliente è responsabile per l'utilizzo di .NET Framework SDK per generare e firmare il manifesto di distribuzione.  
  
 Lo svantaggio di questo metodo è che richiede il cliente di installare gli strumenti di .NET Framework SDK e disporre di uno sviluppatore o un amministratore di sistema utilizzarli. Alcuni clienti potrebbero richiedere una soluzione che richiede poco o non necessarie competenze tecniche questa parte.  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuzione di applicazioni ClickOnce per il test e i server di produzione senza riapposizione della firma](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md)   
 [Procedura dettagliata: Distribuzione manuale di un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [Procedura dettagliata: distribuzione manuale di una applicazione ClickOnce che non richiede una nuova firma e mantiene le informazioni di personalizzazione](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md)