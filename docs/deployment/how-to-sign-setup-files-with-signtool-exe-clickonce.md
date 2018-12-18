---
title: 'Procedura: accesso file di installazione con SignTool.exe (ClickOnce) | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, signtool.exe
- deploying applications [ClickOnce], re-signing setup.exe
- ClickOnce deployment, signtool.exe
- ClickOnce applications, re-signing setup.exe
- ClickOnce deployment, re-signing setup.exe
ms.assetid: 545a4005-d283-4110-9821-c78a9833c250
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dc4dc7b2f96b1d36e91e8114458a7a8e9f3231f3
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-sign-setup-files-with-signtoolexe-clickonce"></a>Procedura: firmare i file di installazione con SignTool.exe (ClickOnce)
È possibile usare SignTool.exe per firmare un programma di installazione (setup.exe). Questo processo aiuta ad assicurare che nei computer degli utenti finali non siano installati file alterati.  
  
 Per impostazione predefinita, ClickOnce include manifesti firmati e un programma di installazione firmato. Se tuttavia si vogliono modificare i parametri del programma di installazione in un secondo momento, sarà necessario firmare il programma in un secondo momento. Se si cambiano i parametri dopo la firma del programma di installazione, la firma sarà danneggiata.  
  
 La procedura seguente genera manifesti non firmati e un programma di installazione non firmato. La firma ClickOnce è quindi abilitata in seguito in Visual Studio per generare manifesti firmati. Il programma di installazione è lasciato non firmato, in modo che il cliente possa firmare il file eseguibile con il proprio certificato.  
  
### <a name="to-generate-an-unsigned-setup-program-and-sign-later"></a>Per generare un programma di installazione non firmato e firmarlo in seguito  
  
1.  Installare nel computer di sviluppo il certificato da usare per la firma del manifesto.  
  
2.  Selezionare il progetto in **Esplora**.  
  
3.  Nel **progetto** menu, fare clic su *ProjectName* **proprietà**.  
  
4.  Nel **firma** pagina deseleziona **firmare i manifesti ClickOnce**.  
  
5.  Nel **pubblica** pagina, fare clic su **prerequisiti**.  
  
6.  Verificare che tutti i prerequisiti siano selezionati e, quindi fare clic su **OK**.  
  
7.  Nel **pubblica** pagina, verificare le impostazioni di pubblicazione e quindi fare clic su **pubblica**.  
  
     La soluzione pubblica il manifesto dell'applicazione non firmato, il manifesto della distribuzione non firmato, i file specifici della versione e il programma di installazione non firmato nel percorso della cartella di pubblicazione.  
  
8.  Nel **pubblica** pagina, fare clic su **prerequisiti**.  
  
9. Nel **prerequisiti** nella finestra di dialogo Cancella **Crea programma di installazione per installare componenti dei prerequisiti**.  
  
10. Nel **pubblica** pagina, verificare le impostazioni di pubblicazione e quindi fare clic su **pubblica**.  
  
     La soluzione pubblica il manifesto dell'applicazione firmato, il manifesto della distribuzione firmato e i file specifici della versione nel percorso della cartella di pubblicazione. Il programma di installazione non firmato non sarà sovrascritto dal processo di pubblicazione.  
  
11. Aprire un prompt dei comandi nel sito del cliente.  
  
12. Passare alla directory che contiene il file con estensione exe.  
  
13. Firmare il file con estensione exe con il comando seguente:  
  
    ```  
    signtool sign /sha1 CertificateHash Setup.exe  
    signtool sign /f CertFileName Setup.exe  
    ```  
  
     Per firmare il programma di installazione, ad esempio, usare uno dei comandi seguenti:  
  
    ```  
    signtool sign /sha1 CCB... Setup.exe  
    signtool sign /f CertFileName Setup.exe  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Ripetere la firma dei manifesti dell'applicazione e di distribuzione](../deployment/how-to-re-sign-application-and-deployment-manifests.md)