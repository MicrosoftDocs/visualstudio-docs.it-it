---
title: 'Procedura: configurare la protezione di elenco di inclusione | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio
- inclusion lists [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f8995e95ed1a35841aab945daa1ea35854946b56
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-configure-inclusion-list-security"></a>Procedura: configurare la sicurezza dell'elenco di inclusione
  Se si dispone delle autorizzazioni di amministratore, è possibile configurare il [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] richiesta di attendibilità per controllare se gli utenti finali è data la possibilità di installare le soluzioni Office salvando una decisione di attendibilità per l'elenco di inclusione. Per informazioni sugli elenchi di inclusione, vedere [Trusting soluzioni di Office per gli elenchi di inclusione](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Per le soluzioni in ognuna delle cinque aree, è possibile impostare le opzioni seguenti:  
  
-   Abilitare il [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] chiave dei messaggi di richiesta di attendibilità e l'elenco di inclusione. È possibile consentire agli utenti finali di concedere l'attendibilità alle soluzioni Office firmate con un certificato.  
  
-   Limitare il [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] chiave dei messaggi di richiesta di attendibilità e l'elenco di inclusione. È possibile consentire agli utenti finali di installare le soluzioni Office firmate con un certificato che identifica il server di pubblicazione, ma che non è attendibile.  
  
-   Disabilitare il [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] chiave dei messaggi di richiesta di attendibilità e l'elenco di inclusione. È possibile impedire agli utenti finali di installazione di soluzioni Office che non sono firmato con un certificato attendibile in modo esplicito.  
  
## <a name="enabling-the-inclusion-list"></a>Abilitazione dell'elenco di inclusione  
 Abilitare l'elenco di inclusione per una zona quando si desidera che gli utenti finali devono essere presentati con l'opzione di installazione e l'esecuzione di soluzioni Office che provengono da tale area.  
  
#### <a name="to-enable-the-inclusion-list-by-using-the-registry-editor"></a>Per abilitare l'elenco di inclusione tramite l'editor del Registro di sistema  
  
1.  Aprire l'editor del Registro di sistema:  
  
    1.  Fare clic su **avviare**, quindi fare clic su **eseguire**.  
  
    2.  Nel **aprire** digitare **regedt32.exe**, quindi fare clic su **OK**.  
  
2.  Trovare la chiave del Registro di sistema seguente:  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel  
  
     Se la chiave non esiste, crearla.  
  
3.  Aggiungere le seguenti sottochiavi come **valore stringa**, se non già presenti, con i valori associati.  
  
    |Sottochiave del valore stringa|Valore|  
    |-------------------------|-----------|  
    |**Internet**|**AuthenticodeRequired**|  
    |**Siti non attendibili**|**Disabilitato**|  
    |**Risorse del computer**|**Enabled**|  
    |**LocalIntranet**|**Enabled**|  
    |**Siti attendibili**|**Enabled**|  
  
     Per impostazione predefinita, **Internet** ha il valore **AuthenticodeRequired** e **siti non** ha il valore **disabilitato**.  
  
#### <a name="to-enable-the-inclusion-list-programmatically"></a>Per abilitare l'elenco di inclusione a livello di codice  
  
1.  Creare un'applicazione console Visual Basic o Visual c#.  
  
2.  Aprire il file Program. vb o Program.cs per la modifica e aggiungere il codice seguente.  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Enabled")  
    key.SetValue("LocalIntranet", "Enabled")  
    key.SetValue("Internet", "AuthenticodeRequired")  
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
  
## <a name="restricting-the-inclusion-list"></a>Limitare l'elenco di inclusione  
 Limitare l'elenco di inclusione in modo che le soluzioni devono essere firmate con certificati Authenticode con identità nota affinché gli utenti vengono richiesto di prendere una decisione di attendibilità.  
  
#### <a name="to-restrict-the-inclusion-list"></a>Per limitare l'elenco di inclusione  
  
1.  Aprire l'editor del Registro di sistema:  
  
    1.  Fare clic su **avviare**, quindi fare clic su **eseguire**.  
  
    2.  Nel **aprire** digitare **regedt32.exe**, quindi fare clic su **OK**.  
  
2.  Trovare la chiave del Registro di sistema seguente:  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel  
  
     Se la chiave non esiste, crearla.  
  
3.  Aggiungere le seguenti sottochiavi come **valore stringa**, se non già presenti, con i valori associati.  
  
    |Sottochiave del valore stringa|Valore|  
    |-------------------------|-----------|  
    |**Siti non attendibili**|**Disabilitato**|  
    |**Internet**|**AuthenticodeRequired**|  
    |**Risorse del computer**|**AuthenticodeRequired**|  
    |**LocalIntranet**|**AuthenticodeRequired**|  
    |**Siti attendibili**|**AuthenticodeRequired**|  
  
     Per impostazione predefinita, **Internet** ha il valore **AuthenticodeRequired** e **siti non** ha il valore **disabilitato**.  
  
#### <a name="to-restrict-the-inclusion-list-programmatically"></a>Per limitare l'elenco di inclusione a livello di codice  
  
1.  Creare un'applicazione console Visual Basic o Visual c#.  
  
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
  
## <a name="disabling-the-inclusion-list"></a>La disabilitazione dell'elenco di inclusione  
 È possibile disabilitare l'elenco di inclusione in modo che gli utenti finali possono installare solo le soluzioni che sono firmate con un certificato attendibile e noto.  
  
#### <a name="to-disable-the-inclusion-list"></a>Per disabilitare l'elenco di inclusione  
  
1.  Aprire l'editor del Registro di sistema:  
  
    1.  Fare clic su **avviare**, quindi fare clic su **eseguire**.  
  
    2.  Nel **aprire** digitare **regedt32.exe**, quindi fare clic su **OK**.  
  
2.  Se questa non esiste già, creare la chiave del Registro di sistema seguente:  
  
     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel**  
  
3.  Aggiungere le seguenti sottochiavi come **valore stringa**, se non già presenti, con i valori associati.  
  
    |Sottochiave del valore stringa|Valore|  
    |-------------------------|-----------|  
    |**Siti non attendibili**|**Disabilitato**|  
    |**Internet**|**Disabilitato**|  
    |**Risorse del computer**|**Disabilitato**|  
    |**LocalIntranet**|**Disabilitato**|  
    |**Siti attendibili**|**Disabilitato**|  
  
#### <a name="to-disable-the-inclusion-list-programmatically"></a>Per disabilitare l'elenco di inclusione a livello di codice  
  
1.  Creare un'applicazione console Visual Basic o Visual c#.  
  
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
 [Concessione dell'attendibilità alle soluzioni Office mediante gli elenchi di inclusione](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)   
 [Sicurezza delle soluzioni Office](../vsto/securing-office-solutions.md)  
  
  