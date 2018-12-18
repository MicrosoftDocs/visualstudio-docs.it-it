---
title: "Procedura: configurare il comportamento della richiesta di attendibilità ClickOnce | Documenti Microsoft"
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
- ClickOnce deployment, install without prompting
- deploying applications [ClickOnce], trust prompt
- ClickOnce applications, install without prompting
- ClickOnce applications, trust prompt
- ClickOnce deployment, trust prompt
ms.assetid: cc04fa75-012b-47c9-9347-f4216be23cf2
caps.latest.revision: "11"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 8822d0aa9947dccbdfabc43d7090b52eba7d0844
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-the-clickonce-trust-prompt-behavior"></a>Procedura: configurare il comportamento di richiesta di attendibilità di ClickOnce
È possibile configurare la richiesta di attendibilità di ClickOnce per controllare se gli utenti finali viene forniti la possibilità di installare le applicazioni ClickOnce, ad esempio le applicazioni Windows Form, applicazioni Windows Presentation Foundation, applicazioni console, browser WPF le applicazioni e soluzioni Office. Per configurare la richiesta di attendibilità, impostare le chiavi del Registro di sistema nel computer di ogni utente finale.  
  
 Nella tabella seguente vengono illustrate le opzioni di configurazione che possono essere applicate a ognuna delle cinque aree (Internet, siti non attendibili, MyComputer, LocalIntranet e siti attendibili).  
  
|Opzione|Valore dell'impostazione del Registro di sistema|Descrizione|  
|------------|----------------------------|-----------------|  
|Abilitare la richiesta di attendibilità.|`Enabled`|La richiesta di attendibilità di ClickOnce è visualizzato in modo che gli utenti finali possono concedere l'attendibilità alle applicazioni ClickOnce.|  
|Limitare la richiesta di attendibilità.|`AuthenticodeRequired`|La richiesta di attendibilità di ClickOnce viene visualizzata solo se le applicazioni ClickOnce sono firmate con un certificato che identifica il server di pubblicazione.|  
|Disabilitare la richiesta di attendibilità.|`Disabled`|La richiesta di attendibilità di ClickOnce non viene visualizzata per le applicazioni ClickOnce che non sono firmate con un certificato attendibile in modo esplicito.|  
  
 Nella tabella seguente viene illustrato il comportamento predefinito per ogni area. La colonna applicazioni fa riferimento per le applicazioni Windows Form, applicazioni Windows Presentation Foundation, le applicazioni browser WPF e applicazioni console.  
  
|Zona|Applicazioni|soluzioni Office|  
|----------|------------------|----------------------|  
|`MyComputer`|`Enabled`|`Enabled`|  
|`LocalIntranet`|`Enabled`|`Enabled`|  
|`TrustedSites`|`Enabled`|`Enabled`|  
|`Internet`|`Enabled`|`AuthenticodeRequired`|  
|`UntrustedSites`|`Disabled`|`Disabled`|  
  
 È possibile eseguire l'override di queste impostazioni abilitando, limitare o disabilitare la richiesta di attendibilità di ClickOnce.  
  
## <a name="enabling-the-clickonce-trust-prompt"></a>Abilitare la richiesta di attendibilità di ClickOnce  
 Abilitare la richiesta di attendibilità per una zona quando si desidera che gli utenti finali devono essere presentati con l'opzione di installazione e l'esecuzione di qualsiasi applicazione ClickOnce che proviene da tale area.  
  
#### <a name="to-enable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Per abilitare la richiesta di attendibilità di ClickOnce utilizzando l'editor del Registro di sistema  
  
1.  Aprire l'editor del Registro di sistema:  
  
    1.  Fare clic su **avviare**, quindi fare clic su **eseguire**.  
  
    2.  Nel **aprire** digitare `regedit32`, quindi fare clic su **OK**.  
  
2.  Trovare la chiave del Registro di sistema seguente:  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel  
  
     Se la chiave non esiste, crearla.  
  
3.  Aggiungere le seguenti sottochiavi come **valore stringa**, se non già presenti, con i valori associati riportati nella tabella seguente.  
  
    |Sottochiave del valore stringa|Valore|  
    |-------------------------|-----------|  
    |`Internet`|`Enabled`|  
    |`UntrustedSites`|`Disabled`|  
    |`MyComputer`|`Enabled`|  
    |`LocalIntranet`|`Enabled`|  
    |`TrustedSites`|`Enabled`|  
  
     Per le soluzioni Office, `Internet` ha il valore predefinito `AuthenticodeRequired` e `UntrustedSites` ha il valore `Disabled`. Per tutti gli altri, `Internet` ha il valore predefinito `Enabled`.  
  
#### <a name="to-enable-the-clickonce-trust-prompt-programmatically"></a>Per abilitare la richiesta di attendibilità ClickOnce a livello di codice  
  
1.  Creare un'applicazione console Visual Basic o Visual c# in Visual Studio.  
  
