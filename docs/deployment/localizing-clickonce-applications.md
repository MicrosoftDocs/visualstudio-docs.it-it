---
title: Localizzazione di applicazioni ClickOnce | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- WPF, ClickOnce applications
- ClickOnce deployment, globalization
- deploying applications [ClickOnce], localizing ClickOnce applications
- localization, ClickOnce deployment
- ClickOnce deployment, download on-demand
- ClickOnce deployment, localization
- Windows Forms, ClickOnce applications
- console applications, ClickOnce applications
ms.assetid: c92b193b-054d-4923-834b-d4226a4c7a1a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c3d7ebc762c7b1feb895323f7ef9ee0180ce954e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="localizing-clickonce-applications"></a>Localizzazione delle applicazioni ClickOnce
La localizzazione è il processo di adattamento di un'applicazione a impostazioni cultura specifiche. Questo processo consiste nel tradurre il testo dell'interfaccia utente in una lingua specifica di un paese/area geografica, usare la formattazione di data e valuta corretta, regolare la dimensione dei controlli di un form e, se necessario, eseguire il mirroring dei controlli da destra verso sinistra.  
  
 La localizzazione di un'applicazione comporta la creazione di uno o più assembly satellite. In ogni assembly sono contenute stringhe dell'interfaccia utente, immagini e altre risorse specifiche di determinate impostazioni cultura. Nel file eseguibile principale dell'applicazione sono contenute le stringhe delle impostazioni cultura predefinite dell'applicazione.  
  
 Questo argomento descrive tre modi in cui è possibile distribuire un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] per altre impostazioni cultura:  
  
-   Includere tutti gli assembly satellite in una sola distribuzione.  
  
-   Generare una distribuzione per le singole impostazioni cultura, con un solo assembly satellite incluso in ognuna di esse.  
  
-   Scaricare gli assembly satellite su richiesta.  
  
## <a name="including-all-satellite-assemblies-in-a-deployment"></a>Inclusione di tutti gli assembly satellite in una sola distribuzione  
 Anziché pubblicare più distribuzioni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], è possibile pubblicare una sola distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] contenente tutti gli assembly satellite.  
  
 Questo metodo rappresenta il metodo predefinito in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Per usarlo in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] non è necessario effettuare operazioni aggiuntive.  
  
 Per utilizzare questo metodo con MageUI.exe, è necessario impostare le impostazioni cultura per l'applicazione da **neutro** in MageUI.exe. e quindi includere manualmente tutti gli assembly satellite nella distribuzione. In MageUI.exe, è possibile aggiungere gli assembly satellite tramite il **Popola** pulsante il **file** scheda del manifesto dell'applicazione.  
  
 Il vantaggio di questo approccio è dato dalla possibilità di creare un'unica distribuzione e di semplificare il processo della distribuzione localizzata. In fase di esecuzione verrà usato l'assembly satellite appropriato, a seconda delle impostazioni cultura predefinite del sistema operativo Windows dell'utente. L'inconveniente di questo approccio riguarda il fatto che, ogni volta che l'applicazione viene installata o aggiornata in un computer client, vengono scaricati tutti gli assembly satellite. Se nell'applicazione è contenuto un numero elevato di stringhe o i clienti hanno una connessione di rete lenta, questo processo può influire sulle prestazioni durante l'aggiornamento dell'applicazione.  
  
> [!NOTE]
>  Con questo approccio si presuppone che l'applicazione regoli automaticamente l'altezza, la larghezza e la posizione dei controlli per adattare dimensioni diverse delle stringhe di testo nelle varie impostazioni cultura. In Windows Form è disponibile un'ampia gamma di controlli e tecnologie che consentono di progettare il form in modo da facilitarne la localizzazione, inclusi i controlli <xref:System.Windows.Forms.FlowLayoutPanel> e <xref:System.Windows.Forms.TableLayoutPanel> e la proprietà <xref:System.Windows.Forms.Control.AutoSize%2A>.  Vedere anche [procedura: supportare la localizzazione in Windows Form usando AutoSize e il controllo TableLayoutPanel](http://msdn.microsoft.com/library/1zkt8b33\(v=vs.110\)).  
  
