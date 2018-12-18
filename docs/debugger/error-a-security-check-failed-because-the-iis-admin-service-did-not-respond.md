---
title: 'Errore: Un controllo di sicurezza non riuscita perché il servizio di amministrazione IIS non risponde | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.iis_not_responding
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a3b0b3412c450976cb15211813de32ab6e78eaa9
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="error-a-security-check-failed-because-the-iis-admin-service-did-not-respond"></a>Errore: controllo di sicurezza non riuscito. Il servizio di amministrazione IIS non ha risposto
Questo errore si verifica quando il servizio di amministrazione IIS non risponde. In questo modo viene indicato che l'installazione di IIS presenta un problema. In primo luogo, verificare che il servizio sia in esecuzione utilizzando il **servizi** dello strumento **strumenti di amministrazione**.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Reinstallare IIS tramite il **Aggiungi / Rimuovi programmi** Pannello di controllo.  
  
-   oppure  
  
-   Disinstallare IIS dal computer mediante Installazione applicazioni in Pannello di controllo. Se è stato disinstallato IIS ma si verificano ancora problemi, controllare il Registro di sistema e accertarsi che questa chiave non esista più:  
  
    ```  
    HKEY_CLASSES_ROOT\CLSID\{A9E69610-B80D-11D0-B9B9-00A0C922E750}  
    ```  
  
     oppure  
  
-   Disabilitare il servizio di amministrazione IIS tramite il pannello di controllo Strumenti di amministrazione. In questo modo il servizio IIS verrà disabilitato sul proprio computer.  
  
     Dopo aver eseguito uno di questi tre passaggi, riavviare il computer.  
  
     Per ulteriori informazioni, vedere la documentazione relativa al servizio IIS.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di applicazioni Web: errori e risoluzione dei problemi](../debugger/debugging-web-applications-errors-and-troubleshooting.md)