2.  Aprire il file Program. vb o Program.cs per la modifica e aggiungere il codice seguente.  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Enabled")  
    key.SetValue("LocalIntranet", "Enabled")  
    key.SetValue("Internet", "Enabled")  
    key.SetValue("TrustedSites", "Enabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```csharp  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "Enabled");  
    key.SetValue("LocalIntranet", "Enabled");  
    key.SetValue("Internet", "AuthenticodeRequired");  
    key.SetValue("TrustedSites", "Enabled");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
    ```  
  
3.  Compilare ed eseguire l'applicazione.  
  
## <a name="restricting-the-clickonce-trust-prompt"></a>Limitare la richiesta di attendibilità di ClickOnce  
 Limitare la richiesta di attendibilità in modo che le soluzioni devono essere firmate con certificati Authenticode con identità nota affinché gli utenti vengono richiesto di prendere una decisione di attendibilità.  
  
#### <a name="to-restrict-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Per limitare la richiesta di attendibilità di ClickOnce utilizzando l'editor del Registro di sistema  
  
1.  Aprire l'editor del Registro di sistema:  
  
    1.  Fare clic su **avviare**, quindi fare clic su **eseguire**.  
  
    2.  Nel **aprire** digitare `regedit`, quindi fare clic su **OK**.  
  
2.  Trovare la chiave del Registro di sistema seguente:  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel  
  
     Se la chiave non esiste, crearla.  
  
3.  Aggiungere le seguenti sottochiavi come **valore stringa**, se non già presenti, con i valori associati riportati nella tabella seguente.  
  
    |Sottochiave del valore stringa|Valore|  
    |-------------------------|-----------|  
    |`UntrustedSites`|`Disabled`|  
    |`Internet`|`AuthenticodeRequired`|  
    |`MyComputer`|`AuthenticodeRequired`|  
    |`LocalIntranet`|`AuthenticodeRequired`|  
    |`TrustedSites`|`AuthenticodeRequired`|  
  
#### <a name="to-restrict-the-clickonce-trust-prompt-programmatically"></a>Per limitare la richiesta di attendibilità ClickOnce a livello di codice  
  
1.  Creare un'applicazione console Visual Basic o Visual c# in Visual Studio.  
  
2.  Aprire il file Program. vb o Program.cs per la modifica e aggiungere il codice seguente.  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "AuthenticodeRequired")  
    key.SetValue("LocalIntranet", "AuthenticodeRequired")  
    key.SetValue("Internet", "AuthenticodeRequired")  
    key.SetValue("TrustedSites", "AuthenticodeRequired")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```csharp  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "AuthenticodeRequired");  
    key.SetValue("LocalIntranet", "AuthenticodeRequired");  
    key.SetValue("Internet", "AuthenticodeRequired");  
    key.SetValue("TrustedSites", "AuthenticodeRequired");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
    ```  
  
3.  Compilare ed eseguire l'applicazione.  
  
## <a name="disabling-the-clickonce-trust-prompt"></a>Disabilitare la richiesta di attendibilità di ClickOnce  
 È possibile disabilitare la richiesta di attendibilità in modo che gli utenti finali non viene forniti la possibilità di installare le soluzioni che non sono già attendibili in Criteri di sicurezza.  
  
#### <a name="to-disable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Per disabilitare la richiesta di attendibilità di ClickOnce utilizzando l'editor del Registro di sistema  
  
1.  Aprire l'editor del Registro di sistema:  
  
    1.  Fare clic su **avviare**, quindi fare clic su **eseguire**.  
  
    2.  Nel **aprire** digitare `regedit`, quindi fare clic su **OK**.  
  
2.  Trovare la chiave del Registro di sistema seguente:  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel  
  
     Se la chiave non esiste, crearla.  
  
3.  Aggiungere le seguenti sottochiavi come **valore stringa**, se non già presenti, con i valori associati riportati nella tabella seguente.  
  
    |Sottochiave del valore stringa|Valore|  
    |-------------------------|-----------|  
    |`UntrustedSites`|`Disabled`|  
    |`Internet`|`Disabled`|  
    |`MyComputer`|`Disabled`|  
    |`LocalIntranet`|`Disabled`|  
    |`TrustedSites`|`Disabled`|  
  
#### <a name="to-disable-the-clickonce-trust-prompt-programmatically"></a>Per disabilitare la richiesta di attendibilità ClickOnce a livello di codice  
  
1.  Creare un'applicazione console Visual Basic o Visual c# in Visual Studio.  
  
2.  Aprire il file Program. vb o Program.cs per la modifica e aggiungere il codice seguente.  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Disabled")  
    key.SetValue("LocalIntranet", "Disabled")  
    key.SetValue("Internet", "Disabled")  
    key.SetValue("TrustedSites", "Disabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```csharp  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "Disabled");  
    key.SetValue("LocalIntranet", "Disabled");  
    key.SetValue("Internet", "Disabled");  
    key.SetValue("TrustedSites", "Disabled");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
  
    ```  
  
3.  Compilare ed eseguire l'applicazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Protezione di applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Sicurezza dall'accesso di codice per applicazioni ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce e Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Cenni preliminari sulla distribuzione di applicazioni attendibili](../deployment/trusted-application-deployment-overview.md)   
 [How to: Enable ClickOnce Security Settings](../deployment/how-to-enable-clickonce-security-settings.md)  (Procedura: Abilitare le impostazioni di sicurezza ClickOnce)  
 [Procedura: impostare un'area di sicurezza per un'applicazione ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Procedura: impostare le autorizzazioni personalizzate per un'applicazione ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Procedura: eseguire il debug di un'applicazione ClickOnce con autorizzazioni limitate](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Procedura: aggiungere un autore attendibile a un Computer Client per applicazioni ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Procedura: Ripetere la firma dei manifesti dell'applicazione e di distribuzione](../deployment/how-to-re-sign-application-and-deployment-manifests.md)