---
title: "Procedura: gestire gli aggiornamenti per un'applicazione ClickOnce | Microsoft Docs"
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.Update
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, managing applications
- ClickOnce deployment, updates
- updating data, ClickOnce
- application updates
ms.assetid: a3f23f05-e7f1-4620-b23c-2d68f9643684
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 30a02c4b438d6e7504056ce5cdcc06bfc129d218
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/19/2018
ms.locfileid: "39151588"
---
# <a name="how-to-manage-updates-for-a-clickonce-application"></a>Procedura: gestire gli aggiornamenti per un'applicazione ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] le applicazioni possono cercare gli aggiornamenti automaticamente o a livello di codice. Gli sviluppatori, è necessario un numero elevato di flessibilità nello specificare come e quando vengono eseguiti controlli di aggiornamento, se gli aggiornamenti sono obbligatori e in cui controllare la disponibilità di aggiornamenti.  
  
 È possibile configurare l'applicazione per cercare gli aggiornamenti automaticamente prima dell'avvio dell'applicazione o a intervalli prestabiliti dopo l'avvio dell'applicazione. È inoltre possibile specificare una versione minima richiesta. vale a dire, viene installato un aggiornamento se la versione dell'utente è inferiore alla versione richiesta.  
  
 È possibile configurare l'applicazione per cercare gli aggiornamenti a livello di programmazione basati su un evento, ad esempio una richiesta dell'utente. La procedura "per cercare gli aggiornamenti a livello di programmazione" in questo argomento viene illustrato come scrivere codice che usa il <xref:System.Deployment.Application.ApplicationDeployment> classe per cercare gli aggiornamenti in base a un evento.  
  
 È anche possibile distribuire l'applicazione da un'unica posizione e aggiornarlo da un altro. Vedere la procedura "per"specificare un percorso diverso.  
  
 Per altre informazioni, vedere [scelta di una strategia di aggiornamento ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
 Comportamento di aggiornamento viene gestito nel **gli aggiornamenti dell'applicazione** della finestra di dialogo disponibile dal **Publish** pagina del **Progettazione progetti.**  
  
### <a name="to-check-for-updates-before-the-application-starts"></a>Per cercare gli aggiornamenti prima dell'avvio dell'applicazione  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Scegliere il **pubblica** scheda.  
  
3.  Fare clic sul **aggiornamenti** per aprire il **gli aggiornamenti dell'applicazione** nella finestra di dialogo.  
  
4.  Nel **gli aggiornamenti dell'applicazione** finestra di dialogo, assicurarsi che le **controllare la disponibilità di aggiornamenti** casella di controllo è selezionata.  
  
5.  Nel **scegliere quando controllare la disponibilità di aggiornamenti** sezione, selezionare **prima dell'avvio dell'applicazione**. Ciò garantisce che gli utenti connessi alla rete sempre eseguono l'applicazione con gli aggiornamenti più recenti.  
  
### <a name="to-check-for-updates-in-the-background-after-the-application-starts"></a>Per cercare gli aggiornamenti in background dopo l'avvio dell'applicazione  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Scegliere il **pubblica** scheda.  
  
3.  Fare clic sul **aggiornamenti** per aprire il **gli aggiornamenti dell'applicazione** nella finestra di dialogo.  
  
4.  Nel **gli aggiornamenti dell'applicazione** finestra di dialogo, assicurarsi che la casella di controllo **controllare la disponibilità di aggiornamenti** sia selezionata.  
  
5.  Nel **scegliere quando controllare la disponibilità di sezione aggiornamenti**, selezionare **dopo l'avvio dell'applicazione**. L'applicazione inizierà più velocemente in questo modo, e quindi verrà cercare gli aggiornamenti in background e notifica solo all'utente quando è disponibile un aggiornamento. Una volta installato, gli aggiornamenti verranno rese effettive fino a quando l'applicazione viene riavviata.  
  
6.  Nel **specificare la frequenza con cui controllare l'applicazione di aggiornamenti** , quindi selezionare **controllare ogni volta che l'applicazione viene eseguita** (predefinito) o **controllare ogni** e immettere un intervallo di tempo e numerico.  
  
### <a name="to-specify-a-minimum-required-version-for-the-application"></a>Per specificare una versione minima richiesta per l'applicazione  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Scegliere il **pubblica** scheda.  
  
3.  Fare clic sul **aggiornamenti** per aprire il **gli aggiornamenti dell'applicazione** nella finestra di dialogo.  
  
4.  Nel **gli aggiornamenti dell'applicazione** finestra di dialogo, assicurarsi che le **controllare la disponibilità di aggiornamenti** casella di controllo è selezionata.  
  
5.  Selezionare il **specificare la versione minima richiesta per questa applicazione** casella di controllo e quindi immettere **principali**, **secondaria**, **compilare**e  **Revisione** numeri per l'applicazione.  
  
### <a name="to-specify-a-different-update-location"></a>Per specificare un percorso di aggiornamento diversi  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Scegliere il **pubblica** scheda.  
  
3.  Fare clic sul **aggiornamenti** per aprire il **gli aggiornamenti dell'applicazione** nella finestra di dialogo.  
  
4.  Nel **gli aggiornamenti dell'applicazione** finestra di dialogo, assicurarsi che le **controllare la disponibilità di aggiornamenti** casella di controllo è selezionata.  
  
5.  Nel **percorso di aggiornamento** immettere il percorso di aggiornamento con un URL completo, utilizzando il formato *http://Hostname/ApplicationName*, o un percorso UNC nel formato  *\\\Server\ ApplicationName*, oppure fare clic sui **Sfoglia** per cercare il percorso di aggiornamento.  
  
### <a name="to-check-for-updates-programmatically"></a>Per cercare gli aggiornamenti a livello di codice  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Scegliere il **pubblica** scheda.  
  
3.  Fare clic sul **aggiornamenti** per aprire il **gli aggiornamenti dell'applicazione** nella finestra di dialogo.  
  
4.  Nel **gli aggiornamenti dell'applicazione** finestra di dialogo, assicurarsi che le **controllare la disponibilità di aggiornamenti** casella di controllo è deselezionata. (Facoltativamente, è possibile selezionare questa casella di controllo per verificare gli aggiornamenti a livello di codice e anche consentono il runtime di ClickOnce cercare gli aggiornamenti automaticamente.)  
  
5.  Nel **percorso di aggiornamento** immettere il percorso di aggiornamento con un URL completo, utilizzando il formato *http://Hostname/ApplicationName*, o un percorso UNC nel formato  *\\\Server\ ApplicationName*, oppure fare clic sui **Sfoglia** per cercare il percorso di aggiornamento. Il percorso di aggiornamento è in cui l'applicazione avrà un aspetto di una versione aggiornata di se stesso.  
  
6.  Creare un pulsante, voce di menu o un altro elemento dell'interfaccia utente in un Form Windows che gli utenti selezioneranno per cercare gli aggiornamenti. Dal gestore eventi dell'elemento, chiamare un metodo per verificare e installare gli aggiornamenti. È possibile trovare un esempio di codice Visual Basic e Visual c# per tale metodo in [procedura: verificare la presenza di aggiornamenti dell'applicazione a livello di codice tramite l'API della distribuzione ClickOnce](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md).  
  
7.  Compilare l'applicazione.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Deployment.Application.ApplicationDeployment>   
 [Finestra di dialogo Aggiornamenti applicazione](http://msdn.microsoft.com/en-us/8eca8743-8e68-4d04-bfd5-4dc0a9b2934f)   
 [Scegliere una strategia di aggiornamento ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Pubblicazione ClickOnce aplications](../deployment/publishing-clickonce-applications.md)   
 [Procedura: pubblicare un'applicazione ClickOnce mediante la pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Procedura: verificare la presenza di aggiornamenti dell'applicazione a livello di codice tramite l'API della distribuzione ClickOnce](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md)