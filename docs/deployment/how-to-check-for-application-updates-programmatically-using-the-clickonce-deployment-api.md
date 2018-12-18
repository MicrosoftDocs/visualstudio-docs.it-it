---
title: "Procedura: cercare gli aggiornamenti dell'applicazione a livello di codice utilizzando l'API della distribuzione ClickOnce | Documenti Microsoft"
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- application updates
ms.assetid: 1a886310-67c8-44e5-a382-c2f0454f887d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5953af7c6aafe914be409d8c3ab459b6b4261e54
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api"></a>Procedura: controllare gli aggiornamenti dell'applicazione a livello di codice tramite l'API della distribuzione ClickOnce
ClickOnce fornisce due modi per aggiornare un'applicazione distribuita. Nel primo metodo, è possibile configurare la distribuzione ClickOnce per cercare automaticamente gli aggiornamenti a determinati intervalli. Il secondo metodo, è possibile scrivere codice che usa la <xref:System.Deployment.Application.ApplicationDeployment> classe per controllare gli aggiornamenti in base a un evento, ad esempio una richiesta dell'utente.  
  
 Nelle procedure seguenti è illustrato il codice per l'esecuzione di un aggiornamento a livello di codice e viene inoltre descritto come configurare la distribuzione ClickOnce per abilitare i controlli a livello di codice di aggiornamento.  
  
 Per aggiornare un'applicazione ClickOnce a livello di codice, è necessario specificare un percorso per gli aggiornamenti. Ciò è talvolta detta un provider di distribuzione. Per ulteriori informazioni sull'impostazione di questa proprietà, vedere [scelta di una strategia di aggiornamento ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
> [!NOTE]
>  È inoltre possibile utilizzare la tecnica descritta di seguito per distribuire l'applicazione da un'unica posizione, ma è un aggiornamento da un'altra. Per ulteriori informazioni, vedere [procedura: specificare un percorso alternativo per la distribuzione degli aggiornamenti](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md).  
  
### <a name="to-check-for-updates-programmatically"></a>Per cercare gli aggiornamenti a livello di codice  
  
1.  Creare una nuova applicazione Windows Form utilizzando gli strumenti da riga di comando o nell'oggetto visivo Preferiti.  
  
2.  Creare pulsanti, voce di menu o altri elementi dell'interfaccia utente con cui si desidera agli utenti di selezionare questa opzione per cercare gli aggiornamenti. Dal gestore di evento dell'elemento, chiamare il metodo seguente per verificare e installare gli aggiornamenti.  
  
     [!code-csharp[ClickOnceAPI#6](../deployment/codesnippet/CSharp/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cs)]
     [!code-cpp[ClickOnceAPI#6](../deployment/codesnippet/CPP/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cpp)]
     [!code-vb[ClickOnceAPI#6](../deployment/codesnippet/VisualBasic/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.vb)]  
  
3.  Compilare l'applicazione.  
  
### <a name="using-mageexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Utilizzo di Mage.exe per distribuire un'applicazione che controlla gli aggiornamenti a livello di codice  
  
-   Seguire le istruzioni per la distribuzione dell'applicazione utilizzando Mage.exe, come illustrato in [procedura dettagliata: distribuzione manuale di un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Quando si chiama Mage.exe per generare il manifesto di distribuzione, assicurarsi di utilizzare l'opzione della riga di comando `providerUrl`e per specificare l'URL in cui deve essere controllato per gli aggiornamenti. Se l'applicazione verrà aggiornato da [ http://www.adatum.com/MyApp ](http://www.adatum.com/MyApp), ad esempio, la chiamata per generare il manifesto di distribuzione sarà simile al seguente:  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application  
    ```  
  
### <a name="using-mageuiexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Uso di MageUI.exe per distribuire un'applicazione che controlla gli aggiornamenti a livello di codice  
  
-   Seguire le istruzioni per la distribuzione dell'applicazione utilizzando Mage.exe, come illustrato in [procedura dettagliata: distribuzione manuale di un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Nel **opzioni di distribuzione** scheda, impostare il **Start Location** campo al manifesto dell'applicazione ClickOnce deve cercare gli aggiornamenti. Nel **le opzioni di aggiornamento** scheda, deseleziona il **l'applicazione deve controllare disponibilità di aggiornamenti** casella di controllo.  
  
## <a name="net-framework-security"></a>Sicurezza di .NET Framework  
 L'applicazione deve disporre delle autorizzazioni di attendibilità totale per utilizzare l'aggiornamento a livello di codice.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: specificare un percorso alternativo per la distribuzione aggiornamenti](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)   
 [Scelta di una strategia di aggiornamento ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)