## <a name="generate-one-deployment-for-each-culture"></a>Generare una distribuzione per le singole impostazioni cultura  
 In questa strategia di distribuzione vengono generate più distribuzioni. In ogni distribuzione viene incluso solo l'assembly satellite necessario per impostazioni cultura specifiche e la distribuzione viene contrassegnata come specifica di tali impostazioni cultura.  
  
 Utilizzare questo metodo in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], impostare il **lingua di pubblicazione** proprietà il **pubblica** scheda per la regione desiderata. L'assembly satellite richiesto per il paese/area geografica selezionato verrà incluso automaticamente in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e tutti gli altri assembly satellite verranno esclusi dalla distribuzione.  
  
 Questa stessa operazione può essere eseguita con lo strumento MageUI.exe in Microsoft [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Utilizzare il **Popola** pulsante il **file** scheda del manifesto dell'applicazione per escludere tutti gli altri assembly satellite dalla directory dell'applicazione, quindi impostare il **delle impostazioni cultura**nel campo di **nome** scheda per il manifesto di distribuzione in MageUI.exe. Questi passaggi non consentono solo di includere l'assembly satellite corretto, ma anche di impostare l'attributo `language` dell'elemento `assemblyIdentity` nel manifesto della distribuzione sul valore delle impostazioni cultura corrispondenti.  
  
 Dopo aver pubblicato l'applicazione, è necessario ripetere questo passaggio per tutte le impostazioni cultura aggiuntive supportate dall'applicazione. È necessario assicurarsi che la pubblicazione in una directory del server Web diversa o una directory di condivisione file ogni volta, perché ogni manifesto dell'applicazione farà riferimento a un assembly satellite diverso e ogni manifesto di distribuzione avrà un valore diverso per il `language`attributo.  
  
## <a name="downloading-satellite-assemblies-on-demand"></a>Download di assembly satellite su richiesta  
 Se si decide di includere tutti gli assembly satellite in un'unica distribuzione, è possibile migliorare le prestazioni usando il download su richiesta, che consente di contrassegnare gli assembly come facoltativi. Gli assembly contrassegnati non verranno scaricati quando viene installata o aggiornata l'applicazione. Sarà possibile installarli in qualunque momento chiamando il metodo <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> nella classe <xref:System.Deployment.Application.ApplicationDeployment>.  
  
 Il download degli assembly satellite su richiesta differisce leggermente dal download degli altri tipi di assembly su richiesta. Per ulteriori informazioni ed esempi di codice su come abilitare questo scenario di utilizzo di [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] di strumenti per [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], vedere [procedura dettagliata: download di assembly Satellite su richiesta con l'API della distribuzione ClickOnce](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md).  
  
 Questo scenario può essere attivato anche in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Vedere anche [Procedura dettagliata: Download di assembly satellite su richiesta con l'API della distribuzione ClickOnce tramite la finestra di progettazione](http://msdn.microsoft.com/library/ms366788\(v=vs.110\)) o [Procedura dettagliata: Download di assembly satellite su richiesta con l'API della distribuzione ClickOnce tramite la finestra di progettazione](http://msdn.microsoft.com/library/ms366788\(v=vs.120\)).  
  
## <a name="testing-localized-clickonce-applications-before-deployment"></a>Verifica delle applicazioni ClickOnce localizzate prima della distribuzione  
 Un assembly satellite verrà usato per un'applicazione Windows Form solo se la proprietà <xref:System.Threading.Thread.CurrentUICulture%2A> per il thread principale dell'applicazione è impostata sulle impostazioni cultura dell'assembly satellite. È probabile che i clienti nei mercati locali eseguano già una versione localizzata di Windows con il valore predefinito appropriato specificato per le impostazioni cultura.  
  
 Sono disponibili tre opzioni per la verifica delle distribuzioni localizzate prima di rendere disponibile l'applicazione ai clienti:  
  
-   È possibile eseguire l'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nelle versioni localizzate appropriate di Windows.  
  
-   È possibile impostare la proprietà <xref:System.Threading.Thread.CurrentUICulture%2A> a livello di codice nell'applicazione. Questa proprietà deve essere impostata prima di chiamare il metodo <xref:System.Windows.Forms.Application.Run%2A>.  
  
## <a name="see-also"></a>Vedere anche  
 [\<assemblyIdentity > elemento](../deployment/assemblyidentity-element-clickonce-deployment.md)   
 [Sicurezza e distribuzione di ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Globalizzazione di Windows Form](/dotnet/framework/winforms/advanced/globalizing-windows-forms)