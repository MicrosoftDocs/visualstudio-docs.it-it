---
title: Modalità di esecuzione di aggiornamenti dell'applicazione ClickOnce | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- updates, ClickOnce
- ClickOnce deployment, updates
- deploying applications [ClickOnce], application updates
ms.assetid: d54313c2-cf0c-420d-b151-99953a95f0bb
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bbe09cfe546d947bf07334e9dd6468226884e9e3
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="how-clickonce-performs-application-updates"></a>Come vengono eseguiti gli aggiornamenti di applicazioni con ClickOnce
ClickOnce utilizza le informazioni sulla versione di file specificati nel manifesto di distribuzione di un'applicazione per decidere se aggiornare i file dell'applicazione. Dopo l'avvio di un aggiornamento, ClickOnce Usa una tecnica denominata *file patch* per evitare la ridondanza di download dei file dell'applicazione.  
  
## <a name="file-patching"></a>L'applicazione di patch di file  
 Durante l'aggiornamento di un'applicazione ClickOnce non scarica tutti i file per la nuova versione dell'applicazione a meno che non sono stati modificati i file. Al contrario, vengono confrontate le firme hash dei file specificati nel manifesto dell'applicazione per l'applicazione corrente rispetto alle firme contenute nel manifesto per la nuova versione. Se le firme di un file sono diverse, viene scaricata la nuova versione. Se le firme corrispondono, il file non è modificato da una versione a quella successiva. In questo caso, ClickOnce consente di copiare il file esistente e viene utilizzato nella nuova versione dell'applicazione. Questo approccio impedisce ClickOnce di dover scaricare di nuovo l'intera applicazione anche se solo uno o due file sono stati modificati.  
  
 L'applicazione di patch file funziona anche per gli assembly che vengono scaricati su richiesta utilizzando il <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> e <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroupAsync%2A> metodi.  
  
 Se si utilizza Visual Studio per compilare l'applicazione, verrà generato nuove firme hash per tutti i file ogni volta che si ricompila l'intero progetto. In questo caso, tutti gli assembly verranno scaricati nel client, anche se solo alcuni assembly sia stato modificato.  
  
 File di patch non funziona per i file che sono contrassegnati come dati archiviati nella directory di dati. Questi vengono sempre scaricati indipendentemente dalla firma di hash del file. Per ulteriori informazioni sulla directory dei dati, vedere [l'accesso a dati locali e remoti in applicazioni ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Scelta di una strategia di aggiornamento ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Scelta di una strategia di distribuzione ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)